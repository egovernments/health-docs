---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-console-configuration/enable-new-campaign-type
---

# Enable New Campaign Type

## Overview

A project type defines how campaigns are created, delivered, and monitored. Enabling a new campaign type involves configuring products, templates, attributes, targets, checklists, localisation, and default screen behaviour.

> ⚠️ Note: A generic campaign type (`codelivery`) already supports most use cases. Create a new campaign type only if explicitly required.

{% file src="../../../../.gitbook/assets/Creating new Project type.postman_collection.json" %}

{% hint style="info" %}
The default template requires Product & Variant configuration (optional).
{% endhint %}

## Steps

### Step 1: Configure Products & Variants

Default templates may require product and variant configuration.

1. **Create a Product**
   * Example product:

{% include "../../../../.gitbook/includes/product-....md" %}

**Create a Product Variant**

* Use the `productId` returned from the product creation API.
* Tag the variant with the project type code.

```postman_json
"ProductVariant": [
        {
            "tenantId": "dev",
            "productId": "P-2025-01-09-009569",
            "variation": "600mg",
            "sku": "Praziquantel - 600mg",
            "additionalFields": {
                "schema": "ProductVariant",
                "version": 1,
                "fields": [
                    {
                        "value": "NTD",
                        "key": "{{projectType}}"
                    }
                ]
            }
        }
    ]
```

### Step 2: Configure the Project Type Template

1. **Create a New Project Type**
   * Example project type code: `NTD`
   * Ensure the `id` in the `data` object is **unique**.
2. **Set Core Properties**
   * `group`: Example – `MALARIA`
   * `type`: Example – `multiround`
   * `beneficiaryType`: Choose one:
     * `INDIVIDUAL`
     * `HOUSEHOLD`

```postman_json
"INDIVIDUAL"
"HOUSEHOLD"
```

3. **Configure Cycles and Deliveries**
   1. You may prefill them or leave them empty.
   2. Example: one cycle with one delivery.

<details>

<summary>Cycles &#x26; Delivery Templates</summary>

PreSuggested Cycles

In the NTD Campaign, there’s one cycle, one delivery, but different products for different groups.

```
"cycles": [
                {
                    "id": 1,
                    "endDate": 1715279400000,
                    "startDate": 1714329000000,
                    "deliveries": [
                        {
                            "id": 1,
                            "doseCriteria": [
                                {
                                    "condition": "age>=5andheight>=178",
                                    "ProductVariants": [
                                        {
                                            "name": "Praziquantel 600mg",
                                            "quantity": 5,
                                            "productVariantId": "PVAR-2025-01-09-000145"
                                        }
                                    ]
                                },
                                {
                                    "condition": "age>=5and160<=height<177",
                                    "ProductVariants": [
                                        {
                                            "name": "Praziquantel 600mg",
                                            "quantity": 4,
                                            "productVariantId": "PVAR-2025-01-09-000145"
                                        }
                                    ]
                                },
                                {
                                    "condition": "age>=5and150<=height<159",
                                    "ProductVariants": [
                                        {
                                            "name": "Praziquantel 600mg",
                                            "quantity": 3,
                                            "productVariantId": "PVAR-2025-01-09-000145"
                                        }
                                    ]
                                },
                                {
                                    "condition": "age>=5and138<=height<149",
                                    "ProductVariants": [
                                        {
                                            "name": "Praziquantel 600mg",
                                            "quantity": 2.5,
                                            "productVariantId": "PVAR-2025-01-09-000145"
                                        }
                                    ]
                                },
                                {
                                    "condition": "age>=5and125<=height<137",
                                    "ProductVariants": [
                                        {
                                            "name": "Praziquantel 600mg",
                                            "quantity": 2,
                                            "productVariantId": "PVAR-2025-01-09-000145"
                                        }
                                    ]
                                },
                                {
                                    "condition": "age>=5and110<=height<124",
                                    "ProductVariants": [
                                        {
                                            "name": "Praziquantel 600mg",
                                            "quantity": 1.5,
                                            "productVariantId": "PVAR-2025-01-09-000145"
                                        }
                                    ]
                                },
                                {
                                    "condition": "age>=5and94<=height<109",
                                    "ProductVariants": [
                                        {
                                            "name": "Praziquantel 600mg",
                                            "quantity": 1,
                                            "productVariantId": "PVAR-2025-01-09-000145"
                                        }
                                    ]
                                },
                                {
                                    "condition": "age<5andheight<94",
                                    "ProductVariants": [
                                        {
                                            "name": "Praziquantel 600mg",
                                            "quantity": 0,
                                            "productVariantId": "PVAR-2025-01-09-000145"
                                        }
                                    ]
                                }
                            ],
                            "deliveryStrategy": "DIRECT"
                            // "mandatoryWaitSinceLastDeliveryInDays": null
                        }
                        
                    ]
                    // "mandatoryWaitSinceLastCycleInDays": null

                }
            ]
```



Empty Cyles Example

```
"cycles": [
]


```

</details>

4. **Attach Product Resources**
   1. Reference the product variant created in Step 1:

```postman_json
"resources": [
                {
                    "name": "Praziquantel - 600mg",
                    "productVariantId": "PVAR-2025-01-09-000145",
                    "isBaseUnitVariant": true
                }
            ]
```

The final constructed project type will be:

<details>

<summary>Project Type Config</summary>

```
{
  "id": "2a1bb2e7-06d8-4fe4-ba1e-f4a6363a2367",
  "code": "NTD",
  "name": "configuration for Campaign",
  "type": "multiround",
  "group": "MALARIA",
  "cycles": [
    {
      "id": 1,
      "endDate": 1715279400000,
      "startDate": 1714329000000,
      "deliveries": [
        {
          "id": 1,
          "doseCriteria": [
            {
              "condition": "age>=5andheight>=178",
              "ProductVariants": [
                {
                  "name": "Praziquantel 600mg",
                  "quantity": 5,
                  "productVariantId": "PVAR-2025-01-29-000446"
                }
              ]
            },
            {
              "condition": "age>=5and160<=height<177",
              "ProductVariants": [
                {
                  "name": "Praziquantel 600mg",
                  "quantity": 4,
                  "productVariantId": "PVAR-2025-01-29-000446"
                }
              ]
            },
            {
              "condition": "age>=5and150<=height<159",
              "ProductVariants": [
                {
                  "name": "Praziquantel 600mg",
                  "quantity": 3,
                  "productVariantId": "PVAR-2025-01-29-000446"
                }
              ]
            },
            {
              "condition": "age>=5and138<=height<149",
              "ProductVariants": [
                {
                  "name": "Praziquantel 600mg",
                  "quantity": 2,
                  "productVariantId": "PVAR-2025-01-29-000446"
                }
              ]
            },
            {
              "condition": "age>=5and125<=height<137",
              "ProductVariants": [
                {
                  "name": "Praziquantel 600mg",
                  "quantity": 2,
                  "productVariantId": "PVAR-2025-01-29-000446"
                }
              ]
            },
            {
              "condition": "age>=5and110<=height<124",
              "ProductVariants": [
                {
                  "name": "Praziquantel 600mg",
                  "quantity": 1,
                  "productVariantId": "PVAR-2025-01-29-000446"
                }
              ]
            },
            {
              "condition": "age>=5and94<=height<109",
              "ProductVariants": [
                {
                  "name": "Praziquantel 600mg",
                  "quantity": 1,
                  "productVariantId": "PVAR-2025-01-29-000446"
                }
              ]
            },
            {
              "condition": "age<5andheight<94",
              "ProductVariants": [
                {
                  "name": "Praziquantel 600mg",
                  "quantity": 0,
                  "productVariantId": "PVAR-2025-01-29-000446"
                }
              ]
            }
          ],
          "deliveryStrategy": "DIRECT"
        }
      ]
    }
  ],
  "resources": [
    {
      "name": "Praziquantel - 600mg",
      "productVariantId": "PVAR-2025-01-29-000446",
      "isBaseUnitVariant": true
    }
  ],
  "dashboardUrls": {
    "DISTRICT_SUPERVISOR": "2",
    "NATIONAL_SUPERVISOR": "1",
    "PROVINCIAL_SUPERVISOR": "1"
  },
  "beneficiaryType": "INDIVIDUAL"
}
```

</details>

### Step 3: Configure Delivery Attributes

Delivery attributes control what data can be captured during delivery.

1. **Search Existing Attributes**
   * MDMS schema:

```postman_json
"moduleName": "HCM-ADMIN-CONSOLE"
"masterName": "allAttributes"
```

Search for the attributes in MDMS. The collection has the curl named "Search allAttributes data".&#x20;

```postman_json
"MdmsCriteria": {
    "tenantId": "dev",
    "schemaCode": "HCM-ADMIN-CONSOLE.allAttributes" 
  }
```

2. **Link Attributes to the New Project Type -** Add `{{projectTypeCode}}` to the `projectTypes` list.\
   Sample update data is given below:

```postman_json
"Mdms": {
        "id": "f0f1c893-3f93-43ac-a18d-6f52b757b29c",
        "tenantId": "dev",
        "schemaCode": "HCM-ADMIN-CONSOLE.allAttributes",
        "uniqueIdentifier": "height",
        "data": {
                "key": 4,
                "code": "height",
                "i18nKey": "CAMPAIGN_ATTRIBUTE_HEIGHT",
                "projectTypes": [
                    "CO-DEL",
                    "MR-DN",
                    "{{projectTypeCode}}"
                ]
            },
        "isActive": true,
    }
```

{% hint style="warning" %}
Ensure attributes are set correctly, as they will be used for delivery rule creation.
{% endhint %}

### Step 4: Configure target template

* **Add Target Template Definitions**
  * Schema: `adminSchema`
  * Create two entries with unique identifiers:
    * `boundary.{{projectTypeCode}}`
    * `boundaryWithTarget.{{projectTypeCode}}`
* **Purpose**
  * Defines the target sheet structure used to enter village-level targets.
* **Add Localisation**
  * Add localisation keys for the newly created project type.

{% hint style="info" %}
This master is for the target sheet template used to enter target values for each village. Make sure to configure it accordingly.
{% endhint %}

<details>

<summary>HCM-ADMIN-CONSOLE.schemas</summary>

```
"Mdms": {
        "id": "925093c7-4f02-4baf-8af3-43b7f153ae7e",
            "tenantId": "dev",
            "schemaCode": "HCM-ADMIN-CONSOLE.schemas",
            "uniqueIdentifier": "boundary.{{projectTypeCode}}",
        "data": {
            "$schema": "http://json-schema.org/draft-07/schema#",
            "properties": {
                "numberProperties": [
                    {
                        "name": "HCM_ADMIN_CONSOLE_TARGET_{{projectTypeCode}}_COLUUM_1",
                        "type": "number",
                        "isRequired": true,
                        "description": "Total Households",
                        "orderNumber": 2
                    },
                    {
                        "name": "HCM_ADMIN_CONSOLE_TARGET_{{projectTypeCode}}_COLUUM_2",
                        "type": "number",
                        "isRequired": false,
                        "description": "Total Households",
                        "orderNumber": 3
                    },
                    {
                        "name": "HCM_ADMIN_CONSOLE_TARGET_{{projectTypeCode}}_COLUUM_3",
                        "type": "number",
                        "isRequired": false,
                        "description": "Number of Tablets",
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
            "title": "boundary",
            "campaignType": "{{projectTypeCode}}"
        },
        "isActive": true,
    }
```

</details>

### Step 5: Configure target mapping for the dashboard

Map dashboard targets to beneficiary types and columns.

{% hint style="info" %}
This configuration maps dashboard targets to columns, ensuring all listed columns align with beneficiaries. The supported beneficiary types include Individual & Household.
{% endhint %}

```
"data": {
            "campaignType": "{{projectTypeCode}}",
            "beneficiaries": [
                {
                    "columns": [
                        "HCM_ADMIN_CONSOLE_TARGET_{{projectTypeCode}}_COLUUM_1",
                        "HCM_ADMIN_CONSOLE_TARGET_{{projectTypeCode}}_COLUUM_2"
                    ],
                    "beneficiaryType": "HOUSEHOLD"
                },
                {
                    "columns": [
                        "HCM_ADMIN_CONSOLE_TARGET_{{projectTypeCode}}_COLUUM_3"
                    ],
                    "beneficiaryType": "INDIVIDUAL"
                }
            ]
        }
```

### Step 6: Configure checklist templates

* Add default checklist templates for the new campaign type.
* Refer to:
  * Existing default checklist configurations, or
  * The [checklist configuration documentation](../console-ui-configuration/hcm-console-web-ui/campaign-setup/manage-checklist/).

<details>

<summary>Checklist Templates</summary>

```json

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
            "campaignType": "{{projectTypeCode}}",
            "checklistType": "WAREHOUSE"
        }

```

</details>

### Step 7: Configure localisation messages

* **Add Localisation Entries**
  * Use the provided localisation collection.
  * Example locale: `en_MZ`.
* **Multi-Language Environments**
  * If your environment supports multiple languages, repeat the upsert for each locale.

<details>

<summary>Localisations</summary>

```json

{
            "code": "CAMPAIGN_CYCLE_CONFIGURE_HEADING_{{projectTypeCode}}",
            "message": "Configuration for {{projectTypeCode1}} Campaign",
            "module": "hcm-campaignmanager",
            "locale": "en_MZ"
        },
        {
            "code": "CAMPAIGN_PROJECT_{{projectTypeCode}}",
            "message": "{{projectTypeCode1}} Campaign",
            "module": "hcm-campaignmanager",
            "locale": "en_MZ"
        },
        {
            "code": "CAMPAIGN_DELIVERY_TAB_SUB_TEXT_{{projectTypeCode}}",
            "message": "Configure delivery condition for {{projectTypeCode1}} Campaign",
            "module": "hcm-campaignmanager",
            "locale": "en_MZ"
        },
          {
            "code": "HCM_ADMIN_CONSOLE_TARGET_{{projectTypeCode}}_COLUUM_1",
            "message": "Column 1",
            "module": "hcm-admin-schemas",
            "locale": "en_MZ"
        },
        {
            "code": "HCM_ADMIN_CONSOLE_TARGET_{{projectTypeCode}}_COLUUM_2",
            "message": "Column 2",
            "module": "hcm-admin-schemas",
            "locale": "en_MZ"
        },
        {
            "code": "HCM_ADMIN_CONSOLE_TARGET_{{projectTypeCode}}_COLUUM_3",
            "message": "Column 3",
            "module": "hcm-admin-schemas",
            "locale": "en_MZ"
        }

```

</details>

### Step 8: Configure Base Templates Screen Configs

* Create **default field-app screen configurations** for the new campaign type.
* This step is mandatory to ensure the campaign is usable end-to-end.
* Use existing base template configs as a reference.

Reference\
[#id-6.-formconfigtemplate](../#id-6.-formconfigtemplate "mention")

### Final Step: Restart Services

Restart the following services to ensure all templates and localisations load correctly:

* `localisation`
* `project-factory`

{% hint style="danger" %}
We are not suggesting the creation of a new campaign type at this time. We already have a campaign type called 'codelivery', which covers all the different use cases. However, if a new campaign type is required and recommended by WHO when project types are created, you can proceed with its creation. A project type is essentially a known template used for creating and delivering campaigns.
{% endhint %}
