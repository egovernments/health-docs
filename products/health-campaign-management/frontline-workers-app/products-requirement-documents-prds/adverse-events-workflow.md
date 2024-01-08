# Adverse Events Workflow

## Table of Contents

[Background](adverse-events-workflow.md#background)

[Target Audience](adverse-events-workflow.md#target-audience)

[Objectives (of this release)](adverse-events-workflow.md#objectives)

[Assumptions and Validations](adverse-events-workflow.md#assumptions-and-validations)

[Process flow](adverse-events-workflow.md#process-flow)

[Specifications](adverse-events-workflow.md#specifications)

[Design](adverse-events-workflow.md#design)

## Background

This document describes the need and scope of adding forms to track adverse events after a dose is administered to a beneficiary within V2.0, explaining the module’s features, specifications, purpose, and functionality. It also provides the descriptive view of the application along with the specification of each element.

While administering the dose to a beneficiary (usually children), there can be instances when the beneficiary shows some symptoms against the dose provided. These adverse events need to be recorded and monitored as it helps to take precautionary measures for further doses as well as in future campaigns for that beneficiary. It is helpful for cases when a beneficiary's situation becomes critical and he/she needs to be referred to a healthcare facility. This is also crucial for resource tracking because in certain campaigns, the beneficiary can be re-administered the dose even after he vomits out the medicine. &#x20;

## Target Audience

This document is intended for the engineering and platform (tech teams), product management, and implementation teams to agree on requirements for the Health Campaign Management (HCM) Platform.

## Objectives (of this release)

1. Recording adverse events.&#x20;
2. Enabling actors to record and track the adverse events observed in a beneficiary after administration of the dose.
3. Monitoring the data to plan and decide for upcoming doses during the campaign.

## Assumptions and Validations

| Sr. No. | Theme                           | Assumption                                                    |
| ------- | ------------------------------- | ------------------------------------------------------------- |
| 1       | Triggering adverse events flow. | Adverse events will always be linked to the service delivery. |

## Process flow

![](https://lh6.googleusercontent.com/Z-qjw\_gzr9DmlVllaj0uVrFlbEVm7lw4RXcjAzzbQqKH0mF88zUPcvnHXRuGUhr0OFbL7LJK-ZNzAc4xAVEV2B90BOcHexofTAxupAuPiQZIG0jzvDvryNd3EHb9rlnUUvxAU-zf4mTzFdwuTGU13Iw)

## Specifications

| Field                            | Data type            | Data validation                                                                                | Required (Y/N) | Comments    |
| -------------------------------- | -------------------- | ---------------------------------------------------------------------------------------------- | -------------- | ----------- |
| Resource administered            | Table (Read-only)    | This displays the data for resources administered to the beneficiary.                          | NA             | <p><br></p> |
| Select the symptoms              | Multiple select list | The user must be able to select multiple values from the list.  The list must be configurable. | Y              | <p><br></p> |
| Did you re-administer            | Binary (yes/no)      | <p><br></p>                                                                                    | Y              | <p><br></p> |
| Number of times re-administered  | Increment/decrement  | If user selects yes for re-administer, then this field must be displayed                       | Y              | <p><br></p> |

## Design

Find the mock-ups below:

### Deliver Intervention

The user needs to provide the delivery details for the resources delivered to the beneficiary. The screen is configurable depending upon the campaign type and the auto-calculated resources and quantity are displayed and populated in the fields. The user can edit the fields if required to change the resource administered.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 11.35.30 AM.png" alt=""><figcaption></figcaption></figure>

### Adverse Events

When the user clicks ‘Next’ on the deliver intervention screen, it opens a pop-up that asks: “Did you observe any adverse events?” If the user selects ‘No’, the adverse events screen is skipped, and he/she is directly navigated to the next screen in the flow. If the user selects ‘Yes’, it opens the adverse events form to capture the details. On top the summary of delivered resources is displayed in a tabular form. The list of symptoms must be configurable to include more values if required. It is possible that the beneficiary shows multiple symptoms, thus the user must be able to select multiple values from the list.

If the dose is readministered, then the user must select ‘yes’ and provide the number of times it has been readministered.&#x20;

The “Refer Beneficiary” button navigates the user to the refer beneficiary flow, in case the beneficiary is critical and requires medical assistance. The ‘Next’ button takes the user to the next screen in the flow.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 11.29.51 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 11.30.02 AM.png" alt=""><figcaption></figcaption></figure>
