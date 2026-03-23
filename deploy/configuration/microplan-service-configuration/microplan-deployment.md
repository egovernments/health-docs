# Microplan Deployment

## Overview

This page is the deployment-oriented companion for Microplanning. It links to Helm values for each Microplanning service and summarises the shared database + migration settings. Use it when you’re setting up a new environment, troubleshooting connectivity, or validating Flyway runs.

## Helm Configurations

The following are the service helm charts:

**Census Service:**

{% embed url="https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/charts/health-services/census-service/values.yaml" %}
Census Service Helm Chart
{% endembed %}

**Plan Service:**

{% embed url="https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/charts/health-services/plan-service/values.yaml" %}
Plan Service Helm Chart
{% endembed %}

**Resource Generator:**

{% embed url="https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/charts/health-services/resource-generator/values.yaml" %}
Resource Generator Helm Chart
{% endembed %}

***

## Database & Migration Configuration

**Database Configuration Information**

The configuration snippet provides the details required to set up and connect to a database, including environment-specific handling, credentials, schema information, and other related settings. Below is a structured breakdown:

***

**Database Connection Information**

| Parameter Name   | Value / Source                                               | Description                                                                                        |
| ---------------- | ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- |
| **DB\_URL**      | `health-db-url` or `db-url` from `egov-config`               | URL for connecting to the database. Uses `health-db-url` in the "health" namespace, else `db-url`. |
| **DB\_HOST**     | `db-host` from `egov-config`                                 | Hostname or IP address of the database server.                                                     |
| **DB\_PORT**     | `"5432"`                                                     | Port number for database connection (default PostgreSQL port).                                     |
| **DB\_NAME**     | `db-name` from `egov-config`                                 | Name of the database being connected to.                                                           |
| **DB\_SCHEMA**   | Namespace value (`"health")` for Microplanning or `"public"` | Specifies the schema within the database. Defaults to `"public"` if no namespace is provided.      |
| **DB\_USER**     | `username` from `db` secret                                  | Database username used for authentication.                                                         |
| **DB\_PASSWORD** | `password` from `db` secret                                  | Database password for authentication.                                                              |

***

**Flyway Migration Information**

| Parameter Name        | Value / Source                                  | Description                                     |
| --------------------- | ----------------------------------------------- | ----------------------------------------------- |
| **FLYWAY\_USER**      | `flyway-username` from `db` secret              | User for running Flyway migrations.             |
| **FLYWAY\_PASSWORD**  | `flyway-password` from `db` secret              | Password for Flyway migration user.             |
| **FLYWAY\_LOCATIONS** | `flyway-locations` from `egov-config`           | Directory or path for Flyway migration scripts. |
| **SCHEMA\_TABLE**     | `schemaTable` from `initContainers.dbMigration` | Table name for tracking Flyway migrations.      |

{% hint style="info" %}
**General Notes**

* **ConfigMap and Secrets Integration**: Sensitive data like `DB_USER`, `DB_PASSWORD`, and Flyway credentials are securely retrieved from Kubernetes secrets (`db` secret). Non-sensitive configurations like `DB_HOST` and `DB_NAME` are stored in ConfigMaps (`egov-config`).
* **Namespace-Specific Configuration**: The `DB_URL` and `DB_SCHEMA` are tailored for specific namespaces. For example, the "health" namespace uses a dedicated `health-db-url` key and the namespace value for the schema.
* **Default Settings**: Where applicable, defaults are provided. For instance, the schema defaults to `"public"` and the port defaults to `5432`.

These configurations enhance the flexibility and usability of the core services of HCM-Microplanning, ensuring smoother operations and better alignment with user needs.
{% endhint %}
