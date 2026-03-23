---
description: Advanced Configurations
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-console-configuration/project-factory-configuration
---

# Project Factory Configuration

## Overview

* The **Project Factory service** is a part of the HCM (Health Campaign Management) console. Its job is to manage projects (campaigns), facilities, users, boundary data, etc.
* It depends on other services: **Kafka**, **Postgres**, **Redis**. These are used for messaging, storage, and caching.&#x20;
* Configuration is done using **Helm charts** (used to deploy apps on Kubernetes) via a `values.yaml` file.

## Steps

The Project Factory service depends on **Kafka, Postgres, and Redis**. To configure it via Helm, you need to set environment variables in the `values.yaml` file or Helm templates.

{% embed url="https://github.com/egovernments/DIGIT-DevOps/blob/unified-env-lts/deploy-as-code/helm/charts/health-services/project-factory/values.yaml" %}
Project factory helm
{% endembed %}

### **Step 1. Enable auto-generation of passwords**

```yaml
- name: USER_PASSWORD_AUTO_GENERATE
  value: "true"
```

* ➝ System will generate random passwords for new users.
* Set default password (if auto-generation disabled)

```yaml
- name: USER_DEFAULT_PASSWORD
  value: "eGov@123"
```

➝ Provides a fallback default password.

### **Step 2: User duplication check**

* Avoid creating duplicate users based on mobile number.

```yaml
- name: NOT_CREATE_USER_IF_ALREADY_THERE
  value: "true"
```

➝ Prevents multiple accounts with the same mobile number.

### **Step 3: Tab Naming - Readme and Sheets**

* Define tab names for different data sheets.

```yaml
- name: READ_ME_TAB
  value: "HCM_README_SHEETNAME"
```

Defines the sheet name to be used for the ReadMe tab. Tab names for different data sheets:

```yaml
- name: FACILITY_TAB_NAME
  value: "HCM_ADMIN_CONSOLE_FACILITIES"
- name: BOUNDARY_TAB_NAME
  value: "HCM_ADMIN_CONSOLE_BOUNDARY_DATA"
- name: USER_TAB_NAME
  value: "HCM_ADMIN_CONSOLE_USER_LIST"
```

* Sets tab names for facilities, boundary data, and user lists in the HCM Console.

### **Step 4: Localisation and default locale**

* Set default locale:

```yaml
- name: LOCALE
  value: {{ .Values.defaultLocale | default "en_IN" }}
```

Defines the default locale as "en\_IN" unless overridden in the Helm values.

* Localisation module:

```yaml
- name: LOCALIZATION_MODULE
  value: "rainmaker-hcm-admin-schemas"
```

Specifies the localisation module used for HCM schemas.

### **Step 5: Logging configuration**

* Set the application log level:

```yaml
- name: APP_LOG_LEVEL
  value: {{ .Values.logLevel | default "info" }}
```

Determines the verbosity of logs, defaulting to 'info'.

* Set maximum debug characters:

```yaml
- name: APP_MAX_DEBUG_CHAR
  value: "{{ .Values.maxDebugChar | default "500" }}"
```

Limits the maximum length of debug logs to 500 characters unless overridden.

### **Step 6: User mapping**

* Enables mapping of users via a common parent:

```yaml
- name: MAP_USER_VIA_COMMON_PARENT
  value: "true"
```

Allows users to be linked based on a shared parent hierarchy.

### **Step 7: Automatic retry mechanism**

* Retry when specific HTTP errors occur:

```yaml
- name: AUTO_RETRY_IF_HTTP_ERROR
  value: "socket hang up"
```

Automatically retries operations if the "socket hang up" error occurs.

### **Step 8: Localisation wait time in boundary creation**

```yaml
- name: LOCALIZATION_WAIT_TIME_IN_BOUNDARY_CREATION
  value: "30000"
```

Localisation wait time in boundary creation

### **Step 9: Localisation chunk size**

```yaml
- name: LOCALIZATION_CHUNK_SIZE_FOR_BOUNDARY_CREATION
  value: "2000"
```

Localisation chunk size

### **Step 10: Enable/Disable Campaign ID Validation in Template Upload (v0.3.1)**

<pre class="language-yaml"><code class="lang-yaml"><strong>- name: VALIDATE_CAMPAIGN_ID_IN_METADATA
</strong>  value: {{ .Values.validateCampaignIdInMetadata | default "false" | quote }}
</code></pre>

The `validateCampaignIdInMetadata`  flag decides whether the application validates `campaignId` in metadata during template uploads.

### **Step 11:** Update Default tenantId

Some of the Master data been fetched using this default tenant configuration&#x20;

```
- name: DEFAULT_TENANT_ID
  value: 'mz' // whatever is been used in that environment
```

## **Service Host Details**

<table><thead><tr><th width="305.17578125">Host Name</th><th>ConfigMap Name</th><th>Key</th></tr></thead><tbody><tr><td>KAFKA_BROKER_HOST</td><td>egov-config</td><td>kafka-brokers</td></tr><tr><td>EGOV_MDMS_HOST</td><td>egov-service-host</td><td>egov-mdms-service</td></tr><tr><td>EGOV_MDMS_V2_HOST</td><td>egov-service-host</td><td>mdms-service-v2</td></tr><tr><td>EGOV_FILESTORE_SERVICE_HOST</td><td>egov-service-host</td><td>egov-filestore</td></tr><tr><td>EGOV_IDGEN_HOST</td><td>egov-service-host</td><td>egov-idgen</td></tr><tr><td>EGOV_FACILITY_HOST</td><td>egov-service-host</td><td>facility</td></tr><tr><td>EGOV_BOUNDARY_HOST</td><td>egov-service-host</td><td>boundary-service</td></tr><tr><td>EGOV_PROJECT_HOST</td><td>egov-service-host</td><td>health-project</td></tr><tr><td>EGOV_USER_HOST</td><td>egov-service-host</td><td>egov-user</td></tr><tr><td>EGOV_PRODUCT_HOST</td><td>egov-service-host</td><td>product</td></tr><tr><td>EGOV_HRMS_HOST</td><td>egov-service-host</td><td>health-hrms</td></tr><tr><td>EGOV_LOCALIZATION_HOST</td><td>egov-service-host</td><td>egov-localization</td></tr><tr><td>EGOV_HEALTH_INDIVIDUAL_HOST</td><td>egov-service-host</td><td>health-individual</td></tr><tr><td>EGOV_AUDIT_HOST</td><td>egov-service-host</td><td>audit-service</td></tr><tr><td>EGOV_PLAN_SERVICE_HOST</td><td>egov-service-host</td><td>plan-service</td></tr><tr><td>EGOV_CENSUS_HOST</td><td>egov-service-host</td><td>census-service</td></tr><tr><td>EXCEL_INGESTION_HOST</td><td>egov-service-host</td><td>excel-ingestion</td></tr></tbody></table>

**Service endpoints**

<table><thead><tr><th width="394.51953125">Path Name</th><th>Value</th></tr></thead><tbody><tr><td>FILE_STORE_SERVICE_END_POINT</td><td>filestore/v1/files</td></tr><tr><td>EGOV_MDMS_V2_SEARCH_ENDPOINT</td><td>mdms-v2/v2/_search</td></tr><tr><td>EGOV_MDMS_V1_SEARCH_ENDPOINT</td><td>mdms-v2/v1/_search</td></tr><tr><td>EGOV_IDGEN_PATH</td><td>egov-idgen/id/_generate</td></tr><tr><td>EGOV_MDMS_SCHEMA_PATH</td><td>mdms-v2/schema/v1/_search</td></tr><tr><td>EGOV_BOUNDARY_RELATIONSHIP_SEARCHPATH</td><td>boundary-service/boundary-relationships/_search</td></tr><tr><td>EGOV_BOUNDARY_SERVICE_SEARCHPATH</td><td>boundary-service/boundary/_search</td></tr><tr><td>EGOV_BOUNDARY_HIERARCHY_SEARCHPATH</td><td>boundary-service/boundary-hierarchy-definition/_search</td></tr><tr><td>HEALTH_PROJECT_CREATE_PATH</td><td>health-project/v1/_create</td></tr><tr><td>EGOV_PROJECT_STAFF_CREATE_PATH</td><td>health-project/staff/v1/_create</td></tr><tr><td>EGOV_PROJECT_RESOURCE_CREATE_PATH</td><td>health-project/resource/v1/_create</td></tr><tr><td>EGOV_PROJECT_RESOURCE_FACILITY_PATH</td><td>health-project/facility/v1/_create</td></tr><tr><td>EGOV_USER_SEARCH_PATH</td><td>user/_search</td></tr><tr><td>EGOV_FACILITY_SEARCH_PATH</td><td>facility/v1/_search</td></tr><tr><td>EGOV_PRODUCT_VARIANT_SEARCH_PATH</td><td>product/variant/v1/_search</td></tr><tr><td>EGOV_BOUNDARY_ENTITY_SEARCHPATH</td><td>boundary-service/boundary/_search</td></tr><tr><td>EGOV_FACILITY_BULK_CREATE</td><td>facility/v1/bulk/_create</td></tr><tr><td>EGOV_HEALTH_INDIVIDUAL_SEARCH</td><td>health-individual/v1/_search</td></tr><tr><td>EGOV_PLAN_FACILITY_SEARCH</td><td>plan-service/plan/facility/_search</td></tr><tr><td>EGOV_PLAN_FACILITY_CONFIG_SEARCH</td><td>plan-service/config/_search</td></tr><tr><td>EGOV_CENSUS_SEARCH</td><td>census-service/_search</td></tr><tr><td>EGOV_PLAN_SEARCH</td><td>plan-service/plan/_search</td></tr><tr><td>EXCEL_INGESTION_SHEET_SEARCH</td><td>excel-ingestion/v1/data/sheet/_search</td></tr><tr><td>EXCEL_INGESTION_PROCESS</td><td>excel-ingestion/v1/data/process/_create</td></tr><tr><td>EXCEL_INGESTION_GENERATE</td><td>excel-ingestion/v1/data/generate/_init</td></tr><tr><td>EXCEL_INGESTION_GENERATE_SEARCH</td><td>excel-ingestion/v1/data/generate/_search</td></tr></tbody></table>

**Kafka topics**

| Topic Name                              | Value                   |
| --------------------------------------- | ----------------------- |
| KAFKA\_SAVE\_CAMPAIGN\_DETAILS\_TOPIC   | save-campaign-details   |
| KAFKA\_UPDATE\_CAMPAIGN\_DETAILS\_TOPIC | update-campaign-details |

**Database configuration information**

The configuration snippet provides the details required to set up and connect to a database, including environment-specific handling, credentials, schema information, and other related settings. Below is a structured breakdown:

Database Connection Information -

<table><thead><tr><th width="172.0234375">Parameter Name</th><th width="187.15234375">Value / Source</th><th>Description</th></tr></thead><tbody><tr><td><strong>DB_URL</strong></td><td><code>health-db-url</code> or <code>db-url</code> from <code>egov-config</code></td><td>URL for connecting to the database. Uses <code>health-db-url</code> in the "health" namespace, else <code>db-url</code>.</td></tr><tr><td><strong>DB_HOST</strong></td><td><code>db-host</code> from <code>egov-config</code></td><td>Hostname or IP address of the database server.</td></tr><tr><td><strong>DB_PORT</strong></td><td><code>"5432"</code></td><td>Port number for database connection (default PostgreSQL port).</td></tr><tr><td><strong>DB_NAME</strong></td><td><code>db-name</code> from <code>egov-config</code></td><td>Name of the database being connected to.</td></tr><tr><td><strong>DB_SCHEMA</strong></td><td>Namespace value or <code>"public"</code></td><td>Specifies the schema within the database. Defaults to <code>"public"</code> if no namespace is provided.</td></tr><tr><td><strong>DB_USER</strong></td><td><code>username</code> from <code>db</code> secret</td><td>Database username used for authentication.</td></tr><tr><td><strong>DB_PASSWORD</strong></td><td><code>password</code> from <code>db</code> secret</td><td>Database password for authentication.</td></tr></tbody></table>

**Flyway Migration Information**

<table><thead><tr><th width="199.09765625">Parameter Name</th><th width="225.859375">Value / Source</th><th>Description</th></tr></thead><tbody><tr><td><strong>FLYWAY_USER</strong></td><td><code>flyway-username</code> from <code>db</code> secret</td><td>User for running flyway migrations.</td></tr><tr><td><strong>FLYWAY_PASSWORD</strong></td><td><code>flyway-password</code> from <code>db</code> secret</td><td>Password for flyway migration user.</td></tr><tr><td><strong>FLYWAY_LOCATIONS</strong></td><td><code>flyway-locations</code> from <code>egov-config</code></td><td>Directory or path for flyway migration scripts.</td></tr><tr><td><strong>SCHEMA_TABLE</strong></td><td><code>schemaTable</code> from <code>initContainers.dbMigration</code></td><td>Table name for tracking Flyway migrations.</td></tr></tbody></table>

### HRMS DevOps Config Changes

<table><thead><tr><th width="315.81640625">Config / Env Var</th><th>Value</th></tr></thead><tbody><tr><td>microplanWebsiteLink</td><td>https://unified-uat.digit.org/workbench-ui/employee/user/login (Update URL according to your environment)</td></tr><tr><td>microplanImplementationPartner</td><td>Console Team</td></tr></tbody></table>

### BASE\_SECRET Config Change

<table><thead><tr><th width="232.1875">Config / Env Var</th><th>Value / Details</th></tr></thead><tbody><tr><td>BASE_SECRET</td><td>Reference secret → project-factory:basesecret Secret value to create: egov-admin-console-enc</td></tr></tbody></table>

### Localisation Service Config Changes

<table><thead><tr><th width="341.7421875">Config</th><th>Value</th></tr></thead><tbody><tr><td>heap</td><td>"-Xmx2500m -Xms512m"</td></tr><tr><td>memory_limits</td><td>3072Mi (~3GB)</td></tr><tr><td>replicas</td><td>2</td></tr></tbody></table>

{% hint style="warning" %}
These changes have been made because sometimes the localisation service runs out of heap memory. By increasing the heap size, memory limits, and replicas, the service will run more stably and handle load without OOM (Out of Memory) issues.
{% endhint %}

Notes:

* **ConfigMap and Secrets Integration**: Sensitive data like `DB_USER`, `DB_PASSWORD`, and Flyway credentials are securely retrieved from Kubernetes secrets (`db` secret). Non-sensitive configurations like `DB_HOST` and `DB_NAME` are stored in ConfigMaps (`egov-config`).
* **Namespace-Specific Configuration**: The `DB_URL` and `DB_SCHEMA` are tailored for specific namespaces. For example, the 'health' namespace uses a dedicated `health-db-url` key and the namespace value for the schema.
* **Default Settings**: Where applicable, defaults are provided. For instance, the schema defaults to `"public"` and the port defaults to `5432`.

These configurations enhance the flexibility and usability of the Project Factory Service, ensuring smoother operations and better alignment with user needs.
