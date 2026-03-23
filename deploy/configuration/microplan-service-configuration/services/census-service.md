# Census Service

## Overview

The **Census Service** manages population census datasets used by microplanning and estimation.

It creates and updates census records for boundaries, validates jurisdiction and roles, and enforces record validity windows. It then exposes approved census data for downstream services (for example: Resource Generator and Plan Service).

For detailed API flows, sequence diagrams, and DB schemas, see [Microplan - Low Level Design](../../../../design/architecture/low-level-design/services/microplan-low-level-design.md).

## Prerequisites

* Spring Boot
* Git (or another version control system)
* REST APIs
* Kafka
* PostgreSQL
* MDMS and Persister familiarity (helpful)

## Capabilities

### Census record lifecycle

* Create census records for specific boundaries.
* Categorise census records by population type (for example: people, animals, plants).
* Update records and support bulk updates.

### Demographic payloads

* Store population values by demographic dimensions (for example: age, gender, ethnicity).
* Example age-group payload:

```json
{"0-14": 1000, "15-24": 8000}
```

### Validation and governance

* Validate boundaries via the Boundary service.
* Enforce role-based access and workflow.
* Manage and update record validity periods (time windows).

### Integration with microplanning

* Supports Plan Service and Resource Generator flows by providing approved census datasets.
* Supports facility-to-boundary assignment flows that can affect census coverage.

## Service Dependencies

* Boundary service
* Plan Service
* Workflow service
* Persister service

## Base URL

```
/census-service
```

## API Specification

Swagger:

{% embed url="https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/DIGIT-Specs/refs/heads/grouped-service-contracts/Domain%20Services/Census/census-v1.0.0.yaml" %}

Postman:

* [Census Service Postman collection](https://api.postman.com/collections/36294834-561ba781-0903-46e3-94ef-72122e95e7ea?access_key=PMAT-01J9K1TNEP5RN5ZS1VJH14GFX4)

## Typical flow

1. Create or bulk-create a census record for a boundary.
2. Validate boundary + permissions (Boundary service + role-action mapping).
3. Move the record through workflow to approval (Workflow service).
4. Downstream services consume the approved dataset for estimation and planning.

## Kafka topics

### Producer topics

| Topic                      | Purpose                               |
| -------------------------- | ------------------------------------- |
| `census-create-topic`      | Create a census record for a boundary |
| `census-update-topic`      | Update a census record                |
| `census-bulk-update-topic` | Bulk update census records            |

### Consumer topics

| Topic                          | Purpose                                             |
| ------------------------------ | --------------------------------------------------- |
| `resource-census-create-topic` | Trigger census creation after resource estimation   |
| `update-plan-facility`         | Mark census boundaries where a facility is assigned |

## Deployment and configuration

### Configurations and Helm chart

* Persister config: [https://github.com/egovernments/configs/blob/UNIFIED-UAT/health/egov-persister/census-service-persister.yml](https://github.com/egovernments/configs/blob/UNIFIED-UAT/health/egov-persister/census-service-persister.yml)​
* Helm chart details: [https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/health-services/census-service](https://github.com/egovernments/DIGIT-DevOps/tree/unified-env/deploy-as-code/helm/charts/health-services/census-service)​

### Access control (roles and role-actions)

* Create roles in the `ACCESSCONTROL-ROLES` MDMS module:
  * `MICROPLAN_ADMIN`
  * `ROOT_POPULATION_DATA_APPROVER`, `POPULATION_DATA_APPROVER`
  * `ROOT_FACILITY_CATCHMENT_MAPPER`, `FACILITY_CATCHMENT_MAPPER`
* Map action IDs to roles in `ACCESSCONTROL-ROLEACTIONS`.

The mappings below are from a Dev environment setup. Treat them as a baseline.

| API endpoint                   | Roles                                                                                                                      |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| `/census-service/_create`      | `MICROPLAN_ADMIN`                                                                                                          |
| `/census-service/_search`      | `ROOT_POPULATION_DATA_APPROVER`, `POPULATION_DATA_APPROVER`, `ROOT_FACILITY_CATCHMENT_MAPPER`, `FACILITY_CATCHMENT_MAPPER` |
| `/census-service/_update`      | `ROOT_POPULATION_DATA_APPROVER`, `POPULATION_DATA_APPROVER`, `ROOT_FACILITY_CATCHMENT_MAPPER`, `FACILITY_CATCHMENT_MAPPER` |
| `/census-service/bulk/_update` | `ROOT_POPULATION_DATA_APPROVER`, `POPULATION_DATA_APPROVER`, `ROOT_FACILITY_CATCHMENT_MAPPER`, `FACILITY_CATCHMENT_MAPPER` |

### Environment variables

Below are the variables that should be configured before deployment of the census service build image:

* Use the existing environment YAMLs as reference (search for `census-service`):
  * [unified-uat.yaml](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/unified-uat.yaml)
  * [unified-health-uat.yaml](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/unified-health-uat.yaml)
* Configure DB and core service connectivity:
  * `db-host`, `db-name`, `db-url`, `domain`
  * Persister, boundary, and other platform service URLs
* Add DB (Postgres + Flyway) credentials and DIGIT core secrets in the environment secrets file:
  * [unified-uat-secrets.yaml](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/unified-uat-secrets.yaml)

Localisation sheet:

* [Localisation details](https://docs.google.com/spreadsheets/d/1wi5c2aOtTiMO0dZtnn2kp3OudOenWkMxisubU_K_5o4/edit?gid=483861604#gid=483861604)

### MDMS

No Census-specific MDMS masters are documented here. The service relies on shared platform masters (for example: access control, workflows, and boundary hierarchies).

### Reference Docs <a href="#reference-docs" id="reference-docs"></a>

* [Persister service](https://core.digit.org/platform/core-services/persister-service)
* [Boundary Service](https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/2388295698/Boundary+Service)
* [Plan Service](plan-service.md)
* ​[API Contract](https://github.com/egovernments/DIGIT-Specs/blob/grouped-service-contracts/Domain%20Services/Census/census-v1.0.0.yaml)
* [Postman Collection](https://api.postman.com/collections/36294834-561ba781-0903-46e3-94ef-72122e95e7ea?access_key=PMAT-01J9K1TNEP5RN5ZS1VJH14GFX4)
