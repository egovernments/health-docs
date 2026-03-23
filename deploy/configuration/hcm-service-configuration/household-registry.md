---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-service-configuration/household-registry
---

# Household Registry

## Overview

The household registry provides APIs to create households and household members for  HCM. This document provides the configuration details for setting up the household registry.

## Pre-requisites

* Knowledge of Java/J2EE (preferably Java 8 version).
* Knowledge of Spring Boot and Spring Boot microservices.
* Knowledge of Git or any version control system.
* Knowledge of RESTful web services.
* Knowledge of the Lombok library is helpful.
* Knowledge of eGov-mdms service, eGov-persister, eGov-idgen, eGov-indexer, and eGov-user will be helpful.

## Functionalities

1. Provides APIs to create, update, delete, and search households.
2. Provides APIs to bulk create, bulk update, and bulk delete households.
3. Provides APIs to create, update, delete, and search household members.
4. Provides APIs to bulk create, bulk update, and bulk delete household members.

## **Setup**&#x20;

{% stepper %}
{% step %}
### Clone or download the code from the GitHub repository

The source code for the Household registry is located in the [Git repository here](https://github.com/egovernments/health-campaign-services/tree/v1.1.0/health-services/household). Clone or download the code from this repository before proceeding.
{% endstep %}

{% step %}
### Add the Lombok extension/plugin&#x20;

The Household registry is a Spring Boot application that uses Lombok, a Java library. Add the Lombok extension/plugin to open and build the project in your IDE (like IntelliJ or Eclipse).
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

## **API Details** <a href="#api-information" id="api-information"></a>

The complete API specifications for the Household registry are documented in the Swagger YAML file:

* **Swagger API YAML:**-<img src="https://github.com/fluidicon.png" alt="" data-size="line"> [Household.yaml](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/docs/health-api-specs/contracts/registries/household.yml)

This YAML file contains:

* API endpoints and methods
* Request/response payloads
* Data models and schema references
* Error codes and descriptions

#### Household API Endpoints

| Endpoint                     | Method | Description                                 |
| ---------------------------- | ------ | ------------------------------------------- |
| `/household/v1/_create`      | POST   | Create/Add a new household                  |
| `/household/v1/bulk/_create` | POST   | Create new households in bulk               |
| `/household/v1/_update`      | POST   | Update the details of an existing household |
| `/household/v1/bulk/_update` | POST   | Update the details of households in bulk    |
| `/household/v1/_delete`      | POST   | Soft delete an existing household           |
| `/household/v1/bulk/_delete` | POST   | Soft delete households in bulk              |
| `/household/v1/_search`      | POST   | Search for existing households              |

#### Household Member API Endpoints

<table><thead><tr><th width="324.16796875">Endpoint</th><th width="117.546875">Method</th><th>Description</th></tr></thead><tbody><tr><td><code>/household/member/v1/_create</code></td><td>POST</td><td>Add a new household member</td></tr><tr><td><code>/household/member/v1/bulk/_create</code></td><td>POST</td><td>Add new household members in bulk</td></tr><tr><td><code>/household/member/v1/_update</code></td><td>POST</td><td>Update the linkage details of a household member</td></tr><tr><td><code>/household/member/v1/bulk/_update</code></td><td>POST</td><td>Update linkage details for household members in bulk</td></tr><tr><td><code>/household/member/v1/_delete</code></td><td>POST</td><td>Soft delete the linking of a household member</td></tr><tr><td><code>/household/member/v1/bulk/_delete</code></td><td>POST</td><td>Soft delete linking of household members in bulk</td></tr><tr><td><code>/household/member/v1/_search</code></td><td>POST</td><td>Search for household members</td></tr></tbody></table>

**Application.properties file information**_**:**_

Kafka topics persister configs for eGov persister

```
household.consumer.bulk.delete.topic=delete-household-bulk-topic
household.consumer.bulk.create.topic=create-household-bulk-topic
household.consumer.bulk.update.topic=update-household-bulk-topic

household.kafka.create.topic=save-household-topic
household.kafka.update.topic=update-household-topic
household.kafka.delete.topic=delete-household-topic

h.kafka.create.topic=save-household-topic
h.kafka.update.topic=update-household-topic

household.member.kafka.create.topic=save-household-member-topic
household.member.kafka.update.topic=update-household-member-topic
household.member.kafka.delete.topic=delete-household-member-topic

household.member.consumer.bulk.create.topic=household-member-consumer-bulk-create-topic
household.member.consumer.bulk.update.topic=household-member-consumer-bulk-update-topic
household.member.consumer.bulk.delete.topic=household-member-consumer-bulk-delete-topic

```

#### External Service URLs

| Service                                   | Property Key         | URL                                                            |
| ----------------------------------------- | -------------------- | -------------------------------------------------------------- |
| eGov-Individual                           | egov.individual.host | [https://health-dev.digit.org/](https://health-dev.digit.org/) |
| eGov MDMS (Master Data Management System) | egov.mdms.host       | [https://health-dev.digit.org/](https://health-dev.digit.org/) |
| eGov ID Generation                        | egov.idgen.host      | [https://health-dev.digit.org/](https://health-dev.digit.org/) |
| User Service                              | egov.user.host       | [https://health-dev.digit.org/](https://health-dev.digit.org/) |

## Configuration Details

Follow the details outlined below to configure and enable Household registry API actions and access control using MDMS, role-action mapping, persister, and indexer configurations.

### **MDMS Configurations**

#### Define Action URLs

Add new actions in the MDMS actions configuration (e.g., `action-test.json`). Each action represents an API endpoint you wish to secure and manage: [**Action-test.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)

```
{
 "id": 1546,
 "name": "Household Create",
 "url": "/household/v1/_create",
 "displayName": "Household Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1547,
 "name": "Household Update",
 "url": "/household/v1/_update",
 "displayName": "Household Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1548,
 "name": "Household Search",
 "url": "/household/v1/_search",
 "displayName": "Household Search",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1558,
 "name": "Household Member Create",
 "url": "/household/member/v1/_create",
 "displayName": "Household Member Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1559,
 "name": "Household Member Update",
 "url": "/household/member/v1/_update",
 "displayName": "Household Member Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1560,
 "name": "Household Member Search",
 "url": "/household/member/v1/_search",
 "displayName": "Household Member Search",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1573,
 "name": "Household Bulk Create",
 "url": "/household/v1/bulk/_create",
 "displayName": "Household Bulk Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1574,
 "name": "Household Bulk Update",
 "url": "/household/v1/bulk/_update",
 "displayName": "Household Bulk Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1575,
 "name": "Household Delete",
 "url": "/household/v1/_delete",
 "displayName": "Household Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1576,
 "name": "Household Bulk Delete",
 "url": "/household/v1/bulk/_delete",
 "displayName": "Household Bulk Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1581,
 "name": "Household Member Bulk Create",
 "url": "/household/member/v1/bulk/_create",
 "displayName": "Household Member Bulk Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1582,
 "name": "Household Member Bulk Update",
 "url": "/household/member/v1/bulk/_update",
 "displayName": "Household Member Bulk Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1583,
 "name": "Household Member Delete",
 "url": "/household/member/v1/_delete",
 "displayName": "Household Member Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},
{
 "id": 1584,
 "name": "Household Member Bulk Delete",
 "url": "/household/member/v1/bulk/_delete",
 "displayName": "Household Member Bulk Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "household",
 "code": "null",
 "path": ""
},

```

### **Role-Action Mapping**

#### Assign Actions to Roles

Configure which user roles can access which API actions in `roleaction.json`. Map each action ID to the required roles: [**roleaction.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ROLEACTIONS/roleactions.json)**.** Refer example below:

```
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1546,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1546,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1546,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1547,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1547,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1547,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1548,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1548,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1548,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1558,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1558,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1558,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1559,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1559,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1559,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1560,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1560,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1560,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1573,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1573,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1573,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1574,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1574,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1574,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1575,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1575,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1575,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1576,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1576,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1576,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1581,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1581,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1581,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1582,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1582,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1582,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1583,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1583,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1583,
 "actioncode": "",
 "tenantId": "default"
}
```

## **Persister Configuration**

Configure the persister service for the Individual module. This is typically done by adding/updating a YAML file (e.g., `household-persister.yml`) - [Household Persister Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-persister/household-persister.yml) This YAML maps API operations to database persistence logic (topics, queries, etc.).

## **Indexer Configuration**

Configure the indexer for the Individual module (e.g., `household-indexer.yml`) - [Household Indexer Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-indexer/household-indexer.yml) This will ensure individual data is indexed and searchable as per business requirements.

## Database Schema

<figure><img src="https://lh5.googleusercontent.com/OwISCIjoHvJKrm3GFVnfHgcXEfQE0rWc2w4v_TsDA2eS3mcaLjA0eXVwOm5qOESly-xGnOzhW-HMUdASnhoFKbRv3JcQruYZ-voZNI75MqKbmwmG_8GUPlFLgRpVOyzan4bxKAFweUbLXLvGLoizYc8" alt=""><figcaption></figcaption></figure>

## **Postman Collection**

[Click here to access](https://www.postman.com/sreejith-kanjarla-759135/hcm-collection/folder/yiuz7as/household) the Postman collection.
