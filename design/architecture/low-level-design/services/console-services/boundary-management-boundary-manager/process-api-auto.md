# Process API - Auto

### Endpoint

* Endpoint: /boundary-service/v1/\_process
* Method: POST

### Request Structure

Query Parameters:

* tenantId: Tenant identifier
* referenceId: Reference identifier (optional)

Body Parameters:

* RequestInfo: Object containing request information
* ResourceDetails: Object containing the details of the boundary data to be processed
  * tenantId: Tenant identifier
  * hierarchyType: Type of hierarchy (e.g., ADMIN, MICROPLAN)
  * fileStoreId: File store ID of the uploaded Excel file
  * action: Action type (create)
  * referenceId: Reference identifier (optional)

### Request Example

```
{
    "RequestInfo": {
      "apiId": "Rainmaker",
      "authToken": "{{authToken}}",
      "userInfo": {
        "uuid": "dd885ccb-f91d-4bf2-adb8-46fb66217797",
        "userName": "ADMIN",
        "tenantId": "mz"
      },
      "msgId": "1761036073664|en_MZ"
    },
    "ResourceDetails": {
      "tenantId": "mz",
      "hierarchyType": "ADMIN",
      "fileStoreId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
      "action": "create",
      "referenceId": "CAMP-001"
    }
  }
```

### Response Structure

Success Response:

* ResourceDetails: Object containing the details of the process request
  * id: Unique identifier for the process request (UUID)
  * tenantId: Tenant identifier
  * hierarchyType: Type of hierarchy
  * fileStoreId: Original uploaded file store ID
  * processedFileStoreId: Processed file store ID (populated when status is 'completed')
  * action: Action type (create)
  * status: Current status (accepted, started, completed, failed, invalid)
  * referenceId: Reference identifier
  * auditDetails: Audit information
    * createdBy: User UUID who created
    * createdTime: Creation timestamp
    * lastModifiedBy: User UUID who last modified
    * lastModifiedTime: Last modification timestamp
  * additionalDetails: Additional details including error information if failed
    * fileName: Original file name
    * error: Error details (present only if status is 'failed')

### Response Example

```
{
    "ResponseInfo": {
      "apiId": "egov-bff",
      "ver": "0.0.1",
      "ts": 1761036103664,
      "status": "successful"
    },
    "ResourceDetails": {
      "id": "550e8400-e29b-41d4-a716-446655440000",
      "tenantId": "mz",
      "hierarchyType": "ADMIN",
      "fileStoreId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
      "processedFileStoreId": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
      "action": "create",
      "status": "completed",
      "referenceId": "CAMP-001",
      "auditDetails": {
        "createdBy": "dd885ccb-f91d-4bf2-adb8-46fb66217797",
        "createdTime": 1761036073664,
        "lastModifiedBy": "dd885ccb-f91d-4bf2-adb8-46fb66217797",
        "lastModifiedTime": 1761036103664
      },
      "additionalDetails": {
      }
    }
  }
```

### Flow

1. Client Initiates Request: The client sends a process request to the Boundary Management service with Excel file already uploaded to FileStore.
2. Fetch Localization Maps: Service fetches localization maps for hierarchy-specific and boundary management modules.
3. Validation of Request: The service validates the request and performs pre-processing validations: - Validates tenantId - Validates hierarchyType - Validates fileStoreId - Validates action is "create"
4. Generate Unique ID: Generate a unique UUID for the process request.
5. Set Audit Details: Enrich ResourceDetails with audit details: - Set createdBy and lastModifiedBy from RequestInfo userInfo - Set createdTime and lastModifiedTime to current timestamp
6. Persist Initial Record: - Set status to 'accepted' - Persist the initial ResourceDetails record to database via Kafka (save topic)
7. Return Immediate Response: Return to client with status 'accepted' and HTTP 200.
8. Start Background Processing: - Download Excel file from FileStore - Get current flow from database (auto/manual) - Get hierarchy definition from Boundary Service - Validate Excel sheet headers and data - Segregate data (withBoundaryCode, withoutBoundaryCode, manualBoundaryCode) - Validate flow consistency
9. Auto-Generate Boundary Codes (Auto Flow): - Build code mappings from existing boundaries - Build child-parent relationships - Call IdGen service to generate boundary codes - Create boundaryMap
10. Create Boundary Entities: - Check existing entities in chunks of 20 - Create new entities in chunks of 200 - Wait 2 seconds for persistence
11. Create Boundary Relationships: - Build modified child-parent map using codes - Confirm parent exists (retry up to 6 times) - Create boundary relationships
12. Create Localization Messages: - Create French localization messages - Create Portuguese localization messages - Create default (English) localization messages
13. Generate Processed Excel File: - Add generated codes to data - Create Excel workbook with headers and data - Upload to FileStore
14. Update Status: - Success Case:
    * Set status to 'completed'
    * Set processedFileStoreId with uploaded file ID
    * Clear any error details from additionalDetails
    * Update lastModifiedTime and lastModifiedBy
    * Persist to database via Kafka (update topic) - Failure Case:
      * Set status to 'failed'
    * Set processedFileStoreId to null
    * Enrich additionalDetails with error information (errorCode, errorMessage)
    * Update lastModifiedTime and lastModifiedBy
    * Persist to database via Kafka (update topic)
15. Trigger Generate API: After 30 seconds, trigger `/v1/_generate` API with determinedCurrentFlow for downloadable file creation.

### Flow Diagram

```
 ┌──────────┐
  │  Client  │
  └─────┬────┘
        │
        │ POST /v1/_process
        │ (ResourceDetails)
        ▼
  ┌──────────────────────────────────┐
  │  Boundary Controller             │
  └────────────┬─────────────────────┘
               │
               │ processBoundaryService()
               ▼
  ┌──────────────────────────────────┐
  │  Boundary Service                │
  └────────────┬─────────────────────┘
               │
               ├─► 1. Fetch Localization Maps
               │
               ├─► 2. Validate Process Request
               │
               ├─► 3. Generate UUID
               │
               ├─► 4. Set Audit Details
               │   (createdBy, createdTime)
               │
               ├─► 5. Push to Kafka Save Topic
               │   (Status: ACCEPTED)
               │   │
               │   └──► Persister saves to DB
               │
               ├─► 6. Return Response
               │   (Status: ACCEPTED, HTTP 200)
               │
               └─► 7. Start Background Processing
                   │
                   ├─► Download Excel from FileStore
                   │
                   ├─► Get Current Flow from DB
                   │
                   ├─► Get Hierarchy Definition
                   │
                   ├─► Validate Excel Data
                   │
                   ├─► Segregate Data
                   │   (withBoundaryCode, withoutBoundaryCode)
                   │
                   ├─► Auto-Generate Codes (IdGen)
                   │
                   ├─► Create Boundary Entities
                   │   (Chunks of 200)
                   │
                   ├─► Create Boundary Relationships
                   │   (With parent validation)
                   │
                   ├─► Create Localization Messages
                   │   (EN, FR, PT)
                   │
                   ├─► Generate Processed Excel
                   │
                   ├─► Upload to FileStore
                   │
                   ├─► Push to Kafka Update Topic
                   │   (Status: COMPLETED)
                   │
                   └─► Trigger Generate API (30s delay)
```

### Status States

The process goes through the following status states:

* accepted: Initial state when the process request is received and validated. Processing is queued for background execution.
* started: Processing has begun (used for non-create actions).
* completed: Boundary data successfully processed. Entities created, relationships established, and processed file uploaded. The processedFileStoreId field contains the file identifier.
* failed: The processing encountered an error. Error details are available in additionalDetails:
  * error: Stringified JSON containing status, code, description, and message
* invalid: Data validation failed but processing continues with some errors.
