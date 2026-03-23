---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-console-configuration/console-ui-configuration/hcm-console-web-ui/campaign-setup
---

# Campaign Setup

## Overview

Use **Campaign Setup** to create and configure a campaign in the HCM Console. This flow covers campaign basics, target boundaries, delivery rules, and app setup.

You can:

* Create a **new campaign** (import is not available in this version).
* Define **campaign details** like type, name, and dates.
* Select **target boundaries** for rollout.
* Configure **delivery cycles** and delivery rules.
* Configure the **mobile app experience** for field teams.
* Upload **facilities, users, and targets**.
* Optionally set up **checklists**.

## Steps

Click on **Create Campaign.** The campaign home screen contains two options:

1. **Create New Campaign**
2. **Import Existing Campaign** (not available in this version).

<figure><img src="../../../../../../.gitbook/assets/image (425).png" alt=""><figcaption></figcaption></figure>

***

### Create New Campaign

#### Step 1: Select Campaign Type

* Click **Create New Campaign**.
* A pop-up will show the items needed to create a campaign. Click **Continue**.
* Choose the **campaign type** from a dropdown (options come from MDMS: `HCM-PROJECT-TYPES.projectTypes`).
* This is a mandatory step.

<figure><img src="../../../../../../.gitbook/assets/image (426).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/image (427).png" alt=""><figcaption></figcaption></figure>

#### Step 2: Enter Campaign Name

* Enter a **name** for the campaign.
* A default name will be suggested based on the campaign type, current month, and year. You can edit this if needed.
* **Validation:** The campaign name must be unique.
* **Validation API:** `/project-factory/v1/project-type/search`

<figure><img src="../../../../../../.gitbook/assets/image (428).png" alt=""><figcaption></figcaption></figure>

#### Step 3: Set Campaign Dates

* Enter **start and end dates** for the campaign.
* **Validation:**
  * Dates cannot be earlier than today.
  * End date must be later than start date.
* **API Used:** `/project-factory/v1/project-type/create`

<figure><img src="../../../../../../.gitbook/assets/image (429).png" alt=""><figcaption></figcaption></figure>

After submitting, you will be redirected to the **campaign details screen**. You can continue creating the campaign or save it as a draft under **My Campaigns** and resume later.

<figure><img src="../../../../../../.gitbook/assets/image (430).png" alt=""><figcaption></figcaption></figure>

* You can edit the campaign name and dates anytime using the edit icons.

***

### Tasks to Complete Campaign Setup

1.  **Define Target Areas**

    * Select the boundaries where the campaign will run.
    * **Validation:** Must select down to the lowest level boundary. If a parent boundary is chosen, at least one child must also be selected.

    <figure><img src="../../../../../../.gitbook/assets/image (431).png" alt=""><figcaption></figcaption></figure>
2.  **Configure Delivery**

    * Define campaign cycles, number of deliveries, and their dates.
    * Set delivery conditions and allocate resources for each cycle.

    <figure><img src="../../../../../../.gitbook/assets/image (432).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../../../../../../.gitbook/assets/image (433).png" alt=""><figcaption></figcaption></figure>
3. **Configure Mobile App**\
   This sets up the app that field workers will use.
   *   **Module Selection**

       * Choose modules to include in the app (from MDMS: `HCM-ADMIN-CONSOLE.FormConfigTemplate`).
       * Selected modules are saved under `HCM-ADMIN-CONSOLE.AppConfigSchema`.
       * Localisation modules are auto-created for the campaign.

       <figure><img src="../../../../../../.gitbook/assets/image (443).png" alt=""><figcaption></figcaption></figure>
   *   **Feature Selection**

       * Select features for each module.
       * Features are fetched from `HCM-ADMIN-CONSOLE.AppModuleSchema`.
       * Display depends on what’s marked as selected in the AppConfigSchema.

       <figure><img src="../../../../../../.gitbook/assets/image (441).png" alt=""><figcaption></figcaption></figure>
   *   **App Configuration**

       * Configure how features will appear in the app.

       <figure><img src="../../../../../../.gitbook/assets/image (440).png" alt=""><figcaption></figcaption></figure>
4. **Upload Data**
   * Upload sheets for facilities, users, and targets.
5. **Checklist (Optional)**
   * Create checklists if needed.

Once all tasks are done, click **Create Campaign**. The campaign will appear under **Upcoming Campaigns** in **My Campaigns**.

***

### My Campaign Page

Accessible from the home screen. Shows the status of your campaigns.

<figure><img src="../../../../../../.gitbook/assets/image (439).png" alt=""><figcaption></figcaption></figure>

Each campaign card provides actions:

* **Clone Campaign** – Create a copy of an existing campaign. You just need to enter a new name and start/end dates.

<figure><img src="../../../../../../.gitbook/assets/image (437).png" alt=""><figcaption></figcaption></figure>

* **Download Mobile App** – Opens a QR code pop-up to download the app.

<figure><img src="../../../../../../.gitbook/assets/image (438).png" alt=""><figcaption></figcaption></figure>

* **Download User Credentials** – Downloads an Excel with user credentials and passwords.
* **Edit Campaign** – Update boundaries or delivery dates.
