---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-console-configuration/console-ui-configuration/hcm-console-web-ui/campaign-setup/my-campaign/update-campaign-dates
---

# Update Campaign Dates

## Overview

The **Update Campaign Dates** feature allows users to modify:

* Campaign **start date**
* Campaign **end date**
* **Cycle start and end dates**

This feature is available **only for Ongoing and Upcoming campaigns** and is accessed from the **Actions** column on the **My Campaign** screen.

The behaviour of the update screen depends on an **MDMS configuration flag**, which determines whether dates are updated:

* **At the root (campaign) level**, or
* **At the boundary level**

## **Steps**

### Step 1: Enable the “Update Dates” Action

#### User Flow

1. Navigate to **My Campaign**.
2. Click the **Actions** button for an ongoing or upcoming campaign.
3. Select **Update Dates**.

**Outcome**

* The user is redirected to the Update Dates flow.
* The system evaluates the MDMS flag to decide which screen to render.

[MDMS link](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/dateWithBoundary.json)

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfkH3JKtFe5SWQopCQYO7kKPSwdcns2WRTZ4Ph9suRGJj3we1F4SZRjrJxbBUDyAv64dEiXcoIKtF5lGyNn9oQEcVwgUpPSg9y_AHsAMoCuiymb0qEkkPtD5F4uUEMlgpY-2O2el8dI0VejMCHUA4apTp6I?key=oCaYcIUXE6aGO0fM5H8mfQ" alt=""><figcaption></figcaption></figure>

### Step 2: Configure MDMS Flag for Date Updates

#### MDMS Configuration

This flag controls whether date updates are boundary-specific or campaign-wide.

**MDMS File**

* `dateWithBoundary.json`

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

#### Behaviour

* `true` → Dates can be updated **per boundary**
* `false` → Dates are updated **at the root campaign level**

### Step 3: Update Dates With Boundary (MDMS = true)

When `dateWithBoundary = true`, boundary-specific date updates are enabled.

#### 3.1 Select Boundary

**Screen Behaviour**

* User selects:
  * Hierarchy level
  * Specific boundary
* Clicks **Confirm** to proceed

**Key Files**

* `DateWithBoundary.js`
* `BoundaryWithDate.js`&#x20;
* [File Path](update-campaign-dates.md#file-path-https-github.com-egovernments-digit-frontend-blob-f00410f4d8198d8eebfaf7d7655661c64aff2397)

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfkUmT2IOZ-MWyEHRiQLB7gSmqiSxM2jc4xEF9ukKfVz_R7dT-lKAgkCDnXlynpe8U1Z9hrNEBruu_VcS4qC33My_GFFRPWrRKBznHC69jPJVsUNVUEqWFzaTi7IQQfwOUglkUqlIJ23S1KZ8z2Vny6BmIl?key=oCaYcIUXE6aGO0fM5H8mfQ" alt=""><figcaption></figcaption></figure>

#### 3.2 Modify Dates for Selected Boundary

**Displayed Data**

* Start date
* End date
* Cycle start and end dates for the selected boundary

**Edit Rules**

* Dates **before the current date** are **read-only**
* Only valid future dates can be edited

**User Action**

* Modify applicable dates
* Click **Confirm**

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfWroXSf_6zGu6K1NslavqA8O7X6vPzR3C7lBCRXPbJ7vJXycSnEjSrPxV6HL1YrQCKYZoEgnJrJRoyjpE4ONEcnNtBj76edKRi0zhAv8p6lFNxlsKdU3fdSDUNoGEMsmzAA5o7jxO9OqwOA6OYyN0iEVE?key=oCaYcIUXE6aGO0fM5H8mfQ" alt=""><figcaption></figcaption></figure>

#### 3.3 Save and Redirect

**Outcome**

* Dates are updated successfully
* A success screen is shown
* User is redirected back to **My Campaign**

[File Path](https://github.com/egovernments/DIGIT-Frontend/blob/8a5503923f3ec5ec3213aa7b901e8845500a6b83/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/BoundaryWithDate.js)

### Step 4: Update Dates Without Boundary (MDMS = false)

When `dateWithBoundary = false`, date updates apply to the entire campaign.

#### Screen Behaviour

* Campaign start date and end date are **pre-filled**
* Cycle dates are shown at the root level

**Key File**

* `DateAndCycleUpdate.js`&#x20;
* [File Path](https://github.com/egovernments/DIGIT-Frontend/blob/8a5503923f3ec5ec3213aa7b901e8845500a6b83/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/DateAndCycleUpdate.js)

#### Edit Rules

* Dates that have already passed are **non-editable**
* Only future dates can be modified

#### User Action

* Update required dates
* Click **Confirm**

**Outcome**

* Dates are saved
* The success screen is displayed
* User is redirected to **My Campaign**

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcmRknpIudsXl9L_YIYsckOLcT9ws140A3yhSSDbLuv8prl-j5hSCIB3MEZQtUJxfCZuRD3Hw2UegrKk3OCmkpx7hpB9O4njPlumtQEHLLX6fTSGXADmzk2VJV9vNHeDrmTtTqgbOpj3sc45m63fhSXPYE?key=oCaYcIUXE6aGO0fM5H8mfQ" alt=""><figcaption></figcaption></figure>

## Reference Links

[File Path](https://github.com/egovernments/DIGIT-Frontend/blob/8a5503923f3ec5ec3213aa7b901e8845500a6b83/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/UpdateDatesWithBoundaries.js)

[MDMS configuration](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/dateWithBoundary.json) to check whether the update date is at the root level or boundary level

#### Hooks

[Project Search](https://github.com/egovernments/DIGIT-Frontend/blob/f00410f4d8198d8eebfaf7d7655661c64aff2397/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useProjectSearchWithBoundary.js)

[Project Update](https://github.com/egovernments/DIGIT-Frontend/blob/f00410f4d8198d8eebfaf7d7655661c64aff2397/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useProjectUpdateWithBoundary.js)

[MDMS Link](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/dateWithBoundary.json)

#### API Details

<table><thead><tr><th width="367.5859375">End Point</th><th width="232">Action</th></tr></thead><tbody><tr><td>/health-project/v1/_search?tenantId=mz&#x26;limit=10&#x26;offset=0</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>/health-project/v1/_update</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>/health-project/v1/_search?tenantId=mz&#x26;limit=10&#x26;offset=0</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>/health-project/v1/_update</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>boundary-service/boundary-hierarchy-definition/_search</td><td>CAMPAIGN_MANAGER</td></tr></tbody></table>

#### Sample Payload

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
