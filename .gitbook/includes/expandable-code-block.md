---
title: Expandable code block
---



<details>

<summary>Sample Payload</summary>

````
```
   "CampaignDetails":  {
            "id": "2b68a3aa-fca2-462e-8d59-8821c9a56132",
            "tenantId": "mz",
            "status": "drafted",
            "action": "create",
            "campaignNumber": "CMP-2024-10-15-004031",
            "isActive": true,
            "parentId": "43503755-db1d-4cef-9851-72360ee6eaa1",
            "campaignName": "LLIN-OCT15a",
            "projectType": "LLIN-mz",
            "hierarchyType": "HIERARCHYTEST",
            "boundaryCode": "",
            "projectId": null,
            "startDate": 1727202600000,
            "endDate": 1727720999000,
            "additionalDetails": {
                "key": 10,
                "beneficiaryType": "HOUSEHOLD"
            },
            "resources": [
            {
                "type": "facility",
                "filename": "update-facility.xlsx",
                "resourceId": "42c04e62-4b7b-4697-b2bd-aa90a212164c",
                "filestoreId": "20420b29-d913-4412-b3bd-34b850e2677b"
            },
            {
                "type": "boundaryWithTarget",
                "filename": "updated-boundary.xlsx",
                "resourceId": "8567db53-450e-465d-a14a-46e2690cf728",
                "filestoreId": "30ae3fd6-b77c-42e7-9a33-e88e29369764"
            },
            {
                "type": "user",
                "filename": "updated-user.xlsx",
                "resourceId": "fcc4a423-6ac5-4ee4-80c2-0f915a95253f",
                "filestoreId": "3c531af7-d923-47cc-b58a-c501a73e749c"
            }
        ],
            "boundaries": [],
            "deliveryRules": [
                {
                    "active": true,
                    "cycleIndex": "1",
                    "deliveries": [
                        {
                            "active": true,
                            "deliveryIndex": "1",
                            "deliveryRules": [
                                {
                                    "ruleKey": 1,
                                    "delivery": {},
                                    "products": [
                                        {
                                            "key": 1,
                                            "count": 1,
                                            "value": "PVAR-2024-05-09-000333"
                                        }
                                    ],
                                    "attributes": [
                                        {
                                            "key": 1,
                                            "value": "1",
                                            "operator": {
                                                "code": "LESS_THAN_EQUAL_TO"
                                            },
                                            "attribute": {
                                                "code": "CAMPAIGN_BEDNET_INDIVIDUAL_LABEL"
                                            }
                                        },
                                        {
                                            "key": 2,
                                            "value": "3",
                                            "operator": {
                                                "code": "LESS_THAN_EQUAL_TO"
                                            },
                                            "attribute": {
                                                "code": "CAMPAIGN_BEDNET_HOUSEHOLD_LABEL"
                                            }
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ],
            "auditDetails": {
                "createdBy": "63a21269-d40d-4c26-878f-4f4486b1f44b",
                "lastModifiedBy": "63a21269-d40d-4c26-878f-4f4486b1f44b",
                "createdTime": 1728983362986,
                "lastModifiedTime": 1728983362995
            }
        },
```
````

</details>
