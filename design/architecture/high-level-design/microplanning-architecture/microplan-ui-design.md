# Microplan - UI Design

<details>

<summary><strong>System Administrator Flow</strong></summary>

The **System Administrator** is responsible for setting up the entire microplanning platform, which includes defining campaign boundaries, configuring facilities, and assigning roles. This user operates at the national or country level and ensures all configurations align with campaign objectives.

#### Step 1: Configure Campaign

**Who:** System Administrator / Program Manager\
**Purpose:** Set up basic campaign details

**What the user does:**

* Select the **Disease** (e.g., Malaria)
* Choose the **Campaign Type** (e.g., Bednets, SMC)
* Select the **Distribution Strategy**:
  * Fixed Post
  * House-to-House
  * Both
* Click **Next** to continue or **Back** to revise

**Rules:**

* All fields are mandatory

#### Step 2: Name the Microplan

**Who:** System Administrator / Program Manager\
**Purpose:** Create a unique microplan name

**What the user does:**

* View the **auto-generated name**\
  &#xNAN;_(Format: Country–Disease–CampaignType–MMYY)_
* Edit the name if required

**Rules:**

* Name must be unique
* Minimum 3 characters
* Allowed characters: letters, numbers, `_ ( )`
* No special characters

#### Step 3: Select Campaign Boundaries

**Who:** System Administrator / Program Manager\
**Purpose:** Define where the campaign will run

**What the user does:**

* Select administrative areas (e.g., Country, State, District, Village)
* Use **multi-select dropdowns** to choose multiple locations

**Rules:**

* All required boundary levels must be selected

#### Step 4: Upload Population Data

**Who:** System Administrator / Program Manager\
**Purpose:** Provide population data for estimation

**What the user does:**

* Download the **population data template**
* Fill in the required details:
  * Total population
  * Target population
  * Village/location coordinates
* Upload the completed file

**Rules:**

* Population values must be whole numbers
* Total population must be greater than zero
* All mandatory columns must be filled

#### Step 5: Upload Facility Data

**Who:** System Administrator / Program Manager\
**Purpose:** Register facilities for campaign operations

**What the user does:**

* Download the **facility template**
* Enter facility details:
  * Facility name
  * Type
  * Capacity
  * Location details
* Upload the completed file

**Rules:**

* Facility name, type, and capacity are mandatory
* Data must pass validation before proceeding

#### Step 6: Configure Microplan Assumptions

**Who:** System Administrator / Program Manager\
**Purpose:** Set parameters used for resource calculation

**What the user does:**

* Define assumptions such as:
  * Population density
  * Distribution strategy parameters

**Rules:**

* All inputs must be numeric

#### Step 7: Configure Access & Roles

**Who:** System Administrator\
**Purpose:** Control who can view, edit, and approve the microplan

**What the user does:**

* Create or assign roles (e.g., Data Collector, Approver)
* Assign users to roles
* Define geographic and functional access levels

**Rules:**

* Users can only access data within their assigned boundaries

### Web Sequence Diagrams

<figure><img src="../../../../.gitbook/assets/image (82).png" alt=""><figcaption><p><em>System Admin Flow</em></p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (83).png" alt=""><figcaption><p><em>Employee Tagging Flow</em></p></figcaption></figure>

</details>

<details>

<summary><strong>Data Approver Flow</strong></summary>

The **Data Approver** is responsible for validating population data collected by data collectors. The role primarily ensures that population data used for microplan resource estimation is accurate and consistent with predefined rules. Data approvers play a crucial role in identifying discrepancies and ensuring the validity of population numbers before final approval.

**Responsibilities:**

* Validate population data collected from the field.
* Identify discrepancies in population estimates.
* Approve or flag data for further review and corrections.

> Note : In the current version we are not including data collectors. Population data uploaded in the system admin flow will be sent for approval

### Steps

#### Step 1: Sign In & View Pending Data

**Who:** Data Approver\
**Purpose:** Access population data awaiting approval

**What happens:**

* The Data Approver logs into the microplanning platform
* The dashboard displays **all pending population datasets** by location

#### Step 2: Review Population Data

**Who:** Data Approver\
**Purpose:** Verify submitted population data

**What happens:**

* Navigate to the **Population Data Review** section
* View data grouped by administrative level (village, district, etc.)
* Review key fields:
  * Total population
  * Target population (e.g., age groups for SMC)
  * Latitude and longitude (if available)
* Compare values with:
  * Previously approved data
  * Other reference or baseline data (if available)

#### Step 3: Check for Discrepancies

**Who:** Data Approver\
**Purpose:** Identify inaccurate or unusual values

**What happens:**

* Manually review records or rely on system flags
* The system highlights **large deviations** from earlier data (e.g., sudden population spikes)

#### Step 4: Correct or Request Fixes

**Who:** Data Approver\
**Purpose:** Resolve issues before approval

**What happens:**

* For flagged records, the Data Approver can:
  * **Request corrections** from the Data Collector, or
  * **Edit the data directly** (if permitted)
* Possible corrections include:
  * Updating total or target population values
  * Fixing missing or incorrect location details

#### Step 5: Approve Population Data

**Who:** Data Approver\
**Purpose:** Finalise population data for use

**What happens:**

* Approve data **individually or in bulk**
* Approved data is **locked** and becomes available for:
  * Microplan creation
  * Resource estimation

#### Step 6: Monitor Updates

**Who:** Data Approver\
**Purpose:** Maintain data accuracy over time

**What happens:**

* The system notifies the approver of:
  * New submissions
  * Updates to previously approved data
* Any changes can be reviewed and re-approved as needed
* All actions are **audited and tracked**

### Web Sequence Diagrams <a href="#web-sequence-diagrams" id="web-sequence-diagrams"></a>

<figure><img src="../../../../.gitbook/assets/image (84).png" alt=""><figcaption><p><em>Population Data approver flow</em></p></figcaption></figure>

</details>

<details>

<summary><strong>Facility Catchment Mapping Flow</strong></summary>

The **Facility Catchment Mapper** is responsible for mapping health facilities to their respective geographic catchment areas (e.g., villages, districts) using data provided via an API. This mapping ensures that each facility is associated with a specific community, enabling efficient distribution of resources during health campaigns.

#### **Responsibilities** <a href="#responsibilities" id="responsibilities"></a>

* Assign health facilities to geographic catchment areas (e.g., villages, localities).
* Ensure each village or locality is mapped to an appropriate facility.
* Review and update facility assignments when necessary based on campaign requirements.

**Workflow for Facility Catchment Flow**

Below are the detailed steps for the facility catchment mapping process.

**Step 1: Log in to the Platform**

* **Actor**: Facility Catchment Mapper
* **Objective**: Access the facility catchment management dashboard.
* **Process**: The Facility Catchment Mapper logs into the microplanning platform using their credentials and navigates to the facility catchment module.
* **Outcome**: The system displays a list of available campaigns and their linked facilities retrieved from the API.

**Step 2: View Facility Data via Plan Facility**

* **Actor**: Facility Catchment Mapper
* **Objective**: Access the list of facilities linked to the microplan, pulled from the Plan Facility.
* **Process**:
  * The system retrieves the list of facilities linked to the current campaign and displays them in the catchment mapping dashboard.
  * The data from the Plan Facility includes key attributes such as:
    * Facility Name
    * Facility Type (e.g., clinic, hospital)
    * Capacity (e.g., beds, vaccine storage)
    * Facility Status (active/inactive)
    * Facility Location (latitude and longitude)
* **Outcome**: The Facility Catchment Mapper can view all the facilities available for mapping in real time.

**Step 3: Assign Facilities to Catchment Areas**

* **Outcome**: Each facility is successfully assigned to its respective catchment area, ensuring proper resource allocation during campaign execution.
* **Process**:
  * **Catchment Area Mapping**:
    * Each facility is mapped to a specific administrative boundary (village, district, etc.).
    * Facility location (latitude and longitude) is used to cross-reference and ensure the correct geographic catchment area is assigned.
  * **Mapping Considerations**:
    * Ensure each catchment area is assigned to the most appropriate or nearest facility based on geographic proximity.
    * Avoid conflicts where multiple facilities are mapped to the same geographic area, unless required by the campaign.
* **Objective**: Map each facility to a corresponding catchment area (e.g., village, district).
* **Actor**: Facility Catchment Mapper

**Step 4: Validate Catchment Area Assignments**

* **Outcome**: The mapping is validated, and all errors are corrected before approval.
* **Process**:
  * The system highlights any potential mapping errors or overlaps, such as:
    * Unmapped villages or localities.
    * Facilities are assigned to incorrect or multiple areas.
  * The Facility Catchment Mapper reviews and resolves these issues before finalising the assignments.
  * Validation checks include:
    * Ensure each village or locality is mapped to exactly one facility.
    * Verify that all mandatory fields (facility name, type, status, location) are populated.
* **Objective**: Ensure the accuracy and validity of facility assignments to catchment areas.
* **Actor**: Facility Catchment Mapper

**Step 5: Approve and Save Facility Catchment Mapping**

* **Actor**: Facility Catchment Mapper
* **Objective**: Finalise and approve the facility catchment mapping.
* **Process**:
  * Once all assignments are validated, the mapper approves the mappings.
  * The system saves the approved mappings, and the data is made available for use in microplan resource estimation and campaign execution.
* **Outcome**: Facility catchment mapping is finalised and stored in the system, ensuring proper facility allocation for the upcoming health campaign.

**Key Considerations for Facility Catchment Mapping**

* **Handling Missing Facilities**:
  * If a catchment area does not have a mapped facility, it must be flagged for review and resolution before the campaign begins.
* **Avoiding Overlap**:
  * Each catchment area (village, locality, etc.) should be mapped to only one facility unless otherwise required by the campaign's objectives.
* **Geographical Accuracy**:
  * Facilities must be assigned to the correct administrative boundaries based on their geographic coordinates.

### Web Sequence Diagrams

_Listing Available Facilities_

![](<../../../../.gitbook/assets/image (85).png>)

_Tagging Facility to catchment areas_

![](<../../../../.gitbook/assets/image (86).png>)

</details>

<details>

<summary><strong>Microplan Estimation Approval Flow</strong></summary>

The **Microplan Estimation Approver** plays a critical role in ensuring the accuracy and approval of resource estimation for health campaigns. This user is responsible for reviewing the resource estimations generated by the system, validating assumptions, and approving or rejecting the final microplan estimations. The goal is to ensure that the estimated resources (e.g., vaccines, bednets, medical personnel) align with the campaign's actual needs, based on validated population and facility data.

#### **Responsibilities**

* Review and validate resource estimation formulas.
* Approve or reject microplan resource estimations.
* Adjust the estimation parameters and assumptions as needed.
* Ensure that the approved resource estimation aligns with the campaign's needs.

### **Steps**

**Workflow for Microplan Estimation Approver Flow**

This section details the steps in the microplan estimation approval process.

**Step 1: Log in to the Platform**

* **Actor**: Microplan Estimation Approver
* **Objective**: Access the microplan estimation dashboard.
* **Process**: The microplan Estimation Approver logs into the platform using their credentials, granting access to the estimation review and approval module.
* **Outcome**: The system displays a list of microplans that require review, with detailed estimations ready for approval.

**Step 2: Review Resource Estimation**

* **Actor**: Microplan Estimation Approver
* **Objective**: Review the resource estimations generated by the system for the current campaign.
* **Process**:
  * The system presents the resource estimation calculations based on the uploaded population and facility data.
  * The estimations are divided into key resources such as:
    * **Vaccines**: Estimated based on population size and target population.
    * **Bednets**: Calculated for campaigns like malaria prevention.
    * **Personnel**: Estimated based on the required workforce for each facility and catchment area.
* **Outcome**: The microplan estimation approver has a comprehensive overview of the resources estimated for the campaign, with breakdowns by resource type.

**Step 3: Review and Validate Assumptions**

* **Actor**: Microplan Estimation Approver
* **Objective**: Ensure that the assumptions used for resource estimations are accurate and reasonable.
* **Process**:
  * The system displays key assumptions that drive the resource estimation formulas, such as:
    * **Target Population**: Number of people eligible for the intervention (e.g., children aged 3-11 months for SMC campaigns).
    * **Resource Allocation**: Number of resources (e.g., bednets, vaccines) per person or household.
    * **Distribution Strategy**: House-to-house, fixed post, or a combination of both.
  * The approver cross-checks these assumptions with known data and campaign requirements.
  * If any assumptions seem inaccurate or unreasonable, the Microplan Estimation Approver can modify assumptions for a list of specific boundaries
* **Outcome**: The assumptions used for resource estimation are validated, and any necessary corrections are made.

**Step 4: Approve or Reject the Microplan Estimation**

* **Actor**: Microplan Estimation Approver
* **Objective**: Make the final decision to approve or reject the resource estimation for the campaign.
* **Process**:
  * After reviewing the resource estimation, the Microplan Estimation Approver selects **Approve** or **Reject**.
    * **Approve**: Confirms that the estimation is valid and the required resources are accurately calculated. Once approved, the estimation becomes final and is locked for campaign execution.
    * **Reject**: If the estimation is inaccurate, the approver provides feedback and requests a re-evaluation of the data or assumptions.
  * The system prompts the approver to provide reasons for rejection, which are communicated to the appropriate team for corrections.
* **Outcome**: Once approved, the resource estimation is finalised, and the required resources are allocated for the campaign. If rejected, the estimation returns to the appropriate team for review and modification.

### Web Sequence Diagram

<figure><img src="../../../../.gitbook/assets/image (87).png" alt=""><figcaption><p><em>Microplan Estimations approval</em> </p></figcaption></figure>

</details>

