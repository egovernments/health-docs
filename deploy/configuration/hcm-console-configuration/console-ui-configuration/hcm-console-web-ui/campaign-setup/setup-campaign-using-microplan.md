---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-console-configuration/console-ui-configuration/hcm-console-web-ui/campaign-setup/setup-campaign-using-microplan
---

# Setup Campaign Using Microplan

## **Overview** <a href="#overview" id="overview"></a>

The **Setup Campaign** flow enables authorised users to create a campaign from an **approved microplan**. The system validates user access, creates a draft campaign, generates required data templates, fetches data from Microplan APIs, and prepares the campaign for configuration.

## Steps

### Step 1: Validate User Role

**Purpose:** Ensure only authorised users can initiate campaign setup.

* **Required Role:** `MICROPLAN_CAMPAIGN_INTEGRATOR`
* When a user selects an approved microplan:
  * The system checks whether the user has the required role.
  * If the role is missing:
    * Access is denied.
    * A clear error message is shown to the user.
  * If the role is present:
    * The user can proceed to create a campaign from the microplan.

### Step 2: Create Campaign Object

**Input:** Approved microplan object

**Actions:**

1. Extract the base campaign configuration from the selected microplan.
2. Create a new campaign by cloning the base campaign object.
3. Update the cloned campaign with:
   * A unique `campaignId`
   * `createdBy` user details
   * Campaign status set to **Draft**
4. Save the newly created campaign to the backend.

### Step 3: Auto-Generate Empty Data Templates

**Trigger:** Campaign creation and boundary selection

**Actions:**

* The backend automatically generates empty templates required for campaign setup:
  * User assignment template
  * Facility data placeholders
  * Target data placeholders
* These templates act as containers to be populated with microplan data in later steps.

### Step 4: Fetch Data from Microplan APIs

**API Endpoint:** `project-factory/v1/project-type/fetch-from-microplan`

**Actions:**

1. The system calls the Microplan API to fetch:
   * User data
   * Facility data
   * Target data
2. Retrieved data is mapped to the corresponding empty templates.
3. Updated templates are saved back to the backend and linked to the campaign.

### Step 5: Poll Campaign Status

**Purpose:** Track progress of data population before moving forward.

**API Endpoint:**\
`/campaign-search`

**Parameters:** `campaignId`

**Actions:**

* The UI periodically calls the campaign search API.
* Based on campaign status:
  * **Completed**
    * Data population is finished.
    * Proceed to the Setup Campaign page.
  * **In Progress**
    * Re-trigger Microplan data fetch if required.
    * Continue polling until completion.

<figure><img src="https://egov-digit.gitbook.io/hcm-console/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2FWNM45210WObYqnJ7UFy1%2FScreenshot%25202024-12-17%2520at%25201.23.42%25E2%2580%25AFPM.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=116de433&#x26;sv=2" alt=""><figcaption><p>fetch from microplan</p></figcaption></figure>

### Step 6: Navigate to Setup Campaign Page

**Actions:**

* Redirect the user to the **Setup Campaign** page.
* Pass campaign details using:
  * Route parameters, or
  * Application state management
* The campaign is now ready for final configuration and review.

## API Details <a href="#api-details" id="api-details"></a>

<table><thead><tr><th width="399.52734375">API Endpoint</th><th>Required Role</th></tr></thead><tbody><tr><td><code>project-factory/v1/project-type/fetch-from-microplan</code></td><td>MICROPLAN_CAMPAIGN_INTEGRATOR</td></tr><tr><td><code>project-factory/v1/project-type/search</code></td><td>CAMPAIGN_MANAGER</td></tr><tr><td><code>project-factory/v1/project-type/create</code></td><td>CAMPAIGN_MANAGER</td></tr><tr><td><code>project-factory/v1/project-type/update</code></td><td>CAMPAIGN_MANAGER</td></tr><tr><td><code>project-factory/v1/data/_download</code></td><td>CAMPAIGN_MANAGER</td></tr></tbody></table>
