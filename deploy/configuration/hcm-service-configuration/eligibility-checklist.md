# Eligibility Checklist

## Overview

This document describes the configuration structure for checklist attributes, response-to-points mapping, precedence logic, and flow assignment. The configuration supports dynamic scoring and prioritisation of actions (flows) based on user responses within a checklist.

***

## Pre-requisites

* **Checklist Engine:**
  * The system must support dynamic attribute rendering and response capture.
* **Points Mapping Logic:**
  * Ability to map responses to points for each flow type.
* **Precedence Logic:**
  * Support for precedence attribute recognition and flow assignment.
* **Unique Attribute Codes:**
  * Each attribute must have a unique code for mapping and tracking.

***

## Functionalities

#### Attribute Definition

* Each checklist is made up of **attributes** (questions/fields).
* Every attribute has:
  * A unique **code** (e.g., `SMC1`, `SMC1.YES.SM1`)
  * Possible responses (e.g., `YES`, `NO`, `NOT_SELECTED`)
  * Association with one or more **flow types**.

#### Points Mapping

* Each possible response is mapped to **points** per flow type.
* Example:
  * `SMC1.YES` → `{ TO_ADMINISTER: 2, BENEFICIARY_REFUSED: 0, BENEFICIARY_REFERRED: 0 }`
  * `SMC1.NO` → `{ TO_ADMINISTER: 0, BENEFICIARY_REFUSED: 2, BENEFICIARY_REFERRED: 0 }`

#### Precedence Questions

* **Precedence attributes** are marked to determine tie-breaker flows.
* If multiple flows have the same score, the precedence attribute's answer determines which flow takes priority.

#### Flow Types

* Typical flows include:
  * `TO_ADMINISTER`
  * `BENEFICIARY_REFUSED`
  * `BENEFICIARY_REFERRED`
* Additional flows can be configured as needed.

***

## Deployment

* Define all checklist attributes and codes in your master configuration (MDMS or equivalent).
* Map each attribute's possible responses to flow points in the configuration.
* Mark precedence attributes and define their precedence logic.
* Deploy the configuration to the application environment (dev, staging, prod).
* Validate scoring and flow assignment logic through checklist UI/API.

***

## API

* **Checklist Retrieval API:**
  * Returns checklist structure, attributes, codes, and points mapping for rendering and validation.
* **Checklist Submission API:**
  * Accepts user responses; applies points mapping and precedence logic on the backend.
* **Flow Assignment Output:**
  * When a checklist is submitted, the API returns the assigned flow based on the configuration and user responses.

***

## Configuration

#### Sample Attribute and Points Mapping Configuration

```json
"ServiceDefinition": {
        "tenantId": "mz",
        "code": "SMC Campaign.ELIGIBILITY.DISTRIBUTOR",
        "isActive": true,
        "additionalFields": {
            "schema": "ServiceDefinition",
            "version": 1,
            "fields": [
                {
                    "key": "precedenceFlow",
                    "value": "SMC1.YES.SM1"
                },
                {
                    "key": "flow",
                    "value": [
                        {
                            "type": "TO_ADMINISTER",
                            "minScore": 5
                        },
                        {
                            "type": "BENEFICIARY_REFUSED",
                            "minScore": 3
                        },
                        {
                            "type": "BENEFICIARY_REFERRED",
                            "minScore": 7
                        }
                    ]
                }
            ]
        },
        "attributes": [
            {
                "tenantId": "mz",
                "code": "SMC1",
                "dataType": "SingleValueList",
                "values": [
                    "YES",
                    "NO",
                    "NOT_SELECTED"
                ],
                "isActive": true,
                "required": true,
                "order": 1,
                "additionalFields": {
                    "schema": "ServiceAttribute",
                    "version": 1,
                    "fields": [
                        {
                            "key": "pointsMapping",
                            "value": {
                                "YES": {
                                    "TO_ADMINISTER": 0,
                                    "BENEFICIARY_REFUSED": 0,
                                    "BENEFICIARY_REFERRED": 10
                                },
                                "NO": {
                                    "TO_ADMINISTER": 2,
                                    "BENEFICIARY_REFUSED": 0,
                                    "BENEFICIARY_REFERRED": 0
                                }
                            }
                        },
                        {
                            "key": "helpText",
                            "value": "SMC1.HELP"
                        }
                    ]
                }
            },
            {
                "tenantId": "mz",
                "code": "SMC1.YES.SM1",
                "dataType": "SingleValueList",
                "values": [
                    "YES",
                    "NO",
                    "NOT_SELECTED"
                ],
                "isActive": true,
                "required": true,
                "order": 2,
                "additionalFields": {
                    "schema": "ServiceAttribute",
                    "version": 1,
                    "fields": [
                        {
                            "key": "pointsMapping",
                            "value": {
                                "YES": {
                                    "TO_ADMINISTER": 0,
                                    "BENEFICIARY_REFUSED": 0,
                                    "BENEFICIARY_REFERRED": 10
                                },
                                "NO": {
                                    "TO_ADMINISTER": 2,
                                    "BENEFICIARY_REFUSED": 0,
                                    "BENEFICIARY_REFERRED": 0
                                }
                            }
                        },
                        {
                            "key": "helpText",
                            "value": "SMC1.YES.HELP"
                        }
                    ]
                }
            },
            {
                "tenantId": "mz",
                "code": "SMC2",
                "dataType": "SingleValueList",
                "values": [
                    "YES",
                    "NO",
                    "NOT_SELECTED"
                ],
                "isActive": true,
                "required": true,
                "order": 3,
                "additionalFields": {
                    "schema": "ServiceAttribute",
                    "version": 1,
                    "fields": [
                        {
                            "key": "pointsMapping",
                            "value": {
                                "YES": {
                                    "TO_ADMINISTER": 0,
                                    "BENEFICIARY_REFUSED": 0,
                                    "BENEFICIARY_REFERRED": 10
                                },
                                "NO": {
                                    "TO_ADMINISTER": 2,
                                    "BENEFICIARY_REFUSED": 0,
                                    "BENEFICIARY_REFERRED": 0
                                }
                            }
                        },
                        {
                            "key": "helpText",
                            "value": "SMC2.HELP"
                        }
                    ]
                }
            },
            {
                "tenantId": "mz",
                "code": "SMC3",
                "dataType": "SingleValueList",
                "values": [
                    "YES",
                    "NO",
                    "NOT_SELECTED"
                ],
                "isActive": true,
                "required": true,
                "order": 4,
                "additionalFields": {
                    "schema": "ServiceAttribute",
                    "version": 1,
                    "fields": [
                        {
                            "key": "pointsMapping",
                            "value": {
                                "YES": {
                                    "TO_ADMINISTER": 0,
                                    "BENEFICIARY_REFUSED": 0,
                                    "BENEFICIARY_REFERRED": 10
                                },
                                "NO": {
                                    "TO_ADMINISTER": 8,
                                    "BENEFICIARY_REFUSED": 0,
                                    "BENEFICIARY_REFERRED": 0
                                }
                            }
                        },
                        {
                            "key": "helpText",
                            "value": "SMC3.HELP"
                        }
                    ]
                }
            }
        ]
    }
```

***

## Checklist Processing Sequence

#### Step-by-Step Example

1. **Processing Inputs**
   * For each attribute:
     * Retrieve user input.
     * Generate a unique key (e.g., `SMC1_YES`) to avoid duplicates.
     * Skip if already processed.
2. **Update Scores**
   * For each response:
     * Retrieve mapped points.
     * Increment score for each flow type accordingly.
3. **Handle Precedence**
   * If the attribute is a precedence attribute and input is provided:
     * Record the answer for the precedence flow assignment.
4. **Final Flow Assignment**
   * Calculate total scores for all flows.
   * If a tie exists:
     * Use the precedence answer to assign the flow.
     * If not, pick the flow with the highest score.
   * If no tie, assign the flow with the highest score.

***

{% hint style="info" %}
**Note:**\
All checklist logic, points mapping, and precedence flows should be thoroughly tested after configuration updates to ensure accurate flow assignment.
{% endhint %}
