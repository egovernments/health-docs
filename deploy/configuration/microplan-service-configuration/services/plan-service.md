# Plan Service

## Overview

The **Plan Service** manages plan configuration and microplans. It supports create/update/search flows, validations, and workflow-driven processing.

It can run standalone for microplanning. It can also integrate with **HCM Console** for campaign execution, monitoring, and reporting.

For deeper design context (APIs, diagrams, and schemas), see [Microplan - Low Level Design](../../../../design/architecture/low-level-design/services/microplan-low-level-design.md).

## Prerequisites

* Spring Boot
* Git (or another version control system)
* REST APIs
* Kafka
* PostgreSQL
* MDMS and Persister familiarity (helpful)

## Capabilities

### Data upload and configuration

* Upload population, facility, and census inputs (for example `.xlsx`, Shapefiles, GeoJSON).
* Configure assumptions for estimation (demographics, constraints, availability).
* Configure formulas to compute HR, commodities, and budgets.

### Activity and resource planning

* Manage activity sequences and dependencies.
* Estimate and persist required resources per activity.
* Track prerequisites for activities.
* Define targets and track progress.
* Generate microplan outputs (save/print/export).

### Assignments

* Assign employees to hierarchy levels (Province/District/Village).
* Map jurisdictions for clear geographic responsibility.
* Associate facilities to plans, including catchments and boundary metadata.

## Dependencies

* MDMS service
* Persister service
* Census service
* Facility service
* Project Factory
* User service
* Workflow service

## API

Base path:

```
/plan-service
```

Swagger:

{% embed url="https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/DIGIT-Specs/grouped-service-contracts/Domain%20Services/Plan%20Service/plan-1.0.0.yaml" %}

Postman collection:

* [Plan Service Postman collection](https://api.postman.com/collections/13428435-2ff775b4-12de-47ec-8d12-0119860ffdcc?access_key=PMAT-01JJ964XDY0NVDBSF3CS4J3TRM)

## Data model and flow diagrams

{% tabs %}
{% tab title="Microplan schema" %}
<figure><img src="../../../../.gitbook/assets/image (126).png" alt="Microplan schema diagram"><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Plan configuration schema" %}
<figure><img src="../../../../.gitbook/assets/image (127).png" alt="Plan configuration schema diagram"><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Sequence diagram" %}
<figure><img src="../../../../.gitbook/assets/image (128).png" alt="Plan Service sequence diagram"><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

## Kafka topics

### Producer topics

| Topic                      | Purpose                                                                           |
| -------------------------- | --------------------------------------------------------------------------------- |
| `plan-config-create-topic` | Create plan configuration with assumptions, operations, and uploaded files        |
| `plan-config-update-topic` | Update a plan configuration                                                       |
| `save-plan`                | Create a microplan for a locality with provided resources, activities, or targets |
| `update-plan`              | Update a microplan                                                                |

### Consumer topics

| Topic                               | Purpose                                                   |
| ----------------------------------- | --------------------------------------------------------- |
| `resource-microplan-create-topic`   | Trigger microplan creation after resource estimation      |
| `resource-plan-config-update-topic` | Update plan configuration from Resource Generator service |

## Deployment and configuration

* Persister config: [plan-service-persister.yml](https://github.com/egovernments/configs/blob/UNIFIED-UAT/health/egov-persister/plan-service-persister.yml)
* Helm chart: [health-services/plan-service](https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/health-services/plan-service)

### Access control (roles and role-actions)

* Create role `MICROPLAN_ADMIN` in the `ACCESSCONTROL-ROLES` MDMS module.
* Map action IDs to role codes in the `ACCESSCONTROL-ROLEACTIONS` MDMS module.

The mappings below are from a Dev environment setup. Treat them as a baseline.

| API endpoint                      | Roles                                                               |
| --------------------------------- | ------------------------------------------------------------------- |
| **Plan APIs**                     |                                                                     |
| `/plan-service/plan/_create`      | `SYSTEM`                                                            |
| `/plan-service/plan/_search`      | `ROOT_RESOURCE_ESTIMATION_APPROVER`, `RESOURCE_ESTIMATION_APPROVER` |
| `/plan-service/plan/_update`      | `ROOT_RESOURCE_ESTIMATION_APPROVER`, `RESOURCE_ESTIMATION_APPROVER` |
| `/plan-service/plan/bulk/_update` | `ROOT_RESOURCE_ESTIMATION_APPROVER`, `RESOURCE_ESTIMATION_APPROVER` |
| **Plan configuration APIs**       |                                                                     |
| `/plan-service/config/_create`    | `MICROPLAN_ADMIN`                                                   |
| `/plan-service/config/_search`    | `MICROPLAN_ADMIN`                                                   |
| `/plan-service/config/_update`    | `MICROPLAN_ADMIN`                                                   |
| **Plan facility catchment APIs**  |                                                                     |
| `/plan-service/facility/_create`  | `SYSTEM`                                                            |
| `/plan-service/facility/_search`  | `ROOT_FACILITY_CATCHMENT_MAPPER`, `FACILITY_CATCHMENT_MAPPER`       |
| `/plan-service/facility/_update`  | `ROOT_FACILITY_CATCHMENT_MAPPER`, `FACILITY_CATCHMENT_MAPPER`       |
| **Plan employee assignment APIs** |                                                                     |
| `/plan-service/employee/_create`  | `MICROPLAN_ADMIN`                                                   |
| `/plan-service/employee/_search`  | `MICROPLAN_ADMIN`                                                   |
| `/plan-service/employee/_update`  | `MICROPLAN_ADMIN`                                                   |

## Environment variables

Configure environment values in your DIGIT DevOps environment YAMLs (search for `plan-service`):

* [unified-uat.yaml](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/unified-uat.yaml)
* [unified-health-uat.yaml](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/unified-health-uat.yaml)

Common values to review:

* `db-host`, `db-name`, `db-url`, `domain`
* Core platform service configs (for example - persister, filestore)
* DB secrets (Postgres + Flyway) in the environment secrets file
* DIGIT core service secrets in the environment secrets file

Localisation sheet:

* [Localisation details](https://docs.google.com/spreadsheets/d/1wi5c2aOtTiMO0dZtnn2kp3OudOenWkMxisubU_K_5o4/edit?gid=483861604#gid=483861604)

## MDMS

Align Plan Service MDMS with a known-good environment (for example - QA). Typical masters:

* UOM config
* Metric config
* Hypothesis assumptions config
* Input rules config
* Output rules config
* Campaign-based schema
* Microplan status config
* Map layers config
* Map filters config
* Preview aggregates config
* UI configs
* Upload config

Reference dataset:

* [Microplanning MDMS JSON data](https://github.com/egovernments/releasekit/tree/master/mdms/HCM/HCM%20Microplanning%20v0.1/JSON%20Data)

## Reference docs

* [MDMS service](https://core.digit.org/platform/core-services/mdms-master-data-management-service)
* [Persister service](https://core.digit.org/platform/core-services/persister-service)
* [Census service](https://app.gitbook.com/o/-MEQmzNGXk5ajuZujG7E/s/QcWfjoZoghzgUXIbmCOZ/technology/specification/census-service)
* [Facility Registry](../../hcm-service-configuration/facility-registry.md)
* [Project Factory docs](https://app.gitbook.com/o/-MEQmzNGXk5ajuZujG7E/s/IBoO8SBg0T10XuKjUuKN/technology/architecture/services/project-factory)
* [User service](https://core.digit.org/platform/core-services/user)
* [Workflow service](https://core.digit.org/platform/core-services/workflow)
