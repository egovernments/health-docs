# Generate API

### Endpoint

* **Endpoint**: `/excel-ingestion/v1/data/generate/_init`
* **Method**: POST

### Request Structure

#### Body Parameters:

RequestInfo: Object containing request information.

GenerateResource: Object containing the details of the resource to be generated.

* type: unified-console
* tenantId: Tenant identifier.
* hierarchyType: Type of hierarchy.
* referenceId: Reference identifier for the resource (e.g., campaign ID, project ID).
* referenceType: Type of reference (e.g., campaign, project).
* locale: Locale for the generated file&#x20;

### Request Example

```
{
"RequestInfo": {
  "apiId": "Rainmaker",
  "authToken": "{{authToken}}",
  "userInfo": {
    "id": 34602,
    "uuid": "dd885ccb-f91d-4bf2-adb8-46fb66217797",
    "userName": "CAPTAIN",
    "name": "Ritik Verma",
    "mobileNumber": "9437584392",
    "emailId": "ritik.kumar@egovernments.org",
    "locale": null,
    "type": "EMPLOYEE",
    "roles": [
      {
        "name": "Campaign Managers",
        "code": "CAMPAIGN_MANAGER",
        "tenantId": "dev"
      }
    ],
    "active": true,
    "tenantId": "dev",
    "permanentCity": null
  },
  "msgId": "1761036073664|en_IN",
  "plainAccessRequest": {}
}
,
    "GenerateResource": {
        "tenantId": "dev",
        "type": "unified-console",
        "hierarchyType": "{{hierarchyType}}",
        "referenceId": "{{referenceId}}",
        "referenceType": "campaign",
        "locale" : "en_IN"
    }
}
```

### Response Structure

Success Response:

GenerateResource: Object containing the details of the generation request.

* id: Unique identifier for the generation request (UUID).
* tenantId: Tenant identifier.
* type: unified-console
* hierarchyType: Type of hierarchy.
* referenceId: Reference identifier.
* referenceType: Type of reference.
* status: Current status of generation (pending, in\_progress, completed, failed, expired).
* locale: Locale for the generated file.
* fileStoreId: File store identifier (populated when status is 'completed').
* additionalDetails: Additional details including error information if failed.
  * errorCode: Error code if generation failed
  * errorMessage: Error message if generation failed
* auditDetails : show the audit description&#x20;

### Flow

1. **Client Initiates Request:** The client sends a `generate/_init` request to the Excel Ingestion service with the GenerateResource details.
2. **Validation of Request:** The Excel Ingestion service validates the request schema and performs pre-generation validations:
   * Validates tenant ID
   * Validates resource type
   * Validates hierarchy type
   * Validates reference ID and reference type
   * Validates boundary data if present in additionalDetails
   * Validates locale
3. **Expire Previous Records:** Before starting generation, the service expires any previous completed records with the same `referenceId + type` combination by setting their status to 'expired'. This ensures only the latest generation is active.
4. **Generate Unique ID:** Generate a unique UUID for the generation request.
5. **Set Audit Details:** Enrich the GenerateResource with audit details:
   * Set createdBy and lastModifiedBy from RequestInfo userInfo
   * Set createdTime and lastModifiedTime to current timestamp
   * Extract and set locale from RequestInfo if not provided
6. **Persist Initial Record:**
   * Set status to 'pending'
   * Persist the initial GenerateResource record to the database via Kafka (save topic)
   * This ensures the record is saved even in central instance deployments
7. **Start Async Generation:**
   * Start the actual Excel generation process in a background thread (using @Async)
   * Return immediately to the client with status 'pending' and HTTP 202 (ACCEPTED)
8. **Async Processing:**
   * The background thread calls `ExcelWorkflowService.generateAndUploadExcel()`
   * This performs the actual Excel file generation based on the type and configuration
   * The generated file is uploaded to filestore
9.  **Update Status:**

    **Success Case:**

    * Set status to 'completed'
    * Set fileStoreId with the uploaded file ID
    * Clear any error details from additionalDetails
    * Update lastModifiedTime and lastModifiedBy
    * Persist to database via Kafka (update topic)

    **Failure Case:**

    * Set status to 'failed'
    * Set fileStoreId to null
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
      │ POST /generate/_init
      │ (GenerateResourceRequest)
      ▼
┌──────────────────────────────────┐
│  Excel Ingestion Controller      │
│  (IngestionController.java:67)   │
└────────────┬─────────────────────┘
             │
             │ initiateGeneration()
             ▼
┌──────────────────────────────────┐
│  Generation Service              │
│  (GenerationService.java:47)     │
└────────────┬─────────────────────┘
             │
             ├─► 1. Generate UUID
             │
             ├─► 2. Perform Validations
             │   (ExcelGenerationValidationService)
             │
             ├─► 3. Expire Previous Completed Records
             │   (Same referenceId + type)
             │
             ├─► 4. Set Audit Details
             │   (createdBy, createdTime, locale)
             │
             ├─► 5. Push to Kafka Save Topic
             │   (Status: PENDING)
             │   │
             │   └──► Persister saves to DB
             │
             ├─► 6. Start Async Generation
             │   (AsyncGenerationService)
             │
             └─► 7. Return Response
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
             │  Async Generation Service       │
             │  (AsyncGenerationService.java:36)│
             └────────────┬────────────────────┘
                          │
                          ├─► Call generateAndUploadExcel()
                          │   (ExcelWorkflowService)
                          │   - Generate Excel based on type
                          │   - Fetch data from services
                          │   - Apply templates
                          │   - Upload to filestore
                          │
                          ├─► SUCCESS CASE:
                          │   - Set status = 'completed'
                          │   - Set fileStoreId
                          │   - Clear error details
                          │   - Update audit details
                          │   - Push to Kafka Update Topic
                          │
                          └─► FAILURE CASE:
                              - Set status = 'failed'
                              - Set fileStoreId = null
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

                    Client polls /generate/_search
                    to check final status
```

### Status States

The generation process goes through the following status states:

1. **pending:** Initial state when the generation request is accepted. The Excel generation is queued for processing.
2. **completed:** The Excel file has been successfully generated and uploaded to filestore. The `fileStoreId` field contains the file identifier.
3. **failed:** The generation process encountered an error. Error details are available in `additionalDetails`:
   * `errorCode`: Identifier for the error type
   * `errorMessage`: Human-readable error description
4. **expired:** Previous completed records are marked as expired when a new generation request is made for the same `referenceId + type` combination. This ensures only the latest generation is active.

#### Generation Configuration

Below is the MDMS configuration used during the `generate/_init` process. Based on the sheet name and generation class, the corresponding sheet is generated.

```
[
    {
        "sheets": [
            {
                "order": 1,
                "visible": true,
                "sheetName": "HCM_ADMIN_CONSOLE_FACILITIES_LIST",
                "schemaName": "facility-microplan-ingestion",
                "generationClass": "FacilitySheetGenerator",
                "isGenerationClassViaExcelPopulator": false
            },
            {
                "order": 2,
                "visible": true,
                "sheetName": "HCM_ADMIN_CONSOLE_USERS_LIST",
                "schemaName": "user-microplan-ingestion",
                "generationClass": "UserSheetGenerator",
                "isGenerationClassViaExcelPopulator": false
            },
            {
                "order": 3,
                "visible": true,
                "sheetName": "HCM_CONSOLE_BOUNDARY_HIERARCHY",
                "generationClass": "BoundaryHierarchySheetGenerator",
                "isGenerationClassViaExcelPopulator": true
            }
        ],
        "applyWorkbookProtection": true,
        "excelIngestionGenerateName": "unified-console"
    }
]
```

### Error Handling

Errors during generation are captured and stored in the `additionalDetails` field:

#### Error Response Example:

```
{
  "GenerateResource": {
    "id": "550e8400-e29b-41d4-a716-446655440000",
    "tenantId": "mz",
    "type": "microplan",
    "status": "failed",
    "fileStoreId": null,
    "additionalDetails": {
      "errorCode": "BOUNDARY_SERVICE_ERROR",
      "errorMessage": "Failed to fetch boundary data: Connection timeout"
    },
    "lastModifiedTime": 1672531500000
  }
}
```
