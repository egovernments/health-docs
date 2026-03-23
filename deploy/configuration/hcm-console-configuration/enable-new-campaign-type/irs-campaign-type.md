# IRS Campaign Type

For IRS to be displayed as the campaign type , initially it needs to added in the MDMS. Master name: projectTypes Module name: "HCM-PROJECT-TYPES" [https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/project-types.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/project-types.json)

campaign type with IRS

<figure><img src="https://egov-digit.gitbook.io/hcm-console/~gitbook/image?url=https%3A%2F%2Flh7-rt.googleusercontent.com%2Fdocsz%2FAD_4nXfH_qaHlEWOd_N-wUKxupmEMXozAMQsejO1iz5Bdy7X6TLD6ZZeVYkedcxxiiLbUJ7bxgSIq4gr9zHcgJ07T4KUi5JuXbErCf9u9iEsddBRMiCIGxMI1F17cMmGREmOzoFWYJbu3e-6xx5MKphcQ3aCCMs%3Fkey%3Dr-hCiZghJuy1mlIo4epSOA&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=8113c671&#x26;sv=2" alt=""><figcaption></figcaption></figure>

Changes in delivery details:

The delivery configuration in the MDMS needs to be updated. The desired properties will show the attributes, operator, and value

cycle details

<figure><img src="https://egov-digit.gitbook.io/hcm-console/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2FJdb4e4jIFb27lF1Wh5VZ%2Fimage.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=b29fec3d&#x26;sv=2" alt=""><figcaption></figcaption></figure>

For the IRS campaign type, the number of cycles and the number of deliveries will not be editable.

To make the cycle and deliveries not editable, we need to pass one flag in the delivery configuration.

Copy

```
 "IsDisable": true
```

delivery config

<figure><img src="https://egov-digit.gitbook.io/hcm-console/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2Ft32Wns8x21OtXuJR2rWg%2Fimage.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=c2bc1801&#x26;sv=2" alt=""><figcaption></figcaption></figure>

The delivery conditions page will be shown like this in which values will come from the MDMS.

Master name: HOUSE\_STRUCTURE\_TYPES

Module name: HCM

{% embed url="https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/house_structure_types.json" %}

For the target templates to be generated dynamically, data needs to be added in the adminSchema.

Copy

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
