# Stock & Inventory

## Overview

The stock service helps and provides APIs to manage stocks and reconciliation of stocks for the HCM. This document provides the configuration details for setting up the stock service.

## Pre-requisites

* Knowledge of Java/J2EE (preferably Java 8 version).
* Knowledge of spring boot and spring-boot micro-services.
* Knowledge of Git or any version control system.
* Knowledge of RESTful web services.
* Knowledge of the Lombok library is helpful.
* Knowledge of eGov-mdms service, eGov-persister, eGov-idgen, eGov-indexer, and eGov-user will be helpful.

## Functionalities

1. Provides APIs to create, update, delete, and search stocks.
2. Provides APIs to bulk create, bulk update, and bulk delete stocks
3. Provides APIs to create, update, delete, and search reconciliation for the stocks.
4. Provides APIs to bulk create, bulk update, and bulk delete reconciliation for the stocks.

### Setup details

The source code for the [Stock](https://github.com/egovernments/health-campaign-services/tree/v1.1.0/health-services/stock) is present in the health-campaign-services Git repo. The spring boot application needs the Lombok\* extension added to the IDE to load it. Once the application is up and running, the API requests can be posted to the URL and the IDs can be generated.

**\*** In the case of IntelliJ, the plugin can be installed directly. For eclipse, the Lombok jar location has to be added in the eclipse.ini file in this format javaagent:lombok.jar.

## API details

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

#### URLs for the external API references:

* eGov -user service :-> egov.user.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)
* eGov -idGen :-> egov.idgen.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)
* eGov -project service :-> egov.project.facility.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)
* eGov -product service :-> egov.product.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)

## Configuration details

#### Access MDMS configurations

**Action test: URL actions adding**

[**Action-test.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)

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

**Access to role-based actions**

[**Roleaction.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ROLEACTIONS/roleactions.json)

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

**Persister configuration**

[Stock Persister Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-persister/stock-persister.yml)

**Indexer configuration**

[Stock Indexer Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-indexer/stock-indexer.yml)

#### Database schema

<figure><img src="https://lh5.googleusercontent.com/o-BpHdAHLfWfbx4Ubf1t6LFRgRFqoL3ZgjNOTVcxFchpFN6vayKx6wiPCbFvRNTh2PoWb0ec58NKz9p6qrwzpdHgLz-3KM7vhnm2tuxoOplXdYx574kIeLbsa8NkUKnxFuIYbykW5iWZZI3fqV7Us0s" alt=""><figcaption></figcaption></figure>

**Postman collection**

[https://www.postman.com/lunar-resonance-126497/workspace/hcm/environment/24751924-61d3084a-c7bf-4591-8b7d-2ec5828d96b1](https://www.postman.com/lunar-resonance-126497/workspace/hcm/environment/24751924-61d3084a-c7bf-4591-8b7d-2ec5828d96b1)



[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
