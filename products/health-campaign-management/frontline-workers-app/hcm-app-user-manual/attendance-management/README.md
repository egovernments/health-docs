---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Attendance Management

## **Overview**

This module helps in marking the attendance of the field users (referred to as attendees), who are supposed to work on the campaign till the campaign is live.

**ROLE: DISTRICT\_SUPERVISOR**

### **User actions**

This module has 3 associated screens:

1. Manage Attendance
2. Date and Session Selection
3. Mark Attendance

## **1. Manage Attendance**

Once the supervisor clicks on the “Manage Attendance” button, the supervisor is taken to the attendance registers mapped to them. The attendance registers are to be created manually, where the attendance register is created by taking a combination of the project, and the supervisor a staff member is mapped to it.

. <img src="https://lh7-us.googleusercontent.com/49dwF5hNZfYutpxfQqoaSwywfEpNSr_6d7tCThE5UerWeVMe-xxwikoVQRzXA0bXUo1FAXNuPt0-360naANEVkWOAmnDfVkwQWRRFKN0txG8fI3CSEtjQ8fJ9pdMZwNBhh9LDUuCrqEM2V5z_4lclU0" alt="" data-size="original">

### Data Field to Manage Attendance Screen:

| **Field**             | **Description**                                                                                                                                              |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Campaign Name         | Name of the campaign                                                                                                                                         |
| Event Type            | Type of event where attendance is done, that is training or distribution                                                                                     |
| Start date            | Start date of the campaign                                                                                                                                   |
| End date              | End date of the campaign                                                                                                                                     |
| Status                | If the end date is passed, the status will be inactive, or if the register status is inactive, the status will be inactive, else, the status will be active. |
| Staff count           | Number of attendees in the register.                                                                                                                         |
| Attendance Completion | Shows the number of days for which attendance has been submitted submitted to the server.                                                                    |

### Attendance Completion Days Logic:

1. Fetch all attendance logs for the register.
2. Based on the sessions configured for the register, check for the logs where the entry time and the exit time are equal to the start and the end time of the session.
3. For individuals who do not have logs are the same as the start and the end time will be by default marked as absent if any of the individuals' log is present for the register.

/`/generateDateList will return the map of completed attendance Dates.`

`list = generateDateList(`

&#x20;`e.attendanceRegister.startDate!,`

&#x20;`e.attendanceRegister.endDate!,`

&#x20;`registerCompletedLogs ?? [],`

&#x20;`e.attendanceRegister.additionalDetails?["sessions"] != 2,`

`);`

`var completedDaysCount =`

&#x20;  `e.attendanceRegister.additionalDetails?["sessions"] == 2`

&#x20;      `? list.length ~/ 2 //for registers with 2 sessions`

&#x20;`: list.length; ////for registers with single session`

## 2. Date and Session Selection

The date selection range commences from the start date of the attendance register and extends to the end date of the register or today's date if today falls before the end date of the register.

* If the attendance for a past day is already submitted, then the CTA must change to view attendance from mark attendance.

<img src="https://lh7-us.googleusercontent.com/eolzJ0PTKblHOu8S6FoSv1_GaNGudzQiNqPb3Vkh9wrNJ0F7dcWDtqMprNKGMIdvHwoi4Uelqy14Y0gk1Ock0iUo2yJDBTg7M9TWtueBMfwDIVpQOEQoQFnROG9Ctb1Di-5B2CEKeEdwXfATBLYf3m0" alt="" data-size="original">

### Missed Attendance Logic:&#x20;

Upon selecting the attendance register, a list of completed dates is generated. We iterate over the dates from the start date to the current date, checking for any missing dates in the list to identify missed attendance dates

## 3. Mark Attendance&#x20;

The trainees or supervisors should be able to mark the attendance daily twice (one for entry and exit) against each register (default configuration for sessions).&#x20;

1. Supervisors can mark half-day, full-day, and absent - Definitions of the statuses are as follows:
   * Not marked: Default status in the register. This must be the status when the user has not taken any action on the line item.
   * Present: Tapping once must change the "Not Marked" status to 'Present' (Not Marked —> Present).&#x20;
   * Absent: Tapping twice must change the 'Present' status to 'Absent' (Not Marked —> Present—->Absent).
   * Half-day (only if config requiring attendance once a day): Tapping thrice must change the absent status to half-day (Not Marked —> Present—->Absent—-> Half Day).
2. Save and Mark Later: If the user marks attendance for 10 out of 50 people, and presses save and mark later, the supervisor should be able to reopen the given attendance register while it is active and see the status of the attendance marked as per the last time they updated the screen.
3. Submit: If the user marks attendance for 10 out of 50 people, and presses submit, an error message is shown to mark attendance for all staff. After marking attendance for all staff, and clicking on submit supervisor navigates to the attendance recorded acknowledgement screen.

<div align="left" data-full-width="false">

<figure><img src="../../../../../.gitbook/assets/Full Half.png" alt="" width="180"><figcaption><p>\</p></figcaption></figure>

</div>







<div align="right">

<figure><img src="../../../../../.gitbook/assets/Mark attendance (2) (1).png" alt="" width="180"><figcaption></figcaption></figure>

</div>

### **Marking attendance and sending to oplog logic implementation:**&#x20;

For the registers, for which attendance is submitted, we have a flag upload\_to\_server for each log. If this is true, then the attendance for the register is submitted.

As we cannot send absent logs to the server, we filter the present and half-day logs , and create the oplog for those.

For each marking, two log objects are created for sending to the server: ENTRY and EXIT as shown below:&#x20;

`[{`

&#x20;`"registerId": registerId,`

&#x20;`"individualId": attendeeList.individualId,`

&#x20;`"time": entryTime,`

&#x20;`"type": "ENTRY",`

&#x20;`"status": "ACTIVE",`

&#x20;`"tenantId": tenantId,`

&#x20;`"documentIds": []`

`},`

`{`

&#x20;`"registerId": registerId,`

&#x20;`"individualId": attendeeList.individualId,`

&#x20;`"time": exitTime,`

&#x20;`"type": "EXIT",`

&#x20;`"status": "ACTIVE",`

&#x20;`"tenantId": tenantId,`

&#x20;`"documentIds": []`

`}]`

### API Details: 

<table><thead><tr><th width="155.33333333333334">End Point</th><th width="169">Request Method</th><th>Request Info</th></tr></thead><tbody><tr><td><strong>/health-attendance/v1/_search</strong></td><td><code>POST</code></td><td><pre class="language-json"><code class="lang-json">curl --location --globoff '{{base_url}}/attendance/v1/_search?tenantId=mz&#x26;staffId={{individualId}}&#x26;referenceId={{projectId}}' \
--header 'Content-Type: application/json' \
--data '{
        "RequestInfo": {
        "apiId": "mukta-services",
        "action": "",
        "did": 1,
        "key": "",
        "msgId": "20170310130900|en_IN",
        "requesterId": "",
        "ts": 1513579888683,
        "ver": ".01",
        "authToken": "{{token}}"
    }
}
'
</code></pre></td></tr><tr><td><strong>/individual/v1/_search</strong></td><td>POST</td><td><pre class="language-json"><code class="lang-json">curl --location 'https://unified-dev.digit.org/individual/v1/_search?limit=1000&#x26;offset=0&#x26;tenantId=mz&#x26;includeDeleted=false' \
--header 'Content-Type: application/json' \
--data '{
<strong>    "RequestInfo": {
</strong>        "authToken": "fc30d219-1075-4ee0-93af-8dc987f18b1c"
    },
    "Individual": {
        
        
        
        "id":[{{listOfIndividualIds}}],
        "tenantId":{{tenanatId}}
    }
}'
</code></pre></td></tr><tr><td><strong>/health-attendance/log/v1/_search</strong></td><td>POST</td><td><pre><code>curl --location 'http://localhost:8023/health-attendance/log/v1/_search?tenantId=mz&#x26;registerId=' \
--header 'Content-Type: application/json' \
--data '{
    "RequestInfo": {
        "apiId": "mukta-services",
        "action": "",
        "did": 1,
        "key": "",
        "msgId": "20170310130900|en_IN",
        "requesterId": "",
        "ts": 1513579888683,
        "ver": ".01",
        "authToken": "{{token}}",
        "userInfo": {
            "id": 324783744763,
            "uuid": "01b5b303-9e80-49d7-9d65-396675f0591e"
        }
    }
}'
</code></pre></td></tr><tr><td><strong>/health-attendance/log/v1/_create</strong></td><td>POST</td><td><pre><code>curl --location 'https://unified-dev.digit.org/health-attendance/log/v1/_create' \
--header 'Content-Type: application/json' \
--data '{
        "RequestInfo": {
        "apiId": "mukta-services",
        "action": "",
        "did": 1,
        "key": "",
        "msgId": "20170310130900|en_IN",
        "requesterId": "",
        "ts": 1513579888683,
        "ver": ".01",
        "authToken":"{{token}}"
    },
  "attendance": [
        {
        "registerId": {{registerId}},
        "individualId": {{individualId}},
        "time": ,
        "type": "ENTRY",
        "status": "ACTIVE",
        "tenantId": {{tenantId}},
        "documentIds":[]
        },
        {
        "registerId": {{registerId}},
        "individualId": {{individualId}},
        "time": ,
        "type": "EXIT",
        "status": "ACTIVE",
        "tenantId": {{tenantId}},
        "documentIds":[]
        }
    ]
}
'
</code></pre></td></tr></tbody></table>
