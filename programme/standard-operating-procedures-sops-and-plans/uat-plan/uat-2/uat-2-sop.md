# UAT 2 SOP

## Objective

The purpose of this document is to outline the User Acceptance Testing (UAT) process for the final round of testing of the Salama (DIGIT-HCM) platform rollout in Mozambique as part of the Group IV distribution in the Tete province. The first round of testing was conducted between April 27th and 28th, 2023, and the platform was found to be satisfying most of the requirements for the campaign. Key learnings and the feedback from the first round of testing have been incorporated in the platform and the app is now being presented for the final round of testing.

## UAT Methodology

During the testing process, a pre-approved list of test cases/scripts will be executed to verify the behaviour and performance of various functionalities with special focus on the feedback that was gathered from the last round of testing. The observations from the testing will be noted and classified as defects or enhancements. The suggested enhancements, if any, will be taken up for inclusion in the platform if found necessary.

#### UAT observation classification:

| # | Observation Type     | Description                                                                                                                                         | Addressing Mechanism                                                                                                                                                                                                                                                                                            |
| - | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Defects              | Any observation pertaining to a feature or functionality not working as expected or agreed at the time of scope review, will be classified as issue | The observations classified as defects will be taken up by the eGov program team for further validation, prioritisation and fixing. Minor issues originating due to incorrect configurations or erroneous labels, or translations will be fixed and be made available for re-testing during the next UAT cycle. |
| 2 | Change Requests (CR) | Any recommendations to enable or disable a functionality from the initial requirements or a new functionality to be added                           | These will be handled via Change control Process as per the SoP defined and will be evaluated based on their impact and effort.                                                                                                                                                                                 |

The UAT team will execute all the test scripts. Users may also perform additional tests not detailed in the plan but remain relevant and within the scope of the project. &#x20;

Users will report feedback to the eGov team for documentation and escalation using a google sheet. These defects will be described, prioritised, and tracked by using screen captures, verbiage, and steps necessary for the development team to reproduce the defect. For change requests the requirements will be described, analysed, prioritised and tracked.  Information on defect  and CR processing can be found later.

#### Test Phases

The various phases of UAT are shown in the below diagram:

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-06-07 at 6.18.26 PM.png" alt=""><figcaption></figcaption></figure>

#### Scope for UAT

UAT will be conducted in  2 phases with the below mentioned scope. This document deals with the UAT-2 scope as UAT-1 has already been completed.

| Test Phases | Tracks                                   | Scope                                                                                             |
| ----------- | ---------------------------------------- | ------------------------------------------------------------------------------------------------- |
| UAT 1       | HCM Mobile App                           | Registration and Service Delivery, Supervision, Inventory, raising complaints from the mobile app |
| UAT 2       | Retest Issues/ Observations from UAT 1.  | Retesting observations and accepted CRs/bug fixes and signoff                                     |

#### Out of scope of UAT

For the below mentioned functionalities, separate demo and/or training sessions will be conducted for the targeted user groups.

1. Helpdesk for complaints and user management

&#x20;     a. User Management module to add/update/ activate/deactivate users and role mapping

&#x20;    b. Handling complaints via inbox functionality

2. Central, Provincial, District dashboards and reports.&#x20;

During UAT , the team will validate the end-to-end flow and features of the application to validate:&#x20;

* Validate end-to-end business flow for each of the identified user flows&#x20;
* All the required fields are present
* System is accepting only valid values
* User can save after form filling all the mandatory fields
* Correctness of label and its translations&#x20;

### Prerequisites for UAT

Following is the list of prerequisites for conducting the UAT

* The HCM Mobile App for UAT deployed in the UAT environment
* Mobile phones setup with HCM app.&#x20;
* Configuration of HCM Mobile App in UAT environment with master data from Zambezia
* Readiness of handouts

&#x20;     \- Test Case document

&#x20;     \- Mockups&#x20;

&#x20;     \- Defect/Change request reporting template&#x20;

* Availability of teams from NMCP, DIS and DTIC for UA testing
* Nomination of participants for the UAT session so that test accounts can be created by eGov.
* Configuration of ticket tracking tool for UAT (JIRA)

## UAT Environment

The UAT environment will be similar to the production environment in terms of specifications, and will be provided by eGov, so that accurate assumptions can be drawn regarding the application’s performance.

Applicable IP addresses and URLs will be provided by eGov team to the UAT team and all the mobiles will be configured for access to the test environment.

#### UAT Process

Each test participant will be provided with a checklist to verify access to the applications within the defined scope of testing. The tester will then login, perform the prescribed steps and generate the expected results for each activity. Any feature identified as missing or bug during testing from the UAT environment should be reported back to eGov.

#### UAT Data

Access to test data is a vital component in conducting a comprehensive test of the system. All UAT participants will require usage of test accounts and other pertinent test data which should be provided by NMCP upon request. All user roles should fully emulate production in the UAT path. The test accounts and role mapping shall be done for the users identified by eGov. Following are sample test data for UA testing:

* Sample Master Data

&#x20;    \- Users data for test login creation

&#x20;    \- Location master (AP/Locality/Village )

&#x20;    \- Inventory module master (warehouse+product)

## UAT Team

The test team is composed of members who possess a knowledge of the operations and processes on the ground. &#x20;

1. These team members will be able to initiate test input, review the results,&#x20;
2. Have prior experience/learnings from campaign digitisation in Mozambique&#x20;

All team members will be presented by the eGov team with an overview of the test process and what their specific role in UAT will be. The eGov team will oversee testing by assigning scripts to testers, providing general support, and serving as the primary UAT contact point throughout the test cycle.

| Name of participant | Project Role/Designation | Phone Extension | E-mail      | <p>Entity </p><p>(NMCP/DIS/DTIC/partners)</p> |
| ------------------- | ------------------------ | --------------- | ----------- | --------------------------------------------- |
|                     |                          |                 |             |                                               |
|                     |                          |                 |             |                                               |
| <p><br></p>         | <p><br></p>              | <p><br></p>     | <p><br></p> | <p><br></p>                                   |

Note: The above table needs to be filled by NMCP/DIS/DTIC with the details of the  nominated participants of the UAT session.

## UAT Deliverables

The following sections detail milestones crucial to the completion of the UAT phase of the project. Once all dependent milestones have been completed, NMCP/DIS/DTIC will formally sign-off on the system’s functionality and distribute an email to all project stakeholders.

#### UAT Activities and Schedule&#x20;

All core UAT activities along with the deliverable dates are described in the below table:

| Task                                                                                                                                             | Owner                        | Start Date  | Expected Closure date |
| ------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------- | ----------- | --------------------- |
| UAT-2                                                                                                                                            |                              |             |                       |
| Incorporating the UAT-1 feedback in the HCM application based on the results of triaging process                                                 | eGov                         | 8-May-23    | 7-June-23             |
| Creation of the UAT test cases/scripts and sharing with NMCP for review                                                                          | eGov                         | 31-May-23   | 7-June-23             |
| Nomination of UAT participants so that user accounts can be created                                                                              | NMCP/DIS/DTIC                | 5-June-23   | 7-June-23             |
| Arrangement of venue and other logistics for UAT session                                                                                         | NMCP                         | 5-June-23   | 9-June-23             |
| Readiness of the UAT server instance                                                                                                             | eGov                         | 5-June-23   | 2-June-23             |
| Installing test version of the HCM application in test phones                                                                                    | CHAI                         | 8-June-23   | 9-June-23             |
| Conducting the second round of UAT testing along with NMCP stakeholders                                                                          | eGov, NMCP, DIS , DTIC, CHAI | 16-Jun-23   | 16-Jun-23             |
| Collation and triaging of UAT feedback and communication to NMCP                                                                                 | eGov                         | 16-June-23  | 19-June-23            |
| Incorporating any minor suggestions arising out of second round of UAT                                                                           | eGov                         | 20-June-23  | 20-June-23            |
| <p>Fit for go-live</p><p>The test results would be reviewed and the application will be declared fit for use during the Group4 distribution.</p> | eGov                         | <p><br></p> | 21-June-23            |

#### UAT - 2 Session Plan & Structure

The UAT session will be conducted physically in Maputo. The agenda for the UAT session will be as follows. However, this may undergo change based on the scope for UAT-2.&#x20;

| #                   | Activity                                                                                                                                                                                                                                                                                                                                               | Approximate Duration | Time              |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------- | ----------------- |
| Day 1(16th June-23) | <p><br></p>                                                                                                                                                                                                                                                                                                                                            |                      |                   |
| 1                   | <ul><li>Introduction to the UAT-2 Session</li></ul>                                                                                                                                                                                                                                                                                                    | 15 minutes           | 8.00am -8.15 am   |
| 2                   | <ul><li>Walkthrough of Mobile app</li><li>Walkthrough of the feedback from the previous(UAT-1) session</li><li>Walkthrough of test scenarios to be executed</li><li>Walkthrough of Defect/CR reporting templates</li><li>Distribution of printed templates for capturing Defects / CR </li><li>Distribution of test cases and mobile devices</li></ul> | 60 Minutes           | 8.15am-9.15 am    |
| <p><br></p>         | <ul><li>Testing of the Salama (DIGIT HCM app)-Session 1</li></ul>                                                                                                                                                                                                                                                                                      | 45 minutes           | 9.15 am-10.00 am  |
| <p><br></p>         | Tea Break-1                                                                                                                                                                                                                                                                                                                                            | 30 minutes           | 10.00 am-10.15 am |
| 3                   | <ul><li>Testing of the Salama (DIGIT HCM app)-Session 2</li></ul>                                                                                                                                                                                                                                                                                      | 150 Minutes          | 10.15 am-12.45 am |
| 4                   | <ul><li>Review of the testing performed</li></ul>                                                                                                                                                                                                                                                                                                      | 15 minutes           | 12.45 am-1.00 pm  |
| <p><br></p>         | Lunch Break                                                                                                                                                                                                                                                                                                                                            | 60  minutes          | 1.00pm-2.00 pm    |
| 5                   | <ul><li>Testing of the Salama (DIGIT HCM app)-Session 3</li></ul>                                                                                                                                                                                                                                                                                      | <p><br></p>          | 2.00 pm-3.00 pm   |
| <p><br></p>         | Tea Break-2                                                                                                                                                                                                                                                                                                                                            | 15 minutes           | 3.00 pm-3.15 pm   |
| 1                   | Defect review: Clarifying Q\&A on defects raised (if any)                                                                                                                                                                                                                                                                                              | 45 Minutes           | 3.00 pm-3.45 pm   |
| 4                   | Session closure                                                                                                                                                                                                                                                                                                                                        | 15 minutes           | 3.45 pm-4.00 pm   |

#### UAT Sign off&#x20;

* The mutually agreed defects/CR from UAT 1 will be re-tested in UAT 2.&#x20;
* Post the second round of testing as part of UAT-2 , the application will be deemed ready for the deployment in the production environment.&#x20;

## UAT Feedback

Any minor feedback arising out of the UAT-2 testing that requires minimal changes in the Salama (DIGIT HCM) platform will be incorporated before the campaign goes live.

#### UAT Defect Life Cycle&#x20;

Defects must be clearly captured and escalated to ensure prompt resolution by development. Each defect submitted by UAT will be assigned a priority, worked by development, resolved, and re-tested by UAT prior to closure. The following is a snapshot of the standard defect lifecycle:

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-06-07 at 6.25.44 PM.png" alt=""><figcaption></figcaption></figure>

#### Prioritisation

eGov and NMCP together will prioritise and classify defects.  Defects found in UAT can be assigned one of three (3) levels of severity:

* Critical defects: These are the defects found during the testing that render the application useless and prevent it from being used during the campaign. These will be resolved on priority.
* Major defects: These defects make a part of the application functionality unavailable to the user but the user should still be able to use the application with limited functionality or a workaround exists. These will be taken up and fixed before the campaign starts.
* Minor: These are the defects that reflect a deviation from the agreed scope but do not hamper the use of the application in any way. These will be considered for fixing only if the time permits.

#### UAT Change Request Life Cycle&#x20;

CR must be clearly captured and reported for analysis to identify effort and Impact to the eGov team. Each CR submitted will be validated and categorised for acceptance and then assigned with a priority. The development team will work on it and will be made available for testing. Following is a snapshot of the standard CR lifecycle:

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-06-07 at 6.27.29 PM.png" alt=""><figcaption></figcaption></figure>

#### Categorisation&#x20;

eGov in consultation with NMCP will decide acceptance and categorisation of change requests. Change requests found in UAT can be assigned one of three (3) levels of category:

* Must Have – Change requests that are needed for the success of a campaign. No workaround exists.
* Should Have – Change requests that are required for better tracking and monitoring and will increase the ease of use of the system for users. A workaround has been identified and is listed in the CR.
* Good to Have – Change requests that are simply for better visualisation and reporting. It could be excluded if not resolved by the scheduled implementation date.

eGov to endeavour to cover Must Have changes before distribution. Lower priority changes will be taken through the eGov gating process for planning subsequent releases.

## Success criterion

1. No Critical defects found during the execution of the test scenarios.
2. 90% of the total test cases could be executed successfully and the observed behaviour was found to match the expected results.

## Post test activities and checklists

**1. SUS Questionnaire : (For the application)**

(On 5 point scale: Strongly Disagree, Disagree, Neutral, Agree, Strongly Agree):

1. I think I would like to use this tool frequently
2. I found the tool unnecessarily complex
3. I thought the tool was easy to use
4. I think that I would need the support of a technical person to be able to use this app
5. I thought there was too much inconsistency in this tool
6. I would imagine that most people would learn to use this tool very quickly
7. I found the tool very difficult to use
8. I felt very confident using the tool
9. I needed to learn a lot of things before I could get going with this tool
10. I could efficiently complete my tasks using the system

**2. Feedback on the UAT process**

1. On a scale of 1 to 10, how well did the UAT task represent real-world scenarios and user interactions with the system?
2. Was the UAT task comprehensive, covering all key functionalities and features of the system?
3. Did the UAT include a variety of scenarios, data  inputs, and user interactions to thoroughly test the system?
4. Was the UAT task representative of different user roles, permissions, and use cases that are relevant to the system?
5. Did the UAT task adequately address any specific requirements or criteria that were defined for the UAT phase?

**3. Sign-Off Checklist**

1. All UAT Test cases completed: Verified that all UAT test cases, as defined in the UAT plan, have been executed and completed
2. Business requirements validated: Validated that all business requirements, as defined in the requirements documentation - all features, functions, workflows, calculations, translations have been thoroughly tested and verified
3. Compatibility tested: Verified that the application has been tested on the specified device which is used for the distribution (Samsung A09) and Operating System (Android) and any compatibility issues have been addressed
4. All feedback have been identified and documented. Agreed on the priority.&#x20;
5. Documentation updated: Ensured that all relevant documentation, including user manuals, has been updated to reflect any changes made during UAT
6. UAT summary report prepared: Prepared a UAT summary report that includes the UAT results, findings, and any outstanding issues or risks identified during UAT

## References

The following are reference documents which have been leveraged for project specific information in the design of the UAT plan:

* [UAT 2 test scenarios for Salama](uat-2-test-scenarios.md)
* [Observations refeReporting Template](uat-observations/)
* [UAT Feedback Form - SUS](uat-feedback-form-sus.md)
* [UAT Feedback Form - Process](uat-feedform-form-process.md)
* [UAT Test Scenarios](../uat-1/uat-1-test-scenarios.md)
* SUS Questionnaire

## Annexure

## UAT-2 Test Scenarios for Salama&#x20;

Location: MISAU, Maputo

Day: 16th June 2023

### Scenarios:

#### Registration & Distribution:

1. Register 5 households residing in a village in Zambezia. Capture how many numbers are living in the household, and fill in details (age, gender, mobile number) for the head of the household. Then, you proceed to deliver bed nets:

&#x20;      a. Which is less than the number of bed nets suggested by the App for 2 households

&#x20;      b. Which is more than the number of bednets suggested by the App for 1 household

&#x20;      c. Which is same as the number of bednets suggested by the App for 2 households

2. As a distributor you are required to do the distribution in another village than the one you did prior. Change the Village and register 2  households. This time skip adding the Landmark in the household details page. Deliver the exact number of bednets as suggested by the app.
3. You realise that you made a mistake while registering one member and want to  correct your mistake. Search for a household head you have registered which has individual members added. First correct the household head details by changing the age. Then change the mobile number you entered previously with a new mobile number.&#x20;
4. You are a registador and you forgot your password. What will you do?
5. You are not able to see your assigned village in the list of villages. What action would you take?
6. Sync all the records pending to be synced in the application.
7. You are a registador and you realise, one of the members you registered has already been registered by your colleague and is a duplicate entry. What will you do to remove the duplicate entry from your records?

#### Supervision:

1. You are the supervisor for the team working in a Village A in Zambezia, and your team members are in the field distributing nets. As per protocol, you are expected to go and observe them work and record your observations in the Registration and Distribution checklist. Please fill out the checklist and submit your observations for the following checklists. Mark ‘No’ as response for atleast 2 questions in each checklist and provide the reasons.

&#x20;     a. Registration & distribution monitoring&#x20;

&#x20;     b. District warehouse monitoring&#x20;

&#x20;     c. Satellite warehouse monitoring &#x20;

&#x20;     d. Local monitors training monitoring&#x20;

&#x20;     e. Registration & distribution training monitoring

2. You are the supervisor for the team working in a village in Zambezia, and you have made 4 checklist entries so far. You are supposed to make 5 entries for the checklist ‘Registration & Distribution monitoring’ daily. How will you check how many entries you have made so far for today and for which boundaries?
3. Sync all the records pending to be synced in the application.

#### Warehouse Management:&#x20;

1. You are a warehouse manager for a warehouse in an Administrative post in Zambezia and received a stock of 2 bales today into your satellite warehouse from a district warehouse. Enter the receipt of this in the App.
2. You are a local monitor for an Administrative post and received a stock of 45 bednets  back from the distribution team. Enter the receipt of this for the satellite warehouse you are managing in the App as a return.
3. You are a district warehouse manager and you distributed the following

&#x20;      a. 200 nets to the delivery team&#x20;

&#x20;      b. 5 bales to a community warehouse

&#x20;      c. Make entries for these distributions

4. You are inspecting the warehouse at the end of the day as a community warehouse manager and you counted the number of nets in stock at the end of the day. How will you make an entry for this for the following cases?

&#x20;     a. There are 50 more number of nets in the warehouse that you counted than the number of nets suggested by the system

&#x20;    b. There are 10 less number of nets in the warehouse that you counted than the number of nets suggested by the system

5. Sync all the records pending to be synced in the application.
