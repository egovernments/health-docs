# Expense Service

## Overview

The expense module implements the functionality of bills and payments. A bill or a group of bills can be aggregated together as payments. Payment advice can be submitted through any other third-party payment provider. The expense module always works in combination with a calculator service. The calculator service is implementation-specific and provides business logic to compute bills. The calculator calls into the expense service to create bills. In general, the expense create/update APIs are not called by any other module other than the calculator.

[Click here ](../../../design/architecture/low-level-design/services/expense-calculator.md)to browse for more information on the sample calculator provided with the Health platform.

## Functionalities <a href="#functionalities" id="functionalities"></a>

* Create/update/search functionality for bills
* Ability to create different bill types according to configuration.
* The workflow is integrated and needs to be configured for use.
* Works with an expense calculator that contains the business logic to compute bills.

## Deployment Details

Here is a list of variables that need to be configured in the Helm environment file before deploying the expense service. This file can typically be found under a specific directory or location as given below:

`https://github.com/`<mark style="color:red;">`{{ORG}}`</mark>`/DIGIT-DevOps/deploy-as-code/helm/environments/`<mark style="color:red;">`{{EnvironmentFile}}`</mark>`.yaml`

Add these ‘db-host’,’db-name’,’db-url’, ’domain’ and all the digit core platform services configurations (Idgen, workflow, user, etc.) in the respective environments yaml file.

Add muster-roll-service related environment variables’ value like the way it's done in the[ ‘dev](https://github.com/egovernments/DIGIT-DevOps/blob/5a9eb4c6141e19bd747238889ceed9bc9fffdc6f/deploy-as-code/helm/environments/works-dev.yaml#L175)’ environment yaml file.

* [https://github.com/egovernments/DIGIT-DevOps/blob/47594728968d9551990b0da81294f7898aceada2/deploy-as-code/helm/environments/unified-health-qa.yaml#L166](https://github.com/egovernments/DIGIT-DevOps/blob/47594728968d9551990b0da81294f7898aceada2/deploy-as-code/helm/environments/unified-health-qa.yaml#L166)
* [https://github.com/egovernments/DIGIT-DevOps/blob/07bdd11e0c91053cb434cd2a79f785e59e2785c8/deploy-as-code/helm/environments/unified-health-qa.yaml#L335-L343](https://github.com/egovernments/DIGIT-DevOps/blob/07bdd11e0c91053cb434cd2a79f785e59e2785c8/deploy-as-code/helm/environments/unified-health-qa.yaml#L335-L343)
* [https://github.com/egovernments/DIGIT-DevOps/tree/07bdd11e0c91053cb434cd2a79f785e59e2785c8/deploy-as-code/helm/charts/health-services/health-expense](https://github.com/egovernments/DIGIT-DevOps/tree/07bdd11e0c91053cb434cd2a79f785e59e2785c8/deploy-as-code/helm/charts/health-services/health-expense)

Check the expense persister file is added to the **`egov-persister.perister-yml-path`** variable. If not, follow the steps outlined [here](https://github.com/egovernments/DIGIT-DevOps/blob/47594728968d9551990b0da81294f7898aceada2/deploy-as-code/helm/environments/unified-health-qa.yaml#L418)

Make sure to add the DB(Postgres and flyway) username & password in the respective environment secret YAML file as per the steps outlined[ here](https://github.com/egovernments/DIGIT-DevOps/blob/e742a292f2966bb1affb3b03edd643a777917ba1/deploy-as-code/helm/environments/works-dev-secrets.yaml#L3).

Make sure to add the digit core services-related secrets that are configured in the respective environment secret file as per the steps outlined[ here](https://github.com/egovernments/DIGIT-DevOps/blob/digit-works/deploy-as-code/helm/environments/works-dev-secrets.yaml).

## Configuration Details

### Configure Actions

Add all the APIs exposed (refer to the table below for actual APIs) to the actions.json file in MDMS

**Module name:** ACCESSCONTROL-ACTIONS-TEST

**Master name:** actions-test

### Configure Roles

Configure roles based on the roles column below in roles.json file.&#x20;

**Module name:** ACCESSCONTROL-ROLES

**Master name:** roles

### Configure Role-Action

Role-action mapping is configured in MDMS per the table below.&#x20;

**Module name:** ACCESSCONTROL-ROLEACTIONS

**Master name:** roleactions.json

<table><thead><tr><th width="302">Roles</th><th>API Endpoints</th></tr></thead><tbody><tr><td>Internal call</td><td>/bill/v1/_create</td></tr><tr><td>Internal call</td><td>/bill/v1/_update</td></tr><tr><td>CAMPAIGN_SUPERVISOR </td><td>/bill/v1/_search</td></tr></tbody></table>

#### Other masters to be added

Other expense masters are configured in the **`common-masters`** folder:

[IdFormat](https://github.com/egovernments/egov-mdms-data/blob/c97c260d595a091aa9f7a8890eac1154169ca4a8/data/mz/common-masters/IdFormat.json#L6)
