---
hidden: true
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-console-configuration/enable-new-campaign-type/irs-campaign-type
---

# IRS Campaign Type

## Overview

To enable **IRS (Indoor Residual Spraying)** as a campaign type, you must register it in MDMS and configure delivery behaviour, conditions, and target templates. IRS has specific rules—such as fixed cycles and deliveries—that must be enforced through configuration.

### Step 1: Add IRS as a Campaign Type in MDMS

IRS must first be registered as a valid campaign (project) type.

1. **Module Name**: [`HCM-PROJECT-TYPES`](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/project-types.json)
2. **Master Name**: `projectTypes`
3. **Add a New Entry**
   * Add an entry for the IRS campaign type in the MDMS JSON. Once this is added, **IRS will appear as a selectable campaign type** in the UI.

<figure><img src="https://egov-digit.gitbook.io/hcm-console/~gitbook/image?url=https%3A%2F%2Flh7-rt.googleusercontent.com%2Fdocsz%2FAD_4nXfH_qaHlEWOd_N-wUKxupmEMXozAMQsejO1iz5Bdy7X6TLD6ZZeVYkedcxxiiLbUJ7bxgSIq4gr9zHcgJ07T4KUi5JuXbErCf9u9iEsddBRMiCIGxMI1F17cMmGREmOzoFWYJbu3e-6xx5MKphcQ3aCCMs%3Fkey%3Dr-hCiZghJuy1mlIo4epSOA&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=8113c671&#x26;sv=2" alt=""><figcaption></figcaption></figure>

### Step 2: Update Delivery Configuration for IRS

IRS has fixed operational rules that must be enforced via delivery configuration.

#### 2.1 Configure Delivery Attributes

* Update the delivery configuration in MDMS to define:
  * Attributes
  * Operators
  * Values
* These configurations drive what appears on the **Delivery Conditions** screen.

<figure><img src="https://egov-digit.gitbook.io/hcm-console/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2FJdb4e4jIFb27lF1Wh5VZ%2Fimage.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=b29fec3d&#x26;sv=2" alt=""><figcaption></figcaption></figure>

#### 2.2 Lock Cycles and Deliveries

For IRS campaigns:

* **Number of cycles** → not editable
* **Number of deliveries** → not editable

To enforce this:

1. Update the delivery configuration.
2. Set the following flag:

```
 "IsDisable": true
```

<figure><img src="https://egov-digit.gitbook.io/hcm-console/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2Ft32Wns8x21OtXuJR2rWg%2Fimage.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=c2bc1801&#x26;sv=2" alt=""><figcaption></figcaption></figure>

This ensures users cannot modify cycles or deliveries for IRS campaigns.

### Step 3: Configure Delivery Conditions Data Source

The **Delivery Conditions** page pulls its values from MDMS.

1. **Module Name**: `HCM`
2. **Master Name**: `HOUSE_STRUCTURE_TYPES`

Ensure:

* The master contains all valid house structure types.
* Values are correctly configured and active.

These values will appear as selectable options in the delivery conditions screen for IRS.

{% embed url="https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/house_structure_types.json" %}

### Step 4: Configure Target Templates (adminSchema)

To enable **dynamic generation of target templates** for IRS:

1. Add entries in MDMS under:
   * **Schema Code**: `HCM-ADMIN-CONSOLE.adminSchema`
2. Configure the schema to:
   * Define columns
   * Map targets to boundaries
   * Support IRS-specific reporting needs

This configuration controls how target sheets are generated and displayed.

```
 "schemaCode": "HCM-ADMIN-CONSOLE.adminSchema"
```

<details>

<summary>IRS Template</summary>

```

{
                "title": "boundary",
                "$schema": "http://json-schema.org/draft-07/schema#",
                "properties": {
                    "numberProperties": [
                        {
                            "name": "HCM_ADMIN_CONSOLE_TARGET_IRS_1",
                            "type": "number",
                            "isRequired": true,
                            "description": "Target at the Selected Boundary Level",
                            "orderNumber": 2
                        },
                        {
                            "name": "HCM_ADMIN_CONSOLE_TARGET_IRS_2",
                            "type": "number",
                            "isRequired": true,
                            "description": "Target at the Selected Boundary Level",
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
                "campaignType": "IRS-mz"
            },
            "isActive": true,
            "auditDetails": {
                "createdBy": "bfab6822-ec28-40f0-aef1-efd1cda8fcd5",
                "lastModifiedBy": "bfab6822-ec28-40f0-aef1-efd1cda8fcd5",
                "createdTime": 1722846607391,
                "lastModifiedTime": 1722846607391
            }
        },
        {
            "id": "87d17bf5-b0dd-4796-a36f-32e466c47569",
            "tenantId": "mz",
            "schemaCode": "HCM-ADMIN-CONSOLE.adminSchema",
            "uniqueIdentifier": "boundaryWithTarget.IRS-mz",
            "data": {
                "title": "boundaryWithTarget",
                "$schema": "http://json-schema.org/draft-07/schema#",
                "properties": {
                    "numberProperties": [
                        {
                            "name": "HCM_ADMIN_CONSOLE_TARGET_IRS_1",
                            "type": "number",
                            "isRequired": true,
                            "description": "Target at the Selected Boundary Level",
                            "orderNumber": 2
                        },
                        {
                            "name": "HCM_ADMIN_CONSOLE_TARGET_IRS_2",
                            "type": "number",
                            "isRequired": true,
                            "description": "Target at the Selected Boundary Level",
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
                "campaignType": "IRS-mz"
            },
            "isActive": true,
            "auditDetails": {
                "createdBy": "bfab6822-ec28-40f0-aef1-efd1cda8fcd5",
                "lastModifiedBy": "bfab6822-ec28-40f0-aef1-efd1cda8fcd5",
                "createdTime": 1722846554092,
                "lastModifiedTime": 1722846554092
            }
        }

```

</details>

