# Validate & Approve Population Data

## **Overview**

The Population Data Validation and Approval screen is designed for population data approvers to ensure the accuracy and consistency of population data submitted for villages. This screen allows approvers to validate, correct, and approve data, ensuring the integrity of the data used for resource planning.

## **User Roles**

<table><thead><tr><th width="136.45703125">Roles</th><th width="371.05859375">Description</th><th>Role Code</th></tr></thead><tbody><tr><td><strong>Population Data Approver</strong></td><td>Responsible for validating the population data, ensuring its accuracy, including the ability to edit data, approve, or send data back for correction.</td><td><code>POPULATION_DATA_APPROVER</code></td></tr><tr><td><strong>Root Population Data Approver</strong></td><td>Responsible for validating the population data, ensuring its accuracy, including the ability to edit data, approve, or send data back for correction.Has additional permissions, including the ability to finalize population data.</td><td><code>ROOT_POPULATION_DATA_APPROVER</code></td></tr></tbody></table>

## **Interface Elements**

<figure><img src="../../../../../.gitbook/assets/image (464).png" alt=""><figcaption></figcaption></figure>

**Header Section**

* **Microplan Name:**\
  Displays the name of the current microplan being reviewed.
* **Logged-in User:**\
  Indicates the user role and account.

#### **Population Data Summary (KPIs)**

* All values are dynamically updated based on the real-time census data.
* These values are sourced directly from microplan-specific KPIs, which reflect any actions taken by data approvers.
* As census data is reviewed, corrected, or approved, the values will change accordingly.

**Filters and Search**

* **Administrative Hierarchy and Area Selection:**\
  Dropdown menus for selecting specific administrative areas (e.g., district and village).
* **Search and Filter Options:**
  * **Workflow Status Filters:**
    * _Pending validation_
    * _Pending approval_&#x20;
    * _Validated_&#x20;
  * **Assigned to Filters:**
    * _Assigned to me_&#x20;
    * _Assigned to all_&#x20;
  * Buttons: **Apply Filter**, **Clear**

**Population Data Table**

<table><thead><tr><th width="267.56640625">Column</th><th>Description</th></tr></thead><tbody><tr><td>Village Name</td><td>Name of the village under review</td></tr><tr><td>Uploaded Target Population</td><td>Target population submitted for the village</td></tr><tr><td>Confirmed Target Population</td><td>Approved target population for the village</td></tr><tr><td>Uploaded Total Population</td><td>Total population submitted for the village</td></tr><tr><td>Confirmed Total Population</td><td>Approved total population for the village</td></tr><tr><td>Action Buttons</td><td>Includes <strong>View Logs</strong> for historical data and other validation actions</td></tr></tbody></table>

**Action Buttons**

* **View Logs:** Displays historical changes and logs related to a specific village's data

<figure><img src="../../../../../.gitbook/assets/image (465).png" alt=""><figcaption></figcaption></figure>

***

## **Population Data Validation Workflow**

#### **4.1. Role-Based Permissions and Actions**

**Population Data Approver (PDA)**

The Population Data Approver is responsible for validating population and editing data. Their responsibilities include:

**Validating Data:**

* Cross-check the uploaded data with the confirmed population to ensure accuracy.

<figure><img src="../../../../../.gitbook/assets/image (466).png" alt=""><figcaption></figcaption></figure>

**Editing Data:**

* Modify the village population data if discrepancies are found, with a reason logged for each change and the data is sent back for approval.

**When No Data Is Assigned:**

* If no data is assigned to the PDA, a "Back" button is shown, allowing them to return to the previous screen.

***

**Root Population Data Approver (RPDA)**

The Root Population Data Approver has all the functionalities of a PDA and additional capabilities to finalise population data. Their responsibilities include:

**Editing Data:**

* Modify the village population data if discrepancies are found, with a reason logged for each change.

<figure><img src="../../../../../.gitbook/assets/image (467).png" alt=""><figcaption></figcaption></figure>

**Approving or Sending Data for Correction:**

* Once the population data is validated, the RPDA can either approve it or send it back for correction if further issues are identified.

**Approval Workflow:**

* If someone from the hierarchy below modifies and sends the data for approval, the RPDA can approve it. For example, if a province-level user sends the data back for approval, the RPDA will receive the application for approval and validation.

**Finalising Actions:**

* If all the villages within the selected microplan have been validated and no further changes are required, the RPDA will see a "Finalise Actions" button at the footer of the page.
* The "Finalise Actions" button will lock the data and prevent further modifications once clicked, marking the end of the validation process for the selected microplan population data.

<figure><img src="../../../../../.gitbook/assets/image (468).png" alt=""><figcaption></figcaption></figure>

* After finalising the population data, a success screen will be shown, indicating that the population data is finalised.

<figure><img src="../../../../../.gitbook/assets/image (469).png" alt=""><figcaption></figcaption></figure>

***

**Additional Notes**

* Once the population data reaches the national-level data approver and the validation is finalised, the system will disable all action buttons. The status will be set to "CENSUS\_APPROVED", and no further changes can be made. At this point, users can only view the details of the data but will not be able to perform any additional actions, such as editing or approving the data.
* Population supervisors will only see the boundaries in their inbox that fall under their jurisdiction.

## API End Points

<table><thead><tr><th width="133">Purpose</th><th width="144">Endpoint URL</th><th width="90">Method</th><th>Payload</th></tr></thead><tbody><tr><td>Get chart data for a specific visualization</td><td><code>dashboard-analytics/dashboard/getChartV2</code></td><td>POST</td><td><code>{ "aggregationRequestDto": { "visualizationType": "METRIC", "visualizationCode": "censusUploadedTargetPopulation", "filters": { "COUNTRY": ["MICROPLAN_MO"], "status": ["PENDING_FOR_VALIDATION"], "planConfigurationId": ["246cfc95-b4b0-43e8-b375-dd44333cc881"], "tenantId": ["mz"] }, "moduleLevel": "CENSUS" }, "headers": { "tenantId": "mz" } }</code></td></tr><tr><td>Search census data</td><td><code>census-service/_search</code></td><td>POST</td><td><code>{ "CensusSearchCriteria": { "tenantId": "mz", "source": "246cfc95-b4b0-43e8-b375-dd44333cc881", "status": "PENDING_FOR_VALIDATION", "assignee": "a7431b92-5db5-46b1-9b5b-33272ba8dbfc", "jurisdiction": ["MICROPLAN_MO"], "limit": 50, "offset": 0 } }</code></td></tr><tr><td>Search business services</td><td><code>egov-workflow-v2/egov-wf/businessservice/_search</code></td><td>POST</td><td><p><code>SearchParams{</code></p><p><code>tenantId=mz,</code></p><p><code>businessServices=CENSUS</code></p><p><code>}</code></p></td></tr><tr><td>Search plan employees</td><td><code>plan-service/employee/_search</code></td><td>POST</td><td><code>{ "PlanEmployeeAssignmentSearchCriteria": { "tenantId": "mz", "active": true, "planConfigurationId": "246cfc95-b4b0-43e8-b375-dd44333cc881", "role": ["POPULATION_DATA_APPROVER", "ROOT_POPULATION_DATA_APPROVER"], "employeeId": ["a7431b92-5db5-46b1-9b5b-33272ba8dbfc"], "limit": 5, "offset": 0 } }</code></td></tr><tr><td>Search project type by campaign ID</td><td><code>project-factory/v1/project-type/search</code></td><td>POST</td><td><code>{ "CampaignDetails": { "tenantId": "mz", "ids": ["5b5a49ca-584c-4226-bbd6-98cddd95ef78"] } }</code></td></tr><tr><td>Search plan configuration details</td><td><code>plan-service/config/_search</code></td><td>POST</td><td><code>{ "PlanConfigurationSearchCriteria": { "tenantId": "mz", "id": "246cfc95-b4b0-43e8-b375-dd44333cc881" } }</code></td></tr></tbody></table>
