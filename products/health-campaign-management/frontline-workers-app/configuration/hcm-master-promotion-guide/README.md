# HCM Master Promotion Guide

## Overview

This document is a step-by-step promotion guide to setup/promote  Health Campaign Manegement (HCM) to higher environments. The guide can be used by implementation teams or other external teams to set up the product.

## Table of Contents

### 1. Release Notes for HCM&#x20;

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

&#x20;      \- Complaints Management

&#x20;      \- User Management     &#x20;

### 2. Promotion Guide&#x20;

* DIGIT environment production setup & deployments
* HCM promotion&#x20;
* Steps to create a tenant for HCM&#x20;
* Steps to add localisation using Rest API&#x20;
* Deploy Digit Core services&#x20;
* Deploy HCM services&#x20;
* UI/APK promotion guide&#x20;

## 1. Release Notes: HCM&#x20;

| Version     | Date       | Description                                  |
| ----------- | ---------- | -------------------------------------------- |
| Version 1.1 | 11/05/2023 | This version covers the HCM promotion guide. |

### Release Features: List of Core DIGIT Services Used

| Service            | Image                                                          |
| ------------------ | -------------------------------------------------------------- |
| Access control     | egovio/egov-accesscontrol:v1.1.3-72f8a8f87b-24                 |
| Encryption Service | egovio/egov-enc-service:v1.1.2-72f8a8f87b-9                    |
| File Store         | egovio/egov-filestore:v1.2.4-72f8a8f87b-10                     |
| Localization       | egovio/egov-localization:v1.1.3-72f8a8f87b-6                   |
| ID Gen             | egovio/egov-idgen:v1.2.3-72f8a8f87b-7                          |
| Indexer            | egovio/egov-indexer:v1.1.7-f52184e6ba-25                       |
| Location           | egovio/egov-location:v1.1.5-f9271c8-7                          |
| MDMS               | egovio/egov-mdms-service:v1.3.2-72f8a8f87b-12                  |
| Notification Mail  | egovio/egov-notification-mail:health-digit-master-6865af2823-2 |
| Notification sms   | egovio/egov-notification-sms:v1.1.3-48a03ad7bb-10              |
| OTP                | egovio/egov-otp:v1.2.2-72f8a8f87b-12                           |
| Persister          | egovio/egov-persister:v1.1.4-72f8a8f87b-6                      |
| Searcher           | egovio/egov-searcher:v1.1.5-72f8a8f87b-16                      |
| URL Shortening     | egovio/egov-url-shortening:v1.1.2-1715164454-3                 |
| User               | egovio/egov-user:health-digit-master-e27b970-31                |
| User OTP           | egovio/user-otp:health-digit-master-6865af2823-3               |
| Workflow           | egovio/egov-workflow-v2:v1.2.1-df98ec3c35-2                    |
| Report             | egovio/report:v1.3.4-96b24b0d72-16                             |
| Document Uploader  | egovio/egov-document-uploader:v1.1.0-75d461a4d2-4              |
| Playground         | egovio/playground:1.0                                          |

### Services uilt for HCM

| Service         | Tag                                                | Description                                                                                                                                |
| --------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Individual      | egovio/individual:v1.1.0-73167482a2-82             | Individual service built in to the DIGIT platform, all the CRUD operations are allowed using API.                                          |
| Household       | egovio/household:v1.1.0-73167482a2-50              | Household service provided to create household and add members to a household.                                                             |
| Facility        | egovio/facility:v1.1.0-73167482a2-28               | Facility services provide the APIs to create, update, delete and read facilities.                                                          |
| Product         | egovio/product:v1.1.0-73167482a2-12                | Product services provide the APIs for CRUD operations for products and product variants.                                                   |
| Project         | egovio/project:v1.1.0-73167482a2-80                | Project services provide the apis for CRUD operations for project, project task, project staff, project resource, and project beneficiary. |
| Stock           | egovio/stock:v1.1.0-73167482a2-36                  | Stock services provide the APIs for creating, updating, deleting of stock receipts and stock reconciliations.                              |
| Service Request | egovio/service-request:v1.0.0-a51bee1435-7         | Service requests provide the create and submission APIs for checklists.                                                                    |
| Transformer     | egovio/transformer:v1.1.0-73167482a2-38            | Library that transforms the data according to the analytics dashboard requirements.                                                        |
| Complaints      | egovio/pgr-services:v1.1.7-f58e5abb0d-8            | Complaints services provide features like add complaints, resolve complaints, etc.                                                         |
| User Management | egovio/egov-hrms:health-digit-master-5bc2341e92-14 | Create and manage users and team assignments for their respective boundaries.                                                              |

### Environment Variables for HCM Services

**Individual: Click** [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/health-services/individual/values.yaml) **to know more.**&#x20;

| Environment Variable                          | Value                                                  | Comments                            |
| --------------------------------------------- | ------------------------------------------------------ | ----------------------------------- |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID            | health-individual                                      | <p><br></p>                         |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER      | org.apache.kafka.common.serialization.StringSerializer | <p><br></p>                         |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS     | <p><br></p>                                            | <p><br></p>                         |
| EGOV\_IDGEN\_HOST                             | <p><br></p>                                            | Value of IDGEN host server          |
| EGOV\_IDGEN\_PATH                             | egov-idgen/id/\_generate                               | <p><br></p>                         |
| EGOV\_IDGEN\_INTEGRATION\_ENABLED             | true/false                                             | <p><br></p>                         |
| IDGEN.INDIVIDUAL.ID.FORMAT                    | individual.id                                          | <p><br></p>                         |
| SPRING\_REDIS\_HOST                           | redis.backbone                                         | <p><br></p>                         |
| SPRING\_REDIS\_PORT                           | <p><br></p>                                            | <p><br></p>                         |
| SPRING\_CACHE\_TYPE                           | redis                                                  | <p><br></p>                         |
| SPRING\_CACHE\_REDIS\_TIME-TO-LIVE            | <p><br></p>                                            | <p><br></p>                         |
| SPRING\_CACHE\_AUTOEXPIRY                     | true                                                   | <p><br></p>                         |
| JAVA\_OPTS                                    | <p><br></p>                                            | <p><br></p>                         |
| JAVA\_ARGS                                    | <p><br></p>                                            | <p><br></p>                         |
| JAVA\_ENABLE\_DEBUG                           | <p><br></p>                                            | <p><br></p>                         |
| SERVER\_PORT                                  | <p><br></p>                                            | <p><br></p>                         |
| SECURITY\_BASIC\_ENABLED                      | false                                                  | <p><br></p>                         |
| MANAGEMENT\_SECURITY\_ENABLED                 | false                                                  | <p><br></p>                         |
| TRACER\_OPENTRACING\_ENABLED                  | true/false                                             | <p><br></p>                         |
| INDIVIDUAL.CONSUMER.SAVE.TOPIC                | save-individual-topic                                  | Topic to save individual            |
| INDIVIDUAL.CONSUMER.UPDATE.TOPIC              | update-individual-topic                                | Topic to update individual          |
| INDIVIDUAL.CONSUMER.DELETE.TOPIC              | delete-individual-topic                                | Topic to delete individual          |
| INDIVIDUAL.CONSUMER.BULK.CREATE.TOPIC         | individual-consumer-bulk-create-topic                  | Topic to create individuals in bulk |
| INDIVIDUAL.CONSUMER.BULK.UPDATE.TOPIC         | individual-consumer-bulk-update-topic                  | Topic to update individuals in bulk |
| INDIVIDUAL.CONSUMER.BULK.DELETE.TOPIC         | individual-consumer-bulk-delete-topic                  | Topic to delete individuals in bulk |
| STATE\_LEVEL\_TENANT\_ID                      | default                                                |                                     |
| EGOV\_ENC\_HOST                               |                                                        |                                     |
| EGOV\_ENC\_ENCRYPT\_ENDPOINT                  | /egov-enc-service/crypto/v1/\_encrypt                  |                                     |
| EGOV\_ENC\_DECRYPT\_ENDPOINT                  | /egov-enc-service/crypto/v1/\_decrypt                  |                                     |
| AADHAAR\_PATTERN                              | \d{12}                                                 |                                     |
| MOBILE\_PATTERN                               | \d+                                                    |                                     |
| EGOV\_USER\_HOST                              |                                                        |                                     |
| EGOV\_CREATE\_USER\_URL                       | /user/users/\_createnovalidate                         |                                     |
| EGOV\_SEARCH\_USER\_URL                       | /user/\_search                                         |                                     |
| EGOV\_UPDATE\_USER\_URL                       | /user/users/\_updatenovalidate                         |                                     |
| EGOV\_USER\_INTEGRATION\_ENABLED              | true                                                   |                                     |
| USER\_SYNC\_ENABLED                           | true                                                   |                                     |
| USER\_SERVICE\_ACCOUNT\_LOCKED                | false                                                  |                                     |
| INDIVIDUAL\_PRODUCER\_UPDATE\_USER\_ID\_TOPIC | update-user-id-topic                                   |                                     |
| NOTIFICATION\_SMS\_ENABLED                    | false                                                  |                                     |

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

**Complaints - PGR: Click** [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/core-services/pgr-services/values.yaml) **to know more.**

| Environment Variables                             | Value                                                                             | Comments                   |
| ------------------------------------------------- | --------------------------------------------------------------------------------- | -------------------------- |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID                | egov-pgr-services                                                                 | <p><br></p>                |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER          | org.apache.kafka.common.serialization.StringSerializer                            | <p><br></p>                |
| SPRING\_KAFKA\_PRODUCER\_VALUE\_SERIALIZER        | org.egov.tracer.kafka.serializer.ISTTimeZoneJsonSerializer                        | <p><br></p>                |
| PGR\_KAFKA\_CREATE\_TOPIC                         | save-pgr-request                                                                  | <p><br></p>                |
| EGOV\_SERVICE\_CREATE\_TOPIC                      | PGR\_KAFKA\_UPDATE\_TOPIC                                                         | <p><br></p>                |
| KAFKA\_TOPICS\_NOTIFICATION\_SMS                  | egov.core.notification.sms                                                        | <p><br></p>                |
| PERSISTER\_SAVE\_TRANSITION\_WF\_TOPIC            | save-wf-transitions                                                               | <p><br></p>                |
| PGR\_KAFKA\_MIGRATION\_TOPIC                      | pgr-migration                                                                     | <p><br></p>                |
| PGR\_KAFKA\_MIGRATION\_PERSISTOR\_TOPIC           | save-pgr-request-batch                                                            | <p><br></p>                |
| PERSISTER\_SAVE\_TRANSITION\_WF\_MIGRATION\_TOPIC | save-wf-transitions-batch                                                         | <p><br></p>                |
| NOTIFICATION\_SMS\_ENABLED                        | <p><br></p>                                                                       | <p><br></p>                |
| REASSIGN\_COMPLAINT\_ENABLED                      | <p><br></p>                                                                       | <p><br></p>                |
| NEW\_COMPLAINT\_ENABLED                           | <p><br></p>                                                                       | <p><br></p>                |
| NOTIFICATION\_EMAIL\_ENABLED                      | <p><br></p>                                                                       | <p><br></p>                |
| EGOV\_IDGEN\_HOST                                 | <p><br></p>                                                                       | Value of IDGEN host server |
| EGOV\_URL\_SHORTNER\_HOST                         | <p><br></p>                                                                       | <p><br></p>                |
| EGOV\_WORKFLOW\_HOST                              | <p><br></p>                                                                       | <p><br></p>                |
| EGOV\_LOCALIZATION\_HOST                          | <p><br></p>                                                                       | <p><br></p>                |
| EGOV\_INFRA\_SEARCHER\_HOST                       | <p><br></p>                                                                       | <p><br></p>                |
| EGOV\_COMMON\_MASTERS\_HOST                       | <p><br></p>                                                                       | <p><br></p>                |
| EGOV\_FILESTORE\_HOST                             | <p><br></p>                                                                       | <p><br></p>                |
| EGOV\_UI\_APP\_HOST                               | <p><br></p>                                                                       | <p><br></p>                |
| EGOV\_USER\_HOST                                  | <p><br></p>                                                                       | <p><br></p>                |
| EGOV\_MDMS\_SEARCH\_ENDPOINT                      | <p><br></p>                                                                       | <p><br></p>                |
| REOPEN\_COMPLAINT\_ENABLED                        | <p><br></p>                                                                       | <p><br></p>                |
| COMMENT\_BY\_EMPLOYEE\_NOTIF\_ENABLED             | <p><br></p>                                                                       | <p><br></p>                |
| EGOV\_PGR\_APP\_PLAYSTORE\_LINK                   | <p><br></p>                                                                       | <p><br></p>                |
| EGOV\_HRMS\_HOST                                  | <p><br></p>                                                                       | <p><br></p>                |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS         | <p><br></p>                                                                       | <p><br></p>                |
| JAVA\_OPTS                                        | <p><br></p>                                                                       | <p><br></p>                |
| JAVA\_ARGS                                        | <p><br></p>                                                                       | <p><br></p>                |
| MANAGEMENT\_SECURITY\_ENABLED                     | false                                                                             | <p><br></p>                |
| SERVER\_PORT                                      | 8080                                                                              | <p><br></p>                |
| SECURITY\_BASIC\_ENABLED                          | false                                                                             | <p><br></p>                |
| EGOV\_LOCATION\_HOST                              | <p><br></p>                                                                       | <p><br></p>                |
| EGOV\_USR\_EVENTS\_NOTIFICATION\_ENABLED          | false                                                                             | <p><br></p>                |
| EGOV\_USR\_EVENTS\_CREATE\_TOPIC                  | persist-user-events-async                                                         | <p><br></p>                |
| EGOV\_USR\_EVENTS\_RATE\_LINK                     | /citizen/otpLogin?mobileNo=$mobile\&redirectTo=feedback/$servicerequestid         | <p><br></p>                |
| EGOV\_USR\_EVENTS\_REOPEN\_LINK                   | /citizen/otpLogin?mobileNo=$mobile\&redirectTo=reopen-complaint/$servicerequestid | <p><br></p>                |
| EGOV\_USR\_EVENTS\_RATE\_CODE                     | RATE                                                                              | <p><br></p>                |
| EGOV\_USR\_EVENTS\_REOPEN\_CODE                   | REOPEN                                                                            | <p><br></p>                |
| ENABLE\_STATE\_LEVEL\_SEARCH                      | true                                                                              | <p><br></p>                |
| PGR\_STATELEVEL\_TENANTID                         | default                                                                           | <p><br></p>                |
| TRACER\_OPENTRACING\_ENABLED                      | true                                                                              | <p><br></p>                |
| PGR\_COMPLAIN\_IDLE\_TIME                         | <p><br></p>                                                                       | <p><br></p>                |

**User Management - HRMS: Click** [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/business-services/egov-hrms/values.yaml) **to know more.**

| Environment Variables                          | Value                                                       | Comments    |
| ---------------------------------------------- | ----------------------------------------------------------- | ----------- |
| EGOV\_SERVICES\_DATA\_SYNC\_EMPLOYEE\_REQUIRED | false                                                       | <p><br></p> |
| EGOV\_MDMS\_HOST                               | http://egov-mdms-service:8080/                              | <p><br></p> |
| EGOV\_MDMS\_SEARCH\_ENDPOINT                   | /egov-mdms-service/v1/\_search                              | <p><br></p> |
| EGOV\_FILESTORE\_HOST                          | http://egov-filestore:8080/                                 | <p><br></p> |
| STATE\_LEVEL\_TENANT\_ID                       | default                                                     | <p><br></p> |
| EGOV\_FILESTORE\_URL\_ENDPOINT                 | /filestore/v1/files/url                                     | <p><br></p> |
| EGOV\_LOCALIZATION\_HOST                       | http://egov-localization:8080/                              | <p><br></p> |
| EGOV\_LOCALIZATION\_SEARCH\_ENDPOINT           | /localization/messages/v1/\_search                          | <p><br></p> |
| EGOV\_IDGEN\_HOST                              | http://egov-idgen:8080/                                     | <p><br></p> |
| EGOV\_SERVICES\_EGOV\_IDGEN\_CREATEPATH        | /egov-idgen/id/\_generate                                   | <p><br></p> |
| EGOV\_SERVICES\_EGOV\_IDGEN\_EMP\_CODE\_NAME   | employee.code                                               | <p><br></p> |
| EGOV\_SERVICES\_EGOV\_IDGEN\_EMP\_CODE\_FORMAT | EMP\_\[SEQ\_EMPLOYEE\_CODE]                                 | <p><br></p> |
| EGOV\_USER\_HOST                               | http://egov-user:8080/                                      | <p><br></p> |
| EGOV\_OTP\_HOST                                | http://egov-otp:8080/                                       | <p><br></p> |
| EGOV\_ENVIRONMENT\_DOMAIN                      | https://health-qa.digit.org/                                | <p><br></p> |
| EGOV\_USER\_SEARCH\_ENDPOINT                   | /user/v1/\_search                                           | <p><br></p> |
| EGOV\_USER\_CREATE\_ENDPOINT                   | /user/users/\_createnovalidate                              | <p><br></p> |
| EGOV\_USER\_UPDATE\_ENDPOINT                   | /user/users/\_updatenovalidate                              | <p><br></p> |
| EGOV\_HRMS\_EMPLOYEE\_APP\_LINK                | <p><br></p>                                                 | <p><br></p> |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID             | employee-group1                                             | <p><br></p> |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER       | org.apache.kafka.common.serialization.StringSerializer      | <p><br></p> |
| SPRING\_KAFKA\_PRODUCER\_VALUE\_SERIALIZER     | org.springframework.kafka.support.serializer.JsonSerializer | <p><br></p> |
| KAFKA\_TOPICS\_SAVE\_SERVICE                   | save-hrms-employee                                          | <p><br></p> |
| KAFKA\_TOPICS\_UPDATE\_SERVICE                 | update-hrms-employee                                        | <p><br></p> |
| KAFKA\_TOPICS\_NOTIFICATION\_SMS               | egov.core.notification.sms                                  | <p><br></p> |
| JAVA\_OPTS                                     | <p><br></p>                                                 | <p><br></p> |
| SERVER\_PORT                                   | 8080                                                        | <p><br></p> |
| JAVA\_ARGS                                     | <p><br></p>                                                 | <p><br></p> |
| SECURITY\_BASIC\_ENABLED                       | false                                                       | <p><br></p> |
| MANAGEMENT\_SECURITY\_ENABLED                  | false                                                       | <p><br></p> |
| EGOV\_HRMS\_AUTO\_GENERATE\_PASSWORD           | false                                                       | <p><br></p> |

## Promotion guide

This section will detail the promotion guide steps for the HCM product.

### Digit Environment Production Setup & deployments

For the DIGIT environment setup, refer to the documentation [here](https://core.digit.org/guides/installation-guide/production-setup).

### HCM Promotion

#### Steps to Create a Tenant for HCM

Refer to the [document](https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/638713938/Configuring+Tenants) for creating a tenant in DIGIT.

#### Steps to Add Localisation Using Rest API

Refer to this [document](https://core.digit.org/platform/core-services/localization-service) for more details.

```
curl --location --request POST 'https://health-dev.digit.org/localization/messages/v1/_upsert' \
--header 'Content-Type: application/json' \
--data-raw '{
   "RequestInfo": {
       "apiId": "Rainmaker",
       "ver": ".01",
       "ts": "",
       "action": "_create",
       "did": "1",
       "key": "",
       "msgId": "20170310130900|en_IN",
       "authToken": "052c8e95-35c1-4f97-b366-c5f23e23ce05"
   },
   "tenantId": "default",
   "messages":[
 {
   "code": "ABG_COMMON_TABLE_COL_ACTION",
   "message": "Action",
   "locale": "en_IN",
   "module": "rainmaker-common"
 },{
   "code": "ABG_COMMON_TABLE_COL_ACTION",
   "message": "Action",
   "locale": "en_IN",
   "module": "rainmaker-common"
 }
]
}'

```

### Steps to Configure the MDMS configs

1. Create Common Masters

&#x20;      a. Create [IdFormat.json](https://github.com/egovernments/health-campaign-mdms/blob/v1.0.0/data/default/common-masters/IdFormat.json) which will be used by [egov-id-gen](https://core.digit.org/platform/core-services/id-generation-service) service.

&#x20;      b. Create [StateInfo.json](https://github.com/egovernments/health-campaign-mdms/blob/v1.0.0/data/default/common-masters/StateInfo.json) which will configure eligible languages for tenant

2. Create sample [boundary data](https://github.com/egovernments/health-campaign-mdms/blob/v1.0.0/data/default/egov-location/boundary-data.json). Refer to this [document](https://core.digit.org/guides/data-setup-guide/location-module) for more details&#x20;
3. Create [field-app-configuration.json](https://github.com/egovernments/health-campaign-mdms/blob/v1.0.0/data/default/egov-location/boundary-data.json) which will be used for drop-down values or select options to be presented in the HCM app&#x20;
4. Create [project-task-configuration.json](https://github.com/egovernments/health-campaign-mdms/blob/v1.0.0/data/default/health/project-task-configuration.json)
5. Create [project-types.json ](https://github.com/egovernments/health-campaign-mdms/blob/v1.0.0/data/default/health/project-types.json)which will be used as a health campaign configuration
6. Create [service-registry.json](https://github.com/egovernments/health-campaign-mdms/blob/v1.0.0/data/default/health/service-registry.json) which has a list of APIs that the HCM app will call.
7. Create PGR/Complaints configs &#x20;
   * [UIConstants.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/RAINMAKER-PGR/UIConstants.json)
   * [ServiceDefs.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/RAINMAKER-PGR/ServiceDefs.json)
   * [RejectionReasons.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/RAINMAKER-PGR/RejectionReasons.json)
   * [ComplainClosingTime.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/RAINMAKER-PGR/ComplainClosingTime.json)
8. Create UserManagemet/HRMS configs
   * [CampaignAssignmentFieldsConfig.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/egov-hrms/CampaignAssignmentFieldsConfig.json)
   * [CommonFieldsConfig.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/egov-hrms/CommonFieldsConfig.json)
   * [DeactivationReason.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/egov-hrms/DeactivationReason.json)
   * [Degree.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/egov-hrms/Degree.json)
   * [EmployeeDepartment.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/egov-hrms/EmployeeDepartment.json)
   * [EmployeeStatus.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/egov-hrms/EmployeeStatus.json)
   * [EmployeeType.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/egov-hrms/EmployeeType.json)
9. Create configs for [Access Control Sevices](https://core.digit.org/platform/core-services/access-control-services)

* [actions-test.json](https://github.com/egovernments/health-campaign-mdms/blob/v1.0.0/data/default/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)
* [roleactions.json ](https://github.com/egovernments/health-campaign-mdms/blob/v1.0.0/data/default/ACCESSCONTROL-ROLEACTIONS/roleactions.json)

8. Configure map-config for the [tenant](https://github.com/egovernments/health-campaign-mdms/tree/v1.0.0/data/default/map-config)

&#x20;Restart the MDMS server and restart the Zuul API gateway.&#x20;

Note: Any modifications in the above configuration, need to restart the MDMS server. Any modifications to action-test.json and roleactions.json require a restart of the Zuul API gateway.

### Steps to Configure Health Campaign Configurations

Step 1: Create a [persister config](https://github.com/egovernments/health-campaign-config/tree/v1.0.0/egov-persister) for each backend service that will be picked by the [persister service](https://core.digit.org/platform/core-services/persister-service).

Step 2: Create an [indexer config](https://github.com/egovernments/health-campaign-config/tree/v1.0.0/egov-indexer) for each backend service which will be picked by the [indexer service](https://core.digit.org/platform/core-services/indexer-service).

Note: Any changes to the indexer and persister configs require the restart of the indexer and the persister.

### Deploy DIGIT Core Services

Refer to this [section](./#release-features-list-of-core-digit-services-used) for a list of core services to be deployed.

### Deploy HCM Services

Refer to this [section](https://health.digit.org/platform/platform-services) for a list of HCM services to be deployed.

### UI/APK Promotion Guide

[https://health.digit.org/product/setup/apk-installation](https://health.digit.org/products/health-campaign-management/frontline-workers-app/installation/app-setup#steps-to-generate-apk)
