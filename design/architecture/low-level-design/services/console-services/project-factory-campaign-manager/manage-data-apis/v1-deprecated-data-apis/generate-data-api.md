---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/low-level-design/services/project-factory-campaign-manager/manage-data-apis/v1-deprecated-data-apis/generate-data-api
---

# Generate Data API

## Endpoint <a href="#generate-data-api" id="generate-data-api"></a>

* **Endpoint**: /data/\_generate
* **Method**: POST

## **Request Structure** <a href="#request-structure-2" id="request-structure-2"></a>

* RequestInfo: Object containing request information.
* Query Parameters:
  * type: Type of the resource for which data needs to be generated.
  * tenantId: Tenant identifier.
  * hierarchyType: Type of hierarchy.
  * forceUpdate: (Optional) Boolean indicating whether to force update existing data.

## **Response Structure** <a href="#response-structure-1" id="response-structure-1"></a>

* ResponseInfo: Object containing response information.
* GeneratedResource: Array containing the details object of the generated resource.

## **Flow** <a href="#flow-2" id="flow-2"></a>

1. **Client Request**: The client sends a POST request to /v1/data/\_generate.
2. **Request Validation**: After receiving the request, the server validates the request structure and parameters.
3. **Generate Data Process**:
   * **Validation**: The server validates the generated request.
   * **Data Processing**:
     * **Fetch Data**: Fetches existing data from the database.
     * **Modify Data**: Modify the retrieved data as necessary.
     * **Generate New ID**: Generates a new random ID and sets the file store ID to null.
     * **Expire Old Data**: Marks existing data status as expired.
     * **Generate New Data**: Generates new data based on the request parameters.
     * **Update and Persist**: Updates and persists the generated request along with the new data.
   * **Force Update Logic**:
     * If the forceUpdate parameter is set to true:
       * **Search and Update**: Searches for existing data of the specified type and updates the existing data information.
     * If the forceUpdate parameter is not provided or set to false:
       * **Fetch Existing Data**: Retrieves already persisted data from the database of the specified type.
4. **Response Creation**: After processing the request, the server creates a response containing the details of the generated resource.
5. **Response Dispatch**: The server sends the generated response back to the client.
6. **Error Handling**: If errors occur, generate an error response and send it.

#### Flow Diagram <a href="#flow-diagram-2" id="flow-diagram-2"></a>

<figure><img src="https://docs.digit.org/~gitbook/image?url=https%3A%2F%2Flh7-us.googleusercontent.com%2FN1GE1Mhw8eGYRKrMT8Us0ygoneV3SgMrsCD2pLrOWI92nnx81A59TOpakrREGOHwc1JOfwOJQSiLN1QbLGFB15ds2NNEN7oV6_oYSy14zEvhj8Sm6kBWEtPzFZI4sedls-oqY0mkJmuCrVl1mzhYTtw&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=9a4d465f&#x26;sv=2" alt=""><figcaption></figcaption></figure>

#### Data to Sheet Parsing Logic <a href="#data-to-sheet-parsing-logic" id="data-to-sheet-parsing-logic"></a>

1. **Fetch Required Columns from MDMS:**
   * Use `callMdmsData` to get type schema columns in the correct order.
2. **Define Headers:**
   * MDMS schema required columns are headers and ensures column orders.
3. **Localise Headers:**
   * Use `getLocalizedHeaders` with `localizationMap`.
4. **Localise Sheet Name:**
   * Use `getLocalizedName` with `localizationMap` and generate a sheet.

#### Adding a New Column to the Generated Sheet <a href="#adding-a-new-column-to-the-generated-sheet" id="adding-a-new-column-to-the-generated-sheet"></a>

To add a new column to the Generated sheet, follow these steps:

1. **Search Schema Details**
   * Locate the type schema from the `HCM-ADMIN-CONSOLE.adminSchema` schema in the workbench.
2. **Identify Column Type**
   * Determine the column type based on the properties defined in the schema:
     * `stringProperties` for string-based columns.
     * `numberProperties` for numeric-based columns.
     * `enumProperties` for enumerated columns.
3. **Define New Column**
   * Add the new column to the schema under the appropriate properties section:
     * **String Column**: Include attributes such as `name`, `type`, `maxLength`, `minLength`, `isUnique`, `isRequired`, `description`, and `orderNumber`.
     * **Number Column**: Include attributes such as `name`, `type`, `maximum`, `minimum`, `isRequired`, `description`, `orderNumber`, and `errorMessage`.
     * **Enum Column**: Include attributes such as `name`, `enum`, `isRequired`, `description`, and `orderNumber`.
4. **Ensure Column Uniqueness**
   * Ensure that the `isUnique` property is correctly set for string columns to enforce uniqueness.
5. **Column Visibility (Future Implementation)**
   * Note that `hideColumn` and `freezeColumn` features will be implemented in the next version.

**Sheet Data Validation:**

This process is sufficient for validating the new column in the generated sheet.

#### Column Change Reflection in APIs <a href="#column-change-reflection-in-apis" id="column-change-reflection-in-apis"></a>

If there's a need to reflect the column in APIs, follow these additional steps:

1. **Update `createAndSearch.ts` File**
   * Modify the `createAndSearch.ts` file under the defined type `parseLogic` object.
   * Integrate the new column into the appropriate data structures used for API operations.
   * Example :
     * **sheetColumn:** A
     * **sheetColumnName:** HCM\_ADMIN\_CONSOLE\_FACILITY\_CODE
     * **resultantPath:** id
     * **type:** string
     * **Mapping:** Data from column A (HCM\_ADMIN\_CONSOLE\_FACILITY\_CODE) in the sheet will be mapped to `id` in the API data.

By following these steps, you can successfully add and validate a new column in the generated sheet and ensure its reflection in the associated APIs.

#### Template Properties <a href="#template-properties" id="template-properties"></a>

**General Rules**

* **Locked Headers:** The headers in the templates for each data type (user, facility, target) are locked and cannot be changed.
* **Sheet Protection:** Certain sheets within the templates will have specific locked areas to ensure data integrity.
* **README Sheet:** Each type of template includes a README sheet which is read-only and locked.

**Target Template**

* **Editable Columns:** You can only modify the 'Target' column. All other columns are locked and cannot be edited.

**Facility Template**

* **Adding Rows:** You are allowed to add new rows to create new facilities.
* **Editable Columns:** You can modify the "Boundary Code" and 'Usage' columns.
* **Locked Sheets:** The boundary data sheet within the facility template is locked and cannot be modified.
* **Dropdown Columns:** The following columns are dropdowns:
  * Facility Type
  * Facility Status
  * Facility Usage
* **Facility Usage:** Facility usage can be 'Active' or 'Inactive'. Active facilities are used in the campaign and require a boundary code to map.

**User Template**

* **Adding Rows:** You are allowed to add new rows.
* **Locked Sheets:** The boundary data sheet within the user template is locked and cannot be modified.
* **Dropdown Columns:** The following columns are dropdowns:
  * Role
  * Employment Type

**Data for Dropdowns**

* The data for the dropdown columns comes from the `mdms` (Master Data Management System) under the `adminSchema` master.
