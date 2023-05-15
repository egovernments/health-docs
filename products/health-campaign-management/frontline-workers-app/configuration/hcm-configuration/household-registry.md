# Household Registry

## Overview

The household service helps and provides APIs to create households and household members for the HCM. This document provides the configuration details for setting up the household registry.

## Pre-requisites

* Knowledge of Java/J2EE (preferably Java 8 version).
* Knowledge of spring boot and spring-boot micro-services.
* Knowledge of Git or any version control system.
* Knowledge of RESTful web services.
* Knowledge of the Lombok library is helpful.
* Knowledge of eGov-mdms service, eGov-persister, eGov-idgen, eGov-indexer, and eGov-user will be helpful.

## Functionalities

1. Provides APIs to create, update, delete, and search households.
2. Provides APIs to bulk create, bulk update, and bulk delete households.
3. Provides APIs to create, update, delete, and search household members.
4. Provides APIs to bulk create, bulk update, and bulk delete household members.

### Setup details

The source code for a [Household](https://github.com/egovernments/health-campaign-services/tree/v1.1.0/health-services/household) is present in the health-campaign-services Git repo. The spring boot application needs the Lombok\* extension added to the IDE to load it. Once the application is up and running, the API requests can be posted to the URL and the IDs can be generated.

**\***In the case of IntelliJ, the plugin can be installed directly. For eclipse, the Lombok jar location has to be added in the eclipse.ini file in this format javaagent:lombok.jar.

## API Details

Refer to the Swagger API for YAML file details: [Household.yaml](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/docs/health-api-specs/contracts/registries/household.yml)

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

#### URLs for the external API references:

* eGov-Individual Service -> egov.individual.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)
* eGvo mdms -> egov.mdms.host =[ https://health-dev.digit.org](https://health-dev.digit.org)/
* eGov -idGen -> egov.idgen.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)
* eGov-User Service -> egov.user.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)

## Configuration details

#### Access MDMS configurations

**Action test: URL actions adding**

[**Action-test.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)

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

**Access to role-based actions**

[**Roleaction.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ROLEACTIONS/roleactions.json)

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

**Persister configuration**

[Household Persister Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-persister/household-persister.yml)

**Indexer configuration**

[Household Indexer Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-indexer/household-indexer.yml)

#### Database schema

<figure><img src="https://lh5.googleusercontent.com/OwISCIjoHvJKrm3GFVnfHgcXEfQE0rWc2w4v_TsDA2eS3mcaLjA0eXVwOm5qOESly-xGnOzhW-HMUdASnhoFKbRv3JcQruYZ-voZNI75MqKbmwmG_8GUPlFLgRpVOyzan4bxKAFweUbLXLvGLoizYc8" alt=""><figcaption></figcaption></figure>

**Postman collection**

[https://www.postman.com/lunar-resonance-126497/workspace/hcm/environment/24751924-61d3084a-c7bf-4591-8b7d-2ec5828d96b1](https://www.postman.com/lunar-resonance-126497/workspace/hcm/environment/24751924-61d3084a-c7bf-4591-8b7d-2ec5828d96b1)\
