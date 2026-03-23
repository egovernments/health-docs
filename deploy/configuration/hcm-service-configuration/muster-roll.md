# Muster Roll

## Overview

The attendance service supplies raw attendance logs, while the muster roll service collects these logs and calculates attendance according to specific business rules. For instance, determining whether attendance is measured in hours or days and defining what constitutes a half-day or a full day of attendance are decisions that depend on the specific implementation. These configurations can be adjusted within the service, and attendance calculations will be carried out based on these settings.

## Pre-requisites

* Attendance
* Individual
* Persister
* MDMS
* Workflow
* Idgen
* Notification

## Functionalities

The functionality includes the following APIs:

1. **Estimate Muster Roll**: This API calculates the attendance for a wage seeker based on their attendance logs.
2. **Create Muster Roll**: It allows you to create a muster roll, which is essentially a list of wage seekers.
3. **Update Muster Roll**: You can use this API to update a muster roll with modified aggregate attendance data.
4. **Search for Muster Roll**: This API enables you to search for a muster roll using specific parameters. For more details, you can refer to the Swagger contract.

## Setup

{% stepper %}
{% step %}
**Locate the Environment YAML File**

Go to the Helm environment file for your deployment environment:

```
https://github.com/{{ORG}}/DIGIT-DevOps/deploy-as-code/helm/environments/{{EnvironmentFile}}.yaml
```
{% endstep %}

{% step %}
**Add Required Variables**

In the environment file, add the following:

* Database details: `db-host`, `db-name`, `db-url`
* `domain`
* Core service configs: `idgen`, `workflow`, `user`, etc.
* Muster Roll-specific variables (refer to how it’s done in the dev file):
  * [Sample - Line 168](https://github.com/egovernments/health-campaign-devops/blob/v1.8/config-as-code/environments/egov-demo.yaml#L113)
  * [Sample - Line 684-709](https://github.com/egovernments/health-campaign-devops/blob/v1.8/config-as-code/environments/egov-demo.yaml#L684-L709)
{% endstep %}

{% step %}
**Verify Helm Chart Reference**

Ensure you're using the correct chart for muster roll:\
[health-muster-roll chart](https://github.com/egovernments/health-campaign-devops/tree/v1.8/config-as-code/helm/charts/health-services/muster-roll)
{% endstep %}

{% step %}
**Configure Persister Path**

Check that the muster-roll persister YAML file is added in `egov-persister.persister-yml-path`. Add it if missing.
{% endstep %}

{% step %}
**Add Secrets to Secret YAML File**

In the corresponding secrets file:

* Add DB credentials for Postgres and Flyway
* Add secrets for DIGIT core services (like user, filestore, mdms, etc.)
* Sample steps [given here](https://github.com/egovernments/DIGIT-DevOps/blob/digit-works/deploy-as-code/helm/environments/works-dev-secrets.yaml)
{% endstep %}
{% endstepper %}

## Configuration Details

### Configure Actions

Add all the APIs exposed (refer to the table below for actual APIs) to the actions.json file in MDMS

**Module name:** ACCESSCONTROL-ACTIONS-TEST

**Master name:** actions-test

### Configure Roles

Configure roles based on the roles column below in roles.json file.&#x20;

**Module name:** ACCESSCONTROL-ROLES

**Master name:** roles

### Configure Role-Action

Role-action mapping is configured in MDMS per the table below.&#x20;

**Module name:** ACCESSCONTROL-ROLEACTIONS

**Master name:** roleactions.json

<table><thead><tr><th width="302">Roles</th><th>API Endpoints</th></tr></thead><tbody><tr><td><p>CAMPAIGN_SUPERVISOR</p><p>PROXIMITY_SUPERVISOR</p></td><td>/muster-roll/v1/_estimate</td></tr><tr><td>CAMPAIGN_SUPERVISOR PROXIMITY_SUPERVISOR</td><td>/muster-roll/v1/_create</td></tr><tr><td>CAMPAIGN_SUPERVISOR PROXIMITY_SUPERVISOR</td><td>/muster-roll/v1/_update</td></tr><tr><td>CAMPAIGN_SUPERVISOR PROXIMITY_SUPERVISOR</td><td>/muster-roll/v1/_search</td></tr></tbody></table>

#### Other masters to be added

Other muster roll masters are configured in the **`common-masters`** folder:

[MusterRoll.json](https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.8/MusterRoll.json)

[IdFormat.json](https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.8/IdFormat.json)

[workerRates.json](https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.8/workerRates.json)

### Persister Configuration

{% embed url="https://github.com/egovernments/configs/blob/HCM-v1.8/health/egov-persister/muster-service-persister.yml" %}

## Integration Details

Links  to the [Environment file](https://github.com/egovernments/DIGIT-Works/blob/HCM-v1.8/backend/muster-roll/src/main/resources/Muster%20Environment.postman_environment.json) and [Postman collection](https://github.com/egovernments/DIGIT-Works/blob/HCM-v1.8/backend/muster-roll/src/main/resources/Muster%20Roll%20Service.postman_collection.json)

1. **Import Collection**\
   Load the _Muster Roll_ Postman collection into your Postman app.
2. **Import Environment**\
   Import the environment file. This sets up a "Muster Environment" with required variables.
3. **Run Attendance Setup APIs First**\
   Before running the Muster Roll APIs, run the following Attendance APIs:
   * **Create Attendance Register**\
     `POST https://{{hostname}}/{{attendance_context}}/v1/_create`
   * **Enrol Attendees**\
     `POST https://{{hostname}}/{{attendance_context}}/attendee/v1/_create`
   * **Create Attendance Logs**\
     `POST https://{{hostname}}/{{attendance_context}}/log/v1/_create`
4. **Update Register ID**\
   Copy the `registerId` from the response of the first API (step 3a), and set it as the current value of `registerId` in the _Muster Environment_.
5. **Run the Muster Roll Collection**\
   Use the **"Run Collection"** option in Postman. This will trigger:
   * `/muster-roll/v1/_estimate`
   * `/muster-roll/v1/_create`
   * `/muster-roll/v1/_update`
   * `/muster-roll/v1/_search`\
     — covering both success and error scenarios.
6. **Track Output Variables**\
   After `/create`, the environment variables `musterRollId` and `musterRollNumber` will be set automatically. These are used in the update and search requests.
