# Stock & Inventory

## Overview

The stock registry provides APIs to manage stocks and reconciliation of stocks for HCM. This document provides the configuration details for setting up the stock service.

## Pre-requisites

* Knowledge of Java/J2EE (preferably Java 8 version).
* Knowledge of Spring Boot and Spring Boot microservices.
* Knowledge of Git or any version control system.
* Knowledge of RESTful web services.
* Knowledge of the Lombok library is helpful.
* Knowledge of eGov-mdms service, eGov-persister, eGov-idgen, eGov-indexer, and eGov-user will be helpful.

## Functionalities

1. Provides APIs to create, update, delete, and search stocks.
2. Provides APIs to bulk create, bulk update, and bulk delete stocks
3. Provides APIs to create, update, delete, and search reconciliation for the stocks.
4. Provides APIs to bulk create, bulk update, and bulk delete reconciliation for the stocks.

## **Setup**&#x20;

{% stepper %}
{% step %}
### Clone or download the code from the GitHub repository

The source code for the Stock registry is located in the [Git repository here](https://github.com/egovernments/health-campaign-services/tree/v1.1.0/health-services/stock). Clone or download the code from this repository before proceeding.
{% endstep %}

{% step %}
### Add the Lombok extension/plugin&#x20;

The Stock/Inventory registry is a Spring Boot application that uses Lombok, a Java library. Add the Lombok extension/plugin to open and build the project in your IDE (like IntelliJ or Eclipse).
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

## API Details

Refer to the Swagger API for YAML file details: [Stock.yaml](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/docs/health-api-specs/contracts/stock.yml)

**Application.properties file information**_**:**_

Kafka topics persister configs for stock and inventory

```
stock.consumer.bulk.delete.topic=delete-stock-bulk-topic
stock.consumer.bulk.create.topic=create-stock-bulk-topic
stock.consumer.bulk.update.topic=update-stock-bulk-topic

stock.kafka.create.topic=save-stock-topic
stock.kafka.update.topic=update-stock-topic
stock.kafka.delete.topic=delete-stock-topic

stock.reconciliation.consumer.bulk.delete.topic=delete-stock-reconciliation-bulk-topic
stock.reconciliation.consumer.bulk.create.topic=create-stock-reconciliation-bulk-topic
stock.reconciliation.consumer.bulk.update.topic=update-stock-reconciliation-bulk-topic

stock.reconciliation.kafka.create.topic=save-stock-reconciliation-topic
stock.reconciliation.kafka.update.topic=update-stock-reconciliation-topic
stock.reconciliation.kafka.delete.topic=delete-stock-reconciliation-topic
```

### External Service URLs

Below are the URLs for external services that the Stock registry interacts with:

| Service            | Property Key               | URL                                                          |
| ------------------ | -------------------------- | ------------------------------------------------------------ |
| eGov User Service  | egov.user.host             | [https://health-dev.digit.org](https://health-dev.digit.org) |
| eGov ID Generation | egov.idgen.host            | [https://health-dev.digit.org](https://health-dev.digit.org) |
| Project Service    | egov.project.facility.host | [https://health-dev.digit.org](https://health-dev.digit.org) |
| Product Service    | egov.product.host          | [https://health-dev.digit.org](https://health-dev.digit.org) |

## Configuration Details

Follow the details outlined below to configure and enable Stock API actions and access control using MDMS, role-action mapping, persister, and indexer configurations.

### **MDMS Configurations**

#### Define Action URLs

Add new actions in the MDMS actions configuration (e.g., `action-test.json`). Each action represents an API endpoint you wish to secure and manage: [**Action-test.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)

```
{
 "id": 1585,
 "name": "Stock Create",
 "url": "/stock/v1/_create",
 "displayName": "Stock Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "stock",
 "code": "null",
 "path": ""
},
{
 "id": 1586,
 "name": "Stock Update",
 "url": "/stock/v1/_update",
 "displayName": "Stock Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "stock",
 "code": "null",
 "path": ""
},
{
 "id": 1587,
 "name": "Stock Delete",
 "url": "/stock/v1/_delete",
 "displayName": "Stock Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "stock",
 "code": "null",
 "path": ""
},
{
 "id": 1588,
 "name": "Stock Bulk Create",
 "url": "/stock/v1/bulk/_create",
 "displayName": "Stock Bulk Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "stock",
 "code": "null",
 "path": ""
},
{
 "id": 1589,
 "name": "Stock Bulk Update",
 "url": "/stock/v1/bulk/_update",
 "displayName": "Stock Bulk Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "stock",
 "code": "null",
 "path": ""
},
{
 "id": 1590,
 "name": "Stock Bulk Delete",
 "url": "/stock/v1/bulk/_delete",
 "displayName": "Stock Bulk Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "stock",
 "code": "null",
 "path": ""
},
{
 "id": 1591,
 "name": "Stock Search",
 "url": "/stock/v1/_search",
 "displayName": "Stock Search",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "stock",
 "code": "null",
 "path": ""
},
{
  "id": 1601,
  "name": "Stock Reconciliation Create",
  "url": "/stock/reconciliation/v1/_create",
  "displayName": "Stock Reconciliation Create",
  "orderNumber": 0,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "stock",
  "code": "null",
  "path": ""
},
{
  "id": 1602,
  "name": "Stock Reconciliation Update",
  "url": "/stock/reconciliation/v1/_update",
  "displayName": "Stock Reconciliation Update",
  "orderNumber": 0,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "stock",
  "code": "null",
  "path": ""
},
{
  "id": 1603,
  "name": "Stock Reconciliation Delete",
  "url": "/stock/reconciliation/v1/_delete",
  "displayName": "Stock Reconciliation Delete",
  "orderNumber": 0,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "stock",
  "code": "null",
  "path": ""
},
{
  "id": 1604,
  "name": "Stock Reconciliation Bulk Create",
  "url": "/stock/reconciliation/v1/bulk/_create",
  "displayName": "Stock Reconciliation Bulk Create",
  "orderNumber": 0,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "stock",
  "code": "null",
  "path": ""
},
{
  "id": 1605,
  "name": "Stock Reconciliation Bulk Update",
  "url": "/stock/reconciliation/v1/bulk/_update",
  "displayName": "Stock Reconciliation Bulk Update",
  "orderNumber": 0,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "stock",
  "code": "null",
  "path": ""
},
{
  "id": 1606,
  "name": "Stock Reconciliation Bulk Delete",
  "url": "/stock/reconciliation/v1/bulk/_delete",
  "displayName": "Stock Reconciliation Bulk Delete",
  "orderNumber": 0,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "stock",
  "code": "null",
  "path": ""
},
{
  "id": 1607,
  "name": "Stock Reconciliation Search",
  "url": "/stock/reconciliation/v1/_search",
  "displayName": "Stock Reconciliation Search",
  "orderNumber": 0,
  "parentModule": "",
  "enabled": false,
  "serviceCode": "stock",
  "code": "null",
  "path": ""
},
```

#### Assign Actions to Roles

Configure which user roles can access which API actions in `roleaction.json`. Map each action ID to the required roles: [**Roleaction.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ROLEACTIONS/roleactions.json)**.** Refer example below:

```
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1585,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1586,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1587,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1588,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1589,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1590,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1591,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1585,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1586,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1587,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1588,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1589,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1590,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1591,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1601,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1602,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1603,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1604,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1605,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1606,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1607,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1601,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1602,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1603,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1604,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1605,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1606,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1607,
 "actioncode": "",
 "tenantId": "default"
},
```

## **Persister Configuration**

[Stock Persister Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-persister/stock-persister.yml)

## **Indexer Configuration**

[Stock Indexer Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-indexer/stock-indexer.yml)

## Database Schema

<figure><img src="https://lh5.googleusercontent.com/o-BpHdAHLfWfbx4Ubf1t6LFRgRFqoL3ZgjNOTVcxFchpFN6vayKx6wiPCbFvRNTh2PoWb0ec58NKz9p6qrwzpdHgLz-3KM7vhnm2tuxoOplXdYx574kIeLbsa8NkUKnxFuIYbykW5iWZZI3fqV7Us0s" alt=""><figcaption></figcaption></figure>

## **Postman Collection**

[**Link**](https://www.postman.com/lunar-resonance-126497/workspace/hcm/environment/24751924-61d3084a-c7bf-4591-8b7d-2ec5828d96b1)
