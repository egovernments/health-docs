# Process Create API

### Endpoint

* **Endpoint:** `/excel-ingestion/v1/data/process/_create`
* **Method:** POST

### Request Structure

#### Body Parameters:

RequestInfo: Object containing request information.

ResourceDetails: Object containing the details of the resource to be processed and created.

* type: unified-console-parse
* tenantId: Tenant identifier.
* hierarchyType: Type of hierarchy (e.g., ADMIN, MICROPLAN).
* referenceId: Reference identifier for the resource (e.g., campaign ID, project ID).
* referenceType: Type of reference (e.g., campaign, project).
* fileStoreId: File store identifier of the uploaded Excel file to be processed.
* locale: Locale for validation messages (optional, defaults to RequestInfo locale).

#### Request Example

```
{
  "RequestInfo": {
    "apiId": "excel-ingestion-api",
    "ver": "1.0",
    "ts": 1672531200000,
    "action": "create",
    "msgId": "unique-message-id",
    "userInfo": {
      "uuid": "user-uuid-123",
      "emailId": "user@example.com"
    }
  },
  "ResourceDetails": {
    "tenantId": "mz",
    "type": "unified-console-parse",
    "hierarchyType": "ADMIN",
    "referenceId": "9401ca0b-220d-441c-b7d5-2167aea2a765",
    "referenceType": "campaign",
    "fileStoreId": "filestore-id-abc-456",
    "locale": "en_IN",
  }
}
```

### Response Structure

#### Success Response:

ResponseInfo: Object containing response information.

ProcessResource: Object containing the details of the processing request.

* id: Unique identifier for the processing request (UUID).
* tenantId: Tenant identifier.
* type: unified-console-parse
* hierarchyType: Type of hierarchy.
* referenceId: Reference identifier.
* referenceType: Type of reference.
* fileStoreId: Original uploaded file store identifier.
* status: Current status of processing (pending, completed, failed).
* processedFileStoreId: File store identifier of the processed file with error columns (populated when status is 'completed').
* processedStatus: Processing status (valid, invalid, etc.).
* locale: Locale for validation messages.
* additionalDetails: Additional details including:
  * errorCount: Total number of validation errors found
  * validationStatus: Overall validation status (valid/invalid)
  * rowCount: Total number of rows processed
  * errorCode: Error code if processing failed
  * errorMessage: Error message if processing failed
  * createdByEmail: Email of the user who initiated the request
* auditDetails: Audit information (createdBy, createdTime, lastModifiedBy, lastModifiedTime).

#### Response Example

```
{
  "ResponseInfo": {
    "apiId": "excel-ingestion-api",
    "ver": "1.0",
    "ts": 1672531200000,
    "status": "successful"
  },
  "ProcessResource": {
    "id": "650e8400-e29b-41d4-a716-446655440000",
    "tenantId": "mz",
    "type": "unified-console-parse",
    "hierarchyType": "ADMIN",
    "referenceId": "9401ca0b-220d-441c-b7d5-2167aea2a765",
    "referenceType": "campaign",
    "fileStoreId": "eabe0aa2-323f-41a4-abe1-715fff722b445",
    "status": "pending",
    "locale": "en_IN",
    "additionalDetails": {},
    "auditDetails": {
      "createdBy": "user-uuid-123",
      "createdTime": 1672531200000,
      "lastModifiedBy": "user-uuid-123",
      "lastModifiedTime": 1672531200000
    }
  }
}
```

### Flow

1. **Client Initiates Request:** The client sends a `process/_create` request to the Excel Ingestion service with the ProcessResource details containing the fileStoreId of the uploaded Excel file.
2. **Validation of Request:** The Excel Ingestion service validates the request schema:
   * Validates tenant ID
   * Validates resource type
   * Validates hierarchy type
3. **Generate Unique ID:** Generate a unique UUID for the processing request.
4. **Validate Processor Configuration:** Before starting processing, the service validates that the processor classes configured for the resource type exist and are accessible.
5. **Set Audit Details:** Enrich the ProcessResource with audit details:
   * Set createdBy and lastModifiedBy from RequestInfo userInfo
   * Set createdTime and lastModifiedTime to current timestamp
   * Extract and set locale from RequestInfo if not provided
6. **Persist Initial Record:**
   * Set status to 'pending'
   * Persist the initial ProcessResource record to the database via Kafka (save topic)
   * This ensures the record is saved even in central instance deployments
7. **Start Async Processing:**
   * Start the actual Excel processing in a background thread (using @Async)
   * Return immediately to the client with status 'pending' and HTTP 202 (ACCEPTED)
8. **Async Processing:**
   * The background thread calls `ExcelProcessingService.processExcelFile()`
   * This performs the actual Excel file processing and validation:
     * Downloads Excel file from filestore
     * Fetches localization maps for error messages
     * Pre-validates and fetches schemas from MDMS
     * Validates data in each sheet against MDMS schemas
     * Collects all validation errors
     * Adds validation error columns to sheets with errors
     * Removes template validation formatting
     * Processes with configured processors (custom business logic)
     * Enriches additionalDetails with error counts and validation status
     * **Persists sheet data to temporary tables** (for downstream processing)
     * **Publishes parsing complete events** (triggers data creation in other services)
     * Uploads the processed Excel file with error columns to filestore
9.  **Update Status:**

    **Success Case (Valid Data - Data Created):**

    * Set status to 'completed'
    * Set processedStatus to 'valid'
    * Set processedFileStoreId with the processed file ID
    * Set additionalDetails with:
      * errorCount: 0
      * validationStatus: 'valid'
      * rowCount: Total rows processed
      * createdByEmail: User's email address
    * Update lastModifiedTime and lastModifiedBy
    * Persist to database via Kafka (update topic)
    * **Sheet data is available in temp tables for downstream services**
    * **Parsing complete events have been published to Kafka**

    **Success Case (Invalid Data - No Data Created):**

    * Set status to 'completed'
    * Set processedStatus to 'invalid'
    * Set processedFileStoreId with the processed file ID (contains error columns)
    * Set additionalDetails with:
      * errorCount: Number of validation errors
      * validationStatus: 'invalid'
      * rowCount: Total rows processed
      * createdByEmail: User's email address
    * Update lastModifiedTime and lastModifiedBy
    * Persist to database via Kafka (update topic)
    * **No data is created when validation errors exist**

    **Failure Case:**

    * Set status to 'failed'
    * Set processedStatus to 'error: ERROR\_CODE'
    * Set processedFileStoreId to null
    * Enrich additionalDetails with error information:
      * errorCode: Error code identifier
      * errorMessage: Human-readable error message
    * Update lastModifiedTime and lastModifiedBy
    * Persist to database via Kafka (update topic)
10. **Response:** The Excel Ingestion service immediately sends the response back to the client containing the processing ID and 'pending' status. The client can then poll the `/process/_search` endpoint to check the processing status.

### Flow Diagram

```
┌──────────┐
│  Client  │
└─────┬────┘
      │
      │ POST /process/_create
      │ (ProcessResourceRequest with fileStoreId)
      ▼
┌──────────────────────────────────┐
│  Excel Ingestion Controller      │
│  (IngestionController.java:155)  │
└────────────┬─────────────────────┘
             │
             │ initiateProcessing()
             ▼
┌──────────────────────────────────┐
│  Processing Service              │
│  (ProcessingService.java:45)     │
└────────────┬─────────────────────┘
             │
             ├─► 1. Generate UUID
             │
             ├─► 2. Validate Processor Classes
             │   (Ensure configured processors exist)
             │
             ├─► 3. Set Audit Details
             │   (createdBy, createdTime, locale)
             │
             ├─► 4. Push to Kafka Save Topic
             │   (Status: PENDING)
             │   │
             │   └──► Persister saves to DB
             │
             ├─► 5. Start Async Processing
             │   (AsyncProcessingService)
             │
             └─► 6. Return Response
                 (Status: PENDING, HTTP 202)
                 │
                 ▼
             ┌──────────┐
             │  Client  │ ◄── Response with pending status
             └──────────┘

┌────────────────────────────────────────────────────────────┐
│           ASYNC BACKGROUND PROCESSING                       │
└────────────────────────────────────────────────────────────┘

             ┌─────────────────────────────────┐
             │  Async Processing Service       │
             │  (AsyncProcessingService.java:40)│
             └────────────┬────────────────────┘
                          │
                          ├─► Call processExcelFile()
                          │   (ExcelProcessingService)
                          │
                          ▼
             ┌─────────────────────────────────┐
             │  Excel Processing Service       │
             │  (ExcelProcessingService.java:79)│
             └────────────┬────────────────────┘
                          │
                          ├─► 1. Download Excel from filestore
                          │
                          ├─► 2. Fetch Localization Maps
                          │   - Boundary hierarchy localization
                          │   - Schema localization for error messages
                          │
                          ├─► 3. Pre-validate and Fetch Schemas
                          │   (from MDMS based on resource type)
                          │
                          ├─► 4. Validate Excel Data
                          │   - For each sheet in workbook:
                          │     * Convert sheet to List<Map> format
                          │     * Get schema for sheet
                          │     * Validate data against schema
                          │     * Collect validation errors
                          │   - Skip hidden sheets (_h_ prefix/suffix)
                          │   - Merge all errors
                          │
                          ├─► 5. Add Validation Columns
                          │   - For sheets with errors:
                          │     * Remove template validation formatting
                          │     * Add error/warning columns
                          │     * Add localized headers
                          │     * Populate error messages
                          │   - Enrich additionalDetails with:
                          │     * errorCount
                          │     * validationStatus
                          │     * rowCount
                          │
                          ├─► 6. Process with Configured Processors
                          │   - Execute custom business logic
                          │   - Apply data transformations
                          │   - Perform additional validations
                          │   - Modify Excel workbook if needed
                          │
                          ├─► 7. Handle Post-Processing ⭐ KEY STEP ⭐
                          │   - For each sheet:
                          │     * Convert sheet data to JSON format
                          │     * Persist to temporary tables (eg_ex_in_sheet_data_temp)
                          │     * Publish ParsingCompleteEvent to Kafka
                          │   - Events trigger downstream data creation
                          │   - Temp tables allow querying via /sheet/_search
                          │
                          ├─► 8. Upload Processed Excel
                          │   (with validation error columns)
                          │
                          └─► 9. Update Resource with Results
                              (errorCount, validationStatus, etc.)
                          │
                          ▼

                          ├─► SUCCESS CASE (Valid - Data Created):
                          │   - Set status = 'completed'
                          │   - Set processedStatus = 'valid'
                          │   - Set processedFileStoreId
                          │   - Set errorCount = 0
                          │   - Set validationStatus = 'valid'
                          │   - Add createdByEmail
                          │   - Update audit details
                          │   - Push to Kafka Update Topic
                          │   - ✅ Sheet data in temp tables
                          │   - ✅ Parsing events published
                          │   - ✅ Downstream services create entities
                          │
                          ├─► SUCCESS CASE (Invalid - No Data Created):
                          │   - Set status = 'completed'
                          │   - Set processedStatus = 'invalid'
                          │   - Set processedFileStoreId
                          │   - Set errorCount = N
                          │   - Set validationStatus = 'invalid'
                          │   - Add createdByEmail
                          │   - Update audit details
                          │   - Push to Kafka Update Topic
                          │   - ❌ No parsing events (errors exist)
                          │   - ❌ No data creation
                          │
                          └─► FAILURE CASE:
                              - Set status = 'failed'
                              - Set processedStatus = 'error: CODE'
                              - Set processedFileStoreId = null
                              - Enrich error details:
                                * errorCode
                                * errorMessage
                              - Update audit details
                              - Push to Kafka Update Topic
                              - ❌ No data creation

                          │
                          ▼
                    ┌────────────┐
                    │  Persister │ ◄── Update Topic
                    └─────┬──────┘
                          │
                          ▼
                    ┌────────────┐
                    │  Database  │ (Final status: completed/failed)
                    └────────────┘

┌────────────────────────────────────────────────────────────┐
│         DOWNSTREAM DATA CREATION (On Valid Data)            │
└────────────────────────────────────────────────────────────┘

             ┌─────────────────────────────────┐
             │  Kafka: Parsing Complete Event  │
             └────────────┬────────────────────┘
                          │
                          │ ParsingCompleteEvent contains:
                          │ - tenantId, referenceId, type
                          │ - sheetName, rowCount
                          │ - fileStoreId, processedFileStoreId
                          │
                          ▼
             ┌─────────────────────────────────┐
             │  Downstream Service Consumers   │
             │  (Boundary, Facility, User, etc)│
             └────────────┬────────────────────┘
                          │
                          ├─► 1. Read ParsingCompleteEvent
                          │
                          ├─► 2. Query temp tables via /sheet/_search
                          │   (Get parsed JSON data)
                          │
                          ├─► 3. Transform data to entity format
                          │
                          ├─► 4. Create entities via service APIs
                          │   - Create boundaries
                          │   - Create facilities
                          │   - Create users
                          │   - etc.
                          │
                          └─► 5. Update processing status (optional)
                              - Mark data creation complete
                              - Add success/failure details

                    Client polls /process/_search
                    to check final status
```

### Status States

The processing goes through the following status states:

1. **pending:** Initial state when the processing request is accepted. The Excel processing is queued for execution.
2. **completed:** The Excel file has been successfully processed. The `processedFileStoreId` field contains the processed file identifier with error columns added (if errors were found). The `processedStatus` field indicates whether the data is 'valid' or 'invalid':
   * **valid:** No validation errors. Data has been persisted to temp tables and parsing events have been published. Downstream services will create entities.
   * **invalid:** Validation errors found. Data is NOT created. Download the processed file to see error details.
3. **failed:** The processing encountered a system error. Error details are available in `additionalDetails`:
   * `errorCode`: Identifier for the error type
   * `errorMessage`: Human-readable error description
   * `processedStatus`: Contains 'error: ERROR\_CODE

#### Process Create Configuration

Below is the MDMS configuration used during the `process/_create` . Based on the sheet name and process class, the corresponding sheet is parse.

```
{
        "sheets": [
            {
                "sheetName": "HCM_ADMIN_CONSOLE_FACILITIES_LIST",
                "schemaName": "facility-microplan-ingestion",
                "parseEnabled": true
            },
            {
                "sheetName": "HCM_ADMIN_CONSOLE_USERS_LIST",
                "schemaName": "user-microplan-ingestion",
                "parseEnabled": true,
                "processorClass": "UserValidationProcessor"
            },
            {
                "sheetName": "HCM_CONSOLE_BOUNDARY_HIERARCHY",
                "parseEnabled": true,
                "processorClass": "BoundaryHierarchyTargetProcessor"
            }
        ],
        "processingResultTopic": "hcm-processing-result",
        "excelIngestionProcessName": "unified-console-parse"
    }
```
