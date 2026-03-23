# Generate API

### Endpoint

* Endpoint: /boundary-service/v1/\_generate
* Method: POST

### Request Structure

Query Parameters:

| Parameter     | Type    | Required | Description                                                              |
| ------------- | ------- | -------- | ------------------------------------------------------------------------ |
| hierarchyType | String  | Yes      | Type of hierarchy (e.g., ADMIN, MICROPLAN)                               |
| tenantId      | String  | Yes      | Tenant identifier (e.g., mz, dev)                                        |
| forceUpdate   | Boolean | No       | If true, expires previous records and generates new file. Default: false |
| referenceId   | String  | No       | Reference identifier (e.g., campaign ID, project ID)                     |

Body Parameters:

| Parameter            | Type   | Required | Description                                                                         |
| -------------------- | ------ | -------- | ----------------------------------------------------------------------------------- |
| RequestInfo          | Object | Yes      | Object containing request information including userInfo and authentication details |
| RequestInfo.userInfo | Object | Yes      | User information for audit tracking                                                 |
| RequestInfo.msgId    | String | Yes      | Message ID with locale (format: timestamp                                           |

### Request Example

```
{
    "RequestInfo": {
      "apiId": "Rainmaker",
      "authToken": "{{authToken}}",
      "userInfo": {
        "id": 34602,
        "uuid": "dd885ccb-f91d-4bf2-adb8-46fb66217797",
        "userName": "ADMIN",
        "name": "Admin User",
        "mobileNumber": "9876543210",
        "emailId": "admin@egovernments.org",
        "locale": null,
        "type": "EMPLOYEE",
        "roles": [
          {
            "name": "Campaign Managers",
            "code": "CAMPAIGN_MANAGER",
            "tenantId": "mz"
          }
        ],
        "active": true,
        "tenantId": "mz",
        "permanentCity": null
      },
      "msgId": "1761036073664|en_MZ",
      "plainAccessRequest": {}
    }
  }
```

```
Query String:
  ?hierarchyType=ADMIN&tenantId=mz&forceUpdate=true&referenceId=CAMP-001
```

### Response Structure

Success Response (HTTP 200):

| Field                                            | Type          | Description                                            |
| ------------------------------------------------ | ------------- | ------------------------------------------------------ |
| ResponseInfo                                     | Object        | Response metadata                                      |
| ResourceDetails                                  | Array         | Array of generated resource objects                    |
| ResourceDetails\[].id                            | String (UUID) | Unique identifier for the generation request           |
| ResourceDetails\[].tenantId                      | String        | Tenant identifier                                      |
| ResourceDetails\[].hierarchyType                 | String        | Type of hierarchy                                      |
| ResourceDetails\[].fileStoreid                   | String        | File store identifier (null when in\_progress)         |
| ResourceDetails\[].status                        | String        | Current status: inprogress, completed, failed, expired |
| ResourceDetails\[].count                         | Integer       | Number of boundary records in the generated file       |
| ResourceDetails\[].locale                        | String        | Locale for the generated file (extracted from msgId)   |
| ResourceDetails\[].referenceId                   | String        | Reference identifier if provided                       |
| ResourceDetails\[].auditDetails                  | Object        | Audit information                                      |
| ResourceDetails\[].auditDetails.createdBy        | String (UUID) | User who created the request                           |
| ResourceDetails\[].auditDetails.createdTime      | Long          | Creation timestamp (epoch milliseconds)                |
| ResourceDetails\[].auditDetails.lastModifiedBy   | String (UUID) | User who last modified                                 |
| ResourceDetails\[].auditDetails.lastModifiedTime | Long          | Last modification timestamp                            |
| ResourceDetails\[].additionalDetails             | Object        | Additional metadata including errors                   |
| ResourceDetails\[].additionalDetails.currentFlow | String        | Flow type: auto or manual                              |
| ResourceDetails\[].additionalDetails.error       | Object        | Error details (present only if                         |

### Response Example

```
{
    "ResponseInfo": {
      "apiId": "egov-bff",
      "ver": "0.0.1",
      "ts": 1761036103664,
      "status": "successful",
      "desc": "new-response"
    },
    "ResourceDetails": [
      {
        "id": "550e8400-e29b-41d4-a716-446655440000",
        "tenantId": "mz",
        "hierarchyType": "ADMIN",
        "fileStoreid": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
        "status": "completed",
        "count": 150,
        "locale": "en_MZ",
        "referenceId": "CAMP-001",
        "auditDetails": {
          "createdBy": "dd885ccb-f91d-4bf2-adb8-46fb66217797",
          "createdTime": 1761036073664,
          "lastModifiedBy": "dd885ccb-f91d-4bf2-adb8-46fb66217797",
          "lastModifiedTime": 1761036103664
        },
        "additionalDetails": {
          "currentFlow": "auto"
        }
      }
    ]
  }

```

### Flow

1. Client Initiates Request

The client sends a \_generate request to the Boundary Management service with query parameters (hierarchyType, tenantId, forceUpdate).

2. Validation of Request

The service validates the request:

* Validates hierarchyType is provided
* Validates tenantId is provided
* Validates RequestInfo structure
* Validates user authentication

3. Search for Existing Records

Query the database for existing generated resources with:

* Same tenantId
* Same hierarchyType
* Same locale (extracted from RequestInfo.msgId)
* Same referenceId (if provided)
* Status: completed, inprogress, or failed

4. Preserve Current Flow

If existing records are found:

* Extract currentFlow (auto/manual) from additionalDetails
* Preserve this flow for the new generation
* Ensures consistency: once a hierarchy uses auto-generation, it continues with auto

5. Expire Previous Records (if forceUpdate = true)

If forceUpdate=true and existing records exist:

* Update all existing records with status completed to expired
* Update lastModifiedTime and lastModifiedBy
* Persist changes via Kafka update topic

6. Generate New Record or Return Existing

Case A: No existing record OR forceUpdate=true

* Generate unique UUID for new generation request
* Set initial status to inprogress
* Set fileStoreid to null
* Set audit details (createdBy, createdTime, lastModifiedBy, lastModifiedTime)
* Extract locale from RequestInfo.msgId (format: timestamp|locale)
* Add currentFlow to additionalDetails if determined from previous records
* Persist to database via Kafka create topic

Case B: Existing record found (not expired)

* Return existing record without creating new one
* Status could be: inprogress, completed, or failed

7. Start Boundary Data Generation (if new record created)

7.1 Check Redis Cache

* Cache key: boundary-management-cacheKey-${hierarchyType}
* Cache TTL: 5 minutes (300 seconds)
* If cache hit: Return cached file details
* If cache miss: Continue to step 7.2

7.2 Fetch Localization Messages

* Fetch hierarchy-specific localization (e.g., ADMIN module)
* Fetch boundary management module localization
* Merge localization maps
* Fetch French localization (fr\_${region})
* Fetch Portuguese localization (pt\_${region})

7.3 Fetch Boundary Relationship Data

* Call Boundary Service API: /boundary-service/boundary-relationship/\_search
* Parameters:
  * tenantId
  * hierarchyType
  * includeChildren: true
* Response: Hierarchical boundary tree structure

7.4 Generate Hierarchy List

* Recursively traverse boundary tree
* Generate comma-separated hierarchy paths
* Example: "Country,Province,District,Locality"

7.5 Fetch Configurable Columns

* Call MDMS v2 service for schema configuration
* Schema: HCM-ADMIN-CONSOLE.adminSchema
* Unique Identifier: boundaryManagement.all
* Extract columns: Boundary Code, French Localization, Portuguese Localization, Latitude, Longitude

7.6 Fetch Coordinates

* Extract all boundary codes from hierarchy list
* Call Boundary Entity Search API in chunks of 20
* Fetch lat/long coordinates for boundaries with Point geometry
* Build map: {boundaryCode -> \[latitude, longitude]}

7.7 Prepare Excel Data

* Create headers:
  * Hierarchy columns (localized): Country, Province, District, Locality
  * Boundary Code
  * French Localization Message
  * Portuguese Localization Message
  * Latitude
  * Longitude
* Create data rows:
  * Parse hierarchy paths
  * Localize boundary names
  * Add boundary codes
  * Add French/Portuguese translations
  * Add coordinates

7.8 Create Excel Workbook

* Create new workbook
* Add worksheet with localized tab name
* Add headers with green background color (#93C47D)
* Set column width to 40
* Freeze first row
* Add data rows

7.9 Upload to FileStore

* Convert workbook to buffer
* Create file with name: Boundary\_${hierarchyType}\_${timestamp}.xlsx
* Upload to FileStore service
* Receive fileStoreId

8. Update Status to Completed

* Set status to completed
* Set fileStoreid to received file store ID
* Set count to number of boundary records
* Update lastModifiedTime and lastModifiedBy
* Clear any error details from additionalDetails
* Persist to database via Kafka update topic

9. Cache Response (if caching enabled)

* Cache the file details in Redis
* Cache key: boundary-management-cacheKey-${hierarchyType}
* TTL: 5 minutes
* Enable cache reset on access (optional configuration)

10. Return Response to Client

* Return response with ResourceDetails array
* Status: completed (or inprogress if async processing)
* Include fileStoreId for completed generations

***

Error Handling

If any error occurs during generation:

11. Update Status to Failed

* Set status to failed
* Set fileStoreid to null
* Set count to null
* Enrich additionalDetails.error with:
  * status: HTTP status code
  * code: Error code identifier
  * description: Detailed error description
  * message: Human-readable error message
* Update lastModifiedTime and lastModifiedBy
* Persist to database via Kafka update topic

### Flow Diagram

```
 ┌─────────────┐
  │   Client    │
  └──────┬──────┘
         │
         │ POST /v1/_generate?hierarchyType=ADMIN&tenantId=mz
         │
         ▼
  ┌─────────────────────────┐
  │ Boundary Controller     │
  │ - validateRequest       │
  └──────────┬──────────────┘
             │
             ▼
  ┌─────────────────────────┐
  │ Search Existing Records │
  │ (DB Query)              │
  └──────────┬──────────────┘
             │
             ├─── Has Existing & !forceUpdate ──────┐
             │                                       │
             │                                       ▼
             │                              ┌────────────────┐
             │                              │ Return Existing│
             │                              │ Record         │
             │                              └────────────────┘
             │
             ├─── forceUpdate = true ───────┐
             │                              │
             ▼                              ▼
  ┌─────────────────────────┐    ┌─────────────────┐
  │ Preserve currentFlow    │    │ Expire Previous │
  │ from existing record    │    │ Records         │
  └──────────┬──────────────┘    └────────┬────────┘
             │                            │
             └────────────┬───────────────┘
                          │
                          ▼
             ┌─────────────────────────┐
             │ Generate New Entry      │
             │ - UUID                  │
             │ - status: inprogress    │
             │ - auditDetails          │
             │ - locale from msgId     │
             └──────────┬──────────────┘
                        │
                        ▼
             ┌─────────────────────────┐
             │ Persist to Kafka        │
             │ (CREATE topic)          │
             └──────────┬──────────────┘
                        │
                        ▼
             ┌─────────────────────────┐
             │ Check Redis Cache       │
             └──────────┬──────────────┘
                        │
           ┌────────────┴────────────┐
           │                         │
      Cache Hit                 Cache Miss
           │                         │
           ▼                         ▼
  ┌─────────────────┐    ┌─────────────────────────┐
  │ Return Cached   │    │ Fetch Boundary Data     │
  │ File Details    │    │ - Localization          │
  └────────┬────────┘    │ - Boundary Relationships│
           │             │ - Coordinates           │
           │             └──────────┬──────────────┘
           │                        │
           │                        ▼
           │             ┌─────────────────────────┐
           │             │ Generate Excel          │
           │             │ - Create workbook       │
           │             │ - Add data & headers    │
           │             └──────────┬──────────────┘
           │                        │
           │                        ▼
           │             ┌─────────────────────────┐
           │             │ Upload to FileStore     │
           │             └──────────┬──────────────┘
           │                        │
           │                        ▼
           │             ┌─────────────────────────┐
           │             │ Cache in Redis          │
           │             │ (TTL: 5 min)            │
           │             └──────────┬──────────────┘
           │                        │
           └────────────┬───────────┘
                        │
                        ▼
             ┌─────────────────────────┐
             │ Update Status: completed│
             │ - Set fileStoreId       │
             │ - Set count             │
             └──────────┬──────────────┘
                        │
                        ▼
             ┌─────────────────────────┐
             │ Persist to Kafka        │
             │ (UPDATE topic)          │
             └──────────┬──────────────┘
                        │
                        ▼
             ┌─────────────────────────┐
             │ Return Response         │
             │ (ResourceDetails)       │
             └─────────────────────────┘

           Error Flow:
                        │
                        ▼
             ┌─────────────────────────┐
             │ Update Status: failed   │
             │ - Set error details     │
             │ - fileStoreid: null     │
             └──────────┬──────────────┘
                        │
                        ▼
             ┌─────────────────────────┐
             │ Persist to Kafka        │
             │ (UPDATE topic)          │
             └──────────┬──────────────┘
                        │
                        ▼
             ┌─────────────────────────┐
             │ Return Error Response   │
             └─────────────────────────┘

```

### Status States

```
| Status     | Description                                                                                        | fileStoreId | count             |
  |------------|----------------------------------------------------------------------------------------------------|-------------|-------------------|
  | inprogress | Initial state when generation starts. Boundary data is being fetched and Excel is being generated. | null        | null              |
  | completed  | Excel file successfully generated and uploaded to FileStore. File is ready for download.           | Valid UUID  | Number of records |
  | failed     | Generation encountered an error. Error details in additionalDetails.error.                         | null        | null              |
  | expired    | Previous completed record marked as expired when new generation requested with forceUpdate=true.   | Previous ID | Previous count    |

```

### Generation Configuration

```
{
    "schemaCode": "HCM-ADMIN-CONSOLE.adminSchema",
    "uniqueIdentifier": "boundaryManagement.all",
    "data": {
      "properties": {
        "stringProperties": [
          {
            "name": "HCM_ADMIN_CONSOLE_BOUNDARY_CODE",
            "isRequired": true,
            "isUnique": true,
            "orderNumber": 1
          },
          {
            "name": "HCM_ADMIN_CONSOLE_FRENCH_LOCALIZATION_MESSAGE",
            "isRequired": false,
            "orderNumber": 2
          },
          {
            "name": "HCM_ADMIN_CONSOLE_PORTUGESE_LOCALIZATION_MESSAGE",
            "isRequired": false,
            "orderNumber": 3
          }
        ],
        "numberProperties": [
          {
            "name": "HCM_ADMIN_CONSOLE_LAT",
            "isRequired": false,
            "orderNumber": 4
          },
          {
            "name": "HCM_ADMIN_CONSOLE_LONG",
            "isRequired": false,
            "orderNumber": 5
          }
        ]
      }
    }
  }
```

### Download Generated File

After successful generation, use the `/v1/_generate-search` endpoint to download:

GET `/boundary-service/v1/_generate-search?tenantId=mz&hierarchyType=ADMIN`

This returns the latest completed generated resource with the fileStoreId that can be used to download the Excel file from FileStore service.
