# Resource Generator Service

## Overview

The **Resource Generator Service** processes uploaded inputs to generate resource estimations and microplans.

It parses supported file formats, applies configured assumptions and formulas, triggers downstream creation flows, and publishes approved outputs back to the platform (including **HCM Console**).

## Pre-requisites

* Spring Boot
* Git (or another version control system)
* REST APIs
* Kafka
* PostgreSQL
* Familiarity with MDMS, Filestore, Boundary, Project Factory, and Localisation (helpful)

## Capabilities

### File parsing and estimation

* Parses Excel, Shapefiles, and GeoJSON inputs.
* Applies configured assumptions and formulas to compute resource needs.

### Triggers and orchestration

* **Plan–facility creation**: on facility file upload, triggers facility mapping creation via Project Factory.
* **Census creation/update**: on population file upload, triggers census ingestion flows.
* **Microplan generation**: once the census is approved, triggers estimation and microplan generation using the latest approved population data.

{% hint style="info" %}
The service supports mixed registration and distribution strategies. It can intentionally leave some fields `null` based on the `MixedStrategy` master.
{% endhint %}

### Resource mapping

* Maps uploaded columns into the expected campaign attributes.
* Validates schema compatibility before estimation runs.

### Output publishing

* Uploads approved estimation sheets to Filestore.
* Writes the final Filestore reference back to the plan configuration for traceability.

### HCM Console integration

* Publish estimated resources back to Project Factory so Console can surface the latest plan outputs.

## Service Dependencies

* MDMS service
* Filestore service
* Boundary service
* Localisation service
* Census service
* Project Factory
* Plan Service

## API Specification

Swagger:

{% embed url="https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/DIGIT-Specs/grouped-service-contracts/Domain%20Services/Resource%20Generator/resource-1.0.0.yaml" %}

[Postman Collection](https://api.postman.com/collections/13428435-c702603a-b3c5-4954-9f67-17c06e41d225?access_key=PMAT-01JRA0QCZE111Z3JQSM4R8KZEP)

## Sequence Diagram

<figure><img src="../../../../.gitbook/assets/image (129).png" alt="Resource Generator Service sequence diagram"><figcaption></figcaption></figure>

## Kafka topics

### Producer topics

<table><thead><tr><th width="276.99609375">Topic</th><th>Description</th></tr></thead><tbody><tr><td>resource-microplan-create-topic</td><td>Pushes to plan service for microplan creation after resource estimation.</td></tr><tr><td>resource-plan-config-update-topic</td><td>Updates a plan configuration with INVALID_DATA status in case of exception while processing file.</td></tr></tbody></table>

### Consumer topics

<table><thead><tr><th width="227.81640625">Topic</th><th>Description</th></tr></thead><tbody><tr><td>plan-config-update-topic</td><td>Triggers resource estimation, microplan creation, and campaign manager integration.</td></tr></tbody></table>

## Deployment configuration

### Environment variables

Configure values in your DIGIT DevOps environment YAMLs (search for `resource` / `resource-generator`):

* DB config: `db-host`, `db-name`, `db-url`, `domain`
* Core platform service configs (for example: persister, filestore)
* Secrets in the environment secrets file:
  * [unified-qa-secrets.yaml](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/unified-qa-secrets.yaml)
  * [unified-uat-secrets.yaml](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/unified-uat-secrets.yaml)

Localisation sheet:

* [Localisation details](https://docs.google.com/spreadsheets/d/1wi5c2aOtTiMO0dZtnn2kp3OudOenWkMxisubU_K_5o4/edit?gid=483861604#gid=483861604)

## MDMS

MDMS for Resource Generator is tightly coupled to microplanning masters used by Plan Service.

References:

* [Plan Service](plan-service.md)
* [Microplanning MDMS JSON data (v0.2)](https://github.com/egovernments/releasekit/tree/master/mdms/HCM/HCM%20Microplanning%20v0.2/JSON%20Data)

### Reference Docs <a href="#reference-docs" id="reference-docs"></a>

* [MDMS Service](https://core.digit.org/platform/core-services/mdms-master-data-management-service)
* [Filestore Service](https://core.digit.org/platform/core-services/filestore-service)
* [Boundary Service](https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/2388295698/Boundary+Service)
* [Localisation Service](https://core.digit.org/platform/core-services/localization-service)
* [Project Factory - Campaign Manager](../../../../design/architecture/low-level-design/services/console-services/project-factory-campaign-manager/)
* [Plan Service](plan-service.md)
