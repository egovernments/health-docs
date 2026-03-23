---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/high-level-design/hcm-console-design
---

# HCM Console Architecture

The platform architecture illustration below provides a visual representation of the key components and layers that facilitate a campaign creation flow in health campaign management.

<figure><img src="../../../.gitbook/assets/Screenshot 2025-12-19 at 9.19.24 AM.png" alt=""><figcaption></figcaption></figure>



### Admin User

**Description:**\
Admin users configure, manage, and monitor campaigns through the HCM Console. They are responsible for setting up campaign parameters, managing users and facilities, and overseeing operational readiness.

***

### Console Web

**Description:**\
The Console Web is the primary administrative interface for HCM. It enables administrators to configure campaigns, manage templates, set up boundaries, and control master and operational data through a unified web-based UI.

**Key Capabilities:**

* Campaign configuration and setup
* Template selection and customization
* Configuration management across services
* Boundary management and hierarchy setup
* Master data configuration and validation

***

### Templates

**Description:**\
Templates represent predefined program and campaign configurations used to standardize campaign creation. These templates encapsulate domain-specific workflows and data structures.

**Examples:**

* Bednet
* SMC
* NTD
* IRS
* Polio

***

## Configuration

**Description:**\
The Configuration module manages all configurable aspects of campaigns and applications, enabling flexible, reusable, and template-driven setups without requiring code changes.

**Responsibilities:**

* Defines application behaviour through configurations
* Drives campaign-specific logic consumed by Console and Mobile apps
* Ensures consistency across templates, campaigns, and field execution

**Includes:**

* Application Screens
* Delivery Rules & Products
* Localization
* Campaign Boundaries
* Campaign Users & Facilities
* Checklists
* Targets

***

### HCM Mobile Application

**Description:**\
The HCM Mobile Application is used by field staff to execute campaign operations. It consumes configurations and data set up through the Console.

**Purpose:**

* Field operations execution
* Task completion and checklist handling
* Data capture during campaigns

***

### API Gateway

**Description:**\
The API Gateway acts as a single entry point for all client applications. It routes requests to backend services, enforces security, and provides traffic control.

**Responsibilities:**

* Request routing
* Authentication and authorization enforcement
* API versioning and rate limiting

***

### User Service

**Category:** Core Platform Service

**Description:**\
Manages user identities and access across the platform.

**Responsibilities:**

* Authentication
* Authorization
* Role and access management

***

### Boundary Service

**Category:** Core Platform Service

**Description:**\
Maintains geographic hierarchy and boundary relationships used across campaigns.

**Responsibilities:**

* Geographic hierarchy data management
* Boundary relationships

***

### HRMS Service

**Category:** Core Platform Service

**Description:**\
Handles employee-related data required for campaign execution.

**Responsibilities:**

* Employee management
* Assignment to facilities and campaigns

***

### Boundary Management Service

**Category:** Console Service

**Description:**\
Provides administrative capabilities to manage boundary templates and boundary creation.

**Responsibilities:**

* Boundary template management
* Boundary creation and updates

***

### Excel Ingestion Service

**Category:** Console Service

**Description:**\
The Excel Ingestion Service enables bulk configuration and data setup through structured Excel templates, accelerating campaign preparation.

**Responsibilities:**

* Validates uploaded Excel files against MDMS schemas
* Parses and transforms Excel data into system-compatible formats
* Supports multiple campaigns and delivery rule templates
* Integrates with FileStore for file handling

***

### Project  Factory Service

**Category:** Console Service

**Description:**\
The Project (Campaign) Factory Service orchestrates campaign creation by combining user inputs from the Console with predefined templates and master data. It acts as the central workflow engine for campaign instantiation.

**Responsibilities:**

* Generates campaign data based on selected templates
* Integrates with MDMS for template and configuration retrieval
* Consumes boundary hierarchy and localisation data
* Creates and initialises campaign, facility, and user mappings

***

### MDMS (Master Data Management Service)

**Category:** Core Platform Service

**Description:**\
MDMS serves as the authoritative repository for master and configuration data required for campaign creation and execution.

**Responsibilities:**

* Stores campaign templates and configuration schemas
* Maintains delivery rule definitions and validation attributes
* Provides schema validation for Excel ingestion
* Supports type-to-API mapping and configuration resolution
* &#x20;App Configuration Templates & Actual Configs
* More details on Master data can be accessed[ here](../../../deploy/configuration/hcm-console-configuration/)

***

### Localisation Service

**Category:** Core Platform Service

**Description:**\
Provides multilingual support and localized content for applications.

**Responsibilities:**

* Language support
* Localization template management

***

### Project Service

**Category:** Health Domain Service

**Description:**\
Manages campaign timelines, rules, and execution parameters.

**Responsibilities:**

* Campaign schedules and rules
* Facility–user mapping

***

### Facility & Product Service

**Category:** Health Domain Service

**Description:**\
Manages facilities and products involved in campaign delivery.

**Responsibilities:**

* Facility management
* Product management

***

### Service Request Service

**Category:** Health Domain Service

**Description:**\
Handles operational service requests raised during campaign execution.

**Responsibilities:**

* Checklist management
* Task management

***

### FileStore Service

**Category:** Core Platform Service

**Description:**\
Provides centralized and secure file storage capabilities for the HCM platform.

**Responsibilities:**

* File upload, storage, and retrieval
* Pre-signed URL based access
* Support for Excel uploads and attachments

#### Click [here](../low-level-design/services/admin-console/) to know more.
