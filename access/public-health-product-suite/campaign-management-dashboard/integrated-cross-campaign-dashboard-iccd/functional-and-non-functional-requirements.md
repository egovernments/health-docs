# Functional & Non-Functional Requirements

## Functional Requirements

### 1. Project Assignment–Based Rendering of Dashboard

Enable users to access dashboards based on their assigned jurisdiction or project assignment, eliminating the need to maintain multiple dashboard roles.

#### Key Capabilities

Upon login, the system should -

* Determine the user’s jurisdiction via the project service.
* Restrict access to data and dashboard views to that jurisdiction.
* Inbox, where users can see live and past campaigns and check their respective dashboards
* Jurisdiction and role-based access to dashboards

#### Benefits

* Eliminates the need to manage multiple roles or dashboards for each hierarchy level or user group.
* Users immediately see the information that matters most to them, improving usability and decision-making.

### 2. Configuration-Based Filter Rendering in Dashboard

Support dynamic filter rendering on dashboards using a configuration-driven approach. This avoids hardcoded filters and allows dashboard views to be easily adapted across campaigns and **K**ey **P**erformance **I**ndicators (KPIs).

#### **Key Capabilities**

Define and allow rendering of dynamic filters from a centralised JSON configuration file.

## Non-functional Requirements

#### Performance

* Dashboard API response times must remain below 200 milliseconds.
* All dashboard aggregation queries to be optimised with:
  * Pre-aggregated views using Elasticsearch Transforms.
  * Proper indexing and mapping strategies.

#### Scalability

* The analytics and dashboard system should handle millions of records across indexes like household-index-v1, household-member-index-v1, project-task-index-v1, etc.

#### Security

* Sensitive personal information (e.g., exact address, phone number, health conditions, or any combination of fields that can uniquely identify an individual) must be excluded during ingestion into analytical indexes.
* All API access must be authenticated and transmitted over HTTPS.

{% hint style="info" %}
**\*\*\* Callouts -**

* Fields like the name of the field level worker, when present alone, are not considered PII and may be retained for contextual or analytical relevance.
* Jurisdiction-based access control will be enforced only at the UI layer. Since no PII or sensitive data is present in the indexed data, this is considered sufficient for now. If required in the future, jurisdiction-based data access should be implemented at the API gateway as a generic capability, rather than introducing custom filters specifically for dashboard APIs.
{% endhint %}

#### Availability

* The system must be highly available to ensure uninterrupted access to dashboards during campaign operations.
* Key practices to meet this requirement include:
  * Managed ElasticSearch cluster with multi-node configuration and shard replication.
  * Load-balanced dashboard pods with auto-scaling support and caching.
  * Monitoring and alerting for failures.

#### Maintainability

* Standardise KPIs across campaigns for population-based campaigns to bring down the required engineering effort.
* Allow dashboard extensibility for campaign-specific customisations.
* Unify the approach for setting up boundary hierarchies and associated map layers (GeoJSON) within Kibana, ensuring consistency and reusability across implementations.
* Maintain a centralised KPI catalogue organised by campaign type to simplify the selection, setup, and validation of metrics during dashboard rollout.
