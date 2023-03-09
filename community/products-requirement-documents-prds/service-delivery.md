# Service Delivery

## Table of Contents

Background

Target Audience

Objectives (of this release)

Assumptions and Validations

Out of Scope

Specifications

Design

Success Criteria

Metrics to Track

## Background

This document describes the need and scope of a digital platform for health campaigns, explaining the product’s features, specifications, purpose, and functionality. It also provides an overview of the application.

The module aims to reduce the risks of data redundancy, provide better service delivery tracking and visibility of the services provided for maximum area coverage in the quickest time possible. It focuses on the design and features of the user interface of the Health Campaign Management (HCM) Platform for service delivery to households or individuals. The document also describes the elements and the process flow of the application along with a wireframe model for easy comprehension.

## Target Audience

The document is intended for the engineering and platform (tech teams), product management, and implementation teams to agree on the requirements for the platform.

Objectives (of this release)

1. Enabling actors with a digital system to manage and implement health campaign activities.&#x20;

* Facilitate FLWs, supervisors, district officers, and other actors to collect and analyse data accurately, along with monitoring the tasks from registration to service delivery. Regular progress checks can be performed at any time and a comparative analysis can be derived at the district levels for different teams.&#x20;
* Facilitate better diagnostics with improved access to healthcare interventions for the general public.

2. Enabling adoption of the HCM platform for multiple health campaigns by providing flexibility in the UI and UX as well as product specifications.

* Emphasis on adopting digital systems by collaborating with several healthcare bodies.
* Provide scope for future changes and improvements in the application.

## Assumptions and Validations

| Theme                | Assumption                                                                                                                                                                                                                                                                                                                                   |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Customer persona     | <ul><li>The actors using the application are not digitally literate and need training before they can use the application independently.</li></ul>                                                                                                                                                                                           |
| Device and services  | <ul><li>The actors have a smartphone and there should be internet connectivity to enable syncing of data from the mobile application to the server for populating the dashboards.</li><li>The actors using the mobile application must sync at least once daily.</li><li>Logging into the application needs internet connectivity.</li></ul> |
| Deliver intervention | <ul><li>The user will be able to add delivery details only after registering a household. </li><li>The option to deliver an intervention must be provided either to the household (in case of a household-based campaign) or to an individual (for an individual-based campaign) and must be configured during system setup.</li></ul>       |
| Peer-to-peer sync    | <ul><li>For v1.0, the product will not support peer-to-peer sync, either by directly syncing phones or routing traffic through the server.</li></ul>                                                                                                                                                                                         |
| Location picker      | <ul><li>The user must select at least the highest boundary to proceed with the registration and delivery.</li></ul>                                                                                                                                                                                                                          |
| Additional fields    | <ul><li>All the non-mandatory fields must be taken care of during implementation. This must be done across all the flows.</li></ul>                                                                                                                                                                                                          |
| Dropdown             | <ul><li>If the field contains only one value, then it must be auto-populated by the system.</li></ul>                                                                                                                                                                                                                                        |

## Risk/Limitations

Addressed in the out-of-scope section.

## Out of scope

* Search and view beneficiaries on the map based on proximity.
* Filter and sort beneficiaries.
* Generate QR codes for registered beneficiaries.
* View payments due for services delivered.

## Specifications

| Field name             | Data type                     | Data validation                       | Required (Y/N) | Comments                                                                              |   |
| ---------------------- | ----------------------------- | ------------------------------------- | -------------- | ------------------------------------------------------------------------------------- | - |
| Location picker        | Dropdown                      | Select at least the highest boundary. | Y              | The area boundary assigned to a specific user.                                        |   |
| Search for a household | String                        | Search by the household head.         | Y              | After two characters, it will start showing related search results.                   |   |
| Resource delivered     | Dropdown                      | NA                                    | Y              | Resource to be delivered in the campaign.                                             |   |
| Quantity distributed   | Numeric; increment/ decrement | NA                                    | Y              | Quantity of the resources distributed. It is defaulted to 1, but can be reduced to 0. |   |
| Delivery comment       | Dropdown                      | NA                                    | N              | Select any comment/reason from the dropdown.                                          |   |

## Design

Find the mock ups below:

### HCM Home screen

After logging into the application, the user lands on this screen which displays daily performance (the number of households registered). The progress bar must reset daily at 00:00 hours and start from 0 registration. The action buttons related to the beneficiary are present, which include:

* Beneficiaries
* View Reports
* Sync Data
* Call Supervisor
* File Complaint

At the bottom, there is a card that shows how many records are unsynced for the user’s convenience to sync data. If all the records are synced, then the card must say, “All records are synced”.

The help button is on every screen of the application. By clicking on this button, a user can get a walkthrough of the elements on that screen. On the top right, the administrative area assigned to the user is displayed which will be based on the level of hierarchy. The hamburger button on the top left corner covers other actions.

<figure><img src="../../.gitbook/assets/Screenshot 2023-03-09 at 10.59.24 AM.png" alt=""><figcaption></figcaption></figure>

### Hamburger Menu

After clicking on the hamburger button, a list of actions appears on the user screen. On top, it displays the user name and contact number, followed by other options such as the home button, language select, edit profile, projects, and logout. The “Edit Profile” option is not in scope for V1, it needs to be taken in V1.1.

If the user clicks on the hamburger button again, it collapses the hamburger menu. The button is available on all screens of the application.

<figure><img src="../../.gitbook/assets/Screenshot 2023-03-09 at 11.00.54 AM.png" alt=""><figcaption></figcaption></figure>

### Edit Profile

The user can edit his/her name, phone number, and select the gender. After updating the details, the user needs to click on the save button which opens a prompt stating “saved successfully”.&#x20;

If the user does not want to make any changes, he/she can click on the back button which will take him/her back to the hamburger menu. This is not in scope for V1.0; it needs to be taken up in V1.1.

<figure><img src="../../.gitbook/assets/Screenshot 2023-03-09 at 11.01.44 AM.png" alt=""><figcaption></figcaption></figure>

### Project Selection

When a user clicks on the projects option in the hamburger menu, it navigates them to the project selection screen from where the user can select another project to work on.

Though the automatic sync is triggered by the login action, after selecting another project, the system must now sync the data for the new project, and the same flow must be followed.

<figure><img src="../../.gitbook/assets/Screenshot 2023-03-09 at 11.02.29 AM.png" alt=""><figcaption></figcaption></figure>

### Location

For a user assigned multiple boundaries, after logging in, the boundary selection overlay must appear. This forces the user to select a boundary only after which the user can view the home screen. The user can then change the boundary whenever required from the location picker placed at the top right. It has dropdown fields to select the boundary, which depends upon the hierarchy level of the user. For an FLW, the boundary selection starts from the administrative post. The values in the dropdown are linked to the higher hierarchy and the user cannot select a boundary if the previous field is left blank.

<figure><img src="../../.gitbook/assets/Screenshot 2023-03-09 at 11.04.29 AM.png" alt=""><figcaption></figcaption></figure>

The dropdown must only consist of the boundaries which are assigned to the user, not all the boundaries under a particular hierarchy. For example, if the user is assigned localities 1, 2, and 3, and there are a total of 5 localities under admin post 1, then the dropdown must have only 1, 2, and 3 localities. The highest boundary must at least be selected to enable the select button which navigates the user to the home screen. For multiple projects, the sync needs to download the data only for the selected project.

<figure><img src="../../.gitbook/assets/Screenshot 2023-03-09 at 11.05.10 AM.png" alt=""><figcaption></figcaption></figure>

### Help Button

If the user clicks on the help button, it will give a walkthrough of the entire screen, including the role of each button placed with two buttons:

* Skip: If the user wants to skip the walkthrough at any point.
* Next: It will proceed to the next action aligned.&#x20;

The text box appears at the bottom of the button.

<figure><img src="../../.gitbook/assets/Screenshot 2023-03-09 at 11.06.17 AM.png" alt=""><figcaption></figcaption></figure>

### Search Households

When a user clicks on the ‘Beneficiaries’ button, he/she will be navigated to this screen. It displays the number of households registered along with the number of bednets delivered in that administrative area. The register button is primarily disabled to ensure that the user performs the search action.

The search bar allows the user to search by the household head’s name, and the system provides the search results. The minimum string length to show results is 2 characters and the order of the results will be the last record displayed first.

Two cases can be generated:

1. No results are displayed.
2. The search results displayed do not match.

Both cases are discussed further. The ‘Back’ button on the top will navigate to the home screen.

When the user searches for a household, there can be two outcomes:

1. The list of households will appear as a search result. The user can then open the household card and proceed with service delivery.
2. No results appear. In this case, the user needs to register the household first, so that he/she can deliver the intervention. (Note: Refer to the [**beneficiary registration**](beneficiary-registration.md) PRD).



\
[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
