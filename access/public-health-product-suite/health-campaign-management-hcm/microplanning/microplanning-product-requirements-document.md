---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/access/public-health-product-suite/health-campaign-management-hcm/microplanning/product-requirements-document
---

# Microplanning - Product Requirements Document

### 1. Overview

The Microplanning Module enables detailed planning for health campaigns (e.g., immunisation, disease prevention) to ensure effective delivery of interventions to target populations. It supports structured planning across administrative hierarchies by leveraging registry data, role-based workflows, and standardised estimation methodologies.

The module is designed to help program teams accurately estimate population coverage, resource requirements, and operational needs prior to campaign execution.

***

### 2. Goals and Objectives

#### Primary Goals

* Enable accurate population-based planning at village and higher administrative levels.
* Support structured validation and approval workflows for microplan data and estimations.
* Generate reliable resource estimates for campaign execution.
* Integrate seamlessly with the Admin Console for campaign setup.

#### Non-Goals (v0.1)

* Creation or modification of boundary, facility, or vehicle registries after microplan setup.
* Advanced analytics or predictive modelling beyond defined estimation logic.

***

### 3. Assumptions

* **Updated Registries:** Boundary, facility, and vehicle registry data are accurate and up-to-date at microplan setup time.
* **Role-Based Access:** Users are pre-assigned roles with defined permissions to ensure data integrity and security.
* **Standardised Data Collection:** Data collectors are trained and follow standard methodologies.
* **Connectivity:** Internet or mobile connectivity is generally available; limited offline support may exist for specific use cases.
* **Localisation:** Platform supports English, French, and Portuguese in v0.1.
* **Scalability:** System can handle multiple campaigns, users, and datasets without performance degradation.
* **Training & Support:** Users receive adequate onboarding and operational support.
* **Sustainability:** Platform is designed for long-term maintenance and incremental enhancements.
* **Registry Freeze:** No registry changes are allowed after microplan setup is completed.

***

### 4. User Personas and Roles

#### 4.1 System Administrator

* Administrative level: National/Country
* Responsibilities:
  * Configure campaign boundaries
  * Set up microplan assumptions
  * Manage initial data and configurations

#### 4.2 Data Collector

* Responsibilities:
  * Collect and validate population data at the village level
  * Capture geographic and contextual attributes (accessibility, security, etc.)

#### 4.3 Supervisors

Supervisory roles may exist across multiple administrative hierarchies with scoped permissions:

* **Population Data Approver**
  * Validate and approve population data
  * Approved data feeds into resource estimation
* **Facility Catchment Mapper**
  * Map facilities to administrative catchment areas
* **Microplan Approver**
  * View, edit, validate, and approve microplan estimations
* **Microplan Viewer**
  * Read-only access to microplan estimations

> Role permissions are governed through an actor–noun–verb access control model.

***

### 5. Pre-requisites and Configuration

#### 5.1 Registry Configuration

* Boundary registry configured during country instance creation
* Facility registry configured with:
  * Facility type
  * Facility status
  * Fixed post indicator
  * Facility usage (Active/Inactive)
* Vehicle registry configured with capacity units aligned to campaign type

#### 5.2 MDMS Dependencies

* Facility types, statuses, usage values
* Vehicle capacities
* Campaign-specific capacity units (e.g., Bales, Blisters)

***

### 6. Registry Data Usage

The Microplanning Module consumes the following registries (managed via MDMS in v0.1):

1. **Boundary Registry**
2. **Facility Registry**
3. **Vehicle Registry**

Future versions will shift registry management to the Admin Console.

***

### 7. User Journey (High-Level)

1. System Administrator sets up the microplan and campaign boundaries.
2. Data Collectors capture population and village-level attributes.
3. Population Data Approvers validate population data.
4. Facility Catchment Mappers assign facilities to boundaries.
5. Microplan Approvers validate and approve estimations.
6. National-level approvers finalise the microplan.
7. Finalised microplan is made available for campaign setup and download.

(Detailed flows are documented separately in the Miro board.)

***

### 8. Functional Scope (v0.1)

#### Core Capabilities

* Microplan creation and configuration
* Role-based task assignment
* Population data collection and approval
* Facility-to-boundary mapping
* Resource estimation
* Validation, approval, and finalisation workflows
* Status tracking and audit logs
* Export of finalised microplan estimates (Excel)

***

### 9. Console Integration Requirements

The Microplanning Module must integrate with the Admin Console to enable campaign setup.

#### Data Shared with Admin Console

* Microplan name and campaign details
* Facility data
* Administrative boundaries with targets
* Resource requirements based on distribution strategy:
  * Registration and distribution staff (fixed post & household)
  * Supervisors and monitors
  * Boundary-wise human resource counts

#### Admin Console Responsibilities

* Provide UI for selecting a microplan during campaign setup
* Consume and apply microplan data for campaign configuration

***

### 10. Success Metrics (v0.1)

#### Adoption & Engagement

* Number of registered microplanning users
* Average session duration
* Number of microplans created per country
* Reuse rate of existing microplans

#### Accuracy & Efficiency

* Population coverage accuracy (planned vs actual)
* Resource utilisation accuracy (estimated vs used)
* Time taken to finalise a microplan

***

### 11. System Specifications & Validation

* The Microplanning Module must comply with defined system specifications and validation rules.
* Detailed technical specifications are documented separately and referenced for v0.1 implementation.

***

### 12. Release Scope

**Version:** v0.1\
**Focus:** Foundational microplanning workflows, approvals, estimations, and admin console integration.
