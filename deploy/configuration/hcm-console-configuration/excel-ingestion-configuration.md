---
description: Advanced Configurations
---

# Excel Ingestion Configuration

## Overview

The **Excel Ingestion service** is a core component of the **HCM (Health Campaign Management)** platform. Its primary responsibility is to:

* Generate Excel templates with validations and localisation
* Ingest uploaded Excel files
* Validate, transform, and process bulk data
* Interact asynchronously with downstream services

The service supports ingestion for **campaigns, boundaries, facilities, individuals, users**, and related domain data.

### Dependencies

The Excel Ingestion service depends on the following external services and infrastructure components:

* **PostgreSQL** – persistent storage and migration tracking
* **Kafka** – event-based asynchronous processing
* **MDMS** – master data lookup
* **File Store** – upload and download of Excel files
* **Boundary, Facility, Individual, Campaign services** – domain validations
* **LocalisationLocalization service** – multilingual support

Configuration is managed using **Helm charts** and deployed on **Kubernetes** via a `values.yaml` file.

## Steps

### Helm Configuration

The Excel Ingestion service depends on Kafka and Postgres. You need to set environment variables in the `values.yaml` file or Helm templates.

{% embed url="https://github.com/egovernments/DIGIT-DevOps/blob/unified-env-lts/deploy-as-code/helm/charts/health-services/excel-ingestion/values.yaml" %}
Excel Ingestion Helm
{% endembed %}

### Common Labels

```yaml
labels:
  app: "excel-ingestion"
  group: "health"
```

* Used for Kubernetes resource identification and grouping.

### Namespace Configuration

```yaml
namespace: health
```

* Deploys the service in the `health` namespace.
* Database schema and DB URL selection depend on this value.

### Ingress Configuration

```yaml
ingress:
  namespace: egov
  enabled: true
  zuul: true
  context: "excel-ingestion"
```

* Exposes the service through Zuul API Gateway
* Base context path: `/excel-ingestion`

### Init Containers – Database Migration

```yaml
initContainers:
  dbMigration:
    enabled: true
    schemaTable: "excel_ingestion_flyway_history"
    image:
      repository: "excel-ingestion-db"
```

* Executes Flyway database migrations before the application starts
* Tracks migration history in `excel_ingestion_flyway_history`

### Application Container Configuration

```yaml
image:
  repository: "excel-ingestion"
replicas: "1"
```

* Runs a single replica by default
* Can be scaled based on ingestion load

### Health Checks

```yaml
healthChecks:
  enabled: true
  livenessProbePath: "/excel-ingestion/health"
  readinessProbePath: "/excel-ingestion/health"
```

* Ensures Kubernetes can detect unhealthy pods
* Uses Spring Boot actuator-style health endpoint

### Application Runtime Configuration

```yaml
appType: "java-spring"
tracing-enabled: true
memory_limits: "3072Mi"
cpu_limits: "500m"
heap: "-Xmx2900m -Xms256m"
java-args: ""
```

* Java Spring Boot application
* Tracing enabled for distributed request tracking
* Heap size tuned to avoid OOM during large Excel processing

### Debug Configuration

```yaml
java-enable-debug: false
java-debug-port: 5005
```

* Enables remote debugging when required
* Disabled by default in production

### Server Configuration

```yaml
- name: SERVER_PORT
  value: "8080"
- name: SERVER_SERVLET_CONTEXT_PATH
  value: "/excel-ingestion"
```

* Application runs on port `8080`
* Base context path: `/excel-ingestion`

### Localisation Configuration

```yaml
- name: DEFAULT_LOCALE
  value: "en_IN"
```

* Default locale used for:
  * Template generation
  * Validation messages
  * Error responses

### External Service Host Configuration

All service hosts are resolved from the **`egov-service-host`  ConfigMap**.

<table><thead><tr><th width="330.5703125">Environment Variable</th><th>ConfigMap Key</th></tr></thead><tbody><tr><td>EGOV_BOUNDARY_HOST</td><td>boundary-service</td></tr><tr><td>EGOV_FILESTORE_HOST</td><td>egov-filestore</td></tr><tr><td>EGOV_CAMPAIGN_HOST</td><td>project-factory</td></tr><tr><td>EGOV_HEALTH_INDIVIDUAL_HOST</td><td>health-individual</td></tr><tr><td>EGOV_FACILITY_HOST</td><td>facility</td></tr><tr><td>EGOV_LOCALIZATION_HOST</td><td>egov-localization</td></tr><tr><td>EGOV_MDMS_HOST</td><td>egov-mdms-service</td></tr></tbody></table>

### Service Endpoints

<table><thead><tr><th width="276.91796875">Purpose</th><th>Endpoint</th></tr></thead><tbody><tr><td>Campaign Search</td><td><code>project-factory/v1/data/campaign/_search</code></td></tr><tr><td>Campaign Bulk Decrypt</td><td><code>project-factory/v1/crypto/_bulkDecrypt</code></td></tr><tr><td>Individual Search</td><td><code>health-individual/v1/_search</code></td></tr><tr><td>Hierarchy Search</td><td><code>boundary-service/boundary-hierarchy-definition/_search</code></td></tr><tr><td>Boundary Relationship Search</td><td><code>boundary-service/boundary-relationships/_search</code></td></tr><tr><td>Facility Search</td><td><code>facility/v1/_search</code></td></tr><tr><td>File Upload</td><td><code>filestore/v1/files</code></td></tr><tr><td>File URL Fetch</td><td><code>filestore/v1/files/url</code></td></tr><tr><td>Localization Search</td><td><code>localization/messages/v1/_search</code></td></tr><tr><td>MDMS Search</td><td><code>egov-mdms-service/v2/_search</code></td></tr></tbody></table>

### Database Configuration

Database connection values are dynamically selected based on the namespace.

#### Database Connection Details

<table><thead><tr><th width="244.86328125">Parameter</th><th width="237.4609375">Source</th><th>Description</th></tr></thead><tbody><tr><td>SPRING_DATASOURCE_URL</td><td><code>health-db-url</code> or <code>db-url</code></td><td>Namespace-based DB URL</td></tr><tr><td>DB_HOST</td><td>egov-config</td><td>Database host</td></tr><tr><td>DB_PORT</td><td><code>5432</code></td><td>PostgreSQL default port</td></tr><tr><td>DB_NAME</td><td>egov-config</td><td>Database name</td></tr><tr><td>DB_SCHEMA</td><td>Namespace or <code>public</code></td><td>Schema selection</td></tr><tr><td>DB_USER</td><td>db secret</td><td>Database username</td></tr><tr><td>DB_PASSWORD</td><td>db secret</td><td>Database password</td></tr></tbody></table>

### JPA / Hibernate Configuration

```yaml
- name: SPRING_JPA_HIBERNATE_DDL_AUTO
  value: "update"
- name: SPRING_JPA_PROPERTIES_HIBERNATE_DIALECT
  value: "org.hibernate.dialect.PostgreSQLDialect"
```

* Automatically updates schema
* Uses PostgreSQL dialect

### Flyway Migration Configuration

| Parameter         | Source                            |
| ----------------- | --------------------------------- |
| FLYWAY\_USER      | db secret                         |
| FLYWAY\_PASSWORD  | db secret                         |
| FLYWAY\_LOCATIONS | egov-config                       |
| SCHEMA\_TABLE     | excel\_ingestion\_flyway\_history |

### Kafka Producer Configuration

```yaml
- name: SPRING_KAFKA_PRODUCER_KEY_SERIALIZER
  value: org.apache.kafka.common.serialization.StringSerializer
- name: SPRING_KAFKA_PRODUCER_VALUE_SERIALIZER
  value: org.springframework.kafka.support.serializer.JsonSerializer
```

* Enables event publishing for async processing

### Redis Health Check Configuration

```yaml
- name: MANAGEMENT_HEALTH_REDIS_ENABLED
  value: "false"
```

* Redis health check is disabled as Redis is not mandatory for Excel Ingestion

{% hint style="info" %}
**Notes**

* **Secrets vs ConfigMaps**
  * Sensitive data (DB credentials, Flyway credentials) is stored in Kubernetes **Secrets**
  * Non-sensitive values are stored in **ConfigMaps**
* **Namespace-Aware Behaviour**
  * Database URL and schema automatically change based on the namespace
  * Ensures isolation between environments
* **Performance Considerations**
  * Heap and memory limits are tuned for large Excel uploads
  * Increase replicas if the concurrent ingestion volume increases
{% endhint %}
