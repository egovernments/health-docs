# Facility Registry

## Overview

The facility registry provides APIs to create facilities for HCM. This document provides the configuration details for setting up the facility.

## Pre-requisites

* Knowledge of Java/J2EE (preferably Java 8 version).
* Knowledge of Spring Boot and Spring Boot microservices.
* Knowledge of Git or any version control system.
* Knowledge of RESTful web services.
* Knowledge of the Lombok library is helpful.
* Knowledge of eGov-mdms service, eGov-persister, eGov-idgen, eGov-indexer, and eGov-user will be helpful.

## Functionalities

1. Provides APIs to create, update, delete, and search facilities.
2. Provides APIs to bulk create, bulk update, and bulk delete facilities.

## **Setup**&#x20;

{% stepper %}
{% step %}
### Clone or download the code from the GitHub repository

The source code for the Facility registry is located in the [Git repository here](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/docs/health-api-specs/contracts/registries/facility.yml). Clone or download the code from this repository before proceeding.
{% endstep %}

{% step %}
### Add the Lombok extension/plugin&#x20;

The Facility registry is a Spring Boot application that uses Lombok, a Java library. Add the Lombok extension/plugin to open and build the project in your IDE (like IntelliJ or Eclipse).
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

Once Lombok is set up and the application is running (using your IDE or command line), you can start making API requests to the Individual service’s endpoints.
{% endstep %}

{% step %}
### Generate IDs

When you send API requests, the system generates the required IDs automatically as part of its normal operation.
{% endstep %}
{% endstepper %}

## API details

Refer to the Swagger API for YAML file details: [Facility.yaml](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/docs/health-api-specs/contracts/registries/facility.yml)

**Application.properties file information**_**:**_

Kafka topics persister configs for Facility

```
facility.consumer.bulk.delete.topic=delete-facility-bulk-topic
facility.consumer.bulk.create.topic=create-facility-bulk-topic
facility.consumer.bulk.update.topic=update-facility-bulk-topic

facility.kafka.create.topic=save-facility-topic
facility.kafka.update.topic=update-facility-topic
facility.kafka.delete.topic=delete-facility-topic
```

### External Service URLs

Below are the URLs for external services that the Facility registry interacts with:

| Service            | Property Key    | URL                                                          |
| ------------------ | --------------- | ------------------------------------------------------------ |
| eGov MDMS          | egov.mdms.host  | [https://health-dev.digit.org](https://health-dev.digit.org) |
| eGov ID Generation | egov.idgen.host | [https://health-dev.digit.org](https://health-dev.digit.org) |
| User Service       | egov.user.host  | [https://health-dev.digit.org](https://health-dev.digit.org) |

## Configuration Details

Follow the details outlined below to configure and enable Facility API actions and access control using MDMS, role-action mapping, persister, and indexer configurations.

### **MDMS Configurations**

#### Define Action URLs

Add new actions in the MDMS actions configuration (e.g., `action-test.json`). Each action represents an API endpoint you wish to secure and manage: [**Action-test.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)

```
{
 "id": 1615,
 "name": "Facility Create",
 "url": "/facility/v1/_create",
 "displayName": "Facility Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "facility",
 "code": "null",
 "path": ""
},
{
 "id": 1616,
 "name": "Facility Bulk Create",
 "url": "/facility/v1/bulk/_create",
 "displayName": "Facility Bulk Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "facility",
 "code": "null",
 "path": ""
},
{
 "id": 1617,
 "name": "Facility Update",
 "url": "/facility/v1/_update",
 "displayName": "Facility Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "facility",
 "code": "null",
 "path": ""
},
{
 "id": 1618,
 "name": "Facility Bulk Update",
 "url": "/facility/v1/bulk/_update",
 "displayName": "Facility Bulk Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "facility",
 "code": "null",
 "path": ""
},
{
 "id": 1619,
 "name": "Facility Delete",
 "url": "/facility/v1/_delete",
 "displayName": "Facility Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "facility",
 "code": "null",
 "path": ""
},
{
 "id": 1620,
 "name": "Facility Bulk Delete",
 "url": "/facility/v1/bulk/_delete",
 "displayName": "Facility Bulk Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "facility",
 "code": "null",
 "path": ""
},
{
 "id": 1621,
 "name": "Facility Search",
 "url": "/facility/v1/_search",
 "displayName": "Facility Search",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "facility",
 "code": "null",
 "path": ""
}
```

#### Assign Actions to Roles

Configure which user roles can access which API actions in `roleaction.json`. Map each action ID to the required roles: [**Roleaction.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ROLEACTIONS/roleactions.json)**.** Refer example below:

```
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1615,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1616,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1617,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1618,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1619,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1620,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1621,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1614,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1615,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1616,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1617,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1618,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1619,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1620,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1621,
 "actioncode": "",
 "tenantId": "default"
},

```

## **Persister Configuration**

[Facility Persister Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-persister/facility-persister.yml)

## **Indexer Configuration**

[Facility Indexer Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-indexer/facility-indexer.yml)

## Database Schema

<figure><img src="https://lh5.googleusercontent.com/wscPUUhRgY_A_1pmJLQ0qz3O_uklMHOatlXjnuifIwkzTHWf-ElEuLHkxtZ5VKooXpUmWbUHvRFLX33s18hzTjaqxdM_7UHjABgQYcfsod6ejqHGdoUIrbDEpZXTCEZGVAccNtHl5KOyLOSG6gckcJY" alt=""><figcaption></figcaption></figure>

## **Postman Collection**

[Click here to access](https://www.postman.com/sreejith-kanjarla-759135/hcm-collection/folder/ruqpnu1/facility) the Postman collection.
