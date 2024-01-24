# Project Services

## Overview

The stock service provides APIs to manage project, project staff, project beneficiary, project task, project resources, and project facility for the HCM. This document provides the configuration details for setting up the project.

## Pre-requisites

* Knowledge of Java/J2EE (preferably Java 8 version).
* Knowledge of spring boot and spring-boot micro-services.
* Knowledge of Git or any version control system.
* Knowledge of RESTful web services.
* Knowledge of the Lombok library is helpful.
* Knowledge of eGov-mdms service, eGov-persister, eGov-idgen, eGov-indexer, and eGov-user will be helpful.

## Functionalities

1. Provides APIs to create, update, delete, and search projects.
2. Provides APIs to create, update, delete, and search project beneficiaries.
3. Provides APIs to bulk create, bulk update, and bulk delete project beneficiaries.
4. Provides APIs to create, update, delete, and search project facilities.
5. Provides APIs to bulk create, bulk update, bulk delete project facility.
6. Provides APIs to create, update, delete, and search project staff.
7. Provides APIs to bulk create, bulk update, and bulk delete project staff.
8. Provides APIs to create, update, delete and search project tasks.
9. Provides APIs to bulk create, bulk update, and bulk delete project tasks.
10. Provides APIs to create, update, delete, and search project resources.
11. Provides APIs to bulk create, bulk update, and bulk delete project tasks.

### Setup details

The source code for the [Project](https://github.com/egovernments/health-campaign-services/tree/v1.1.0/health-services/project) is present in the health-campaign-services Git repo. The spring boot application needs the **Lombok\*** extension added to the IDE to load it. Once the application is up and running, the API requests can be posted to the URL and the IDs can be generated.

**\***In the case of IntelliJ, the plugin can be installed directly. For eclipse, the Lombok jar location has to be added in the eclipse.ini file in this format javaagent:lombok.jar.

## API Details

Refer to the Swagger API for YAML file details. Link - [Project.yaml](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/docs/health-api-specs/contracts/project.yml)

**Application.properties file information**_**:**_

Kafka topics persister configs for projects

```
project.resource.kafka.create.topic=save-project-resource-topic
project.resource.kafka.update.topic=update-project-resource-topic
project.resource.kafka.delete.topic=delete-project-resource-topic

project.resource.consumer.bulk.create.topic=save-project-resource-bulk-topic
project.resource.consumer.bulk.update.topic=update-project-resource-bulk-topic
project.resource.consumer.bulk.delete.topic=delete-project-resource-bulk-topic
project.management.system.kafka.create.topic=save-project
project.management.system.kafka.update.topic=update-project
project.staff.kafka.create.topic=save-project-staff-topic
project.staff.kafka.update.topic=update-project-staff-topic
project.staff.kafka.delete.topic=delete-project-staff-topic

project.staff.consumer.bulk.create.topic=save-project-staff-bulk-topic
project.staff.consumer.bulk.update.topic=update-project-staff-bulk-topic
project.staff.consumer.bulk.delete.topic=delete-project-staff-bulk-topic

project.facility.kafka.create.topic=save-project-facility-topic
project.facility.kafka.update.topic=update-project-facility-topic
project.facility.kafka.delete.topic=delete-project-facility-topic

project.facility.consumer.bulk.create.topic=save-project-facility-bulk-topic
project.facility.consumer.bulk.update.topic=update-project-facility-bulk-topic
project.facility.consumer.bulk.delete.topic=delete-project-facility-bulk-topic


project.beneficiary.kafka.create.topic=save-project-beneficiary-topic
project.beneficiary.kafka.update.topic=update-project-beneficiary-topic
project.beneficiary.kafka.delete.topic=delete-project-beneficiary-topic

project.beneficiary.consumer.bulk.create.topic=project-beneficiary-consumer-bulk-create-topic
project.beneficiary.consumer.bulk.update.topic=project-beneficiary-consumer-bulk-update-topic
project.beneficiary.consumer.bulk.delete.topic=project-beneficiary-consumer-bulk-delete-topic

project.task.kafka.create.topic=save-project-task-topic
project.task.consumer.bulk.create.topic=save-project-task-bulk-topic

project.task.kafka.update.topic=update-project-task-topic
project.task.consumer.bulk.update.topic=update-project-task-bulk-topic

project.task.kafka.delete.topic=delete-project-task-topic
project.task.consumer.bulk.delete.topic=delete-project-task-bulk-topic

```

#### URLs for the external API references:

* eGov-mdms service:-> egov.mdms.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)
* eGov-idGen:-> egov.idgen.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)
* eGov-facility service:-> egov.project.facility.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)
* eGov-product service:-> egov.product.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)
* eGov-user service:-> egov.user.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)

## Configuration details

#### Access MDMS configurations

**Action test: URL actions adding**

[**Action-test.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)

```
{
 "id": 1539,
 "name": "Project Staff Create",
 "url": "/project/staff/v1/_create",
 "displayName": "Project Staff Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1540,
 "name": "Project Staff Update",
 "url": "/project/staff/v1/_update",
 "displayName": "Project Staff Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1545,
 "name": "Project Staff Search",
 "url": "/project/staff/v1/_search",
 "displayName": "Project Staff Search",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1552,
 "name": "Project Task Create",
 "url": "/project/task/v1/_create",
 "displayName": "Project Task Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1553,
 "name": "Project Task Update",
 "url": "/project/task/v1/_update",
 "displayName": "Project Task Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1554,
 "name": "Project Task Search",
 "url": "/project/task/v1/_search",
 "displayName": "Project Task Search",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1555,
 "name": "Project Beneficiary Create",
 "url": "/project/beneficiary/v1/_create",
 "displayName": "Project Beneficiary Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1556,
 "name": "Project Beneficiary Update",
 "url": "/project/beneficiary/v1/_update",
 "displayName": "Project Beneficiary Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1557,
 "name": "Project Beneficiary Search",
 "url": "/project/beneficiary/v1/_search",
 "displayName": "Project Beneficiary Search",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1565,
 "name": "Project Task Bulk Create",
 "url": "/project/task/v1/bulk/_create",
 "displayName": "Project Task Bulk Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1566,
 "name": "Project Task Bulk Update",
 "url": "/project/task/v1/bulk/_update",
 "displayName": "Project Task Bulk Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1567,
 "name": "Project Task Delete",
 "url": "/project/task/v1/_delete",
 "displayName": "Project Task Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1568,
 "name": "Project Task Bulk Delete",
 "url": "/project/task/v1/bulk/_delete",
 "displayName": "Project Task Bulk Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1569,
 "name": "Project Beneficiary Bulk Create",
 "url": "/project/beneficiary/v1/bulk/_create",
 "displayName": "Project Beneficiary Bulk Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1570,
 "name": "Project Beneficiary Bulk Update",
 "url": "/project/beneficiary/v1/bulk/_update",
 "displayName": "Project Beneficiary Bulk Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1571,
 "name": "Project Beneficiary Delete",
 "url": "/project/beneficiary/v1/_delete",
 "displayName": "Project Beneficiary Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1572,
 "name": "Project Beneficiary Bulk Delete",
 "url": "/project/beneficiary/v1/bulk/_delete",
 "displayName": "Project Beneficiary Bulk Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1577,
 "name": "Project Staff Bulk Create",
 "url": "/project/staff/v1/bulk/_create",
 "displayName": "Project Staff Bulk Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1578,
 "name": "Project Staff Bulk Update",
 "url": "/project/staff/v1/bulk/_update",
 "displayName": "Project Staff Bulk Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1579,
 "name": "Project Staff Delete",
 "url": "/project/staff/v1/_delete",
 "displayName": "Project Staff Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1580,
 "name": "Project Staff Bulk Delete",
 "url": "/project/staff/v1/bulk/_delete",
 "displayName": "Project Staff Bulk Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1592,
 "name": "Project Create",
 "url": "/project/v1/_create",
 "displayName": "Project Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1593,
 "name": "Project Update",
 "url": "/project/v1/_update",
 "displayName": "Project Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1594,
 "name": "Project Search",
 "url": "/project/v1/_search",
 "displayName": "Project Search",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1608,
 "name": "Project Resource Create",
 "url": "/project/resource/v1/_create",
 "displayName": "Project Resource Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1609,
 "name": "Project Resource Bulk Create",
 "url": "/project/resource/v1/bulk/_create",
 "displayName": "Project Resource Bulk Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1610,
 "name": "Project Resource Update",
 "url": "/project/resource/v1/_update",
 "displayName": "Project Resource Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1611,
 "name": "Project Resource Bulk Update",
 "url": "/project/resource/v1/bulk/_update",
 "displayName": "Project Resource Bulk Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1612,
 "name": "Project Resource Delete",
 "url": "/project/resource/v1/_delete",
 "displayName": "Project Resource Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1613,
 "name": "Project Resource Bulk Delete",
 "url": "/project/resource/v1/bulk/_delete",
 "displayName": "Project Resource Bulk Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1614,
 "name": "Project Resource Search",
 "url": "/project/resource/v1/_search",
 "displayName": "Project Resource Search",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1622,
 "name": "Project Facility Create",
 "url": "/project/facility/v1/_create",
 "displayName": "Project Facility Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1623,
 "name": "Project Facility Bulk Create",
 "url": "/project/facility/v1/bulk/_create",
 "displayName": "Project Facility Bulk Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1624,
 "name": "Project Facility Update",
 "url": "/project/facility/v1/_update",
 "displayName": "Project Facility Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1625,
 "name": "Project Facility Bulk Update",
 "url": "/project/facility/v1/bulk/_update",
 "displayName": "Project Facility Bulk Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1626,
 "name": "Project Facility Delete",
 "url": "/project/facility/v1/_delete",
 "displayName": "Project Facility Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1627,
 "name": "Project Facility Bulk Delete",
 "url": "/project/facility/v1/bulk/_delete",
 "displayName": "Project Facility Bulk Delete",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},
{
 "id": 1628,
 "name": "Project Facility Search",
 "url": "/project/facility/v1/_search",
 "displayName": "Project Facility Search",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "project",
 "code": "null",
 "path": ""
},

```

**Access to role-based actions**

[**Roleaction.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ROLEACTIONS/roleactions.json)

```
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1539,
 "actioncode": "",
 "tenantid": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1540,
 "actioncode": "",
 "tenantid": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1545,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1545,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1545,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1545,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "NATIONAL_SUPERVISOR",
 "actionid": 1545,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "PROVINCIAL_SUPERVISOR",
 "actionid": 1545,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRICT_SUPERVISOR",
 "actionid": 1545,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "FIELD_SUPERVISOR",
 "actionid": 1545,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1552,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1552,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1552,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1553,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1553,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1553,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1554,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1554,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1554,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1555,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1556,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1557,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1555,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1556,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1557,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1555,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1556,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1557,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1565,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1565,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1565,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1566,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1566,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1566,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1567,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1567,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1567,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1568,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1568,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1568,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1569,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1569,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1569,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1570,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1570,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1570,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1571,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1571,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1571,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1572,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "REGISTRAR",
 "actionid": 1572,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "DISTRIBUTOR",
 "actionid": 1572,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1577,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1578,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1579,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1580,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1592,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1593,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1594,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1608,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1609,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1610,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1611,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1612,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1613,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1614,
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
 "rolecode": "DISTRIBUTOR",
 "actionid": 1614,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1622,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1623,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1624,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1625,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1626,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1627,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1628,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1622,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1623,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1624,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1625,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1626,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1627,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "WAREHOUSE_MANAGER",
 "actionid": 1628,
 "actioncode": "",
 "tenantId": "default"
},

```

## **Persister Configuration**

[Project Persister Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-persister/project-persister.yml)

## **Indexer Configuration**

[Project Indexer Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-indexer/project-indexer.yml)

## Database Schema

<figure><img src="https://lh5.googleusercontent.com/9fy2MSfDZccFOtOC5tegd6e-ObmjtEUQmOviJHCJv7NgiLvxscWm1_dsFNvM24a9hJ9CZYA1QdQnT1GIPIhCJkNSpFdIs1LX9jKZ-xe-VbXR4FKVFOyfKZhQSJ07r2U-ZxiciBp2LNbHDtof3oekBiU" alt=""><figcaption></figcaption></figure>

## **Postman Collection**

[https://www.postman.com/lunar-resonance-126497/workspace/hcm/environment/24751924-61d3084a-c7bf-4591-8b7d-2ec5828d96b1](https://www.postman.com/lunar-resonance-126497/workspace/hcm/environment/24751924-61d3084a-c7bf-4591-8b7d-2ec5828d96b1)
