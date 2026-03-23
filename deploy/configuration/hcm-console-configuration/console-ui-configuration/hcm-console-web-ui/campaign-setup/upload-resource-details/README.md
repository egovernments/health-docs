# Upload Resource Details

The resource upload details consists of 3 types of uploads:&#x20;

* Upload Target Data
* Facility Upload
* User Upload
* Upload Summary

## 1. Upload Target Data

This screen will come after a user selects the boundaries.&#x20;

<figure><img src="../../../../../../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

When a user clicks on the download template button, an Excel will get downloaded which will contain readMe, Boundary Data sheet along with the sheets with districts, where the user has to fill the target at the lowest level. After the file is uploaded, it will go for validation. Once validated, a user can go to the next page, where the user can delete the file and move to the next page to upload facility date.

## 2. Upload Facility Data

This screen will come after the target upload screen.

<figure><img src="../../../../../../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

In this screen, when a user clicks on the download template, an Excel gets downloaded containing readMe, Facility sheet, and BoundaryData sheet. A user has to fill in the boundary codes and from that sheet, the user has to fill in the facility sheet.

## 3. Upload User Data&#x20;

This screen will appear after the facility details screen.

<figure><img src="../../../../../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

When a user clicks on the download template, an Excel file gets downloaded that consists of readMe, User Sheet, and BoundaryData. The user has to fillout the user sheet only.&#x20;

All the 3 downloads are happening through the Generate and Download APIs.\
For the Generate API, the following hook is used: \
[https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useGenerateIdCampaign.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useGenerateIdCampaign.js)

This hook will return the ID which is stored in the local storage according to the type:&#x20;

```javascript
HCM_CAMPAIGN_MANAGER_UPLOAD_ID
```

Next, /project-factory/v1/data/\_download is used to download the template.

## 4. Summary

<figure><img src="../../../../../../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

This screen displays all the files which were uploaded in the previous screens, \
Validation in this screen -

All the 3 files are mandatory to upload in this step otherwise the user is not allowed to move to the next step.

## Schema Validation

After uploading the templates, UI validation is done through schema stored in the MDMS:\
Schema Data link: [https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/adminSchema.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/adminSchema.json)

Schema Module = adminSchema\
Below is the admin schema-

<details>

<summary>SchemaDefinitions</summary>

```
 "SchemaDefinitions": [
        {
            "id": "92fb3b53-adfe-44e9-ab27-da3209b5e0f1",
            "tenantId": "mz",
            "code": "HCM-ADMIN-CONSOLE.adminSchema",
            "description": null,
            "definition": {
                "type": "object",
                "title": "Comprehensive Example Schema",
                "$schema": "http://json-schema.org/draft-07/schema#",
                "required": [
                    "$schema",
                    "title",
                    "campaignType"
                ],
                "x-unique": [
                    "title",
                    "campaignType"
                ],
                "properties": {
                    "title": {
                        "type": "string"
                    },
                    "$schema": {
                        "enum": [
                            "http://json-schema.org/draft-07/schema#"
                        ],
                        "type": "string",
                        "default": "http://json-schema.org/draft-07/schema#"
                    },
                    "properties": {
                        "type": "object",
                        "properties": {
                            "enumProperties": {
                                "type": "array",
                                "items": {
                                    "type": "object",
                                    "required": [
                                        "name",
                                        "description"
                                    ],
                                    "properties": {
                                        "enum": {
                                            "type": "array",
                                            "items": {
                                                "type": "string"
                                            }
                                        },
                                        "name": {
                                            "type": "string"
                                        },
                                        "isUnique": {
                                            "type": "boolean"
                                        },
                                        "hideColumn": {
                                            "type": "boolean"
                                        },
                                        "isRequired": {
                                            "type": "boolean"
                                        },
                                        "description": {
                                            "type": "string"
                                        },
                                        "orderNumber": {
                                            "type": "integer",
                                            "minimum": 1
                                        },
                                        "errorMessage": {
                                            "type": "string"
                                        },
                                        "freezeColumn": {
                                            "type": "boolean"
                                        }
                                    },
                                    "minProperties": 1
                                },
                                "minItems": 1
                            },
                            "numberProperties": {
                                "type": "array",
                                "items": {
                                    "type": "object",
                                    "required": [
                                        "name",
                                        "description"
                                    ],
                                    "properties": {
                                        "name": {
                                            "type": "string"
                                        },
                                        "type": {
                                            "enum": [
                                                "number"
                                            ],
                                            "type": "string"
                                        },
                                        "maximum": {
                                            "type": "number"
                                        },
                                        "minimum": {
                                            "type": "number"
                                        },
                                        "isUnique": {
                                            "type": "boolean"
                                        },
                                        "hideColumn": {
                                            "type": "boolean"
                                        },
                                        "isRequired": {
                                            "type": "boolean"
                                        },
                                        "multipleOf": {
                                            "type": "number"
                                        },
                                        "description": {
                                            "type": "string"
                                        },
                                        "orderNumber": {
                                            "type": "integer",
                                            "minimum": 1
                                        },
                                        "errorMessage": {
                                            "type": "string"
                                        },
                                        "freezeColumn": {
                                            "type": "boolean"
                                        },
                                        "exclusiveMaximum": {
                                            "type": "boolean"
                                        },
                                        "exclusiveMinimum": {
                                            "type": "boolean"
                                        }
                                    },
                                    "minProperties": 1
                                },
                                "minItems": 1
                            },
                            "stringProperties": {
                                "type": "array",
                                "items": {
                                    "type": "object",
                                    "required": [
                                        "name",
                                        "description"
                                    ],
                                    "properties": {
                                        "name": {
                                            "type": "string"
                                        },
                                        "type": {
                                            "enum": [
                                                "string"
                                            ],
                                            "type": "string"
                                        },
                                        "pattern": {
                                            "type": "string",
                                            "format": "regex"
                                        },
                                        "isUnique": {
                                            "type": "boolean"
                                        },
                                        "maxLength": {
                                            "type": "integer",
                                            "minimum": 0
                                        },
                                        "minLength": {
                                            "type": "integer",
                                            "minimum": 0
                                        },
                                        "hideColumn": {
                                            "type": "boolean"
                                        },
                                        "isRequired": {
                                            "type": "boolean"
                                        },
                                        "description": {
                                            "type": "string"
                                        },
                                        "orderNumber": {
                                            "type": "integer",
                                            "minimum": 1
                                        },
                                        "errorMessage": {
                                            "type": "string"
                                        },
                                        "freezeColumn": {
                                            "type": "boolean"
                                        }
                                    },
                                    "minProperties": 1
                                },
                                "minItems": 1
                            },
                            "additionalProperties": {
                                "type": "boolean"
                            }
                        },
                        "additionalProperties": false
                    },
                    "campaignType": {
                        "type": "string"
                    }
                },
                "description": "A simplified JSON Schema example based on data type.",
                "additionalProperties": false
            },
            "isActive": true,
            "auditDetails": {
                "createdBy": "8b110055-330f-4e7b-b4c0-f618f29b9d47",
                "lastModifiedBy": "8b110055-330f-4e7b-b4c0-f618f29b9d47",
                "createdTime": 1718169189364,
                "lastModifiedTime": 1718169189364
            }
        }
    ]
```

</details>

By using AJV Validation , we are validating the headers of the facility sheet. We are also doing some basic validations for the data such as-

* Facility Type can only be Warehouse/Health Facility
* Facility Name can only be string
* Facility Status can only be Temporary or Permanent etc.

Apart from this, we are also validating (v0.3.1):

1. **Sheet Names**: Ensuring the sheet names in all three uploads match the expected values.
2. **Template Locale**: The uploaded template should be in the same locale in which it was generated.
3. **Campaign ID**: The campaign ID in the upload must match the campaign ID for which the template was generated. This validation is conditional and can be toggled at the DevOps level.

For target validation, we use schema only for validating the header of the target and boundary codes. Here, we also validate the target at the lowest level, where the value should be between:

```javascript
targetValue <= 0 || targetValue >= 100000000
```

### Validation API Call:

Before calling we are using base time out which is fetched from the MDMS&#x20;

For more information on this schema, you can refer to:&#x20;

{% content-ref url="/broken/pages/HOE2bIXaoPn6bibfTTpA" %}
[Broken link](/broken/pages/HOE2bIXaoPn6bibfTTpA)
{% endcontent-ref %}

[https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/baseTimeOut.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/baseTimeOut.json)

### Reference Links:

For the backend validation, we use the following hook:\
[https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useResourceData.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useResourceData.js)

The screens are using the given below components for upload and validation-

Bulk upload: [https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/BulkUpload.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/BulkUpload.js)

Preview component: [https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/XlsPreview.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/XlsPreview.js)

File screen: [https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/UploadData.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/UploadData.js)

### API Details

<table><thead><tr><th width="280">End Point </th><th width="105">Role</th><th>Details</th></tr></thead><tbody><tr><td>/project-factory/v1/data/_download</td><td>CAMPAIGN_MANAGER</td><td><p>Params will be different for different types-<br><br>1) boundary<br>tenantId:mz</p><p>type:boundary</p><p>hierarchyType:ADMIN</p><p>id:987eadc3-55a0-4553-925d-bf8087f57e5a<br><br>2) facilityWithBoundary<br>tenantId:mz</p><p>type:facilityWithBoundary</p><p>hierarchyType:ADMIN</p><p>id:052f59fc-18a7-4e07-816a-f5d8062b56b5<br><br>3) userWithBoundary<br>tenantId:mz</p><p>type:userWithBoundary</p><p>hierarchyType:ADMIN</p><p>id:fbfbd393-d053-4f51-9e12-1068b97da292</p></td></tr><tr><td>/project-factory/v1/data/_create</td><td>CAMPAIGN_MANAGER</td><td><p>1)  type: boundaryWithTarget<br>{ "type": "boundaryWithTarget", ""action": "validate",</p><p> "campaignId": "13175791-db53-4d10-be90-2dba1c138756" }</p><p><br>2) type: facility<br>{ "type": "facility",</p><p>"action": "validate",</p><p> "campaignId": "13175791-db53-4d10-be90-2dba1c138756"}</p><p><br>3) type: user<br>{ "type": "user", </p><p> "action": "validate", </p><p>"campaignId": "13175791-db53-4d10-be90-2dba1c138756" }</p></td></tr><tr><td></td><td></td><td></td></tr></tbody></table>

## New Features

A new pop-up has been added which displays the option to download the template in all three upload screens.

**Use Case:**&#x20;

when the user comes after clicking next on the delivery screen and the file is not uploaded then this pop-up is displayed.

<figure><img src="../../../../../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>
