# User Interface Design

## Overview

This page explains how to configure the UI for setting up **Microplans** using MDMS-driven configurations in the **hcm-microplanning** module.

## Steps

### Step 1: Understand UI Actions and Action IDs

Each **Action ID** represents a unique navigation path or user action in the Microplanning UI (for example, create microplan, configure resources, or review distribution).

* Action IDs are mapped to UI flows and screens.
* These actions are defined and resolved through configuration, not hardcoded logic.

Ensure all required actions for microplanning are correctly mapped before proceeding with master configurations.

[City module file path](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/tenant/citymodule.json) - required to run the campaign module.

```
{
      "module": "Microplan",
      "code": "Microplan",
      "active": true,
      "order": 1,
      "tenants": [
        {
          "code": "mz"
        }
      ]
    }
```

{% embed url="https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/ACCESSCONTROL-ROLEACTIONS/roleactions.json" %}

### Step 2: Configure Microplanning Masters in MDMS

The **HCM-microplanning** module relies on multiple MDMS masters to drive UI behaviour, validation, and workflows. Each master is accessed from MDMS and controls a specific part of the microplanning experience.

#### Core Microplanning Masters

Configure the following masters under the **HCM-Microplanning** module:

1. **Microplan Naming Convention**\
   Defines the standard naming structure for microplans.
2. **Microplan Naming Regex**\
   Validates microplan names entered in the UI.
3. **Resource Distribution Strategy**\
   Controls how resources are allocated during microplanning.
4. **Roles for Microplan**\
   Defines roles, permissions, and access levels for microplanning workflows.
5. **Hypothesis Assumptions**\
   Provides predefined assumptions used during hypothesis creation.

***

#### Rule Configuration Masters

These masters drive rule-based logic and calculations shown in the UI:

6. **Rule Configure Inputs**\
   Defines input parameters required by the rule engine.
7. **Rule Configure Output**\
   Specifies expected outputs from rule execution.
8. **Auto-Filled Rule Configurations**\
   Enables system-driven auto-fill of rule values.
9. **Rule Configure Operators**\
   Lists operators available for rule evaluation.

***

#### Workflow and Hierarchy Masters

10. **Registration and Distribution Mode**\
    Defines whether registration and distribution occur together or separately.
11. **Hierarchy Config**\
    Defines hierarchical levels and their relationships.
12. **Hierarchy Schema**\
    Specifies the order and structure of boundary hierarchies.

***

#### Geography and Infrastructure Masters

13. **Village Road Condition**\
    Captures road accessibility data for villages.
14. **Village Terrain**\
    Describes terrain characteristics influencing distribution planning.
15. **Vehicle Details**\
    Lists available vehicles for resource transportation.

***

#### Facility and Security Masters

16. **Facility Type**\
    Defines facility categories used in microplanning.
17. **Facility Status**\
    Indicates operational status of facilities.
18. **Security Questions**\
    Configures security questions used in authentication flows.

***

#### Context and Analytics Masters

19. **Context Path for User**\
    Determines user-specific navigation and access paths.
20. **DSS KPI Configs**\
    Defines KPIs used by the Decision Support System (DSS).

***

#### Master Schema

All the above masters are managed using the:

* **Schema Code:** `BASE_MASTER_DATA`

This ensures consistency, validation, and reuse across the microplanning UI.

### Step 3: Verify MDMS Data Source

Ensure the required MDMS data is available and up to date:

* **MDMS Repository:**\
  [`egov-mdms-data → data/mz/health/hcm-microplanning`](https://github.com/egovernments/egov-mdms-data/tree/UNIFIED-DEV/data/mz/health/hcm-microplanning)

All configured masters must exist here to render correctly in the UI.

### Step 4: Configure Environment-Level Settings

Add global configuration entries for microplanning in the deployment environment file:

* **Environment Config Location:**\
  [`DIGIT-DevOps → deploy-as-code/helm/environments/unified-health-uat.yaml`](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/unified-uat.yaml)

These settings ensure that the microplanning module is enabled and correctly resolved at runtime.

### Step 5: Configure Localisation for Microplanning UI

Microplanning UI text is fully localisation-driven. Ensure translations are added to the correct modules:

<table><thead><tr><th width="403.34765625">Localisation Module</th><th>Usage</th></tr></thead><tbody><tr><td><code>rainmaker-common</code></td><td>Common screens (login, homepage, sidebar)</td></tr><tr><td><code>rainmaker-microplanning</code></td><td>Microplanning workflows and configurations</td></tr><tr><td><code>rainmaker-boundary-${BOUNDARY_HIERARCHY_TYPE}</code></td><td>Boundary-level labels</td></tr><tr><td><code>rainmaker-Microplanning</code></td><td>Microplanning screen content</td></tr><tr><td><code>rainmaker-workbench</code></td><td>Operational tools and utilities</td></tr><tr><td><code>rainmaker-mdms</code></td><td>MDMS-driven master labels</td></tr><tr><td><code>rainmaker-schema</code></td><td>Schema definitions</td></tr><tr><td><code>rainmaker-hcm-admin-schemas</code></td><td>HCM admin and schema configuration text</td></tr></tbody></table>

Ensure localisation keys are available before testing the UI.

### Step 6: Validate UI Behaviour

After configuration:

* Verify microplan creation screens
* Validate naming rules and regex enforcement
* Check rule-based auto-filled fields
* Confirm hierarchy-driven dropdowns and filters
* Ensure localisation renders correctly across all screens

Once all steps are completed:

* The Microplanning UI is fully configuration-driven
* No code changes are required for UI behaviour updates
* Changes in MDMS are reflected immediately in the UI

## Reference File Links & Sample Payload

{% embed url="https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/ACCESSCONTROL-ROLES/roles.json" %}

Sample payload for adding roles in MDMS

```
MICROPLAN_ADMIN
ROOT_FACILITY_CATCHMENT_MAPPER
FACILITY_CATCHMENT_MAPPER
ROOT_POPULATION_DATA_APPROVER
POPULATION_DATA_APPROVER
ROOT_PLAN_ESTIMATION_APPROVER
PLAN_ESTIMATION_APPROVER
```

Role-action mapping

{% embed url="https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ROLEACTIONS/roleactions.json" %}

Actions ID MDMS data

{% embed url="https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json" %}

HCM Microplanning master details&#x20;

```
hcm.microplanning.MicroplanNamingConvention, hcm.microplanning.MicroplanNamingRegex
hcm.microplanning.ResourceDistributionStrategy, hcm.microplanning.RolesForMicroplan
hcm.microplanning.HypothesisAssumptions, hcm.microplanning.RuleConfigureOutput
hcm.microplanning.RuleConfigureInputs, hcm.microplanning.AutoFilledRuleConfigurations
hcm.microplanning.RuleConfigureOperators, hcm.microplanning.RegistrationAndDistributionHappeningTogetherOrSeparately
hcm.microplanning.HierarchyConfig, hcm.microplanning.VillageRoadCondition
hcm.microplanning.VillageTerrain, hcm.microplanning.SecurityQuestions
hcm.microplanning.FacilityType, hcm.microplanning.FacilityStatus
hcm.microplanning.VehicleDetails, hcm.microplanning.ContextPathForUser
hcm.microplanning.DSSKPIConfigs, hcm.microplanning.HierarchySchema
```

Hierarchy schema sample payload

```

  {
    "type": "microplan",
    "group": [
      "MALARIA"
    ],
    "hierarchy": "MICROPLAN",
    "department": [],
    "lowestHierarchy": "VILLAGE",
    "highestHierarchy": "COUNTRY",
    "splitBoundariesOn": "DISTRICT"
  }
]
```

