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

\
[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
