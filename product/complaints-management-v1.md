# Complaints Management v1

## Table of contents&#x20;

Background

Target Audience

Assumptions and Validations

Process flow

Solution - Quick Win

Out of scope

Specifications

## Background

This document describes the need and scope of a digital platform for health campaigns, explaining the product’s features, specifications, purpose, and functionality. It also provides a descriptive view of the application along with the specification of each element.

## Target Audience

This document is intended for the engineering and platform (tech teams), product management, and implementation teams to agree on requirements for the Health Campaign Management Platform (HCM).

## Assumptions and Validations

| Theme                | Assumption                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Logging complaints   | <ul><li>Not all complaints will be logged using the complaints module. Users may prefer raising complaints on WhatsApp groups/calls, and may not be registered in the system.</li><li>Complaints are most likely to be logged by users on behalf of other users (Most common use case: Supervisors raising complaints on behalf of users</li></ul>                                                                                                                          |
| Resolving complaints | <ul><li>There is a support helpdesk set up by the program which will receive all complaints raised by system users.</li><li>The support helpdesk must be responsible for reviewing all the complaints in the inbox</li><li>Depending on the complaint, the helpdesk can either resolve, reject or assign the complaint to the respective actor</li><li>Helpdesk users may create complaints on the user’s behalf, which are received over call/WhatsApp messages.</li></ul> |

### Role-Action Mapping

Registrar: Create, view, update and cancel complaints.

Field Supervisor:

a. Create, view, update, and cancel complaints.

b. Resolve complaints, re-assign complaints back to the helpdesk, and reject complaints.

Supervisor:&#x20;

a. Create, view, update, and cancel complaints.

b. Resolve complaints, re-assign complaints back to the helpdesk, and reject complaints.

Helpdesk user:&#x20;

a. Create, view, update, and cancel complaints.

b.  Resolve complaints, assign complaints, and reject complaints.

### Statuses in the workflow

| Status name                                  | Description                                                                                                                                                                | Leads to (next status)                                                                                |
| -------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Submitted (TBD depending on design approach) | Status when a complaint is submitted but hasn’t been received by the helpdesk (to support offline use case).                                                               | Pending Assignment                                                                                    |
| Pending Assignment                           | Status when the complaint has been received by the helpdesk (in the event of a completely online system), the pending assignment must be the first status in the workflow. | Resolved, Rejected, Assigned                                                                          |
| Resolved                                     | Status when the complaint has been addressed and closed successfully.                                                                                                      | NA                                                                                                    |
| Rejected                                     | Status when the complaint is found to be invalid and rejected.                                                                                                             | NA                                                                                                    |
| Assigned To < >                              | Status when the complaint is assigned by the helpdesk to other roles in the workflow.                                                                                      | Resolved, Rejected. The possible status will depend on the workflow configured during implementation. |
| Cancelled                                    | Status, when the user decided to delete the complaint, created.                                                                                                            | NA                                                                                                    |

## Process Flow

<figure><img src="../.gitbook/assets/Screenshot 2023-01-25 at 10.46.33 AM.png" alt=""><figcaption></figcaption></figure>

## Solution

### Complaints: For mobile users

1. Creating a new complaint:

* Any campaign staff (with access to the complaints module) must be able to create a complaint using the mobile app for themselves or on behalf of other users.
* Users can only create complaints for users in the same boundary hierarchy.

&#x20; 2\.  Viewing “My Complaints”:&#x20;

* Users must be able to view the complaints created by themselves in the mobile app and the web portal.
* Users must be able to filter, sort, and search complaints.

Helpdesk View: (Web app and mobile responsive app)&#x20;

1. All complaints raised by any system user in the system must first be routed to the helpdesk.
2. Helpdesk user must be able to filter, sort, and search complaints.
3. The helpdesk user must review all complaints received in the helpdesk’s inbox and perform one of the following actions:

* Resolve: For complaints that can be resolved by the L1 support helpdesk, the helpdesk user must be able to view the details mentioned in the complaints, mark them as “Resolved” and add resolution details.
* Reject: If the helpdesk user determines a complaint to be false, irrelevant, or invalid, the user must be able to mark the complaint as “Rejected” and give proper justification for rejecting the complaint.
* Assign: For complaints that cannot be resolved by the L1 support helpdesk, the helpdesk user must be able to select the appropriate role and assign the complaint. Once the helpdesk user assigns a complaint, the status must be shown as “Assigned."

&#x20;     a. Workflow to be set up during implementation.&#x20;

&#x20;     b. The core product would offer the following workflow: Create→ Submitted to L1 Helpdesk→ Assign to L2 support.

&#x20;     c. The workflow must be configurable to support additions of more workflow states: (For eg. Assign to: Program Managers, Supervisors, etc).

&#x20;4\. Help desk users must be able to create new complaints. The new complaint created must be visible in the helpdesk user’s inbox to take action on (Use case: Helpdesk user receives a complaint over call and creates a complaint in the system for tracking on the user’s behalf).

&#x20; 5\. Report Generation: (Good to have for v1 since already covered in the dashboard)

&#x20;    a. Helpdesk performance report: Report generated on the following parameters:

&#x20;        1\. Time range

&#x20;        2\. Status of complaints

&#x20;        3\. User name

## Risk/ Limitations:&#x20;

Addressed in the Out of Scope section.

## Out of scope:

* Re-opening of complaints
* Auto-escalation of complaints
* Auto-routing of complaints
* Sharing feedback on complaint resolution
* Notification to users on status change
* SLA tracking

## Specifications

| Field                        | Data Type       | Data Validation                                                       | Required (Y/N) | Comment                                                                                                                                                  |
| ---------------------------- | --------------- | --------------------------------------------------------------------- | -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Complaint type               | Dropdown        | Only one complaint type must be selected.                             | Y              | <p>Values to be configured. </p><p>If type is “Other”: Display text box to enter type.</p><p><br></p>                                                    |
| Date of complaint            | Date            | System fetches the current date.                                      | Y              | Must be non-editable (no action required by user).                                                                                                       |
| Administrative area          | String dropdown |                                                                       | Y              | For mobile view: Admin area must be populated based on value set in the location picker For Web view: Select from list of assigned projects/ boundaries. |
| Complaint raised for         | Boolean         |                                                                       | Y              | Options available: Self and other.                                                                                                                       |
| Complainant’s name           | String          | If “self”: Name must be populated as entered in the user’s profile.   | Y              | If “Name” is blank in the user’s profile, the text field must be empty.                                                                                  |
| Complainant’s contact number | Numeric         | If “self”: Number must be populated as entered in the user’s profile. | Y              | If “Number” is blank in the user’s profile, the text field must be empty.                                                                                |
| Supervisor’s name            | String          |                                                                       | N              |                                                                                                                                                          |
| Supervisor’s contact number  | Numeric         |                                                                       | N              |                                                                                                                                                          |
| Complaint description        | String          | Max limit of description: TBD                                         | Y              |                                                                                                                                                          |
| Upload photo                 | Media           | Max size of media: TBD                                                | N              |                                                                                                                                                          |
| Complaint number             | String          |                                                                       | Y              | Unique ID generated by the system.                                                                                                                       |
| Reason for rejection         | Dropdown        |                                                                       | Y              | Must be configurable during impel.                                                                                                                       |
| Assign to                    | Dropdown        | Mandatory if action taken to assign.                                  | C(Y)           | Must be configurable during impel depending on the workflow. Default value: Assign to L2.                                                                |



[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
