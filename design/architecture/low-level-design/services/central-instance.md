---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/low-level-design/services/central-instance
---

# Central Instance

## Overview

This release introduces the Central Instance Deployment Model for the Health Campaign Management (HCM) consolidating multi-tenant operations (can be multiple countries in one server or multiple states in one country) into a single Kubernetes cluster with namespace-level and database schema-level isolation.

The goal is to reduce operational overhead, standardize configurations, and avoid service duplication while still supporting tenant-specific variations where necessary.&#x20;

Key areas of change include multi-schema database support, standardized Kafka topic conventions, updated Flyway migration scripts, and Helm/environment configuration adjustments to enable smooth centralized deployments across tenants.

**Main updates:**

* Multi-schema database support
* Standardised Kafka topic naming
* Updated Flyway migration scripts
* Helm and environment configuration improvements for smooth multi-tenant deployments

## Key Features&#x20;

#### 1. Centralized Multi-Tenant Deployment

* The new HCM server can now run campaigns for multiple countries in a single Kubernetes cluster, instead of spinning up a new server for every country or disease.
* Introduced a common namespace hosting all shared and core services:
* These are the services that are tenant agnostic in execution when and can be used by all different tenants configured in the server
* Create dedicated tenant namespaces (e.g., tenantA, tenantB) for services requiring country-specific customizations&#x20;
* Encryption and id gen are currently tenant specific services

#### 2. Multi-Schema Database Support

* A single PostgreSQL instance now hosts separate schemas (e.g. public, country1, country2) to isolate tenant data.
* Updated Flyway migration process:
* The new migrate.sh script loops through all configured schemas automatically.
* Ensures all migrations execute across tenants without manual intervention.
* Database schema lists and enablement flags are now configurable per service via Helm and environment YAML files.

#### 3. Standardized Kafka Topic Naming

* All Kafka topics now use tenant-prefixed names to avoid cross-tenant collisions.

Example:

* country1: c1-save-household-topic
* country2: c2-save-household-topic
* country3: c3-save-household-topic

#### 4. Helm and Configuration Updates

* Common values.yml now provides baseline DB and service configurations.
* App-specific values.yml files override:
* Schema lists (db-schemas).
* Multi-schema enablement flags.
* Most default configurations remain untouched, ensuring backward compatibility for services not requiring multi-schema support.

#### 6. Centralized Internal Gateway and MDMS v2

* Internal Gateway configurations are now maintained centrally in a shared Git repository for easier updates.
* MDMS v2 configurations for each tenant are consolidated, ensuring consistent metadata management.

## Breaking Changes



### Kafka Topic Renaming

* All topics now follow a tenant-prefixed convention when the central instance is enabled.
* Example: save-household-topic is now c1-save-household-topic(country1) or c2-save-household-topic(country2) if the central instance is enabled.
* Persister, Indexer config files must be updated to have the correct topic name and use schema name.<br>

### Flyway Migration Updates

* Services running in the common namespace must now define their target schemas explicitly using:
* SCHEMA\_NAME (comma-separated schema list).
* DB\_URL (database url without schema name)
* IS\_ENVIRONMENT\_CENTRAL\_INSTANCE (boolean flag).
* Helm and environment YAMLs must be updated for all multi-schema services.
* The new migrate.sh script replaces manual schema-specific migrations.
* Existing CI/CD pipelines must be updated to use the new script for deployments.<br>

### Helm Chart Changes

* values.yml for services must include overrides for:
* Schema lists.
* Enablement flags for multi-schema support.
* Charts without overrides will default to single-schema mode (public schema).<br>

### Namespace Restructuring

* Some services must be redeployed into tenant-specific namespaces.
* Any scripts or automation referencing old namespaces must be adjusted(public schema reference in database migrations are not allowed).

### Encryption Service

Encryption Service is modified to not use default public schema for schema migration but use the db url defined in the environment properties.
