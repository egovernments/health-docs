---
description: /project-factory/v1/project-type/fetch-from-microplan
---

# Integration with Microplan

## Overview <a href="#overview" id="overview"></a>

This document describes the web flow for updating an existing campaign by integrating the existing microplan with the console. This process involves the integration of several backend services to update the data in the facility, target, and user sheet in the existing campaign object.

## Services Used <a href="#services-used" id="services-used"></a>

* Core Services
* Plan Service
* Census Service

## Sequence Flow <a href="#sequence-flow" id="sequence-flow"></a>

1.  Initiate Request: The request body for the microplan integration will be:

    ```
    {
        "RequestInfo": {
            "apiId": "Rainmaker",
            "authToken": "{{auth}}",
            "msgId": "1730962198879|en_MZ",
            "plainAccessRequest": {}
        },
        "MicroplanDetails": {
            "tenantId": "mz",
            "campaignId": "58fb49a9-6772-4ecf-afc1-61f747e8c412",
            "planConfigurationId": "e314a0b1-648c-4f7b-8551-f9441df00eb4"
        }
    }

    Here campaignId will be the id of campaign for which the current plan is linked
    and planConfigurationId is the id of the microplan.
    ```
2. Validations: This request validates whether the `campaignId` and `planConfigurationId` exist in the system or are invalid.
3.  Update Facility Sheet: The process begins by searching for the facility associated with the `planConfigurationId`, which provides details about the facility code and the linked service boundaries. Next, a facility sheet is generated for the campaign. Once the facility sheet is obtained, the service boundaries are populated within the sheet where the specific facility code is present.

    After completing the facility sheet, it is validated using the **Validate API**. Once validation is successful, the campaign object is updated with the new `facilityId` and `resourceId`. We get the data to fill in this sheet from plan-service/plan/facility/\_search where data is like this and map the facilityId to the serviceBoundaries.

    Copy

    ```
    {
                "id": "01a6cdc9-f777-4792-ad17-6dc7042fe1fd",
                "tenantId": "mz",
                "planConfigurationId": "f44bffa1-653a-455a-998d-e556ac097d3b",
                "planConfigurationName": "Malaria-SMC Campaign-M1x3d-1-26 Nov 24",
                "facilityId": "F-2024-11-26-104823",
                "facilityName": "angelic being 3713",
                "residingBoundary": "MICROPLAN_MO_13_05_02_02_07_ZAYBAY_TOWN",
                "serviceBoundaries": [
                    "MICROPLAN_MO_13_05_01_03_04_GORBO_COMMUNITY",
                    "MICROPLAN_MO_13_05_01_03_03_FDA_COMMUNITY",
                    "MICROPLAN_MO_13_05_01_03_01_BARLAVILLE",
                    "MICROPLAN_MO_13_05_01_02_12_GARLOVILLE_COMMUNITY",
                    "MICROPLAN_MO_13_05_01_02_11_SUAH_COMMUNITY",
                    "MICROPLAN_MO_13_05_01_02_10_KANNAH_ROAD_COMMUNITY",
                    "MICROPLAN_MO_13_05_01_02_09_ZWEDRU_CENTRAL_MARKET",
                    "MICROPLAN_MO_13_05_01_02_08_ZOE_BUSH",
                    "MICROPLAN_MO_13_05_01_02_07_CITY_HALL_COMMUNITY",
                    "MICROPLAN_MO_13_05_01_02_06_WELBO_QUARTER",
                    "MICROPLAN_MO_13_05_01_02_05_TRIANGLE_COMMUNITY",
                    "MICROPLAN_MO_13_05_01_02_04_SPS_COMMUNITY",
                    "MICROPLAN_MO_13_05_01_02_03_BAPTIST_COMMUNITY",
                    "MICROPLAN_MO_13_05_01_02_02_TOWAH_COMMUNITY",
                    "MICROPLAN_MO_13_05_01_02_01_A_G__COMMUNITY",
                    "MICROPLAN_MO_13_05_01_01_09_NAO_COMMUNITY",
                    "MICROPLAN_MO_13_05_01_01_07_GBAGBAVILLE",
                    "MICROPLAN_MO_13_05_01_01_06_ELRZ_COMMUNITY",
                    "MICROPLAN_MO_13_05_01_01_05_MANDINGO_QUARTER",
                    "MICROPLAN_MO_13_05_01_01_04_ZANBO_QUARTER",
                    "MICROPLAN_MO_13_05_01_01_03_KYNE_QUARTER",
                    "MICROPLAN_MO_13_05_01_01_02_GBOE_QUARTER",
                    "MICROPLAN_MO_13_05_01_01_01_BOWEN_QUARTER"
                ],
                "additionalDetails": {
                    "capacity": 1280,
                    "fixedPost": "No",
                    "facilityName": "angelic being 3713",
                    "facilityType": "Storing Resource",
                    "facilityStatus": "Temporary",
                    "assignedVillages": [],
                    "servingPopulation": 15272
                },
                "active": true,
                "auditDetails": {
                    "createdBy": "29f73f64-2f5b-4699-b92c-4b093ac65749",
                    "lastModifiedBy": "bae97a73-8c70-4e09-92fd-d1ae97321cb5",
                    "createdTime": 1732615033646,
                    "lastModifiedTime": 1732619625034
                }
            }
    ```
4.  Update Target Sheet: The process begins by performing a plan census search using the `planConfigurationId`, which retrieves details about the boundary code and its associated census data. After obtaining the mapping between the boundary code and the linked census, a target sheet of type **boundary** is generated for the campaign and hierarchy by invoking the **Generate API**.

    A predefined MDMS schema ensures accurate mapping between the headers in the target sheet and the fields in the data. This schema acts as a blueprint, defining the correspondence between the data fields and their respective headers in the generated sheet. For this sheet, we get the data from the census search API, where the data looks like this:

    ````
     {
            "id": "baece49c-a7fa-49e7-bddd-d19ba71b2b89",
            "tenantId": "mz",
            "code": "HCM-ADMIN-CONSOLE.microplanIntegration",
            "description": "HCM-ADMIN-CONSOLE.microplanIntegration",
            "definition": {
                "type": "object",
                "title": "HCM-ADMIN-CONSOLE.microplanIntegration",
                "$schema": "http://json-schema.org/draft-07/schema#",
                "required": [
                    "type",
                    "mappings"
                ],
                "x-unique": [
                    "type"
                ],
                "properties": {
                    "type": {
                        "type": "string"
                    },
                    "mappings": {
                        "type": "array",
                        "minItems": 1,
                        "items": {
                            "type": "object",
                            "properties": {
                                "to": {
                                    "type": "string"
                                },
                                "from": {
                                    "type": "array",
                                    "items": {
                                        "type": "string"
                                    }
                                },
                                "filter": {
                                    "type": "string",
                                    "enum": [
                                        "includes",
                                        "equal"
                                    ],
                                    "default": "includes"
                                }
                            }
                        }
                    }
                },
                "isActive": true,
                "auditDetails": {
                    "createdBy": null,
                    "lastModifiedBy": null,
                    "createdTime": 1697098069220,
                    "lastModifiedTime": 1697098069220
                }
            }
        }
    ```
    ````

The sample data for filling the target sheet is:

```
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
```

Here, the **type** of the target sheet is constructed as `Target-<projectType>` of the campaign.

* **`to`**: This specifies the key to be extracted from the census object.
* **`from`**: These are the keys representing the headers that need to be enriched in the generated sheet.

This mapping ensures that the data from the census object is correctly aligned and populated into the appropriate headers in the target sheet. After populating the worksheet with data from the census objects, the file is uploaded to the **filestore**. Next, the sheet is validated using the **Validate API** with the type `boundaryWithTarget`. Once the validation is completed, the campaign object is updated with the newly generated`filestoreId` and `resourceId`. We get data from the census search as follows:

```
 {
            "id": "dc8521c0-102f-4879-bca2-97ad96883b7d",
            "tenantId": "mz",
            "hierarchyType": "MICROPLAN",
            "boundaryCode": "MICROPLAN_MO_13_05_04_01_03_TOFFOI_TOWN",
            "assignee": null,
            "status": "VALIDATED",
            "type": "people",
            "totalPopulation": 987,
            "populationByDemographics": null,
            "additionalFields": [
                {
                    "id": "8c66b784-212f-4771-9794-d554e0626466",
                    "key": "UPLOADED_HCM_ADMIN_CONSOLE_TARGET_POPULATION_AGE_3TO11",
                    "value": 432.00,
                    "showOnUi": true,
                    "editable": false,
                    "order": 3
                },
                {
                    "id": "bf0ba6b9-48e5-4545-b702-c6f97afdd604",
                    "key": "UPLOADED_HCM_ADMIN_CONSOLE_TOTAL_POPULATION",
                    "value": 987.00,
                    "showOnUi": true,
                    "editable": false,
                    "order": 1
                },
                {
                    "id": "5c16f657-f9b9-4100-b9a8-2a3898d2f89a",
                    "key": "CONFIRMED_HCM_ADMIN_CONSOLE_TOTAL_POPULATION",
                    "value": 987.00,
                    "showOnUi": true,
                    "editable": true,
                    "order": 2
                },
                {
                    "id": "8346d4a7-4e68-4481-a252-eb493fb08c42",
                    "key": "CONFIRMED_HCM_ADMIN_CONSOLE_TARGET_POPULATION_AGE_3TO11",
                    "value": 432.00,
                    "showOnUi": true,
                    "editable": true,
                    "order": 4
                },
                {
                    "id": "ca33c533-7abd-4325-a64a-52771a98857a",
                    "key": "UPLOADED_HCM_ADMIN_CONSOLE_TARGET_POPULATION_AGE_12TO59",
                    "value": 232.00,
                    "showOnUi": true,
                    "editable": false,
                    "order": 5
                },
                {
                    "id": "9e450a98-7229-4137-b93c-a6901e1561cc",
                    "key": "CONFIRMED_HCM_ADMIN_CONSOLE_TARGET_POPULATION_AGE_12TO59",
                    "value": 232.00,
                    "showOnUi": true,
                    "editable": true,
                    "order": 6
                }
            ],
            "effectiveFrom": 1732614985701,
            "effectiveTo": 1732617841760,
            "source": "f44bffa1-653a-455a-998d-e556ac097d3b",
            "facilityAssigned": true,
            "workflow": null,
            "jurisdictionMapping": null,
            "additionalDetails": {
                "facilityId": "F-2024-11-26-104824",
                "facilityName": "angelic being 3714",
                "UPLOADED_HCM_ADMIN_CONSOLE_TOTAL_POPULATION": 987,
                "CONFIRMED_HCM_ADMIN_CONSOLE_TOTAL_POPULATION": 987,
                "UPLOADED_HCM_ADMIN_CONSOLE_TARGET_POPULATION_AGE_3TO11": 432,
                "CONFIRMED_HCM_ADMIN_CONSOLE_TARGET_POPULATION_AGE_3TO11": 432,
                "UPLOADED_HCM_ADMIN_CONSOLE_TARGET_POPULATION_AGE_12TO59": 232,
                "CONFIRMED_HCM_ADMIN_CONSOLE_TARGET_POPULATION_AGE_12TO59": 232
            },
            "auditDetails": {
                "createdBy": "29f73f64-2f5b-4699-b92c-4b093ac65749",
                "lastModifiedBy": "d3fcb513-622c-4b68-a6fa-073267397da0",
                "createdTime": 1732614985701,
                "lastModifiedTime": 1732619464507
            }
        }
```

5. Update User Sheet: The process begins by fetching the plan associated with the `planConfigurationId` and retrieving the boundaries from the campaign details, specifically those of type **LOCALITY**. Next, for each locality, the count of all roles is obtained from the plan search response. This role count is then enriched in the corresponding sheet for that locality.

To map the roles and their requirements for determining the role count in the plan facility response, the predefined **MDMS schema** for the target is utilised. In this schema:

* **`to`**: Represents the role to be mapped.
* **`from`**: Specifies an array of keywords that must be present in the key to identify the role.

This ensures accurate and efficient mapping and population of role-related data in the sheet. Also used -

```
HCM-ADMIN-CONSOLE.HierarchySchema
```

Added a field consolidateUsersAt in the schema to filter for boundaries based on a particular hierarchy; Example: LOCALITY Sample Data:

```
{
                    "type": "console",
                    "group": [
                        "MALARIA",
                        "PERFORMANCE",
                        "ADMINISTRATIVEPOST",
                        "DISTRICT"
                    ],
                    "hierarchy": "MICROPLAN",
                    "department": [],
                    "lowestHierarchy": "VILLAGE",
                    "splitBoundariesOn": "DISTRICT",
                    "consolidateUsersAt": "LOCALITY"
                }
```

Sample MDMS data:

```
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
                }
```

After populating the sheet with the appropriate information, the sheet is validated by calling the **Validate API** with the type `userWithBoundary`. Once the validation is successful, the campaign object is updated accordingly. We get the data to fill in this sheet from this API:

```
  {
            "id": "eb33e406-a94a-4862-be9b-10e89f7759a3",
            "tenantId": "mz",
            "locality": "MICROPLAN_MO_13_05_04_01_11_GREBO_VILLAGE_2",
            "campaignId": "fab0e988-c124-4b2b-9f28-adbbc0c0bbb4",
            "planConfigurationId": "bc6e5fab-fd25-4b05-8286-7c567e88507a",
            "status": "VALIDATED",
            "assignee": null,
            "additionalDetails": null,
            "activities": [],
            "resources": [
                {
                    "id": "109745bf-e77e-42c6-ab33-32b5b2b591b9",
                    "resourceType": "NO_OF_BEDNETS_PER_BOUNDARY",
                    "estimatedNumber": 1.19,
                    "activityCode": null
                },
                {
                    "id": "07453754-16db-4884-bc88-f4e08d1a5e58",
                    "resourceType": "NO_OF_HOUSEHOLD_DISTRIBUTION_TEAMS_PER_BOUNDARY_FOR_THE_CAMPAIGN",
                    "estimatedNumber": 0.01,
                    "activityCode": null
                },
                {
                    "id": "2e803e3a-2735-426c-bdb0-b9556c20a8d3",
                    "resourceType": "NO_OF_BALES_PER_BOUNDARY",
                    "estimatedNumber": 0.01,
                    "activityCode": null
                },
                {
                    "id": "34007919-c5ed-4372-bcc5-2da8693d4972",
                    "resourceType": "NO_OF_MONITORS_FOR_HOUSEHOLD_DISTRIBUTION_TEAM_PER_BOUNDARY",
                    "estimatedNumber": 0.00,
                    "activityCode": null
                },
                {
                    "id": "95d1ed12-16d4-4c4f-94e9-e12289e6e634",
                    "resourceType": "NO_OF_HOUSEHOLD_DISTRIBUTION_TEAMS_PER_BOUNDARY_FOR_ONE_DAY",
                    "estimatedNumber": 1.23,
                    "activityCode": null
                },
                {
                    "id": "ef15c6d7-761a-494e-94d1-32dd1e5a2396",
                    "resourceType": "NO_OF_HOUSEHOLDS_PER_BOUNDARY",
                    "estimatedNumber": 1.28,
                    "activityCode": null
                },
                {
                    "id": "b8169c1f-eb9a-4329-97b5-8f2715af5832",
                    "resourceType": "NO_OF_FIXED_POST_REGISTRATION_TEAMS_PER_BOUNDARY_FOR_ONE_DAY",
                    "estimatedNumber": 0.88,
                    "activityCode": null
                },
                {
                    "id": "1e34c841-7f40-4fe2-9f44-e857ae1ee0df",
                    "resourceType": "NO_OF_FIXED_POST_REGISTRATION_TEAMS_PER_BOUNDARY_FOR_THE_CAMPAIGN",
                    "estimatedNumber": 0.01,
                    "activityCode": null
                },
                {
                    "id": "ce84ea0d-b670-4dad-b2b2-308da03af8fd",
                    "resourceType": "NO_OF_FIXED_POST_REGISTRATION_TEAM_SUPERVISORS_PER_BOUNDARY",
                    "estimatedNumber": 0.00,
                    "activityCode": null
                },
                {
                    "id": "96b60c74-6c0d-4f27-9192-51335d80fbce",
                    "resourceType": "NO_OF_STICKERS_ROLLS_PER_BOUNDARY",
                    "estimatedNumber": 0.01,
                    "activityCode": null
                },
                {
                    "id": "5c86bc8b-cd0f-41b3-bf4d-c30597559581",
                    "resourceType": "NO_OF_FIXED_POST_REGISTRATION_TEAM_MEMBERS_PER_BOUNDARY",
                    "estimatedNumber": 0.65,
                    "activityCode": null
                },
                {
                    "id": "29c5028d-2e78-433c-92bf-901d7d031677",
                    "resourceType": "NO_OF_HOUSEHOLD_DISTRIBUTION_TEAM_MEMBERS_PER_BOUNDARY",
                    "estimatedNumber": 0.32,
                    "activityCode": null
                },
                {
                    "id": "b0e007de-d437-4055-931c-181b0bf617bf",
                    "resourceType": "NO_OF_SUPERVISORS_FOR_HOUSEHOLD_DISTRIBUTION_TEAM_PER_BOUNDARY",
                    "estimatedNumber": 0.00,
                    "activityCode": null
                }
            ],
            "targets": [],
            "auditDetails": {
                "createdBy": "6c0fd096-60ec-45fd-b81c-526c3f1a3f0b",
                "lastModifiedBy": "7c6714e9-72c8-46f7-a2c3-14edfe20cb1b",
                "createdTime": 1732964373948,
                "lastModifiedTime": 1732965150594
            },
            "jurisdictionMapping": null,
            "workflow": null
        }
```

## Conclusion <a href="#conclusion" id="conclusion"></a>

This document outlines the process for updating an existing campaign by integrating a microplan through the admin console. It involves validating the `campaignId` and `planConfigurationId` and updating the facility, target, and user sheets using data from backend services.

1. **Facility Sheet**: Generated using facility details from the `planConfigurationId`, enriched with service boundaries, validated, and updated in the campaign object.
2. **Target Sheet**: Created by mapping census data to boundary codes using the MDMS schema. The sheet is populated, validated, uploaded, and updated in the campaign object.
3. **User Sheet**: Locality boundaries are fetched, role counts are calculated and enriched using the MDMS schema, and the sheet is validated before updating the campaign object.

This integration ensures accurate, automated updates and efficient campaign management.
