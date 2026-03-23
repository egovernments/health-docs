---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-console-configuration/console-ui-configuration/hcm-console-web-ui/campaign-setup/my-campaign/campaign-timeline
---

# Campaign Timeline

## Overview

The **Campaign Timeline** provides a visual view of a campaign’s progress across its lifecycle. It helps users track creation stages and understand the current state of a campaign.

The timeline is available for campaigns in the following states:

* **Upcoming**
* **Ongoing**
* **Completed**
* **Failed**

Users can access the timeline from:

* The **Campaign Summary** page
* The **My Campaign** screen (via the Actions menu)

## Steps

### Step 1: Enable Timeline Access

#### Access Points

1. **Campaign Summary**
   * The timeline is displayed directly on the summary page.
2. **My Campaign Screen**
   * Users click the **Action** button for a campaign.
   * The timeline opens as a **pop-up modal**.

<figure><img src="../../../../../../../.gitbook/assets/image (187).png" alt=""><figcaption><p>Timeline In summary page</p></figcaption></figure>

### Step 2: Render Timeline Stages

**Purpose:** Show campaign progress visually.

#### Timeline States

The timeline displays campaign stages as:

* **Upcoming** – Steps that are yet to start
* **Current** – The step currently in progress
* **Completed** – Steps that have finished successfully

These states update dynamically based on campaign status.

<figure><img src="../../../../../../../.gitbook/assets/image (188).png" alt=""><figcaption></figcaption></figure>

### Step 3: Display Timeline During Campaign Creation

**Behaviour**

* While campaign creation is in progress:
  * The timeline shows:
    * Completed steps
    * The current step
    * Upcoming steps
* This view is consistent across:
  * Summary screen
  * My Campaign timeline pop-up

<figure><img src="../../../../../../../.gitbook/assets/image (189).png" alt=""><figcaption><p>Timeline in my campaign</p></figcaption></figure>

### Step 4: Configure Timeline Pop-up from My Campaign

**Behaviour**

* Clicking **Action → View Timeline** (or equivalent option):
  * Opens the timeline as a pop-up
  * Displays the same step progression as the summary screen
* User credentials become available once campaign creation completes successfully.

## Reference Links

* [Timeline Component File Link](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/TimelineComponent.js)

#### API Details

<table><thead><tr><th width="244.2890625">End point</th><th width="139.51953125">Method</th><th>Params</th></tr></thead><tbody><tr><td>/project-factory/v1/project-type/getProcessTrack</td><td>POST</td><td>params: { <br>campaignId: campaignId,<br> },</td></tr></tbody></table>
