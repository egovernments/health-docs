---
hidden: true
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-console-configuration/enable-new-campaign-type/co-delivery-campaign-type
---

# Co-Delivery Campaign Type

## Overview

**Co-delivery** is the **default campaign configuration** in the Console. It supports flexible delivery rules with **no restrictions** on cycles, deliveries, or conditions.

To enable Co-delivery as a campaign type, it must be registered in MDMS and linked to the required attribute and target configurations.

## Steps

### Step 1: Add Co-delivery as a Campaign Type in MDMS

Co-delivery must be defined as a project type so it appears in the campaign creation flow.

* **Project Type Code**: `DEFAULT`
* **Module Name**: `HCM-PROJECT-TYPES`
* **Master Name**: `projectTypes`

#### Action

Add an entry for `DEFAULT` in the `projectTypes` master.

This ensures **Co-delivery appears as a selectable campaign type** in the Console.

<details>

<summary>HCM-PROJECT-TYPES</summary>

```
{
            "id": "469a45cd-7a5f-45d9-bacc-f441320a0c48",
            "tenantId": "mz",
            "schemaCode": "HCM-PROJECT-TYPES.projectTypes",
            "uniqueIdentifier": "ea1bb2e7-06d8-4fe4-ba1e-f4a6363a23re",
            "data": {
                "id": "ea1bb2e7-06d8-4fe4-ba1e-f4a6363a23re",
                "code": "DEFAULT",
                "name": "configuration for Co-Delivery Campaign",
                "type": "multiround",
                "group": "MALARIA",
                "cycles": [],
                "resources": [],
                "beneficiaryType": "INDIVIDUAL"
            },
            "isActive": true,
            "auditDetails": {
                "createdBy": "db842ca9-25c5-4419-a72f-459443d38feb",
                "lastModifiedBy": "db842ca9-25c5-4419-a72f-459443d38feb",
                "createdTime": 1734585310867,
                "lastModifiedTime": 1734585310867
            }
        }
```

</details>

### Step 2: Configure Attributes for Co-delivery (allAttributes)

Co-delivery uses the new attribute framework for defining delivery rules.

* **Schema Name**: `HCM-ADMIN-CONSOLE.allAttributes`

#### Purpose

This schema defines:

* Available delivery attributes
* Supported operators per attribute
* Project types where each attribute is applicable

#### Action

For each attribute:

* Add `DEFAULT` to the `projectTypes` list
* Configure supported operators
* Ensure `isActive` is set to `true`

These attributes will be available while defining **delivery rules** for Co-delivery campaigns.

<details>

<summary>HCM-ADMIN-CONSOLE.allAttributes</summary>

```
[
        {
            "id": "b6ca2d6a-3f40-4823-9436-7f5db9c4e8eb",
            "tenantId": "mz",
            "schemaCode": "HCM-ADMIN-CONSOLE.allAttributes",
            "uniqueIdentifier": "gender",
            "data": {
                "key": 6,
                "code": "gender",
                "i18nKey": "CAMPAIGN_ATTRIBUTE_GENDER",
                "projectTypes": [
                    "CO-DEL",
                    "MR-DN"
                ],
                "valuesSchema": "common-masters.GenderType",
                "allowedOperators": [
                    "EQUAL_TO"
                ]
            },
            "isActive": true
        },
        {
            "id": "6d874cc3-23b9-49d1-ab93-f03c2199174f",
            "tenantId": "mz",
            "schemaCode": "HCM-ADMIN-CONSOLE.allAttributes",
            "uniqueIdentifier": "weight",
            "data": {
                "key": 5,
                "code": "weight",
                "i18nKey": "CAMPAIGN_ATTRIBUTE_WEIGHT",
                "projectTypes": [
                    "CO-DEL",
                    "MR-DN"
                ]
            },
            "isActive": true
        },
        {
            "id": "600f3003-fdaa-4c14-86dd-c5f79dc69baa",
            "tenantId": "mz",
            "schemaCode": "HCM-ADMIN-CONSOLE.allAttributes",
            "uniqueIdentifier": "height",
            "data": {
                "key": 4,
                "code": "height",
                "i18nKey": "CAMPAIGN_ATTRIBUTE_HEIGHT",
                "projectTypes": [
                    "CO-DEL",
                    "MR-DN"
                ]
            },
            "isActive": true
        },
        {
            "id": "bb8ca065-e406-43b0-9a47-5a744a64386d",
            "tenantId": "mz",
            "schemaCode": "HCM-ADMIN-CONSOLE.allAttributes",
            "uniqueIdentifier": "age",
            "data": {
                "key": 3,
                "code": "age",
                "i18nKey": "CAMPAIGN_ATTRIBUTE_AGE",
                "projectTypes": [
                    "CO-DEL",
                    "MR-DN"
                ]
            },
            "isActive": true
        },
        {
            "id": "6ca05e70-06c1-4f0b-abf7-e4dfc7173086",
            "tenantId": "mz",
            "schemaCode": "HCM-ADMIN-CONSOLE.allAttributes",
            "uniqueIdentifier": "type_of_structure",
            "data": {
                "key": 2,
                "code": "type_of_structure",
                "i18nKey": "TYPE_OF_STRUCTURE",
                "projectTypes": [
                    "CO-DEL",
                    "IRS-mz"
                ],
                "valuesSchema": "HCM.HOUSE_STRUCTURE_TYPES",
                "allowedOperators": [
                    "EQUAL_TO"
                ]
            },
            "isActive": true
        },
        {
            "id": "a07cdcfb-83b0-4543-bfd7-01f4c7bd8bea",
            "tenantId": "mz",
            "schemaCode": "HCM-ADMIN-CONSOLE.allAttributes",
            "uniqueIdentifier": "memberCount",
            "data": {
                "key": 1,
                "code": "memberCount",
                "i18nKey": "CAMPAIGN_BEDNET_INDIVIDUAL_LABEL",
                "projectTypes": [
                    "LLIN-mz",
                    "CO-DEL"
                ]
            },
            "isActive": true
        }
    ]
```

</details>

### Step 3: Configure Dropdown Values (valuesSchema)

Some attributes require predefined dropdown values.

#### Action

* Set `valuesSchema` in the attribute configuration
* This schema determines where dropdown options are fetched from

Example use cases:

* Household structure types
* Population categories
* Facility types

Ensure the referenced schema exists and contains valid MDMS data.

The following schema is **no longer used** and should not be configured:

* `HCM-ADMIN-CONSOLE.attributeConfig`

All attribute-related configurations must now be done using:

* `HCM-ADMIN-CONSOLE.allAttributes`&#x20;

<details>

<summary><code>ADMIN SCHEMAS</code></summary>

```json

 "data": {
                "title": "boundary",
                "$schema": "http://json-schema.org/draft-07/schema#",
                "properties": {
                    "numberProperties": [
                        {
                            "name": "HCM_ADMIN_CONSOLE_TARGET_INDIVIDUAL",
                            "type": "number",
                            "isRequired": false,
                            "description": "Target Individual",
                            "orderNumber": 2
                        },
                        {
                            "name": "HCM_ADMIN_CONSOLE_TARGET_HOUSEHOLD",
                            "type": "number",
                            "isRequired": false,
                            "description": "Target Household",
                            "orderNumber": 3
                        },
                        {
                            "name": "HCM_ADMIN_CONSOLE_TARGET_PRODUCT",
                            "type": "number",
                            "isRequired": false,
                            "description": "Target Product",
                            "orderNumber": 4
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
                "campaignType": "DEFAULT"
            }
            

{
                "title": "boundaryWithTarget",
                "$schema": "http://json-schema.org/draft-07/schema#",
                "properties": {
                    "numberProperties": [
                        {
                            "name": "HCM_ADMIN_CONSOLE_TARGET_INDIVIDUAL",
                            "type": "number",
                            "isRequired": false,
                            "description": "Target Individual",
                            "orderNumber": 2
                        },
                        {
                            "name": "HCM_ADMIN_CONSOLE_TARGET_HOUSEHOLD",
                            "type": "number",
                            "isRequired": false,
                            "description": "Target Household",
                            "orderNumber": 3
                        },
                        {
                            "name": "HCM_ADMIN_CONSOLE_TARGET_PRODUCT",
                            "type": "number",
                            "isRequired": false,
                            "description": "Target Product",
                            "orderNumber": 4
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
                "campaignType": "DEFAULT"
            }

```

</details>

The **Admin Schema** defines templates and metadata required during campaign setup.

* **Module**: `HCM-ADMIN-CONSOLE`
* **Master**: `adminSchema`
* **Project Type**: `DEFAULT`

#### Action

Configure required entries to support:

* Boundary-based templates
* Target upload sheets
* Campaign metadata

This ensures the campaign setup screens work correctly for Co-delivery.

### Step 4: Configure Target Mapping (targetConfigs)

Target mapping is required for dashboard visualisation and reporting.

* **Master Name**: `targetConfigs`

#### Action

Configure:

* Target columns
* Beneficiary type mappings (Individual / Household)
* Association with project type `DEFAULT`

This allows the dashboard to correctly interpret and display targets for Co-delivery campaigns.

<details>

<summary>targetConfigs</summary>

```json

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
            }

```

</details>
