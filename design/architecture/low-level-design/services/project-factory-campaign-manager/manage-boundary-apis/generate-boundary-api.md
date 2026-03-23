# Generate Boundary API

## **Overview**

**Base URL:** project-factory/v1/

**Endpoint:** /data/\_generate

**Method:** POST

## **Request Structure**

**Body Parameters:**

* **RequestInfo:** Object containing RequestInfo
* **Query Parameters:**
  * **tenantId:** Tenant
  * **type:** Type of Resource (e.g., boundary)
  * **forceUpdate:** Boolean type (either true or false)
  * **hierarchyType:** Name of Boundary Hierarchy
  * **campaignId:** CampaignId

## **Response Structure**

**Success Response:**

```json
{
   "ResponseInfo": {
       "apiId": "egov-bff",
       "ver": "0.0.1",
       "ts": 1716878176955,
       "status": "successful",
       "desc": "new-response"
   },
   "GeneratedResource": [
       {
           "id": "5ef5547e-414f-4164-9c12-644716e4fa71",
           "fileStoreid": null,
           "type": "boundary",
           "status": "inprogress",
           "hierarchyType": "ADMIN",
           "tenantId": "mz",
           "auditDetails": {
               "lastModifiedTime": 1716878176947,
               "createdTime": 1716878176947,
               "createdBy": "867ba408-1b82-4746-8274-eb916e625fea",
               "lastModifiedBy": "867ba408-1b82-4746-8274-eb916e625fea"
           },
           "additionalDetails": {
               "Filters": null
           },
           "count": null
       }
   ]
}
```

## **Flow**

1. **Client Initiates Request:**
   * The client initiates a dataGenerate request to the Project Factory Service.
2. **Validation of Request:**
   * Schema Validation: Validate against generateRequestSchema.
   * Tenant ID Validation: Ensure tenantId matches in query and RequestInfo.userInfo.
   * Force Update: Default to "false" if missing.
   * Hierarchy Type Validation: Validate hierarchyType for the tenantId.
3. **Processing of Generate Request:**
   * **Fetch Data from DB:**
     * Retrieve data using getResponseFromDb(request).
   * **Modify Response Data:**
     * Modify the fetched data with getModifiedResponse(responseData).
   * **Generate New Entry:**
     * Create a new entry with getNewEntryResponse(request).
   * **Expire Old Data:**
     * Update the status of old data to expired using getOldEntryResponse(modifiedResponse, request).
   * **Persist Data Changes:**
     * Call updateAndPersistGenerateRequest(newEntryResponse, oldEntryResponse, responseData, request).
       * **Purpose:**
         * If forceUpdate is true and data exists: Mark existing data as expired and create new data.
         * No data exists, or force update is true: Generate new data.
         * If forceUpdate is false and data exists: Return the old data.
4. **Boundary Data Processing:**
   * **Generate new Boundary Data:**
     * Fetch Boundary Relationships.
     * If no boundary is found, generate an empty boundary sheet.
     * Fetch Filters from CampaignId and generate Boundary Data based on those Filters.
       * If Filters is null, it will generate the whole Boundary Data.
   * After the Boundary Sheet has been generated, append the ReadMeSheet.
   * Generate different tabs based on any boundary level configured (here District).
5. **Generating  Different Boundary Templates  based on Campaign Type**

* Fetch configurable columns from mdms present for each campaign type from schema -_<mark style="color:blue;">\[HCM-ADMIN-CONSOLE.adminSchema]</mark>_.
* Here is a sample data from the given schema, having configurable columns for Campaign SMC-

```
 "mdms": [
        {
            "id": "536f6de8-8c90-4631-b401-5a3beabf4893",
            "tenantId": "mz",
            "schemaCode": "HCM-ADMIN-CONSOLE.adminSchema",
            "uniqueIdentifier": "boundary.MR-DN",
            "data": {
                "title": "boundary",
                "$schema": "http://json-schema.org/draft-07/schema#",
                "properties": {
                    "numberProperties": [
                        {
                            "name": "HCM_ADMIN_CONSOLE_TARGET_SMC_AGE_3_TO_11",
                            "type": "number",
                            "isRequired": true,
                            "description": "Target at village level - Age 3 to 11 Months (Mandatory and to be entered by the user)",
                            "orderNumber": 2
                        },
                        {
                            "name": "HCM_ADMIN_CONSOLE_TARGET_SMC_AGE_12_TO_59",
                            "type": "number",
                            "isRequired": true,
                            "description": "Target at village level - Age 12 to 59 Months (Mandatory and to be entered by the user)",
                            "orderNumber": 3
                        }
                    ],
                    "stringProperties": [
                        {
                            "name": "HCM_ADMIN_CONSOLE_BOUNDARY_CODE",
                            "type": "string",
                            "isRequired": true,
                            "description": "Boundary Code",
                            "orderNumber": 1,
                            "freezeColumn": true
                        }
                    ]
                },
                "campaignType": "MR-DN"
            },
            "isActive": true,
            "auditDetails": {
                "createdBy": "63a21269-d40d-4c26-878f-4f4486b1f44b",
                "lastModifiedBy": "63a21269-d40d-4c26-878f-4f4486b1f44b",
                "createdTime": 1718171965428,
                "lastModifiedTime": 1718171965428
            }
        }
    ]
```

1. **Handle Error:**
   * Update the status to failed, add error details, log the error, and produce a message to the update topic.
2. **Downloading the generated boundary template through /data/\_generate API:**
   * One can get the filestoreId through the /data/\_download API, which will fetch from the database using the ID from the response of /data/\_generate API.

{% hint style="info" %}
**Note:** The downloaded Template will have one ReadMe sheet, one Boundary Data Tab, and all other tabs on several unique districts (or whichever level is configured).
{% endhint %}

