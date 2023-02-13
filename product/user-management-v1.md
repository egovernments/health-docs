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

## Process Flow

<figure><img src="../.gitbook/assets/Screenshot 2023-02-07 at 11.22.49 AM.png" alt=""><figcaption></figcaption></figure>

## Solution

High-level scope:

* Along with APIs, provide a UI to empower district managers/supervisors to own and manage user account creations/updates for their respective campaigns.&#x20;
* Both bulk user management (template-based upload) and individual user management functionalities would be required on the UI.

&#x20;     \- Bulk user creation will be done at the beginning of the campaign.

&#x20;     \- Individual user create/updates/deletes will most likely be done before and during the campaign.

&#x20;     \- Bulk user deactivation will be done after the campaign.

* The program would need the flexibility to move actors from one campaign to another for operational reasons. Hence, to change campaign assignments, a UI component would be required so that user management can be decentralised.

Note: A project (aka campaign) is defined as follows in the HCM system:

A campaign can be any collection where:

* Either service delivery takes place (that is, the lowest level in the administrative hierarchy),&#x20;
* Or any boundary, which is a parent of the boundaries where the service delivery takes place but needs to report on metrics by aggregating metrics from all the child boundaries.
* Example:

&#x20;     a. Either the campaigns can be setup as a parent-child relationship (tree structure), that is, National (only reporting)-Province(s) (only reporting)-District(s)-only reporting–villages (service delivery and reporting). (Must be of the same campaign type);

&#x20;     b. Or can be set up only at the village level: where village A, village B are two separate campaigns (can be of the same campaign type or different).

### User Accounts

There are two types of user accounts that need to be created during a health campaign:

1. Mobile app users’ accounts: Frontline workers (mostly contractual) who will log in on the phones and submit data into their assigned project. These users must also be able to view mobile reports to track their progress or the progress of their teams.
2. Web app user accounts: Supervisors, system administrators, helpdesk users (most likely permanent employees of the health system, but some can also be contractual), who are mostly responsible for viewing online dashboards and reports to monitor campaign progress and view data submitted by the frontline workers (mobile app users).

&#x20;      a. However, some supervisors may also be responsible for data collection and may act as both data collection agents as well as data reviewers.

3. The system administration must be able to create all user roles and assign actions to each role as mentioned in the role-action mapping section.
4. The system administrator must have the ability to provide user management permissions to other roles as required (example, supervisors, managers).
5. Any user, who has the permission to manage/create users in the system, must also be able to perform the following actions:

&#x20;      a. Create users (except system admin).

&#x20;      b. Search for existing users - Search parameters: Name, username, etc.&#x20;

&#x20;      c. Edit user details.

&#x20;      d. Deactivate users.

&#x20;      e. Edit campaign assignment.

6. The system administrator must be able to create a new user by only specifying the username (credential used to login to the system) and setting the password with an ability to add other demographic information later.

&#x20;      a. The system user must be able to share the list of usernames and passwords with the program, once created.

7. Once created during user creation, the username must not be changed. Users creating user accounts must NOT be able to change usernames once created. Product recommendations on choosing a username (these are only recommendations and the program can decide to create their own username format):&#x20;

&#x20;      a. First name: This is for people to remember. But if there are multiple users with the same name, then use serials (user, user2) or add a second initial.&#x20;

&#x20;      b. Phone number: This is a unique number and easy for most people to remember (existing DIGIT functionality).

&#x20;      c. First-last name: This may be longer and more complex but more likely to be unique for each user.

&#x20;      d. Administrative area name: This approach may be adopted if there is a high turnover as multiple users may use the same username. However, the system will not be able to tell which individual person has submitted the data during analysis (current approach following in LLIN campaign in Mozambique).

&#x20;         i. If the program wants to track the performance of each frontline worker individually, then the product SOP recommends that each mobile app user should have their own username even if they are sharing a device. Since the system will provide reports on the performance/productivity of your mobile app users, If there are multiple mobile users sharing a username, then the performance reports will reflect the team performance and not necessarily individual performance, provided the username to individual mapping is maintained outside the system.

&#x20;     e. Regarding the use of special characters: It is recommended that only commonly known special characters like period (.) be used in the username to make it easy to remember.

&#x20;      f. Regarding the use of capital case: It is recommended to use either all lowercase or all uppercase characters to make it easy for the users to remember and enter the login credentials (lowercase preferred).

&#x20;      g. Regarding the setting of passwords: It is highly recommended that passwords for system administrators, training applications and production applications be kept distinct to avoid confusion.

&#x20;      h. It is also recommended to keep passwords simple so that mobile app users do not forget the password and hence do not face a barrier in using the app.

## Specifications

### Login Credentials (Must have)

| Field    | Data type | Data Validation                           | Required | Comments                                                 |
| -------- | --------- | ----------------------------------------- | -------- | -------------------------------------------------------- |
| Username | String    | Must be unique and non-editable once set. | Y        | The format for creating user names must be configurable. |
| Password | String    |                                           | Y        |                                                          |

### Demographic Information

| Field                  | Data type | Required | Comments                                                                            |
| ---------------------- | --------- | -------- | ----------------------------------------------------------------------------------- |
| First name             | String    | Y        | Must be editable.                                                                   |
| Last name              | String    | Y        | Must be editable.                                                                   |
| Mobile number          | Numeric   | N        | Must be editable.                                                                   |
| Father/husband's name  | String    | N        |                                                                                     |
| Gender                 | Dropdown  | N        | Values: Male, female, others.                                                       |
| Date of birth          | Date      | N        |                                                                                     |
| Email                  | String    | Y        | Add a common email for all users to support OTP-based authorisation-recovery email. |
| Correspondence address | String    | Y        |                                                                                     |



## Risk/Limitations:&#x20;

Due to the existing system design, the system cannot support the following use cases:

1. If a user has role R1 in the LLIN campaign, access to boundaries 1 and 2, and has a different role R2 in the IRS campaign with access to the same boundary (1 and 2). This is due to the HRMS limitation that a role is a common attribute assigned to the user and will remain constant across all campaign assignments.&#x20;
2. Scope for future versions: Linking of role attributes to project assignments \<Needs further discussion>
3. Workaround: During user creation, assign both R1 and R2 roles to the user along with IRS and LLIN campaign assignments.

&#x20;      i. Cons: Users will be able to perform actions associated with both roles in both campaigns assigned.

4. However, this is an edge case and needs to be resolved in future versions of the product. No risk is anticipated for the v1 and v1.1 rollout in Mozambique.

## Out of scope:

1. UI for performing bulk user management actions: CRUD (Will be supported via backend APIs).
2. Collecting additional user details such as payment, education, skills, language, and previous work experience (to be picked up in v2 for supporting training, staffing, attendance, and payment use cases in the future).

\


[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
