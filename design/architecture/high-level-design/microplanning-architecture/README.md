# Microplanning Architecture

## Overview

The Microplanning module enables the creation, validation, approval, and finalisation of microplans for health campaigns across multiple administrative boundaries. It supports population planning, facility mapping, resource estimation, and hierarchical approvals at sub-national and national levels. The system is designed to be scalable, secure, and configurable to support diverse campaign types and country contexts.

## Goals

* Support **end-to-end microplanning workflows** from setup to final approval
* Enable **role-based access and boundary-based governance**
* Ensure **data integrity and auditability** through validations and approval flows
* Integrate seamlessly with **registry systems** and the **Admin Console**
* Scale across **multiple countries, campaigns, and users**

## Service Architecture

The Microplanning module follows a **modular, service-oriented architecture**, aligned with DIGIT platform principles. Each service encapsulates a clear business responsibility and communicates via APIs and asynchronous events where required.

<figure><img src="../../../../.gitbook/assets/image (62).png" alt=""><figcaption><p><em>Microplanning Service Architecture</em></p></figcaption></figure>

### Key Architectural Characteristics

* Stateless services
* Centralised registry consumption (Boundary, Facility, Vehicle)
* Event-driven processing for data ingestion
* Strong validation and approval layers
* Read-optimised views for dashboards and maps

## Services Overview  <a href="#overview-of-services" id="overview-of-services"></a>

#### 1. Plan Management Service

**Purpose:**\
Manages the lifecycle of microplans.

**Responsibilities:**

* Microplan creation and configuration
* Campaign boundary selection
* Assignment of users and roles
* Facility-to-catchment mapping
* Microplan assumptions and estimation formulas
* Validation, approval, and finalisation of microplans
* Exposure of finalised microplan data for Admin Console integration

#### 2. Census Management Service

**Purpose:**\
Manages population data used for microplanning.

**Responsibilities:**

* Storage and management of village-level population data
* Support for centrally uploaded and field-validated data
* Population data validation rules
* Approval and rejection workflows
* Maintenance of audit trails (comments, status history)

#### 3. Resource Generator Service

**Purpose:**\
Processes uploaded data files and generates system-ready records.

**Responsibilities:**

* Parse population and facility Excel/Geo files
* Validate file structure and data integrity
* Generate population entities and facility-boundary mappings
* Trigger downstream processing for estimation readiness

#### 4. Project Factory Service

**Purpose:**\
Provides template and configuration utilities.

**Responsibilities:**

* Generate population upload templates
* Generate facility upload templates
* Enforce campaign-specific configuration rules
* Ensure standardised data collection formats

## Service Interactions <a href="#service-interactions" id="service-interactions"></a>

* **Census Management**
  * Stores population data
  * Manages validation and approval workflows

<figure><img src="../../../../.gitbook/assets/image (60).png" alt=""><figcaption><p><em>Census Management Service Interactions</em></p></figcaption></figure>

* **Plan Management**
  * Consumes approved population and facility mappings
  * Performs microplan estimation
  * Manages approval and finalisation workflows

<figure><img src="../../../../.gitbook/assets/image (61).png" alt=""><figcaption><p><em>Plan Management Service Interactions</em></p></figcaption></figure>
