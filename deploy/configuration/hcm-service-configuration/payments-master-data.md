---
description: Health payments master data configuration details
---

# Payments Master Data

## Overview

This document outlines the configuration details for managing payment master data in the HCM module. The configuration enables or restricts payment approval timing and sets the lowest boundary level for payment-related operations, ensuring flexibility and alignment with organisation and campaign requirements.

***

## Pre-requisites

* **MDMS (Master Data Management System):**
  * Ensure MDMS is set up and accessible for your environment.
* **Tenant Hierarchy:**
  * Tenant IDs and boundary types (e.g., DISTRICT, BLOCK, etc.) should be defined and consistent.
* **HCM Module Integration:**
  * The payments configuration should be referenced by the HCM module for all payment and approval flows.

***

## Functionalities

* **Approval Timing Control:**
  * `enableApprovalAnyTime` flag determines if payment approvals can be performed at any time or only after campaign validation/end date.
    * `true`: Approvals allowed at any time.
    * `false`: Approvals allowed only after campaign end/validation.
* **Boundary Level Selection:**
  * `lowestLevelBoundary` specifies the lowest administrative level (e.g., DISTRICT, BLOCK) available in the boundary dropdown during payment operations, enhancing localisation and control.

***

## Deployment

* **Configuration File Placement:**
  * Add/update the configuration in the MDMS under the correct tenant and module (typically in the `paymentsConfig` section).
* **Version Control:**
  * Track changes to the MDMS configuration in your source code repository.
* **Environment Promotion:**
  * Promote the configuration through your standard DevOps process (dev → staging → prod), ensuring all environments are updated.
* **Validation:**
  * After deployment, validate via the HCM module UI or API that payment approval and boundary dropdowns behave as configured.

***

## API

* **MDMS Fetch:**
  * The HCM module fetches payment configuration via the MDMS API, filtering by `tenantId` and `moduleName`.
* **Usage Example:**
  * When a user initiates a payment approval, the system checks `enableApprovalAnyTime` and the current campaign status.
  * The boundary dropdown in payment forms is populated up to the specified `lowestLevelBoundary`.

***

## Configuration

#### Sample Configuration

```json
{
  "tenantId": "{{tenantId}}", 
  "moduleName": "HCM", 
  "paymentsConfig": [ 
    { 
      "tenantId": "{{tenantId}}", 
      "enableApprovalAnyTime": "{{boolean}}", // e.g., true - Allows approval at any time. To restrict approval to only validate through the campaign endDate, set to false.
      "lowestLevelBoundary": "{{boundaryType}}" // e.g., "DISTRICT" - Specifies the lowest-level dropdown option in boundary selection
    } 
  ] 
}
```

**Field Explanations:**

* `tenantId`: ID of the tenant (city, state, or organisation).
* `moduleName`: Always set to `"HCM"` for this configuration.
* `enableApprovalAnyTime`: Boolean to allow payment approval anytime (`true`) or restrict to campaign end (`false`).
* `lowestLevelBoundary`: Sets the lowest selectable boundary type in the UI (e.g., `"DISTRICT"`, `"BLOCK"`).

***

#### Configuration Links

<table><thead><tr><th width="157.73828125">Master</th><th width="155.4921875">Module</th><th width="210.1875">Reference Link</th><th>Description</th></tr></thead><tbody><tr><td>HCM</td><td>paymentsConfig</td><td><a href="https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.8/payments-config.json">HCM.paymentsConfig</a></td><td>UI Configs</td></tr><tr><td>HCM</td><td>WORKER_RATES</td><td><a href="https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.8/workerRates.json">HCM.WORKER_RATES</a></td><td>Rate Master Configs</td></tr><tr><td>common-masters</td><td>MusterRoll</td><td><a href="https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.8/MusterRoll.json">common-masters.MusterRoll</a></td><td>Muster Roll and Attendance Configs</td></tr></tbody></table>
