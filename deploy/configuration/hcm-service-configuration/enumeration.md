---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-service-configuration/enumeration
---

# Enumeration

## Overview

This document describes the configuration and structure of the Checklist Module. The module supports dynamic checklists for household and individual enumeration, manages relationships, and enables offline data synchronisation (downsync) and referral flows. All aspects are highly configurable via MDMS and environment variables.

***

## Pre-requisites

* **MDMS Setup:**
  * MDMS schemas for checklist types, attributes, and household member relationship types must be present.
* **Database:**
  * Required tables/collections must exist (see Database Design).
* **Environment Variables:**
  * Downsync and referral feature flags should be set by DevOps.
* **Formula Parser:**
  * The system must have access to a formula parser for dynamic checklist rendering.
* **Proper Role Mapping:**
  * User roles must be mapped (e.g., DISTRIBUTOR) for context-aware checklist selection.

***

## Functionalities

### Checklist Rendering

* **Dynamic Selection:**
  * Checklists are selected based on:
    * `pageName`
    * `checklistType` (HOUSEHOLD, INDIVIDUAL)
    * `userRole` (e.g., DISTRIBUTOR)
    * `project`
    * Combinatorial codes (e.g., AGE.GENDER)
* **Conditional Logic:**
  * Visibility of checklists/attributes is controlled by formulas (e.g., show maternal health only for females).
* **Checklist Code Matching:**
  * Exact rendering is triggered if all matching parameters (pageName, checklistType, role, project, combinatorialCode) align.
* **Downsync Support:**
  * Each response is tagged with a reference ID for offline sync.
  * Mappings are maintained for mobile/offline use.

### Service Request & Downsync API

* **Entities:**
  * `ServiceRequest`: Tracks requests with fields like id, clientReferenceId, tenantId, attributes, etc.
  * `DownsyncModel`: Contains clientReferenceId, services, householdClientRefIds, individualClientRefIds, pagination, and filters.
* **Core Logic:**
  * `clientReferenceId` supports offline and referral management.
  * Referral management (if enabled) loads services by reference ID and tenant.
  * Downsync model maintains a list of services per clientReferenceId.
* **Service Search:**
  * Services can be searched by clientReferenceId, with pagination and filtering.
* **Configurable Downsync:**
  * Downsync can be toggled via environment variables.
  * Config changes ensure clientReferenceId is persisted.

### Household Service & Relationship Management

* **Entities:**
  * `Household`: id, householdType, members
  * `HouseholdMember`: id, householdId, individualId, relationshipType
  * `RelationshipTypes` (from MDMS): Defines allowed types (e.g., CHILD, MOTHER), max allowed, and active status.
* **Logic:**
  * Relationships are supported only if householdType is FAMILY.
  * Relationship types and limits are defined in MDMS (e.g., maxAllowed for CHILD is 4).
  * Relationships are stored in a dedicated table.
  * Flows are integrated with referral management and downsync.

***

## Deployment Details

* Ensure all required database tables/collections are created and indexed.
* MDMS entries for checklist types, attributes, and household relationships must be deployed.
* Set environment variables (downsync, referral flags) according to deployment environment.
* Deploy the formula parser or ensure access to it within the application.
* Update persister and service configuration files as needed to support new entities and fields.

***

## API Details

#### Checklist APIs

* **Fetch Checklists:**
  * Returns checklists based on context (pageName, checklistType, role, project, combinatorial codes).
* **Submit Checklist Response:**
  * Accepts responses tagged with appropriate reference IDs for offline sync.

#### Downsync APIs

* **Downsync Fetch:**
  * Returns submitted checklists and services for a given clientReferenceId.
* **Service Search:**
  * Search for services by clientReferenceId, supports pagination and filters.

#### Household APIs

* **Link Members:**
  * Associate individuals to households with relationship types from MDMS.
* **Manage Relationships:**
  * Updates and validates household member relationships.

***

## Configuration Details

#### MDMS Schemas

* **Checklist:**
  * Fields: id, type, code, pageName, project, role, formula, attributes, active
* **ChecklistAttribute:**
  * Fields: id, checklistId, code, label, type, options, visibilityFormula, mandatory, order
*   **RelationshipTypes (HCM.HOUSEHOLD\_MEMBER\_RELATIONSHIP\_TYPES):**

    ```json
    [
      { "code": "CHILD", "maxAllowed": 4, "active": true },
      { "code": "MOTHER", "maxAllowed": 1, "active": true },
      { "code": "FATHER", "maxAllowed": 1, "active": true }
    ]
    ```

#### Environment Variables

* **Enable/Disable Downsync:**
  * `DOWNSYNC_ENABLED=true|false`
* **Enable/Disable Referral Management:**
  * `REFERRAL_MANAGEMENT_ENABLED=true|false`

***

## Database Design

* **Checklists:** Stores checklist definitions.
* **ChecklistAttributes:** Stores checklist questions/attributes.
* **ChecklistResponses:** Links responses to household/individual.
* **ServiceRequests:** Tracks enumeration service requests.
* **Households:** Household entities.
* **HouseholdMembers:** Relationship between individuals and households.
* **MDMS\_HouseholdRelationshipTypes:** Configuration for allowed relationships.

***

{% hint style="info" %}
### Notes

* All configurations (checklists, relationships, referral flags) are MDMS and environment variable-driven.
* Downsync/offline flows are configurable and can be toggled per environment.
* Ensure role mappings and formula logic are tested for each deployment.
{% endhint %}

***
