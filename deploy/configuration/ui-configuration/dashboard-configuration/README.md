# Dashboard Configuration

## Overview

The Dashboard Configuration enables a flexible and modular way to define, render, and control access to analytical dashboards. The configuration is split across multiple JSON files that collectively define the chart logic, dashboard structure, role-based access, and tenant mappings.\
This design ensures that dashboards are highly configurable without requiring code changes, supporting rapid customisation across different user roles, projects, and tenants.

## Key Features & Components

* Chart Configuration (`ChartApiConfig.json`)\
  Purpose: Defines all available charts and their underlying query logic.
* Dynamic Data Queries
  * Charts are powered by aggregation queries executed by the dashboard-analytics service.
  * Queries reference indices, fields, and filters to fetch and aggregate relevant data.
* Chart Properties
  * Chart type: metric, bar, line, stacked, etc.
  * Value type: number, percentage, etc.
  * Drill-down or insight definitions (e.g., compare today vs. yesterday).
* Insight Rules
  * Supports upward/downward indicators (positive/negative trends).
  * Configurable text messages with placeholders for values and intervals.

2\. Dashboard Layouts (`MasterDashboardConfig.json`)\
Purpose: Defines how charts are arranged and displayed within dashboards.

* Dashboard Structure
  * Dashboards are defined by an ID and name (e.g., `national-health-dashboard`).
  * Each dashboard is split into rows containing visualisation blocks.
* Visualization Blocks
  * Group charts together under a named section (e.g., “Household Metrics”).
  * Each block can contain multiple charts from `ChartApiConfig.json`.
* Flexibility
  * Charts can be reused across multiple dashboards.
  * Supports different visualisation styles (linear, stacked, collapsible, etc.).

3\. Role-to-Dashboard Mappings (`RoleDashboardMappingsConf.json`)\
Purpose: Controls which roles have access to which dashboards.<br>

* Role-Based Access Control (RBAC)
  * Each role is mapped to one or more dashboards.
  * Example: `NationalSupervisor` role can access National, Provincial, and District dashboards.
* Scalability
  * New roles and dashboards can be introduced without modifying existing code.
  * Ensures access policies are configurable and auditable.

Click [here](https://github.com/egovernments/health-campaign-config/tree/dashboard-v1.0.0/egov-dss-dashboards/dashboard-analytics) for details.&#x20;
