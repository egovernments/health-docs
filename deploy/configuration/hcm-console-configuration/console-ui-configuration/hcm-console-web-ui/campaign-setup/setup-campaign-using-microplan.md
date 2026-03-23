# Setup Campaign Using Microplan

#### **Overview** <a href="#overview" id="overview"></a>

The "Setup Campaign" feature facilitates the creation of a campaign using an approved microplan. It ensures that only authorized users can initiate the setup process, generates required campaign data, and integrates with external APIs to fetch user, facility, and target data.

**. User Role Validation**

* **Role Required**: **MICROPLAN\_CAMPAIGN\_INTEGRATOR**
* **Validation Logic**:
  * Only users with the above role can select an approved microplan to initiate the campaign setup.
  * If the user lacks the role, access to the feature is denied with a proper error message.

**Campaign Object Creation**

* **Input**: Approved microplan object.
* **Steps**:
  1. Extract the base campaign object from the selected microplan.
  2. Create a new campaign object by cloning the base campaign object with the following updates:
     * Add unique identifiers (`campaignId`, `createdBy`).
     * Set the campaign status to `draft`.
  3. Save the new campaign object to the backend.

**Generate Empty Templates**

* **Trigger**: After updating the campaign object with selected boundaries, it gets auto-generated from Backend
* **Steps**:
  1. Automatically generate empty templates for the campaign, including:
     * User assignments.
     * Facility data placeholders.
     * Target data placeholders.

**Fetch Data from Microplan API**

* **API Endpoint**: project-factory/v1/project-type/fetch-from-microplan
* **Steps**:
  1. Call the Microplan API to fetch:
     * User data.
     * Facility data.
     * Target data.
  2. Populate the empty templates with the fetched data.
  3. Save the updated templates back to the backend.

**Campaign Search Polling**

* **Purpose**: Monitor the progress of data population and transition to the next step once completed.
* **Steps**:
  1. The UI triggers a periodic call to the `campaignSearch` endpoint:
     * API Endpoint: `/campaign-search`
     * Parameters: `campaignId`.
  2. Check the status of the campaign:
     * **If Completed**:
       * Navigate the user to the **Setup Campaign** page.
     * **If In Progress**:
       * Re-trigger the data fetch from Microplan API to ensure completion.
       * Continue polling.

fetch from microplan

<figure><img src="https://egov-digit.gitbook.io/hcm-console/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2FWNM45210WObYqnJ7UFy1%2FScreenshot%25202024-12-17%2520at%25201.23.42%25E2%2580%25AFPM.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=116de433&#x26;sv=2" alt=""><figcaption></figcaption></figure>

**Navigation to "Setup Campaign" Page.**

* **Steps**:
  1. Transition the user to the **Setup Campaign** page.
  2. Pass the necessary campaign data as route parameters or via state management.

#### API Details: <a href="#api-details" id="api-details"></a>

Action (Api details)Role

project-factory/v1/project-type/fetch-from-microplan

MICROPLAN\_CAMPAIGN\_INTEGRATOR

project-factory/v1/project-type/search

CAMPAIGN\_MANAGER

project-factory/v1/project-type/create

CAMPAIGN\_MANAGER

project-factory/v1/project-type/update

CAMPAIGN\_MANAGER

project-factory/v1/data/\_download

CAMPAIGN\_MANAGER
