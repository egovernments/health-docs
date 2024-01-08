# Referral Management

## Table of Contents

Background

Target Audience

Objectives

Assumptions and Validations

Process flow

Specifications

Design

## Background

This document describes the need and scope of adding a referral management module  within V2.0, explaining the module’s features, specifications, purpose, and functionality. It also provides a descriptive view of the application along with the specification of each element.

In health campaigns, it is very common that beneficiaries show some symptoms against the dose administered, such as fever, body ache, etc., which are not alarming. But in cases where the dose has an adverse effects on the beneficiary and he/she requires medical assistance, the beneficiary is referred to a healthcare facility for treatment. This module helps to track the referral details for a beneficiary and ensure the authenticity of genuine referrals done within the campaign.

## Target Audience

This document is intended for the engineering and platform (tech teams), product management and implementation teams to agree on the requirements for the Health Campaign Management Platform (HCM).

## Objectives

1. Referral Management:&#x20;

&#x20;      \- Enable actors to collect referral details of beneficiaries before as well as after administering the dose.

&#x20;     \- Capture details of the referred facility, referring individual, and reasons for referral.

2. Enhance user experience:

&#x20;      \- Simplified forms for capturing referral information.

&#x20;      \- Ensure authenticity of data:

&#x20;      \- Referral details to track the beneficiary and avoid fraudulent referrals by verifying the collected data.

## Assumptions and Validations

| Sr. No. | Theme             | Assumption                                                                                                                                                                                                                                                                                                                      |
| ------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | Refer beneficiary | <ol><li>The beneficiaries may be referred before or after administering the dose.</li><li>The actors must refer the beneficiary to a healthcare facility and collect the data on the same date.</li><li>The reasons for referral can be multiple and the user can elaborate the details within the referral comments.</li></ol> |

## Process flow

![](https://lh5.googleusercontent.com/3aIsfLUg1n-v5kNmcVxDqX4\_d9vJv62GKo7WWslisD5RfARGtL2D6pwEab0aAMZbSPzLo3QWYRv2bpaXD3sxOtCNkxW442mjH7lhbDUa8R7ncnLuSwPixSexnud09\_hhbcz0pYMZde22s0AZA9YGr7g)

## Specifications

| Field                        | Data type             | Data validation                                                                                           | Required (Y/N) | Comments                                                  |
| ---------------------------- | --------------------- | --------------------------------------------------------------------------------------------------------- | -------------- | --------------------------------------------------------- |
| Refer beneficiary            | Button                | The user must refer a beneficiary if they require medical support.                                        | NA             | <p><br></p>                                               |
| Date of referral             | Date                  | The date is populated by the system and must be non-editable.                                             | Y              | <p><br></p>                                               |
| Administrative unit          | String                | The unit is populated by the system and must be non-editable.                                             | Y              | The user can change the boundary from the boundary picker |
| Referred by                  | Search-based dropdown | The system must populate the team code from the user’s profile and it must be editable.                   | Y              | <p><br></p>                                               |
| Referred to                  | Search-based dropdown | The system auto-populates the resource which is editable.                                                 | Y              | <p><br></p>                                               |
| Reason for referral          | Multi-checklist       | The system auto-populates the quantity which is editable.                                                 | Y              | <p><br></p>                                               |
| Referral comments            | String                | Additional details for referral.                                                                          | N              | <p><br></p>                                               |
| Was the delivery successful? | Binary (Yes/No)       | <p><br></p>                                                                                               | Y              | <p><br></p>                                               |
| Reason for not delivering    | Dropdown              | The field must be dynamic and appear when the user selects ‘No’. The list must be configured in the MDMS. | Y              | <p><br></p>                                               |

## Design

Find the mock-ups below:

### Refer Beneficiary (Household Card)

When the user clicks on the ‘Open’ button on the beneficiary card or scans a voucher on the search household screen, the household card is opened, which contains the household details.

Based on campaign type, the deliver intervention button is displayed either on each individual’s card or the entire household. For individual-based campaigns, the button appears only on the individual’s card that was searched or scanned.&#x20;

The user must click on the “Refer Beneficiary” button in case the beneficiary is suffering from any illness and needs medical treatment before delivering the intervention.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 10.48.43 AM.png" alt=""><figcaption></figcaption></figure>

### Refer Beneficiary (Adverse Events)

After administering the dose, if the user observes any [adverse events](adverse-events-workflow.md), he/she captures the details on this screen and clicks on the “Refer Beneficiary” button which navigates the user to referral management flow.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 10.50.28 AM.png" alt=""><figcaption></figcaption></figure>

### Referral Details

After clicking on “Refer Beneficiary”, the referral details screen appears where the user provides information for referral.

The date and administrative unit fields are auto-populated by the system and are non-editable.&#x20;

The referred by field automatically captures the team code from the user’s profile but can be edited. The user must select a facility where the beneficiary is being referred to.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 10.52.50 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 10.53.22 AM.png" alt=""><figcaption></figcaption></figure>

## Search Facilities

When the user clicks on the search icon in the “Referred to” field, a pop-up screen appears, which contains the list of all the health facilities within the campaign. The user can search for any facility by typing within the search box, and it will display the related search results.

When the user selects any facility, the screen collapses and the value is displayed within the field. The user must click again on the search icon if he/she wants to change the facility.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 10.55.55 AM.png" alt=""><figcaption></figcaption></figure>

### Reason For Referral

Users must select the reason for referring the beneficiary. Reasons are basically the adverse events observed in a beneficiary and the user can select multiple values from the list. Users can describe the beneficiary's health condition in the referral comments field.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 10.59.08 AM.png" alt=""><figcaption></figcaption></figure>

### Was the delivery successful

The user must provide the details for whether the delivery was successful or not.

If the user selects ‘No’, an additional field must appear asking for the reason of non-delivery. The dropdown must have the reasons that are configured in the MDMS.

After selecting the response, the user must click on the ‘Submit’ button, which opens the acknowledgement screen stating that the delivery is successful, and the user can go back to the search household screen.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 11.05.51 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 11.06.38 AM.png" alt=""><figcaption></figcaption></figure>
