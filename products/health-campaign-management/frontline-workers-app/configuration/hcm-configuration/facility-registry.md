# Facility Registry

## Overview

The facility service helps and provides APIs to create facilities for the HCM. This document provides the configuration details for setting up the facility.

## Pre-requisites

* Knowledge of Java/J2EE (preferably Java 8 version).
* Knowledge of spring boot and spring-boot micro-services.
* Knowledge of Git or any version control system.
* Knowledge of RESTful web services.
* Knowledge of the Lombok library is helpful.
* Knowledge of eGov-mdms service, eGov-persister, eGov-idgen, eGov-indexer, and eGov-user will be helpful.

## Functionalities

1. Provides APIs to create, update, delete, and search facilities.
2. Provides APIs to bulk create, bulk update, and bulk delete facilities.

### Setup details

The source code for [Facility](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/docs/health-api-specs/contracts/registries/facility.yml) is present in the health-campaign-services Git repo. The spring boot application needs the Lombok\* extension added to the IDE to load it. Once the application is up and running, the API requests can be posted to the URL and the IDs can be generated.

**\***In the case of IntelliJ, the plugin can be installed directly. For eclipse, the Lombok jar location has to be added in the eclipse.ini file in this format javaagent:lombok.jar.

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

#### URLs for the external API references:

* eGvo mdms :-> egov.mdms.host =[ https://health-dev.digit.org](https://health-dev.digit.org)/
* eGov -idGen :-> egov.idgen.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)
* eGov-User Service -> egov.user.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)

## Configuration details

#### Access MDMS configurations

**Action test: URL actions adding**

[**Action-test.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)

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

**Access to role-based actions**

[**Roleaction.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ROLEACTIONS/roleactions.json)

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

**Persister configuration**

[Facility Persister Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-persister/facility-persister.yml)

**Indexer configuration**

[Facility Indexer Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-indexer/facility-indexer.yml)

#### Database schema

<figure><img src="https://lh5.googleusercontent.com/wscPUUhRgY_A_1pmJLQ0qz3O_uklMHOatlXjnuifIwkzTHWf-ElEuLHkxtZ5VKooXpUmWbUHvRFLX33s18hzTjaqxdM_7UHjABgQYcfsod6ejqHGdoUIrbDEpZXTCEZGVAccNtHl5KOyLOSG6gckcJY" alt=""><figcaption></figcaption></figure>

**Postman collection**

[https://www.postman.com/lunar-resonance-126497/workspace/hcm/environment/24751924-61d3084a-c7bf-4591-8b7d-2ec5828d96b1](https://www.postman.com/lunar-resonance-126497/workspace/hcm/environment/24751924-61d3084a-c7bf-4591-8b7d-2ec5828d96b1)

[\
](https://github.com/egovernments/health-campaign-services/blob/demo/health-services/individual/src/main/resources/individual-persister.yml)[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
