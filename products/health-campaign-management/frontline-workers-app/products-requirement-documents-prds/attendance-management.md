# Attendance Management

## Table of Contents

[Background](attendance-management.md#background)

[Target Audience](attendance-management.md#target-audience)

[Objectives](attendance-management.md#objectives)

[Assumptions and Validations](attendance-management.md#assumptions-and-validations)

[Process Flow](attendance-management.md#process-flow-diagrams)

[Solution](attendance-management.md#solution)

[Specifications](attendance-management.md#specifications)

[Risk and Limitation](attendance-management.md#risk-and-limitations)

[Out of Scope](attendance-management.md#out-of-scope-for-v1.3)

[Design](attendance-management.md#design)

## Background

This document describes the need and scope of adding an Attendance Management module  within v1.3, explaining the module’s features, specifications, purpose, and functionality. It also provides a descriptive view of the application along with the specification of each element.

#### About

The ability for supervisors to mark the attendance of field workers at the time of training or drug distribution for their respective teams through their user interface.

#### Problem

1. **Inaccuracy of records:** Attendance is being captured on paper, which has a possibility of being lost creating inaccuracy of attendance records, making the wage calculation for each worker inaccurate as well.
2. **Data fraud:** The data being recorded in the current format can be tampered with or changed easily, creating inauthentic records and eventually incorrect payments to the field workers.

**Impact**

If the attendance records of the workers in a given campaign are inaccurate, the final wage payment for these workers will also be inaccurate. There could be cases where workers, who are owed more, are paid less and vice versa.

## Target Audience

This document is intended for the engineering and platform (tech teams), product management and implementation teams to agree on the requirements for the attendance feature on the Health Campaign Management Platform (HCM).

## Objectives

1. Attendance management: Enabling supervisors to capture attendance on the Health Campaign Management Platform. Capture attendance for multiple sessions, if needed, based on the way the campaign is structured
2. Enhance user experience: Simplified forms for capturing referral information and ensure authenticity of data at the time of attendance.

## Assumptions and Validations

| Theme                                 | Assumptions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Attendance register creation/updation | <ul><li>This will be done by the system administrator, and each register will have a unique set of staff.</li><li>Only the staff who are created in the system and linked to a project and a supervisor must be listed in the attendance registers (default configuration in product). This implies that if a new staff is to be added, the system admin must create a new user in the HRMS and then assign projects and reporting supervisors in the project after which the new staff will reflect in the supervisors attendance register.</li><li>If a staff is removed from the supervisors reporting or from a project (project supersedes reporting hierarchy), then the name of the staff must be removed from the register and reflect after down-sync (users can be a staff for multiple projects and have multiple supervisors).</li></ul> |
| Recording attendance for staff        | <ul><li>Based on the type of attendance set for a campaign, supervisors can record attendance as follows: </li></ul><p>       - If the attendance is done once a day, the supervisor can record 3 responses, that is,  full day, half day, and absent. </p><p>       - If the attendance is done twice a day, the supervisor will have only two options for marking attendance, that is, present and absent in each recording.</p>                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Saving attendance for staff           | <ul><li>The HCM mobile app will validate statuses during submission and will not allow submission of any register having a staff with the "Not Marked" status.</li><li>The attendance entries, once submitted, will not be allowed to change by the supervisor. If there are any edits needed, a separate request needs to be raised to the system admin.</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

## Role Action Mapping

1. **System Administrator:**&#x20;
   * Configure all attendance registers, and map the correct staff to their respective supervisors.&#x20;
   * Execute edit requests from the backend which are raised by supervisors who have marked incorrect attendance.
2. **Supervisor:**
   * Supervisors must be able to down sync attendance registers after login, and collect the attendance data while offline, which will be automatically or manually synced once internet connection is available.
   * View attendance registers of only the staff mapped to them.&#x20;
   * Mark and save attendance registers on a daily basis.
   * View the attendance marked for previous campaign dates while the campaign is active. Once the campaign is over. the supervisors will not be able to view or change any entries made for previous days.

## Process Flow Diagrams&#x20;

## **Solution**:&#x20;

High-Level Scope:

* The aim is to digitalise the flow for recording attendance and reduce inaccuracies/inconsistencies in the attendance data being captured by the supervisors during a campaign.&#x20;
* The attendance registers for staff working in the campaign will be created by a combination of the project and supervisor assigned to a given staff member.
* Supervisors will be able to down sync attendance registers and role-access mapping after they login. They can collect the attendance data while offline, which will be automatically or manually synced once internet connection is available.
* Supervisors from other projects must not be able to view the attendance registers for a different project.
* The product will come with a default configuration of marking attendance twice a day, once in the morning and once in the evening, which will allow the supervisor to mark the attendance as absent/present.&#x20;
* If the programme plans to conduct attendance only once a day, then the product can be configured to capture present, absent, and half day as attendance records for a given staff member.
* The system admin must be able to edit the submitted attendance from the backend if required. Validation is needed to check the role of the user before the system admin can update the attendance from the backend even after the campaign is completed.

## Specifications

Select Session:

| Field             | Data type    | Data Validation                                  | Required | Comments         |
| ----------------- | ------------ | ------------------------------------------------ | -------- | ---------------- |
| Date of session   | Date type    | Only today’s date and past dates can be entered. | Yes      | Must be editable |
| Session selection | Radio button | Only morning or evening can be selected at once. | Yes      | Must be editable |

Mark Attendance:

| Field                    | Data type        | Data Validation                                                                                 | Required | Comments                       |
| ------------------------ | ---------------- | ----------------------------------------------------------------------------------------------- | -------- | ------------------------------ |
| Search by name/ID number | String           | Can add alpha-numeric characters to search by name or the ID number.                            | Yes      | Must be editable               |
| Attendance               | Multi-tap button | Can be set to present/absent/half day based on how the the programme team sets up the campaign. | Yes      | Must be editable before saving |

## Risk and Limitations

Due to the existing design, the system cannot support the following use cases:

1. Saving marked attendance as draft: When a supervisor marks the attendance for a set of staff members, the supervisor cannot leave any user unmarked. This will force the supervisor to wait for everyone to be present at the time of attendance and only then cam save the attendance. The supervisor cannot come back to the sheet again to update/mark new attendances on the sheet.
2. Sorting on the basis of the attendance status: For supervisors who want to view the attendance register on the basis of the status of attendance - to focus on a particular set of records in the register - is not available in the current edition of the application.

## Out of Scope&#x20;

1. Editing submitted attendance in the HCM mobile app (to be enabled in future versions).
2. UI to create attendance registers and configure muster roll generation and reports.

## Design

Find the mock-ups below:

### Home screen

Once the supervisor has synced the project data from the server, based on the role action mapping assigned to them, the home screen will have the "Attendance Management" tab.

![](https://lh7-us.googleusercontent.com/qJsjkz918Qak9QGQ2TkAmIX4ifSrwSxnrwujjvb\_LSFL5ucz9f3fMNcjmuOPZzPGGpgPVSD6SaAC3s0o8yyqBL-4qoM9S3BO1trhG4NyF6KlX4tNP8Xm7vMp7P-NdD1wBiD-FdI8p8SQ6NxkVU-G0Lg)

### Manage Attendance screen

This screen will have all the attendance register mapped to that specific supervisor.

<img src="https://lh7-us.googleusercontent.com/SN5GEpDqoJS88w3J7aXEQImu7IbG9-yrJEs8kN39DN5qBZcZFVv8iwTaEk7kDcqSh9C2fKW7x0RLo-J4dfbuhzQPpl9OTjUeARCfkW9RuddYLnk4GhRxtXGoudDQ5-ku6TdK-u2fM_zFbMJNRJK2GSw" alt="" data-size="original">

### Date and Session Selection Screen

On this screen, the supervisor can select the date and session for which they want to mark the attendance for a given attendance register. The missed attendance information box will notify the supervisor if they have missed marking attendance on any of the previous days of the selected campaign.

![](https://lh7-us.googleusercontent.com/3mOcXICAaqr1oqwaSfind9-4lA2NmPIWIOok\_xRd-EAvZv3pD5oP8k7\_eRF0MLi1MBrWYjMDNXUeGSc2TZHzIcaJALoHF9eb6RxbrNWcXvpH1PDVpMp-JABdsVTJtsW6jOuD3BNo7HVCC0wW\_RuN6as)

### Attendance Details Screen

This screen will allow the supervisor to mark attendance for the staff Members mapped to them.

![](https://lh7-us.googleusercontent.com/dhfbkbjymLogTmp83nHSZIHVS\_NETUYPaROxETsbt\_vVeaUKpLkFvtSwfqAgtHx-QpMLcI-SFv2\_6TMj2fXUylTjo3az73Q\_t4KD\_v4Gmrz\_Wx107WcfOnQqwNlLWkoa6pL4qoGr8kfDSl9tNt8tRXc)

### Ready to Submit Screen

On this screen, the supervisor can make the submission of the attendance data for the selected session.

![](https://lh7-us.googleusercontent.com/DNP\_3DjATSUM9LvkRHC5uBJflHAbEWki0W6SJfQIUbPQY30qn5vX32iKWR\_J5SzCzPkWZ0MymJHgxZwSt2Mt5NVLEobPz3si8qcJsKzstYlo8pZOVg592gy2LHTcwVxClXsD4fjTShAl06\_a88p-Ux0)

### Confirmation Screen

This screen will be shown if the attendance data submitted by the supervisor was saved successfully.

![](https://lh7-us.googleusercontent.com/t5hdAB9AoaWKdS7wuQeTaz9dZqpMWVszfDSC4hGOofpIPIfA6YLz\_44I58KejjPlc-QGDHANAOk8TZxhIjWBD7e\_yO9VFFb4j1tEH27HZwKyC\_SIkyvp\_Ka5DYGg3CWGzn6D85RQFYGlhcpiiujwO6o)
