---
description: Multi-round delivery of resources
---

# Multi-Round Service Delivery

## Table of Contents

Background

Target Audience

Objectives (of this release)

Assumptions and Validations

Process flow

Specifications

Design

## Background

This document describes the need and scope of adding multi-round delivery capability  within V2.0, explaining the module’s features, specifications, purpose, and functionality. It also provides a descriptive view of the application along with the specification of each element.

For certain campaigns, especially at the individual levels, the doses are administered in multiple rounds which are referred to as ‘cycles’. Each cycle has multiple doses within them. In such campaigns, the doses are administered by following either of the two strategies: DOT 1 and DOT n, where DOT means Direct Observation of Treatment. In DOT 1 strategy, the distributor provides the first dose of the first cycle, and the remaining doses are given to the caretaker/mother to be given accordingly. The process is repeated for the next cycles. In DOT n, the distributor himself/herself provides each dose to the beneficiary. Thus, the application must be capable of capturing data for multi-round campaigns.

## Target Audience

This document is intended for the engineering and platform (tech teams), product management, and implementation teams to agree on requirements for the Health Campaign Management (HCM) Platform.

## Objectives

1. Support multi-round delivery:&#x20;

&#x20;      \- Enable actors to capture delivery details for multi round campaigns.

&#x20;      \- Able to capture details for both types of DOT strategies.

2. Enhance user experience:

&#x20;      \- Auto-populate the number of cycles and doses being administered to the beneficiary for the user’s convenience.

&#x20;      \- Provide the auto-calculated resource and quantity to be administered for each dose.

&#x20;      \- Enable actors to deliver multiple resources based on the campaign.

3. Record past delivery:

&#x20;      \- Enable actors to record past delivery details (for DOT 1-based campaigns).

## Assumptions and Validations

<table data-header-hidden><thead><tr><th width="78"></th><th width="132"></th><th></th></tr></thead><tbody><tr><td>Sr. No.</td><td>Theme </td><td>Assumption</td></tr><tr><td>1</td><td>Deliver intervention</td><td><ol><li>The actors collect the data for multi-round campaigns for each cycle and each dose within the cycle.</li><li>There must be a time interval, restricting the user to record the delivery data for next dose/cycle and it must be configurable.</li><li>The user cannot change the dose and cycle to avoid collection of incorrect data.</li></ol></td></tr><tr><td>2</td><td>Resource delivered</td><td><ol><li>Auto-populate the resource and the quantity from the calculated values.</li><li>The fields are editable if the user wants to change the resource or quantity.</li></ol></td></tr><tr><td>3</td><td>Beneficiary details</td><td><ol><li>Provide the history for delivery details on the beneficiary details screen to track the resource delivery.</li></ol></td></tr></tbody></table>

## Process Flow

![](https://lh3.googleusercontent.com/DvKafC3Py6cIPoeOZKDybJuQahgBPqhlRHU6pdOCC1zDtijDfhQBRXqS-ksvtMRTW2lT5KZQCCeqGUacbIXcRU8funWtL6FKw-gZFM1lOntTrromZZPzmzoWS1dB0Lr6iQme088ESBXTBWa2smSIsOA)

## Specifications

| Field                                                | Data type           | Data validation                                                                                            | Required (Y/N) | Comments    |
| ---------------------------------------------------- | ------------------- | ---------------------------------------------------------------------------------------------------------- | -------------- | ----------- |
| Height                                               | Integer             | <p>Height of the beneficiary:</p><p>Should not exceed 3 digits.</p>                                        | Y              | <p><br></p> |
| Weight                                               | Integer             | <p>Weight of the beneficiary:</p><p>Should not exceed 3 digits.</p>                                        | Y              | <p><br></p> |
| Is the beneficiary sick?                             | Binary (Yes/No)     | <p><br></p>                                                                                                | Y              | <p><br></p> |
| Sickness description                                 | String              | Must appear if a user selects ‘Yes’.                                                                       | Y              | <p><br></p> |
| Is the beneficiary undergoing any form of treatment? | Binary (Yes/No)     | <p><br></p>                                                                                                | Y              | <p><br></p> |
| Treatment description                                | String              | Must appear if a user selects ‘Yes’.                                                                       | Y              | <p><br></p> |
| Does the beneficiary have any co-morbidities?        | Binary (Yes/No)     | <p><br></p>                                                                                                | Y              | <p><br></p> |
| Co-morbidities                                       | Dropdown            | Must appear if a user selects ‘Yes’. A user must be able to select multiple values from the dropdown list. | Y              | <p><br></p> |
| Was the dose administered                            | Binary (Yes/No)     | A user must select whether the dose was administered or not.                                               | Y              | <p><br></p> |
| Date of administration                               | Date                | The date must be non-editable for recording current delivery and editable for past delivery records.       | Y              | <p><br></p> |
| Dose administered by                                 | Dropdown            | A user must select from the list the person who administered the dose.                                     | Y              | <p><br></p> |
| Resource to be administered                          | Read-only           | This is calculated by the system based on the configurations.                                              | NA             | <p><br></p> |
| Resource delivered                                   | Dropdown            | The system auto-populates the resource which is editable.                                                  | Y              | <p><br></p> |
| Quantity administered                                | Increment/decrement | The system auto-populates the quantity which is editable.                                                  | Y              | <p><br></p> |
| Was the delivery successful?                         | Binary (Yes/No)     | <p><br></p>                                                                                                | Y              | <p><br></p> |
| Reason for not delivering                            | Dropdown            | The field must be dynamic and appear when the user selects ‘No’. The list must be configured in the MDMS.  | Y              | <p><br></p> |

## Design

Find the mock-ups below:

### Household Card

When the user clicks the ‘Open’ button on the beneficiary card in the search household screen or scans a voucher, the household card is opened, which contains the household details.&#x20;

Based on the campaign type, the “Deliver Intervention” button is displayed either on each individual’s card or the entire household. For individual based campaigns, the button appears only on the individual’s card that was searched or scanned.



<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-25 at 9.43.11 AM.png" alt=""><figcaption></figcaption></figure>

### Beneficiary Details

Clicking on the “Deliver Intervention” button opens this screen which has the beneficiary data as well as delivery data if he/she has received any intervention earlier. The user can record past delivery data (if DOT 1 strategy is followed) or simply click on the ‘Next’ button to record current delivery details.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-25 at 9.54.52 AM.png" alt=""><figcaption></figcaption></figure>

### Health Information (PHI Details)

For certain campaigns, the resources delivered are calculated based on the beneficiary’s height, weight, age, or other parameters. This screen captures details of the beneficiary along with a checklist that has health-related questionnaires: Whether the beneficiary is sick and undergoing any treatment, or if he/she is suffering from disease(s).

The form must be configurable to support multiple question types and add questions, if needed. For questions that require specific details, a text field appears when the user selects ‘Yes’. The dropdown list for comorbidities must allow multiple selection.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-25 at 10.03.16 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-25 at 10.06.37 AM.png" alt=""><figcaption></figcaption></figure>

### Deliver Intervention

The user needs to provide the delivery details for the resources delivered to the beneficiary. The screen is configurable depending on the campaign type, and the auto-calculated resources and quantity are displayed and populated in the fields. \`The user can edit the fields if he/she needs to change the resource administered.

The “Date of Administration” is non-editable if the user records current delivery details. For past delivery data, the field must be editable with a restriction on the earliest date that can be captured (cannot select the date less than that of previous dose, and if additional time interval is added).\


<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-25 at 11.03.46 AM.png" alt=""><figcaption></figcaption></figure>

### Scan QR Code

Click [here](2d-voucher-scanning.md) to know more.&#x20;

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-25 at 11.12.17 AM.png" alt=""><figcaption></figcaption></figure>

### Adverse Events

When a user clicks on the ‘Next’ button on the “Deliver Intervention” screen, a pop-up appears to check if the user observed any adverse events in the beneficiary. Click [here](adverse-events-workflow.md) to know more.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-25 at 11.22.13 AM.png" alt=""><figcaption></figcaption></figure>

### Was the delivery successful?

The user must provide the details for whether the delivery was successful or not. If the user selects ‘No’, an additional field must appear asking for the reason of non-delivery.

The dropdown must have the reasons that are configured in the MDMS. After selecting the response, the user must click on the ‘Submit’ button, which opens the acknowledgement screen stating that the delivery was successful. The user can go back to the search household screen or record the next dose, if required.\


<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-25 at 11.26.41 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-25 at 11.26.52 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-25 at 11.27.02 AM.png" alt=""><figcaption></figcaption></figure>
