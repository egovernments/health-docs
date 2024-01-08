# UAT Plan

## Objective

The purpose of this document is to outline the User Acceptance Testing (UAT) process for the DIGIT-HCM platform rollout in Mozambique as part of the seasonal malaria chemoprevention (SMC) campaign in the Nampula province. This will enable the SMC campaign users to validate that the HCM software meets the agreed upon acceptance criteria for various functionalities. It will ensure that the system satisfies the needs of the business as specified in the functional requirements and provides confidence in its use. It will also help to identify the defects with associated risks and suggest enhancements (change requests), communicate all known defects/enhancements to the project team, and ensure that all issues are addressed in an appropriate manner prior to go-live.

## &#x20;Expected Results&#x20;

At the end of the UAT, the following results are expected:&#x20;

* Sign-off of the application indicating that the app meet the requirements gathered.&#x20;
* Obtain feedback from the end users (Health Facility coordinators, Community Distributors and Community Distributor Supervisors).
* Verify if the application is able to do the functionality required to conclude the task of the Health Facility coordinators, Community Distributors and Community Distributor Supervisors (completeness functionality).
* Verify if the application is easy to use for the users (usability).
* Understand the areas that end-user may face challenges to improve the training curricula.

## Summary of the UAT&#x20;

| Participants         | <p>SPS (Provincial Health Service)<br>Health Facility coordinators ( 2 people)</p><p>Community Distributor Supervisors (2 people)<br>Community Distributors (3 people)</p><p>M&#x26;E  (2 people)</p><p>NMCP - National Malaria Control Program </p><p>1 person </p><p>MC - Malaria Consortium </p><p>              1 person</p><p>eGov</p><p>              2 people</p>             |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Dates                | 16th and  17th of November                                                                                                                                                                                                                                                                                                                                                           |
| Location             | Nampula City                                                                                                                                                                                                                                                                                                                                                                         |
| Devices Needed       | 6 phones for the DPS participants                                                                                                                                                                                                                                                                                                                                                    |
| Macro plan for Day 1 | <p>From 9 am to 12 pm:<br>      - Session with TWG to go through the UAT Test Cases;<br><br>From 2 pm to 4:30 pm:</p><ul><li>Induction session with Health Facility (HF) Coordinators and Community Distributor (CD) Supervisor; </li><li>UAT with Community Distributor Supervisor;</li><li>Debrief session with CD Supervisor and HF Coordinator; </li></ul>                       |
| Macro plan for Day 2 | <p>From 8 am to 11:30 am:</p><ul><li>Induction session with community distributor supervisor and -community distributor;</li></ul><ul><li>UAT with Community Distributor and Community Distributor Supervisor </li></ul><ul><li>Debrief session with CD Supervisor and CD</li></ul><p>From 1 pm to 3:30 pm: </p><ul><li>Session with TWG to debrief on the UAT </li></ul><p><br></p> |

## UAT Methodology

During the testing process, a pre-approved list of test cases/scripts will be executed to verify the behaviour and performance of various functionalities. The observations from the testing will be noted and classified as defects or enhancements. Some of the enhancements may be doable using configuration changes while others (change requests) may have to go through a [change management](change-management-strategy.md) process.

UAT observation classification:

<table data-header-hidden><thead><tr><th width="118"></th><th></th><th></th><th></th></tr></thead><tbody><tr><td>Serial number</td><td>Observation Type</td><td>Description</td><td>Addressing Mechanism</td></tr><tr><td>1</td><td>Defects</td><td>Any observation pertaining to a feature or functionality not working as expected or agreed at the time of scope review, will be classified as issue</td><td>The observations classified as defects will be taken up by the eGov program team for further validation, prioritisation and fixing. Minor issues originating due to incorrect configurations or erroneous labels, or translations will be fixed and be made available for re-testing during the next UAT cycle.</td></tr><tr><td>2</td><td>Change Requests (CR)</td><td>Any recommendations to enable or disable a functionality from the initial requirements or a new functionality to be added</td><td>These will be handled via Change control Process as per the SoP defined and will be evaluated based on their impact and effort.</td></tr></tbody></table>

The UAT team will execute all the test scripts referenced later in the "UAT Feedback" section. Users may also perform additional tests not detailed in the plan but remain relevant and within the scope of the project. &#x20;

Users will report the feedback to the eGov team for documentation and escalation using a Google sheet. These defects will be described, prioritised, and tracked by using screen captures and steps necessary for the development team to reproduce the defect. For change requests, the requirements will be described, analysed, prioritised, and tracked. &#x20;

## Test Phases

The various phases of UAT are shown in the below diagram:

| ![](https://lh7-us.googleusercontent.com/\_mDq4IUC1QXWsnaYy4GhojpmyfBs8kbGkbeVmClYY1AnOnBBsKTT\_kAur1yZCBNd7A6AJ-IA3YBFJcOJqdXc4ZFOIYYBgSn3ywAt1b4R6BG0sdbnaQXo9FaC5paLmmE-wmrn-ft22Xw0AK7LFCqGkA) |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## Scope for UAT

UAT will be conducted in  1 phase with the below mentioned scope

| Test Phase | Tracks             | Scope                                                                          |
| ---------- | ------------------ | ------------------------------------------------------------------------------ |
| UAT        | SMC HCM Mobile App | Registration and Service Delivery, Supervision, Inventory from the mobile app. |

#### Out of scope of UAT

For the below mentioned functionalities, separate demo and/or training sessions will be conducted for the targeted user groups.

1. Help desk for complaints and user management

&#x20;      a. User Management module to add/update/ activate/deactivate users and role mapping

&#x20;      b. Handling complaints via inbox functionality

2. Central, Provincial, District dashboards and reports.&#x20;

During UAT , the team will validate the end-to-end flow and features of the application as listed below:&#x20;

* End-to-end business flow for each of the identified user flows&#x20;
* All the required fields are present
* System is accepting only valid values
* User can save after form filling all the mandatory fields
* Correctness of label and its translations&#x20;

## Prerequisites for UAT

Following is the list of prerequisites for conducting the UAT

* The HCM Mobile App for UAT deployed in the UAT environment
* Mobile phones setup with HCM app.&#x20;
* Configuration of HCM Mobile App in UAT environment with master data from Nampula
* Readiness of handouts

&#x20;     \- Test Case document

&#x20;     \- Mockups&#x20;

&#x20;     \- Defect/Change request reporting template&#x20;

* Availability of teams from SMC TWG (Technical Working Group) and SPS for UA testing
* Nomination of participants for the UAT session so that test accounts can be created by eGov.

## UAT Environment

The UAT environment will be similar to the production environment in terms of specifications, and will be provided by eGov, so that accurate assumptions can be drawn regarding the application’s performance.

## UAT Process

Each test participant will be provided with a checklist to verify access to the applications within the defined scope of testing. The tester will then login, perform the prescribed steps, and generate the expected results for each activity. Any feature identified as missing or bug during testing from the UAT environment should be reported back to eGov.

## UAT Data

Access to the test data is a vital component in conducting a comprehensive test of the system. All UAT participants will require the usage of test accounts and other pertinent test data which should be provided by SMC TWG upon request. The user roles should fully emulate production in the UAT path. The test accounts and role mapping shall be done for the users identified by eGov. Following are sample test data for UA testing:

* Sample Master Data

&#x20;     \- Users data for test login creation

&#x20;     \- Location master (AP/Locality/Health Facility/Village )

&#x20;     \- Micro Plan of a district&#x20;

## Roles and Responsibilities

| SoP                             | Priority | Owner    | eGov Int review-1 | eGov Int review-2 | Sharing with CHAI | CHAI review | Finalization |
| ------------------------------- | -------- | -------- | ----------------- | ----------------- | ----------------- | ----------- | ------------ |
| Training                        | P1       | Pradipta | 13-Feb-23         | 15-Feb-23         | 16-Feb-23         | 21-Feb-23   | 23-Feb-23    |
| Helpdesk                        | P1       | Pradipta | 13-Feb-23         | 15-Feb-23         | 16-Feb-23         | 21-Feb-23   | 23-Feb-23    |
| User management                 | P1       | Ankit    | 16-Feb-23         | 17-Feb-23         | 17-Feb-23         | 21-Feb-23   | 23-Feb-23    |
| UAT                             | P1       | Sagar    | 16-Feb-23         | 17-Feb-23         | 17-Feb-23         | 21-Feb-23   | 23-Feb-23    |
| Change Management               | P2       | Ankit    |                   |                   |                   |             |              |
| Master Data management          | P2       | Sagar    |                   |                   |                   |             |              |
| Platform and app monitoring SoP | P2       | Elzan    |                   |                   |                   |             |              |
| MDM(scale fusion ) SoP          | P2       | CHAI     |                   |                   |                   |             |              |
| Login/logout and sync           | P1       |          |                   |                   |                   |             |              |

#### SMC TWG

* Nomination of stakeholders for executing  the UAT
* Verification of product based on UAT scenarios
* Decision regarding date and venue
* Providing feedback after the UAT session and sign off

#### eGov

* Readiness of HCMP with required features
* Demo to SMC TWG before the UAT event
* Framing test scenarios
* Creation of UAT Plan
* Collection and triaging of the UAT feedback
* Translation of UAT feedback

#### NMCP

* Arrangement of logistics-Venue
* Addressing costs for all the government personnel involved in the UAT

#### MC

* Providing feedback after the UAT session

#### Nampula SPS

* Availability of the end users for SMC&#x20;
* Access to the HF&#x20;

## UAT Team

The test team is composed of members who possess a knowledge of the operations and processes on the ground. &#x20;

1. These team members will be able to initiate test input, review the results,&#x20;
2. Have prior experience/learnings from SMC campaign digitisation in Mozambique&#x20;

All team members will be presented by the eGov team with an overview of the test process and what their specific role in UAT will be.  The eGov team will oversee testing by assigning scripts to testers, providing general support, and serving as the primary UAT contact point throughout the test cycle.

| Name of participant | Project Role/Designation | Phone | E-mail | <p>Entity </p><p>(NMCP/DIS/DTIC/MC)</p> |
| ------------------- | ------------------------ | ----- | ------ | --------------------------------------- |
|                     |                          |       |        |                                         |
|                     |                          |       |        |                                         |

**Note:** The above table needs to be filled by SMC TWG with the details of the  nominated participants of the UAT session.

## UAT Deliverables

The following sections detail milestones crucial to the completion of the UAT phase of the project. Once all dependent milestones have been completed, NMCP/DIS/DTIC will formally sign-off on the system’s functionality and distribute an email to all project stakeholders.

## UAT Activities and Schedule&#x20;

All core UAT activities along with the deliverable dates are described in the below table:

| Task                                                                                                                  | Owner   | Start Date | Expected Closure date |
| --------------------------------------------------------------------------------------------------------------------- | ------- | ---------- | --------------------- |
| UAT                                                                                                                   |         |            |                       |
| Creation of the UAT-1 test plan and sharing with NMCP for review                                                      | eGov    | 18-Oct-23  | 18-Oct-23             |
| Creation of the UAT test cases/scripts and sharing with NMCP for review                                               | eGov    | 18-Oct-23  | 20-Oct-23             |
| Nomination of UAT participants so that user accounts can be created                                                   | SMC TWG | 16-Oct-23  | 19-Oct-23             |
| Arrangement of venue and other logistics for UAT session                                                              | NMCP    | 19-Oct-23  | 20-Oct-23             |
| Readiness of the UAT server instance                                                                                  | eGov    | 19-Oct-23  | 23-Oct-23             |
| Installing test version of the HCM application in personal phones                                                     | NMCP    | 15-Nov-23  | 15-Nov-23             |
| Conducting the UAT testing along with the end users and SMC TWG                                                       | SMC TWG | 16-Nov-23  | 17-Nov-23             |
| Collation and triaging of UAT feedback and communication to SMC TWG regarding what can be incorporated in the HCM app | eGov    | 17-Nov-23  | 17-Nov-23             |
| Reviewing the test results  and providing sign off of UAT                                                             | SMC TWG | 17-Nov-23  | 17-Nov-23             |

## UAT Session Structure

The UAT session will be conducted hybrid, in Nampula and remotely using Zoom Meeting. The detailed plan for the UAT session is as follows:&#x20;

| Serial number                | Activity                                                                                                                                                                                                                | Approximate Duration/Participants              | Time / Location                                                   |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------- | ----------------------------------------------------------------- |
| **Day 1: 16 Nov 2023**       | <p><br></p>                                                                                                                                                                                                             |                                                |                                                                   |
| 1                            | <ul><li>Introductions to UAT Session plan </li></ul>                                                                                                                                                                    | 10 minutes \| TWG members                      | <p>9.00 am-9.10 am</p><p><br></p><p>Zoom Meeting/ SPS Office</p>  |
| 2                            | <ul><li>Walkthrough of Mobile app and Test cases </li><li>Walkthrough of Defect/CR reporting templates </li><li>Distribution of test cases </li></ul>                                                                   | 50 Minutes \| TWG members                      | <p>8.10 am - 9.00 am</p><p>Zoom Meeting /SPS Office</p>           |
| 3                            | <ul><li>Execution of Test cases </li><li><p></p><ul><li>Registration &#x26; Distribution</li><li>Supervision </li><li>Refer</li><li>Inventory Management </li></ul></li><li>Capture feedback  in google sheet</li></ul> | 120 Minutes \| TWG members                     | <p>9.00 am-11.00 am</p><p>Zoom Meeting /SPS Office</p>            |
| 4                            | <ul><li>Collation of feedback received</li></ul>                                                                                                                                                                        | 90 minutes \| TWG members                      | <p>11.00am-12.30 pm</p><p>Zoom Meeting /SPS Office</p><p><br></p> |
| <p><br></p>                  |                                                                                                                                                                                                                         |                                                |                                                                   |
| 5                            | <ul><li>Walkthrough of Mobile app and Test cases for HF Supervisor and CD Supervisor and </li><li>Inventory Management and supervision  test Cases</li></ul>                                                            | 30 Minutes \| HF Supervisor and CD Supervisor  | 2.00pm - 2.30pm                                                   |
| 6                            | <ul><li>Execution of Test cases </li><li><p></p><ul><li>Supervision </li><li>Inventory Management </li></ul></li><li>Capture feedback  in google sheet</li></ul>                                                        | 90 min \| HF Supervisor and CD Supervisor      | 2.30pm - 4.00pm                                                   |
| 7                            | <ul><li>Collation of feedback received and debrief of the session and results </li></ul>                                                                                                                                | 30 minutes \| HF Supervisor and CD Supervisor  | 4.00pm - 4.30 pm                                                  |
| **Day 2: 17 November  2023** |                                                                                                                                                                                                                         |                                                |                                                                   |
| 1                            | <p>Induction session with community distributor supervisor and community distributor;</p><ul><li>Registration &#x26; Distribution </li><li>Refer</li></ul>                                                              | 30 min \| CD Supervisor and CD                 | 8:30 am - 9:00 am                                                 |
| 2                            | UAT with Community Distribuitor and Community Distribuitor Supervisor                                                                                                                                                   | 120 min \| CD Supervisor and CD                | 9.00 am - 11.00 am                                                |
| 3                            | Debrief session with CD Supervisor and CD                                                                                                                                                                               | 30 min \| CD Supervisor and CD                 | 11.00 am - 11.30 am                                               |
| <p><br></p>                  |                                                                                                                                                                                                                         |                                                |                                                                   |
| 4                            | Review of feedback received and clarification of doubts if any (agreement on CRs and bugs)                                                                                                                              | 60 minutes \| CD Supervisor and CD             | 2.00pm-3.00pm                                                     |
| 5                            | UAT Sign off and defining next steps                                                                                                                                                                                    | 30 minutes \| CD Supervisor and CD             | 3.00 pm - -3.30pm                                                 |

For the CRs identified during UAT, the standard change management process will be followed.&#x20;

## UAT Sign off&#x20;

* The mutually agreed defects/CR from UAT will be discussed in the post- meeting.&#x20;
* The sign-off shall be provided at the end of UAT by SMC TWG via an email communication.
* Post sign-off the application will be ready for the deployment in the production environment.&#x20;

## User Acceptance Test  Cases

Test cases provide a high-level description of the functionality to be tested.  All regression and new functionality test cases are contained in the Excel spreadsheet “UA Test Cases” to be shared before.&#x20;

The team will leverage relevant QA test cases for project specific functionality.  Each test case based on new functionality will reference a specific functional requirement.

Each script contains the test case number, test description, requirement number, action to be performed, test data to be utilized, expected results, error descriptions (if applicable), pass/fail results, date tested, and any additional comments from the UA tester.

The UA test scripts are contained within the UAT test case spreadsheet and can be accessed via hyperlink from each individual test case.

## UAT Feedback&#x20;

Defects and change requests will be entered and tracked in Google sheet by any member of SMC TWG during the UAT process. Each entry will include detailed information about each defect/CR.

#### UAT Defect/CR Tracking

Test team will be provided with instruction on how to effectively execute test scripts, as well identify, capture, and report defects/observations by the eGov team at the beginning of the UAT session. The test team will present their findings during the UAT session.&#x20;

#### UAT Defect Life Cycle&#x20;

Defects must be clearly captured and escalated to ensure prompt resolution by development.  Each defect submitted by UAT will be assigned a priority, worked by development, resolved, and re-tested by UAT prior to closure. The following is a snapshot of the standard defect lifecycle:

![](https://lh7-us.googleusercontent.com/7rd4mqlAZsRKx4t8g6pzk7LyXg6XEZShpS68NXsv3E68GxxjUVO4DumSxCuJPFkHYDTxTZ7ObP7UWTXyCQuf9-KX2WKsG7WDZRG9AsIG5cCzZXD1-c3igYR7zzzpKE5oweaKErkWL7lzVh1yoQKOoQ)

#### Prioritisation

the SMC TWG together will prioritise and classify defects.  Defects found in UAT can be assigned one of three (3) levels of severity:

* P1, Work Halted – Testing defects that due to the complexity of the function or the scheduled dates are putting the implementation date at risk.  No workaround exists.
* P2, Work Slowed – Testing defects occurring in a less complex function of the application with sufficient time to resolve before the implementation date – but must be implemented as scheduled.  A workaround has been identified and is listed in the defect.
* P3 and lower, Work Unaffected – Testing defects occurring in a function that are simple to fix or could be excluded if not resolved by the scheduled implementation date.

#### Response (acknowledgement of the issue) Commitments for Defects

| Severity                      | Description                                                                                                      |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| P1, Work Halted               | Critical application outage impacting service for which the cause is unknown. No bypass or workaround available. |
| P2, Work Slowed               | A key component of the application is degraded, unusable or unavailable, some users affected.                    |
| P3 and lower, Work Unaffected | A component of the application is degraded, which causes a minor inconvenience, but a workaround is available.   |

As a non-profit, we are unable to make any commitment on how long issues will take to fix and deploy in production. We will endeavour to resolve P1 issues as quickly as possible.  &#x20;

## UAT Change Request Life Cycle&#x20;

The change request must be clearly captured and reported for analysis to identify effort and Impact to the eGov team. Each CR submitted will be validated and categorised for acceptance and then assigned with a priority. The development team will work on it and will be made available for testing. Following is a snapshot of the standard CR lifecycle:

![](https://lh7-us.googleusercontent.com/LDmUBfWkOnPMI0jyLpPyp4iOINABag-5-K31RAkDGOjQetEBnqE1iypirUuzFjPzEC6laP3La5uwXav2gjsD9MStidEeD7yxkY6IT4kbrOfjtAI-nA-g27R9VUu416XBLY0a-ZLrQmHjGVGcXMMnYg)

#### Categorisation&#x20;

eGov in consultation with NMCP will decide acceptance and categorisation of change requests. Change requests found in UAT can be assigned one of three (3) levels of category:

* Must Have – Change requests that are needed for the success of a campaign. No workaround exists.
* Should Have – Change requests that are required for better tracking and monitoring and will increase the ease of use of the system for users. A workaround has been identified and is listed in the CR.
* Good to Have – Change requests that are simply for better visualisation and reporting. It could be excluded if not resolved by the scheduled implementation date.

eGov to endeavour to cover the "must have" changes before distribution. Lower priority changes will be taken through the eGov gating process for planning the subsequent releases.
