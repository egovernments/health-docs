# Attendance

## Overview

The attendance registry allows creation of an attendance register, enrollment of staff and attendees and capture of attendance records with entry/exit times. To compute attendance based on the logs, a calculator service should be built with specific business logic.&#x20;

## Pre-requisites

* DIGIT backbone services
* Idgen
* Persister
* Project Service
* Boundary Service

## Functionalities

* Allows creation/updation/search of an attendance register
* Allows mapping of staff and attendees to a register and enforces permissions.
* Log entry and exit timestamps in epoch time for a referenced entity
* Staff members can be added or removed from the Attendance Register, with roles (Editor, Approver, Owner) defining permissions: Editors modify records, Approvers validate records, and Owners have full administrative control.

## Setup&#x20;

{% stepper %}
{% step %}
### Clone or download the code from the GitHub repository

The source code for the Attendance registry is located in the [Git repository here](https://github.com/egovernments/DIGIT-Works/tree/master/backend/attendance). Clone or download the code from this repository before proceeding.
{% endstep %}

{% step %}
### Add the Lombok extension/plugin&#x20;

The Attendance module is a Spring Boot application that uses Lombok, a Java library. Add the Lombok extension/plugin to open and build the project in your IDE (like IntelliJ or Eclipse).
{% endstep %}

{% step %}
### Setup Lombok in IDEs

Install the Lombok plugin directly from the IntelliJ plugins marketplace.&#x20;

* Download the Lombok jar file.
*   Add the following line to your `eclipse.ini` file (replace `lombok.jar` with the correct path to your Lombok jar):

    ```
    -javaagent:lombok.jar
    ```
{% endstep %}

{% step %}
### Run application

Once Lombok is set up and the application is running (using your IDE or command line), you can start making API requests to the Attendance service’s endpoints.
{% endstep %}

{% step %}
### Generate IDs

When you send API requests, the system will generate the required IDs automatically as part of its normal operation.
{% endstep %}
{% endstepper %}

## API Details

### API Reference

The complete API specifications for the Attendance Service are documented in the Swagger YAML file:

* **Swagger API YAML:** [Attendance-v1.0.0.yaml](https://github.com/egovernments/DIGIT-Specs/blob/master/Domain%20Services/Health/Attendance-v1.0.0.yaml)

This YAML file contains:

* API endpoints
* Request/response payloads
* Data models
* Error codes and descriptions

### Application Properties - Kafka Topic Configuration

Below are the Kafka topics configured in the `application.properties` file for the eGov persister:

| Functionality       | Create Topic        | Update Topic          | Bulk Topic(s)                                                                                 |
| ------------------- | ------------------- | --------------------- | --------------------------------------------------------------------------------------------- |
| Attendance Register | save-attendance     | update-attendance     |                                                                                               |
| Attendance Staff    | save-staff          | update-staff          |                                                                                               |
| Attendance Attendee | save-attendee       | update-attendee       |                                                                                               |
| Attendance Log      | save-attendance-log | update-attendance-log | <p>save-attendance-log-bulk-health (create)<br>update-attendance-log-bulk-health (update)</p> |

**Properties format:**

```
attendance.register.kafka.create.topic=save-attendance
attendance.register.kafka.update.topic=update-attendance

attendance.staff.kafka.create.topic=save-staff
attendance.staff.kafka.update.topic=update-staff

attendance.attendee.kafka.create.topic=save-attendee
attendance.attendee.kafka.update.topic=update-attendee

attendance.log.kafka.create.topic=save-attendance-log
attendance.log.kafka.update.topic=update-attendance-log
attendance.log.kafka.consumer.bulk.create.topic=save-attendance-log-bulk-health
attendance.log.kafka.consumer.bulk.update.topic=update-attendance-log-bulk-health
```

### External Service URLs

Below are the URLs for external services that the Attendance Service interacts with:

| Service              | Property Key           | URL                                                              |
| -------------------- | ---------------------- | ---------------------------------------------------------------- |
| eGov MDMS            | egov.mdms.host         | [https://unified-dev.digit.org/](https://unified-dev.digit.org/) |
| eGov ID Generation   | egov.idgen.host        | [https://unified-dev.digit.org/](https://unified-dev.digit.org/) |
| Localization Service | egov.localization.host | [https://unified-dev.digit.org/](https://unified-dev.digit.org/) |
| Project Service      | egov.project.host      | [http://unified-dev.digit.org](http://unified-dev.digit.org/)    |

## Configuration Details

### MDMS Configurations <a href="#access-mdms-configurations" id="access-mdms-configurations"></a>

#### Define Action URLs

Add new actions in the MDMS actions configuration (e.g., `action-test.json`). Each action represents an API endpoint you wish to secure and manage: [actions-test.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)

```
{
  "id": 1696,
  "name": "Create Attendance Register",
  "url": "/attendance/v1/_create",
  "parentModule": "attendance-service",
  "displayName": "Create attendance register",
  "orderNumber": 0,
  "enabled": false,
  "serviceCode": "attendance-service",
  "code": "null",
  "path": ""
},
{
  "id": 1697,
  "name": "Search Attendance Register",
  "url": "/attendance/v1/_search",
  "parentModule": "attendance-service",
  "displayName": "Search attendance register",
  "orderNumber": 0,
  "enabled": false,
  "serviceCode": "attendance-service",
  "code": "null",
  "path": ""
},
{
  "id": 1698,
  "name": "Update Attendance Register",
  "url": "/attendance/v1/_update",
  "parentModule": "attendance-service",
  "displayName": "Update attendance register",
  "orderNumber": 0,
  "enabled": false,
  "serviceCode": "attendance-service",
  "code": "null",
  "path": ""
},
{
  "id": 1699,
  "name": "Create Attendance Register Log",
  "url": "/attendance/log/v1/_create",
  "parentModule": "attendance-service",
  "displayName": "Create attendance register log",
  "orderNumber": 0,
  "enabled": false,
  "serviceCode": "attendance-service",
  "code": "null",
  "path": ""
},
{
  "id": 1700,
  "name": "Search Attendance Register Log",
  "url": "/attendance/log/v1/_search",
  "parentModule": "attendance-service",
  "displayName": "Search attendance register log",
  "orderNumber": 0,
  "enabled": false,
  "serviceCode": "attendance-service",
  "code": "null",
  "path": ""
},
{
  "id": 1701,
  "name": "Update Attendance Register Log",
  "url": "/attendance/log/v1/_update",
  "parentModule": "attendance-service",
  "displayName": "Update attendance register log",
  "orderNumber": 0,
  "enabled": false,
  "serviceCode": "attendance-service",
  "code": "null",
  "path": ""
},
{
  "id": 1702,
  "name": "Create Attendee",
  "url": "/attendance/attendee/v1/_create",
  "parentModule": "attendance-service",
  "displayName": "Create Attendee",
  "orderNumber": 0,
  "enabled": false,
  "serviceCode": "attendance-service",
  "code": "null",
  "path": ""
},
{
  "id": 1703,
  "name": "Delete Attendee",
  "url": "/attendance/attendee/v1/_delete",
  "parentModule": "attendance-service",
  "displayName": "Delete Attendee",
  "orderNumber": 0,
  "enabled": false,
  "serviceCode": "attendance-service",
  "code": "null",
  "path": ""
},
{
  "id": 1704,
  "name": "Create Staff",
  "url": "/attendance/staff/v1/_create",
  "parentModule": "attendance-service",
  "displayName": "Create Staff",
  "orderNumber": 0,
  "enabled": false,
  "serviceCode": "attendance-service",
  "code": "null",
  "path": ""
},
{
  "id": 1705,
  "name": "Delete Staff",
  "url": "/attendance/staff/v1/_delete",
  "parentModule": "attendance-service",
  "displayName": "Delete Staff",
  "orderNumber": 0,
  "enabled": false,
  "serviceCode": "attendance-service",
  "code": "null",
  "path": ""
}
```

#### Assign Actions to Roles

Configure which user roles can access which API actions in `roleaction.json`. Map each action ID to the required roles: [**Roleaction.json**](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/ACCESSCONTROL-ROLEACTIONS/roleactions.json)**.** Refer example below:

```
{
  "rolecode": "SYSTEM_ADMINISTRATOR",
  "actionid": 1696,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "NATIONAL_SUPERVISOR",
  "actionid": 1696,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "PROVINCIAL_SUPERVISOR",
  "actionid": 1696,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "DISTRICT_SUPERVISOR",
  "actionid": 1696,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SUPERUSER",
  "actionid": 1696,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SYSTEM_ADMINISTRATOR",
  "actionid": 1697,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "NATIONAL_SUPERVISOR",
  "actionid": 1697,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "PROVINCIAL_SUPERVISOR",
  "actionid": 1697,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "DISTRICT_SUPERVISOR",
  "actionid": 1697,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SUPERUSER",
  "actionid": 1697,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SYSTEM_ADMINISTRATOR",
  "actionid": 1698,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "NATIONAL_SUPERVISOR",
  "actionid": 1698,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "PROVINCIAL_SUPERVISOR",
  "actionid": 1698,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "DISTRICT_SUPERVISOR",
  "actionid": 1698,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SUPERUSER",
  "actionid": 1698,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SYSTEM_ADMINISTRATOR",
  "actionid": 1699,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "NATIONAL_SUPERVISOR",
  "actionid": 1699,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "PROVINCIAL_SUPERVISOR",
  "actionid": 1699,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "DISTRICT_SUPERVISOR",
  "actionid": 1699,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SUPERUSER",
  "actionid": 1699,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SYSTEM_ADMINISTRATOR",
  "actionid": 1700,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "NATIONAL_SUPERVISOR",
  "actionid": 1700,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "PROVINCIAL_SUPERVISOR",
  "actionid": 1700,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "DISTRICT_SUPERVISOR",
  "actionid": 1700,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SUPERUSER",
  "actionid": 1700,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SYSTEM_ADMINISTRATOR",
  "actionid": 1701,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "NATIONAL_SUPERVISOR",
  "actionid": 1701,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "PROVINCIAL_SUPERVISOR",
  "actionid": 1701,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "DISTRICT_SUPERVISOR",
  "actionid": 1701,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SUPERUSER",
  "actionid": 1701,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SYSTEM_ADMINISTRATOR",
  "actionid": 1702,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "NATIONAL_SUPERVISOR",
  "actionid": 1702,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "PROVINCIAL_SUPERVISOR",
  "actionid": 1702,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "DISTRICT_SUPERVISOR",
  "actionid": 1702,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SUPERUSER",
  "actionid": 1702,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SYSTEM_ADMINISTRATOR",
  "actionid": 1703,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "NATIONAL_SUPERVISOR",
  "actionid": 1703,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "PROVINCIAL_SUPERVISOR",
  "actionid": 1703,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "DISTRICT_SUPERVISOR",
  "actionid": 1703,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SUPERUSER",
  "actionid": 1703,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SYSTEM_ADMINISTRATOR",
  "actionid": 1704,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "NATIONAL_SUPERVISOR",
  "actionid": 1704,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "PROVINCIAL_SUPERVISOR",
  "actionid": 1704,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "DISTRICT_SUPERVISOR",
  "actionid": 1704,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SUPERUSER",
  "actionid": 1704,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SYSTEM_ADMINISTRATOR",
  "actionid": 1705,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "NATIONAL_SUPERVISOR",
  "actionid": 1705,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "PROVINCIAL_SUPERVISOR",
  "actionid": 1705,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "DISTRICT_SUPERVISOR",
  "actionid": 1705,
  "actioncode": "",
  "tenantId": "mz"
},
{
  "rolecode": "SUPERUSER",
  "actionid": 1705,
  "actioncode": "",
  "tenantId": "mz"
}
```

## Persister Configuration <a href="#persister-configs" id="persister-configs"></a>

[Attendance YAML](https://github.com/egovernments/configs/blob/UNIFIED-UAT/health/egov-persister/attendance-service-persister.yml)

## Database Schema <a href="#database-schema" id="database-schema"></a>

<figure><img src="https://docs.digit.org/~gitbook/image?url=https%3A%2F%2F1644155002-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252Frm339myl1mngFnv59mnL%252Fuploads%252FowhvZvWfcrv26O0ZSYRb%252Fattendance_db.png%3Falt%3Dmedia%26token%3Dd884c910-6f91-49db-a3f7-d958ec35601a&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=42595263&#x26;sv=2" alt=""><figcaption></figcaption></figure>

### Postman Collections <a href="#postman-collections" id="postman-collections"></a>

[Link](https://api.postman.com/collections/28428162-42a38d4b-9af6-41cc-86ee-ce99fc40d95d?access_key=PMAT-01HM8EYY8H24BERS02TQ5M2HB9)
