# Process Search API

### Endpoint

* **Endpoint:** `/excel-ingestion/v1/data/process/_search`
* **Method:** POST

### Request Structure

#### Body Parameters:

RequestInfo: Object containing request information.

ProcessingSearchCriteria: Object containing the search criteria for filtering processing records.

* tenantId: Tenant identifier (required).
* ids: List of processing IDs to search for (optional).
* referenceIds: List of reference IDs to filter by (optional).
* referenceTypes: List of reference types to filter by (optional).
* types: List of resource types to filter by (unified-console-parse , unified-console-validation) (optional).
* statuses: List of statuses to filter by (pending, completed, failed) (optional).
* limit: Maximum number of records to return (optional, default: 50, minimum: 1).
* offset: Number of records to skip for pagination (optional, default: 0, minimum: 0).

#### Request Example 1: Search by Processing ID

```
{
  "RequestInfo": {
    "apiId": "excel-ingestion-api",
    "ver": "1.0",
    "ts": 1672531200000,
    "action": "search",
    "msgId": "unique-message-id"
  },
  "ProcessingSearchCriteria": {
    "tenantId": "mz",
    "ids": ["650e8400-e29b-41d4-a716-446655440000"]
  }
}
```

#### Request Example 2: Search by Reference ID and Status

```
{
  "RequestInfo": {
    "apiId": "excel-ingestion-api",
    "ver": "1.0",
    "ts": 1672531200000
  },
  "ProcessingSearchCriteria": {
    "tenantId": "mz",
    "referenceIds": [{{referenceID}}],
    "statuses": ["completed"],
    "limit": 10,
    "offset": 0
  }
}
```

### Response Structure

ResponseInfo: Object containing response information.

ProcessingDetails: Array of ProcessResource objects matching the search criteria.

Each ProcessResource contains:

* id: Unique identifier for the processing request.
* tenantId: Tenant identifier.
* type: Type of resource (unified-console-parse , unified-console-validation).
* hierarchyType: Type of hierarchy (e.g., ADMIN, MICROPLAN).
* referenceId: Reference identifier (e.g., campaign ID, project ID).
* referenceType: Type of reference (e.g., campaign, project).
* fileStoreId: Original uploaded file store identifier.
* processedFileStoreId: Processed file store identifier (populated when status is 'completed').
* status: Current status (pending, completed, failed).
* processedStatus: Processing result status (valid, invalid, error: CODE).
* locale: Locale used for validation messages.
* additionalDetails: Additional details including:
  * errorCount: Total number of validation errors found
  * validationStatus: Overall validation status (valid/invalid)
  * rowCount: Total number of rows processed
  * errorCode: Error code if status is 'failed'
  * errorMessage: Error message if status is 'failed'
  * createdByEmail: Email of the user who initiated the request
* auditDetails: Audit information containing:
  * createdBy: User UUID who created the record
  * lastModifiedBy: User UUID who last modified the record
  * createdTime: Timestamp when created
  * lastModifiedTime: Timestamp when last modified

TotalCount: Total number of records matching the search criteria (without pagination).

#### Response Example

```
{
  "ResponseInfo": {
    "apiId": "excel-ingestion-api",
    "ver": "1.0",
    "ts": 1672531200000,
    "status": "successful"
  },
  "ProcessingDetails": [
    {
      "id": "650e8400-e29b-41d4-a716-446655440000",
      "tenantId": "mz",
      "type": "boundary",
      "hierarchyType": "ADMIN",
      "referenceId": "campaign-123",
      "referenceType": "campaign",
      "fileStoreId": "filestore-id-abc-456",
      "processedFileStoreId": "filestore-id-xyz-789",
      "status": "completed",
      "processedStatus": "valid",
      "locale": "en_IN",
      "additionalDetails": {
        "errorCount": 0,
        "validationStatus": "valid",
        "rowCount": 150,
        "createdByEmail": "user@example.com"
      },
      "auditDetails": {
        "createdBy": "user-uuid-123",
        "lastModifiedBy": "user-uuid-123",
        "createdTime": 1672531200000,
        "lastModifiedTime": 1672531500000
      }
    }
  ],
  "TotalCount": 1
}
```
