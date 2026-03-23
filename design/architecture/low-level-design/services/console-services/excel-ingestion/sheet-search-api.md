# Sheet Search API

### Endpoint

* **Endpoint:** `/excel-ingestion/v1/data/sheet/_search`
* **Method:** POST

### Overview

The Sheet Search API allows you to query temporary sheet data that was persisted during the processing of Excel files via `/process/_create`. After successful processing, the parsed Excel data (converted to JSON format) is stored in temporary tables. This API enables downstream services and applications to retrieve this parsed data for entity creation or analysis.

### Request Structure

#### Body Parameters:

RequestInfo: Object containing request information.

SheetDataSearchCriteria: Object containing the search criteria for filtering sheet data.

* tenantId: Tenant identifier (required).
* referenceId: Reference identifier to filter by (e.g., campaign ID, project ID) (optional).
* fileStoreId: File store identifier to filter by (optional).
* sheetName: Sheet name to filter by (optional).
* limit: Maximum number of records to return (optional, default: all records, minimum: 1, maximum: 100000).
* offset: Number of records to skip for pagination (optional, default: 0, minimum: 0).

Important: At least ONE of `referenceId`, `fileStoreId`, or `sheetName` must be provided.

#### Request Example 1: Search by Reference ID and File Store ID

```
{
  "RequestInfo": {
    "apiId": "excel-ingestion-api",
    "ver": "1.0",
    "ts": 1672531200000,
    "action": "search",
    "msgId": "unique-message-id"
  },
  "SheetDataSearchCriteria": {
    "tenantId": "mz",
    "referenceId": "campaign-123",
    "fileStoreId": "filestore-id-abc-456"
  }
}
```

#### Request Example 2: Search by Reference ID, File Store ID, and Sheet Name

```
{
  "RequestInfo": {
    "apiId": "excel-ingestion-api",
    "ver": "1.0",
    "ts": 1672531200000
  },
  "SheetDataSearchCriteria": {
    "tenantId": "mz",
    "referenceId": "campaign-123",
    "fileStoreId": "filestore-id-abc-456",
    "sheetName": "HCM_ADMIN_CONSOLE_BOUNDARY_DATA"
  }
}
```

### Response Structure

#### Success Response:

ResponseInfo: Object containing response information.

SheetDataDetails: Object containing the search results.

* Data: Array of row data objects. Each object contains:
  * tenantid: Tenant identifier
  * referenceid: Reference identifier
  * filestoreid: File store identifier
  * sheetname: Name of the sheet
  * rownumber: Row number in the sheet (0-indexed, excluding header)
  * rowjson: Parsed row data as JSON object (column name → value mapping)
  * createdby: User UUID who created the record
  * createdtime: Timestamp when created
  * deletetime: Timestamp when marked for deletion (null if not deleted)
* TotalCount: Total number of records matching the search criteria (without pagination).
*   SheetWiseCounts: Array of sheet-wise record counts (only populated when searching by referenceId and fileStoreId without sheetName). Each object contains:

    * sheetname: Name of the sheet
    * recordcount: Number of records in that sheet



#### Response Example

```
{
  "ResponseInfo": {
    "apiId": "excel-ingestion-api",
    "ver": "1.0",
    "ts": 1672531200000,
    "status": "successful"
  },
  "SheetDataDetails": {
    "Data": [
      {
        "tenantid": "mz",
        "referenceid": "campaign-123",
        "filestoreid": "filestore-id-abc-456",
        "sheetname": "HCM_ADMIN_CONSOLE_BOUNDARY_DATA",
        "rownumber": 0,
        "rowjson": {
          "code": "BND001",
          "name": "Province A",
          "type": "Province",
          "parent": "",
          "isRoot": true
        },
        "createdby": "user-uuid-123",
        "createdtime": 1672531500000,
        "deletetime": null
      },
      {
        "tenantid": "mz",
        "referenceid": "campaign-123",
        "filestoreid": "filestore-id-abc-456",
        "sheetname": "HCM_ADMIN_CONSOLE_BOUNDARY_DATA",
        "rownumber": 1,
        "rowjson": {
          "code": "BND002",
          "name": "District B",
          "type": "District",
          "parent": "BND001",
          "isRoot": false
        },
        "createdby": "user-uuid-123",
        "createdtime": 1672531500000,
        "deletetime": null
      },
      {
        "tenantid": "mz",
        "referenceid": "campaign-123",
        "filestoreid": "filestore-id-abc-456",
        "sheetname": "HCM_ADMIN_CONSOLE_BOUNDARY_DATA",
        "rownumber": 2,
        "rowjson": {
          "code": "BND003",
          "name": "Administrative Post C",
          "type": "AdministrativePost",
          "parent": "BND002",
          "isRoot": false
        },
        "createdby": "user-uuid-123",
        "createdtime": 1672531500000,
        "deletetime": null
      }
    ],
    "TotalCount": 3,
    "SheetWiseCounts": null
  }
}
```

<br>
