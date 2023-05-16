# UAT Plan

## Objective

The purpose of this document is to outline the User Acceptance Testing (UAT) process for the DIGIT-HCM platform rollout in Mozambique as part of the Group IV distribution in the Tete province. This will enable the NMCP users to validate that the HCM software meets the agreed upon acceptance criteria for various functionalities.

It will ensure that the system satisfies the needs of the business as specified in the functional requirements(PRD) and provides confidence in its use. It will also help to identify defects with associated risks and suggest enhancements(change requests), communicate all known defects/enhancements to the project team, and ensure that all issues are addressed in an appropriate manner prior to go-live.

## UAT Methodology

During the testing process, a pre-approved list of test cases/scripts will be executed to verify the behaviour and performance of various functionalities. The observations from the testing will be noted and classified as defects or enhancements. Some of the enhancements may be doable using configuration changes while others( Change Requests) may have to go through a change management process. The UAT presentation deck was utilised for this purpose: [https://docs.google.com/presentation/d/1Z3KKXuEy41vw9YtJWrjqYDfjil89F6kIiCC\_2DLnorY/edit#slide=id.g238f467a117\_0\_0](https://docs.google.com/presentation/d/1Z3KKXuEy41vw9YtJWrjqYDfjil89F6kIiCC\_2DLnorY/edit#slide=id.g238f467a117\_0\_0)

UAT observation classification:

| # | Observation Type     | Description                                                                                                                                         | Addressing Mechanism                                                                                                                                                                                                                                                                                            |
| - | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Defects              | Any observation pertaining to a feature or functionality not working as expected or agreed at the time of scope review, will be classified as issue | The observations classified as defects will be taken up by the eGov program team for further validation, prioritisation and fixing. Minor issues originating due to incorrect configurations or erroneous labels, or translations will be fixed and be made available for re-testing during the next UAT cycle. |
| 2 | Change Requests (CR) | Any recommendations to enable or disable a functionality from the initial requirements or a new functionality to be added                           | These will be handled via Change control Process as per the SoP defined and will be evaluated based on their impact and effort.                                                                                                                                                                                 |

\
The UAT team will execute all the test scripts referenced in section 6.0.  Users may also perform additional tests not detailed in the plan but remain relevant and within the scope of the project. &#x20;

Users will report feedback to the eGov team for documentation and escalation using a google sheet. These defects will be described, prioritised, and tracked by using screen captures, verbiage, and steps necessary for the development team to reproduce the defect. For change requests the requirements will be described, analysed, prioritised and tracked.  Information on defect  and CR processing can be found in section 7.0.

## Test Phases

The various phases of UAT are shown in the below diagram:

<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-16 at 12.01.09 PM.png" alt=""><figcaption></figcaption></figure>

### Scope for UAT

UAT will be conducted in 2 phases with the below mentioned scope

| Test Phases | Tracks                                   | Scope                                                                                             |
| ----------- | ---------------------------------------- | ------------------------------------------------------------------------------------------------- |
| UAT 1       | HCM Mobile App                           | Registration and Service Delivery, Supervision, Inventory, raising complaints from the mobile app |
| UAT 2       | Retest Issues/ Observations from UAT 1.  | Retesting observations and accepted CRs/bug fixes and sign-off                                    |

* Validate end-to-end business flow for each of the identified user flows&#x20;
* All the required fields are present
* System is accepting only valid values
* User can save after form filling all the mandatory fields
* Correctness of label and its translations&#x20;

### Out of scope of UAT

For the below mentioned functionalities, separate demo and/or training sessions will be conducted for the targeted user groups.

&#x20;1\. Helpdesk for complaints and user management

&#x20;   a. User Management module to add/update/ activate/deactivate users and role mapping

&#x20;   b. Handling complaints via inbox functionality

2. Central, Provincial, District dashboards and reports.

During UAT , the team will validate the end-to-end flow and features of the application to validate:&#x20;

* Validate end-to-end business flow for each of the identified user flows&#x20;
* All the required fields are present
* System is accepting only valid values
* User can save after form filling all the mandatory fields
* Correctness of label and its translations&#x20;

### Prerequisites for UAT

Following is the list of prerequisites for conducting the UAT:

* The HCM Mobile App for UAT deployed in the UAT environment
* Mobile phones setup with HCM app.&#x20;
* Configuration of HCM Mobile App in UAT environment with master data from Zambezia
* Readiness of handouts

&#x20;     \- Test Case document

&#x20;     \- Mockups&#x20;

&#x20;     \- Defect/Change request reporting template

* Availability of teams from NMCP, DIS and DTIC for UA testing
* Nomination of participants for the UAT session so that test accounts can be created by eGov.
* Configuration of ticket tracking tool for UAT (JIRA)

### UAT Environment

The UAT environment will be similar to the production environment in terms of specifications,  and will be provided by eGov, so that accurate assumptions can be drawn regarding the application’s performance. Applicable IP addresses and URLs will be provided by eGov team to the UAT Team and all the mobiles will be configured for access to the test environment.

### UAT Process

Each test participant will be provided with a checklist to verify access to the applications within the defined scope of testing.  The tester will then login, perform the prescribed steps and generate the expected results for each activity.  Any feature identified as missing or bug during testing from the UAT environment should be reported back to eGov.

### UAT Data

Access to test data is a vital component in conducting a comprehensive test of the system.  All UAT participants will require usage of test accounts and other pertinent test data which should be provided by NMCP upon request.  All user roles should fully emulate production in the UAT path. The test accounts and role mapping shall be done for the users identified by eGov. Following are sample test data for UA testing:

* Sample Master Data

&#x20;      \- Users data for test login creation

&#x20;      \- Location master (AP/Locality/Village )

&#x20;      \- Inventory module master (warehouse+product)

### UAT Team

The test team is composed of members who possess a knowledge of the operations and processes on the ground. &#x20;

1. These team members will be able to initiate test input, review the results,&#x20;
2. Have prior experience/learnings from campaign digitisation in Mozambique&#x20;

All team members will be presented by the eGov team with an overview of the test process and what their specific role in UAT will be.  The eGov team will oversee testing by assigning scripts to testers, providing general support, and serving as the primary UAT contact point throughout the test cycle.

### UAT Deliverables&#x20;

The following sections detail milestones crucial to the completion of the UAT phase of the project. Once all dependent milestones have been completed, NMCP/DIS/DTIC will formally sign-off on the system’s functionality and distribute an email to all project stakeholders.

### UAT Activities and Schedule&#x20;

All core UAT activities along with the deliverable dates are described in the below table:

| Task                                                                                                                                                                                                                                        | Owner                        | Start Date  | Expected Closure date |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------- | ----------- | --------------------- |
| UAT-1                                                                                                                                                                                                                                       |                              |             |                       |
| Creation of the UAT-1 test plan and sharing with NMCP for review                                                                                                                                                                            | eGov                         | 12-Apr-23   | 17-Apr-23             |
| Creation of the UAT test cases/scripts and sharing with NMCP for review                                                                                                                                                                     | eGov                         | 13-Apr-23   | 19-Apr-23             |
| Nomination of UAT participants so that user accounts can be created                                                                                                                                                                         | NMCP/DIS/DTIC                | 19-Apr-23   | 21-Apr-23             |
| Arrangement of venue and other logistics for UAT session                                                                                                                                                                                    | NMCP/DIS/DTIC                | 24-Apr-23   | 25-Apr-23             |
| Readiness of the UAT server instance                                                                                                                                                                                                        | eGov                         | 13-Apr-23   | 21-Apr-23             |
| Installing test version of the HCM application in test phones                                                                                                                                                                               | CHAI                         | 24-Apr-23   | 25-Apr-23             |
| Conducting the UAT testing along with NMCP stakeholders                                                                                                                                                                                     | eGov, NMCP, DIS , DTIC, CHAI | 27-Apr-23   | 28-Apr-23             |
| Collation and triaging of UAT feedback and communication to NMCP regarding what can be incorporated in the HCM app                                                                                                                          | eGov                         | 2-May-23    | 4-May-23              |
| Reviewing the test results results and providing provisional sign off on first round of UAT                                                                                                                                                 | NMCP/DIS/DTIC                | 2-May-23    | 8-May-23              |
| UAT-2                                                                                                                                                                                                                                       |                              |             |                       |
| Incorporating the UAT-1 feedback in the HCM application based on the results of triaging process                                                                                                                                            | eGov                         | 8-May-23    | 30-May-23             |
| Creation of the UAT test cases/scripts and sharing with NMCP for review                                                                                                                                                                     | eGov                         | 31-May-23   | 2-June-23             |
| Nomination of UAT participants so that user accounts can be created                                                                                                                                                                         | NMCP/DIS/DTIC                | 5-June-23   | 7-June-23             |
| Arrangement of venue and other logistics for UAT session                                                                                                                                                                                    | NMCP                         | 5-June-23   | 7-June-23             |
| Readiness of the UAT server instance                                                                                                                                                                                                        | eGov                         | 5-June-23   | 7-June-23             |
| Installing test version of the HCM application in test phones                                                                                                                                                                               | CHAI                         | 8-June-23   | 9-June-23             |
| Conducting the second round of UAT testing along with NMCP stakeholders                                                                                                                                                                     | eGov, NMCP, DIS , DTIC, CHAI | 12-Jun-23   | 13-Jun-23             |
| Collation and triaging of UAT feedback and communication to NMCP                                                                                                                                                                            | eGov                         | 14-June-23  | 16-June-23            |
| Incorporating any minor suggestions arising out of second round of UAT                                                                                                                                                                      | eGov                         | 14-June-23  | 20-June-23            |
| <p>Reviewing the test results and providing final sign-off* in the second round of UAT .</p><p>Final sign-off : This would indicate that application is fit to be used during the Group4 distribution and no more changes are required.</p> | eGov                         | <p><br></p> | 21-June-23            |

### UAT Sign-off&#x20;

* The mutually agreed defects/CR from UAT 1 will be re-tested in UAT 2.&#x20;
* The sign-off shall be provided at the end of UAT 2 by NMCP via an email communication or official orders/memo to the eGov.
* Post sign-off the application will be ready for the deployment in the production environment.

## UA Test  Cases

Test cases provide a high-level description of the functionality to be tested.  All regression and new functionality test cases are contained in the Excel spreadsheet “UA Test Cases” available at: \[insert hyperlink to UAT folder in Project Directory here]. &#x20;

The team will leverage relevant QA test cases for project specific functionality.  Each test case based on new functionality will reference a specific functional requirement.

Each script contains: test case number, test description, requirement number, action to be performed, test data to be utilized, expected results, error descriptions (if applicable), pass/fail results, date tested, and any additional comments from the UA tester.

The UA test scripts are contained within the UAT test case spreadsheet and can be accessed via hyperlink from each individual test case.

## UAT Feedback&#x20;

Defects and Change Requests will be entered and tracked in JIRA by the eGov team during the UAT process.  Each entry will include detailed information about each defect/CR.

### UAT Defect/CR Tracking

Test team will be provided with instruction on how to effectively execute test scripts, as well identify, capture, and report defects/observations by the eGov team at the beginning of the UAT session. Test team will present their findings during the UAT session.&#x20;

### UAT Defect Life Cycle&#x20;

Defects must be clearly captured and escalated to ensure prompt resolution by development.  Each defect submitted by UAT will be assigned a priority, worked by development, resolved, and re-tested by UAT prior to closure.  The following is a snapshot of the standard defect lifecycle:

<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-16 at 12.21.14 PM.png" alt=""><figcaption></figcaption></figure>

### Prioritisation

eGov and NMCP together will prioritise and classify defects.  Defects found in UAT can be assigned one of three (3) levels of severity:

* P1, Work Halted – Testing defects that due to the complexity of the function or the scheduled dates are putting the implementation date at risk.  No workaround exists.
* P2, Work Slowed – Testing defects occurring in a less complex function of the application with sufficient time to resolve before the implementation date – but must be implemented as scheduled.  A workaround has been identified and is listed in the defect.
* P3 and lower, Work Unaffected – Testing defects occurring in a function that are simple to fix or could be excluded if not resolved by the scheduled implementation date.

Response (acknowledgement of the issue) Commitments for Defects

| Severity                      | Description                                                                                                      | Response SLA |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------- | ------------ |
| P1, Work Halted               | Critical application outage impacting service for which the cause is unknown. No bypass or workaround available. | 4 hours      |
| P2, Work Slowed               | A key component of the application is degraded, unusable or unavailable, some users affected.                    | 1 day        |
| P3 and lower, Work Unaffected | A component of the application is degraded, which causes a minor inconvenience, but a workaround is available.   | 2 days       |

### UAT Change Request Life Cycle&#x20;

CR must be clearly captured and reported for analysis to identify effort and Impact to the eGov team. Each CR submitted will be validated and categorised for acceptance and then assigned with a priority. The development team will work on it and will be made available for testing. Following is a snapshot of the standard CR lifecycle:

<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-16 at 12.23.25 PM.png" alt=""><figcaption></figcaption></figure>

### Categorisation&#x20;

eGov in consultation with NMCP will decide acceptance and categorisation of change requests. Change requests found in UAT can be assigned one of three (3) levels of category:

* Must Have – Change requests that are needed for the success of a campaign. No workaround exists.
* Should Have – Change requests that are required for better tracking and monitoring and will increase the ease of use of the system for users. A workaround has been identified and is listed in the CR.
* Good to Have – Change requests that are simply for better visualisation and reporting. It could be excluded if not resolved by the scheduled implementation date.

eGov to endeavour to cover Must Have changes before distribution. Lower priority changes will be taken through the eGov Gating process for planning subsequent releases
