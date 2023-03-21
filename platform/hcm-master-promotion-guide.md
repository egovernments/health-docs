# HCM Master Promotion Guide

## Overview

This document is a step-by-step promotion guide to setup/promote  Health Campaign Manegement (HCM) to higher environments. The guide can be used by implementation teams or other external teams to set up the product.

## Table of Contents

### 1. Release Notes for – HCM 1.0&#x20;

* Release features&#x20;
* List of Core DIGIT services used
* Services built for HCM&#x20;
* Environment variables for HCM services&#x20;

&#x20;      \- Individual

&#x20;      \- Household

&#x20;      \- Product

&#x20;      \- Facility

&#x20;      \- Project

&#x20;      \- Stock&#x20;

&#x20;      \- Service request

### 2. Promotion guide&#x20;

* DIGIT environment production setup & deployments
* HCM promotion&#x20;
* Steps to create a tenant for HCM&#x20;
* Steps to add localisation using Rest API&#x20;
* Deploy Digit Core services&#x20;
* Deploy HCM services&#x20;
* UI/APK promotion guide&#x20;

## 1. Release Notes: HCM 1.0

| Version     | Date       | Description                                  |
| ----------- | ---------- | -------------------------------------------- |
| Version 1.0 | 03/03/2023 | This version covers the HCM promotion guide. |

### Release Features: List of core digit services used

| Service            | Image                                              |
| ------------------ | -------------------------------------------------- |
| Access control     | egovio/egov-accesscontrol:v1.1.3-72f8a8f87b-24     |
| Encryption Service | egovio/egov-enc-service:v1.1.2-72f8a8f87b-9        |
| File Store         | egovio/egov-filestore:v1.2.4-72f8a8f87b-10         |
| Localization       | egovio/egov-localization:v1.1.3-72f8a8f87b-6       |
| ID Gen             | egovio/egov-idgen:v1.2.3-72f8a8f87b-7              |
| Indexer            | egovio/egov-indexer:v1.1.7-f52184e6ba-25           |
| Location           | egovio/egov-location:v1.1.4-72f8a8f87b-6           |
| MDMS               | egovio/egov-mdms-service:v1.3.2-72f8a8f87b-12      |
| Notification Mail  | egovio/egov-notification-mail:v1.1.2-72f8a8f87b-12 |
| Notification sms   | egovio/egov-notification-sms:v1.1.3-48a03ad7bb-10  |
| OTP                | egovio/egov-otp:v1.2.2-72f8a8f87b-12               |
| Persister          | egovio/egov-persister:v1.1.4-72f8a8f87b-6          |
| Searcher           | egovio/egov-searcher:v1.1.5-72f8a8f87b-16          |
| URL Shortening     | egovio/egov-url-shortening:v1.1.2-1715164454-3     |
| User               | egovio/egov-user:v1.2.7-cc363f0584-12              |
| User OTP           | egovio/user-otp:v1.1.5-1715164454-3                |
| Workflow           | egovio/egov-workflow-v2:v1.2.1-df98ec3c35-2        |
| Report             | egovio/report:v1.3.4-96b24b0d72-16                 |
| Document Uploader  | egovio/egov-document-uploader:v1.1.0-75d461a4d2-4  |
| Playground         | egovio/playground:1.0                              |

### Services built for HCM

| Service         | Tag                                    | Description                                                                                                                              |
| --------------- | -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Individual      | egovio/individual:qa-6b25ac0bdc-31     | Individual service built in to digit platform, all the CRUD operations are allowed using api                                             |
| Household       | egovio/household:qa-6b25ac0bdc-38      | Household service provide to create household and add members to a household                                                             |
| Facility        | egovio/facility:qa-70438364e6-16       | Facility services provide the apis to create, update, delete and read facilities                                                         |
| Product         | egovio/product:qa-0ec164c4d3-7         | Product services provide the apis for CRUD operations for products and product variants                                                  |
| Project         | egovio/project:dev-4ba215e908-66       | Project services provide the apis for CRUD operations for project, project task, project staff, project resource and project beneficiary |
| Stock           | egovio/stock:qa-70438364e6-29          | Stock services provide the apis for creating, updating, deleting of stock receipts and stock reconciliations                             |
| Service Request | egovio/service-request:qa-2b9bf0593e-5 | Service Requests provide the create and submission apis for checklists.                                                                  |

### Environment Variables for HCM services

**Individual: Click** [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/health-services/individual/values.yaml) **to know more.**&#x20;

| Environment Variable                      | Value                                                  | Comments                            |
| ----------------------------------------- | ------------------------------------------------------ | ----------------------------------- |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID        | health-individual                                      | <p><br></p>                         |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER  | org.apache.kafka.common.serialization.StringSerializer | <p><br></p>                         |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS | <p><br></p>                                            | <p><br></p>                         |
| EGOV\_IDGEN\_HOST                         | <p><br></p>                                            | Value of IDGEN host server          |
| EGOV\_IDGEN\_PATH                         | egov-idgen/id/\_generate                               | <p><br></p>                         |
| EGOV\_IDGEN\_INTEGRATION\_ENABLED         | true/false                                             | <p><br></p>                         |
| IDGEN.INDIVIDUAL.ID.FORMAT                | individual.id                                          | <p><br></p>                         |
| SPRING\_REDIS\_HOST                       | redis.backbone                                         | <p><br></p>                         |
| SPRING\_REDIS\_PORT                       | <p><br></p>                                            | <p><br></p>                         |
| SPRING\_CACHE\_TYPE                       | redis                                                  | <p><br></p>                         |
| SPRING\_CACHE\_REDIS\_TIME-TO-LIVE        | <p><br></p>                                            | <p><br></p>                         |
| SPRING\_CACHE\_AUTOEXPIRY                 | true                                                   | <p><br></p>                         |
| JAVA\_OPTS                                | <p><br></p>                                            | <p><br></p>                         |
| JAVA\_ARGS                                | <p><br></p>                                            | <p><br></p>                         |
| JAVA\_ENABLE\_DEBUG                       | <p><br></p>                                            | <p><br></p>                         |
| SERVER\_PORT                              | <p><br></p>                                            | <p><br></p>                         |
| SECURITY\_BASIC\_ENABLED                  | false                                                  | <p><br></p>                         |
| MANAGEMENT\_SECURITY\_ENABLED             | false                                                  | <p><br></p>                         |
| TRACER\_OPENTRACING\_ENABLED              | true/false                                             | <p><br></p>                         |
| INDIVIDUAL.CONSUMER.SAVE.TOPIC            | save-individual-topic                                  | Topic to save individual            |
| INDIVIDUAL.CONSUMER.UPDATE.TOPIC          | update-individual-topic                                | Topic to update individual          |
| INDIVIDUAL.CONSUMER.DELETE.TOPIC          | delete-individual-topic                                | Topic to delete individual          |
| INDIVIDUAL.CONSUMER.BULK.CREATE.TOPIC     | individual-consumer-bulk-create-topic                  | Topic to create individuals in bulk |
| INDIVIDUAL.CONSUMER.BULK.UPDATE.TOPIC     | individual-consumer-bulk-update-topic                  | Topic to update individuals in bulk |
| INDIVIDUAL.CONSUMER.BULK.DELETE.TOPIC     | individual-consumer-bulk-delete-topic                  | Topic to delete individuals in bulk |

**Household: Click** [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/health-services/household/values.yaml) **to know more.** &#x20;

| Environment Variable                        | Value                                                  | Comments                               |
| ------------------------------------------- | ------------------------------------------------------ | -------------------------------------- |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID          | health-household                                       | <p><br></p>                            |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER    | org.apache.kafka.common.serialization.StringSerializer | <p><br></p>                            |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS   | <p><br></p>                                            | <p><br></p>                            |
| EGOV\_IDGEN\_HOST                           | <p><br></p>                                            | Value of IDGEN host server             |
| EGOV\_IDGEN\_PATH                           | egov-idgen/id/\_generate                               | <p><br></p>                            |
| EGOV\_IDGEN\_INTEGRATION\_ENABLED           | true/false                                             | <p><br></p>                            |
| HOUSEHOLD.IDGEN.ID.FORMAT                   | household.id                                           | <p><br></p>                            |
| SPRING\_REDIS\_HOST                         | redis.backbone                                         | <p><br></p>                            |
| SPRING\_REDIS\_PORT                         | 6379                                                   | <p><br></p>                            |
| SPRING\_CACHE\_TYPE                         | redis                                                  | <p><br></p>                            |
| SPRING\_CACHE\_REDIS\_TIME-TO-LIVE          | <p><br></p>                                            | <p><br></p>                            |
| SPRING\_CACHE\_AUTOEXPIRY                   | true                                                   | <p><br></p>                            |
| JAVA\_OPTS                                  | <p><br></p>                                            | <p><br></p>                            |
| JAVA\_ARGS                                  | <p><br></p>                                            | <p><br></p>                            |
| JAVA\_ENABLE\_DEBUG                         | <p><br></p>                                            | <p><br></p>                            |
| SERVER\_PORT                                | 8080                                                   | <p><br></p>                            |
| SECURITY\_BASIC\_ENABLED                    | false                                                  | <p><br></p>                            |
| MANAGEMENT\_SECURITY\_ENABLED               | false                                                  | <p><br></p>                            |
| TRACER\_OPENTRACING\_ENABLED                | true/false                                             | <p><br></p>                            |
| HOUSEHOLD.KAFKA.CREATE.TOPIC                | save-household-topic                                   | Topic to save household                |
| HOUSEHOLD.KAFKA.UPDATE.TOPIC                | update-household-topic                                 | Topic to update household              |
| HOUSEHOLD.KAFKA.DELETE.TOPIC                | delete-household-topic                                 | Topic to delete household              |
| HOUSEHOLD.CONSUMER.BULK.CREATE.TOPIC        | create-household-bulk-topic                            | Topic to create households in bulk     |
| HOUSEHOLD.CONSUMER.BULK.UPDATE.TOPIC        | update-household-bulk-topic                            | Topic to update households in bulk     |
| HOUSEHOLD.CONSUMER.BULK.DELETE.TOPIC        | delete-household-bulk-topic                            | Topic to delete households in bulk     |
| HOUSEHOLD\_MEMBER\_KAFKA\_CREATE\_TOPIC     | save-household-member-topic                            | Topic to create household member       |
| HOUSEHOLD\_MEMBER\_KAFKA\_UPDATE\_TOPIC     | update-household-member-topic                          | Topic to update household member       |
| HOUSEHOLD\_MEMBER\_KAFKA\_DELETE\_TOPIC     | delete-household-member-topic                          | Topic to delete household member       |
| HOUSEHOLD.MEMBER.CONSUMER.BULK.CREATE.TOPIC | household-member-consumer-bulk-create-topic            | Topic to create bulk household members |
| HOUSEHOLD.MEMBER.CONSUMER.BULK.UPDATE.TOPIC | household-member-consumer-bulk-update-topic            | Topic to update bulk household members |
| HOUSEHOLD.MEMBER.CONSUMER.BULK.DELETE.TOPIC | household-member-consumer-bulk-delete-topic            | Topic to delete bulk household members |

**Product: Click** [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/health-services/product/values.yaml) **to know more.** &#x20;

| Environment Variable                      | Value                                                  | Comments                        |
| ----------------------------------------- | ------------------------------------------------------ | ------------------------------- |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID        | health-product                                         | <p><br></p>                     |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER  | org.apache.kafka.common.serialization.StringSerializer | <p><br></p>                     |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS | <p><br></p>                                            | <p><br></p>                     |
| EGOV\_IDGEN\_HOST                         | <p><br></p>                                            | Value of IDGEN host server      |
| EGOV\_IDGEN\_PATH                         | egov-idgen/id/\_generate                               | <p><br></p>                     |
| EGOV\_IDGEN\_INTEGRATION\_ENABLED         | true/false                                             | <p><br></p>                     |
| SPRING\_REDIS\_HOST                       | redis.backbone                                         | <p><br></p>                     |
| SPRING\_REDIS\_PORT                       | 6379                                                   | <p><br></p>                     |
| SPRING\_CACHE\_TYPE                       | redis                                                  | <p><br></p>                     |
| SPRING\_CACHE\_REDIS\_TIME-TO-LIVE        | <p><br></p>                                            | <p><br></p>                     |
| SPRING\_CACHE\_AUTOEXPIRY                 | true                                                   | <p><br></p>                     |
| JAVA\_OPTS                                | <p><br></p>                                            | <p><br></p>                     |
| JAVA\_ARGS                                | <p><br></p>                                            | <p><br></p>                     |
| JAVA\_ENABLE\_DEBUG                       | <p><br></p>                                            | <p><br></p>                     |
| SERVER\_PORT                              | 8080                                                   | <p><br></p>                     |
| SECURITY\_BASIC\_ENABLED                  | false                                                  | <p><br></p>                     |
| MANAGEMENT\_SECURITY\_ENABLED             | false                                                  | <p><br></p>                     |
| TRACER\_OPENTRACING\_ENABLED              | true/false                                             | <p><br></p>                     |
| PRODUCT\_KAFKA\_CREATE\_TOPIC             | save-product-topic                                     | Topic to save product           |
| PRODUCT\_KAFKA\_UPDATE\_TOPIC             | update-product-topic                                   | Topic to update product         |
| PRODUCT\_VARIANT\_KAFKA\_CREATE\_TOPIC    | save-product-variant-topic                             | Topic to create product variant |
| PRODUCT\_VARIANT\_KAFKA\_UPDATE\_TOPIC    | update-product-variant-topic                           | Topic to update product variant |

**Facility: Click** [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/health-services/facility/values.yaml) **to know more.** &#x20;

| Environment Variable                      | Value                                                  | Comments                   |
| ----------------------------------------- | ------------------------------------------------------ | -------------------------- |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID        | health-project                                         | <p><br></p>                |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER  | org.apache.kafka.common.serialization.StringSerializer | <p><br></p>                |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS | <p><br></p>                                            | <p><br></p>                |
| EGOV\_IDGEN\_HOST                         | <p><br></p>                                            | Value of IDGEN host server |
| EGOV\_IDGEN\_PATH                         | egov-idgen/id/\_generate                               | <p><br></p>                |
| EGOV\_IDGEN\_INTEGRATION\_ENABLED         | true/false                                             | <p><br></p>                |
| FACILITY.IDGEN.ID.FORMAT                  | facility.id                                            | <p><br></p>                |
| SPRING\_REDIS\_HOST                       | redis.backbone                                         | <p><br></p>                |
| SPRING\_REDIS\_PORT                       | 6379                                                   | <p><br></p>                |
| SPRING\_CACHE\_TYPE                       | redis                                                  | <p><br></p>                |
| SPRING\_CACHE\_REDIS\_TIME-TO-LIVE        | <p><br></p>                                            | <p><br></p>                |
| SPRING\_CACHE\_AUTOEXPIRY                 | true                                                   | <p><br></p>                |
| JAVA\_OPTS                                | <p><br></p>                                            | <p><br></p>                |
| JAVA\_ARGS                                | <p><br></p>                                            | <p><br></p>                |
| JAVA\_ENABLE\_DEBUG                       | <p><br></p>                                            | <p><br></p>                |
| SERVER\_PORT                              | <p><br></p>                                            | <p><br></p>                |
| SECURITY\_BASIC\_ENABLED                  | false                                                  | <p><br></p>                |
| MANAGEMENT\_SECURITY\_ENABLED             | false                                                  | <p><br></p>                |
| TRACER\_OPENTRACING\_ENABLED              | true/false                                             | <p><br></p>                |
| FACILITY.KAFKA.CREATE.TOPIC               | save-facility-topic                                    | <p><br></p>                |
| FACILITY.KAFKA.UPDATE.TOPIC               | update-facility-topic                                  | <p><br></p>                |
| FACILITY.KAFKA.DELETE.TOPIC               | delete-facility-topic                                  | <p><br></p>                |
| FACILITY.CONSUMER.BULK.CREATE.TOPIC       | create-facility-bulk-topic                             | <p><br></p>                |
| FACILITY.CONSUMER.BULK.UPDATE.TOPIC       | update-facility-bulk-topic                             | <p><br></p>                |
| FACILITY.CONSUMER.BULK.DELETE.TOPIC       | delete-facility-bulk-topic                             | <p><br></p>                |

**Project: Click** [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/health-services/project/values.yaml) **to know more.**&#x20;

| Environment Variable                           | Value                                                  | Comments                                         |
| ---------------------------------------------- | ------------------------------------------------------ | ------------------------------------------------ |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID             | health-project                                         | <p><br></p>                                      |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER       | org.apache.kafka.common.serialization.StringSerializer | <p><br></p>                                      |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS      | <p><br></p>                                            | <p><br></p>                                      |
| EGOV\_IDGEN\_HOST                              | <p><br></p>                                            | Value of IDGEN host server                       |
| EGOV\_IDGEN\_PATH                              | egov-idgen/id/\_generate                               | <p><br></p>                                      |
| EGOV\_IDGEN\_INTEGRATION\_ENABLED              | true/false                                             | <p><br></p>                                      |
| PROJECT.STAFF.IDGEN.ID.FORMAT                  | project.staff.id                                       | Project staff id generated format                |
| PROJECT.FACILITY.IDGEN.ID.FORMAT               | project.facility.id                                    | Project facility id generated format             |
| PROJECT.TASK.IDGEN.ID.FORMAT                   | project.task.id                                        | Project task id generated format                 |
| IDGEN.PROJECT.BENEFICIARY.ID.FORMAT            | project.beneficiary.id                                 | Project beneficiary id generated format          |
| EGOV\_USER\_CONTEXT\_PATH                      | /user/users                                            | User service context path                        |
| EGOV\_SEARCH\_USER\_URL                        | /user/\_search                                         | User service search url                          |
| EGOV\_USER\_INTEGRATION\_ENABLED               | true/false                                             | User service integration enabled if it is true   |
| SPRING\_REDIS\_HOST                            | redis.backbone                                         | <p><br></p>                                      |
| SPRING\_REDIS\_PORT                            | 6379                                                   | <p><br></p>                                      |
| SPRING\_CACHE\_TYPE                            | redis                                                  | <p><br></p>                                      |
| SPRING\_CACHE\_REDIS\_TIME-TO-LIVE             | <p><br></p>                                            | <p><br></p>                                      |
| SPRING\_CACHE\_AUTOEXPIRY                      | true                                                   | <p><br></p>                                      |
| JAVA\_OPTS                                     | <p><br></p>                                            | <p><br></p>                                      |
| JAVA\_ARGS                                     | <p><br></p>                                            | <p><br></p>                                      |
| JAVA\_ENABLE\_DEBUG                            | <p><br></p>                                            | <p><br></p>                                      |
| SERVER\_PORT                                   | 8080                                                   | <p><br></p>                                      |
| SECURITY\_BASIC\_ENABLED                       | false                                                  | <p><br></p>                                      |
| MANAGEMENT\_SECURITY\_ENABLED                  | false                                                  | <p><br></p>                                      |
| TRACER\_OPENTRACING\_ENABLED                   | true/false                                             | <p><br></p>                                      |
| EGOV\_LOCATION\_CONTEXT\_PATH                  | /egov-location/location/v11                            | <p><br></p>                                      |
| EGOV\_LOCATION\_ENDPOINT                       | /boundarys/\_search                                    | Egov Location end point                          |
| EGOV\_MDMS\_INTEGRATION\_ENABLED               | true/false                                             | <p><br></p>                                      |
| EGOV\_MDMS\_MASTER\_NAME                       | project\_master                                        | Creating a mdms service bean                     |
| EGOV\_MDMS\_MODULE\_NAME                       | project                                                | Nor required.                                    |
| EGOV\_HOUSEHOLD\_HOST                          | <p><br></p>                                            | Host of the household service                    |
| EGOV\_INDIVIDUAL\_HOST                         | <p><br></p>                                            | Host of individual service                       |
| EGOV\_SEARCH\_INDIVIDUAL\_URL                  | /individual/v1/\_search                                | Search url of the individual                     |
| EGOV\_PRODUCT\_HOST                            | <p><br></p>                                            | Host of product service                          |
| EGOV\_SEARCH\_PRODUCT\_VARIANT\_URL            | /product/variant/v1/\_search                           | URL of the product variant search                |
| PROJECT.TASK.KAFKA.CREATE.TOPIC                | save-project-task-topic                                | Topic to save project task                       |
| PROJECT.TASK.CONSUMER.BULK.CREATE.TOPIC        | save-project-task-bulk-topic                           | Topic to save bulk project tasks                 |
| PROJECT.TASK.KAFKA.UPDATE.TOPIC                | update-project-task-topic                              | Topic to update project task                     |
| PROJECT.TASK.CONSUMER.BULK.UPDATE.TOPIC        | update-project-task-bulk-topic                         | Topic to update bulk project tasks               |
| PROJECT.TASK.KAFKA.DELETE.TOPIC                | delete-project-task-topic                              | Topic to delete project task                     |
| PROJECT.TASK.CONSUMER.BULK.DELETE.TOPIC        | delete-project-task-bulk-topic                         | Topic to delete bulk project tasks               |
| PROJECT.BENEFICIARY.KAFKA.CREATE.TOPIC         | save-project-beneficiary-topic                         | Topic to create project beneficiary              |
| PROJECT.BENEFICIARY.KAFKA.UPDATE.TOPIC         | update-project-beneficiary-topic                       | Topic to update project beneficiary              |
| PROJECT.BENEFICIARY.KAFKA.DELETE.TOPIC         | delete-project-beneficiary-topic                       | Topic to delete project beneficiary              |
| PROJECT.BENEFICIARY.CONSUMER.BULK.CREATE.TOPIC | project-beneficiary-consumer-bulk-create-topic         | Topic to create bulk project beneficiaries       |
| PROJECT.BENEFICIARY.CONSUMER.BULK.UPDATE.TOPIC | project-beneficiary-consumer-bulk-update-topic         | Topic to update bulk project beneficiaries       |
| PROJECT.BENEFICIARY.CONSUMER.BULK.DELETE.TOPIC | project-beneficiary-consumer-bulk-delete-topic         | Topic to delete bulk project beneficiaries       |
| PROJECT.STAFF.KAFKA.DELETE.TOPIC               | delete-project-staff-topic                             | Topic to delete project staff                    |
| PROJECT.STAFF.KAFKA.CREATE.TOPIC               | save-project-staff-topic                               | Topic to create project staff                    |
| PROJECT.STAFF.KAFKA.UPDATE.TOPIC               | update-project-staff-topic                             | Topic to update project staff                    |
| PROJECT.STAFF.CONSUMER.BULK.DELETE.TOPIC       | delete-project-staff-bulk-topic                        | Topic to delete bulk project staff               |
| PROJECT.STAFF.CONSUMER.BULK.CREATE.TOPIC       | create-project-staff-bulk-topic                        | Topic to create bulk project staff               |
| PROJECT.STAFF.CONSUMER.BULK.UPDATE.TOPIC       | update-project-staff-bulk-topic                        | Topic to update bulk project staff               |
| SEARCH\_API\_LIMIT                             | 1000                                                   | Search api limit                                 |
| PROJECT.DOCUMENT.ID.VERIFICATION.REQUIRED      | false                                                  | Project ID verification is done if value is true |
| PROJECT.MANAGEMENT.SYSTEM.KAFKA.CREATE.TOPIC   | save-project                                           | Topic to save project                            |
| PROJECT.MANAGEMENT.SYSTEM.KAFKA.UPDATE.TOPIC   | update-project                                         | Topic to update project                          |
| PROJECT.DEFAULT.OFFSET                         | 0                                                      | <p><br></p>                                      |
| PROJECT.DEFAULT.LIMIT                          | 100                                                    | <p><br></p>                                      |
| PROJECT.SEARCH.MAX.LIMIT                       | 200                                                    | <p><br></p>                                      |
| EGOV.IDGEN.PROJECT.NUMBER.NAME                 | project.number                                         | <p><br></p>                                      |
| PROJECT.RESOURCE.IDGEN.ID.FORMAT               | project.resource.id                                    | <p><br></p>                                      |
| PROJECT.RESOURCE.KAFKA.CREATE.TOPIC            | save-project-resource-topic                            | Topic to save project resource                   |
| PROJECT.RESOURCE.KAFKA.UPDATE.TOPIC            | update-project-resource-topic                          | Topic to update project resource                 |
| PROJECT.RESOURCE.KAFKA.DELETE.TOPIC            | delete-project-resource-topic                          | Topic to delete project resource                 |
| PROJECT.RESOURCE.CONSUMER.BULK.CREATE.TOPIC    | save-project-resource-bulk-topic                       | Topic to create bulk project resources           |
| PROJECT.RESOURCE.CONSUMER.BULK.UPDATE.TOPIC    | update-project-resource-bulk-topic                     | Topic to update bulk project resources           |
| PROJECT.RESOURCE.CONSUMER.BULK.DELETE.TOPIC    | delete-project-resource-bulk-topic                     | Topic to delete bulk project resources           |
| PROJECT.FACILITY.KAFKA.CREATE.TOPIC            | save-project-facility-topic                            | Topic to save project facility                   |
| PROJECT.FACILITY.KAFKA.UPDATE.TOPIC            | update-project-facility-topic                          | Topic to update project facility                 |
| PROJECT.FACILITY.KAFKA.DELETE.TOPIC            | delete-project-facility-topic                          | Topic to delete project facility                 |
| PROJECT.FACILITY.CONSUMER.BULK.CREATE.TOPIC    | create-project-facility-bulk-topic                     | Topic to create bulk project facilities          |
| PROJECT.FACILITY.CONSUMER.BULK.UPDATE.TOPIC    | update-project-facility-bulk-topic                     | Topic to update bulk project facilities          |
| PROJECT.FACILITY.CONSUMER.BULK.DELETE.TOPIC    | delete-project-facility-bulk-topic                     | Topic to delete bulk project facilities          |
| EGOV\_FACILITY\_HOST                           | <p><br></p>                                            | Host of the facility service                     |
| EGOV\_SEARCH\_FACILITY\_URL                    | /facility/v1/\_search                                  | Url of the search facility                       |
| PROJECT\_MDMS\_MODULE                          | HCM-PROJECT-TYPES                                      | <p><br></p>                                      |
| EGOV\_LOCATION\_HIERARCHY\_TYPE                | Admin                                                  | Hierarchy value used to get boundary values      |
| EGOV\_LOCATION\_CODES\_QUERY\_PARAM            | code                                                   | Query param used in egov location boundary api   |

**Stock: Click** [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/health-services/stock/values.yaml) **to know more.**&#x20;

| Environment Variable                            | Value                                                  | Comments                                                  |
| ----------------------------------------------- | ------------------------------------------------------ | --------------------------------------------------------- |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID              | health-project                                         | <p><br></p>                                               |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER        | org.apache.kafka.common.serialization.StringSerializer | <p><br></p>                                               |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS       | <p><br></p>                                            | <p><br></p>                                               |
| EGOV\_IDGEN\_HOST                               | <p><br></p>                                            | Value of IDGEN host server                                |
| EGOV\_IDGEN\_PATH                               | egov-idgen/id/\_generate                               | <p><br></p>                                               |
| EGOV\_IDGEN\_INTEGRATION\_ENABLED               | true/false                                             | <p><br></p>                                               |
| STOCK.IDGEN.ID.FORMAT                           | stock.id                                               | stock id generated format                                 |
| STOCK.RECONCILIATION.IDGEN.ID.FORMAT            | stock.reconciliation.id                                | Stock reconciliation id generated format                  |
| PROJECT.TASK.IDGEN.ID.FORMAT                    | project.task.id                                        | Project task id generated format                          |
| SPRING\_REDIS\_HOST                             | redis.backbone                                         | <p><br></p>                                               |
| SPRING\_REDIS\_PORT                             | 6379                                                   | <p><br></p>                                               |
| SPRING\_CACHE\_TYPE                             | redis                                                  | <p><br></p>                                               |
| SPRING\_CACHE\_REDIS\_TIME-TO-LIVE              | <p><br></p>                                            | <p><br></p>                                               |
| SPRING\_CACHE\_AUTOEXPIRY                       | true                                                   | <p><br></p>                                               |
| JAVA\_OPTS                                      | <p><br></p>                                            | <p><br></p>                                               |
| JAVA\_ARGS                                      | <p><br></p>                                            | <p><br></p>                                               |
| JAVA\_ENABLE\_DEBUG                             | <p><br></p>                                            | <p><br></p>                                               |
| SERVER\_PORT                                    | 8080                                                   | <p><br></p>                                               |
| SECURITY\_BASIC\_ENABLED                        | false                                                  | <p><br></p>                                               |
| MANAGEMENT\_SECURITY\_ENABLED                   | false                                                  | <p><br></p>                                               |
| TRACER\_OPENTRACING\_ENABLED                    | true/false                                             | <p><br></p>                                               |
| EGOV\_SEARCH\_PRODUCT\_VARIANT\_URL             | /product/variant/v1/\_search                           | Product variant search url to validate product variant id |
| STOCK.KAFKA.CREATE.TOPIC                        | save-stock-topic                                       | Topic to save stock receipts                              |
| STOCK.KAFKA.UPDATE.TOPIC                        | update-stock-topic                                     | Topic to update stock receipts                            |
| STOCK.KAFKA.DELETE.TOPIC                        | delete-stock-topic                                     | Topic to delete stock receipts                            |
| STOCK.CONSUMER.BULK.CREATE.TOPIC                | create-stock-bulk-topic                                | Topic to create bulk stock receipts                       |
| STOCK.CONSUMER.BULK.UPDATE.TOPIC                | update-stock-bulk-topic                                | Topic to update bulk stock receipts                       |
| STOCK.CONSUMER.BULK.DELETE.TOPIC                | delete-stock-bulk-topic                                | Topic to delete bulk stock receipts                       |
| STOCK.RECONCILIATION.KAFKA.CREATE.TOPIC         | save-stock-reconciliation-topic                        | Topic to create stock reconciliation audits               |
| STOCK.RECONCILIATION.KAFKA.UPDATE.TOPIC         | update-stock-reconciliation-topic                      | Topic to update stock reconciliation audits               |
| STOCK.RECONCILIATION.KAFKA.DELETE.TOPIC         | delete-stock-reconciliation-topic                      | Topic to delete stock reconciliation audits               |
| STOCK.RECONCILIATION.CONSUMER.BULK.CREATE.TOPIC | create-stock-reconciliation-bulk-topic                 | Topic to create bulk stock reconciliation                 |
| STOCK.RECONCILIATION.CONSUMER.BULK.UPDATE.TOPIC | update-stock-reconciliation-bulk-topic                 | Topic to update bulk stock reconciliation                 |
| STOCK.RECONCILIATION.CONSUMER.BULK.DELETE.TOPIC | delete-stock-reconciliation-bulk-topic                 | Topic to delete bulk stock reconciliation                 |
| SEARCH\_API\_LIMIT                              | 1000                                                   | Search api limit                                          |
| EGOV\_FACILITY\_HOST                            | <p><br></p>                                            | Host of the facility services                             |
| EGOV\_SEARCH\_FACILITY\_URL                     | /facility/v1/\_search                                  | Search url of the facility                                |
| EGOV\_PROJECT\_FACILITY\_HOST                   | <p><br></p>                                            | Host of the project facility service                      |
| EGOV\_SEARCH\_PROJECT\_FACILITY\_URL            | /project/facility/v1/\_search                          | Search url of the project facility                        |

**Service Request: Click** [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/core-services/service-request/values.yaml) **to know more.**&#x20;

| Environment Variable                       | Value                                                       | Comments                  |
| ------------------------------------------ | ----------------------------------------------------------- | ------------------------- |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID         | service-request                                             | <p><br></p>               |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER   | org.apache.kafka.common.serialization.StringSerializer      | <p><br></p>               |
| SPRING\_KAFKA\_PRODUCER\_VALUE\_SERIALIZER | org.springframework.kafka.support.serializer.JsonSerializer | <p><br></p>               |
| EGOV\_SERVICE\_DEFINITION\_CREATE\_TOPIC   | save-service-definition                                     | Checkist definition       |
| EGOV\_SERVICE\_CREATE\_TOPIC               | save-service                                                | Checklist answers payload |
| EGOV\_SERVICE\_REQUEST\_DEFAULT\_OFFSET    | 0                                                           | <p><br></p>               |
| EGOV\_SERVICE\_REQUEST\_DEFAULT\_LIMIT     | 10                                                          | <p><br></p>               |
| EGOV\_SERVICE\_REQUEST\_MAX\_LIMIT         | 100                                                         | <p><br></p>               |
| EGOV\_MAX\_STRING\_INPUT\_SIZE             | 8192                                                        | <p><br></p>               |
| JAVA\_OPTS                                 | <p><br></p>                                                 | <p><br></p>               |
| JAVA\_ARGS                                 | <p><br></p>                                                 | <p><br></p>               |
| MANAGEMENT\_SECURITY\_ENABLED              | false                                                       | <p><br></p>               |
| SERVER\_PORT                               | 8080                                                        | <p><br></p>               |
| SECURITY\_BASIC\_ENABLED                   | false                                                       | <p><br></p>               |



