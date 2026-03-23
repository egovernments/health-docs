# Generate Search API

### Endpoint

* **Endpoint:** `/excel-ingestion/v1/data/generate/_search`
* **Method:** POST

### Request Structure

#### Body Parameters:

RequestInfo: Object containing request information.

GenerationSearchCriteria: Object containing the search criteria for filtering generation records.

* tenantId: Tenant identifier (required).
* ids: List of generation IDs to search for (optional).
* referenceIds: List of reference IDs to filter by (optional).
* referenceTypes: List of reference types to filter by (optional).
* types: List of resource types to filter by (unified-console) (optional).
* statuses: List of statuses to filter by (pending, completed, failed, expired) (optional).
* locale: Locale to filter by (optional).
* limit: Maximum number of records to return (optional, default: 50, minimum: 1).
* offset: Number of records to skip for pagination (optional, default: 0, minimum: 0).

#### Request Example 1: Search by Generation ID

```
{
  "RequestInfo": {
    "apiId": "excel-ingestion-api",
    "ver": "1.0",
    "ts": 1672531200000,
    "action": "search",
    "msgId": "unique-message-id"
  },
  "GenerationSearchCriteria": {
    "tenantId": "mz",
    "ids": ["550e8400-e29b-41d4-a716-446655440000"]
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
  "GenerationSearchCriteria": {
    "tenantId": "mz",
    "referenceIds": ["campaign-123"],
    "statuses": ["completed"],
    "limit": 10,
    "offset": 0
  }
}
```

#### Request Example 3: Search All Generations for a Tenant

```
{
  "RequestInfo": {
    "apiId": "excel-ingestion-api",
    "ver": "1.0",
    "ts": 1672531200000
  },
  "GenerationSearchCriteria": {
    "tenantId": "mz"
  }
}
```

### Response Structure

#### Success Response:

ResponseInfo: Object containing response information.

GenerationDetails: Array of GenerateResource objects matching the search criteria.

Each GenerateResource contains:

* id: Unique identifier for the generation request.
* tenantId: Tenant identifier.
* type: Type of resource (unified-console).
* hierarchyType: Type of hierarchy.
* referenceId: Reference identifier (e.g., campaign ID).
* referenceType: Type of reference (e.g., campaign, project).
* status: Current status (pending, completed, failed, expired).
* locale: Locale used for the generation.
* fileStoreId: File store identifier (populated when status is 'completed').
* additionalDetails: Additional details including:
  * errorCode: Error code if status is 'failed'
  * errorMessage: Error message if status is 'failed'
* auditDetails: Audit information containing:
  * createdBy: User UUID who created the record
  * lastModifiedBy: User UUID who last modified the record
  * createdTime: Timestamp when created
  * lastModifiedTime: Timestamp when last modified

TotalCount: Total number of records matching the search criteria (without pagination).

