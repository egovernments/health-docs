# User Login

## Table of Contents

Background

Target Audience&#x20;

Objectives (of this release)

Assumptions and Validations&#x20;

Process Flow

Out of scope&#x20;

Specifications&#x20;

Design&#x20;

Success Criteria&#x20;

Metrics to track

## Background

This document describes the need and scope of a digital platform for health campaigns, explaining the product’s features, specifications, purpose, and functionality. It also provides a descriptive view of the application along with the specification of each element.

The module focuses on the design and features of the user interface of HCM for beneficiary registration and service delivery. It provides a detailed description of the elements and the process flow of the application along with a wireframe model for easier comprehension. The module also aims to reduce the risks of data redundancy, provide better service delivery tracking, and visibility of the services provided for maximum coverage in the quickest time possible

## Target Audience&#x20;

The document is intended for the engineering and platform (tech teams), product management, and implementation teams to agree on requirements for the Health Campaign Management (HCM) Platform.

## Objectives (of this release)

1\. To enable actors with a digital system to manage and implement health campaign activities.&#x20;

a. Facilitate FLWs, supervisors, district officers, and other actors to collect and analyse data accurately, along with monitoring the tasks from registration to service delivery. Regular progress checks can be performed at any time and a comparative analysis can be derived at the district levels for different teams.&#x20;

b. Facilitate better diagnostics with improved access to healthcare interventions for the general public.&#x20;

2\. To enhance the adoption of the HCM platform for multiple health campaigns by providing flexibility in the UI and UX, and product specifications.&#x20;

a. Emphasis on adopting digital systems by collaborating with healthcare bodies.&#x20;

b. Provide scope for future changes and improvements in the application.

## Assumptions and Validations

| Theme               | Assumption                                                                                                                                                                                                                                                                                                                                   |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Customer persona    | <ul><li>The actors using the application are not digitally literate and need training before being able to use the application independently.</li></ul>                                                                                                                                                                                      |
| Device and services | <ul><li>The actors have a smartphone and there should be internet connectivity to enable syncing of data from the mobile. application to the server for populating the dashboards.</li><li>The actors using the mobile application must sync at least once daily.</li><li>Logging into the application needs internet connectivity</li></ul> |
| Peer-to-peer sync   | For v1.0, the product will not support peer-to-peer sync, either by directly syncing phones or routing traffic through the server.                                                                                                                                                                                                           |
| User login          | <ul><li>The system-generated user ID and password must be provided to the user for login.</li><li>The user needs to login daily before going to the field and log out after coming back from the field.</li></ul>                                                                                                                            |

## Process flow

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.43.08 PM.png" alt=""><figcaption></figcaption></figure>

## Risk/ Limitations&#x20;

Addressed in the out of scope section.

## Out of scope

* Password reset for the users.
* User capability of resetting the password if they forget it.
* User capability of creating own user ID for login.

Specifications

| Field            | Data type                     | Data validation             | Required (Y/N) | Comments                                                                 |
| ---------------- | ----------------------------- | --------------------------- | -------------- | ------------------------------------------------------------------------ |
| Language         | Choose from the given options | Need to select one language | Y              | Select the language for the application.                                 |
| User ID          | String                        | NA                          | Y              | The unique system-generated ID.                                          |
| Password         | Alphanumeric                  | NA                          | Y              | The unique system-generated password                                     |
| New password     | Alphanumeric                  | NA                          | Y              | After the first login, a user needs to create a new password (V1.1).     |
| Confirm password | Alphanumeric                  | NA                          | Y              | Confirm the new password (V1.1).                                         |
| Project          | Choose from the given options | Need to select one language | Y              | This is the project selection page for users assigned multiple projects. |

## Design

Find the mock-ups below:

### Language Select

When the user opens the application, it asks them to first select the language. The selected language is highlighted in orange color. Once the user selects a language, he/she must click on the ‘Continue’ button which opens the login page.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.51.35 PM.png" alt=""><figcaption></figcaption></figure>

### Login

The user will be provided a unique system-generated ID and password manually for first-time login. After logging in, the user is taken to the password reset page where they need to enter a new password of their choice. The password reset is not in scope for V1.0. If a user enters an incorrect username, it should show an error message below the field saying “username does not match”. For an incorrect password, it should show the message “incorrect password” below the password field.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.53.16 PM.png" alt=""><figcaption></figcaption></figure>

If an existing user does not remember his/her password, they must click on “Forgot Password”. This will open a popup asking the user to contact the administrator. The ‘OK’ button will collapse the popup.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.53.24 PM.png" alt=""><figcaption></figcaption></figure>

### Reset Password (Not in V1.0)

After the user logs in for the first time, a screen appears where he/she needs to create a new password. There are two fields, “Enter new password” and “Confirm password”, with the eye button present in both.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.55.04 PM.png" alt=""><figcaption></figcaption></figure>

After entering and reviewing the new password, the user clicks on the submit button which opens a screen with the message “New password created successfully” along with a “Back to Login” button below the text. Clicking on this button will take the user back to the login page. The password reset flow is not in scope for V1.0.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.55.12 PM.png" alt=""><figcaption></figcaption></figure>

### Project Selection

If the user is assigned to multiple projects, they need to select a particular project on this page by clicking on the arrow in front of each project name. Once the user has selected a project, it will open the application’s home page. After selecting a project, the system must download the data for the selected project only. For single-project users, the sync action takes place directly after the login action. There can be multiple cases for projects assigned to a user:

* If the user is assigned 0 projects, an overlay must appear saying “Please contact the system administrator for a project”  after logging in, and the user must log out of the application.
* If the user is assigned multiple projects as mentioned above.
* If the user has been assigned a project but later the project has been unassigned. In this case, if the user logs in and selects that project, an error message must appear stating “the project is not assigned to you, please select another project”. When the user clicks on the ‘OK’ button, he/she must be navigated to the updated project selection screen which must not display the unassigned project.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.56.50 PM.png" alt=""><figcaption></figcaption></figure>

### Sync

After every login action, the system will automatically sync the data with the system. Since the user will log in only at the start of the day and before going into the field, there must be stable internet connectivity for the device to perform this process. A “Sync in Progress” window will appear on the screen and the user cannot perform any other action until the process is complete.&#x20;

The overlay will appear over the previous screen. For users assigned to multiple projects, the overlay appears over the project selection screen when the user selects one project from the list.  For single-project users, the overlay must appear over the login page.

### Sync Status

Once the data is synced, it will show a popup that the data is successfully synced, with a ‘Close’ button at the bottom. When the user clicks on this button, it will navigate him/her to the homepage. These overlays also appear over the previous screens.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 2.01.10 PM.png" alt=""><figcaption></figcaption></figure>

If the data is not synced due to an error, it will show a popup stating “Sync Failed” with two buttons below it:

1. Retry: If the user wants to retry syncing the data. This will open the sync in progress window.
2. Close: Clicking on this will navigate the user back to the login page and he/she is required to log in again.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 2.01.17 PM.png" alt=""><figcaption></figcaption></figure>

## Success criteria

1. Various actors involved in the process will be able to collect, track, and analyse the data for beneficiaries registered as well as services delivered to them using a bug-free platform.
2. The supervisors, district officers, and program managers will be able to monitor the team’s performance which will help them understand the problems and challenges faced.&#x20;
3. Enable warehouse managers to optimise the inventory management of interventions which will further improve the supply chain and prevent surplus or deficit of stock. This includes stock receipts, issues, returns, and lateral movements of the stock.&#x20;
4. Digital records will result in maximum coverage with less chances of households being missed during a campaign.

## Metrics to track

The following metrics that will be tracked:

1. Number of logins by a user.
2. User ID and password of the users.
3. Number of password reset requests.
