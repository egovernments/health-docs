# Microplan Service Configuration

## Overview

Microplanning configuration controls how microplans are created, validated, and estimated. Most settings live in **MDMS** under the `hcm-microplanning` module. Some settings depend on the **boundary** hierarchy/data and **deployment values** for the services.

Use this page as the index of what to configure and where it is used.

{% hint style="info" %}
This page focuses on **Microplanning**. For broader HCM platform configuration (registries, attendance, payments, etc), see [HCM Service Configuration](../hcm-service-configuration/).
{% endhint %}

## Audience

* **Implementers / system admins**: manage MDMS, boundaries, and environment rollouts.
* **Developers**: add/extend masters, defaults, and validation rules.
* **Product admins**: tune assumptions, uploads, and roles for a campaign type.

## Configuration Details

### 1) Boundary hierarchy and boundary data

Microplanning relies on the platform Boundary service for all geo hierarchy lookups. Make sure the hierarchy exists and boundary data is loaded before running estimation.

* UI + flow details: [Manage Boundary Data](../hcm-console-configuration/console-ui-configuration/hcm-console-web-ui/manage-boundary-data.md)

### 2) Microplanning services

Microplanning is implemented as 3 services. Their docs explain APIs, Kafka topics, and service-level behaviour.

* [Services](services/)

### 3) Deployment (Helm + DB)

Helm values, DB schema/migrations, and core environment variables live with deployment config.

* [Microplan Deployment](microplan-deployment.md)

### 4) Web UI configuration&#x20;

If you’re configuring the Microplan Web UI navigation and screens, use:

* [Microplan Web Service Configuration](microplan-web-service-configuration/)

### Microplanning MDMS masters (`hcm-microplanning`)

These masters drive validations, dropdowns, estimation logic, and upload handling across:

* [Plan Service](services/plan-service.md)
* [Resource Generator Service](services/resource-generator-service.md)
* [Census Service](services/census-service.md)

## Naming & Identifiers

#### MicroplanNamingConvention

Controls naming conventions for microplans.

#### MicroplanNamingRegex

Validates microplan names using a regex pattern.

### Planning strategy and workflow

#### ResourceDistributionStrategy

Defines supported resource allocation strategies.

#### RegistrationAndDistributionHappeningTogetherOrSeparately

Represents whether registration and distribution are combined or split.

#### rolesForMicroplan

Defines roles and their execution order in microplanning flows.

#### ContextPathForUser

Maps user contexts used by the Microplan UI and routing.

### Security

#### securityQuestions

Security questions are used for user verification flows. Populate this only if your deployment enables it.

### Estimation and rules engine

#### HypothesisAssumptions

Campaign-type assumptions are used by estimation.

#### RuleConfigureInputs

Inputs available to the rule configuration.

#### RuleConfigureOperators

Operators supported by the rules engine.

#### RuleConfigureOutput

Outputs produced/expected from rule configuration.

#### AutoFilledRuleConfigurations

Default rule configurations are auto-populated from the above masters.

#### MixedStrategyOperationLogic

Logic is used when mixed strategy execution is enabled.

### Geography, logistics, and facility metadata

#### hierarchyConfig

Defines hierarchy model assumptions used during planning.

#### villageRoadCondition

Road condition master for village-level logistics planning.

#### villageTerrain

Terrain master for village-level logistics planning.

#### facilityType

Facility types used in facility mapping and UI filters.

#### facilityStatus

Facility status values used in validations and UI.

#### VehicleType

Vehicle categories used in logistics modelling.

#### VehicleDetails

Vehicle catalogue entries (type, capacity, UOM, etc).

### Uploads and schemas

#### UploadConfiguration

Supported upload types, extensions, and naming conventions.

#### Schemas

Templates and mappings for hierarchical and facility-based data.

### Metrics and common config

#### Uom

Units of measure used across estimation and logistics.

#### Metric

Metric definitions used by the UI and exports.

#### CommonConstants

Shared constants referenced by other masters and UI behaviour.

### Dashboards (microplanning)

#### DssKpiConfigs

KPI configuration used by DSS dashboards for microplanning contexts.

{% hint style="warning" %}
If your dashboard setup requires GeoJSON assets and S3 mappings, see [MDMS Configurations & S3 Assets](../hcm-dashboard-configurations/mdms-configurations-and-s3-assets.md).
{% endhint %}

### Console/platform UI masters that Microplanning depends on

Some Microplanning screens reuse Console/platform configuration for hierarchy and sheet rendering. These are not part of `hcm-microplanning`, but they often need to be present.

#### HierarchySchema (`HCM-ADMIN-CONSOLE`)

Defines hierarchies used by Boundary Management and related admin flows.

#### customSheetData (`HCM-ADMIN-CONSOLE`)

Defines custom sheet structures for admin consoles.

## Change checklist (practical)

1. Update the MDMS masters in the target environment.
2. Validate boundary hierarchy + boundary data is available.
3. Restart services only if your MDMS cache strategy requires it.
4. Re-run estimation/microplan generation if assumptions or schemas changed.

### Helm Configurations

See [Microplan Deployment](microplan-deployment.md) for Helm charts and DB/migration notes.
