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

<figure><img src="../../.gitbook/assets/Screenshot 2023-03-20 at 1.43.08 PM.png" alt=""><figcaption></figcaption></figure>

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

\


