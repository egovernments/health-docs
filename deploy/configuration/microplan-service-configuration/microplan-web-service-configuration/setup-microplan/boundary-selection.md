# Boundary Selection

## Overview

The **Boundary Selection** step is the **second step** in the microplan creation flow.\
It defines the **geographic scope** of the campaign by allowing users to select administrative boundaries across a configured hierarchy.

Boundary selection is **hierarchical and sequential**, ensuring accurate targeting and downstream planning.

## Steps

### Step 1: Configure the Boundary Selection Screen Header

#### Header Details

* **Title:** Select the boundaries where you want to run the campaign\
  Clearly instructs users to choose campaign locations.
* **Description:**\
  &#xNAN;_&#x42;oundaries are the administrative areas where you want to run a campaign. Start selecting boundaries from the first level so that the boundaries in the next level become available._\
  Explains why selections must follow the hierarchy.
* **Localisation:**\
  Title and description are fully translatable using localisation configurations.

<figure><img src="../../../../../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

### Step 2: Configure Boundary Hierarchy Levels

Boundary fields are rendered dynamically based on the **hierarchy definition configured in the system**.\
The number of levels and their labels are **not fixed**.

#### Example Hierarchy (Illustrative)

* Country
* Province
* District
* Administrative Post
* Locality
* Village

> ⚠️ This is only an example. Actual hierarchies depend on system configuration.

### Step 3: Configure Boundary Selection Fields

Each boundary level is rendered as a **dropdown field** and follows the same interaction pattern.

#### 3.1 Top-Level Boundary (e.g., Country)

* **Purpose:** Select the highest administrative boundary.
* **Field Type:** Dropdown
* **Mandatory:** Yes
* **Behaviour:**\
  Selecting this level enables the next level.

#### 3.2 Subsequent Boundary Levels (Province → Village)

For each subsequent level:

* **Purpose:** Narrow down the campaign area within the selected parent boundary.
* **Field Type:** Dropdown
* **Mandatory:** Yes
* **Availability:**\
  Enabled only after the parent boundary is selected.
* **Behaviour:**\
  Each selection filters the available options in the next level.

> **Note**: The hierarchy structure (e.g., Country > Province > District > Administrative Post > Locality > Village) is just an example. Actual levels and labels will vary based on the specific administrative hierarchy configured in the system.

### Step 4: Define Key Behaviour Rules

#### Sequential Selection

* Users **must select boundaries in order**
* Skipping a level is not allowed
* Each level unlocks the next

#### Dynamic Rendering

* Levels and labels are derived from the hierarchy configuration
* Supports any depth (not limited to six levels)

#### Localisation

* Boundary labels (e.g., Country, District)
* Dropdown options
* Validation messages
* All are fully translatable.

### Step 5: Configure User Interface Behaviour

#### Dropdown Behaviour

* **Hierarchical filtering:** Options depend on parent selection
* **Text search:** Users can type to filter values
* **Dropdown icon:** Indicates selectable options

#### Validation Behaviour

* Ensures:
  * No hierarchy level is skipped
  * All mandatory levels are selected
* Error messages are:
  * Contextual
  * Localised

### Step 6: Configure Validation Rules

* All boundary fields are mandatory (\*)
* Users cannot proceed unless:
  * Selection is completed down to the **last configured level**
  * Every selected boundary has its child boundary selected
* Clear error messages are shown if:
  * A level is missing
  * The hierarchy is incomplete

### Step 7: Configure Boundary Selection Overview Card

#### Purpose

The **Boundary Selection Overview Card** provides a quick summary of selections made.

#### What It Displays

* Number of selected boundaries at each hierarchy level\
  (e.g., 1 Country, 3 Provinces, 12 Districts)

#### Benefits

* Helps users:
  * Verify selections at a glance
  * Track progress across hierarchy levels
* Reduces errors before moving to the next step

**Boundary Selection Overview Card**

<figure><img src="../../../../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

### Step 8: Proceed to the Next Microplanning Step

Once:

* All hierarchy levels are selected
* Validation passes successfully

The user can proceed to the next step in the microplan creation flow.

## API Endpoints

<table><thead><tr><th width="202.64453125">Endpoint</th><th width="105">Method</th><th>Payload</th></tr></thead><tbody><tr><td>/boundary-service/boundary-relationships/_search</td><td>POST</td><td>{ "tenantId": "mz", "hierarchyType": "MICROPLAN", "includeChildren": true, "RequestInfo": {} }</td></tr><tr><td>/boundary-service/boundary-hierarchy-definition/_search</td><td>POST</td><td>{ "BoundaryTypeHierarchySearchCriteria": { "tenantId": "mz", "limit": 1, "offset": 0, "hierarchyType": "MICROPLAN" }, "RequestInfo": {} }</td></tr><tr><td>/project-factory/v1/project-type/search</td><td>POST</td><td>{ "CampaignDetails" : { "tenantId": "mz", "ids": [ "730fb389-5e60-4c43-b6ce-b1c109b23f54" ]},  "RequestInfo": {} }</td></tr><tr><td>/plan-service/config/_search</td><td>POST</td><td>{ "PlanConfigurationSearchCriteria": { "tenantId": "mz", "id": "660fb389-5e60-4c43-b6ce-b1c109b23f54" } ,"RequestInfo": {} }</td></tr><tr><td>/project-factory/v1/project-type/update</td><td>POST</td><td>{ "CampaignDetails":{"id":"8c413d61-c411-4c33-b6eb-76ea005a84c9","tenantId":"mz","status":"drafted","action":"draft","campaignNumber":"CMP-2024-12-03-006616","isActive":true,"parentId":null,"campaignName":"Malaria-Bednet Campaign-Fixed Popp0099","projectType":"LLIN-mz","hierarchyType":"MICROPLAN","boundaryCode":"MICROPLAN_MO","projectId":null,"startDate":1735810905674,"endDate":0,"additionalDetails":{"source":"microplan","disease":"MALARIA","resourceDistributionStrategy":"MIXED"},"resources":[],"boundaries":[],"deliveryRules":[],"auditDetails":{"createdBy":"f4f36858-0e9e-4150-a37f-444b90995e7c","lastModifiedBy":"f4f36858-0e9e-4150-a37f-444b90995e7c","createdTime":1733218905816,"lastModifiedTime":1733218919304}},"RequestInfo":{}}</td></tr><tr><td>/plan-service/config/_update</td><td>POST</td><td>`{"PlanConfiguration":{"id":"660fb389-5e60-4c43-b6ce-b1c109b23f54","tenantId":"mz","name":"Malaria-Bednet Campaign-Fixed Popp0099","campaignId":"8c413d61-c411-4c33-b6eb-76ea005a84c9","status":"DRAFT","files":[],"assumptions":[],"operations":[],"resourceMapping":[],"auditDetails":{"createdBy":"f4f36858-0e9e-4150-a37f-444b90995e7c","lastModifiedBy":"f4f36858-0e9e-4150-a37f-444b90995e7c","createdTime":1733218906001,"lastModifiedTime":1733218924572},"additionalDetails":{"key":"2"},"workflow":null},"RequestInfo": {} }</td></tr></tbody></table>
