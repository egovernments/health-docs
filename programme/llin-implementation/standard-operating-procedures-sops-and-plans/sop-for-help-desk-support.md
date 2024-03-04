---
description: DIGIT-HCM Pilot in Mozambique (Tete Province)
---

# SOP for Help desk Support

## Overview

The Ministry of Health is implementing the Health Campaign Management (DIGIT-HCM) platform in Mozambique with support from eGovernment's Foundation (eGov) and the Clinton Health Access Initiative (CHAI). A help desk has been proposed to receive, log, prioritise, assign, track, escalate and resolve hardware and software-related issues raised during the campaign which impede campaign operations. &#x20;

The help desk team will be based either in Maputo or Tete to ensure easier coordination with the provincial teams who are responsible for distribution. For resolving technical issues or queries in the DIGIT-HCM app, there will be one to two members from eGov based in Mozambique to support the help desk staff. eGov will also set up a remote support team (also called as L3 support), located in Bangalore, to resolve issues that the local help desk is unable to resolve.&#x20;

As it will be a limited duration (that is, 3-5 days) campaign, the help desk will become operational 1-2 days before the start of the actual bed net distribution activities and will remain operational for 1-2 days after the distribution. The help desk will operate between 6.00 am and midnight (12.00 am) Mozambique time (CAT). A roster should be maintained for the entire duration, both for the local team (layer 2 support in Mozambique) as well as the remote support team (layer 3 team based in Bangalore).

#### Scope of the help desk

* Technical support on hardware and software (for Salama - DIGIT HCM app only).
* Resolution of general how-to queries relating to the HCM app with the help of an FAQ document that may arise from the field.
* User management: Creation of the users and helping them with passwords.&#x20;
* Master data management: Updates to the master data if the list of villages changes during the campaign.

Examples of the queries to be handled by the help desk:&#x20;

1. Issues with the application or the dashboard functioning.
2. Login or password not working or forgotten.
3. Creating new users, if any, due to field staff getting changed during the campaign.
4. Updating new localities or villages in the system during the campaign.

#### Out-of-scope for the help desk

Resolving operational or programmatic issues related to bed net distribution: The operational/programmatic queries received by the help desk will be redirected to NMCP officials (Ines).

Examples of operational or programmatic queries (to be routed to NMCP):

1. Not having sufficient stock of bed nets.
2. Not receiving the device or any loss of the device in the field.
3. Bed net quality issues.
4. Logistic issues related to the distribution of bed nets.
5. Any issues relating to the bed net distribution process as outlined by the NMCP.

## Help desk Workflow

The typical lifecycle of a help desk ticket starts when an issue is received, and ends when a ticket gets closed. The below representation shows how the help desk ticketing management system will work:

The WhatsApp groups of registrars, local monitors (LMs), and district supervisors will play the role of L1.

The central help desk will play the role of L2.

eGov tech team (India) will play the role of L3.&#x20;

<figure><img src="../../../.gitbook/assets/Screenshot 2023-06-07 at 6.10.10 PM.png" alt=""><figcaption></figcaption></figure>

For issues that are not related to the scope of the help desk, the help desk team will redirect the issue (over call/WhatsApp) to the concerned NMCP official (Ines) for further communication and resolution.&#x20;

#### Raising Tickets

The help desk staff will use the grievance portal (Complaints Module) to record every incident or grievance that is reported to them. The help desk staff will be able to log in with a dedicated user ID and password and log a complaint by raising a ticket against it. The login credentials will be generated from the backend and provided to the identified users.

## Support Levels

| S.No. | Levels                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Who will respond to queries                                              |
| ----- | ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| 1     | <p>Level 1 </p><p>(L1 - Local support)</p> | <ul><li>Support provided by a local monitor, district supervisor or any member of the field staff for general queries.</li><li>In this level of support, the user can opt to do phone calls/WhatsApp. </li><li>All the requests may not be logged into the help desk portal as some queries may get directly answered by local monitors over phone or WhatsApp.</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | <p>Local monitors or</p><p>district supervisors.</p>                     |
| 2     | Level 2 (L2 - Help desk team)              | <ul><li>Scope of the help desk formally starts at this level.</li><li>The issues that are not resolved by local monitors or district supervisors will be escalated to the help desk team via call or WhatsApp messaging or by logging into the complaints tool.</li><li>At this level, issues will be triaged. All technical queries will be assigned to the technical team (CHAI supported by eGov team). For all programmatic or process-related queries, the respective nodal officers, part of the help desk team from NMCP/DIS/DTIC, will be contacted.</li><li>This will be staffed by four help desk executives positioned at the help desk. These executives will be from CHAI and supported by eGov.</li><li>This team will also be responsible for user provisioning (that is, the creation of users) using the DIGIT-HCM’s user management module during the campaign window.</li><li>In case of any master data changes during the campaign, this team will create a request in the complaints module and share it with the L3 support team.</li></ul> | <p>CHAI (3-4 persons</p><p>lead by Frank) and</p><p>eGov (1 person).</p> |
| 3     | Level 3 (L3 - India based eGov team)       | <ul><li>eGov team for resolving technical issues/queries that the L2 help desk team is not able to resolve.</li><li>Master data update requests (if any) during the campaign.</li><li>Bulk user creation requests through backend APIs for coded users   (who will be identified using a code or a serial number, that is, the registrars).</li><li>User creation requests before the campaign starts  for the named users (who will have their own ID and password).</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | eGov                                                                     |

## Modes of Communication

#### Phone calls & WhatsApp messaging

It has been observed from previous campaigns that users in the field (that is, distribution teams) often reach out to local monitors (LMs) and district supervisors for simpler queries over a phone call or WhatsApp communication for quick resolution of their queries. This is deemed as the L1 support in this document. The district supervisors escalate more complex issues to the help desk team again, over phone calls or WhatsApp group communication. Usually, the provincial focal points, create a WhatsApp group during provincial ToTs and add the relevant members. The same approach would be followed for the Group 4 campaign in Tete. When the issue gets escalated from district supervisors over a phone call or WhatsApp message, the help desk team (L2 team) will record them in the complaints management tool.

| Reporter                              | Resolver                              | Communication channel                                                                     |
| ------------------------------------- | ------------------------------------- | ----------------------------------------------------------------------------------------- |
| Field workers/distribution teams      | Local monitor or district supervisor  | Phone calls/WhatsApp                                                                      |
| Local monitor or district supervisor  | Help desk (layer 2) support           | <p>Phone call or WhatsApp group message or </p><p>logging in to the complaints module</p> |
| Help desk (Layer 2) support           | Help desk (layer 3) support           | Complaints module/emails                                                                  |

## Tickets Categories&#x20;

The following categories of incidents are envisaged to be logged at the help desk. Each incident category will have its independent process of resolution as defined in the SOP section of this document.

| # | Category            | Description                                                                                                                                              | Examples                                                                                                       |
| - | ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| 1 | Technical query     | Any issues with the functioning of the Salama (DIGIT HCM) app or the hardware (device).                                                                  | <ul><li>App malfunction</li><li>Broken device</li><li>Sync errors</li><li>Battery issues</li></ul>             |
| 2 | User account        | Any user management-related issues because of which the users are not able to access the application or play the designated role mapped to their logins. | <ul><li>Login errors</li><li>Forgot username or password requests</li><li>Change of user categories </li></ul> |
| 3 | Data/content issues | Any issues pertaining to the master data that is loaded in the platform.                                                                                 | <ul><li>Problem with form</li><li>Viewing other users' profiles</li><li>Viewing other users' records</li></ul> |
| 4 | Security issue      | <p><br></p>                                                                                                                                              | <ul><li>Device stolen or lost</li></ul>                                                                        |
| 5 | Performance issue   | <p><br></p>                                                                                                                                              | <ul><li>Lack of network coverage in the region</li></ul>                                                       |

#### Help desk operating dates and timings

The help desk will be operational for the below-mentioned duration:&#x20;

Dates: 7-Aug-23 to 14-Aug-23

Mozambique: 6:00 AM – 12.00 AM CAT (midnight)

India: 9:30 AM – 03:30 AM IST

## Ticket Tracking and Response Times

The primary goal of the help desk is to restore normal operations at the earliest possible, and with minimum impact.&#x20;

Critical app-related issues that cannot be resolved within the campaign duration will be shared with eGov, which will be picked up immediately after the campaign for the second round of pilot in Group V.&#x20;

Enhancements (major and minor) will go through a change request process. Due to the nature of the project, there will be no feature updates to the DIGIT system during the campaign period. Any updates to the HCM application during the campaign window will be avoided as far as possible because it may be difficult to push the updates to all the devices and there may be data loss due to the same.&#x20;

#### Updation in Jira

Since the Jira tickets are getting created automatically from the complaints module, the L3 staff at eGov should triage the ticket and update the severity appropriately.

### Tools for the help desk team

What do they need to be effective?

* FAQ on issues commonly-faced.
* User manual on the Salama (DIGIT HCM) app.&#x20;
* User manual on complaints portal and user management.

## Help Desk Team Composition&#x20;

The help desk team will have the following composition:

| Support level | Name of support lead | Name of other members from CHAI | eGov team members                        |
| ------------- | -------------------- | ------------------------------- | ---------------------------------------- |
| L2            | Frank                | <p><br></p>                     | Velkur Sai Prakash                       |
| L3            | Prasanna             | <ul><li>NA -</li></ul>          | Vishal, Sai Prakash, Ajay, Tumul, Swathi |
