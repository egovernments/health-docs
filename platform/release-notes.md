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

