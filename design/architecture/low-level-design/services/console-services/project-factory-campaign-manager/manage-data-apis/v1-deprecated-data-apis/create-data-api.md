---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/low-level-design/services/project-factory-campaign-manager/manage-data-apis/v1-deprecated-data-apis/create-data-api
---

# Create Data API

## Endpoint <a href="#endpoint" id="endpoint"></a>

* **Endpoint**: /data/\_create
* **Method**: POST

## **Request Structure** <a href="#request-structure" id="request-structure"></a>

* **Body Parameters**:
  * RequestInfo: Object containing request information.
  * Resource Details: Object containing the details of the resource to be created or validated.
    * type: Type of resource (boundary, facility, user, boundaryWithTarget).
    * tenantId: Tenant identifier.
    * fileStoreId: File store identifier.
    * action: Action type (create or validate).
    * hierarchyType: Type of hierarchy.
    * campaignId: Campaign identifier.
    * additionalDetails: Additional details object (optional).

## **Response Structure** <a href="#response-structure" id="response-structure"></a>

*   **Success Response**:

    \- ResponseInfo: Object containing response information.

    \- ResourceDetails: Array containing the detail objects of the created or validated resource.

## **Flow** <a href="#flow" id="flow"></a>

1. **Client Initiates Request**: The client sends a createData request to the Project Factory service.
2. **Validation of Request**: The Project Factory service validates the request schema and the provided resource details.
3. **Processing the Request**:
   * If action is 'create':
     * Enrich resource details, set status to "data-accepted", and persist in the database.
     * Further creation process happens in the background.
     * After successful creation, set the status to 'completed' and persist resource details in the database.
   * If action is 'validate':
     * Enrich resource details, set the status to "validation-started", and persist in the database.
     * Further creation process happens in the background.
     * If file data is invalid, set the status to 'invalid' and persist in the database.
     * After successful creation, set the status to 'completed' and persist resource details in the database.
   * **Fail case**: If validation or creation fails, set the status to 'failed' and persist in the database with the error cause in additional details.
4. **Response**: The Project Factory service sends the response back to the client containing the resource details and status.

## Flow Diagram <a href="#flow-diagram" id="flow-diagram"></a>

<figure><img src="https://docs.digit.org/~gitbook/image?url=https%3A%2F%2Flh7-us.googleusercontent.com%2FIZhs_77mFsrxKrB7yekJEFU2n8fXneuZSRlHTcTN7DPrpQHkdb_izZaQeWkwRod8wMmU_al9gsZwyH9bXMM4AOhhTWEwG4960vqRPqgUYFhZmsQ3Ldeh1zNs9D8pE6yvdx-5amgsImDOtIlaynCj-BQ&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=34cd4c6a&#x26;sv=2" alt=""><figcaption></figcaption></figure>

**Parsing Logic from sheet**

The getSheetData function retrieves and processes data from an Excel sheet, validating the structure according to the configuration provided in createAndSearchConfig. The key part of this process is the parseArrayConfig.parseLogic configuration, which specifies how to parse and validate the columns in the sheet. Here's a detailed explanation of how the function works, including the parsing logic:

**Parsing Logic Using parseArrayConfig.parseLogic**

The parseArrayConfig.parseLogic configuration specifies how each column in the sheet should be processed. Here's how the parsing logic works:

```
parseLogic: [
    {
        sheetColumn: "A",
        sheetColumnName: "HCM_ADMIN_CONSOLE_FACILITY_CODE",
        resultantPath: "id",
        type: "string"
    },
    {
        sheetColumn: "B",
        sheetColumnName: "HCM_ADMIN_CONSOLE_FACILITY_NAME",
        resultantPath: "name",
        type: "string"
    },
    {
        sheetColumn: "C",
        sheetColumnName: "HCM_ADMIN_CONSOLE_FACILITY_TYPE",
        resultantPath: "usage",
        type: "string"
    },
    {
        sheetColumn: "D",
        sheetColumnName: "HCM_ADMIN_CONSOLE_FACILITY_STATUS",
        resultantPath: "isPermanent",
        type: "boolean",
        conversionCondition: {
            "Permanent": "true",
            "Temporary": ""
        }
    },
    {
        sheetColumn: "E",
        sheetColumnName: "HCM_ADMIN_CONSOLE_FACILITY_CAPACITY",
        resultantPath: "storageCapacity",
        type: "number"
    },
    {
        sheetColumn: "F",
        sheetColumnName: "HCM_ADMIN_CONSOLE_BOUNDARY_CODE_MANDATORY"
    }
]
```

### Column Configuration <a href="#column-configuration" id="column-configuration"></a>

Each column configuration specifies:

* `sheetColumn`: The column letter in the sheet.
* `sheetColumnName`: The expected name of the column in the sheet.
* `resultantPath`: The path where the value will be stored in the resultant JSON.
* `type`: The expected type of the value (e.g., string, number, or boolean).
* `conversionCondition`: Optional conditions for converting values.

**Validating Column Names**

During the validation step, the function checks that the first-row value matches the expected column name.

**Processing Rows**

When mapping the rows to JSON, the function uses the `resultantPath` to place the values in the correct location in the JSON object. It converts values according to the specified `type` and `conversionCondition`.

**Example Conversion**

For a column configuration with `type: "boolean"` and `conversionCondition`, the function would convert "Permanent" to true and "Temporary" to an empty string.

```
{
    "sheetColumn": "D",
    "sheetColumnName": "HCM_ADMIN_CONSOLE_FACILITY_STATUS",
    "resultantPath": "isPermanent",
    "type": "boolean",
    "conversionCondition": {
        "Permanent": "true",
        "Temporary": ""
    }
}
```

In summary, the getSheetData function retrieves and processes data from an Excel sheet, validating the structure and content according to the createAndSearchConfig configuration. The parseArrayConfig.parseLogic configuration specifies how each column should be validated and processed into the resultant JSON format.
