# Microplanning - Functional Specifications

### 1. Purpose

The Microplanning module enables planning, validation, approval, and finalisation of campaign resource estimates (e.g., bednets, SPAQ) at the village level, based on approved population data and facility-to-village catchment mapping. The module supports hierarchical workflows across administrative levels with full auditability.

### 2. Scope

In scope:

* Facility/POS to village catchment mapping
* Microplan estimation generation
* Validation, approval, and correction workflows
* Finalisation and download of microplan estimates
* Geo-spatial visualisation of villages and facilities

Out of scope:

* Campaign execution and logistics setup
* Population data creation (only consumption of approved data)

### 3. User Roles

* **Population Data Approver (National)**: Approves population data required for mapping and estimation
* **Facility Catchment Assigner / Mapper**: Maps villages to facilities/POS
* **Microplan Approver**: Validates, customises, and approves microplan estimations
* **Microplan Viewer**: View-only access to validated microplans

### 4. Preconditions & Validations

* Population data must be approved at the national level before:
  * Facility catchment mapping
  * Microplan estimation workflows
* Facility-to-village mapping must be finalised before:
  * Geo-spatial views
  * Microplan validation and approval

### 5. Functional Overview

#### 5.1 Facility Catchment Mapping

**Landing Dashboard**

* Displays all facilities/POS within the user’s administrative boundary
* Summary cards:
  * Villages with mapped facilities
  * Facilities with mapped villages
* Search and filter facilities by type, status, fixed post, and residing village

**Unassigned Villages**

* Lists villages not mapped to any facility
* Mapper can assign one or more villages to a selected facility
* Optional distance input (numeric only)
* Confirmation required before assignment

**Assigned Villages**

* Lists villages already mapped to a facility
* Mapper can unassign villages (with confirmation)

**Finalisation**

* The national-level assigner can finalise mapping
* Enabled only when all campaign villages are mapped
* Post-finalisation: mapping becomes read-only
* Triggers microplan estimation

#### 5.2 Microplan Estimation

* System generates village-level estimates based on:
  * Approved population data
  * Campaign configuration
  * Facility mapping (for HR estimation only)
* Supports multiple campaign types (e.g., Bednet, SMC)

#### 5.3 Microplan Validation & Approval

**Landing Dashboard (Approver)**

* Villages grouped by status:
  * Pending validation
  * Validated
  * Pending approval
* Hierarchical visibility across parent/child boundaries
* Filters by boundary, facility, and village attributes

**Actions**

* Validate microplan estimates (bulk supported)
* Customise estimation assumptions
* Send estimates for approval
* Approve estimates (hierarchical)
* Send back for correction (with mandatory comment)

**Workflow Rules**

* Validation moves villages to “Validated” state
* Customisation requires approval by the higher hierarchy (except national)
* National approver can directly save assumption changes

#### 5.4 Finalisation of Microplan

* National Microplan Approver can finalise the microplan when:
  * Pending validation = 0
  * Pending approval = 0
  * All villages validated
* Post-finalisation:
  * Microplan becomes read-only
  * Estimations available for Excel download

#### 5.5 Geo-spatial Visualisation

* Map-based view of villages and facilities
* Boundary-based filtering
* Toggle layers: villages, facilities/POS
* Tooltips show key estimation and capacity data

### 6. Data & Metrics

#### Fixed Data Points

* Administrative boundaries
* Approved population and target population
* Assigned facility/POS
* Village attributes (road, terrain, security – if available)

#### Metrics

**Bednet Campaign**

* Target population
* Households
* Bednets and bales required

**SMC Campaign**

* Target population (3–11 months, 12–59 months)
* SPAQ blisters (with/without buffer)

### 7. Audit & Traceability

* **Comment Logs**: Action, user, role, timestamp, comment
* **Change Logs**: Assumption changes, old vs new values, timestamp
* All state transitions are recorded and visible to authorised users

### 8. Permissions & Controls

* Actions restricted by role and administrative boundary
* Finalised data is strictly read-only
* All destructive actions require confirmation

### 9. Outputs

* Downloadable microplan estimation (Excel)
* Read-only dashboards for viewers and post-finalisation users
