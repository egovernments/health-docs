# Complaints Management v1

## Table of contents&#x20;

Background

Target Audience

Assumptions and Validations

Process flow

Solution - Quick Win

Out of scope

Specifications

Design

Metrics to track

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



[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
