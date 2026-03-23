# HCM Console Configuration

## Overview

This document describes the configuration options available in the HCM (Health Campaign Management) Console. Its goal is to guide administrators, developers, and power-users to correctly set up and customise console behaviour for optimal performance, security, and user experience. These configurations include global settings, per-module options, UI customisations, environment-specific parameters, schema-based validations, feature flags, and integrations. To learn more about DIGIT HCM Service/App Configuration, click [here](https://health.digit.org/setup/configuration).

## Steps

### Boundary Master Setup

The Boundary is the primary master data for a campaign. To upload it into the database, a hierarchy is needed. If the required hierarchy doesn’t exist, you can create one using the provided screens. Hierarchies can be created at any level.

{% hint style="info" %}
&#x20;An example of a hierarchy structure is as follows, with the hierarchy type set to ADMIN:
{% endhint %}

{% code title="Admin" %}
```
Country -> Province -> District -> AdministrativePost -> Locality -> Village
```
{% endcode %}

* **Navigate to MDMS Configuration:**\
  Go to the **MDMS data configuration page** with the following parameters:
  * `moduleName = HCM-ADMIN-CONSOLE`
  * `masterName = HierarchySchema`
* **Set Up Console and Campaign Hierarchy:**
  * Configure both the **console** and **campaign** using the hierarchy you want to apply.
  * Example: **Admin**
*   **Maintain Consistency in Settings:**

    * Ensure the **hierarchy**, **lowest level**, and **split boundaries** are the same for both **console** and **campaign**.
    * Use the same **name** as defined while creating the hierarchy.

    **Example:**

    * Hierarchy: **AdministrativePost**
    * Lowest level: **Locality**

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-11-22 14-06-35.png" alt=""><figcaption></figcaption></figure>

* Navigate to the Boundary Data Management page and click on Create new boundary data.

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-11-22 12-24-32.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-11-22 12-24-50.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-11-22 12-29-28.png" alt=""><figcaption></figcaption></figure>

* Create the hierarchy and then download the template. Add data in the template.

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-11-22 12-38-38.png" alt=""><figcaption></figcaption></figure>

* Refer to the dummy template attached for reference.
* All the boundaries are localised to the localisation module below: &#x20;

```javascript
hcm-boundary-${BOUNDARY_HIERARCHY_TYPE} // hierarchy type should be according to the selected hierarchy and  the module has everything in lowercase.
```

{% hint style="info" %}
The system automatically generates a default localisation for all boundary codes during the boundary data upload, using the same language/locale as specified at the time of upload.
{% endhint %}

{% embed url="https://docs.google.com/spreadsheets/d/1n9lEmkNFeQxnzqtHpVkwfYs4fVSyyYNuyQjCSSfcp1w/edit?usp=sharing" %}

{% hint style="info" %}
The data provided above is based on the hierarchy created above. Any changes in the levels will change the headers respectively, and data will have to be filled accordingly.
{% endhint %}

#### MDMS Data Setup

{% embed url="https://app.gitbook.com/o/-MEQmzNGXk5ajuZujG7E/s/IBoO8SBg0T10XuKjUuKN/~/changes/152/release-notes/v0.1-release-notes/master-data-management-service-mdms-and-configuration-updates" %}
MDMS Schema Collection
{% endembed %}

### 1. Hierarchy Configuration&#x20;

The **HierarchySchema** in MDMS defines how boundaries are structured for campaign creation in the system.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `HierarchySchema`

**Key Fields**

1. **hierarchyType**
   * Contains the different types of hierarchies supported.
   * Each hierarchy defines the levels of boundaries available (e.g., Province → District → Locality).
2. **isActive**
   * Determines which hierarchy type will be used to create a campaign.
   * Only the hierarchy marked as `isActive = true` will be applied.
3. **lowestHierarchy**
   * Represents the **lowest boundary level** visible to users on the boundary selection screen during campaign creation.
   * Example: If `lowestHierarchy = Locality`, the campaign supervisor will select boundaries up to the locality level.
4. **splitBoundariesOn**
   * Defines the hierarchy level on which the **target sheet tabs** will be divided.
   * Example: If set to **District**, separate target sheets will be created per district.
5. **consolidateUsersAt**
   * Used during **microplan integration**.
   * Ensures user sheets are consolidated at a particular boundary level so that campaign user assignments (e.g., distributors, supervisors) are correctly populated.

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>selecting boundaries</p></figcaption></figure>

{% hint style="info" %}
Users can change the lowest hierarchy, but it is advised to keep it till the mentioned level because a lot of boundaries will increase the validations and the load on the server to load all the boundaries
{% endhint %}

<details>

<summary>HierarchySchema Sample MDMS Data</summary>

```
[
    {
        "type": "microplan",
        "group": [
            "MALARIA"
        ],
        "hierarchy": "MICROPLAN",
        "department": [],
        "lowestHierarchy": "VILLAGE",
        "highestHierarchy": "COUNTRY",
        "splitBoundariesOn": "DISTRICT",
        "consolidateUsersAt": "LOCALITY"
    },
    {
        "type": "boundary",
        "group": [
            "MALARIA"
        ],
        "hierarchy": "MICROPLAN",
        "department": [],
        "lowestHierarchy": "VILLAGE",
        "highestHierarchy": "COUNTRY",
        "splitBoundariesOn": "DISTRICT",
        "consolidateUsersAt": "LOCALITY"
    },
    {
        "type": "campaign",
        "group": [
            "MALARIA"
        ],
        "hierarchy": "NEWTEST0002",
        "department": [],
        "lowestHierarchy": "ADMINISTRATIVEPOST",
        "splitBoundariesOn": "DISTRICT",
        "consolidateUsersAt": "LOCALITY",
        "highestHierarchy": "COUNTRY"
    },
    {
        "type": "default",
        "group": [
            "MALARIA"
        ],
        "hierarchy": "DEFAULTBOUNDARYNEWONE",
        "department": [],
        "lowestlevel": "ADMINISTRATIVEPOST",
        "splitBasedOn": "DISTRICT",
        "consolidateUsersAt": "LOCALITY",
        "highestHierarchy": "COUNTRY"
        
    },
    {
        "type": "console",
        "group": [
            "MALARIA"
        ],
        "hierarchy": "ADMIN",
        "department": [],
        "lowestHierarchy": "Posto Administrativo",
        "splitBoundariesOn": "Distrito",
        "consolidateUsersAt": "LOCALITY",
        "highestHierarchy": "COUNTRY"
    }
]
```

</details>

In the **HierarchySchema** configuration, different `type` values are used to define the purpose of each hierarchy. These types determine how the hierarchy will be applied during different stages of the campaign.

Here, we have 4 types used in the campaign flow:

* `"type": "console"`: Used for the Campaign creation flow. Defines the boundary hierarchy structure that will be visible when creating a new campaign
* `"type": "microplan"`: Used for the Microplan creation flow. Ensures that microplans are aligned to the configured boundary hierarchy.
* `"type": "campaign"`: Used for the Boundary Management creation flow. Specifies the hierarchy for managing campaign boundaries once a campaign is set up.
* `"type": "default"`: Serves as the default hierarchy for Boundary Management creation flow and holds default settings.

{% hint style="warning" %}
We support the development and handling of various use cases. However, we recommend using the same hierarchy configuration across all types to ensure a seamless flow. This allows for creating a microplan within the same hierarchy, building campaigns on it, and managing the boundary hierarchy consistently.
{% endhint %}

### 2. Template Validations  - Schemas

#### Excel Upload Validation Schema

The system uses a single schema to validate Excel uploads, both on the **UI** and the **backend**. The schema ensures that uploaded data matches the required structure and rules. Each upload type has its own schema **title**.

If a user wants to change how validation works, the schema configuration must be updated.

#### Schema Properties

1. **`isRequired`**
   * Marks the columns that must be filled.
   * `true` → the column is mandatory.
   * `false` → the column is optional.
2. **`orderNumber`**
   * Defines the **position** of the column in the Excel sheet.
   * Ensures the columns are uploaded in the correct order.
3. **`title`**
   * Represents the schema title.
   * Each title is linked to the type of upload (e.g., user upload, campaign upload, etc.).
4. **`enum`**
   * Lists the **allowed values** for a field.
   * Ensures that only predefined options can be entered (e.g., `"Male"`, `"Female"`, `"Other"` for gender).
5. **`numberProperties`**
   * Applies to numeric fields.
   * Defines constraints such as:
     * **uniqueness** (whether duplicate values are allowed),
     * **required status**,
     * **minimum/maximum limits**.
6. **`stringProperties`**
   * Applies to text fields.
   * Defines rules such as:
     * **required status**,
     * **uniqueness**,
     * **length restrictions** (minimum/maximum characters),
     * **content constraints** (e.g., regex patterns).

#### Excel Validation Configurations

The **schemas** stored under the MDMS configuration define how validations are applied for different Excel uploads. These validations apply at both the **UI** and **backend** levels.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `schemas`

If users want to adjust or extend the validations, they can do so by updating the schema.

#### Types of Validations

**1. User Validations**

* **Roles** → Add or remove roles to be validated.
* **Employment Type** → Update the `enum` list to add or remove types.
* **Headers** → All headers are mandatory by default, but you can toggle this by setting `isRequired = true/false`.

**2. Facility Validations**

* **Facility Type** → Add or delete facility categories.
* **Facility Status** → Add or delete status options.
* **Facility Usage** → Add or delete usage options.
* **Capacity** → Adjust `minimum` and `maximum` values.
* **Facility Name** → Update constraints for `minLength` and `maxLength`.
* **Headers** → All headers are mandatory by default; adjust using `isRequired`.

**3. Target Validations**

* **Target** → Adjust `minimum` and `maximum` validations.
* **Boundary Code** → Mandatory field.
* **Target Header** → Mandatory field.
* **Campaign Type** → Based on the selected campaign type, boundary targets are updated.
* **Custom Columns** → New target columns can be introduced if required.

{% hint style="info" %}
As V1 Api is deprecated, it used _HCM-ADMIN-CONSOLE.adminSchema,_ which is no longer in use, No V2 Apis uses  **HCM-ADMIN-CONSOLE.schemas**
{% endhint %}

<details>

<summary>AdminSchema Sample MDMS data</summary>

```
{
    "title": "target-Bednet",
    "$schema": "http://json-schema.org/draft-07/schema#",
    "properties": {
      "numberProperties": [
        {
          "name": "HCM_ADMIN_CONSOLE_TARGET",
          "type": "number",
          "color": "#93c47d",
          "maximum": 100000000,
          "minimum": 1,
          "isRequired": true,
          "multipleOf": 1,
          "description": "Target at the Selected Boundary Level",
          "orderNumber": 1,
          "unFreezeColumnTillData": true
        },
        {
          "name": "HCM_ADMIN_CONSOLE_TARGET_BEDNET_COLUMN_2",
          "type": "number",
          "color": "#93c47d",
          "maximum": 100000000,
          "minimum": 1,
          "isRequired": false,
          "description": "Target Population",
          "orderNumber": 2,
          "unFreezeColumnTillData": true
        },
        {
          "name": "HCM_ADMIN_CONSOLE_TARGET_BEDNET_COLUMN_3",
          "type": "number",
          "color": "#93c47d",
          "maximum": 100000000,
          "minimum": 1,
          "isRequired": false,
          "description": "Number of Bednets to be Distributed",
          "orderNumber": 3,
          "unFreezeColumnTillData": true
        }
      ]
    }
  },
  {
    "title": "user-readme",
    "$schema": "http://json-schema.org/draft-07/schema#",
    "properties": {
      "stringProperties": [
        {
          "name": "USERWITHBOUNDARY_README_MAINHEADER",
          "type": "string",
          "color": "#f25449",
          "width": 120,
          "wrapText": true,
          "uniqueKey": "userReadmeHeader",
          "description": "Readme header",
          "orderNumber": 1,
          "adjustHeight": true,
          "freezeColumn": true
        }
      ]
    }
  },
  {
    "title": "user",
    "$schema": "http://json-schema.org/draft-07/schema#",
    "properties": {
      "enumProperties": [
        {
          "enum": [
            "Temporary",
            "Permanent"
          ],
          "name": "HCM_ADMIN_CONSOLE_USER_EMPLOYMENT_TYPE",
          "color": "#93c47d",
          "uniqueKey": "userEmployementType",
          "isRequired": true,
          "description": "Employement Type",
          "orderNumber": 4,
          "errorMessage": "Employment Type is missing or invalid.",
          "freezeColumnIfFilled": true
        },
        {
          "enum": [
            "Active",
            "Inactive"
          ],
          "name": "HCM_ADMIN_CONSOLE_USER_USAGE",
          "color": "#93c47d",
          "uniqueKey": "userUsage",
          "isRequired": true,
          "description": "User Usage",
          "orderNumber": 5,
          "errorMessage": "User usage is missing or invalid."
        }
      ],
      "numberProperties": [
        {
          "name": "HCM_ADMIN_CONSOLE_USER_PHONE_NUMBER",
          "type": "number",
          "color": "#93c47d",
          "maximum": 9999999999,
          "minimum": 1000000000,
          "pattern": "^[0-9]{10}$",
          "isUnique": true,
          "uniqueKey": "userPhoneNumber",
          "isRequired": true,
          "description": "Phone Number",
          "orderNumber": 2,
          "errorMessage": "Phone Number must be a 10-digit number.",
          "freezeColumnIfFilled": true
        }
      ],
      "stringProperties": [
        {
          "name": "HCM_ADMIN_CONSOLE_USER_ROLE",
          "color": "#93c47d",
          "prefix": "ACCESSCONTROL_ROLES_ROLES_",
          "uniqueKey": "userRoles",
          "hideColumn": true,
          "description": "User Role",
          "orderNumber": 3,
          "errorMessage": "At least one user role is required.",
          "freezeTillData": true,
          "multiSelectDetails": {
            "enum": [
              "DISTRIBUTOR",
              "DASHBOARD_VIEWER",
              "HEALTH_FACILITY_WORKER",
              "WAREHOUSE_MANAGER",
              "NATIONAL_SUPERVISOR",
              "PROVINCIAL_SUPERVISOR",
              "DISTRICT_SUPERVISOR",
              "FIELD_SUPERVISOR",
              "REGISTRAR",
              "SUPERVISOR",
              "HELPDESK_USER",
              "MONITOR_LOCAL",
              "LOGISTICAL_OFFICER",
              "TEAM_SUPERVISOR"
            ],
            "maxSelections": 5,
            "minSelections": 1
          },
          "freezeColumnIfFilled": true
        },
        {
          "name": "HCM_ADMIN_CONSOLE_USER_NAME",
          "type": "string",
          "color": "#93c47d",
          "maxLength": 128,
          "minLength": 2,
          "uniqueKey": "userPrefferedName",
          "isRequired": true,
          "description": "User Name",
          "orderNumber": 1,
          "errorMessage": "Name must be alphanumeric and between 2 to 128 characters.",
          "freezeColumnIfFilled": true
        },
        {
          "name": "HCM_ADMIN_CONSOLE_BOUNDARY_CODE_MANDATORY",
          "type": "string",
          "color": "#93c47d",
          "uniqueKey": "boundaryCodes",
          "isRequired": true,
          "description": "Boundary Code (Mandatory)",
          "orderNumber": 7,
          "errorMessage": "Boundary Code is required and must be a valid string."
        },
        {
          "name": "#status#",
          "type": "string",
          "color": "#ffff00",
          "isUpdate": true,
          "hideColumn": true,
          "description": "status",
          "orderNumber": 9,
          "freezeColumn": true,
          "showInProcessed": true
        },
        {
          "name": "UserService Uuids",
          "type": "string",
          "color": "#ffff00",
          "isUpdate": true,
          "uniqueKey": "userServiceUuids",
          "hideColumn": true,
          "description": "uuid",
          "orderNumber": 11,
          "freezeColumn": true
        },
        {
          "name": "#errorDetails#",
          "type": "string",
          "color": "#ffff00",
          "isUpdate": true,
          "hideColumn": true,
          "description": "error details",
          "orderNumber": 10,
          "freezeColumn": true,
          "showInProcessed": true
        },
        {
          "name": "UserName",
          "type": "string",
          "color": "#93c47d",
          "pattern": "^[a-zA-Z][a-zA-Z0-9._-]{2,29}$",
          "isUnique": true,
          "uniqueKey": "userUserName",
          "description": "user name",
          "orderNumber": 7,
          "errorMessage": "Username must be 3–30 characters long, start with a letter, and contain only letters, numbers, dots (.), underscores (_), or hyphens (-).",
          "freezeColumn": false,
          "freezeTillData": true,
          "freezeColumnIfFilled": true
        },
        {
          "name": "Password",
          "type": "string",
          "color": "#ffff00",
          "pattern": "^(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[!@#$%^&*()_+\\-=\\[\\]{};':\"\\\\|,.<>/?]).{8,}$",
          "minLength": 8,
          "uniqueKey": "userPassword",
          "hideColumn": true,
          "description": "password",
          "orderNumber": 8,
          "freezeColumn": true,
          "showInProcessed": true
        }
      ]
    }
  },
  {
    "title": "boundary-data",
    "$schema": "http://json-schema.org/draft-07/schema#",
    "properties": {
      "stringProperties": [
        {
          "name": "HCM_ADMIN_CONSOLE_BOUNDARY_CODE",
          "type": "string",
          "color": "#f3842d",
          "width": 40,
          "uniqueKey": "boundaryCodes",
          "description": "Boundary Code Header",
          "orderNumber": 1,
          "freezeColumn": true
        }
      ]
    }
  },
  {
    "title": "target-readme",
    "$schema": "http://json-schema.org/draft-07/schema#",
    "properties": {
      "stringProperties": [
        {
          "name": "BOUNDARY_README_MAINHEADER",
          "type": "string",
          "color": "#f25449",
          "width": 120,
          "wrapText": true,
          "uniqueKey": "boundaryReadmeHeader",
          "description": "Readme header",
          "orderNumber": 1,
          "adjustHeight": true,
          "freezeColumn": true
        }
      ]
    }
  },
  {
    "title": "facility-readme",
    "$schema": "http://json-schema.org/draft-07/schema#",
    "properties": {
      "stringProperties": [
        {
          "name": "FACILITYWITHBOUNDARY_README_MAINHEADER",
          "type": "string",
          "color": "#f25449",
          "width": 120,
          "wrapText": true,
          "description": "Readme header",
          "orderNumber": 1,
          "adjustHeight": true,
          "freezeColumn": true
        }
      ]
    }
  },
  {
    "title": "facility",
    "$schema": "http://json-schema.org/draft-07/schema#",
    "properties": {
      "enumProperties": [
        {
          "enum": [
            "Warehouse",
            "Health Facility",
            "Storing Resource"
          ],
          "name": "HCM_ADMIN_CONSOLE_FACILITY_TYPE",
          "color": "#93c47d",
          "uniqueKey": "facilityType",
          "isRequired": true,
          "description": "Facility type",
          "orderNumber": 3,
          "freezeColumnIfFilled": true
        },
        {
          "enum": [
            "Temporary",
            "Permanent"
          ],
          "name": "HCM_ADMIN_CONSOLE_FACILITY_STATUS",
          "color": "#93c47d",
          "uniqueKey": "facilityStatus",
          "isRequired": true,
          "description": "Facility status",
          "orderNumber": 4,
          "freezeColumnIfFilled": true
        },
        {
          "enum": [
            "Active",
            "Inactive"
          ],
          "name": "HCM_ADMIN_CONSOLE_FACILITY_USAGE",
          "color": "#93c47d",
          "uniqueKey": "facilityUsage",
          "isRequired": true,
          "description": "Facility usage",
          "orderNumber": 7
        }
      ],
      "numberProperties": [
        {
          "name": "HCM_ADMIN_CONSOLE_FACILITY_CAPACITY",
          "type": "number",
          "color": "#93c47d",
          "maximum": 100000000,
          "minimum": 1,
          "uniqueKey": "facilityCapacity",
          "isRequired": true,
          "description": "Capacity",
          "orderNumber": 5,
          "freezeColumnIfFilled": true
        }
      ],
      "stringProperties": [
        {
          "name": "HCM_ADMIN_CONSOLE_FACILITY_NAME",
          "type": "string",
          "color": "#93c47d",
          "isUnique": true,
          "maxLength": 2000,
          "minLength": 1,
          "uniqueKey": "facilityName",
          "isRequired": true,
          "description": "Facility Name",
          "orderNumber": 2,
          "freezeColumnIfFilled": true
        },
        {
          "name": "HCM_ADMIN_CONSOLE_FACILITY_CODE",
          "type": "string",
          "color": "#93c47d",
          "isUnique": true,
          "maxLength": 2000,
          "minLength": 1,
          "uniqueKey": "facilityCode",
          "hideColumn": true,
          "description": "Facility Code",
          "orderNumber": 1
        },
        {
          "name": "HCM_ADMIN_CONSOLE_BOUNDARY_CODE_MANDATORY",
          "type": "string",
          "color": "#93c47d",
          "uniqueKey": "boundaryCodes",
          "isRequired": true,
          "description": "Boundary Code",
          "orderNumber": 6
        },
        {
          "name": "#status#",
          "type": "string",
          "color": "#ffff00",
          "isUpdate": true,
          "hideColumn": true,
          "description": "status",
          "orderNumber": 8,
          "freezeColumn": true,
          "showInProcessed": true
        },
        {
          "name": "#errorDetails#",
          "type": "string",
          "color": "#ffff00",
          "isUpdate": true,
          "hideColumn": true,
          "description": "error details",
          "orderNumber": 9,
          "freezeColumn": true,
          "showInProcessed": true
        }
      ]
    }
  }
```

</details>

{% hint style="danger" %}
While introducing a new campaign/project type, this admin schema needs to be added for that type.
{% endhint %}

### 3. Attributes Configuration

The schema includes a **list of attribute configurations**, where each attribute is:

* Identified by a **unique key**,
* Defined with a **code**, and
* Linked to an **internationalisation key (i18nKey)** for multi-language support.

**Example Attributes**

The following attributes are available for use in campaigns to capture beneficiary information:

* **Age**
* **Height**
* **Weight**
* **Gender**

These attributes ensure that consistent, standardised data points are collected across campaigns.

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Attributes </p></figcaption></figure>

The **attribute dropdown** in the system is dynamically populated from the `attributeConfig` schema. This schema defines the set of attributes available for selection during campaign setup or data entry.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `attributeConfig`

<details>

<summary>attributeConfig Sample MDMS Data</summary>

```
[
    {
        "key": 4,
        "code": "Gender",
        "i18nKey": "CAMPAIGN_ATTRIBUTE_GENDER"
    },
    {
        "key": 1,
        "code": "Age",
        "i18nKey": "CAMPAIGN_ATTRIBUTE_AGE"
    }
]
```

</details>

### 4. Base Timeout

This schema defines the rules for how frequently the system should call the **search API** after a file upload. The purpose of these calls is to check the **validation status** of the uploaded file.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `baseTimeOut`

**How It Works**

1. **Base Time**
   * Defines the minimum interval after which the search API is triggered.
2. **Dynamic Interval Calculation**
   * The actual interval = **baseTime × number of fields in the uploaded sheet**.
   * This interval is constrained by:
     * **Minimum base time** (lower limit), and
     * **maxTime** (upper limit).
3. **Search API Calls**
   * The search API is called repeatedly at the calculated interval.
   * Calls stop only when a **successful** or **failed** response is received.
4. **TimelineRefetch**
   * Configured to call the getProcessAPI of the timeline periodically.
   * Ensures the process status is kept up to date after a certain interval.

<details>

<summary>baseTimeOut Sample MDMS Data</summary>

```
[
  {
      "maxTime": 5000,
      "baseTimeOut": 50,
      "timelineRefetch": 3000
  }
]
```

</details>

{% hint style="info" %}
Advised not to change the base time and max time to prevent delay in validation progress.
{% endhint %}

{% embed url="https://raw.githubusercontent.com/egovernments/egov-mdms-data/UNIFIED-QA/data/mz/health/hcm-admin-console/baseTimeOut.json" %}
[baseTimeOut.json](https://raw.githubusercontent.com/egovernments/egov-mdms-data/UNIFIED-QA/data/mz/health/hcm-admin-console/baseTimeOut.json)
{% endembed %}

### 6. Delivery Type Configuration

The **delivery configuration schema** is used to define how **deliveries** are displayed in the system. It distinguishes between:

* **Direct Deliveries** → Items or services provided directly to the beneficiary.
* **Indirect Deliveries** → Items or services provided through an intermediary (e.g., via a facility, distributor, or supervisor).
* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `deliveryTypeConfig`

<details>

<summary>deliveryTypeConfig Sample MDMS Data</summary>

```
[
    {
        "key": 1,
        "code": "DIRECT"
    },
    {
        "key": 2,
        "code": "INDIRECT"
    }
]
```

</details>

### 7. Mail Configuration

The **mailConfig** schema is used to define the **default email ID** for contacting the **L1 support team** or the **implementation team**. This comes into play when a user requests a hierarchy that is not currently available in the system.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `mailConfig`

<details>

<summary>mailConfig Sample MDMS Data</summary>

```
[
    {
        "mailId": "L1team@email.com"
    }
]
```

</details>

### 8.  Operator Configuration

The **operatorConfig** schema defines all the **operator options** that can be applied to attributes. These operators are used in the system for filtering, validation, and logical conditions during campaign configuration and execution.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `operatorConfig`

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Operators containg options</p></figcaption></figure>

<details>

<summary>operatorConfig Sample MDMS Data</summary>

```
[
    {
        "key": 6,
        "code": "LESS_THAN_EQUAL_TO"
    },
    {
        "key": 5,
        "code": "GREATER_THAN_EQUAL_TO"
    },
    {
        "key": 4,
        "code": "EQUAL_TO"
    },
    {
        "key": 3,
        "code": "IN_BETWEEN"
    },
    {
        "key": 2,
        "code": "GREATER_THAN"
    },
    {
        "key": 1,
        "code": "LESS_THAN"
    }
]
```

</details>

### 9.  Product Type

The **productType** schema defines the list of **resource types** that can be selected in the system. If a required resource type is not already available, it can be added through this schema. Once added, the new resource type will automatically appear in the **resources dropdown**.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `productType`

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Resource type options</p></figcaption></figure>

<details>

<summary>productType Sample MDMS Data</summary>

```
[
    {
        "key": 4,
        "code": "RESIDUAL_SPRAY"
    },
    {
        "key": 3,
        "code": "TONIC"
    },
    {
        "key": 2,
        "code": "TABLET"
    },
    {
        "key": 1,
        "code": "BEDNET"
    }
]
```

</details>

### 10.  ReadMe Configuration

The **ReadMeConfig** schema defines the **information messages** that are displayed both in the **UI** and in the **ReadMe sheet** of the downloaded Excel templates. These messages act as **instructions** for users, guiding them on how to correctly fill in the upload templates.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `ReadMeConfig`

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption><p>info message for downloaded template</p></figcaption></figure>

Below is an example of how data is entered into the read-me schema for the headers and their description:

<details>

<summary>ReadMeConfig Sample MDMS Data</summary>

```
{
      "type": "userWithBoundary",
      "texts": [
        {
          "header": "USERWITHBOUNDARY_README_HEADER_1",
          "isHeaderBold": true,
          "inSheet": true,
          "inUiInfo": true,
          "descriptions": [
            {
              "text": "USERWITHBOUNDARY_README_HEADER_1_DESC_1",
              "isStepRequired": true
            },
            {
              "text": "USERWITHBOUNDARY_README_HEADER_1_DESC_2",
              "isStepRequired": true
            }
          ]
        },
        {
          "header": "USERWITHBOUNDARY_README_HEADER_2",
          "isHeaderBold": true,
          "inSheet": true,
          "inUiInfo": true,
          "descriptions": [
            {
              "text": "USERWITHBOUNDARY_README_HEADER_2_DESC_1",
              "isStepRequired": true
            },
            {
              "text": "USERWITHBOUNDARY_README_HEADER_2_DESC_2",
              "isStepRequired": true
            },
            {
              "text": "USERWITHBOUNDARY_README_HEADER_2_DESC_3",
              "isStepRequired": true
            },
            {
              "text": "USERWITHBOUNDARY_README_HEADER_2_DESC_4",
              "isStepRequired": true
            }
          ]
        },
```

</details>

**Schema Fields**

* **type**: Defines the upload type (e.g., _User_, _Facility_, _Target_).
* **header**: The text identifier for the header (localised using the localisation module).
* **isHeaderBold**: Boolean → whether the header should be displayed in **bold**.
* **inSheet**: Boolean → whether the header should appear in the **downloaded Excel sheet**.
* **inUiInfo**: Boolean → whether the header should appear in the **UI information panel**.
* **text**: The text identifier for the description (localised).
* **isStepRequired**: Boolean → whether the description is a **mandatory step** for users.

**Localisation**

* All **header** and **text** values are stored as **codes**, which are then mapped through the **localisation module**.
* This ensures multi-language support for instructions across the platform.

```json
hcm-admin-schemas
```

### 11. Login Configuration

To display the **Privacy Policy component** on the login page, you need to add the required configurations in **MDMS**.

* **Module Name**: `LoginConfig`
* **Master Name**: `commonUiConfig`

In version **v0.4**, the login page was revamped, and the configuration was updated accordingly.

**Steps**

1. Navigate to the **MDMS configuration** for the login page.
2. Locate the module: `LoginConfig`.
3. In the `commonUiConfig` master, add or update the fields as required.
4. You can **customise** the fields (add or delete) depending on your implementation needs.

For detailed configuration examples and usage, refer [here](https://core.digit.org/guides/developer-guide/ui-developer-guide/customisation/login-page).

<details>

<summary>LoginConfig Sample MDMS Data</summary>

```json
{
                "texts": {
                    "header": "CORE_COMMON_LOGIN",
                    "submitButtonLabel": "CORE_COMMON_CONTINUE",
                    "secondaryButtonLabel": "CORE_COMMON_FORGOT_PASSWORD"
                },
                "title": "login",
                "inputs": [
                    {
                        "key": "username",
                        "type": "text",
                        "label": "CORE_LOGIN_USERNAME",
                        "populators": {
                            "name": "username",
                            "error": "ERR_USERNAME_REQUIRED",
                            "validation": {
                                "required": true
                            }
                        },
                        "isMandatory": true
                    },
                    {
                        "key": "password",
                        "type": "password",
                        "label": "CORE_LOGIN_PASSWORD",
                        "populators": {
                            "name": "password",
                            "error": "ERR_PASSWORD_REQUIRED",
                            "validation": {
                                "required": true
                            }
                        },
                        "isMandatory": true
                    },
                    {
                        "key": "check",
                        "type": "component",
                        "disable": false,
                        "component": "PrivacyComponent",
                        "populators": {
                            "name": "check"
                        },
                        "customProps": {
                            "module": "HCM"
                        },
                        "isMandatory": true,
                        "withoutLabel": true
                    }
                ],
                "bannerImages": [
                    {
                        "id": 1,
                        "image": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/banner/Pageone.png",
                        "title": "CORE_HCM_TITLE_ONE",
                        "description": "CORE_HCM_DESCRIPTION_ONE"
                    },
                    {
                        "id": 2,
                        "image": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/banner/Pagetwo.png",
                        "title": "CORE_HCM_TITLE_SEVEN",
                        "description": "CORE_HCM_DESCRIPTION_SEVEN"
                    },
                    {
                        "id": 3,
                        "image": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/banner/Pagethree.png",
                        "title": "CORE_HCM_TITLE_TWO",
                        "description": "CORE_HCM_DESCRIPTION_TWO"
                    },
                    {
                        "id": 4,
                        "image": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/banner/pagefour.jpeg",
                        "title": "CORE_HCM_TITLE_THREE",
                        "description": "CORE_HCM_DESCRIPTION_THREE"
                    },
                    {
                        "id": 5,
                        "image": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/banner/Pageone.png",
                        "title": "CORE_HCM_TITLE_FOUR",
                        "description": "CORE_HCM_DESCRIPTION_FOUR"
                    },
                    {
                        "id": 6,
                        "image": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/banner/pagefive.jpeg",
                        "title": "CORE_HCM_TITLE_FIVE",
                        "description": "CORE_HCM_DESCRIPTION_FIVE"
                    },
                    {
                        "id": 7,
                        "image": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/banner/Pagetwo.png",
                        "title": "CORE_HCM_TITLE_SIX",
                        "description": "CORE_HCM_DESCRIPTION_SIX"
                    }
                ]
            }
```

</details>

{% hint style="info" %}
configure banner images relevant to the product deployment and use case
{% endhint %}

### 12. Policy Configuration

This configuration displays the data in the privacy pop-up. An example of the configuration is shown below:

<details>

<summary>Policy MDMS Data</summary>

```
{
      "header": "PRIVACY_HEADER",
      "module": "HCM",
      "contents": [
        {
          "header": "PRIVACY_HEADER_1_SUB_1",
          "descriptions": [
            {
              "text": "PRIVACY_HEADER_1_SUB_1_DESC_1",
              "type": null,
              "isBold": false
            },
            {
              "text": "PRIVACY_HEADER_1_SUB_1_DESC_2",
              "type": null,
              "isBold": false
            },
            {
              "text": "PRIVACY_HEADER_1_SUB_1_DESC_3",
              "type": null,
              "isBold": false
            },
]
},
 {
              "text": "PRIVACY_HEADER_9_SUB_9_DESC_5",
              "type": null,
              "isBold": false,
              "subDescriptions":[
                {
                  "text": "PRIVACY_HEADER_9_SUB_9_DESC_5_SUBDESC_1",
                  "type": null,
                  "isBold": false,
                  "isSpaceRequired": true
                },
                {
                  "text": "PRIVACY_HEADER_9_SUB_9_DESC_5_SUBDESC_2",
                  "type": null,
                  "isBold": false,
                  "isSpaceRequired": true
                }
              ]
            }
          ]
        },
```

</details>

In the schema:

Type can be the following:&#x20;

* **`null:`**
  * When `type` is `null`, it indicates that the description is just plain text.&#x20;
* **`point:`**
  * When `type` is set to `point`, it likely means that the description should be displayed as a bullet point or list item.&#x20;
* **`step:`**
  * When `type` is set to `step`, it suggests that the description is part of a sequence of steps.
* **subdescriptions**: to show the sub-descriptions at the point.

### 13. Date with Boundary

This configuration is used when you want to update the dates with or without the selected boundaries.

If the flag is false, then by default, it updates the dates at the country level. If you want to update the dates at the lower boundary levels, then make the flag true.

<details>

<summary>DateWithBoundary MDMS data</summary>

```
"dateWithBoundary": [
    {
      "dateWithBoundary": true
    }
  ]
```

</details>

### 14. Project Type Configuration

This configuration is now used in place of the delivery configuration.

This is used to store all the pre-required conditions for the delivery conditions screens.

Master Name: **HCM-PROJECT-TYPES**

ModuleName: **projectTypes**

<details>

<summary>ProjectTypes MDMS Data</summary>

```
 {
      "id": "ea1bb2e7-06d8-4fe4-ba1e-f4a6363a21be",
      "name": "configuration for Multi Round Campaigns",
      "code": "MR-DN",
      "group": "MALARIA",
      "type": "multiround",
      "beneficiaryType": "INDIVIDUAL",
      "eligibilityCriteria": [
        "All households having members under the age of 18 are eligible.",
        "Prison inmates are eligible."
      ],
      "taskProcedure": [
        "1 bednet is to be distributed per 2 household members.",
        "If there are 4 household members, 2 bednets should be distributed.",
        "If there are 5 household members, 3 bednets should be distributed."
      ],
      "resources": [
        {
          "productVariantId": "PVAR-2024-05-09-000331",
          "isBaseUnitVariant": false,
          "name": "SP 500mg"
        },
        {
          "productVariantId": "PVAR-2024-05-09-000332",
          "isBaseUnitVariant": true,
          "name": "SP 250mg"
        }
      ],
      "observationStrategy": "DOT1",
      "validMinAge": 3,
      "validMaxAge": 64,
      "cycles": [
        {
          "mandatoryWaitSinceLastCycleInDays": null,
          "startDate": 1714329000000,
          "endDate": 1715279400000,
          "id": 1,
          "deliveries": [
            {
              "id": 1,
              "deliveryStrategy": "DIRECT",
              "mandatoryWaitSinceLastDeliveryInDays": null,
              "doseCriteria": [
                {
                  "condition": "3<=age<11",
                  "ProductVariants": [
                    {
                      "productVariantId": "PVAR-2024-05-09-000331", // should be set according to the environment
                      "quantity": 1,
                       "name": "SP 500mg"
                    },
                  ]
                },
              ]
            },
          ]
        },
      ]
    },
```

</details>

This is the sample data for the project type - MR-DN

Explanation for the MDMS Data -

1. **Project Types**: Three main project types (`LLIN-mz`, `MR-DN`, and `IRS-mz`) with unique configurations.
2. **Cycles and Deliveries**:
   * Each project type contains cycles, and each cycle contains multiple deliveries.
   * Deliveries include details such as `deliveryStrategy`, `doseCriteria`, and `ProductVariants`.
3. **Resources**: A list of resources specific to each project type.
4. **Eligibility Criteria**: Contains a list of conditions for each project type.
5. **Other Configurations**:
   * `attrAddDisable`, `deliveryAddDisable`, and similar attributes determine UI behaviour.

**Requirements:**

{% hint style="danger" %}
Mandatory to set the product variant ID according to the environment.
{% endhint %}

```
"ProductVariants": [
                    {
                      "productVariantId": "PVAR-2024-05-09-000331", // should be set according to the environment
                      "quantity": 1,
                       "name": "SP 500mg"
                    },
                  ]
```

### 15.  Roles for Checklist

* [x] Master Name: **HCM-ADMIN-CONSOLE**
* [x] ModuleName: **rolesForChecklist**

This master data is used to show the dropdown of roles in the checklist screens -

<details>

<summary>RolesForChecklist Sample MDMS Data</summary>

```
{
    "tenantId": "mz",
    "schemaCode": "HCM-ADMIN-CONSOLE.rolesForChecklist",
    "uniqueIdentifier": null,
    "data": {
        "key": 1,
        "code": "DISTRIBUTOR"
    },
    "isActive": true
}
```

</details>

### 16. Checklist Templates

This master data is used to create default template of the checklist for the selected campaign + role + checklist type -

* [x] Master Name: HCM-ADMIN-CONSOLE
* [x] ModuleName: ChecklistTemplates

<details>

<summary>Checklist Templates Sample MDMS Data</summary>

```
{
        "tenantId": "mz",
        "schemaCode": "HCM-ADMIN-CONSOLE.ChecklistTemplates",
        "uniqueIdentifier": null,
        "data": {
            "data": [
                {
                    "id": "2d4a7b1e-1f2f-4a8a-9672-43396c6c9a1c",
                    "key": 1,
                    "type": {
                        "code": "SingleValueList"
                    },
                    "level": 1,
                    "title": "Is there a feedback system for health facilities to report any issues or requests related to bednet distribution?",
                    "value": null,
                    "options": [
                        {
                            "id": "0cff9846-03a2-4453-bf0e-200cdda5f390",
                            "key": 1,
                            "label": "Shortages",
                            "optionComment": true,
                            "optionDependency": false,
                            "parentQuestionId": "2d4a7b1e-1f2f-4a8a-9672-43396c6c9a1c"
                        },
                        {
                            "id": "2d4a7b1e-7c0d-48b1-9d53-8601c6264b90",
                            "key": 2,
                            "label": "Quality complaints",
                            "optionDependency": false,
                            "parentQuestionId": "2d4a7b1e-1f2f-4a8a-9672-43396c6c9a1c"
                        }
                    ],
                    "isActive": true,
                    "parentId": null,
                    "isRequired": false
                },
                {
                    "id": "4add5323-fc98-4e71-a783-27dbb922c99f",
                    "key": 2,
                    "type": {
                        "code": "SingleValueList"
                    },
                    "level": 1,
                    "title": "What types of health facilities do you distribute to?",
                    "value": null,
                    "options": [
                        {
                            "id": "34eac43a-e0b5-428f-9d11-12fc5b10b1ac1",
                            "key": 1,
                            "label": "Hospitals",
                            "optionComment": false,
                            "optionDependency": false,
                            "parentQuestionId": "4add5323-fc98-4e71-a783-27dbb922c99f"
                        },
                        {
                            "id": "23ace43b-e0b5-428f-9d11-12fc5b10b1ac1",
                            "key": 2,
                            "label": "Clinics",
                            "optionComment": false,
                            "optionDependency": true,
                            "parentQuestionId": "4add5323-fc98-4e71-a783-27dbb922c99f"
                        },
                        {
                            "id": "32bbca43-db87-469b-8be4-22012cc22284",
                            "key": 3,
                            "label": "Community health centers",
                            "optionDependency": false,
                            "parentQuestionId": "4add5323-fc98-4e71-a783-27dbb922c99f"
                        }
                    ],
                    "isActive": true,
                    "parentId": null,
                    "isRequired": false
                },
                {
                    "id": "23ca54be-038e-42df-a557-bb5fcd374dd5",
                    "key": 3,
                    "type": {
                        "code": "SingleValueList"
                    },
                    "level": 1,
                    "title": "What services or products do you distribute to health facilities?",
                    "value": null,
                    "options": [
                        {
                            "id": "ea32bc56-038e-42df-a557-bb5fcd374dd5",
                            "key": 1,
                            "label": "Medical equipment",
                            "optionComment": false,
                            "optionDependency": false,
                            "parentQuestionId": "23ca54be-038e-42df-a557-bb5fcd374dd5"
                        },
                        {
                            "id": "a34vc429-d13f-4340-ae5e-fe7f8aca4212",
                            "key": 2,
                            "label": "Pharmaceuticals",
                            "optionDependency": false,
                            "parentQuestionId": "23ca54be-038e-42df-a557-bb5fcd374dd5"
                        },
                        {
                            "id": "6c43b57c-d13f-4340-ae5e-fe7f8aca4212",
                            "key": 3,
                            "label": "Personal protective equipment (PPE)",
                            "optionDependency": false,
                            "parentQuestionId": "23ca54be-038e-42df-a557-bb5fcd374dd5"
                        }
                    ],
                    "isActive": true,
                    "parentId": null,
                    "isRequired": false
                },
                {
                    "id": "c65ac34b-7cc0-4993-a8fe-37e854d2b189",
                    "key": 4,
                    "type": {
                        "code": "SingleValueList"
                    },
                    "level": 2,
                    "title": "Do you have enough products for distribution to health facilities?",
                    "value": null,
                    "options": [
                        {
                            "id": "cb45ca84-7cc0-4993-a8fe-37e854d2b189",
                            "key": 1,
                            "label": "Yes",
                            "optionDependency": false,
                            "parentQuestionId": "c65ac34b-7cc0-4993-a8fe-37e854d2b189"
                        },
                        {
                            "id": "a54c73cb-60da-4c51-8501-cf4a4f473a66",
                            "key": 2,
                            "label": "No",
                            "optionComment": true,
                            "optionDependency": false,
                            "parentQuestionId": "c65ac34b-7cc0-4993-a8fe-37e854d2b189"
                        }
                    ],
                    "isActive": true,
                    "parentId": "23ace43b-e0b5-428f-9d11-12fc5b10b1ac1",
                    "isRequired": false
                }
            ],
            "role": "DISTRIBUTOR",
            "campaignType": "IRS-mz",
            "checklistType": "TRAINING_SUPERVISION"
        },
        "isActive": true
    }
```

</details>

### 17. App Field Types

* [x] Master Name: HCM-ADMIN-CONSOLE
* [x] ModuleName: appFieldTypes

This is used to describe the type of questions available in the dropdown while configuring the checklist.

<details>

<summary>AppFieldTypes Sample MDMS Data</summary>

```
{
    "code": "SingleValueList",
    "type": [
        "checklist"
    ]
}
```

</details>

### 18. Microplan Integration

* [x] Master Name: HCM-ADMIN-CONSOLE
* [x] ModuleName: microplanIntegration

This master is utilised for the microplan data fetching. Here, 'type' refers to the data template that needs to be filled. 'To' and 'from' pertain to the microplan data, and while populating campaign data, various filter conditions, such as 'includes', or 'equals', can be applied.

<details>

<summary>microplanIntegration MDMS Data</summary>

```
[
    {
        "type": "user",
        "mappings": [
            {
                "to": "Supervisor",
                "from": [
                    "PER_BOUNDARY_FOR_THE_CAMPAIGN",
                    "PER_BOUNDARY",
                    "TEAM",
                    "SUPERVISORS"
                ],
                "filter": "includes"
            },
            {
                "to": "Registrar",
                "from": [
                    "PER_BOUNDARY_FOR_THE_CAMPAIGN",
                    "PER_BOUNDARY",
                    "TEAM",
                    "REGISTRATION"
                ],
                "filter": "includes"
            },
            {
                "to": "Distributor",
                "from": [
                    "PER_BOUNDARY_FOR_THE_CAMPAIGN",
                    "PER_BOUNDARY",
                    "TEAM",
                    "DISTRIBUTION"
                ],
                "filter": "includes"
            }
        ]
    },
    {
        "type": "Target-LLIN-mz",
        "mappings": [
            {
                "to": "HCM_ADMIN_CONSOLE_TARGET",
                "from": [
                    "CONFIRMED_HCM_ADMIN_CONSOLE_TARGET_POPULATION"
                ],
                "filter": "equal"
            }
        ]
    },
    {
        "type": "Target-MR-DN",
        "mappings": [
            {
                "to": "HCM_ADMIN_CONSOLE_TARGET_SMC_AGE_3_TO_11",
                "from": [
                    "CONFIRMED_HCM_ADMIN_CONSOLE_TARGET_POPULATION_AGE_3TO11"
                ],
                "filter": "equal"
            },
            {
                "to": "HCM_ADMIN_CONSOLE_TARGET_SMC_AGE_12_TO_59",
                "from": [
                    "CONFIRMED_HCM_ADMIN_CONSOLE_TARGET_POPULATION_AGE_12TO59"
                ],
                "filter": "equal"
            }
        ]
    }
]
```

</details>

### 19. IdGen Configuration

To enable the generation of unique identifiers via the idGen service, the following data must be added to the MDMS under `moduleName=common-masters` and `masterName=IdFormat`.

* [x] Master Name: `common-masters`
* [x] ModuleName: `IdFormat`

<details>

<summary><code>common-masters.IdFormat</code>.</summary>

```json
[{
    "format": "USR-[SEQ_EG_USER_NAME]",
    "idname": "username.name"
},
{
    "format": "CMP-[cy:yyyy-MM-dd]-[SEQ_EG_CMP_ID]",
    "idname": "campaign.number"
}]
```

</details>

Ensure both configurations are added to MDMS before proceeding with ID generation.

<details>

<summary>troubleshooting if any user creation or campaign creation due to number generation</summary>

#### Sequence Management in PostgreSQL

The IDGen service relies on PostgreSQL sequences to generate unique identifiers. If the sequences are not automatically created during ID generation, they must be manually created in the database.

#### **Sequence for Usernames**

To create a sequence for usernames, execute the following SQL script:

```sql
CREATE SEQUENCE IF NOT EXISTS public.seq_eg_user_name
    INCREMENT 1
    START 1
    MINVALUE 1
    MAXVALUE 9223372036854775807
    CACHE 1;
```

#### **Sequence for Campaigns**

To create a sequence for campaign IDs, execute the following SQL script:

```sql
CREATE SEQUENCE IF NOT EXISTS public.seq_eg_cmp_id
    INCREMENT 1
    START 1
    MINVALUE 1
    MAXVALUE 9223372036854775807
    CACHE 1;
```

</details>

### &#x20;20. Target Configuration&#x20;

This configuration is used to define the mapping of target-related data from the target sheet to different beneficiary types. Each beneficiary type can be associated with one or more columns from the target sheet, which hold the respective target values.

**Key Details:**

* **campaignType**: Specifies the campaign type this configuration applies to (e.g., "LLIN-mz").
* **beneficiaries**: A list of beneficiary types, each having:
  * **columns**: The columns in the target sheet that map to this beneficiary type.
  * **beneficiaryType**: The type of beneficiary (e.g., "INDIVIDUAL", "HOUSEHOLD", "PRODUCT").

<details>

<summary>HCM-ADMIN-CONSOLE.targetConfigs</summary>

```json
[{
    "campaignType": "LLIN-mz",
    "beneficiaries": [
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_BEDNET_COLUMN_2"
            ],
            "beneficiaryType": "INDIVIDUAL"
        },
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET"
            ],
            "beneficiaryType": "HOUSEHOLD"
        },
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_BEDNET_COLUMN_3"
            ],
            "beneficiaryType": "PRODUCT"
        }
    ]
},
{
    "campaignType": "MR-DN",
    "beneficiaries": [
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_SMC_AGE_3_TO_11",
                "HCM_ADMIN_CONSOLE_TARGET_SMC_AGE_12_TO_59"
            ],
            "beneficiaryType": "INDIVIDUAL"
        },
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_SMC_COLUUM_3"
            ],
            "beneficiaryType": "HOUSEHOLD"
        },
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_SMC_COLUUM_4"
            ],
            "beneficiaryType": "PRODUCT"
        }
    ]
},
{
    "campaignType": "IRS-mz",
    "beneficiaries": [
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_IRS_4"
            ],
            "beneficiaryType": "INDIVIDUAL"
        },
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_IRS_1"
            ],
            "beneficiaryType": "HOUSEHOLD"
        },
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_IRS_3"
            ],
            "beneficiaryType": "PRODUCT"
        }
    ]
},
{
    "campaignType": "DEFAULT",
    "beneficiaries": [
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_INDIVIDUAL"
            ],
            "beneficiaryType": "INDIVIDUAL"
        },
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_HOUSEHOLD"
            ],
            "beneficiaryType": "HOUSEHOLD"
        },
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_PRODUCT"
            ],
            "beneficiaryType": "PRODUCT"
        }
    ]
},
{
    "campaignType": "Co-delivery",
    "beneficiaries": [
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_INDIVIDUAL"
            ],
            "beneficiaryType": "INDIVIDUAL"
        },
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_HOUSEHOLD"
            ],
            "beneficiaryType": "HOUSEHOLD"
        },
        {
            "columns": [
                "HCM_ADMIN_CONSOLE_TARGET_PRODUCT"
            ],
            "beneficiaryType": "PRODUCT"
        }
    ]
}]
```

</details>

## New Schemas Added

### 1. HelpTutorial

This configuration is used to define help tutorial content for the users during the flow

master details\
commonUiConfig.HelpTutorial

<details>

<summary>commonUiConfig.HelpTutorial</summary>

```json
[
                {
                    "module": "campaign",
                    "helpContent": [
                        {
                            "url": "https://share.descript.com/view/Nh6owXfM6UA",
                            "icon": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/helpimages/proximity.png",
                            "order": 0,
                            "pages": [
                                "app-modules"
                            ],
                            "title": "Module Selection",
                            "iconBackground": "#F6F0E8"
                        },
                        {
                            "url": "https://share.descript.com/view/EzE0NuMZauY",
                            "icon": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/helpimages/mapView.png",
                            "order": 1,
                            "pages": [
                                "app-configuration-redesign"
                            ],
                            "title": "Adding a new field",
                            "iconBackground": "#F6EBE8"
                        },
                        {
                            "url": "https://youtu.be/_yxD9Wjqkfw?feature=shared",
                            "icon": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/helpimages/qrScanner.png",
                            "order": 2,
                            "pages": [
                                "app-modules",
                                "app-features",
                                "app-configuration-redesign"
                            ],
                            "title": "CMN_CAMP_PREVIEW_APPLICATIONS",
                            "iconBackground": "#F1F6E8"
                        },
                        {
                            "url": "https://youtu.be/_yxD9Wjqkfw?feature=shared",
                            "icon": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/helpimages/proximity.png",
                            "order": 3,
                            "pages": [
                                "app-modules",
                                "app-features",
                                "app-configuration-redesign"
                            ],
                            "title": "CMN_CAMP_OFFLINE_QR_SCANNER",
                            "iconBackground": "#E8F4F6"
                        }
                    ]
                }
            ]
```

</details>

### 2. AllowedModules

This configuration is restrict the App config to unselect some module if optional

master details\
HCM-ADMIN-CONSOLE.AllowedModules

<details>

<summary>HCM-ADMIN-CONSOLE.AllowedModules</summary>

```json
[
  {
    "projectType": "Bednet",
    "allowedModule": [
      "DELIVERYFLOW",
      "REGISTRATIONFLOW"
    ]
  }
]

```

</details>

### 3. AppLink

This configuration is used to provide the Downloadable APK link, after the campaign is created.&#x20;

So APK needs to be manually generated [here](https://github.com/egovernments/health-campaign-field-worker-app/actions) and update the link in this master

<div data-full-width="false"><figure><img src="../../../.gitbook/assets/Screenshot 2025-09-23 at 2.56.12 PM.png" alt=""><figcaption></figcaption></figure></div>

master details\
HCM-ADMIN-CONSOLE.AppLink

<details>

<summary>HCM-ADMIN-CONSOLE.AppLink</summary>

```json
[
  {
    "appLink": "https://drive.google.com/drive/folders/1x41en8O7ZpgZfGm0G7X_TCsmrldItPTm"
  }
]

```

</details>

### 4. AppModuleSchema

This configuration is used to define the Modules & its features in App config flow

master details\
HCM-ADMIN-CONSOLE.AppModuleSchema

<details>

<summary>HCM-ADMIN-CONSOLE.AppModuleSchema</summary>

```json
[
  {
    "code": "REGISTRATIONANDDELVFLOW",
    "features": [
      {
        "code": "QR_CODE_SCANNER",
        "description": "QR_CODE_SCANNER_DESC"
      },
      {
        "code": "PROXIMITY_SEARCH",
        "description": "PROXIMITY_SEARCH_DESC"
      },
      {
        "code": "MAP_VIEW",
        "description": "MAP_VIEW_DESC"
      },
      {
        "code": "OFFLINE_DATA_SHARING",
        "description": "OFFLINE_DATA_SHARING_DESC"
      }
    ],
    "description": "DELIVERY_DESC"
  },
  {
    "code": "REGISTRATIONFLOW",
    "features": [
      {
        "code": "QR_CODE_SCANNER",
        "type": "form",
        "order": 1,
        "format": "scanner",
        "disabled": false,
        "description": "QR_CODE_SCANNER_DESC"
      },
      {
        "code": "PROXIMITY_SEARCH",
        "type": "template",
        "order": 2,
        "format": "searchByProximity",
        "disabled": false,
        "description": "PROXIMITY_SEARCH_DESC"
      },
      {
        "code": "MAP_VIEW",
        "type": "form",
        "order": 3,
        "format": "map",
        "disabled": true,
        "description": "MAP_VIEW_DESC"
      },
      {
        "code": "OFFLINE_DATA_SHARING",
        "type": "form",
        "order": 4,
        "format": "offlinedata",
        "disabled": true,
        "description": "OFFLINE_DATA_SHARING_DESC"
      }
    ],
    "description": "REGISTRATION_DESC"
  },
  {
    "code": "DELIVERY",
    "features": [
      {
        "code": "QR_CODE_SCANNER",
        "description": "QR_CODE_SCANNER_DESC"
      },
      {
        "code": "PROXIMITY_SEARCH",
        "description": "PROXIMITY_SEARCH_DESC"
      },
      {
        "code": "MAP_VIEW",
        "description": "MAP_VIEW_DESC"
      },
      {
        "code": "OFFLINE_DATA_SHARING",
        "description": "OFFLINE_DATA_SHARING_DESC"
      }
    ],
    "description": "DELIVERY_DESC"
  },
  {
    "code": "INVENTORY",
    "features": [
      {
        "code": "QR_CODE_SCANNER",
        "description": "QR_CODE_SCANNER_DESC"
      },
      {
        "code": "FACILITY_SEARCH",
        "description": "FACILITY_SEARCH_DESC"
      }
    ],
    "description": "INVENTORY_DESC"
  },
  {
    "code": "COMPLAINTS",
    "features": [],
    "description": "COMPLAINTS_DESC"
  },
  {
    "code": "ATTENDANCE",
    "features": [],
    "description": "ATTENDANCE_DESC"
  },
  {
    "code": "DELIVERYFLOW",
    "features": [
      {
        "code": "QR_CODE_SCANNER",
        "type": "form",
        "order": 1,
        "format": "scanner",
        "disabled": false,
        "description": "QR_CODE_SCANNER_DESC"
      }
    ],
    "description": "DELIVERY_DESC"
  }
]

```

</details>

### 5. AppScreenLocalisationConfig

This configuration is used to define the property to localistion to be enabled  in App config flow

master details\
HCM-ADMIN-CONSOLE.AppScreenLocalisationConfig

<details>

<summary>HCM-ADMIN-CONSOLE.AppScreenLocalisationConfig</summary>

```json
 [
  {
    "fields": [
      {
        "fieldType": "textInput",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "dropdown",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "dropdownOptions",
          "dropDownOptions",
          "message"
        ]
      },
      {
        "fieldType": "number",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "numeric",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "checkbox",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "numeric",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "scanner",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "date",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "dob",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "administrativeArea",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "latLng",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "textArea",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "mobileNumber",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "editHousehold",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message",
          "message"
        ]
      },
      {
        "fieldType": "editIndividual",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "addMember",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "IndividualDeliverySecondaryButton",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "IndividualDeliveryPrimaryButton",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "SecondaryButton",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "AcknowledgementTitle",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "AcknowledgementDescription",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "PrimaryButton",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "searchBar",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "searchByProximity",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "filter",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "select",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "text",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "qrscanner",
        "localisableProperties": [
          "errorMessage",
          "tooltip",
          "innerLabel",
          "helpText",
          "label",
          "message"
        ]
      },
      {
        "fieldType": "idPopulator",
        "localisableProperties": [
          "label",
          "message"
        ]
      },
      {
        "fieldType": "radio",
        "localisableProperties": [
          "label",
          "message"
        ]
      },
      {
        "fieldType": "deliveryConditionDialog",
        "localisableProperties": [
          "label",
          "message"
        ]
      },
      {
        "fieldType": "resourceCard",
        "localisableProperties": [
          "label",
          "message"
        ]
      }
    ],
    "screenName": "appScreenConfig",
    "moduleVersion": "3",
    "minModuleVersion": "1",
    "LocalisationModule": "configure-app"
  }
]
```

</details>

### 6. FormConfigTemplate

This configuration is used as the base template for the form config screens\
\
HCM-ADMIN-CONSOLE.FormConfigTemplate

{% hint style="info" %}
### We also have one more master FormConfig, AppConfigCache, which needs only schema, data will be auto added during campaign configuration.
{% endhint %}

<details>

<summary>HCM-ADMIN-CONSOLE.FormConfigTemplate</summary>

```json
 {
            "id": "050d071a-bf69-4e08-b376-b1ee9bebae0a",
            "tenantId": "mz",
            "schemaCode": "HCM-ADMIN-CONSOLE.FormConfigTemplate",
            "uniqueIdentifier": "REGISTRATIONFLOW.LLIN",
            "data": {
                "name": "REGISTRATIONFLOW",
                "order": 1,
                "pages": [
                    {
                        "page": "SearchBeneficiary",
                        "type": "template",
                        "label": "APPONE_REGISTRATION_SEARCHBENEFICIARY_SCREEN_HEADING",
                        "order": 1,
                        "navigateTo": {
                            "name": "overview",
                            "type": "template"
                        },
                        "properties": [
                            {
                                "type": "template",
                                "label": "APPONE_REGISTRATION_SEARCHBENEFICIARY_BY_PROXIMITY",
                                "order": 1,
                                "value": true,
                                "format": "searchByProximity",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "readOnly": false,
                                "fieldName": "searchByProximity",
                                "deleteFlag": false,
                                "innerLabel": "",
                                "systemDate": false,
                                "validations": [],
                                "isMultiSelect": false
                            },
                            {
                                "type": "template",
                                "label": "APPONE_REGISTRATION_SEARCHBENEFICIARY_BAR",
                                "order": 2,
                                "value": "",
                                "format": "searchBar",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "readOnly": false,
                                "fieldName": "searchBar",
                                "deleteFlag": false,
                                "innerLabel": "enter the name of household",
                                "systemDate": false,
                                "validations": [
                                    {
                                        "type": "required",
                                        "value": true,
                                        "message": "Required field cannot be empty"
                                    }
                                ],
                                "isMultiSelect": false
                            },
                            {
                                "type": "template",
                                "label": "APPONE_REGISTRATION_SEARCHBENEFICIARY_FILTER_LABEL",
                                "order": 3,
                                "value": [],
                                "format": "filter",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "readOnly": false,
                                "fieldName": "filter",
                                "deleteFlag": false,
                                "innerLabel": "",
                                "systemDate": false,
                                "validations": [],
                                "isMultiSelect": false
                            },
                            {
                                "type": "template",
                                "label": "APPONE_REGISTRATION_SEARCHBENEFICIARY_REGISTRATION_LABEL",
                                "order": 4,
                                "value": "",
                                "format": "PrimaryButton",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "readOnly": false,
                                "fieldName": "PrimaryButton",
                                "deleteFlag": false,
                                "innerLabel": "",
                                "systemDate": false,
                                "validations": [
                                    {
                                        "type": "required",
                                        "value": true,
                                        "message": "Required field cannot be empty"
                                    }
                                ],
                                "isMultiSelect": false
                            },
                            {
                                "type": "button",
                                "label": "APPONE_REGISTRATION_SEARCHBENEFICIARY_QR_LABEL",
                                "order": 5,
                                "value": true,
                                "format": "qrscanner",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "readOnly": false,
                                "fieldName": "SecondaryButton",
                                "deleteFlag": false,
                                "innerLabel": "",
                                "systemDate": false,
                                "validations": [],
                                "isMultiSelect": false
                            }
                        ],
                        "actionLabel": "",
                        "description": "APPONE_REGISTRATION_SEARCHBENEFICIARY_SCREEN_DESCRIPTION"
                    },
                    {
                        "page": "beneficiaryLocation",
                        "type": "object",
                        "label": "APPONE_REGISTRATION_BENEFICIARYLOCATION_SCREEN_HEADING",
                        "order": 2,
                        "navigateTo": {
                            "name": "REGISRATIONFLOW",
                            "type": "form"
                        },
                        "properties": [
                            {
                                "type": "string",
                                "label": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_administrativeArea",
                                "order": 1,
                                "value": "",
                                "format": "locality",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_administrativeArea_helpText",
                                "infoText": "",
                                "readOnly": true,
                                "fieldName": "administrativeArea",
                                "deleteFlag": false,
                                "innerLabel": "",
                                "validations": [
                                    {
                                        "type": "required",
                                        "value": true,
                                        "message": "Required field cannot be empty"
                                    }
                                ],
                                "isMultiSelect": false
                            },
                            {
                                "type": "string",
                                "label": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_latlong",
                                "order": 2,
                                "value": "",
                                "format": "latLng",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_latlong_helpText",
                                "infoText": "",
                                "readOnly": true,
                                "fieldName": "latLng",
                                "innerLabel": "",
                                "validations": [
                                    {
                                        "type": "required",
                                        "value": true,
                                        "message": "Required field cannot be empty"
                                    }
                                ],
                                "isMultiSelect": false
                            },
                            {
                                "type": "string",
                                "label": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_addressLine1",
                                "order": 3,
                                "value": "",
                                "format": "text",
                                "hidden": true,
                                "tooltip": "",
                                "helpText": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_addressLine1_helpText",
                                "infoText": "",
                                "readOnly": false,
                                "fieldName": "addressLine1",
                                "innerLabel": "",
                                "validations": [],
                                "isMultiSelect": false
                            },
                            {
                                "type": "string",
                                "label": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_addressLine2",
                                "order": 4,
                                "value": "",
                                "format": "text",
                                "hidden": true,
                                "tooltip": "",
                                "helpText": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_addressLine2_helpText",
                                "infoText": "",
                                "fieldName": "addressLine2",
                                "innerLabel": "",
                                "validations": [],
                                "isMultiSelect": false
                            },
                            {
                                "type": "string",
                                "label": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_landmark",
                                "order": 5,
                                "value": "",
                                "format": "text",
                                "hidden": true,
                                "tooltip": "",
                                "helpText": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_landmark_helpText",
                                "infoText": "",
                                "fieldName": "landmark",
                                "deleteFlag": false,
                                "innerLabel": "",
                                "validations": [],
                                "isMultiSelect": false
                            },
                            {
                                "type": "integer",
                                "label": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_pincode",
                                "order": 6,
                                "value": "",
                                "format": "text",
                                "hidden": true,
                                "tooltip": "",
                                "helpText": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_pincode_helpText",
                                "infoText": "",
                                "fieldName": "pincode",
                                "innerLabel": "",
                                "systemDate": false,
                                "validations": []
                            },
                            {
                                "type": "string",
                                "enums": [
                                    {
                                        "code": "PERMANENT",
                                        "name": "BENEFICIARYLOCATION_PERMANENT"
                                    },
                                    {
                                        "code": "CORRESPONDENCE",
                                        "name": "BENEFICIARYLOCATION_CORRESPONDENCE"
                                    },
                                    {
                                        "code": "OTHER",
                                        "name": "BENEFICIARYLOCATION_OTHER"
                                    }
                                ],
                                "label": "APPONE_REGISTRATION_BENEFICIARYLOCATION_label_typeOfAddress",
                                "order": 7,
                                "value": "PERMANENT",
                                "format": "dropdown",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "fieldName": "typeOfAddress",
                                "innerLabel": "",
                                "validations": [],
                                "includeInForm": true,
                                "includeInSummary": false
                            }
                        ],
                        "actionLabel": "APPONE_REGISTRATION_BENEFICIARYLOCATION_ACTION_BUTTON_LABEL_1",
                        "description": "APPONE_REGISTRATION_BENEFICIARYLOCATION_SCREEN_DESCRIPTION"
                    },
                    {
                        "page": "householdDetails",
                        "type": "object",
                        "label": "APPONE_REGISTRATION_HOUSEHOLDDETAILS_SCREEN_HEADING",
                        "order": 3,
                        "navigateTo": {
                            "name": "REGISRATIONFLOW",
                            "type": "form"
                        },
                        "properties": [
                            {
                                "type": "integer",
                                "label": "APPONE_REGISTRATION_HOUSEHOLDDETAILS_label_dateOfRegistration",
                                "order": 1,
                                "value": "",
                                "format": "date",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "readOnly": true,
                                "fieldName": "dateOfRegistration",
                                "innerLabel": "",
                                "systemDate": true,
                                "validations": [
                                    {
                                        "type": "required",
                                        "value": true,
                                        "message": "Required field cannot be empty"
                                    }
                                ]
                            },
                            {
                                "type": "integer",
                                "label": "APPONE_REGISTRATION_HOUSEHOLDDETAILS_label_childrenCount",
                                "order": 2,
                                "value": "0",
                                "format": "numeric",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "fieldName": "childrenCount",
                                "innerLabel": ""
                            },
                            {
                                "type": "integer",
                                "label": "APPONE_REGISTRATION_HOUSEHOLDDETAILS_label_pregnantWomenCount",
                                "order": 3,
                                "value": "0",
                                "format": "numeric",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "fieldName": "pregnantWomenCount",
                                "innerLabel": ""
                            },
                            {
                                "type": "integer",
                                "label": "APPONE_REGISTRATION_HOUSEHOLDDETAILS_label_memberCount",
                                "order": 4,
                                "value": "1",
                                "format": "numeric",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "fieldName": "memberCount",
                                "innerLabel": "",
                                "validations": [
                                    {
                                        "type": "required",
                                        "value": true,
                                        "message": "Please fill the required field."
                                    },
                                    {
                                        "type": "min",
                                        "value": "1",
                                        "message": "Total household members cannot be less than 1"
                                    },
                                    {
                                        "type": "max",
                                        "value": "10",
                                        "message": "Total household members cannot be more than 10"
                                    }
                                ]
                            }
                        ],
                        "actionLabel": "APPONE_REGISTRATION_HOUSEHOLDDETAILS_ACTION_BUTTON_LABEL_1",
                        "description": "APPONE_REGISTRATION_HOUSEHOLDDETAILS_SCREEN_DESCRIPTION"
                    },
                    {
                        "page": "beneficiaryDetails",
                        "type": "object",
                        "label": "APPONE_REGISTRATION_BENEFICIARYDETAILS_SCREEN_HEADING",
                        "order": 4,
                        "navigateTo": {
                            "name": "beneficiary-details",
                            "type": "template"
                        },
                        "properties": [
                            {
                                "type": "string",
                                "label": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_nameOfIndividual",
                                "order": 1,
                                "value": "",
                                "format": "text",
                                "hidden": false,
                                "tooltip": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_nameOfIndividual_tooltip",
                                "helpText": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_nameOfIndividual_helpText",
                                "infoText": "",
                                "fieldName": "nameOfIndividual",
                                "innerLabel": "",
                                "validations": [
                                    {
                                        "type": "required",
                                        "value": true,
                                        "message": "Required field cannot be empty"
                                    },
                                    {
                                        "type": "minLength",
                                        "value": "2",
                                        "message": "Size must be 2 to 200 characters"
                                    },
                                    {
                                        "type": "maxLength",
                                        "value": "200",
                                        "message": "Size must be 2 to 200 characters"
                                    }
                                ]
                            },
                            {
                                "type": "boolean",
                                "label": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_isHeadOfFamily",
                                "order": 2,
                                "value": false,
                                "format": "checkbox",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "fieldName": "isHeadOfFamily",
                                "innerLabel": "",
                                "validations": [
                                    {
                                        "type": "required",
                                        "value": true,
                                        "message": "Required field cannot be empty"
                                    }
                                ]
                            },
                            {
                                "type": "string",
                                "label": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_identifiers",
                                "order": 3,
                                "value": "",
                                "format": "idPopulator",
                                "hidden": true,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "readOnly": false,
                                "fieldName": "identifiers",
                                "innerLabel": "",
                                "schemaCode": "HCM.ID_TYPE_OPTIONS_POPULATOR",
                                "validations": [
                                    {
                                        "type": "required",
                                        "value": true,
                                        "message": "Required field cannot be empty"
                                    }
                                ],
                                "includeInForm": true,
                                "includeInSummary": false
                            },
                            {
                                "type": "string",
                                "label": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_dobPicker",
                                "order": 5,
                                "value": "",
                                "format": "dob",
                                "hidden": false,
                                "tooltip": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_dobPicker_tooltip",
                                "helpText": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_dobPicker_helpText",
                                "infoText": "",
                                "fieldName": "dobPicker",
                                "innerLabel": "",
                                "validations": []
                            },
                            {
                                "type": "string",
                                "label": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_gender",
                                "order": 6,
                                "value": "",
                                "format": "select",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "fieldName": "gender",
                                "innerLabel": "",
                                "schemaCode": "common-masters.GenderType",
                                "validations": []
                            },
                            {
                                "type": "integer",
                                "label": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_phone",
                                "order": 7,
                                "value": "",
                                "format": "text",
                                "hidden": false,
                                "tooltip": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_phone_tooltip",
                                "helpText": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_phone_helpText",
                                "infoText": "",
                                "fieldName": "phone",
                                "innerLabel": ""
                            },
                            {
                                "type": "string",
                                "label": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_scanner",
                                "order": 8,
                                "value": "",
                                "format": "scanner",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "fieldName": "scanner",
                                "innerLabel": ""
                            }
                        ],
                        "actionLabel": "APPONE_REGISTRATION_BENEFICIARYDETAILS_ACTION_BUTTON_LABEL_1",
                        "description": "APPONE_REGISTRATION_BENEFICIARYDETAILS_SCREEN_DESCRIPTION"
                    },
                    {
                        "page": "HouseholdOverview",
                        "type": "template",
                        "label": "APPONE_REGISTRATION_HOUSEHOLDOVERVIEW_SCREEN_HEADING",
                        "order": 5,
                        "navigateTo": {
                            "name": "beneficiary-details",
                            "type": "template"
                        },
                        "properties": [
                            {
                                "type": "template",
                                "label": "APPONE_REGISTRATION_HOUSEHOLDOVERVIEW_EDIT_HOUSEHOLD",
                                "order": 1,
                                "value": true,
                                "format": "editHousehold",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "readOnly": true,
                                "fieldName": "editHousehold",
                                "deleteFlag": false,
                                "innerLabel": "",
                                "systemDate": false,
                                "validations": [],
                                "isMultiSelect": false
                            },
                            {
                                "type": "template",
                                "enums": [
                                    {
                                        "code": "Individual.name",
                                        "name": "name",
                                        "fieldKey": "name",
                                        "jsonPath": "Individual.name.givenName",
                                        "mandatory": "true"
                                    },
                                    {
                                        "code": "Household.locality",
                                        "name": "locality",
                                        "isList": "true",
                                        "fieldKey": "locality",
                                        "jsonPath": "Household.address.locality.code",
                                        "mandatory": "false"
                                    },
                                    {
                                        "code": "Household.memberCount",
                                        "name": "memberCount",
                                        "fieldKey": "memberCount",
                                        "jsonPath": "Household.memberCount",
                                        "mandatory": "true"
                                    }
                                ],
                                "label": " ",
                                "order": 2,
                                "value": "",
                                "format": "DetailsCard",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "readOnly": false,
                                "fieldName": "DetailsCard",
                                "deleteFlag": false,
                                "innerLabel": "",
                                "systemDate": false,
                                "validations": [],
                                "errorMessage": "",
                                "isMultiSelect": false
                            },
                            {
                                "type": "template",
                                "label": "APPONE_REGISTRATION_HOUSEHOLDOVERVIEW_EDIT_INDIVIDUAL",
                                "order": 3,
                                "value": "",
                                "format": "editIndividual",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "readOnly": true,
                                "fieldName": "editIndividual",
                                "deleteFlag": false,
                                "innerLabel": "",
                                "systemDate": false,
                                "validations": [],
                                "isMultiSelect": false
                            },
                            {
                                "type": "template",
                                "label": "APPONE_REGISTRATION_HOUSEHOLDOVERVIEW_ADD_MEMBER",
                                "order": 4,
                                "value": [],
                                "format": "addMember",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "readOnly": true,
                                "fieldName": "addMember",
                                "deleteFlag": false,
                                "innerLabel": "",
                                "systemDate": false,
                                "validations": [],
                                "isMultiSelect": false
                            },
                            {
                                "type": "template",
                                "label": "APPONE_REGISTRATION_HOUSEHOLDOVERVIEW_DELIVERY_DETAILS_LABEL",
                                "order": 5,
                                "value": "",
                                "format": "PrimaryButton",
                                "hidden": false,
                                "tooltip": "",
                                "helpText": "",
                                "infoText": "",
                                "readOnly": false,
                                "fieldName": "PrimaryButton",
                                "deleteFlag": false,
                                "innerLabel": "",
                                "systemDate": false,
                                "validations": [],
                                "isMultiSelect": false
                            }
                        ],
                        "actionLabel": "",
                        "description": "APPONE_REGISTRATION_HOUSEHOLDOVERVIEW_SCREEN_DESCRIPTION"
                    }
                ],
                "project": "LLIN",
                "summary": true,
                "version": 1,
                "disabled": false
            },
            "isActive": true,
            "auditDetails": {
                "createdBy": "3496b299-06f3-4dd2-8340-573cf8c4f1fc",
                "lastModifiedBy": "3496b299-06f3-4dd2-8340-573cf8c4f1fc",
                "createdTime": 1753782699505,
                "lastModifiedTime": 1753782699505
            }
        }
```

</details>

### 7. CampaignNamingConvention

To add a similar configuration for `HCM-ADMIN-CONSOLE.CampaignNamingConvention`, follow these steps:

<details>

<summary>HCM-ADMIN-CONSOLE.CampaignNamingConvention</summary>

```
[
  {
    "id": 1,
    "data": [
      "CONSOLE_NAMING_CONVENTION_LENGTH_5_TO_32",
      "CONSOLE_NAMING_CONVENTION_NO_LEADING_TRAILING_SPACE",
      "CONSOLE_NAMING_CONVENTION_NO_SPECIAL_SYMBOLS",
      "CONSOLE_NAMING_CONVENTION_NO_REPEAT_SEPARATOR"
    ],
    "isActive": true
  }
]
```

</details>

### 8. FieldPropertiesPanelConfig

<details>

<summary>HCM-ADMIN-CONSOLE.FieldPropertiesPanelConfig</summary>

```
{
    "tab": "validation",
    "label": "maxAge",
    "order": 11,
    "bindTo": "toArray.maxAge",
    "tabOrder": 2,
    "fieldType": "toggle",
    "defaultValue": false,
    "conditionalField": [
      {
        "type": "number",
        "label": "APPCONFIG_MAX_AGE",
        "bindTo": "toArray.maxAge"
      },
      {
        "type": "text",
        "label": "APPCONFIG_ERRORMESSAGE",
        "bindTo": "toArray.maxAge.message"
      }
    ],
    "showFieldOnToggle": true,
    "visibilityEnabledFor": [
      "dob"
    ]
  },
  {
    "tab": "validation",
    "label": "minLength",
    "order": 5,
    "bindTo": "toArray.minLength",
    "tabOrder": 2,
    "fieldType": "toggle",
    "defaultValue": false,
    "conditionalField": [
      {
        "type": "number",
        "label": "APPCONFIG_MIN_LENGTH",
        "bindTo": "toArray.minLength",
        "validation": {
          "pattern": "^(0|[1-9]\\d*)$"
        }
      },
      {
        "type": "text",
        "label": "APPCONFIG_ERRORMESSAGE",
        "bindTo": "toArray.minLength.message"
      }
    ],
    "showFieldOnToggle": true,
    "visibilityEnabledFor": [
      "text",
      "number",
      "mobileNumber"
    ]
  },
{
    "tab": "content",
    "label": "label",
    "order": 2,
    "bindTo": "label",
    "tabOrder": 1,
    "fieldType": "text",
    "defaultValue": false,
    "conditionalField": [],
    "showFieldOnToggle": true,
    "visibilityEnabledFor": [
      "checkbox",
      "numeric",
      "scanner",
      "dob",
      "date",
      "select",
      "dropdown",
      "mobileNumber",
      "number",
      "textArea",
      "text",
      "filter",
      "searchByProximity",
      "searchBar",
      "qrscanner",
      "BeneficiaryRegistrationButton",
      "latLng",
      "administrativeArea",
      "editHousehold",
      "editIndividual",
      "addMember",
      "IndividualDeliverySecondaryButton",
      "IndividualDeliveryPrimaryButton",
      "SecondaryButton",
      "AcknowledgementTitle",
      "AcknowledgementDescription",
      "PrimaryButton",
      "idPopulator",
      "radio",
      "deliveryConditionDialog"
    ]
  }
```

</details>

### 9. FieldTypeMappingConfig

Master Details

HCM-ADMIN-CONSOLE.FieldTypeMappingConfig<br>

<details>

<summary>HCM-ADMIN-CONSOLE.FieldTypeMappingConfig<br></summary>

```
  {
            "id": "63b4d6f0-0d2c-48e1-8390-2bb4dfba8cb3",
            "tenantId": "mz",
            "schemaCode": "HCM-ADMIN-CONSOLE.FieldTypeMappingConfig",
            "uniqueIdentifier": "deliveryConditionDialog",
            "data": {
                "type": "deliveryConditionDialog",
                "order": 18,
                "metadata": {
                    "type": "dynamic",
                    "format": "custom"
                },
                "fieldType": "custom",
                "attributeToRename": {}
            },
            "isActive": true,
            "auditDetails": {
                "createdBy": "b2be1420-4656-407a-9176-5486a964c326",
                "lastModifiedBy": "b2be1420-4656-407a-9176-5486a964c326",
                "createdTime": 1754306116365,
                "lastModifiedTime": 1754306116365
            }
        },
        {
            "id": "5d8fbd68-fb9d-4ce5-88f8-2df57af335bb",
            "tenantId": "mz",
            "schemaCode": "HCM-ADMIN-CONSOLE.FieldTypeMappingConfig",
            "uniqueIdentifier": "editHousehold",
            "data": {
                "type": "editHousehold",
                "metadata": {
                    "type": "template",
                    "format": "editHousehold"
                },
                "fieldType": "editHousehold",
                "attributeToRename": {}
            },
            "isActive": true,
            "auditDetails": {
                "createdBy": "3496b299-06f3-4dd2-8340-573cf8c4f1fc",
                "lastModifiedBy": "3496b299-06f3-4dd2-8340-573cf8c4f1fc",
                "createdTime": 1753783022403,
                "lastModifiedTime": 1753783022403
            }
        },
```

</details>

### 10. DETAILS\_RENDERER\_CONFIG

Master details

HCM-ADMIN-CONSOLE.DETAILS\_RENDERER\_CONFIG

<details>

<summary>HCM-ADMIN-CONSOLE.DETAILS_RENDERER_CONFIG</summary>

```
{
    "entity": "Household",
    "displayFields": [
      {
        "fieldKey": "locality",
        "jsonPath": "Household.address.locality.code",
        "mandatory": "false"
      },
      {
        "fieldKey": "memberCount",
        "jsonPath": "Household.memberCount",
        "mandatory": "false"
      },
      {
        "fieldKey": "pregnantWomenCount",
        "jsonPath": "Household.additionalFields",
        "mandatory": "false",
        "additionalField": "true"
      },
      {
        "fieldKey": "childrenCount",
        "jsonPath": "Household.additionalFields",
        "mandatory": "false",
        "additionalField": "true"
      }
    ]
  },
```

</details>

## Removed Masters

### 1. adminSchemas

## Helm Configurations

Refer [here](project-factory-configuration.md) to learn more about the helm configurations
