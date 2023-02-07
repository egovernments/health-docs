# User Management v1

## Table of Contents

Background

Target Audience

Assumptions and Validations

Process Flow

Solution

Out of Scope

Specifications

## Background

This document describes the need and scope of a digital platform for health campaigns, explaining the product’s features, specifications, purpose, and functionality. It also provides a descriptive view of the application along with the specification of each element.

## Target Audience

This document is intended for the engineering and platform (tech team), product management, and implementation teams to agree on the requirements for the Health Campaign Management Platform (HCM).

#### About

The ability for supervisors/managers to create and manage users and team assignments for their respective boundaries through the user interface.

#### Problem

The current process for managing users is operationally heavy for the following reasons:

* A high volume of user accounts is required initially.
* The program does not have the capacity to use backend API’s, and hence would rely on implementation partners (CHAI or eGov). This acts as a blocker as the final list of users and teams is finalised 3 days before the campaign starts.
* Multiple changes are requested throughout the campaign (high churn rate for contractual workers).

#### Impact

Delay in creating and sharing new user credentials or changing project assignments impacts campaign operations (and ultimately coverage) as users have to wait on the field to receive their credentials and start working. This also creates a dependency on the implementation partner to support each campaign and does not empower the program to take ownership (the solution is not sustainable).&#x20;

Assumptions and Validations

| Theme                                            | Assumption                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| User account creation                            | <ul><li>Assumed that the program will collect user demographic details during user onboarding and link them to the user profiles. </li><li>If demographic details are not collected and linked to user accounts, then the creation of a staff registry will not provide the data that is fit for reuse.</li><li>Users can exist in the system even without a campaign assigned.</li></ul> |
| Bulk operations                                  | <ul><li>Assumed that the frequency of bulk account creation and deactivation is low and will happen before and after the campaign (UI to perform bulk user management is good to have).</li></ul>                                                                                                                                                                                         |
| UI for user management                           | <p></p><ul><li>A UI for user management will enable decentralised user management and the program will train district-level users to perform user management actions to reduce the load on the central system admin.</li></ul>                                                                                                                                                            |
| Mapping of user accounts to administrative areas | <ul><li>With a UI that decentralises user management, it is assumed that users will be created and mapped to more granular levels in the boundary hierarchy.</li><li>Mapping user accounts at a higher boundary level will hamper the generation of reports for team performance.</li></ul>                                                                                               |
| User management                                  | <ul><li>UI for user management will require an internet connection (no support for offline user management).</li><li>User management functionality to be accessed using responsive web apps (support desktop and mobile views).</li></ul>                                                                                                                                                 |
| Password reset                                   | <ul><li>If the users do no have email IDs linked to their accounts, then a common recovery email must be linked to each account which will be used for password recovery.</li></ul><p>         - In this case, only the system administrator    or any user who has access to the recovery email must be able to reset passwords via an email   OTP-based authentication.</p>             |

### Role-Action Mapping

1. System administrator&#x20;

&#x20;      a. Create, search, update and deactivate user accounts.

&#x20;          \- CRUD other system administrator accounts.

&#x20;      b. Create, assign, update, delete role assignments.

&#x20;      c. Create, assign, update, delete campaign assignments.

2. Supervisors

&#x20;      a. Create, search, update and deactivate user accounts (except system admin).

&#x20;      b. Assign/update/delete role assignments.

&#x20;      c. Assign/update/delete campaign assignments.

3. Helpdesk user

&#x20;      a. Create, search, update and deactivate user accounts (except system admin).

&#x20;      b. Assign/update/delete role assignments.

&#x20;      c. Assign/update/delete campaign assignments.

\


[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
