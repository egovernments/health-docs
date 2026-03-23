---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/low-level-design/services/project-factory-campaign-manager/manage-data-apis
---

# Manage Data APIs

This section of the documentation details APIs for creating, searching, generating, and downloading data, including request/response structures, flows, and error handling.\
\
Campaign Creation V2 Flow – Documentation

### Overview

The Campaign Creation V2 flow improves upon the earlier V1 implementation by introducing a type-aware, config-driven, and extensible architecture for handling Excel-based data uploads.

This change simplifies how Excel sheets are parsed, validated, transformed, and annotated, making the flow scalable and easier to maintain.

***

### V1 vs V2 – Key Differences

| Feature            | V1 (/v1/data/\_create) | V2 (/v2/data/\_process)                         |
| ------------------ | ---------------------- | ----------------------------------------------- |
| API Endpoint       | /v1/data/\_create      | /v2/data/\_process                              |
| Sheet Type Support | Embedded in sheet      | Explicit in API payload (type)                  |
| Validation Support | Manual/Inline          | Automated via MDMS config                       |
| Flexibility        | Rigid, fixed structure | Modular, type-based flow                        |
| Extensibility      | Limited                | Easily extendable by adding type-specific logic |

***

### 🛠️ API: POST /v2/data/\_process

#### 🔹 Purpose

Processes uploaded Excel files for validation-type sheets.\
This API is exposed to the client UI through role-action mapping.

#### 🔹 Supported Types

| Category   | Types                                                  |
| ---------- | ------------------------------------------------------ |
| Data Entry | user, facility, boundary                               |
| Validation | userValidation, facilityValidation, boundaryValidation |

#### 🔹 Sample Payload

```
{
  "ResourceDetails": {
    "tenantId": "dev",
    "type": "userValidation",
    "fileStoreId": "{{fileId}}",
    "hierarchyType": "NEWTEST00222",
    "additionalDetails": {},
    "campaignId": "5c845eb8-f8b2-43d0-a301-8e24692499f1"
  },
  "RequestInfo": {
    "apiId": "Rainmaker",
    "authToken": "{{Auth}}",
    "userInfo": {
      "id": 1052,
      "uuid": "8b110055-330f-4e7b-b4c0-f618f29b9d47"
    }
  }
}
```

#### 🔹 Processing Behavior

* &#x20;Sheet Parsing: Extracts data from each sheet using configured schema.<br>
* &#x20;Data Transformation: Applies field-level or row-level transformations (e.g., date parsing, ID lookup).<br>
* &#x20;Validation: Enforces rules defined in MDMS.<br>
* &#x20;Error Annotation: Errors are annotated row-wise and can be returned in response or in the processed Excel file.<br>

***

### 🔄 API: POST /v2/data/\_process-any

#### 🔹 Purpose

Processes any sheet type (both validation and data entry).

{% hint style="danger" %}
&#x20;Internal Use Only – this API is not exposed via role-action mapping. It is used internally by services like project-factory-service.
{% endhint %}

🔹 Differences from /v2/data/\_process

| Feature         | /v2/data/\_process       | /v2/data/\_process-any            |
| --------------- | ------------------------ | --------------------------------- |
| Scope           | Validation-only          | All types (data + validation)     |
| Use Case        | UI pre-submission checks | Backend ingestion, internal flows |
| Config Handling | Strict type filtering    | Dynamic resolution based on type  |
| Role Access     | ✅ Yes                    | ❌ No (internal only)              |
| Intended Caller | Client (UI)              | Internal services                 |

#### 🔹 Sample Payload

Same structure as /v2/data/\_process, e.g.,

```
{
  "ResourceDetails": {
    "tenantId": "dev",
    "type": "facility",
    "fileStoreId": "{{fileId}}",
    "hierarchyType": "NEWTEST00222",
    "additionalDetails": {},
    "campaignId": "5c845eb8-f8b2-43d0-a301-8e24692499f1"
  },
  "RequestInfo": {
    "apiId": "Rainmaker",
    "authToken": "{{Auth}}",
    "userInfo": {
      "id": 1052,
      "uuid": "8b110055-330f-4e7b-b4c0-f618f29b9d47"
    }
  }

```

***

### ✅ When to Use Which API?

| Scenario                          | Recommended API        |
| --------------------------------- | ---------------------- |
| Validate uploaded sheet via UI    | /v2/data/\_process     |
| Internal data ingestion (backend) | /v2/data/\_process-any |

***

### 🔐 Role Access Mapping

| API Endpoint           | Role Mapping | Intended Caller      |
| ---------------------- | ------------ | -------------------- |
| /v2/data/\_process     | ✅ Yes        | UI / client-facing   |
| /v2/data/\_process-any | ❌ No         | Internal service use |

***

### 🧠 Internal Flow – How Processing Works

The V2 system uses a dynamic, type-based processing mechanism to ensure clean separation of concerns and better maintainability.

#### 🔧 Step 1: Type-Based Class Resolution

The system uses the type field in the request to determine the processing class:

const className = \`${ResourceDetails?.type}-processClass\`;

This maps to a file like

processFlowClasses/userValidation-processClass.ts

processFlowClasses/facility-processClass.ts

#### 🔄 Step 2: Dynamic Class Import and Execution

const { TemplateClass } = await import(classFilePath);

const sheetMap = await TemplateClass.process(ResourceDetails, wholeSheetData, localizationMap);

Each class implements a static process() method that:

* Accepts the parsed sheet data
* Performs transformation + validation
* Returns a SheetMap object with data, errors, and annotations

#### 🧩 Inside Each Type Class

Each class (e.g., userValidation-processClass) encapsulates all logic for that type:

* Data cleanup or enrichment
* Business rule validation
* Conditional field logic
* Return of structured, annotated sheet data

***

### 🌟 Why This Approach?

| Feature                  | Benefit                                                    |
| ------------------------ | ---------------------------------------------------------- |
| 🔌 Low Coupling          | Each type is self-contained – changes don't affect others  |
| 🔧 Easily Extendable     | Adding a new type is as simple as creating a new class     |
| 🧼 Clean Architecture    | Sheet logic lives in its own file, not the main service    |
| ⚙️ Config-Driven         | Sheet schema, headers, validation rules all come from MDMS |
| 🧑‍💻 Developer Friendly | Developers only need to work on their type-specific class  |

***

\
\
<br>

## 📄 Campaign Template Generation V2 Flow – Documentation

***

### 🧾 Overview

The Template Generation V2 flow is an upgrade over the earlier /v1/data/\_generate implementation. It enables a loosely coupled, type-driven, and config-based Excel template generation system, ensuring better maintainability and extensibility.

The legacy endpoint:

http

POST /v1/data/\_generate<br>

has now been replaced with:

http

POST /v2/data/\_generate

<br>

***

### 🔁 V1 vs V2 – Key Differences

| Feature            | V1 (/v1/data/\_generate) | V2 (/v2/data/\_generate)         |
| ------------------ | ------------------------ | -------------------------------- |
| API Endpoint       | /v1/data/\_generate      | /v2/data/\_generate              |
| Sheet Type Support | Embedded logic           | Passed via type query param      |
| Logic Coupling     | Tightly coupled          | Type-based, dynamic classes      |
| Extensibility      | Hard to extend           | Add new types via config + class |

⚙️ Earlier most things were hardcoded.\
Now, \~80% is config-driven via MDMS or file-based config, and \~20% uses dynamic functions for specialized transformation logic.

***

### 🛠️ API: POST /v2/data/\_generate

#### 🔹 Purpose

Generates Excel templates for campaign resource types such as user, facility, boundary, etc., using MDMS-driven config and dynamic logic. UI integrates with this endpoint to export downloadable templates for upload flows.

***

#### 🔹 Required Query Parameters

| Parameter     | Type   | Description                                         |
| ------------- | ------ | --------------------------------------------------- |
| tenantId      | string | Tenant under which the campaign runs                |
| type          | string | Type of template to generate (user, facility, etc.) |
| hierarchyType | string | Hierarchy code associated with the campaign         |
| campaignId    | string | ID of the campaign                                  |

***

#### 🔹 Sample cURL Request

```json

curl --location 'http://localhost:8080/project-factory/v2/data/_generate?tenantId=dev&type=user&hierarchyType=NEWTEST00222&campaignId=5c845eb8-f8b2-43d0-a301-8e24692499f1' \
--header 'Content-Type: application/json;charset=UTF-8' \
--data '{
  "RequestInfo": {
    "apiId": "Rainmaker",
    "authToken": "your-auth-token",
    "userInfo": {
      "id": 1052,
      "uuid": "8b110055-330f-4e7b-b4c0-f618f29b9d47",
      "userName": "UATMZ",
      "name": "UATMZ",
      "mobileNumber": "8998988112",
      "type": "EMPLOYEE",
      "roles": [
        {
          "code": "CAMPAIGN_MANAGER",
          "tenantId": "mz"
        }
      ],
      "active": true,
      "tenantId": "dev"
    }
  }
}'


```

### 🔧 Internal Flow – How Generation Works

#### 🔹 Step 1: Type-Based Class Resolution

const className = \`${responseToSend?.type}-generateClass\`;

let classFilePath = path.join(\_\_dirname, '..', 'generateFlowClasses', \`${className}.js\`);<br>

if (!fs.existsSync(classFilePath)) {

&#x20; classFilePath = path.join(\_\_dirname, '..', 'generateFlowClasses', \`${className}.ts\`);

}

Expected files (per type):

* user-generateClass.ts
* facility-generateClass.ts
* boundary-generateClass.ts

***

#### 🔄 Step 2: Dynamic Import and Execution

const { TemplateClass } = await import(classFilePath);

const sheetMap = await TemplateClass.generate(ResourceDetails, localizationMap);

Returns an object with:

* ✅ Sheet Name(s)
* ✅ Header Row(s)
* ✅ Pre-filled Data (if any)
* ✅ Column metadata (dropdowns, styles, widths)

***

### 🔃 Transform Configuration (transformConfigs)

This configuration defines how API response data maps to Excel sheets and how sheet uploads map back to request payloads.

#### 🔹 Driven By

* MDMS config
* File-based transformConfigs
* Optional dynamic transformation functions (transformBulkX, transformX)

***

#### 🧩 Sample: employeeHrms

<details>

<summary>HRMS Config</summary>

```
employeeHrms: {
  metadata: { tenantId: "dev", hierarchy: "MICROPLAN" },
  fields: [
    { path: "$.user.name", source: { header: "HCM_ADMIN_CONSOLE_USER_NAME" } },
    { path: "$.user.mobileNumber", source: { header: "HCM_ADMIN_CONSOLE_USER_PHONE_NUMBER" } },
    { path: "$.user.roles[*].name", source: { header: "HCM_ADMIN_CONSOLE_USER_ROLE", splitBy: "," } },
    { path: "$.user.roles[*].code", source: { header: "HCM_ADMIN_CONSOLE_USER_ROLE", splitBy: "," } },
    { path: "$.user.roles[*].tenantId", value: "${metadata.tenantId}" },
    { path: "$.user.userName", source: { header: "UserName" } },
    { path: "$.user.password", source: { header: "Password" } },
    { path: "$.user.tenantId", value: "${metadata.tenantId}" },
    { path: "$.user.dob", value: 0 },
    {
      path: "$.employeeType",
      source: {
        header: "HCM_ADMIN_CONSOLE_USER_EMPLOYMENT_TYPE",
        transform: {
          mapping: {
            Permanent: "PERMANENT",
            Temporary: "TEMPORARY",
            "%default%": "TEMPORARY"
          }
        }
      }
    },
    {
      path: "$.jurisdictions[*].boundary",
      source: { header: "HCM_ADMIN_CONSOLE_BOUNDARY_CODE_MANDATORY", splitBy: "," }
    },
    { path: "$.jurisdictions[*].tenantId", value: "${metadata.tenantId}" },
    { path: "$.jurisdictions[*].hierarchy", value: "${metadata.hierarchy}" },
    { path: "$.jurisdictions[*].boundaryType", value: "${metadata.hierarchy}" },
    { path: "$.tenantId", value: "${metadata.tenantId}" },
    { path: "$.code", source: { header: "UserName" } }
  ],
  transFormSingle: "transformEmployee",
  transFormBulk: "transformBulkEmployee"
}
```

</details>

***

#### 🧩 Sample: Facility

{% include "../../../../../../../.gitbook/includes/expandable-code-block.md" %}

#### 🔹 Field Properties

| Property      | Description                                                          |
| ------------- | -------------------------------------------------------------------- |
| path          | JSON path in request/response                                        |
| source.header | Column name in Excel sheet                                           |
| value         | Static value or dynamic reference like ${metadata.tenantId}          |
| splitBy       | Delimiter for multi-valued fields                                    |
| transform     | Mapping to normalize values (e.g., from "Permanent" to boolean true) |

***

### 🌟 Why This Approach?

| Feature               | Benefit                                                  |
| --------------------- | -------------------------------------------------------- |
| 🔌 Low Coupling       | Per-type logic and config separation                     |
| ⚙️ Config-Driven      | Most headers, styles, mappings are externalized          |
| 🔧 Easily Extendable  | Drop in a class + config entry for new types             |
| 🧼 Clean Architecture | Controller remains generic; logic lives in type handlers |
| 🧩 Reusable Logic     | Same config powers both generation and upload parsing    |

\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
<br>

## 🔁 Retry Mechanism During Campaign Creation

***

### 🧾 Overview

The retry mechanism allows safe re-triggering of campaign creation only if the campaign is in a drafted or failed state.\
It uses the existing /v1/project-type/update API with action: "create" inside CampaignDetails.\
There is no dedicated retry API.

⚠️ Not fully idempotent\
🔁 Re-uses creation API\
✅ Works only for failed/drafted campaigns

***

### 🚫 When Retry Does NOT Work

* If the campaign is already created and active, and a retry (action: "create") is attempted, it will throw an error.\
  <br>
* Only campaigns in the following statuses are allowed to be re-processed:\
  <br>

<br>

\["drafted", "failed"]

<br>

***

### 🚀 Retry API (Same as Create)

http

CopyEdit

POST /project-factory/v1/project-type/update

<br>

#### 🔹 Required Query Params

| Parameter  | Type   | Required | Description              |
| ---------- | ------ | -------- | ------------------------ |
| tenantId   | string | ✅        | Tenant ID                |
| campaignId | string | ✅        | Campaign UUID (external) |

***

### 📦 Sample Request Body

<br>

{

&#x20; "RequestInfo": {

&#x20;   "apiId": "Rainmaker",

&#x20;   "authToken": "your-auth-token",

&#x20;   "userInfo": {

&#x20;     "uuid": "user-uuid",

&#x20;     "roles": \[{ "code": "CAMPAIGN\_MANAGER", "tenantId": "mz" }],

&#x20;     "tenantId": "dev"

&#x20;   }

&#x20; },

&#x20; "CampaignDetails": {

&#x20;   "campaignId": "5c845eb8-f8b2-43d0-a301-8e24692499f1",

&#x20;   "campaignNumber": "HCMP-CAM-00001",

&#x20;   "action": "create",

&#x20;   ...

&#x20; }

}

<br>

***

### 📊 Internal Tables Used

***

#### 📁 eg\_cm\_campaign\_data — Sheet Row Status

Tracks each data row uploaded from sheet.

| Column               | Description                    |
| -------------------- | ------------------------------ |
| campaignNumber       | Campaign ref                   |
| type                 | Template type (user, facility) |
| uniqueIdentifier     | Unique row key                 |
| data                 | Original sheet data (JSONB)    |
| uniqueIdAfterProcess | Generated ID (after success)   |
| status               | ✅ pending, completed, failed   |

<br>

export const dataRowStatuses = {

&#x20; failed: "failed",

&#x20; completed: "completed",

&#x20; pending: "pending"

}

<br>

***

#### 🔗 eg\_cm\_campaign\_mapping\_data — Mapping Status

Stores mapping status per row and boundary.

| Column                  | Description                                  |
| ----------------------- | -------------------------------------------- |
| type                    | Mapping type (userMapping, etc.)             |
| uniqueIdentifierForData | FK to campaign data                          |
| boundaryCode            | Boundary associated                          |
| mappingId               | Generated ID post-mapping                    |
| status                  | ✅ toBeMapped, mapped, toBeDeMapped, deMapped |

<br>

export const mappingStatuses = {

&#x20; toBeMapped: "toBeMapped",

&#x20; mapped: "mapped",

&#x20; toBeDeMapped: "toBeDeMapped",

&#x20; deMapped: "deMapped"

}

<br>

***

#### 🧩 eg\_cm\_campaign\_process\_data — Process Flow Status

Tracks which steps of campaign creation are done/pending/failed.

| Column      | Description                  |
| ----------- | ---------------------------- |
| processName | Each campaign step name      |
| status      | ✅ pending, completed, failed |

ts

CopyEdit

export const processStatuses = {

&#x20; failed: "failed",

&#x20; pending: "pending",

&#x20; completed: "completed"

}

<br>

**👇 Process Names**

<br>

export const allProcesses = {

&#x20; facilityCreation: "CAMPAIGN\_FACILITY\_CREATION\_PROCESS",

&#x20; userCreation: "CAMPAIGN\_USER\_CREATION\_PROCESS",

&#x20; projectCreation: "CAMPAIGN\_PROJECT\_CREATION\_PROCESS",

&#x20; facilityMapping: "CAMPAIGN\_FACILITY\_MAPPING\_PROCESS",

&#x20; userMapping: "CAMPAIGN\_USER\_MAPPING\_PROCESS",

&#x20; resourceMapping: "CAMPAIGN\_RESOURCE\_MAPPING\_PROCESS",

&#x20; userCredGeneration: "CAMPAIGN\_USER\_CRED\_GENERATION\_PROCESS"

}

<br>

***

### 🔁 Retry Logic Summary

| Step             | Logic                                                    |
| ---------------- | -------------------------------------------------------- |
| ✅ Allowed Status | Retry only works if campaign is in drafted or failed     |
| ❌ Disallowed     | Retry fails if campaign is already active or completed   |
| Sheet Rows       | Retries only rows with status pending or failed          |
| Mapping Rows     | Retries only rows with status toBeMapped or toBeDeMapped |
| Process Steps    | Retries only steps with status pending or failed         |
| Completed Work   | Skipped entirely                                         |

***

### ✅ Final Notes

* This approach provides partial re-execution based on current statuses.\
  <br>
* Helps in recovery from partial failure (e.g., during bulk upload).\
  <br>
* Prevents overwriting already created resources.\
  <br>
* Make sure to validate campaign status before retrying.\
  <br>

\
\
\
\
\
\
\
\
\
\
\
\
\
\
<br>

## 📘 Document: App Config & Localisation Setup During Campaign Creation

### 🧩 Overview

When a new campaign is created using the /project-factory/v1/project-type/create API, the backend asynchronously triggers:

* Creation of campaign-specific MDMS module configs\
  <br>
* Copying of base localisations to campaign-localised keys\
  <br>

This happens in the background and does not block the campaign creation response.

***

### ⚙️ Trigger Point

#### API Endpoint

bash

CopyEdit

POST /project-factory/v1/project-type/create

<br>

#### Trigger Logic

ts

CopyEdit

createAppConfig(tenantId, campaignNumber, campaignType); // No await

<br>

* createAppConfig(...) runs without await\
  <br>
* The API returns immediately while config generation runs in parallel\
  <br>

***

### 🔧 Internal Flow: createAppConfig(...)

#### 1. Fetch Enabled Template Modules

From schema:\
HCM-ADMIN-CONSOLE.FormConfigTemplate

ts

CopyEdit

const templateModules = (templateResponse?.mdms || \[])

&#x20; .map(item => item?.data || \[])

&#x20; .flat()

&#x20; .filter(module => !module?.disabled);

<br>

✔️ Only modules where disabled !== true are processed.

***

#### 2. Localisation Copy

For each module:

* Base Key: hcm-base-{moduleName}-{campaignType}\
  <br>
* Target Key: hcm-{moduleName}-{campaignNumber}\
  <br>

For each locale:

* Fetch localisation entries using the base key\
  <br>
* Replace module with the new target key\
  <br>
* Upload entries in chunks of 100\
  <br>

await localisation.createLocalisation(chunk, tenantId);

<br>

🧩 RequestInfo is not passed\
💡 Failures are logged but do not interrupt other locale uploads

***

#### 3. Insert MDMS Module Config

Target schema:\
HCM-ADMIN-CONSOLE.FormConfig

Each module:

* Is enriched with:\
  <br>
* project: campaignNumber\
  <br>
* isSelected: true\
  <br>
* Is posted to MDMS v2 API:\
  <br>

ts

CopyEdit

await httpRequest(mdms\_create\_or\_update\_url, requestBody);

<br>

🧱 Module configs are associated with the campaign being created.

***

### ✅ Summary Table

| Step                    | Description                                                            |
| ----------------------- | ---------------------------------------------------------------------- |
| Trigger API             | POST /project-factory/v1/project-type/create                           |
| Async Execution         | createAppConfig(...) runs in background, no delay to API response      |
| Template Schema         | HCM-ADMIN-CONSOLE.FormConfigTemplate                                   |
| Target Schema           | HCM-ADMIN-CONSOLE.FormConfig                                           |
| Localisation Source Key | hcm-base-{moduleName}-{campaignType}                                   |
| Localisation Target Key | hcm-{moduleName}-{campaignNumber}                                      |
| Upload Method           | In chunks of 100, per locale                                           |
| Error Handling          | Errors logged per module or locale, but execution continues gracefully |

***

### 📝 Additional Notes

* Ensures every campaign has its own set of configuration modules and localised messages\
  <br>
* Localisation is cloned and renamed from base templates for each campaign\
  <br>
* This system supports high performance and reliability through async background execution\
  <br>

***

<br>
