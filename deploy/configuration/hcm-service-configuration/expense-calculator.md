---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-service-configuration/expense-calculator
---

# Expense Calculator

## Overview

The **Expense Calculator Service** is a core component of DIGIT HCM that applies business logic to calculate campaign expenses. It works closely with the Expense Service: after performing calculations, it prepares the payload for bill creation and generates Excel and PDF formats of the resulting bills.

The service supports different types of bills (e.g., wage bills based on approved muster rolls, paid to workers after work completion).

## Pre-requisites <a href="#dependency" id="dependency"></a>

Before deploying the Expense Calculator, ensure the following are available:

* **DIGIT Core Services** (Idgen, Workflow, User, etc.) are configured and accessible.
* **Supporting Services** such as:
  * Persister
  * MDMS (Master Data Management System)
  * Attendance Service
  * Muster Roll Service
  * Project Service
  * Individual Service / Registry
  * Expense Service
  * Localization
  * PdfService (for generating documents)
  * Filestore (for storing and retrieving files)

## Functionalities

* **Calculation API**: Retrieves attendance and computes payable amounts using MDMS-defined rates, roles, and worker skills.
* **Bill Generation**: Prepares and submits payloads to the Expense Service to create bills.
* **Document Creation**: Produces Excel and PDF versions of bills for record-keeping and distribution.

## Setup

*   **Helm Environment Configuration**

    *   Locate the environment file:

        ```
        https://github.com/{{ORG}}/DIGIT-DevOps/deploy-as-code/helm/environments/{{EnvironmentFile}}.yaml
        ```

    Refer to the [sample here](https://github.com/egovernments/DIGIT-DevOps/blob/digit-works/deploy-as-code/helm/environments/works-dev.yaml).

    * Add:
      * `db-host`, `db-name`, `db-url`, `domain`
      * DIGIT core services configurations (Idgen, workflow, user, etc.)
      * Expense Calculator environment variables (reference [`dev` ](https://github.com/egovernments/DIGIT-DevOps/blob/5a9eb4c6141e19bd747238889ceed9bc9fffdc6f/deploy-as-code/helm/environments/works-dev.yaml#L175)environment for examples)
      * [service-host-config-map](https://github.com/egovernments/health-campaign-devops/blob/v1.8/config-as-code/environments/egov-demo.yaml#L112) - Update the `egov-service-host` config map.
      * ​[expense service environment variables](https://github.com/egovernments/health-campaign-devops/blob/v1.8/config-as-code/environments/egov-demo.yaml#L111) -&#x20;
      * ​[health-expense calculator service helm chart](https://github.com/egovernments/health-campaign-devops/tree/v1.8/config-as-code/helm/charts/health-services/expense) - Reference the **health-expense-calculator** helm chart
* **Secrets and Credentials**
  * Add Postgres and Flyway DB credentials (username and password) in the environment secret YAML file as per the steps outlined[ here](https://github.com/egovernments/health-campaign-devops/blob/v1.8/config-as-code/environments/egov-demo-secrets.yaml#L3).
  * Configure secrets for DIGIT core services in the same secret file as per the steps outlined[ here](https://github.com/egovernments/DIGIT-DevOps/blob/digit-works/deploy-as-code/helm/environments/works-dev-secrets.yaml).

## Configuration&#x20;

### Actions

* Add Expense Calculator APIs (e.g., `/health-expense-calculator/v1/_calculator`) to `actions.json` in MDMS.
* **Module Name**: `ACCESSCONTROL-ACTIONS-TEST`
* **Master Name**: `actions-test`

### Roles

* Define the necessary roles in `roles.json`.
* **Module Name**: `ACCESSCONTROL-ROLES`
* **Master Name**: `roles`

### Role-Action Mapping

* Map APIs to roles in `roleactions.json`.
* **Module Name**: `ACCESSCONTROL-ROLEACTIONS`
* **Master Name**: `roleactions.json`

<table><thead><tr><th width="302">Roles</th><th>API Endpoints</th></tr></thead><tbody><tr><td>CAMPAIGN_SUPERVISOR</td><td>/health-expense-calculator/v1/_calculator</td></tr></tbody></table>

#### Other masters to be added

Other muster roll masters are configured in the **`common-masters`** folder: [workerRates.json](https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.8/workerRates.json)
