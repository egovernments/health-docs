# Expense Service

## Overview

The Expense Service within the DIGIT Health Campaign Management (HCM) ecosystem facilitates the creation and management of bills and payments associated with health campaigns. It operates in conjunction with the [Expense Calculator Service](../../../design/architecture/low-level-design/services/expense-calculator.md), which provides the business logic for computing expenses. The Expense Service is primarily invoked by the Expense Calculator to generate bills, which can then be aggregated into payments. Payment advice can be submitted through any third-party payment provider.&#x20;

***

## Pre-requisites

Before deploying the Expense Service, ensure the following configurations are in place:

* **Helm Environment Configuration**: Update the Helm environment file (e.g., `unified-health-qa.yaml`) with the necessary environment variables, including:
  * `db-host`, `db-name`, `db-url`, `domain`
  * Configurations for core DIGIT platform services such as Idgen, workflow, user, etc.
  * Expense service-related environment variables.&#x20;
* **Database Credentials**: Ensure that the Postgres and Flyway database credentials are added to the respective environment secret YAML files.
* **Expense Persister Configuration**: Verify that the expense persister file is included in the `egov-persister.perister-yml-path` variable. If not, follow the outlined steps to add it.

***

## Functionalities

The Expense Service offers the following capabilities:

* **Bill Management**: Create, update, and search bills.
* **Bill Type Configuration**: Define various bill types according to the configuration.
* **Workflow Integration**: Integrate with workflows, which need to be configured for use.
* **Calculator Integration**: Work in conjunction with the Expense Calculator, which contains the business logic to compute bills.

***

## Setup

Before deploying the Expense Service, configure the required environment variables and secrets as outlined below:

1.  **Helm Environment File**\
    Locate the environment YAML file at:

    ```
    https://github.com/{{ORG}}/DIGIT-DevOps/deploy-as-code/helm/environments/{{EnvironmentFile}}.yaml
    ```

    * Add the following variables: `db-host`, `db-name`, `db-url`, `domain`.
    * Configure all DIGIT core platform services (e.g., Idgen, workflow, user, etc.) within this file.
    * Include **muster-roll-service-related variables** in the same way as defined in the [`dev`](https://github.com/egovernments/health-campaign-devops/blob/v1.8/config-as-code/environments/egov-demo.yaml#L684) environment YAML file.
      * [egov-service-host config map](https://github.com/egovernments/health-campaign-devops/blob/v1.8/config-as-code/environments/egov-demo.yaml#L111) - Configure `egov-service-host` in the config map
      * [expense service environment variables](https://github.com/egovernments/health-campaign-devops/blob/v1.8/config-as-code/environments/egov-demo.yaml#L111) - Add **expense service environment variables**
      * [health-expense service helm chart](https://github.com/egovernments/health-campaign-devops/tree/v1.8/config-as-code/helm/charts/health-services/expense) - Reference the **health-expense service helm chart**
2. **Expense Persister Configuration**
   * Verify that the `expense-persister` file is added to the `egov-persister.persister-yml-path` variable.
   * If it is missing, follow the [steps provided here](https://github.com/egovernments/health-campaign-devops/blob/v1.8/config-as-code/environments/egov-demo.yaml#L339).
3. **Database Credentials**
   * Add Postgres and Flyway **DB username and password** in the respective environment secret YAML file. Follow the [steps provided here.](https://github.com/egovernments/health-campaign-devops/blob/v1.8/config-as-code/environments/egov-demo-secrets.yaml#L3)
   * Ensure that all DIGIT core services–related secrets are also configured in the same secret file. Follow the [steps provided here](https://github.com/egovernments/health-campaign-devops/blob/v1.8/config-as-code/environments/egov-demo-secrets.yaml).

## Configuration&#x20;

### Configure Actions

Add all the exposed APIs to the `actions.json` file in MDMS:

* **Module Name**: `ACCESSCONTROL-ACTIONS-TEST`
* **Master Name**: `actions-test`

### Configure Roles

Configure roles in the `roles.json` file:

* **Module Name**: `ACCESSCONTROL-ROLES`
* **Master Name**: `roles`

### Configure Role-Action Mapping

Map roles to actions in the `roleactions.json` file:

* **Module Name**: `ACCESSCONTROL-ROLEACTIONS`
* **Master Name**: `roleactions.json`

Ensure that the role-action mappings align with the defined roles and actions.&#x20;

<table><thead><tr><th width="244.30078125">Roles</th><th>API Endpoints</th></tr></thead><tbody><tr><td>Internal call</td><td>/bill/v1/_create</td></tr><tr><td>Internal call</td><td>/bill/v1/_update</td></tr><tr><td>CAMPAIGN_SUPERVISOR</td><td>/bill/v1/_search</td></tr></tbody></table>

Other expense masters are configured in the **`common-masters`** folder: [IdFormat](https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.8/IdFormat.json#L6)
