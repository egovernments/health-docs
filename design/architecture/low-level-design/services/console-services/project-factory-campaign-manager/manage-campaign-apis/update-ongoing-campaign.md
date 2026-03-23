---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/low-level-design/services/project-factory-campaign-manager/manage-campaign-apis/update-ongoing-campaign
---

# Update Ongoing Campaign

## Overview

This document details the low-level design for handling campaign creation and update flows when a parent campaign is present. The system supports hierarchical campaigns, boundary inheritance, resource template generation, and robust retry mechanisms. This design aims to ensure data consistency, correct parent-child relationships, and efficient error recovery.

***

## Data Model Changes

#### Database: Campaign Details Table

* **New Columns**
  * `isActive` (boolean): Indicates if the campaign is currently active.
  * `parentId` (string): References the parent campaign’s unique ID, if any.

```sql
ALTER TABLE CampaignDetails
  ADD COLUMN isActive BOOLEAN DEFAULT TRUE,
  ADD COLUMN parentId VARCHAR(64) NULL;
```

***

## Request Validation Logic

#### Parent Campaign Validation

* **If `parentId` is present in the request:**
  * **On `create` action:**
    * Parent campaign (`parentId`) must exist and `isActive = true`.
  * **On `update` action:**
    * Parent campaign (`parentId`) must exist and `isActive = false` (inactive).

***

## Boundary Management Logic

* **For child campaigns:**
  * The `boundaries` array in the request must contain only new boundaries.
  * Existing boundaries are fetched from the parent campaign.
  * Merged boundaries = parent boundaries + new boundaries (for use in template/resource generation).

***

## Resource & Template Generation

#### On Campaign Creation (with Parent Campaign)

* Generate templates for all three types: **boundary**, **user**, **facility**.
* If `actionInUrl = create` and `parentId` is present, templates are generated freshly using both parent and new boundaries.

#### On Campaign Update

* For newly added boundaries, create new projects/resources only for those.
* If existing targets are updated, call update on the respective project with new target mappings.
* Facility and user sheets can be edited: updating these updates related mappings (ProjectFacility, ProjectStaff).

***

## Retry Mechanism

* If campaign creation or update fails, a retry API allows the process to restart from the failure point.
* Retry is stateful and resumes based on the persisted CampaignDetails and status.

**Retry API Example:**

```http
POST /project-factory/v1/project-type/retry
Body: {
  CampaignDetails: { ... }, // Full campaign object
  RequestInfo: { ... }
}
```

***

## Campaign Object Structure

* See below for sample fields (simplified):

```json
{
  "id": "campaign-uuid",
  "tenantId": "mz",
  "status": "drafted",
  "action": "create",
  "campaignNumber": "...",
  "isActive": true,
  "parentId": "parent-campaign-uuid",
  "campaignName": "...",
  "projectType": "...",
  "hierarchyType": "...",
  "boundaries": [...],
  "resources": [
    { "type": "facility", "filename": "...", "resourceId": "...", "filestoreId": "..." },
    { "type": "boundaryWithTarget", "filename": "...", "resourceId": "...", "filestoreId": "..." },
    { "type": "user", "filename": "...", "resourceId": "...", "filestoreId": "..." }
  ],
  "deliveryRules": [...],
  "auditDetails": { ... }
}
```

* After each update and once the campaign is in the "Created" state, templates are consolidated for future updates.

***

## Update & Multiple Update Handling

* After a campaign reaches the "Created" state:
  * Uploaded template sheets (Facility, User, Target) are consolidated back to the initial format.
  * Any subsequent update is handled as the first update (fresh diff against the current state).

***

## Edit Mappings in Update Flow

* In the update flow, facility mappings to boundary codes can be edited and toggled (active/inactive).
* Updates propagate to ProjectFacility and ProjectStaff mapping tables.

***

## Sequence Flow

1. **Request** received with or without `parentId`.
2. **Validation:**
   * If `parentId` present, validate parent state as per action.
3. **Boundary merge:**
   * To create, merge the parent and new boundaries.
   * For updates, only new boundaries are considered for new projects.
4. **Template/Resource Generation:**
   * Generate templates for relevant types (boundary, user, facility).
   * Edit and manage sheets/mappings as per user input.
5. **Retry:**
   * On failure, retry resumes from the last state using the latest CampaignDetails object.

***

## Error & Edge Case Handling

* **Validation Errors:**
  * If the parent campaign is not in the required state, reject the request.
  * If new boundaries overlap with the parent, reject or merge as per the business rule.
* **Retry Errors:**
  * If the retry fails repeatedly, log the state and escalate for manual intervention.

***

{% hint style="info" %}
Points to consider:

* All actions logged with audit details (user, timestamp).
* Only authorised roles can create/update hierarchical campaigns.
* Parent-child relationships can be extended to deeper hierarchies if needed.
* Additional resource/template types can be added.
* Retry logic can be enhanced for partial retries and granular checkpoints.
{% endhint %}

***

## Sample Payload

{% include "../../../../../../../.gitbook/includes/expandable-code-block.md" %}

**Multiple updates to a Campaign**

1. Once the ongoing campaign is updated and reaches the "Created" state, the updated sheet templates (i.e., Facility, User, and Target) are consolidated back into the format used during the initial "Create" flow.
2. This ensures that when you attempt to update the campaign again, it will be treated as the first update.

**Retry API Payload**

{% include "../../../../../../../.gitbook/includes/expandable-code-block.md" %}

