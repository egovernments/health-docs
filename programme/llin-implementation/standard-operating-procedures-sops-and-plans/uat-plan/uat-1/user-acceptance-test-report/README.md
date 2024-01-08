# User Acceptance Test Report

## Introduction

The purpose of the User Acceptance Test (UAT) is to verify that the system meets the business needs as defined in the functional requirements (product requirement document or PRD) and instills confidence in its usage. Additionally, the UAT helps to identify any defects with associated risks, suggest potential enhancements (via change requests), communicate any known defects or enhancements to the project team, and ensure that all issues are resolved before go-live in an appropriate manner.

## Scope

The UAT process included testing the following user flows:

* Registration & Delivery
* Inventory Management
* Supervision

The participants validated the end-to-end flow and features of the application to:

* Verify the end-to-end business flow for each of the identified user flows.
* Ensure that all required fields were present.
* Confirm that the system accepts only valid values.
* Test that the user could save after filling all mandatory fields in the form.
* Check the correctness of labels and their translations.

Separate demo and/or training sessions will be conducted for the following functionalities, as they were not included in the scope of UAT:

1. Helpdesk for complaints and user management

&#x20;      a. User management module for adding/updating/activating/deactivating users and role mapping.

&#x20;      b. Handling complaints via inbox functionality.

2. Central, provincial, and district dashboards, and reports

These targeted sessions will ensure that the relevant user groups are trained on the proper use and functionality of these features.

## Participants&#x20;

Ines Juleca, Catarina, Bernardo Espinosa, Aderito Joaquim Suaze, Marta Chande, Joao Dombo, Custodio Mondlane, Guidion Mathe, Luis Ismael, Gerito Augusto, Silva Pedro, Gercio Machva, Aurelio Carlos Marindze, Mariana da silva, Figuereido Mussambala, Carla Bambo, Sergio Tsabete.

The selection of participants for the UAT was decided by NMCP, and specifically targeted members of the "Nucelo Duro" group. A total of 17 participants took part in the UAT and were supported by a three-member team from eGov and CHAI.

Moderators: Abhishek Suresh, Mrunal Surve, Frank Cumaio

## Methodology

The UAT planning was comprehensively documented in the following documents.

* [User Acceptance Test Plan](../../)
* [UAT Plan Dates](plan-dates.md)

Before commencing testing, the participants were provided with a brief overview of the health mission and the benefits of DIGIT's platform approach. Each user flow was demonstrated to the participants by the moderator, and they were then tasked with executing each testing scenario under the three user flows.&#x20;

A pre-approved list of test cases/scripts was executed to verify the behavior and performance of various functionalities. All observations from each participant during testing were captured and compiled. These observations will be subsequently classified as either defects or enhancements based on internal discussions within eGov. While some of the enhancements may be implemented using configuration changes, others (change requests) may require going through a formal change management process.

| # | Observation type     | Description                                                                                                                                             | Addressing mechanism                                                                                                                                                                                                                                                                                           |
| - | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Defects              | Any observation pertaining to a feature or functionality not working as expected or agreed at the time of scope review, will be classified as an issue. | The observations classified as defects will be taken up by the eGov programme team for further validation, prioritisation and fixing. Minor issues originating due to incorrect configurations or erroneous labels, or translations will be fixed and made available for re-testing during the next UAT cycle. |
| 2 | Change requests (CR) | Any recommendation to enable or disable a functionality from the initial requirements or a new functionality to be added.                               | These will be handled via the change control process as per the SoP defined, and will be evaluated based on their impact and effort.                                                                                                                                                                           |

### Prioritisation framework for Defects

eGov and NMCP together will prioritise and classify defects.  Defects found in the UAT can be assigned one of three (3) levels of severity:

* P1, Work halted – Testing defects that due to the complexity of the function or the scheduled dates are putting the implementation date at risk. No workaround exists.
* P2, Work slowed – Testing defects occurring in a less complex function of the application with sufficient time to resolve before the implementation date – but must be implemented as scheduled. A workaround has been identified and is listed in the defect.
* P3 and lower, Work uUnaffected – Testing defects occurring in a function that are simple to fix or could be excluded if not resolved by the scheduled implementation date.

### Prioritisation Framework for Change Requests&#x20;

CRs will be clearly captured and reported for analysis to identify effort and impact to the eGov team. Each CR submitted will be validated and categorised for acceptance or rejection and then assigned with a priority. The development team will work on it and will be made available for testing. Following is a snapshot of the standard CR lifecycle.

### Categorisation of Change Requests

eGov, in consultation with NMCP, will decide acceptance and categorisation of change requests. Change requests found in UAT can be assigned one of three (3) levels of category:

* Must have – Change requests that are needed for the success of a campaign. No workaround exists.
* Should have – Change requests that are required for better tracking and monitoring and will increase the ease of use of the system for users. A workaround has been identified and is listed in the CR.
* Good to have – Change requests that are simply for better visualisation and reporting. It could be excluded if not resolved by the scheduled implementation date.

eGov to endeavour to cover "Must Have" changes before distribution. Lower priority changes will be taken through the eGov Gating process for planning subsequent releases.

## Feedback

The participants provided highly positive feedback, which was gathered through feedback forms accessed via QR codes presented during the session. To enable this, QR code scanners were installed on MISAU mobile devices using the scale fusion software. The feedback forms included:

* System Usability Scale (SUS) feedback form: This form aimed to measure the overall usability of the system as perceived by the participants.
* Overall UAT process feedback form: This form was designed to assess the effectiveness and efficiency of the UAT session, with the goal of incorporating feedback into future sessions.

## SUS Questionnaire Responses

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.17.06 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.17.42 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.18.08 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.18.30 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.19.09 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.21.17 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.23.04 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.24.03 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.24.26 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.24.49 PM.png" alt=""><figcaption></figcaption></figure>

### SUS Questionnaire Responses Interpretation

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.25.46 PM.png" alt=""><figcaption></figcaption></figure>

The average SUS score for all participants was 81.25, which exceeded the standard acceptable range:&#x20;

0-59:  Very Poor

60-69: Poor

70-79: OK

80-89: Good

90-100: Excellent

## UAT Process Feedback

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.29.26 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.29.33 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.30.22 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.30.33 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/Screenshot 2023-05-16 at 1.31.09 PM.png" alt=""><figcaption></figcaption></figure>

#### Open Suggestions

* “Show features like dashboards”
* “I think I would need to see the dashboard for decision making”
* “For me everything is fine“
* “Include transport management to better support planning“
* “Place visualisation panels and interoperability with other platforms“
* “Extend to the dashboard to be more complete“
* “Reports should appear in graphics for better monitoring“
* “We should have more time and not happen between campaigns“
* “Submit the application to practice before the start of the UAT“
* “The language issue makes interaction with the team a little difficult“
* “Must be included another forms suggested to be more a creaky“

## Recommendations

Moving forward, the following needs to be checked for UAT or any other event:

* Availability of a dedicated translator.
* All documents and presentations to be made available in Portuguese.
* A  terms of reference (TOR) to be shared before the event

## Way Forward

The eGov team will categorise the noted observations as either defects or change requests, and subsequently develop a plan to address them within an agreed-upon timeline. Following the resolution of identified bugs and change requests from UAT-1, which have been mutually agreed to by both eGov and NMCP, a second round of UAT is scheduled for June 2023.\
