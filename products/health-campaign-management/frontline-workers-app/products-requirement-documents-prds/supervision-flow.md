# Supervision Flow

## Table of Contents

Background&#x20;

Target Audience&#x20;

Objectives (of this release)&#x20;

Assumptions and Validations&#x20;

Solution - Quick Win&#x20;

Out of scope&#x20;

Design&#x20;

## Background

This document describes the need and scope of a digital platform for health campaigns, explaining the product’s features, specifications, purpose, and functionality. It also provides a descriptive view of the application along with the specification of each element.

## Target Audience

This document is intended for the engineering and platform (tech team), product management, and implementation teams to agree on requirements for the Health Campaign Management Platform (HCM).

## Objectives (of this release)

1. To enable actors with a digital system to manage and implement health campaign activities.&#x20;

&#x20;      a. Facilitate FLWs, supervisors, district officers, and other actors to collect and analyze data accurately, along with monitoring the tasks from registration to service delivery. Also, regular progress checks can be performed at any time and a comparative analysis can be derived at the district levels for different teams.&#x20;

&#x20;      b. Facilitate better diagnostics with improved access to healthcare interventions for the general public.

2. To enable more and more adoption of the HCM platform for multiple health campaigns by providing flexibility in the UI and UX as well as product specifications.

&#x20;      a. Emphasis on adopting digital systems by collaborating with several healthcare initiative bodies.

&#x20;      b. Provide scope for future changes and improvements in the application.

## Assumptions and Validations

| Theme               | Assumption                                                                                                                                                                                                                                                                                                                                                                       |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Filling a checklist | <ul><li>Assumed that supervisors will record the checklist during or after they have performed the inspection.</li><li>There is no requirement to backdate a checklist or make changes to responses after a checklist has been submitted.</li><li>All checklists will be completed in one go and there is no requirement to submit an incomplete checklist as a draft.</li></ul> |
| Creating checklists | <ul><li>Questions types supported would be:</li></ul><p>       - Yes/No answers</p><p>       - Short answer type</p><p>       - Long answer type</p><p>       - Multiple answers type</p><p>       - Checkbox answer type</p><p>       - Date answer type</p><p>       - Time answer type</p>                                                                                    |

### Role-Action Mapping

System Administrator:&#x20;

a. Create, search, edit and delete checklists.

b. Assign checklists to projects.

c. Edit/delete filled checklists.&#x20;

Supervisors:&#x20;

a. View assigned checklists.

b. Fill assigned checklists.

Field Supervisor:

a. View assigned checklists.

b. Fill assigned checklists.

## Solution

1. Context: Supervisors are required to perform random or scheduled inspections and record observations of the inspection activity in the supervision checklists.
2. The number of checklists and the number of questions in the checklist will be based on the program’s requirements.
3. The system administrator must have the ability to create supervision checklists.

&#x20;       a. Checklists are forms with questions.

&#x20;       b. Current scope:

&#x20;       i. Ability to create/edit a questionnaire with yes/no responses: Questions and alert messages must be configurable as per the program requirements.

&#x20;      ii. Ability to insert validations/conditions on the questions present in the checklist. The use case to consider for v1: If the user selects “No” as a response to a particular question, the user must be able to see an information tip on the checklist displaying the corrective action to be taken and must also be able to enter a justification behind selecting ‘No.’

&#x20;      iii. Marking a question as mandatory or optional (Validations are applicable on all questions irrespective of whether the question is mandatory or not).

&#x20;      iv. Localization support is required as checklists would be required in the local language:&#x20;

&#x20;      v. Support for the following question types required:&#x20;

&#x20;      a. Yes/No answers

&#x20;      b. Short answer type

&#x20;      c. Long answer type

&#x20;      d. Multiple answers type

&#x20;      e. Checkbox answer type

&#x20;      f. Date answer type

&#x20;      g. Time answer type

&#x20;      h. Lat/Long coordinates– Must have for v1

&#x20;      i. Media - Good to have

&#x20;      vi. The system admin must be able to view all filled-in checklists and be able to edit or delete the submitted checklists (via backend, No UI).

4.  Ability to assign checklists to particular roles: Not all checklists may be required by all supervisors. For example, a provincial supervisor may be responsible for inspecting X while a district supervisor may be responsible for performing X and Y.



    a. One checklist can be mapped to multiple roles\
    \
    b. Users must be able to view and fill the checklists that are assigned to their assigned roles.\

5. Users must be able to view all previously submitted checklists:

&#x20;      a. Good to have: Inform users if the checklist submission is due.

&#x20;      b. Good to have: A user must be able to view whether a particular checklist was filled or not, when it was filled, how many times it was filled (as per the program SOP, users are required to fill the checklists x number of times during the campaign).

&#x20;      c. The same checklist may be filled out  multiple times during the campaign.

7. The date of checklist submission must be tracked and the frequency of each checklist submission (linked to the user) must be recorded for reporting purposes.
8. The latitude/longitude coordinates must be captured at the backend and linked to the checklist submission.
9. Users must be able to save a checklist as a draft (good to have).
10. Users must be able to view and fill checklists even when offline and sync the filled checklists once internet connectivity is available.

&#x20;      a. Sync down and Sync up support required.

11. Dashboard requirements:

&#x20;      a. Indicators to track the aggregates of all checklists filled:

&#x20;      i. Filter based on administrative area.

![](https://lh6.googleusercontent.com/VK8lxtCd3xutpDpZglfEBM7hqOnooqQV4noCp9Wwc6kUWHWIHHD-3B3eOWplAYbdooYsRmhafmJ0\_Wrk7kG49bWSPHPCSoIV16eStOyD041WvlrrgQsCh\_JsYADodJSXbK9gQ4RVDPkBk07iMI0ievc)

12. Reports:

&#x20;      a. Users must be able to view a report on the response trend for each question within a checklist.

&#x20;      b. Indicators to track the aggregates of each checklists filled:

&#x20;      i. Filter based on role.

## Risk/Limitations&#x20;

Addressed in the out of scope section.

Out of scope

* Deleting a filled checklist on UI.
* Editing a checklist on UI.

## Design

Find the mock-ups below:

HCM Homescreen

After logging into the application, the user lands on this screen which displays daily performance (number of households registered). The progress bar must reset daily at 00:00 hours and start from 0 registrations. The action buttons related to the beneficiary are present  which include:

* Beneficiaries
* View Reports
* Sync Data
* Call Supervisor
* File Complaint

At the bottom, there is a card that shows how many records are unsynced for the user’s convenience to sync data. If all the records are synced, then the card must say, “All records are synced.”

The help button is on every screen of the application, and by clicking on it a user can get the walkthrough of the elements on that screen.

On the top right, the administrative area assigned to the user is displayed which will be based on the level of hierarchy. The hamburger button on the top left corner covers some other actions mentioned further.

![](<../../../../.gitbook/assets/Android - 484 (2).png>)

### View My Checklists

![](../../../../.gitbook/assets/IMG\_20230513\_234352.jpg)\
\


<div align="left">

<figure><img src="../../../../.gitbook/assets/IMG_20230513_234420.jpg" alt="" width="188"><figcaption></figcaption></figure>

</div>

### Filling a Checklist

&#x20;![](../../../../.gitbook/assets/IMG\_20230513\_234434.jpg)

![](../../../../.gitbook/assets/IMG\_20230513\_234539.jpg)\
\


### Confirmation Screen

![](../../../../.gitbook/assets/IMG\_20230513\_234551.jpg)

### Acknowledgement Screen

![](<../../../../.gitbook/assets/IMG\_20230513\_234704 (1).jpg>)

