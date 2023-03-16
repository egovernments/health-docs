# Release Notes

## Version: 1.0&#x20;

### Release date: 03/03/2023

## Release Summary&#x20;

DIGIT Health 1.0 covers individual, household, facility, product, project, and stock services, as well as service requests.

## Features&#x20;

The following applications are part of the release

| Service         | Tag                                    | Description                                                                                                                               |
| --------------- | -------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Individual      | egovio/individual:qa-247a48c674-21     | Individual service built into the DIGIT platform. All the CRUD operations are allowed using API.                                          |
| Household       | egovio/household-db:qa-689445a57c-31   | Household service enables one to create households and add members to a household.                                                        |
| Facility        | egovio/facility:qa-972edcca9a-13       | Facility services provide the APIs to create, update, delete and read facilities.                                                         |
| Product         | egovio/product:qa-0ec164c4d3-7         | Product services provide the APIs for CRUD operations for products and product variants.                                                  |
| Project         | egovio/project:qa-e5087fd79c-60        | Project services provide the APIs for CRUD operations for project, project task, project staff, project resource and project beneficiary. |
| Stock           | egovio/stock:qa-ff36d52eb2-23          | Stock services provide the APIs for creating, updating, and deleting stock receipts and stock reconciliations.                            |
| Service request | egovio/service-request:qa-2b9bf0593e-5 | Service requests provide the create and submission APIs for checklists.                                                                   |

## List of DIGIT Services Used

| Service            | Image                                              |
| ------------------ | -------------------------------------------------- |
| Access control     | egovio/egov-accesscontrol:v1.1.3-72f8a8f87b-24     |
| Encryption service | egovio/egov-enc-service:v1.1.2-72f8a8f87b-9        |
| File store         | egovio/egov-filestore:v1.2.4-72f8a8f87b-10         |
| Localisation       | egovio/egov-localization:v1.1.3-72f8a8f87b-6       |
| ID generation      | egovio/egov-idgen:v1.2.3-72f8a8f87b-7              |
| Indexer            | egovio/egov-indexer:v1.1.7-f52184e6ba-25           |
| Location           | egovio/egov-location:v1.1.4-72f8a8f87b-6           |
| MDMS               | egovio/egov-mdms-service:v1.3.2-72f8a8f87b-12      |
| Notification mai   | egovio/egov-notification-mail:v1.1.2-72f8a8f87b-12 |
| Notification SMS   | egovio/egov-notification-sms:v1.1.3-48a03ad7bb-10  |
| OTP                | egovio/egov-otp:v1.2.2-72f8a8f87b-12               |
| Persister          | egovio/egov-persister:v1.1.4-72f8a8f87b-6          |
| Searcher           | egovio/egov-searcher:v1.1.5-72f8a8f87b-16          |
| URL Sshortening    | egovio/egov-url-shortening:v1.1.2-1715164454-3     |
| User               | egovio/egov-user:v1.2.7-cc363f0584-12              |
| User OTP           | egovio/user-otp:v1.1.5-1715164454-3                |
| Workflow           | egovio/egov-workflow-v2:v1.2.1-df98ec3c35-2        |
| Report             | egovio/report:v1.3.4-96b24b0d72-16                 |
| Document uploader  | egovio/egov-document-uploader:v1.1.0-75d461a4d2-4  |
| Playground         | egovio/playground:1.0                              |

## Environment Variables for HCM Services

Individual: Click [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/health-services/individual/values.yaml) to know more.

| Environment variables                     | Value                                                  | Comments                            |
| ----------------------------------------- | ------------------------------------------------------ | ----------------------------------- |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID        | health-individual                                      |                                     |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER  | org.apache.kafka.common.serialization.StringSerializer |                                     |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS |                                                        |                                     |
| EGOV\_IDGEN\_HOST                         |                                                        | Value of IDGEN host server          |
| EGOV\_IDGEN\_PATH                         | egov-idgen/id/\_generate                               |                                     |
| EGOV\_IDGEN\_INTEGRATION\_ENABLED         | true/false                                             |                                     |
| IDGEN.INDIVIDUAL.ID.FORMAT                | individual.id                                          |                                     |
| SPRING\_REDIS\_HOST                       | redis.backbone                                         |                                     |
| SPRING\_REDIS\_PORT                       |                                                        |                                     |
| SPRING\_CACHE\_TYPE                       | redis                                                  |                                     |
| SPRING\_CACHE\_REDIS\_TIME-TO-LIVE        |                                                        |                                     |
| SPRING\_CACHE\_AUTOEXPIRY                 | true                                                   |                                     |
| JAVA\_OPTS                                |                                                        |                                     |
| JAVA\_ARGS                                |                                                        |                                     |
| JAVA\_ENABLE\_DEBUG                       |                                                        |                                     |
| SERVER\_PORT                              |                                                        |                                     |
| SECURITY\_BASIC\_ENABLED                  | false                                                  |                                     |
| MANAGEMENT\_SECURITY\_ENABLED             | false                                                  |                                     |
| TRACER\_OPENTRACING\_ENABLED              | true/false                                             |                                     |
| INDIVIDUAL.CONSUMER.SAVE.TOPIC            | save-individual-topic                                  | Topic to save individual            |
| INDIVIDUAL.CONSUMER.UPDATE.TOPIC          | update-individual-topic                                | Topic to update individual          |
| INDIVIDUAL.CONSUMER.DELETE.TOPIC          | delete-individual-topic                                | Topic to delete individua           |
| INDIVIDUAL.CONSUMER.BULK.CREATE.TOPIC     | individual-consumer-bulk-create-topic                  | Topic to create individuals in bulk |
| INDIVIDUAL.CONSUMER.BULK.UPDATE.TOPIC     | individual-consumer-bulk-update-topic                  | Topic to update individuals in bulk |
| INDIVIDUAL.CONSUMER.BULK.DELETE.TOPIC     | individual-consumer-bulk-delete-topic                  | Topic to delete individuals in bulk |

Household: Click [here](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/health-services/household/values.yaml) to know more.

| Environment variables                       | Value                                                  | Comments                               |
| ------------------------------------------- | ------------------------------------------------------ | -------------------------------------- |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID          | health-household                                       |                                        |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER    | org.apache.kafka.common.serialization.StringSerializer |                                        |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS   |                                                        | Value of IDGEN host serve              |
| EGOV\_IDGEN\_HOST                           |                                                        |                                        |
| EGOV\_IDGEN\_PATH                           | egov-idgen/id/\_generate                               |                                        |
| EGOV\_IDGEN\_INTEGRATION\_ENABLED           | true/false                                             |                                        |
| HOUSEHOLD.IDGEN.ID.FORMAT                   | household.id                                           |                                        |
| SPRING\_REDIS\_HOST                         | redis.backbone                                         |                                        |
| SPRING\_REDIS\_PORT                         | 6379                                                   |                                        |
| SPRING\_CACHE\_TYPE                         | redis                                                  |                                        |
| SPRING\_CACHE\_REDIS\_TIME-TO-LIVE          |                                                        |                                        |
| SPRING\_CACHE\_AUTOEXPIRY                   | true                                                   |                                        |
| JAVA\_OPTS                                  |                                                        |                                        |
| JAVA\_ARGS                                  |                                                        |                                        |
| JAVA\_ENABLE\_DEBUG                         |                                                        |                                        |
| SERVER\_PORT                                | 8080                                                   |                                        |
| SECURITY\_BASIC\_ENABLED                    | false                                                  |                                        |
| MANAGEMENT\_SECURITY\_ENABLED               | false                                                  |                                        |
| TRACER\_OPENTRACING\_ENABLED                | true/false                                             |                                        |
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

Product: Click [here](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/health-services/product/values.yaml) to know more.

| Environment variables                     | Value                                                  | Comments                        |
| ----------------------------------------- | ------------------------------------------------------ | ------------------------------- |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID        | health-product                                         |                                 |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER  | org.apache.kafka.common.serialization.StringSerializer |                                 |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS |                                                        |                                 |
| EGOV\_IDGEN\_HOST                         |                                                        | Value of IDGEN host server      |
| EGOV\_IDGEN\_PATH                         | egov-idgen/id/\_generate                               |                                 |
| EGOV\_IDGEN\_INTEGRATION\_ENABLED         | true/false                                             |                                 |
| SPRING\_REDIS\_HOST                       | redis.backbone                                         |                                 |
| SPRING\_REDIS\_PORT                       | 6379                                                   |                                 |
| SPRING\_CACHE\_TYPE                       | redis                                                  |                                 |
| SPRING\_CACHE\_REDIS\_TIME-TO-LIVE        |                                                        |                                 |
| SPRING\_CACHE\_AUTOEXPIRY                 | true                                                   |                                 |
| JAVA\_OPTS                                |                                                        |                                 |
| JAVA\_ARGS                                |                                                        |                                 |
| JAVA\_ENABLE\_DEBUG                       |                                                        |                                 |
| SERVER\_PORT                              | 8080                                                   |                                 |
| SECURITY\_BASIC\_ENABLED                  | false                                                  |                                 |
| MANAGEMENT\_SECURITY\_ENABLED             | false                                                  |                                 |
| TRACER\_OPENTRACING\_ENABLED              | true/false                                             |                                 |
| PRODUCT\_KAFKA\_CREATE\_TOPIC             | save-product-topic                                     | Topic to save product           |
| PRODUCT\_KAFKA\_UPDATE\_TOPIC             | update-product-topic                                   | Topic to update product         |
| PRODUCT\_VARIANT\_KAFKA\_CREATE\_TOPIC    | save-product-variant-topic                             | Topic to create product variant |
| PRODUCT\_VARIANT\_KAFKA\_UPDATE\_TOPIC    | update-product-variant-topic                           | Topic to update product variant |

Facility: Click **** [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/health-services/facility/values.yaml) to know more.

| Environment variables                     | Value                                                  | Comments                   |   |
| ----------------------------------------- | ------------------------------------------------------ | -------------------------- | - |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID        | health-project                                         |                            |   |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER  | org.apache.kafka.common.serialization.StringSerializer |                            |   |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS |                                                        |                            |   |
| EGOV\_IDGEN\_HOST                         |                                                        | Value of IDGEN host server |   |
| EGOV\_IDGEN\_PATH                         | egov-idgen/id/\_generate                               |                            |   |
| EGOV\_IDGEN\_INTEGRATION\_ENABLED         | true/false                                             |                            |   |
| FACILITY.IDGEN.ID.FORMAT                  | facility.id                                            |                            |   |
| SPRING\_REDIS\_HOST                       | redis.backbone                                         |                            |   |
| SPRING\_REDIS\_PORT                       | 6379                                                   |                            |   |
| SPRING\_CACHE\_TYPE                       | redis                                                  |                            |   |
| SPRING\_CACHE\_REDIS\_TIME-TO-LIVE        |                                                        |                            |   |
| SPRING\_CACHE\_AUTOEXPIRY                 | true                                                   |                            |   |
| JAVA\_OPTS                                |                                                        |                            |   |
| JAVA\_ARGS                                |                                                        |                            |   |
| JAVA\_ENABLE\_DEBUG                       |                                                        |                            |   |
| SERVER\_PORT                              |                                                        |                            |   |
| SECURITY\_BASIC\_ENABLED                  | false                                                  |                            |   |
| MANAGEMENT\_SECURITY\_ENABLED             | false                                                  |                            |   |
| TRACER\_OPENTRACING\_ENABLED              | true/false                                             |                            |   |
| FACILITY.KAFKA.CREATE.TOPIC               | save-facility-topic                                    |                            |   |
| FACILITY.KAFKA.UPDATE.TOPIC               | update-facility-topic                                  |                            |   |
| FACILITY.KAFKA.DELETE.TOPIC               | delete-facility-topic                                  |                            |   |
| FACILITY.CONSUMER.BULK.CREATE.TOPIC       | create-facility-bulk-topic                             |                            |   |
| FACILITY.CONSUMER.BULK.UPDATE.TOPIC       | update-facility-bulk-topic                             |                            |   |
| FACILITY.CONSUMER.BULK.DELETE.TOPIC       | delete-facility-bulk-topic                             |                            |   |

Project: Click [**here**](https://github.com/egovernments/health-campaign-devops/blob/master/deploy-as-code/helm/charts/health-services/project/values.yaml) to know more.

| Environment variables                     | Value                                                  | Comments                                       |   |
| ----------------------------------------- | ------------------------------------------------------ | ---------------------------------------------- | - |
| SPRING\_KAFKA\_CONSUMER\_GROUP\_ID        | health-project                                         |                                                |   |
| SPRING\_KAFKA\_PRODUCER\_KEY\_SERIALIZER  | org.apache.kafka.common.serialization.StringSerializer |                                                |   |
| TRACER\_ERRORS\_PROVIDEEXCEPTIONINDETAILS |                                                        |                                                |   |
| EGOV\_IDGEN\_HOST                         |                                                        | Value of IDGEN host server                     |   |
| EGOV\_IDGEN\_PATH                         | egov-idgen/id/\_generate                               |                                                |   |
| EGOV\_IDGEN\_INTEGRATION\_ENABLED         | true/false                                             |                                                |   |
| PROJECT.STAFF.IDGEN.ID.FORMAT             | project.staff.id                                       | Project staff ID generated format              |   |
| PROJECT.FACILITY.IDGEN.ID.FORMAT          | project.facility.id                                    | Project facility id generated format           |   |
| PROJECT.TASK.IDGEN.ID.FORMAT              | project.task.id                                        | Project task id generated format               |   |
| IDGEN.PROJECT.BENEFICIARY.ID.FORMAT       | project.beneficiary.id                                 | Project beneficiary id generated format        |   |
| EGOV\_USER\_CONTEXT\_PATH                 |                                                        | User service context path                      |   |
| EGOV\_SEARCH\_USER\_URL                   | /user/\_search                                         | User service search url                        |   |
| EGOV\_USER\_INTEGRATION\_ENABLED          | true/false                                             | User service integration enabled if it is true |   |
| SPRING\_REDIS\_HOST                       | redis.backbone                                         |                                                |   |
| SPRING\_REDIS\_PORT                       | 6379                                                   |                                                |   |
| SPRING\_CACHE\_TYPE                       | redis                                                  |                                                |   |
| SPRING\_CACHE\_REDIS\_TIME-TO-LIVE        |                                                        |                                                |   |
| SPRING\_CACHE\_AUTOEXPIRY                 | true                                                   |                                                |   |
| JAVA\_OPTS                                |                                                        |                                                |   |
| JAVA\_ARGS                                |                                                        |                                                |   |
| JAVA\_ENABLE\_DEBUG                       |                                                        |                                                |   |
| SERVER\_PORT                              | 8080                                                   |                                                |   |
| SECURITY\_BASIC\_ENABLED                  | false                                                  |                                                |   |
| MANAGEMENT\_SECURITY\_ENABLED             | false                                                  |                                                |   |
| TRACER\_OPENTRACING\_ENABLED              | true/false                                             |                                                |   |
| EGOV\_LOCATION\_CONTEXT\_PATH             | /egov-location/location/v11                            |                                                |   |
| EGOV\_LOCATION\_ENDPOINT                  | /boundarys/\_search                                    | eGov location end -point                       |   |
| EGOV\_MDMS\_INTEGRATION\_ENABLED          | true/false                                             |                                                |   |
| EGOV\_MDMS\_MASTER\_NAME                  | project\_master                                        | Creating an MDMS service bean                  |   |
| EGOV\_MDMS\_MODULE\_NAME                  | project                                                | Not required                                   |   |
| EGOV\_HOUSEHOLD\_HOST                     |                                                        | Host of the household service                  |   |
| EGOV\_INDIVIDUAL\_HOST                    |                                                        |                                                |   |
| EGOV\_SEARCH\_INDIVIDUAL\_URL             | /individual/v1/\_search                                | Search the URL of the individual               |   |
| EGOV\_PRODUCT\_HOST                       |                                                        | Host of the product service                    |   |
| EGOV\_SEARCH\_PRODUCT\_VARIANT\_URL       | /product/variant/v1/\_search                           | The URL of the product variant search          |   |
| PROJECT.TASK.KAFKA.CREATE.TOPIC           | save-project-task-topic                                | The topic to save the project task             |   |
| PROJECT.TASK.CONSUMER.BULK.CREATE.TOPIC   | save-project-task-bulk-topic                           | The topic to save the bulk project tasks       |   |
| PROJECT.TASK.KAFKA.UPDATE.TOPIC           | update-project-task-topic                              | The topic to update the project task           |   |
| PROJECT.TASK.CONSUMER.BULK.UPDATE.TOPIC   | update-project-task-bulk-topic                         | The topic to update the bulk project tasks     |   |
| PROJECT.TASK.KAFKA.DELETE.TOPIC           | delete-project-task-topic                              | The topic to delete the project task           |   |
| PROJECT.TASK.CONSUMER.BULK.DELETE.TOPIC   | delete-project-task-bulk-topic                         | The topic to delete the bulk project tasks     |   |
| PROJECT.BENEFICIARY.KAFKA.CREATE.TOPIC    |                                                        |                                                |   |
|                                           |                                                        |                                                |   |

\
\




