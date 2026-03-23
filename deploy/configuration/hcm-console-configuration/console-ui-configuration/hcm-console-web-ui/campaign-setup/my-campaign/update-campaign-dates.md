# Update Campaign Dates

## Overview

This screen enables users to update the start date, end date, and cycle dates for both ongoing and upcoming campaigns. Additionally, an 'Actions' column has been added to the "My Campaign" screen, providing more options for managing the campaigns.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfkH3JKtFe5SWQopCQYO7kKPSwdcns2WRTZ4Ph9suRGJj3we1F4SZRjrJxbBUDyAv64dEiXcoIKtF5lGyNn9oQEcVwgUpPSg9y_AHsAMoCuiymb0qEkkPtD5F4uUEMlgpY-2O2el8dI0VejMCHUA4apTp6I?key=oCaYcIUXE6aGO0fM5H8mfQ" alt=""><figcaption></figcaption></figure>

When a user clicks on 'Actions', they will see the "Update Dates" option. Selecting "Update Dates" redirects the user to the update date screen.

We have added an MDMS configuration flag to determine whether the dates can be updated with or without boundaries. Depending on the MDMS flag, the appropriate screen will be rendered.

#### MDMS link: [https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/dateWithBoundary.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/dateWithBoundary.json)

```

{
  "tenantId": "mz",
  "moduleName": "HCM-ADMIN-CONSOLE",
  "dateWithBoundary": [
  {
  "dateWithBoundary": true // if true, date change as per boundary level
                           // if false, date change on root level 
  }
]
}

```

### Update Dates Based on Boundary

If the MDMS flag for updating dates with a boundary is set to true, the corresponding screen for updating dates will be rendered.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfkUmT2IOZ-MWyEHRiQLB7gSmqiSxM2jc4xEF9ukKfVz_R7dT-lKAgkCDnXlynpe8U1Z9hrNEBruu_VcS4qC33My_GFFRPWrRKBznHC69jPJVsUNVUEqWFzaTi7IQQfwOUglkUqlIJ23S1KZ8z2Vny6BmIl?key=oCaYcIUXE6aGO0fM5H8mfQ" alt=""><figcaption></figcaption></figure>

#### File Path:[https://github.com/egovernments/DIGIT-Frontend/blob/f00410f4d8198d8eebfaf7d7655661c64aff2397/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/DateWithBoundary.js](https://github.com/egovernments/DIGIT-Frontend/blob/f00410f4d8198d8eebfaf7d7655661c64aff2397/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/DateWithBoundary.js)

If the MDMS flag for updating with a boundary is set to true, the corresponding screen will be rendered. On this screen, the user first selects the hierarchy level and boundary they wish to update. After making their selection, the user clicks the 'Confirm' button.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfWroXSf_6zGu6K1NslavqA8O7X6vPzR3C7lBCRXPbJ7vJXycSnEjSrPxV6HL1YrQCKYZoEgnJrJRoyjpE4ONEcnNtBj76edKRi0zhAv8p6lFNxlsKdU3fdSDUNoGEMsmzAA5o7jxO9OqwOA6OYyN0iEVE?key=oCaYcIUXE6aGO0fM5H8mfQ" alt=""><figcaption></figcaption></figure>

File Path: [https://github.com/egovernments/DIGIT-Frontend/blob/8a5503923f3ec5ec3213aa7b901e8845500a6b83/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/BoundaryWithDate.js](https://github.com/egovernments/DIGIT-Frontend/blob/8a5503923f3ec5ec3213aa7b901e8845500a6b83/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/BoundaryWithDate.js)<br>

Based on the selected boundaries, the corresponding dates are displayed. The user can then change the dates and cycle dates as needed. Fields with dates that have already passed (relative to today) are made non-editable.

After making the desired changes, the user clicks the 'Confirm' button to update the dates. Once the update is successful, a success response screen is shown, and the user is redirected back to the "My Campaign" screen.

### Update Dates Without Boundary

If the MDMS flag is set to false, the corresponding screen is rendered to update the dates without considering boundaries, at the root level.

When the user clicks on "Update Date" for the respective campaign, the update date screen is shown with all the prefilled start and end dates. The user can then make the necessary changes.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcmRknpIudsXl9L_YIYsckOLcT9ws140A3yhSSDbLuv8prl-j5hSCIB3MEZQtUJxfCZuRD3Hw2UegrKk3OCmkpx7hpB9O4njPlumtQEHLLX6fTSGXADmzk2VJV9vNHeDrmTtTqgbOpj3sc45m63fhSXPYE?key=oCaYcIUXE6aGO0fM5H8mfQ" alt=""><figcaption></figcaption></figure>

#### File Path: [https://github.com/egovernments/DIGIT-Frontend/blob/8a5503923f3ec5ec3213aa7b901e8845500a6b83/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/DateAndCycleUpdate.js](https://github.com/egovernments/DIGIT-Frontend/blob/8a5503923f3ec5ec3213aa7b901e8845500a6b83/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/DateAndCycleUpdate.js)

The user can change the editable dates. Any date fields that have passed the current date are non-editable. Once the user confirms the date change, the data is updated. After a successful update, the user is redirected to a success screen.

#### File Path:

[https://github.com/egovernments/DIGIT-Frontend/blob/8a5503923f3ec5ec3213aa7b901e8845500a6b83/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/UpdateDatesWithBoundaries.js](https://github.com/egovernments/DIGIT-Frontend/blob/8a5503923f3ec5ec3213aa7b901e8845500a6b83/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/UpdateDatesWithBoundaries.js)

MDMS configuration to check whether the update date is at the root level or boundary level: [https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/dateWithBoundary.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/dateWithBoundary.json)

## Hooks

#### Project Search: [https://github.com/egovernments/DIGIT-Frontend/blob/f00410f4d8198d8eebfaf7d7655661c64aff2397/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useProjectSearchWithBoundary.js](https://github.com/egovernments/DIGIT-Frontend/blob/f00410f4d8198d8eebfaf7d7655661c64aff2397/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useProjectSearchWithBoundary.js)

#### Project Update:

[https://github.com/egovernments/DIGIT-Frontend/blob/f00410f4d8198d8eebfaf7d7655661c64aff2397/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useProjectUpdateWithBoundary.js](https://github.com/egovernments/DIGIT-Frontend/blob/f00410f4d8198d8eebfaf7d7655661c64aff2397/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useProjectUpdateWithBoundary.js)

**MDMS Link:**&#x20;

[https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/dateWithBoundary.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/dateWithBoundary.json)

### API Details

### API Details

<table><thead><tr><th width="345">End Point</th><th width="232">Action</th></tr></thead><tbody><tr><td>/health-project/v1/_search?tenantId=mz&#x26;limit=10&#x26;offset=0</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>/health-project/v1/_update</td><td>CAMPAIGN_MANAGER</td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td>/health-project/v1/_search?tenantId=mz&#x26;limit=10&#x26;offset=0</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>/health-project/v1/_update</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>boundary-service/boundary-hierarchy-definition/_search</td><td>CAMPAIGN_MANAGER</td></tr></tbody></table>

### Sample:

{% code overflow="wrap" %}
```json

  
"Projects": [
    {
        "id": "c714afc2-9ab8-4d0a-bf2b-71fe56649a77",
        "tenantId": "mz",
        "projectNumber": "PJT-2024-07-08-001876",
        "name": "MR_DN_CHECK_TEST_001",
        "projectType": "MR-DN",
        "projectSubType": "MR-DN",
        "department": "MALARIA",
        "description": "configuration for Multi Round Campaigns",
        "referenceID": "b8bb1cd8-99f8-4bf8-82e3-751c06aa70e4",
        "projectTypeId": "b1107f0c-7a91-4c76-afc2-a279d8a7b76a",
        "documents": null,
        "address": {
            "id": "9e3b5e50-5dde-4f8a-88cb-9b9b1e9c3dab",
            "tenantId": "mz",
            "clientReferenceId": null,
            "doorNo": null,
            "latitude": 0,
            "longitude": 0,
            "locationAccuracy": 0,
            "type": null,
            "addressLine1": null,
            "addressLine2": null,
            "landmark": null,
            "city": null,
            "pincode": null,
            "buildingName": null,
            "street": null,
            "boundaryType": "Country",
            "boundary": "WORKBENCH_MO",
            "locality": null
        },
        "startDate": 1721154600000,
        "endDate": 1725128999000,
        "isTaskEnabled": false,
        "parent": null,
        "projectHierarchy": null,
        "natureOfWork": null,
        "ancestors": null,
        "descendants": null,
        "targets": [
            {
                "id": "fd1faf99-7980-429c-99c6-4041b854376f",
                "beneficiaryType": "INDIVIDUAL",
                "totalNo": 62520,
                "targetNo": 62520,
                "isDeleted": false,
                "auditDetails": {
                    "createdBy": "867ba408-1b82-4746-8274-eb916e625fea",
                    "lastModifiedBy": "867ba408-1b82-4746-8274-eb916e625fea",
                    "createdTime": 1720417261161,
                    "lastModifiedTime": 1721633347090
                }
            }
        ],
        "additionalDetails": {
            "projectType": {
                "id": "b1107f0c-7a91-4c76-afc2-a279d8a7b76a",
                "code": "MR-DN",
                "name": "MR_DN_CHECK_TEST_001",
                "group": "MALARIA",
                "cycles": [
                    {
                        "id": "1",
                        "endDate": 1721586599000,
                        "startDate": 1721241000000,
                        "deliveries": [
                            {
                                "id": "1",
                                "doseCriteria": [
                                    {
                                        "condition": "3<=ageandage<=11",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-02-26-000034",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    },
                                    {
                                        "condition": "12<=ageandage<=59",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-03-15-000042",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    }
                                ],
                                "deliveryStrategy": "DIRECT",
                                "mandatoryWaitSinceLastDeliveryInDays": null
                            },
                            {
                                "id": "2",
                                "doseCriteria": [
                                    {
                                        "condition": "3<=ageandage<=11",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-02-26-000034",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    },
                                    {
                                        "condition": "12<=ageandage<=59",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-03-15-000043",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    }
                                ],
                                "deliveryStrategy": "INDIRECT",
                                "mandatoryWaitSinceLastDeliveryInDays": null
                            },
                            {
                                "id": "3",
                                "doseCriteria": [
                                    {
                                        "condition": "3<=ageandage<=11",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-03-15-000042",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    },
                                    {
                                        "condition": "12<=ageandage<=59",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-03-15-000042",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    }
                                ],
                                "deliveryStrategy": "INDIRECT",
                                "mandatoryWaitSinceLastDeliveryInDays": null
                            }
                        ],
                        "mandatoryWaitSinceLastCycleInDays": null
                    },
                    {
                        "id": "2",
                        "endDate": 1722104999000,
                        "startDate": 1721673000000,
                        "deliveries": [
                            {
                                "id": "1",
                                "doseCriteria": [
                                    {
                                        "condition": "3<=ageandage<=11",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-02-26-000034",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    },
                                    {
                                        "condition": "12<=ageandage<=59",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-03-15-000043",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    }
                                ],
                                "deliveryStrategy": "DIRECT",
                                "mandatoryWaitSinceLastDeliveryInDays": null
                            },
                            {
                                "id": "2",
                                "doseCriteria": [
                                    {
                                        "condition": "3<=ageandage<=11",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-02-26-000034",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    },
                                    {
                                        "condition": "12<=ageandage<=59",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-03-15-000043",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    }
                                ],
                                "deliveryStrategy": "INDIRECT",
                                "mandatoryWaitSinceLastDeliveryInDays": null
                            },
                            {
                                "id": "3",
                                "doseCriteria": [
                                    {
                                        "condition": "3<=ageandage<=11",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-02-26-000034",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    },
                                    {
                                        "condition": "12<=ageandage<=59",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-03-15-000042",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    }
                                ],
                                "deliveryStrategy": "INDIRECT",
                                "mandatoryWaitSinceLastDeliveryInDays": null
                            }
                        ],
                        "mandatoryWaitSinceLastCycleInDays": null
                    },
                    {
                        "id": "3",
                        "endDate": 1722709799000,
                        "startDate": 1722277800000,
                        "deliveries": [
                            {
                                "id": "1",
                                "doseCriteria": [
                                    {
                                        "condition": "3<=ageandage<=11",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-02-26-000034",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    },
                                    {
                                        "condition": "12<=ageandage<=59",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-03-15-000042",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    }
                                ],
                                "deliveryStrategy": "DIRECT",
                                "mandatoryWaitSinceLastDeliveryInDays": null
                            },
                            {
                                "id": "2",
                                "doseCriteria": [
                                    {
                                        "condition": "3<=ageandage<=11",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-02-26-000034",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    },
                                    {
                                        "condition": "12<=ageandage<=59",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-03-15-000042",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    }
                                ],
                                "deliveryStrategy": "INDIRECT",
                                "mandatoryWaitSinceLastDeliveryInDays": null
                            },
                            {
                                "id": "3",
                                "doseCriteria": [
                                    {
                                        "condition": "3<=ageandage<=11",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-03-15-000042",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    },
                                    {
                                        "condition": "12<=ageandage<=59",
                                        "ProductVariants": [
                                            {
                                                "quantity": 1,
                                                "productVariantId": "PVAR-2024-03-15-000042",
                                                "isBaseUnitVariant": true
                                            }
                                        ]
                                    }
                                ],
                                "deliveryStrategy": "INDIRECT",
                                "mandatoryWaitSinceLastDeliveryInDays": null
                            }
                        ],
                        "mandatoryWaitSinceLastCycleInDays": null
                    }
                ],
                "resources": [
                    {
                        "productVariantId": "PVAR-2024-02-26-000034",
                        "isBaseUnitVariant": true
                    },
                    {
                        "productVariantId": "PVAR-2024-03-15-000042",
                        "isBaseUnitVariant": true
                    },
                    {
                        "productVariantId": "PVAR-2024-03-15-000043",
                        "isBaseUnitVariant": true
                    }
                ],
                "validMaxAge": 59,
                "validMinAge": 3,
                "beneficiaryType": "INDIVIDUAL",
                "observationStrategy": "DOT1"
            }
        },
        "isDeleted": false,
        "rowVersion": 0,
        "auditDetails": {
            "createdBy": "867ba408-1b82-4746-8274-eb916e625fea",
            "lastModifiedBy": "867ba408-1b82-4746-8274-eb916e625fea",
            "createdTime": 1720417261161,
            "lastModifiedTime": 1721633347090
        }
    }
]
```
{% endcode %}
