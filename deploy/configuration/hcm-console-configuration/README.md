---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-console-configuration
---

# HCM Console Configuration

## Overview

This page explains **how to configure the HCM (Health Campaign Management) Console** using MDMS. These configurations control how campaigns are created, validated, displayed, and executed across web and mobile apps.&#x20;

You will configure:

* Boundaries and hierarchies
* Excel upload validations
* Campaign and delivery behaviour
* App modules, forms, and UI rules
* Supporting configurations (login, help, IDs, templates)

&#x20;See [HCM Service Configuration](../hcm-service-configuration/) for details.

## Steps

{% stepper %}
{% step %}
### Set Up Boundary Master Data (Mandatory)

Boundaries are the foundation of every campaign.\
You must configure a boundary hierarchy before creating campaigns or microplans.

#### 1.1 Create a Boundary Hierarchy

If a hierarchy does not already exist, create one from the Boundary Management screens.

**Example (Hierarchy Type: ADMIN)**

```
Country → Province → District → AdministrativePost → Locality → Village
```

You can define hierarchies at any depth based on campaign needs.

#### 1.2 Configure Hierarchy in MDMS

Navigate to MDMS and configure the hierarchy:

* **Module Name**: `HCM-ADMIN-CONSOLE`
* **Master Name**: `HierarchySchema`

Use the **same hierarchy** for:

* Console
* Campaign
* Microplan

**Keep these values consistent:**

* Hierarchy name
* Lowest hierarchy level
* Split boundary level

**Example**

* Hierarchy: `AdministrativePost`
* Lowest Level: `Locality`&#x20;

#### 1.3 Upload Boundary Data

1. Go to **Boundary Data Management**
2. Click **Create New Boundary Data**
3. Select the hierarchy
4. Download the Excel template
5. Fill in boundary data
6. Upload the file

**Important**

* Headers change automatically if hierarchy levels change
* Data must match the template exactly

{% embed url="https://app.supademo.com/demo/cml68aacq4yhgzsadcgvjdy45?utm_source=link" %}

#### 1.4 Boundary Localisation

Boundary names are automatically localised during upload.

**Localisation Module Format**

```
hcm-boundary-${BOUNDARY_HIERARCHY_TYPE}
```

* Must be lowercase
* Must match the hierarchy type
{% endstep %}

{% step %}
### Configure Hierarchy Behaviour (MDMS)

The hierarchy schema controls **how boundaries are used during campaign flows**.

**MDMS Location**

* Module: `HCM-ADMIN-CONSOLE`
* Master: `HierarchySchema`

#### Key Fields&#x20;

<table><thead><tr><th width="184.640625">Field</th><th>What it controls</th></tr></thead><tbody><tr><td><code>hierarchyType</code></td><td><p></p><ul><li>Contains the different types of hierarchies supported.</li><li>Each hierarchy defines the levels of boundaries available (e.g., Province → District → Locality).</li></ul></td></tr><tr><td><code>isActive</code></td><td><p></p><ul><li>Determines which hierarchy type will be used to create a campaign.</li><li>Only the hierarchy marked as <code>isActive = true</code> will be applied.</li></ul></td></tr><tr><td><code>lowestHierarchy</code></td><td><p></p><ul><li>Represents the <strong>lowest boundary level</strong> visible to users on the boundary selection screen during campaign creation.</li><li>Example: If <code>lowestHierarchy = Locality</code>, the campaign supervisor will select boundaries up to the locality level.</li></ul></td></tr><tr><td><code>splitBoundariesOn</code></td><td><p></p><ul><li>Defines the hierarchy level on which the <strong>target sheet tabs</strong> will be divided.</li><li>Example: If set to <strong>District</strong>, separate target sheets will be created per district.</li></ul></td></tr><tr><td><code>consolidateUsersAt</code></td><td><p></p><ul><li>Used during <strong>microplan integration</strong>.</li><li>Ensures user sheets are consolidated at a particular boundary level so that campaign user assignments (e.g., distributors, supervisors) are correctly populated.</li></ul></td></tr></tbody></table>

{% hint style="info" %}
⚠️ **Recommendation -** Users can change the lowest hierarchy, but it is advised to keep it till the mentioned level because a lot of boundaries will increase the validations and the load on the server to load all the boundaries
{% endhint %}

<details>

<summary>Hierarchy Schema Sample MDMS Data</summary>

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

**Supported Hierarchy Types**

In the **HierarchySchema** configuration, different `type` values are used to define the purpose of each hierarchy. These types determine how the hierarchy will be applied during different stages of the campaign.

Here, we have 4 types used in the campaign flow:

* `"type": "console"`: Used for the Campaign creation flow. Defines the boundary hierarchy structure that will be visible when creating a new campaign
* `"type": "microplan"`: Used for the Microplan creation flow. Ensures that microplans are aligned to the configured boundary hierarchy.
* `"type": "campaign"`: Used for the Boundary Management creation flow. Specifies the hierarchy for managing campaign boundaries once a campaign is set up.
* `"type": "default"`: Serves as the default hierarchy for Boundary Management creation flow and holds default settings.

{% hint style="info" %}
We support the development and handling of various use cases. However, we recommend using the same hierarchy configuration across all types to ensure a seamless flow. This allows for creating a microplan within the same hierarchy, building campaigns on it, and managing the boundary hierarchy consistently.
{% endhint %}
{% endstep %}

{% step %}
### Configure Excel Upload Validations

All Excel uploads (users, facilities, targets) are validated using schemas.

**MDMS Location**

* Module: `HCM-ADMIN-CONSOLE`
* Master: `schemas`

Validations apply at:

* UI level
* Backend level

#### What You Can Control

**Common Schema Properties**

<table><thead><tr><th width="172.97265625"></th><th></th></tr></thead><tbody><tr><td><code>isRequired</code>:</td><td><p></p><ul><li>Marks the columns that must be filled.</li><li><code>true</code> → the column is mandatory.</li><li><code>false</code> → the column is optional.</li></ul></td></tr><tr><td><code>orderNumber</code>:</td><td><p></p><ul><li>Defines the <strong>position</strong> of the column in the Excel sheet.</li><li>Ensures the columns are uploaded in the correct order.</li></ul></td></tr><tr><td><code>title</code></td><td><p></p><ul><li>Represents the schema title.</li><li>Each title is linked to the type of upload (e.g., user upload, campaign upload, etc.).</li></ul></td></tr><tr><td><code>enum</code>:</td><td><p></p><ul><li>Lists the <strong>allowed values</strong> for a field.</li><li>Ensures that only predefined options can be entered (e.g., <code>"Male"</code>, <code>"Female"</code>, <code>"Other"</code> for gender).</li></ul></td></tr><tr><td><code>numberProperties</code>:</td><td><p></p><ul><li>Applies to numeric fields.</li><li><p>Defines constraints such as:</p><ul><li><strong>uniqueness</strong> (whether duplicate values are allowed),</li><li><strong>required status</strong>,</li><li><strong>minimum/maximum limits</strong>.</li></ul></li></ul></td></tr><tr><td><code>stringProperties</code>: </td><td><p></p><ul><li>Applies to text fields.</li><li><p>Defines rules such as:</p><ul><li><strong>required status</strong>,</li><li><strong>uniqueness</strong>,</li><li><strong>length restrictions</strong> (minimum/maximum characters),</li><li><strong>content constraints</strong> (e.g., regex patterns).</li></ul></li></ul></td></tr></tbody></table>

#### Validation Types

* [x] **User Validations**

- **Roles** → Add or remove roles to be validated.
- **Employment Type** → Update the `enum` list to add or remove types.
- **Headers** → All headers are mandatory by default, but you can toggle this by setting `isRequired = true/false`.

* [x] **Facility Validations**

- **Facility Type** → Add or delete facility categories.
- **Facility Status** → Add or delete status options.
- **Facility Usage** → Add or delete usage options.
- **Capacity** → Adjust `minimum` and `maximum` values.
- **Facility Name** → Update constraints for `minLength` and `maxLength`.
- **Headers** → All headers are mandatory by default; adjust using `isRequired`.

* [x] **Target Validations**

- **Target** → Adjust `minimum` and `maximum` validations.
- **Boundary Code** → Mandatory field.
- **Target Header** → Mandatory field.
- **Campaign Type** → Based on the selected campaign type, boundary targets are updated.
- **Custom Columns** → New target columns can be introduced if required.

<details>

<summary>Admin Schema Sample MDMS Data</summary>

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

{% hint style="info" %}
Since the V1 API is deprecated, it used `HCM-ADMIN-CONSOLE.adminSchema`, which is no longer used. All V2 APIs now use `HCM-ADMIN-CONSOLE.schemas`. Add the admin schema when introducing a new campaign or project type.
{% endhint %}
{% endstep %}

{% step %}
### Configure Attributes (Beneficiary Data)

The schema includes a **list of attribute configurations**, where each attribute is:

* Identified by a **unique key**,
* Defined with a **code**, and
* Linked to an **internationalisation key (i18nKey)** for multi-language support.

**Example Attributes**The following attributes are available for use in campaigns to capture beneficiary information:

* **Age**
* **Height**
* **Weight**
* **Gender**

These attributes ensure that consistent, standardised data points are collected across campaigns.

<div align="left"><figure><img src="../../../.gitbook/assets/image (130).png" alt="" width="375"><figcaption></figcaption></figure></div>

The **attribute dropdown** in the system is dynamically populated from the `attributeConfig` schema. This schema defines the set of attributes available for selection during campaign setup or data entry.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `attributeConfig`&#x20;

<details>

<summary>Attribute Config Sample MDMS Data</summary>

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
{% endstep %}

{% step %}
### Configure Upload Processing Timings

Controls how often the system checks the upload status. The schema defines the rules for how frequently the system should call the **search API** after a file upload. The purpose of these calls is to check the **validation status** of the uploaded file.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `baseTimeOut`&#x20;
* [baseTimeOut.json](https://raw.githubusercontent.com/egovernments/egov-mdms-data/UNIFIED-QA/data/mz/health/hcm-admin-console/baseTimeOut.json)

#### How It Works

* **Base Time**
  * Defines the minimum interval after which the search API is triggered.
* **Dynamic Interval Calculation**
  * The actual interval = **baseTime × number of fields in the uploaded sheet**.
  * This interval is constrained by:
    * **Minimum base time** (lower limit), and
    * **maxTime** (upper limit).
* **Search API Calls**
  * The search API is called repeatedly at the calculated interval.
  * Calls stop only when a **successful** or **failed** response is received.
* **TimelineRefetch**
  * Configured to call the getProcessAPI of the timeline periodically.
  * Ensures the process status is kept up to date after a certain interval.

<details>

<summary>Base Time Out Sample MDMS Data</summary>

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
{% endstep %}

{% step %}
### Configure Campaign & Delivery Behaviour

The **delivery configuration schema** is used to define how **deliveries** are displayed in the system. It distinguishes between:

* **Direct Deliveries** → Items or services provided directly to the beneficiary.
* **Indirect Deliveries** → Items or services provided through an intermediary (e.g., via a facility, distributor, or supervisor).
* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `deliveryTypeConfig`

<details>

<summary>Delivery Time Config Sample MDMS Data</summary>

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
{% endstep %}

{% step %}
### Mail Configurations

The **mailConfig** schema is used to define the **default email ID** for contacting the **L1 support team** or the **implementation team**. This comes into play when a user requests a hierarchy that is not currently available in the system.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `mailConfig`&#x20;

<details>

<summary>Mail Config Sample MDMS Data</summary>

```
[
    {
        "mailId": "L1team@email.com"
    }
]
```

</details>
{% endstep %}

{% step %}
### Operator Configuration

The **operatorConfig** schema defines all the **operator options** that can be applied to attributes. These operators are used in the system for filtering, validation, and logical conditions during campaign configuration and execution.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `operatorConfig`&#x20;

<figure><img src="../../../.gitbook/assets/image (131).png" alt=""><figcaption></figcaption></figure>

<details>

<summary>Operator Config Sample MDMS Data</summary>

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
{% endstep %}

{% step %}
### Product Type Configuration

The **productType** schema defines the list of **resource types** that can be selected in the system. If a required resource type is not already available, it can be added through this schema. Once added, the new resource type will automatically appear in the **resources dropdown**.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `productType`&#x20;

<figure><img src="../../../.gitbook/assets/image (132).png" alt=""><figcaption></figcaption></figure>

<details>

<summary>Product Type Sample MDMS Data</summary>

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
{% endstep %}

{% step %}
### ReadMe Configuration

The **ReadMeConfig** schema defines the **information messages** that are displayed both in the **UI** and in the **ReadMe sheet** of the downloaded Excel templates. These messages act as **instructions** for users, guiding them on how to correctly fill in the upload templates.

* **Module Name:** `HCM-ADMIN-CONSOLE`
* **Master Name:** `ReadMeConfig`&#x20;

<figure><img src="../../../.gitbook/assets/image (133).png" alt=""><figcaption></figcaption></figure>

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

Below is an example of how data is entered into the read-me schema for the headers and their description:

<details>

<summary>ReadMe Config Sample MDMS Data</summary>

```
[
{
                "type": "unified-console",
                "texts": [
                    {
                        "header": "UNIFIED_CONSOLE_README_HEADER_1",
                        "inSheet": false,
                        "inUiInfo": true,
                        "descriptions": [
                            {
                                "text": "UNIFIED_CONSOLE_README_HEADER_1_DESC_1",
                                "isStepRequired": true
                            },
                            {
                                "text": "UNIFIED_CONSOLE_README_HEADER_1_DESC_2",
                                "isStepRequired": true
                            }
                        ],
                        "isHeaderBold": true
                    }
                ]
            },
{
                "type": "user",
                "texts": [
                    {
                        "header": "USERWITHBOUNDARY_README_HEADER_1",
                        "inSheet": false,
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
                        ],
                        "isHeaderBold": true
                    },
                    {
                        "header": "USERWITHBOUNDARY_README_HEADER_2",
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
                        ],
                        "isHeaderBold": true
                    },
                    {
                        "header": "USERWITHBOUNDARY_README_HEADER_3",
                        "inSheet": true,
                        "inUiInfo": true,
                        "descriptions": [
                            {
                                "text": "USERWITHBOUNDARY_README_HEADER_3_DESC_1",
                                "isStepRequired": false
                            },
                            {
                                "text": "USERWITHBOUNDARY_README_HEADER_3_DESC_2",
                                "isStepRequired": false
                            }
                        ],
                        "isHeaderBold": true
                    }
                ]
            },{
                "type": "facilityWithBoundary",
                "texts": [
                    {
                        "header": "FACILITYWITHBOUNDARY_README_HEADER_1",
                        "inSheet": false,
                        "inUiInfo": true,
                        "descriptions": [
                            {
                                "text": "FACILITYWITHBOUNDARY_README_HEADER_1_DESC_1",
                                "isStepRequired": true
                            },
                            {
                                "text": "FACILITYWITHBOUNDARY_README_HEADER_1_DESC_2",
                                "isStepRequired": true
                            }
                        ],
                        "isHeaderBold": true
                    },
                    {
                        "header": "FACILITYWITHBOUNDARY_README_HEADER_2",
                        "inSheet": true,
                        "inUiInfo": true,
                        "descriptions": [
                            {
                                "text": "FACILITYWITHBOUNDARY_README_HEADER_2_DESC_1",
                                "isStepRequired": true
                            },
                            {
                                "text": "FACILITYWITHBOUNDARY_README_HEADER_2_DESC_2",
                                "isStepRequired": true
                            },
                            {
                                "text": "FACILITYWITHBOUNDARY_README_HEADER_2_DESC_3",
                                "isStepRequired": true
                            },
                            {
                                "text": "FACILITYWITHBOUNDARY_README_HEADER_2_DESC_4",
                                "isStepRequired": true
                            },
                            {
                                "text": "FACILITYWITHBOUNDARY_README_HEADER_2_DESC_5",
                                "isStepRequired": false
                            },
                            {
                                "text": "FACILITYWITHBOUNDARY_README_HEADER_2_DESC_6",
                                "isStepRequired": false
                            },
                            {
                                "text": "FACILITYWITHBOUNDARY_README_HEADER_2_DESC_7",
                                "isStepRequired": false
                            }
                        ],
                        "isHeaderBold": true
                    },
                    {
                        "header": "FACILITYWITHBOUNDARY_README_HEADER_3",
                        "inSheet": true,
                        "inUiInfo": true,
                        "descriptions": [
                            {
                                "text": "FACILITYWITHBOUNDARY_README_HEADER_3_DESC_1",
                                "isStepRequired": false
                            },
                            {
                                "text": "FACILITYWITHBOUNDARY_README_HEADER_3_DESC_2",
                                "isStepRequired": false
                            },
                            {
                                "text": "FACILITYWITHBOUNDARY_README_HEADER_3_DESC_3",
                                "isStepRequired": false
                            }
                        ],
                        "isHeaderBold": true
                    }
                ]
            }
]
```

</details>
{% endstep %}

{% step %}
### Login & Privacy Configuration

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
[
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
                        "key": "city",
                        "type": "dropdown",
                        "label": "CORE_COMMON_CITY",
                        "disable": false,
                        "populators": {
                            "name": "city",
                            "error": "ERR_HRMS_INVALID_CITY",
                            "mdmsConfig": {
                                "select": "(data)=>{ return Array.isArray(data['tenant'].tenants) && Digit.Utils.getUnique(data['tenant'].tenants).map(ele=>({code:ele.code,name:Digit.Utils.locale.getTransformedLocale('TENANT_TENANTS_'+ele.code)}))}",
                                "masterName": "tenants",
                                "moduleName": "tenant",
                                "localePrefix": "TENANT_TENANTS"
                            },
                            "optionsKey": "name"
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
                        "isMandatory": false,
                        "withoutLabel": true
                    }
                ]
            }
]
```

</details>

{% hint style="info" %}
configure banner images relevant to the product deployment and use case
{% endhint %}
{% endstep %}

{% step %}
### Policy Configurations

This configuration displays the data in the privacy pop-up. An example of the configuration is shown below:

<details>

<summary>Policy MDMS Data</summary>

```json
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

Type can be the following:

* **`null:`**
  * When `type` is `null`, it indicates that the description is just plain text.
* **`point:`**
  * When `type` is set to `point`, it likely means that the description should be displayed as a bullet point or list item.
* **`step:`**
  * When `type` is set to `step`, it suggests that the description is part of a sequence of steps.
* **subdescriptions**: to show the sub-descriptions at the point.
{% endstep %}

{% step %}
### Date with Boundary Configurations

This configuration is used when you want to update the dates with or without the selected boundaries. If the flag is false, it updates the dates at the country level by default. If you want to update the dates at the lower boundary levels, then make the flag true.

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `dateWithBoundary`

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
{% endstep %}

{% step %}
### Project Type Configurations

This configuration is now used in place of the delivery configuration.

This is used to store all the pre-required conditions for the delivery conditions screens.

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `projectTypes`

<details>

<summary>ProjectTypes MDMS Data</summary>

```json
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
{% endstep %}

{% step %}
### Roles For Checklist&#x20;

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `rolesForChecklist`

This master data is used to show the dropdown of roles in the checklist screens -

<details>

<summary>Roles for Checklist Config Sample MDMS Data</summary>

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
{% endstep %}

{% step %}
### Checklist Templates

This master data is used to create a default template of the checklist for the selected campaign + role + checklist type -

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `ChecklistTemplates`

<details>

<summary>Checklist Templates Sample MDMS Data</summary>

```
{
    "code": "SingleValueList",
    "type": [
        "checklist"
    ]
}
```

</details>
{% endstep %}

{% step %}
### App Field Types

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `appFieldTypes`

This is used to describe the type of questions available in the dropdown while configuring the checklist.

<details>

<summary>App Field Types Config Sample MDMS Data</summary>

```
{
    "code": "SingleValueList",
    "type": [
        "checklist"
    ]
}
```

</details>
{% endstep %}

{% step %}
### Microplan Integration

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `microplanIntegration`

This master is utilised for the microplan data fetching. Here, 'type' refers to the data template that needs to be filled. 'To' and 'from' pertain to the microplan data, and while populating campaign data, various filter conditions, such as 'includes', or 'equals', can be applied.

<details>

<summary>Microplan integration MDMS Data</summary>

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
{% endstep %}

{% step %}
### IdGen Configuration

To enable the generation of unique identifiers via the idGen service, the following data must be added to the MDMS under `moduleName=common-masters` and `masterName=IdFormat`.

* Master Name: **common-master**s
* ModuleName: **IdFormat**

<details>

<summary>IdFormat Sample Data</summary>

```
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

<summary>troubleshooting if any user creation or campaign creation is due to the number generation</summary>

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
    CACHE 1
```

</details>
{% endstep %}

{% step %}
### Target Configuration

This configuration is used to define the mapping of target-related data from the target sheet to different beneficiary types. Each beneficiary type can be associated with one or more columns from the target sheet, which hold the respective target values.

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `targetConfigs`

**Key Details:**

* **campaignType**: Specifies the campaign type this configuration applies to (e.g., "LLIN-mz").
* **beneficiaries**: A list of beneficiary types, each having:
  * **columns**: The columns in the target sheet that map to this beneficiary type.
  * **beneficiaryType**: The type of beneficiary (e.g., "INDIVIDUAL", "HOUSEHOLD", "PRODUCT").

<details>

<summary>HCM-ADMIN-CONSOLE.targetConfigs</summary>

```
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
{% endstep %}

{% step %}
### Help Tutorial

This configuration is used to define help tutorial content for the users during the flow. It provides contextual help videos, guided tours, and documentation links based on the current screen.

* Master Name: `commonUiConfig`
* ModuleName: `HelpTutorial`&#x20;

<details>

<summary>Help Tutorial Sample MDMS Data</summary>

```
[
{
                "module": "campaign",
                "helpContent": [
                    {
                        "url": "https://youtu.be/_yxD9Wjqkfw?feature=shared",
                        "icon": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/helpimages/proximity.png",
                        "order": 0,
                        "pages": [
                            "new-app-configuration-redesign"
                        ],
                        "title": "CMN_CAMP_START_CONFIG_FORMS",
                        "iconBackground": "#F6F0E8"
                    },
                    {
                        "url": "https://youtu.be/_yxD9Wjqkfw?feature=shared",
                        "icon": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/helpimages/proximity.png",
                        "order": 0,
                        "pages": [
                            "new-app-modules"
                        ],
                        "title": "CMN_CAMP_TUTORIALS",
                        "tours": [
                            {
                                "title": "To explore Tutorials",
                                "target": ".camp-help-button-new-app-modules",
                                "content": "Welcome to Manage Master Data screen. Here you can search and update any master data that is configured for the logged in user tenant",
                                "placement": "bottom",
                                "disableBeacon": true
                            },
                            {
                                "title": "To configure different modules",
                                "target": ".module-card",
                                "content": "Select any module name where the master is present",
                                "placement": "top",
                                "disableBeacon": true
                            },
                            {
                                "title": "To configure / edit module configs",
                                "target": ".campaign-module-button",
                                "content": "Select any master name where the master is present",
                                "placement": "bottom",
                                "disableBeacon": true
                            },
                            {
                                "title": "To close the App config and proceed with Campaign creation",
                                "target": ".action-bar-individual-action-field",
                                "content": "Select any master name where the master is present",
                                "placement": "top",
                                "disableBeacon": true
                            }
                        ],
                        "iconBackground": "#F6F0E8"
                    },
                    {
                        "url": "https://youtu.be/_yxD9Wjqkfw?feature=shared",
                        "icon": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/helpimages/mapView.png",
                        "order": 1,
                        "pages": [
                            "new-app-modules",
                            "new-app-configuration-redesign"
                        ],
                        "title": "CMN_CAMP_HOW_TO_CONFIG_MAPVIEW",
                        "iconBackground": "#F6EBE8"
                    },
                    {
                        "url": "https://youtu.be/_yxD9Wjqkfw?feature=shared",
                        "icon": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/helpimages/qrScanner.png",
                        "order": 2,
                        "pages": [
                            "new-app-modules",
                            "new-app-configuration-redesign"
                        ],
                        "title": "CMN_CAMP_PREVIEW_APPLICATIONS",
                        "iconBackground": "#F1F6E8"
                    },
                    {
                        "url": "https://youtu.be/_yxD9Wjqkfw?feature=shared",
                        "icon": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/helpimages/proximity.png",
                        "order": 3,
                        "pages": [
                            "new-app-modules",
                            "new-app-configuration-redesign"
                        ],
                        "title": "CMN_CAMP_OFFLINE_QR_SCANNER",
                        "iconBackground": "#E8F4F6"
                    },
                    {
                        "url": "https://youtu.be/_yxD9Wjqkfw?feature=shared",
                        "icon": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/helpimages/qrScanner.png",
                        "order": 4,
                        "pages": [
                            "new-app-modules",
                            "new-app-configuration-redesign"
                        ],
                        "title": "CMN_CAMP_OFFLINE_DATA_SHARING",
                        "iconBackground": "#F1F6E8"
                    },
                    {
                        "url": "https://youtu.be/_yxD9Wjqkfw?feature=shared",
                        "icon": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/helpimages/mapView.png",
                        "order": 5,
                        "pages": [
                            "new-app-modules",
                            "new-app-configuration-redesign"
                        ],
                        "title": "CMN_CAMP_HOW_TO_CONFIG_LOCATIONTAG",
                        "iconBackground": "#F6EBE8"
                    },
                    {
                        "url": "https://youtu.be/_yxD9Wjqkfw?feature=shared",
                        "icon": "https://egov-dev-assets.s3.ap-south-1.amazonaws.com/hcm/helpimages/mapView.png",
                        "order": 6,
                        "pages": [
                            "new-app-modules",
                            "new-app-configuration-redesign"
                        ],
                        "title": "CMN_CAMP_HOW_TO_CONFIG_ADMIN_AREA",
                        "iconBackground": "#F6EBE8"
                    }
                ]
            }
]
```

</details>

**tours (Guided Tour Steps)**

For interactive page walkthroughs, each tour step contains:

<table data-header-hidden><thead><tr><th width="138.16015625">Property</th><th width="145.36328125">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>title</code></td><td>string</td><td>Tour step title</td></tr><tr><td><code>target</code></td><td>string</td><td>CSS selector for the target element (e.g., <code>.module-card</code>)</td></tr><tr><td><code>content</code></td><td>string</td><td>Description text for the tour step</td></tr><tr><td><code>placement</code></td><td>string</td><td>Tooltip placement (<code>top</code>, <code>bottom</code>, <code>left</code>, <code>right</code>)</td></tr><tr><td><code>disableBeacon</code></td><td>boolean</td><td>Whether to disable the beacon animation</td></tr></tbody></table>

**How It Works**

**module**

The application module this help content belongs to (e.g., `campaign`).

**helpContent**

Array of help items to display. Each item contains:

<table><thead><tr><th width="146.421875">Property</th><th width="100.32421875">Type</th><th width="112.2265625">Required</th><th>Description</th></tr></thead><tbody><tr><td><code>title</code></td><td>string</td><td>Yes</td><td>Localization key for the help item title</td></tr><tr><td><code>url</code></td><td>string</td><td>Yes</td><td>URL to the tutorial video or documentation</td></tr><tr><td><code>icon</code></td><td>string</td><td>Yes</td><td>URL to the icon/thumbnail image</td></tr><tr><td><code>order</code></td><td>number</td><td>No</td><td>Display order of the help item</td></tr><tr><td><code>pages</code></td><td>array</td><td>No</td><td>List of page paths where this help item should appear</td></tr><tr><td><code>iconBackground</code></td><td>string</td><td>No</td><td>Background color for the icon (hex code)</td></tr><tr><td><code>actionText</code></td><td>string</td><td>No</td><td>Localization key for the action button text</td></tr><tr><td><code>subtitle</code></td><td>string</td><td>No</td><td>Localization key for subtitle text</td></tr><tr><td><code>cta</code></td><td>string</td><td>No</td><td>Call-to-action text</td></tr><tr><td><code>tours</code></td><td>array</td><td>No</td><td>Array of guided tour steps (for interactive walkthroughs)</td></tr></tbody></table>
{% endstep %}

{% step %}
### Allowed Modules Configurations

This configuration is used to restrict the App Config from deselecting certain modules. It defines the mandatory modules that must be selected for each project type during campaign setup. Users cannot proceed without selecting all the allowed (required) modules.

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `AllowedModules`

**How It Works**

**projectType**

The project type code for which this configuration applies (e.g., `Bednets`, `IRS-mz`, `MR-DN`).

**allowedModule**

Array of module codes that are mandatory for this project type. These modules cannot be unselected by users.

**Example Data**

<details>

<summary>AllowedModules Sample Data</summary>

```
[
 {
                "projectType": "Bednets",
                "allowedModule": [
                    "REGISTRATION",
                    "COMPLAINTS",
                    "INVENTORY"
                ]
},
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
{% endstep %}

{% step %}
### App Link Configurations&#x20;

This configuration is used to provide the Downloadable APK link after the campaign is created. So APK needs to be manually generated [here](https://github.com/egovernments/health-campaign-field-worker-app/actions) and update the link in this master![](https://images.gitbook.com/__img/dpr=2,width=760,onerror=redirect,format=auto,signature=-957866975/https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2Fmb5VUHEnO0msarLMPz6q%2Fblobs%2FF7jbh8cRvv1NoTfs1BUR%2FScreenshot%202025-09-23%20at%202.56.12%E2%80%AFPM.png)

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `AppLink`&#x20;

<details>

<summary>App Link Sample Config Data</summary>

```
[
  {
    "appLink": "https://drive.google.com/drive/folders/1x41en8O7ZpgZfGm0G7X_TCsmrldItPTm"
  }
]

```

</details>

<div align="left"><figure><img src="../../../.gitbook/assets/image (134).png" alt="" width="288"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### App Module Schema Configurations

This configuration is used to define the modules and their features in the App Config flow. It specifies which features are available for each module and controls their visibility and behaviour.

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `AppModuleSchema`

#### How It Works

**code**

Unique identifier for the module (e.g., `REGISTRATIONFLOW`, `DELIVERYFLOW`, `COMPLAINTS`, `INVENTORY`).

**description**

Localisation key for the module description (e.g., `REGISTRATION_DESC`, `DELIVERY_DESC`).

**features**

Array of feature configurations is available for this module. Each feature contains:

<table><thead><tr><th width="132.31640625">Property</th><th width="129.5234375">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>code</code></td><td>string</td><td>Unique feature identifier (e.g., <code>QR_CODE_SCANNER</code>, <code>PROXIMITY_SEARCH</code>)</td></tr><tr><td><code>description</code></td><td>string</td><td>Localization key for the feature description</td></tr><tr><td><code>type</code></td><td>string</td><td>(Optional) Feature type (<code>form</code>, <code>template</code>)</td></tr><tr><td><code>format</code></td><td>string</td><td>(Optional) Field format mapping (e.g., <code>scanner</code>, <code>searchByProximity</code>)</td></tr><tr><td><code>order</code></td><td>number</td><td>(Optional) Display order of the feature</td></tr><tr><td><code>disabled</code></td><td>boolean</td><td>(Optional) Whether the feature is disabled/hidden (<code>true</code>/<code>false</code>)</td></tr></tbody></table>

**Available Modules**

<table><thead><tr><th width="240.21875">Module Code</th><th>Description</th></tr></thead><tbody><tr><td><code>REGISTRATIONFLOW</code></td><td>Registration flow module</td></tr><tr><td><code>DELIVERYFLOW</code></td><td>Delivery flow module</td></tr><tr><td><code>COMPLAINTFLOW</code></td><td>Complaints flow module</td></tr><tr><td><code>INVENTORY</code></td><td>Inventory/Stock management module</td></tr><tr><td><code>ATTENDANCE</code></td><td>Attendance tracking module</td></tr><tr><td><code>HFREFERALFLOW</code></td><td>Health facility referral flow</td></tr><tr><td><code>REGISTRATIONANDDELVFLOW</code></td><td>Combined registration and delivery flow</td></tr></tbody></table>

**Available Features**

<table><thead><tr><th width="228.875">Feature Code</th><th>Description</th></tr></thead><tbody><tr><td><code>QR_CODE_SCANNER</code></td><td>QR/Barcode scanning capability</td></tr><tr><td><code>PROXIMITY_SEARCH</code></td><td>Search by GPS proximity</td></tr><tr><td><code>SEARCH_BY_ID</code></td><td>Search by beneficiary ID</td></tr><tr><td><code>MAP_VIEW</code></td><td>Map view for locations</td></tr><tr><td><code>OFFLINE_DATA_SHARING</code></td><td>Offline data sync capability</td></tr><tr><td><code>FACILITY_SEARCH</code></td><td>Search facilities</td></tr><tr><td><code>SEARCH_COMPLAINTS</code></td><td>Search complaints</td></tr></tbody></table>

**Example Data**

<details>

<summary>HCM-ADMIN-CONSOLE.AppModuleSchema</summary>

```
[
  {
                "code": "HFREFERALFLOW",
                "features": [
                    {
                        "code": "QR_CODE_SCANNER",
                        "type": "template",
                        "order": 1,
                        "format": "SecondaryButton",
                        "disabled": false,
                        "description": "QR_CODE_SCANNER_DESC"
                    }
                ],
                "description": "HFREFERALFLOW_DESC"
            },
 {
                "code": "COMPLAINTFLOW",
                "features": [
                    {
                        "code": "SEARCH_COMPLAINTS",
                        "type": "form",
                        "order": 2,
                        "format": "searchComplaints",
                        "disabled": false,
                        "description": "SEARCH_COMPLAINTS_DESC"
                    }
                ],
                "description": "COMPLAINTS_DESC"
            },
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
            },{
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
            },{
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
                        "code": "SEARCH_BY_ID",
                        "type": "template",
                        "order": 1,
                        "format": "searchByID",
                        "disabled": false,
                        "description": "SEARCH_BY_ID_DESC"
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
            },{
                "code": "REGISTRATIONFLOW",
                "features": [
                    {
                        "code": "QR_CODE_SCANNER",
                        "disabled": false,
                        "description": "QR_CODE_SCANNER_DESC"
                    },
                    {
                        "code": "PROXIMITY_SEARCH",
                        "disabled": false,
                        "description": "PROXIMITY_SEARCH_DESC"
                    },
                    {
                        "code": "MAP_VIEW",
                        "disabled": true,
                        "description": "MAP_VIEW_DESC"
                    },
                    {
                        "code": "OFFLINE_DATA_SHARING",
                        "disabled": true,
                        "description": "OFFLINE_DATA_SHARING_DESC"
                    }
                ],
                "description": "REGISTRATION_DESC"
            },{
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
            },{
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
            }, {
                "code": "COMPLAINTS",
                "features": [
                    {
                        "code": "PROXIMITY_SEARCH",
                        "type": "template",
                        "order": 2,
                        "format": "searchByProximity",
                        "disabled": false,
                        "description": "PROXIMITY_SEARCH_DESC"
                    }
                ],
                "description": "COMPLAINTS_DESC"
            },{
                "code": "ATTENDANCE",
                "features": [],
                "description": "ATTENDANCE_DESC"
            }
]

```

</details>
{% endstep %}

{% step %}
### App Screen Localisation Configurations

This configuration is used to define the properties for which localisation should be enabled in the App Config flow. It determines which properties in the app configuration screens should show the localisation input fields (multi-language support).

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `AppScreenLocalisationConfig`&#x20;

#### How It Works

**screenName**

Unique identifier for the configuration (e.g., `appScreenConfig`).

**LocalisationModule**

The localisation module name used for storing translations (e.g., `configure-app`).

**moduleVersion**

Current version of the module configuration.

**minModuleVersion**

Minimum supported module version for backward compatibility.

**fields**

Array of field type configurations. Each entry defines which properties can be localized for that field type.

<table><thead><tr><th width="200.87109375">Property</th><th width="113.21484375">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>fieldType</code></td><td>string</td><td>The field type identifier (e.g., <code>text</code>, <code>dropdown</code>, <code>date</code>)</td></tr><tr><td><code>localisableProperties</code></td><td>array</td><td>List of property names that support localisation</td></tr></tbody></table>

#### Common Localisable Properties

<table><thead><tr><th width="216.09765625">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>label</code></td><td>Field label text</td></tr><tr><td><code>helpText</code></td><td>Help text displayed below the field</td></tr><tr><td><code>tooltip</code></td><td>Tooltip text on hover</td></tr><tr><td><code>innerLabel</code></td><td>Placeholder text inside the field</td></tr><tr><td><code>errorMessage</code></td><td>Validation error message</td></tr><tr><td><code>message</code></td><td>General message text</td></tr><tr><td><code>dropDownOptions</code></td><td>Dropdown option labels (for dropdo</td></tr></tbody></table>

#### Example Data

<details>

<summary>App Screen Localisation Config</summary>

```
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
                    },
                    {
                        "fieldType": "searchByID",
                        "localisableProperties": [
                            "label",
                            "message"
                        ]
                    },
                    {
                        "fieldType": "sortComplaints",
                        "localisableProperties": [
                            "label",
                            "message"
                        ]
                    },
                    {
                        "fieldType": "searchComplaints",
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
{% endstep %}

{% step %}
### Form Config Template

This master serves as the base template for mobile app form configuration screens. When a new campaign is created, the system copies the relevant template configuration for the selected project type and uses it as the starting point for app configuration.<br>

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `FormConfigTemplate`&#x20;

#### How It Works

**name**

Module name identifier (e.g., `REGISTRATION`, `DELIVERY`, `COMPLAINTS`, `ATTENDANCE`, `MANAGESTOCK`).

**project**

Project type code this template belongs to (e.g., `IRS-mz`, `MR-DN`, `LLIN-mz`, `DEFAULT`).

**flows**

Array of flow configurations within the module. Each flow contains:

<table><thead><tr><th width="150.02734375">Property</th><th width="156.859375">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>name</code></td><td>string</td><td>Flow identifier (e.g., <code>MANAGESTOCK</code>, <code>REGISTRATION-DELIVERY</code>)</td></tr><tr><td><code>pages</code></td><td>array</td><td>Array of page configurations</td></tr><tr><td><code>version</code></td><td>number</td><td>Version number of the flow</td></tr><tr><td><code>disabled</code></td><td>boolean</td><td>Whether the flow is disabled</td></tr><tr><td><code>isSelected</code></td><td>boolean</td><td>Whether the flow is selected for the campaign</td></tr><tr><td><code>screenType</code></td><td>string</td><td>Type of screen (<code>FORM</code>, <code>TEMPLATE</code>)</td></tr></tbody></table>

**pages**

Each page within a flow contains:

<table><thead><tr><th width="133.1640625">Property</th><th width="172.0703125">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>page</code></td><td>string</td><td>Page identifier (e.g., <code>stockDetails</code>, <code>warehouseDetails</code>)</td></tr><tr><td><code>type</code></td><td>string</td><td>Page type (<code>object</code>)</td></tr><tr><td><code>label</code></td><td>string</td><td>Screen heading localization key</td></tr><tr><td><code>order</code></td><td>number</td><td>Display order of the page</td></tr><tr><td><code>description</code></td><td>string</td><td>Screen description localization key</td></tr><tr><td><code>actionLabel</code></td><td>string</td><td>Action button label localization key</td></tr><tr><td><code>navigateTo</code></td><td>object</td><td>Navigation configuration (<code>name</code>, <code>type</code>)</td></tr><tr><td><code>properties</code></td><td>array</td><td>Array of field configurations</td></tr></tbody></table>

**properties (Fields)**

Each field within a page contains properties.

#### Example Data

<details>

<summary>Form Config Template</summary>

```
[
{
                "name": "ATTENDANCE",
                "flows": [
                    {
                        "name": "MANAGESTOCK",
                        "pages": [
                            {
                                "page": "stockProductDetails",
                                "type": "object",
                                "label": "APP_CONFIG_INVENTORY_stockProductDetails_SCREEN_HEADING",
                                "order": 3,
                                "navigateTo": {
                                    "name": "stock-acknowledgement",
                                    "type": "template"
                                },
                                "properties": [
                                    {
                                        "type": "string",
                                        "label": "APP_CONFIG_INVENTORY_stockProductDetails_WAYBILL_LABEL",
                                        "order": 1,
                                        "value": "",
                                        "format": "text",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_stockProductDetails_ENTER_THE_WAYBILL_NUMBER_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "wayBillNumber",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [],
                                        "errorMessage": "",
                                        "isMultiSelect": false
                                    },
                                    {
                                        "type": "string",
                                        "label": "APP_CONFIG_INVENTORY_stockProductDetails_BATCH_NUMBER_LABEL",
                                        "order": 2,
                                        "value": "",
                                        "format": "text",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_stockProductDetails_ENTER_THE_BATCH_NUMBER_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "batchNumber",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [],
                                        "errorMessage": "",
                                        "isMultiSelect": false
                                    },
                                    {
                                        "type": "string",
                                        "label": "APP_CONFIG_INVENTORY_stockProductDetails_EXPIRY_DATE_LABEL",
                                        "order": 3,
                                        "value": "",
                                        "format": "date",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_stockProductDetails_SELECT_THE_EXPIRY_DATE_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "expiryDate",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [
                                            {
                                                "type": "required",
                                                "value": true,
                                                "message": "APP_CONFIG_INVENTORY_stockProductDetails_EXPIRY_DATE_IS_REQUIRED_MESSAGE"
                                            }
                                        ],
                                        "errorMessage": "",
                                        "isMultiSelect": false
                                    },
                                    {
                                        "type": "string",
                                        "label": "APP_CONFIG_INVENTORY_stockProductDetails_QUANTITY_SENT_LABEL",
                                        "order": 4,
                                        "value": "",
                                        "format": "text",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_stockProductDetails_ENTER_THE_QUANTITY_SENT_BY_THE_WAREHOUSE_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "quantitySent",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [
                                            {
                                                "type": "required",
                                                "value": true,
                                                "message": "APP_CONFIG_INVENTORY_stockProductDetails_QUANTITY_SENT_IS_REQUIRED_MESSAGE"
                                            }
                                        ],
                                        "errorMessage": "",
                                        "isMultiSelect": false
                                    },
                                    {
                                        "type": "string",
                                        "label": "APP_CONFIG_INVENTORY_stockProductDetails_QUANTITY_RECEIVED_LABEL",
                                        "order": 5,
                                        "value": "",
                                        "format": "text",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_stockProductDetails_ENTER_THE_ACTUAL_QUANTITY_RECEIVED_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "quantityReceived",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [
                                            {
                                                "type": "required",
                                                "value": true,
                                                "message": "APP_CONFIG_INVENTORY_stockProductDetails_QUANTITY_RECEIVED_IS_REQUIRED_MESSAGE"
                                            }
                                        ],
                                        "errorMessage": "",
                                        "isMultiSelect": false,
                                        "visibilityCondition": {
                                            "expression": "stockDetails.facilityFromWhich!=National Warehouse"
                                        }
                                    },
                                    {
                                        "type": "string",
                                        "label": "APP_CONFIG_INVENTORY_stockProductDetails_COMMENT_LABEL",
                                        "order": 7,
                                        "value": "",
                                        "format": "textArea",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_stockProductDetails_ADD_COMMENTS_IF_QUANTITIES_DIFFER_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "comment",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [],
                                        "errorMessage": "",
                                        "isMultiSelect": false,
                                        "visibilityCondition": {
                                            "expression": "stockProductDetails.quantitySent!=stockProductDetails.quantityReceived"
                                        }
                                    },
                                    {
                                        "type": "string",
                                        "enums": [],
                                        "label": "APP_CONFIG_INVENTORY_stockProductDetails_SCAN_RESOURCE_LABEL",
                                        "order": 8,
                                        "value": "",
                                        "format": "scanner",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_stockProductDetails_SCAN_RESOURCE_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "scanResource",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [],
                                        "errorMessage": "",
                                        "isMultiSelect": false
                                    }
                                ],
                                "actionLabel": "APP_CONFIG_INVENTORY_stockProductDetails_ACTION_BUTTON_LABEL_1",
                                "description": "APP_CONFIG_INVENTORY_stockProductDetails_SCREEN_DESCRIPTION"
                            },
                            {
                                "page": "stockDetails",
                                "type": "object",
                                "label": "APP_CONFIG_INVENTORY_stockDetails_SCREEN_HEADING",
                                "order": 2,
                                "navigateTo": {
                                    "name": "stockProductDetails",
                                    "type": "form"
                                },
                                "properties": [
                                    {
                                        "type": "dynamic",
                                        "enums": [],
                                        "label": "APP_CONFIG_INVENTORY_productDetails_LABEL",
                                        "order": 1,
                                        "value": "",
                                        "format": "custom",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_productDetails_SELECT_MULTIPLE_PRODUCTS_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "productdetail",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "schemaCode": "HCM.DELIVERY_COMMENT_OPTIONS_POPULATOR",
                                        "systemDate": false,
                                        "validations": [
                                            {
                                                "type": "required",
                                                "value": true,
                                                "message": "APP_CONFIG_INVENTORY_productDetails_PRODUCT_SELECTION_IS_REQUIRED_MESSAGE"
                                            }
                                        ],
                                        "errorMessage": "",
                                        "isMultiSelect": true
                                    },
                                    {
                                        "type": "dynamic",
                                        "label": "APP_CONFIG_INVENTORY_stockDetails_facilityFromWhich_LABEL",
                                        "order": 2,
                                        "value": "",
                                        "format": "custom",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_stockDetails_SELECT_THE_FACILITY_FROM_WHICH_THE_STOCK_IS_BEING_RECEIVED_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "facilityFromWhich",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "schemaCode": "HCM.FACILITY_OPTIONS_POPULATOR",
                                        "systemDate": false,
                                        "validations": [
                                            {
                                                "type": "required",
                                                "value": true,
                                                "message": "APP_CONFIG_INVENTORY_stockDetails_facilityFromWhich_IS_REQUIRED_MESSAGE"
                                            }
                                        ],
                                        "errorMessage": "",
                                        "includeInForm": true,
                                        "isMultiSelect": false
                                    },
                                    {
                                        "type": "string",
                                        "enums": [],
                                        "label": "APP_CONFIG_INVENTORY_stockDetails_deliveryTeamCode_LABEL",
                                        "order": 4,
                                        "value": "",
                                        "format": "scanner",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_stockDetails_SCAN_TEAM_CODE_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "deliveryTeam",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [
                                            {
                                                "type": "required",
                                                "value": true,
                                                "message": "APP_CONFIG_INVENTORY_stockDetails_deliveryTeamCode_IS_REQUIRED_MESSAGE"
                                            }
                                        ],
                                        "errorMessage": "",
                                        "isMultiSelect": false,
                                        "visibilityCondition": {
                                            "expression": "stockDetails.facilityFromWhich==Delivery Team"
                                        }
                                    },
                                    {
                                        "type": "string",
                                        "enums": [
                                            {
                                                "code": "BUS",
                                                "name": "Bus"
                                            },
                                            {
                                                "code": "TRUCK",
                                                "name": "Truck"
                                            }
                                        ],
                                        "label": "APP_CONFIG_INVENTORY_stockDetails_transportType_LABEL",
                                        "order": 3,
                                        "value": "",
                                        "format": "dropdown",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_stockDetails_SELECT_THE_TYPE_OF_TRANSPORT_USED_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "transportType",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [
                                            {
                                                "type": "required",
                                                "value": true,
                                                "message": "APP_CONFIG_INVENTORY_stockDetails_TRANSPORT_TYPE_IS_REQUIRED_MESSAGE"
                                            }
                                        ],
                                        "errorMessage": "",
                                        "isMultiSelect": false
                                    },
                                    {
                                        "type": "string",
                                        "label": "APP_CONFIG_INVENTORY_stockDetails_vehicleNumber_LABEL",
                                        "order": 4,
                                        "value": "",
                                        "format": "text",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_stockDetails_ENTER_THE_VEHICLE_NUMBER_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "vehicleNumber",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [
                                            {
                                                "type": "required",
                                                "value": true,
                                                "message": "APP_CONFIG_INVENTORY_stockDetails_VEHICLE_NUMBER_IS_REQUIRED_MESSAGE"
                                            }
                                        ],
                                        "errorMessage": "",
                                        "isMultiSelect": false
                                    }
                                ],
                                "actionLabel": "APP_CONFIG_INVENTORY_STOCKDETAILS_ACTION_BUTTON_LABEL",
                                "description": "APP_CONFIG_INVENTORY_STOCKDETAILS_SCREEN_DESCRIPTION"
                            },
                            {
                                "page": "warehouseDetails",
                                "type": "object",
                                "label": "APP_CONFIG_INVENTORY_warehouseDetails_WAREHOUSE_SCREEN_HEADING",
                                "order": 1,
                                "navigateTo": {
                                    "name": "stockDetails",
                                    "type": "form"
                                },
                                "properties": [
                                    {
                                        "type": "integer",
                                        "label": "APP_CONFIG_INVENTORY_warehouseDetails_dateOfReceipt_LABEL",
                                        "order": 1,
                                        "value": "",
                                        "format": "date",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_warehouseDetails_ENTER_THE_DATE_ON_WHICH_THE_STOCK_WAS_RECEIVED_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "dateOfEntry",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": true,
                                        "validations": [
                                            {
                                                "type": "required",
                                                "value": true,
                                                "message": "APP_CONFIG_INVENTORY_warehouseDetails_dateOfReceipt_IS_REQUIRED_MESSAGE"
                                            }
                                        ],
                                        "errorMessage": "",
                                        "includeInForm": true,
                                        "isMultiSelect": false
                                    },
                                    {
                                        "type": "string",
                                        "label": "APP_CONFIG_INVENTORY_warehouseDetails_administrativeArea_LABEL",
                                        "order": 2,
                                        "value": "",
                                        "format": "locality",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_warehouseDetails_SELECT_THE_ADMINISTRATIVE_AREA_OF_THE_WAREHOUSE_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "administrativeArea",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [
                                            {
                                                "type": "required",
                                                "value": true,
                                                "message": "APP_CONFIG_INVENTORY_warehouseDetails_administrativeArea_IS_REQUIRED_MESSAGE"
                                            }
                                        ],
                                        "errorMessage": "",
                                        "includeInForm": true,
                                        "isMultiSelect": false
                                    },
                                    {
                                        "type": "dynamic",
                                        "enums": [],
                                        "label": "APP_CONFIG_INVENTORY_warehouseDetails_facilityToWhich_LABEL",
                                        "order": 3,
                                        "value": "",
                                        "format": "custom",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_warehouseDetails_SELECT_THE_FACILITY_TO_WHICH_THE_STOCK_IS_BEING_SENT_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "facilityToWhich",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [
                                            {
                                                "type": "required",
                                                "value": true,
                                                "message": "APP_CONFIG_INVENTORY_warehouseDetails_facilityToWhich_IS_REQUIRED_MESSAGE"
                                            }
                                        ],
                                        "errorMessage": "",
                                        "includeInForm": true,
                                        "isMultiSelect": false
                                    },
                                    {
                                        "type": "string",
                                        "enums": [],
                                        "label": "APP_CONFIG_INVENTORY_warehouseDetails_teamCode_LABEL",
                                        "order": 4,
                                        "value": "",
                                        "format": "scanner",
                                        "hidden": false,
                                        "tooltip": "",
                                        "helpText": "APP_CONFIG_INVENTORY_warehouseDetails_SCAN_TEAM_CODE_HELP_TEXT",
                                        "infoText": "",
                                        "readOnly": false,
                                        "fieldName": "teamCode",
                                        "deleteFlag": false,
                                        "innerLabel": "",
                                        "systemDate": false,
                                        "validations": [
                                            {
                                                "type": "required",
                                                "value": true,
                                                "message": "APP_CONFIG_INVENTORY_warehouseDetails_teamCode_IS_REQUIRED_MESSAGE"
                                            }
                                        ],
                                        "errorMessage": "",
                                        "isMultiSelect": false,
                                        "visibilityCondition": {
                                            "expression": "warehouseDetails.facilityToWhich==Delivery Team"
                                        }
                                    }
                                ],
                                "actionLabel": "APP_CONFIG_INVENTORY_warehouseDetails_ACTION_BUTTON_LABEL_1",
                                "description": "APP_CONFIG_INVENTORY_warehouseDetails_SCREEN_DESCRIPTION"
                            }
                        ],
                        "version": 1,
                        "disabled": false,
                        "isSelected": true,
                        "screenType": "FORM"
                    }
                ],
                "order": 8,
                "active": false,
                "project": "IRS-mz",
                "version": 1,
                "disabled": false,
                "isSelected": false,
                "initialPage": "complaintDetails"
            }
]
```

</details>

{% hint style="info" %}
### We also have one more master FormConfig, AppConfigCache, which needs only schema, data will be auto added during campaign configuration.
{% endhint %}
{% endstep %}

{% step %}
### Campaign Naming Convention

This master defines the naming convention rules displayed to users when creating a campaign name. The rules are shown as a checklist with real-time validation feedback.

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `CampaignNamingConvention`&#x20;

#### How It Works

**id**

Unique identifier for the naming convention configuration.

**data**

Array of localisation keys (translation codes) for the naming rules.

**isActive**

Whether this configuration is active.

<details>

<summary>Campaign Naming Convention</summary>

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
{% endstep %}

{% step %}
### Field Properties Panel Config

This master defines the configuration for the properties panel (right-side drawer) that appears when editing a field in the mobile app configuration screens. It controls which properties and validations are available for each field type.

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `FieldPropertiesPanelConfig`&#x20;

#### How It Works

**Label**

Unique identifier for the panel configuration (e.g., `NewPanelConfig`).

**Content**

Array of property fields shown in the panel. Each field can have:

<table><thead><tr><th width="201.5">Property</th><th width="120.05078125">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td>string</td><td>Unique field identifier</td></tr><tr><td><code>label</code></td><td>string</td><td>Display label for the property</td></tr><tr><td><code>order</code></td><td>number</td><td>Display order in the panel</td></tr><tr><td><code>bindTo</code></td><td>string</td><td>Property path where value is saved (e.g., <code>label</code>, <code>required</code>, <code>properties.popupConfig.title</code>)</td></tr><tr><td><code>fieldType</code></td><td>string</td><td>Type of input (<code>text</code>, <code>textarea</code>, <code>toggle</code>, <code>number</code>, <code>dropdown</code>, <code>fieldTypeDropdown</code>, <code>labelPairList</code>, <code>table</code>)</td></tr><tr><td><code>defaultValue</code></td><td>any</td><td>Default value for the property</td></tr><tr><td><code>visibilityEnabledFor</code></td><td>array</td><td>List of field types for which this property is visible (empty array = visible for all)</td></tr><tr><td><code>conditionalField</code></td><td>array</td><td>Additional fields shown when toggle is enabled</td></tr><tr><td><code>showFieldOnToggle</code></td><td>boolean</td><td>Whether conditional fields appear on toggle</td></tr><tr><td><code>disableForRequired</code></td><td>boolean</td><td>Disable this property for mandatory fields</td></tr><tr><td><code>isLocalisable</code></td><td>boolean</td><td>Whether the value supports localization</td></tr><tr><td><code>isPopupProperty</code></td><td>boolean</td><td>Whether this is a popup-specific property</td></tr></tbody></table>

**Validation**

Array of validation rules is available in the panel:

<table><thead><tr><th width="181.5390625">Validation</th><th width="196.5546875">Visible For</th><th>Description</th></tr></thead><tbody><tr><td><code>RegexPattern</code></td><td><code>text</code></td><td>Text pattern validation with predefined options (alphabets, numbers, alphanumeric)</td></tr><tr><td><code>ScannerRegexPattern</code></td><td><code>scanner</code>, <code>qrScanner</code></td><td>Pattern validation for scanned values</td></tr><tr><td><code>isGS1Barcode</code></td><td><code>scanner</code>, <code>qrScanner</code></td><td>GS1 barcode format validation</td></tr><tr><td><code>scanLimit</code></td><td><code>scanner</code>, <code>qrScanner</code></td><td>Maximum number of scans allowed</td></tr><tr><td><code>numberRange</code></td><td><code>numeric</code>, <code>number</code></td><td>Min/max value validation</td></tr><tr><td><code>lengthRange</code></td><td><code>text</code>, <code>number</code>, <code>mobileNumber</code></td><td>Min/max character length validation</td></tr><tr><td><code>dateRange</code></td><td><code>date</code>, <code>dob</code></td><td>Start/end date validation</td></tr><tr><td><code>dependencyFieldWrapper</code></td><td>Most input fields</td><td>Field visibility based on other field values</td></tr></tbody></table>

#### Available Content Properties

<table><thead><tr><th width="148.56640625">Property</th><th width="303.6875">Field Types</th><th>Description</th></tr></thead><tbody><tr><td><code>label</code></td><td>text, dropdown, checkbox, radio, number, date, etc.</td><td>Field label</td></tr><tr><td><code>helpText</code></td><td>text, textarea, dropdown, date, number, etc.</td><td>Help text below the field</td></tr><tr><td><code>Mandatory</code></td><td>text, dropdown, checkbox, number, date, radio, etc.</td><td>Required field validation</td></tr><tr><td><code>defaultValue</code></td><td>text, textarea, numeric, number, mobileNumber</td><td>Pre-filled value</td></tr><tr><td><code>tooltip</code></td><td>text, textarea, dropdown, date, number, etc.</td><td>Tooltip on hover</td></tr><tr><td><code>readOnly</code></td><td>text, textarea, dropdown, date, number, etc.</td><td>Non-editable field</td></tr><tr><td><code>isMdms</code></td><td>dropdown, select, idPopulator, radio</td><td>Populate options from MDMS</td></tr><tr><td><code>isMultiSelect</code></td><td>dropdown, select, idPopulator</td><td>Allow multiple selections</td></tr><tr><td><code>prefixText</code></td><td>mobileNumber, number</td><td>Text before input</td></tr><tr><td><code>suffixText</code></td><td>number</td><td>Text after input</td></tr><tr><td><code>innerLabel</code></td><td>text, textarea</td><td>Placeholder text</td></tr><tr><td><code>systemDate</code></td><td>date, dob</td><td>Use current system date</td></tr><tr><td><code>proximityRadius</code></td><td>proximitySearch</td><td>Search radius in meters</td></tr><tr><td><code>minSearchChars</code></td><td>searchBar</td><td>Minimum characters to trigger search</td></tr></tbody></table>

<details>

<summary>Field Panel Config Data</summary>

```
{
                "label": "NewPanelConfig",
                "content": [
                    {
                        "id": "label",
                        "label": "label",
                        "order": 2,
                        "bindTo": "label",
                        "fieldType": "text",
                        "defaultValue": "",
                        "conditionalField": [],
                        "showFieldOnToggle": false,
                        "visibilityEnabledFor": [
                            "latLng",
                            "textarea",
                            "idPopulator",
                            "text",
                            "date",
                            "dropdown",
                            "select",
                            "checkbox",
                            "dob",
                            "radio",
                            "number",
                            "numeric",
                            "mobileNumber",
                            "button",
                            "filter",
                            "buttonTemplate",
                            "proximitySearch",
                            "searchByID",
                            "PrimaryButton",
                            "qrScanner",
                            "scanner",
                            "switch",
                            "searchBar",
                            "actionPopup",
                            "locality",
                            "infoCard",
                            "dropdownTemplate",
                            "evaluationFacility"
                        ]
                    },
                    {
                        "id": "filter",
                        "label": "filter",
                        "order": 8,
                        "bindTo": "dropDownOptions",
                        "fieldType": "toggle",
                        "defaultValue": false,
                        "conditionalField": [
                            {
                                "type": "filters",
                                "label": "APPCONFIG_SELECT_SCHEMA",
                                "bindTo": "dropDownOptions",
                                "condition": true,
                                "mdmsOptions": [
                                    {
                                        "masterName": "SEARCH_HOUSEHOLD_FILTERS",
                                        "moduleName": "HCM",
                                        "schemaCode": "HCM.SEARCH_HOUSEHOLD_FILTERS"
                                    }
                                ]
                            },
                            {
                                "type": "options",
                                "bindTo": "dropDownOptions",
                                "condition": false
                            }
                        ],
                        "showFieldOnToggle": true,
                        "visibilityEnabledFor": [
                            "filter"
                        ]
                    },
                    {
                        "label": "isMdms",
                        "order": 12,
                        "bindTo": "isMdms",
                        "fieldType": "toggle",
                        "defaultValue": false,
                        "conditionalField": [
                            {
                                "type": "dropdown",
                                "label": "APPCONFIG_SELECT_SCHEMA",
                                "bindTo": "schemaCode",
                                "options": [
                                    {
                                        "masterName": "GenderType",
                                        "moduleName": "common-masters",
                                        "schemaCode": "common-masters.GenderType"
                                    },
                                    {
                                        "masterName": "HOUSE_STRUCTURE_TYPES",
                                        "moduleName": "HCM",
                                        "schemaCode": "HCM.HOUSE_STRUCTURE_TYPES"
                                    },
                                    {
                                        "masterName": "ID_TYPE_OPTIONS_POPULATOR",
                                        "moduleName": "HCM",
                                        "schemaCode": "HCM.ID_TYPE_OPTIONS_POPULATOR"
                                    },
                                    {
                                        "masterName": "DELIVERY_COMMENT_OPTIONS_POPULATOR",
                                        "moduleName": "HCM",
                                        "schemaCode": "HCM.DELIVERY_COMMENT_OPTIONS_POPULATOR"
                                    },
                                    {
                                        "masterName": "ServiceDefs",
                                        "moduleName": "RAINMAKER-PGR",
                                        "schemaCode": "RAINMAKER-PGR.ServiceDefs"
                                    },
                                    {
                                        "masterName": "REFERRAL_REASONS",
                                        "moduleName": "HCM",
                                        "schemaCode": "HCM.REFERRAL_REASONS"
                                    },
                                    {
                                        "masterName": "SEARCH_HOUSEHOLD_FILTERS",
                                        "moduleName": "HCM",
                                        "schemaCode": "HCM.SEARCH_HOUSEHOLD_FILTERS"
                                    }
                                ],
                                "jsonPath": "schemaCode",
                                "condition": true
                            },
                            {
                                "type": "options",
                                "bindTo": "dropDownOptions",
                                "condition": false
                            }
                        ],
                        "showFieldOnToggle": true,
                        "visibilityEnabledFor": [
                            "dropdown",
                            "idPopulator",
                            "select",
                            "radio",
                            "searchableDropdown"
                        ]
                    },
                    {
                        "id": "isMultiSelect",
                        "label": "isMultiSelect",
                        "order": 10,
                        "bindTo": "isMultiSelect",
                        "fieldType": "toggle",
                        "defaultValue": false,
                        "conditionalField": [],
                        "showFieldOnToggle": true,
                        "disableForRequired": true,
                        "visibilityEnabledFor": [
                            "dropdown",
                            "select",
                            "idPopulator"
                        ]
                    }
                ],
                "validation": [
                    {
                        "id": "scannerRegex",
                        "label": "ScannerRegexPattern",
                        "order": 1,
                        "bindTo": "pattern",
                        "fieldType": "toggle",
                        "conditionalField": [
                            {
                                "type": "text",
                                "label": "APPCONFIG_CUSTOM_PATTERN",
                                "bindTo": "pattern",
                                "isLocalisable": false
                            },
                            {
                                "type": "text",
                                "label": "APPCONFIG_ERRORMESSAGE",
                                "bindTo": "pattern.message"
                            }
                        ],
                        "showFieldOnToggle": true,
                        "visibilityEnabledFor": [
                            "scanner",
                            "qrScanner"
                        ]
                    },
                    {
                        "label": "scanLimit",
                        "order": 2,
                        "bindTo": "scanLimit",
                        "fieldType": "toggle",
                        "defaultValue": false,
                        "conditionalField": [
                            {
                                "type": "number",
                                "label": "APPCONFIG_NUMBER_SCAN_LIMIT",
                                "bindTo": "scanLimit",
                                "validation": {
                                    "pattern": "^(0|[1-9]\\d*)$"
                                },
                                "defaultValue": 1
                            },
                            {
                                "type": "text",
                                "label": "APPCONFIG_ERRORMESSAGE",
                                "bindTo": "scanLimit.message",
                                "options": []
                            }
                        ],
                        "showFieldOnToggle": true,
                        "visibilityEnabledFor": [
                            "scanner",
                            "qrScanner"
                        ]
                    },
                    {
                        "id": "dependencyFieldWrapper",
                        "label": "dependencyFieldWrapper",
                        "order": 2,
                        "bindTo": "visibilityCondition.expression",
                        "fieldType": "toggle",
                        "defaultValue": false,
                        "conditionalField": [
                            {
                                "type": "dependencyFieldWrapper",
                                "bindTo": "visibilityCondition.expression"
                            }
                        ],
                        "showFieldOnToggle": true,
                        "visibilityEnabledFor": [
                            "checkbox",
                            "numeric",
                            "dob",
                            "date",
                            "dob",
                            "select",
                            "dropdown",
                            "idPopulator",
                            "mobileNumber",
                            "number",
                            "textarea",
                            "text",
                            "latLng",
                            "radio",
                            "administrativeArea",
                            "searchableDropdown"
                        ]
                    },
                    {
                        "id": "regex",
                        "label": "RegexPattern",
                        "order": 3,
                        "bindTo": "pattern",
                        "fieldType": "toggle",
                        "conditionalField": [
                            {
                                "type": "radioOptions",
                                "label": "APPCONFIG_PATTERN",
                                "bindTo": "pattern",
                                "options": [
                                    {
                                        "code": "CHARACTERONLY",
                                        "pattern": "^[a-zA-Z]+$",
                                        "description": "Alphabets only (uppercase and lowercase)"
                                    },
                                    {
                                        "code": "NUMBERONLY",
                                        "pattern": "^\\d+$",
                                        "description": "Numbers only (0-9)"
                                    },
                                    {
                                        "code": "ALPHANUMERICONLY",
                                        "pattern": "^[a-zA-Z0-9]+$",
                                        "description": "Letters and numbers only (no special characters)"
                                    }
                                ],
                                "jsonPath": "pattern"
                            },
                            {
                                "type": "text",
                                "label": "APPCONFIG_CUSTOM_PATTERN",
                                "bindTo": "pattern",
                                "isLocalisable": false
                            },
                            {
                                "type": "text",
                                "label": "APPCONFIG_ERRORMESSAGE",
                                "bindTo": "pattern.message"
                            }
                        ],
                        "showFieldOnToggle": true,
                        "visibilityEnabledFor": [
                            "text"
                        ]
                    },
                    {
                        "id": "range",
                        "label": "numberRange",
                        "order": 4,
                        "children": [
                            {
                                "id": "min",
                                "label": "Minimum",
                                "bindTo": "range.min",
                                "fieldType": "number",
                                "isLocalisable": false
                            },
                            {
                                "id": "max",
                                "label": "Maximum",
                                "bindTo": "range.max",
                                "fieldType": "number",
                                "isLocalisable": false
                            },
                            {
                                "id": "errorMessage",
                                "label": "errorMessage",
                                "bindTo": "range.errorMessage",
                                "fieldType": "text",
                                "isLocalisable": true
                            }
                        ],
                        "fieldType": "group",
                        "validationMessage": "APPCONFIG_MIN_LESS_EQUAL_MAX",
                        "validationExpression": "range.min <= range.max",
                        "visibilityEnabledFor": [
                            "numeric",
                            "number"
                        ]
                    },
                    {
                        "id": "lengthRange",
                        "label": "lengthRange",
                        "order": 5,
                        "children": [
                            {
                                "id": "minLength",
                                "label": "minLength",
                                "bindTo": "lengthRange.minLength",
                                "fieldType": "number",
                                "isLocalisable": false
                            },
                            {
                                "id": "maxLength",
                                "label": "maxLength",
                                "bindTo": "lengthRange.maxLength",
                                "fieldType": "number",
                                "isLocalisable": false
                            },
                            {
                                "id": "errorMessage",
                                "label": "errorMessage",
                                "bindTo": "lengthRange.errorMessage",
                                "fieldType": "text",
                                "isLocalisable": true
                            }
                        ],
                        "fieldType": "group",
                        "validationMessage": "APPCONFIG_MIN_LENGTH_LESS_EQUAL_MAX",
                        "validationExpression": "lengthRange.minLength <= lengthRange.maxLength",
                        "visibilityEnabledFor": [
                            "text",
                            "number",
                            "mobileNumber"
                        ]
                    },
                    {
                        "id": "range",
                        "label": "dateRange",
                        "order": 6,
                        "children": [
                            {
                                "id": "startDate",
                                "label": "startDate",
                                "bindTo": "dateRange.startDate",
                                "fieldType": "date",
                                "isLocalisable": false
                            },
                            {
                                "id": "endDate",
                                "label": "endDate",
                                "bindTo": "dateRange.endDate",
                                "fieldType": "date",
                                "isLocalisable": false
                            },
                            {
                                "id": "errorMessage",
                                "label": "errorMessage",
                                "bindTo": "dateRange.errorMessage",
                                "fieldType": "text",
                                "isLocalisable": true
                            },
                            {
                                "label": "systemDate",
                                "order": 9,
                                "bindTo": "systemDate",
                                "tabOrder": 1,
                                "fieldType": "toggle",
                                "defaultValue": false,
                                "conditionalField": [],
                                "showFieldOnToggle": false,
                                "disableForRequired": false,
                                "visibilityEnabledFor": [
                                    "date"
                                ]
                            }
                        ],
                        "fieldType": "group",
                        "validationMessage": "APPCONFIG_MIN_DATE_LESS_EQUAL_MAX",
                        "validationExpression": "dateRange.startDate <= dateRange.endDate",
                        "visibilityEnabledFor": [
                            "date",
                            "dob"
                        ]
                    }
                ]
            }
```

</details>
{% endstep %}

{% step %}
### Field Type Mapping Configurations

This master defines the available field types for configuring mobile app screens. It maps each field type to its UI component, metadata, and configurable properties.

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `FieldTypeMappingConfig`&#x20;

**How It Works**

**Type**

Unique identifier for the field type (e.g., `text`, `dropdown`, `card`, `button`).

**Category**

Groups field types for display in the UI:

* `basic` - Simple inputs like text, number, date, dropdown
* `advanced` - Complex components like template components, scanner component etc

**Order**

Display order in the field type selection dropdown.

**Metadata**

Schema information for the field:

* `type` - Data type (`string`, `integer`, `boolean`, `template`)
* `format` - Format identifier for rendering

**Field Type**

Base field type used for rendering.

**Component**

(Optional) React component name for advanced field types.

**Properties**

(Optional) Configurable options for the field type.

**Editable**

(Optional) Whether the field can be modified after creation.

<details>

<summary>Field Type Mapping Configurations</summary>

```
  [
  {
                "type": "select",
                "order": 27,
                "category": "advanced",
                "metadata": {
                    "type": "string",
                    "format": "select"
                },
                "component": "SelectionCard",
                "fieldType": "component"
            },{
                "type": "radioList",
                "order": 18,
                "category": "advanced",
                "editable": false,
                "metadata": {
                    "type": "template",
                    "format": "radioList"
                },
                "component": "RadioListTemplate",
                "fieldType": "radioList"
            },{
                "type": "Row",
                "order": 19,
                "category": "advanced",
                "metadata": {
                    "type": "template",
                    "format": "Row"
                },
                "component": "Row",
                "fieldType": "Row",
                "properties": [
                    {
                        "code": "children",
                        "options": [
                            "Card",
                            "infoCard",
                            "panelCard",
                            "button",
                            "Row",
                            "Column",
                            "switch",
                            "searchBar",
                            "tag",
                            "filter",
                            "textTemplate"
                        ]
                    }
                ]
            },{
                "type": "tag",
                "order": 17,
                "category": "advanced",
                "metadata": {
                    "type": "template",
                    "format": "tag"
                },
                "component": "Tag",
                "fieldType": "tag",
                "properties": [
                    {
                        "code": "tagType",
                        "options": [
                            "success",
                            "error",
                            "warning",
                            "monochrome"
                        ]
                    }
                ]
            },{
                "type": "number",
                "order": 6,
                "category": "basic",
                "metadata": {
                    "type": "integer",
                    "format": "text"
                },
                "fieldType": "number"
            },
  ]
```

</details>
{% endstep %}

{% step %}
### Details Renderer Configurations

Master details

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `DETAILS_RENDERER_CONFIG`&#x20;

<details>

<summary>Details Renderer Config Data</summary>

```
[
{
                "entity": "Task",
                "displayFields": [
                    {
                        "fieldKey": "doseIndex",
                        "jsonPath": "Task.additionalFields",
                        "mandatory": "false",
                        "additionalField": "true"
                    },
                    {
                        "fieldKey": "status",
                        "jsonPath": "Task.status",
                        "mandatory": "false"
                    },
                    {
                        "fieldKey": "createdTime",
                        "jsonPath": "Task.auditDetails.createdTime",
                        "mandatory": "false"
                    },
                    {
                        "fieldKey": "cycleIndex",
                        "jsonPath": "Task.additionalFields",
                        "mandatory": "false",
                        "additionalField": "true"
                    }
                ]
            },{
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
{
                "entity": "Individual",
                "displayFields": [
                    {
                        "fieldKey": "locality",
                        "jsonPath": "Individual.address[0].locality.code",
                        "mandatory": "false"
                    },
                    {
                        "fieldKey": "name",
                        "jsonPath": "Individual.name.givenName",
                        "mandatory": "true"
                    },
                    {
                        "fieldKey": "gender",
                        "jsonPath": "Individual.gender",
                        "mandatory": "false"
                    },
                    {
                        "fieldKey": "identifierId",
                        "jsonPath": "Individual.identifiers[0].identifierId",
                        "mandatory": "false"
                    },
                    {
                        "isList": "true",
                        "fieldKey": "identifierType",
                        "jsonPath": "Individual.identifiers[0].identifierType",
                        "mandatory": "false"
                    },
                    {
                        "fieldKey": "mobileNumber",
                        "jsonPath": "Individual.mobileNumber",
                        "mandatory": "false"
                    }
                ]
            }
]

```

</details>
{% endstep %}

{% step %}
### Campaign Type Templates

This configuration is used to define pre-built campaign templates that users can select when creating a new campaign. Templates provide a quick-start option with predefined settings based on previous successful campaigns.

Master details

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `campaignTypeTemplates`&#x20;

#### How It Works

**id**

Unique identifier for the template (e.g., `MalariaSMC2024`, `PolioNID2025`).

**name**

Display name of the campaign template.

**description**

Detailed description of the template explaining its purpose and use case.

**projectTypeCode**

Code linking to the project type in `HCM-PROJECT-TYPES.projectTypes` (e.g., `MR-DN`, `Bednets`, `POLIO`).

**disease**

Associated disease type (e.g., `MALARIA`, `POLIO`, `VITAMINADEFICIENCY`).

**usedIn**

Location or geography where this template was previously used (e.g., `Kano - Nigeria`, `Maputo, Mozambique`).

**partnerName**

Name of the organization or partner that created/used this template.

**modules**

Array of modules included in the campaign:

* `Registration`
* `Delivery`
* `Inventory`
* `Attendance`

**duration**

Campaign duration configuration

**deliveryCycles**

Array of delivery cycle/round configuration

**imageDetails**

Image configuration for the template card

<details>

<summary>Campaign Type Templates Sample Data</summary>

```
[
{
                "id": "PolioNID2025",
                "name": "Polio National Immunization Day",
                "usedIn": "Taraba - Nigeria",
                "disease": "POLIO",
                "modules": [
                    "Registration",
                    "Delivery",
                    "Inventory",
                    "Attendance"
                ],
                "duration": {
                    "endDate": 1741132200000,
                    "startDate": 1740959400000
                },
                "description": "Designed for high-volume vaccination drives, this template comes ready with modules for beneficiary registration, dose tracking, and real-time coverage reporting. It enables supervisors to monitor field progress and identify missed households easily. Best suited for door-to-door or booth-based immunization campaigns.",
                "partnerName": "Solina",
                "imageDetails": {
                    "url": "https://egov-qa-assets.s3.ap-south-1.amazonaws.com/health/polio.png",
                    "altText": "Illustration of polio vaccination campaign"
                },
                "deliveryCycles": [
                    {
                        "description": "Single-round mass vaccination campaign",
                        "roundNumber": 1,
                        "durationInDays": 3
                    }
                ],
                "projectTypeCode": "POLIO"
            }, {
                "id": "Malaria2024",
                "name": "Malaria 2024",
                "usedIn": "Ondo, Taraba - Nigeria",
                "disease": "MALARIA",
                "modules": [
                    "Registration",
                    "Delivery",
                    "Inventory",
                    "Attendance"
                ],
                "duration": {
                    "endDate": 1715279400000,
                    "startDate": 1714329000000
                },
                "description": "This template includes preconfigured workflows for household registration, eligibility checks, dosage administration, and daily reporting. It supports both online and offline data capture, ensuring smooth delivery tracking across all distribution rounds. Ideal for field teams managing child-based SMC cycles in high-transmission zones.",
                "partnerName": "Malaria Consortium",
                "imageDetails": {
                    "url": "https://egov-qa-assets.s3.ap-south-1.amazonaws.com/health/malaria.png",
                    "altText": "Illustration of mosquito for malaria campaign"
                },
                "deliveryCycles": [
                    {
                        "description": "Bednet Delivery",
                        "roundNumber": 1,
                        "durationInDays": 20
                    }
                ],
                "projectTypeCode": "Bednets"
            },{
                "id": "MalariaSMC2024",
                "name": "Malaria SMC 2024",
                "usedIn": "Kano - Nigeria",
                "disease": "MALARIA",
                "modules": [
                    "Registration",
                    "Delivery",
                    "Inventory",
                    "Attendance"
                ],
                "duration": {
                    "endDate": 1715279400000,
                    "startDate": 1714329000000
                },
                "description": "This template includes preconfigured workflows for household registration, eligibility checks, dosage administration, and daily reporting. It supports both online and offline data capture, ensuring smooth delivery tracking across all distribution rounds. Ideal for field teams managing child-based SMC cycles in high-transmission zones.",
                "partnerName": "Malaria Consortium",
                "imageDetails": {
                    "url": "https://egov-qa-assets.s3.ap-south-1.amazonaws.com/health/malaria.png",
                    "altText": "Illustration of mosquito for malaria campaign"
                },
                "deliveryCycles": [
                    {
                        "description": "First round delivery for malaria chemoprevention",
                        "roundNumber": 1,
                        "durationInDays": 4
                    },
                    {
                        "description": "Second round delivery",
                        "roundNumber": 2,
                        "durationInDays": 4
                    },
                    {
                        "description": "Third round delivery",
                        "roundNumber": 3,
                        "durationInDays": 4
                    }
                ],
                "projectTypeCode": "MR-DN"
            },
]

```

</details>
{% endstep %}

{% step %}
### Campaign Rules & Controls

Includes:

* Date updates by boundary (`dateWithBoundary`)
* Campaign naming rules (`CampaignNamingConvention`)
* Mandatory modules (`AllowedModules`)
* Target-to-beneficiary mapping (`targetConfigs`)
* Checklist roles & templates
* Microplan integration rules
* ID generation (`common-masters.IdFormat`)

{% hint style="info" %}
⚠️ Add **IdGen config before using ID generation**.
{% endhint %}
{% endstep %}

{% step %}
### Dieseases List

This configuration is used to define the list of supported diseases for campaign templates and project types. It provides disease options for filtering and categorising campaigns.

Master details

* Master Name: `HCM-ADMIN-CONSOLE`
* ModuleName: `diseasesList`&#x20;

#### How It Works

**code**

Unique identifier for the disease (e.g., `MALARIA`, `POLIO`, `COVID19`).

**name**

Human-readable display name of the disease.

**active**

Flag to indicate if the disease is currently active and should be shown in dropdowns.

**description**

(Optional) Detailed description of the disease for informational purposes.

<details>

<summary>Diseases List Sample Data</summary>

```
[
{
                "code": "MALARIA",
                "name": "Malaria",
                "active": true,
                "description": "A mosquito-borne infectious disease affecting humans and animals caused by parasitic protozoans of the genus Plasmodium."
            },{
                "code": "POLIO",
                "name": "Polio",
                "active": true,
                "description": "A viral disease that can affect nerves and lead to partial or full paralysis. Preventable by vaccination."
            },{
                "code": "VITAMINADEFICIENCY",
                "name": "Vitamin A Deficiency",
                "active": true,
                "description": "A condition caused by a lack of vitamin A in the body, leading to visual impairment and immune deficiencies."
            },{
                "code": "COVID19",
                "name": "COVID-19",
                "active": true,
                "description": "Respiratory illness caused by the SARS-CoV-2 virus, preventable through vaccination and public health campaigns."
            },
]
```

</details>
{% endstep %}
{% endstepper %}

### Removed / Deprecated

* `adminSchemas` (removed)
* V1 APIs (deprecated)

### Deployment Configuration

For environment-specific settings, refer to [**Helm Configuration** documentation](project-factory-configuration.md).
