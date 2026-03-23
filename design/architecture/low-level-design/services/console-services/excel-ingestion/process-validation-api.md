# Process Validation API

### Endpoint

* **Endpoint:** `/excel-ingestion/v1/data/process/_validation`
* **Method:** POST

### Request Structure

#### Body Parameters:

RequestInfo: Object containing request information.

ResourceDetails: Object containing the details of the resource to be processed and validated.

* type: unified-console-validation
* tenantId: Tenant identifier.
* hierarchyType: Type of hierarchy (e.g., ADMIN, MICROPLAN).
* referenceId: Reference identifier for the resource (e.g., campaign ID, project ID).
* referenceType: Type of reference (e.g., campaign, project).
* fileStoreId: File store identifier of the uploaded Excel file to be validated.
* locale: Locale for validation messages (optional, defaults to RequestInfo locale).

#### Request Example

```
{
  "RequestInfo": {
    "apiId": "excel-ingestion-api",
    "ver": "1.0",
    "ts": 1672531200000,
    "action": "validate",
    "msgId": "unique-message-id",
    "userInfo": {
      "uuid": "user-uuid-123",
      "emailId": "user@example.com"
    }
  },
   "ResourceDetails": {
      "tenantId": "dev",
      "type": "unified-console-validation",
      "locale" : "en_IN",
      "hierarchyType": "NEWTEST00222",
      "referenceId": "{{referenceId}}",
      "referenceType": "campaign",
      "fileStoreId":"290ec4b1-7013-47af-9696-23bf1c657a67"
    }
}
```

### Response Structure

#### Success Response:

ResponseInfo: Object containing response information.

ProcessResource: Object containing the details of the validation request.

* id: Unique identifier for the validation request (UUID).
* tenantId: Tenant identifier.
* type: unified-console-validation
* hierarchyType: Type of hierarchy.
* referenceId: Reference identifier.
* referenceType: Type of reference.
* fileStoreId: Original uploaded file store identifier.
* status: Current status of validation (pending, completed, failed).
* processedFileStoreId: File store identifier of the validated file with error columns (populated when status is 'completed').
* processedStatus: Validation status (valid, invalid, etc.).
* locale: Locale for validation messages.
* additionalDetails: Additional details including:
  * errorCount: Total number of validation errors found
  * validationStatus: Overall validation status (valid/invalid)
  * rowCount: Total number of rows processed
  * errorCode: Error code if processing failed
  * errorMessage: Error message if processing failed
  * createdByEmail: Email of the user who initiated the request
* auditDetails: Audit information (createdBy, createdTime, lastModifiedBy, lastModifiedTime).

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
    "type": "unified-console-validation",
    "hierarchyType": "ADMIN",
    "referenceId": "campaign-123",
    "referenceType": "campaign",
    "fileStoreId": "{{fileStoreID}}",
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

1. **Client Initiates Request:** The client sends a `process/_validation` request to the Excel Ingestion service with the ProcessResource details containing the fileStoreId of the uploaded Excel file.
2. **Validation of Request:** The Excel Ingestion service validates the request schema:
   * Validates tenant ID
   * Validates resource type
   * Validates hierarchy type
3. **Generate Unique ID:** Generate a unique UUID for the validation request.
4. **Validate Processor Configuration:** Before starting validation, the service validates that the processor classes configured for the resource type exist and are accessible.
5. **Set Audit Details:** Enrich the ProcessResource with audit details:
   * Set createdBy and lastModifiedBy from RequestInfo userInfo
   * Set createdTime and lastModifiedTime to current timestamp
   * Extract and set locale from RequestInfo if not provided
6. **Persist Initial Record:**
   * Set status to 'pending'
   * Persist the initial ProcessResource record to the database via Kafka (save topic)
   * This ensures the record is saved even in central instance deployments
7. **Start Async Validation:**
   * Start the actual Excel validation process in a background thread (using @Async)
   * Return immediately to the client with status 'pending' and HTTP 202 (ACCEPTED)
8. **Async Validation Processing:**
   * The background thread calls `ExcelProcessingService.processExcelFile()`
   * This performs the actual Excel file validation:
     * Downloads Excel file from filestore
     * Fetches localization maps for error messages
     * Pre-validates and fetches schemas from MDMS
     * Validates data in each sheet against MDMS schemas
     * Collects all validation errors
     * Adds validation error columns to sheets with errors
     * Removes template validation formatting
     * Processes with configured processors (if any)
     * Enriches additionalDetails with error counts and validation status
     * Uploads the processed Excel file with error columns to filestore
9.  **Update Status:**

    **Success Case (Valid Data):**

    * Set status to 'completed'
    * Set processedStatus to 'valid'
    * Set processedFileStoreId with the validated file ID
    * Set additionalDetails with:
      * errorCount: 0
      * validationStatus: 'valid'
      * rowCount: Total rows processed
      * createdByEmail: User's email address
    * Update lastModifiedTime and lastModifiedBy
    * Persist to database via Kafka (update topic)

    **Success Case (Invalid Data):**

    * Set status to 'completed'
    * Set processedStatus to 'invalid'
    * Set processedFileStoreId with the validated file ID (contains error columns)
    * Set additionalDetails with:
      * errorCount: Number of validation errors
      * validationStatus: 'invalid'
      * rowCount: Total rows processed
      * createdByEmail: User's email address
    * Update lastModifiedTime and lastModifiedBy
    * Persist to database via Kafka (update topic)

    **Failure Case:**

    * Set status to 'failed'
    * Set processedStatus to 'error: ERROR\_CODE'
    * Set processedFileStoreId to null
    * Enrich additionalDetails with error information:
      * errorCode: Error code identifier
      * errorMessage: Human-readable error message
    * Update lastModifiedTime and lastModifiedBy
    * Persist to database via Kafka (update topic)



### Flow Diagram

```
┌──────────┐
│  Client  │
└─────┬────┘
      │
      │ POST /process/_validation
      │ (ProcessResourceRequest with fileStoreId)
      ▼
┌──────────────────────────────────┐
│  Excel Ingestion Controller      │
│  (IngestionController.java:112)  │
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
             ├─► 5. Start Async Validation
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
│           ASYNC BACKGROUND VALIDATION                       │
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
                          │   (Custom validation logic if configured)
                          │
                          ├─► 7. Handle Post-Processing
                          │   - Persist sheet data to temp tables
                          │   - Publish events (if configured)
                          │
                          ├─► 8. Upload Processed Excel
                          │   (with validation error columns)
                          │
                          └─► 9. Update Resource with Results
                              (errorCount, validationStatus, etc.)
                          │
                          ▼

                          ├─► SUCCESS CASE (Valid):
                          │   - Set status = 'completed'
                          │   - Set processedStatus = 'valid'
                          │   - Set processedFileStoreId
                          │   - Set errorCount = 0
                          │   - Set validationStatus = 'valid'
                          │   - Add createdByEmail
                          │   - Update audit details
                          │   - Push to Kafka Update Topic
                          │
                          ├─► SUCCESS CASE (Invalid):
                          │   - Set status = 'completed'
                          │   - Set processedStatus = 'invalid'
                          │   - Set processedFileStoreId
                          │   - Set errorCount = N
                          │   - Set validationStatus = 'invalid'
                          │   - Add createdByEmail
                          │   - Update audit details
                          │   - Push to Kafka Update Topic
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

                    Client polls /process/_search
                    to check final status
```

### Status States

The validation process goes through the following status states:

1. **pending:** Initial state when the validation request is accepted. The Excel validation is queued for processing.
2. **completed:** The Excel file has been successfully validated. The `processedFileStoreId` field contains the validated file identifier with error columns added (if errors were found). The `processedStatus` field indicates whether the data is 'valid' or 'invalid'.
3. **failed:** The validation process encountered an error. Error details are available in `additionalDetails`:
   * `errorCode`: Identifier for the error type
   * `errorMessage`: Human-readable error description
   * `processedStatus`: Contains 'error: ERROR\_CODE'

#### Process Validation Configuration

Below is the MDMS configuration used during the `process/_validation` . Based on the sheet name and process class, the corresponding sheet is validate.

```
{
        "sheets": [
            {
                "sheetName": "HCM_ADMIN_CONSOLE_FACILITIES_LIST",
                "schemaName": "facility-microplan-ingestion",
                "parseEnabled": false,
                "processorClass": "FacilityValidationProcessor"
            },
            {
                "sheetName": "HCM_ADMIN_CONSOLE_USERS_LIST",
                "schemaName": "user-microplan-ingestion",
                "parseEnabled": false,
                "processorClass": "UserValidationProcessor"
            },
            {
                "sheetName": "HCM_CONSOLE_BOUNDARY_HIERARCHY",
                "parseEnabled": false,
                "processorClass": "BoundaryHierarchyTargetProcessor"
            }
        ],
        "excelIngestionProcessName": "unified-console-validation"
    }
```
