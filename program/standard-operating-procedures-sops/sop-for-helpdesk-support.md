---
description: DIGIT-HCM Pilot in Mozambique (Tete Province)
---

# SOP for Helpdesk Support

## Overview

The Ministry of Health is implementing the Health Campaign Management (DIGIT-HCM) platform in Mozambique with support from eGov and CHAI. A helpdesk has been proposed to receive, log, prioritise, assign, track, escalate and resolve hardware and software-related issues raised during the campaign which impede campaign operations. &#x20;

The helpdesk team will be based either in Maputo or Tete to ensure easier coordination with the provincial teams who are responsible for distribution. For resolving technical issues or queries in the DIGIT-HCM app, there will be 1-2 members from eGov based in Mozambique to support the helpdesk staff. eGov will also set up a remote support team    (also called as L3 support), located in Bangalore, to resolve issues that the local helpdesk is unable to resolve.&#x20;

As it will be a limited duration (i.e. 3-5 days) campaign, the helpdesk will become operational 1-2 days before the start of the actual bed net distribution activities and will remain operational for 1-2 after the distribution. The help desk will operate between 6.00 am till midnight( 12.00 am) Mozambique time(CAT) and a roster needs to be maintained for the entire duration both for the local team( Layer 2 support in Mozambique) as well as remote support team( Layer 3 team based in Bangalore).

#### Scope of the helpdesk

* Technical support on hardware and software (for Salama - DIGIT HCM app only).
* Resolution of general how-to queries relating to the HCM app with the help of a FAQ document that may arise from the field.
* User management : Creation of the users and helping them with passwords&#x20;
* Master data management : Updates to Master data if the list of villages                changes during the campaign.

Examples of the queries to be handled by the helpdesk :&#x20;

1. Issues with the application or the dashboard functioning
2. Login or password not working or forgotten
3. Creating new users, if any due to field staff getting changed during the campaign.
4. Updating new localities or villages in the system during the campaign.

#### Out of scope of helpdesk

Resolving operational or programmatic issues related to bed net distribution. The operational/programmatic queries received by the helpdesk will be redirected to NMCP officials (Ines).

Examples of Operational or programmatic queries (to be routed to NMCP):

1. Not having sufficient stock of bed nets
2. Not receiving the device or any loss of device in the field
3. Bed net quality issues
4. Logistic issues related to the distribution of bed nets
5. Any issues relating to the bed net distribution process as outlined by the NMCP

## Helpdesk Workflow

The typical lifecycle of a helpdesk ticket starts when an issue is received and ends when a ticket gets closed. The below representation shows how the helpdesk ticketing management system will work. In this representation :&#x20;

The Whatsapp groups of registrars, LMs and District supervisors will play the role of L1.

Central helpdesk will play the role of L2

eGov tech team (India) will play the role of L3&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-07 at 6.10.10 PM.png" alt=""><figcaption></figcaption></figure>

For the issues which are not related to scope of the helpdesk, Help desk team will redirect the issue (over call/ WhatsApp) to concerned NMCP officials(Ines) for further communication and resolution.&#x20;

#### Raising Tickets

The helpdesk staff will use the Grievance portal (Complaints Module) to record every incident or grievance that is reported to them. The help desk staff would be able to login with dedicated User ID and Password and log a complaint by raising a ticket against it. The login credentials will be generated from the backend and provided to the identified users.

## Support levels

| S.No. | Levels                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Who will respond to queries                                            |
| ----- | ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| 1     | <p>Level 1 </p><p>(L1 - Local support)</p> | <ul><li>Support provided by a local monitor, District supervisor or any member of the field staff for the general queries</li><li>In this level of support, the user can opt to do phone calls/WhatsApp. </li><li>All the requests may not be logged into the helpdesk portal as some queries may get directly answered by local monitors over phone or whatsapp.</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | <p>Local Monitors or</p><p>District supervisors</p>                    |
| 2     | Level 2 (L2 - Helpdesk team)               | <ul><li>Scope of the helpdesk formally starts at this level.</li><li>The issues that are not resolved by local monitors or District supervisors will be escalated to the helpdesk team via call or whatsapp messaging or by logging into the complaints tool.</li><li>At this level, issues will be triaged.  All technical queries will be assigned to the technical team (CHAI supported by eGov team). For all programmatic/process-related queries, the respective nodal officers part of the helpdesk team from NMCP/DIS/DTIC shall be contacted.</li><li>This will be staffed by 4 helpdesk executives positioned at the helpdesk. These executives will be from CHAI and supported by eGOv</li><li>This team will also be responsible for User provisioning (i.e. the creation of users) using the DIGIT-HCM’s user Management module during the campaign window.</li><li>In case of any master data changes during the campaign this team will create a request in the complaints module and share it with the L3 support team.</li></ul> | <p>CHAI(3-4 persons</p><p>lead by Frank) and</p><p>eGov( 1 person)</p> |
| 3     | Level 3 (L3 - India based eGov team)       | <ul><li>eGov team for resolving technical issues/queries that the L2 helpdesk team is not able to resolve.</li><li>Master data update requests (if any) during the campaign</li><li>Bulk user creation requests through backend APIs for the coded users   (who will be identified using a code or a serial number i.e. the registrars)</li><li>User creation requests before the campaign starts  for the named users (who will have their own ID and password)</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | eGov                                                                   |

## Modes Of Communication

#### Phone calls & Whatsapp messaging

It has been observed from the previous campaigns that users in the field (i.e. distribution teams) often reach out to Local Monitors (LMs) and District supervisors for simpler queries over a phone call or Whatsapp communication for quick resolution of their queries. This is deemed as the L1 support in this document. The district supervisors escalate more complex issues to the helpdesk team again, over phone calls or whatsapp group communication. Usually the provincial Focal Points create a whatsapp group during provincial ToTs and add the relevant members. The same approach would be followed for the Group4 campaign in Tete. When the issue gets escalated from District supervisors over a phone call or Whatsapp message, the Helpdesk team (L2 team) will record them in the Complaints Management tool.

| Reporter                              | Resolver                              | Communication channel                                                                                    |
| ------------------------------------- | ------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Field workers/distribution teams      | Local Monitor or District Supervisor  | Phone calls/Whatsapp                                                                                     |
| Local Monitor or District Supervisor  | Helpdesk(Layer 2) support             | <p>Phone call</p><p>or</p><p>Whatsapp group message</p><p>or </p><p>Logging in the Complaints Module</p> |
| Helpdesk(Layer 2) support             | Helpdesk (Layer 3) support            | Complaints Module/Emails                                                                                 |

## Tickets categories&#x20;

Following categories of incidents are envisaged to be logged at the helpdesk. Each incident category will have its independent process of resolution as defined in the SOP section of this document.

| # | Category            | Description                                                                                                                                             | Examples                                                                                                       |
| - | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| 1 | Technical query     | Any issues with the functioning of the Salama(DIGIT HCM) app or the hardware( device)                                                                   | <ul><li>App malfunction</li><li>Broken device</li><li>Sync errors</li><li>Battery issues</li></ul>             |
| 2 | User Account        | Any user management related issues because of which the users are not able to access the application or play the designated role mapped to their logins | <ul><li>login errors</li><li>Forgot username or password requests</li><li>Change of user categories </li></ul> |
| 3 | Data/content issues | Any issues pertaining to the master data that is loaded in the platform                                                                                 | <ul><li>Problem with form</li><li>Viewing other users' profiles</li><li>Viewing other users' records</li></ul> |
| 4 | Security Issue      | <p><br></p>                                                                                                                                             | <ul><li>Device stolen or lost</li></ul>                                                                        |
| 5 | Performance issue   | <p><br></p>                                                                                                                                             | <ul><li>Lack of network coverage in the region.</li></ul>                                                      |

Helpdesk Operating dates and timings

The helpdesk will be operational for the below mentioned duration.

Dates : 7-Aug-23 till 14-Aug-23

Mozambique: 6:00 AM – 12.00 AM CAT(Midnight)

India: 9:30AM – 03:30 AM IST

## Ticket Tracking and Response Times

The primary goal of the helpdesk is to restore normal operations at the earliest possible, and with a minimum impact.&#x20;

Critical app-related issues that cannot be resolved within the campaign duration will be shared with eGov which will be picked up immediately after the campaign for the second round of pilot in Group V.&#x20;

Enhancements (major and minor) will go through a change request process. Due to the nature of the project, there will be no feature updates to the DIGIT system during the campaign period. Also any updates to the HCM application during the campaign window  will be avoided as far as possible because it may be difficult to push the updates to all the devices and there may be data loss due to the same.&#x20;

#### Updation in Jira

Since the Jira tickets are getting created automatically from the complaints module, the L3 staff at the eGov end should triage the ticket and update the severity appropriately.

### Tools for the helpdesk team

What do they need to be effective?

* FAQ on issues commonly-faced
* User manual on the Salama (DIGIT HCM) app.&#x20;
* User manual on complaints portal & user management

## Help Desk Team Composition&#x20;

The helpdesk team will have following composition:

| Support level | Name of support lead | Name of other members from CHAI | eGov team members                       |
| ------------- | -------------------- | ------------------------------- | --------------------------------------- |
| L2            | Frank                | <p><br></p>                     | Velkur Saiprakash                       |
| L3            | Prasanna             | <ul><li>NA -</li></ul>          | Vishal, Saiprakash, Ajay, Tumul, Swathi |
