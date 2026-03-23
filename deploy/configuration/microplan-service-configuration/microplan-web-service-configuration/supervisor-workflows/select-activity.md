# Select Activity

## **Overview**

The Select Activity screen helps supervisors manage and track microplans. It shows role-based activity cards that guide them through tasks like validating population data, assigning facilities, and approving estimations. The activities displayed depend on the user’s role (Root or Normal) and the current microplan status, so supervisors only see actions relevant to their responsibilities at each stage.

## **Interface Elements**

**Microplan Name Display:**

A prominently displayed label at the top of the interface that shows the name of the selected microplan.

**Activity Options:**

Displays a list of activities as clickable items. Selecting an activity navigates the user to the corresponding detailed workflow.

<figure><img src="../../../../../.gitbook/assets/image (463).png" alt=""><figcaption></figcaption></figure>

## Available Activities

**1. Validate & Approve Population Data**

* **Purpose**:\
  Ensures the population data associated with the microplan is accurate and approved for further processing.
* **Steps**:
  * Review uploaded population data for completeness and correctness.
  * Approve or flag data for revision as needed.
* **Roles Involved**:
  * ROOT\_POPULATION\_DATA\_APPROVER: Can review, approve, or send back population data, as well as finalised population data.
  * POPULATION\_DATA\_APPROVER: Can review, approve, or send back population data.
* **Role-Based Access**:
  * This card is visible based on the user role and the `wfStatus` that aligns with the data validation stage.

**2. Assign Facilities to Villages**

* **Purpose**:\
  Assign healthcare or distribution facilities to specific villages or areas within the campaign's scope.
* **Steps**:
  * Map villages to designated facilities.
  * Confirm assignments to ensure logistical accuracy.
* **Roles Involved**:
  * ROOT\_FACILITY\_CATCHMENT\_MAPPER: Assign and unassign facilities to villages, and finalise facility assignments.
  * FACILITY\_CATCHMENT\_MAPPER: Assign and unassign facility to villages.
* **Role-Based Access**:
  * This card appears only when the `wfStatus` indicates that facility assignment is the next step.

**3. Validate & Approve Microplan Estimations**

* **Purpose**:\
  Review and finalise the estimated resources, population coverage, and other metrics calculated for the microplan.
* **Steps**:
  * Check estimations for accuracy and alignment with campaign objectives.
  * Approve or request adjustments as necessary.
* **Roles Involved**:
  * ROOT\_PLAN\_ESTIMATION\_APPROVER: Can approve or request adjustments for microplan estimations, also finalized microplan estimation.
  * PLAN\_ESTIMATION\_APPROVER: Can approve or request adjustments for microplan estimations.
* **Role-Based Access**:
  * The card is displayed based on `wfStatus` of the plan configuration, indicating readiness for estimation validation.

## **User Actions Flow**

1. **Select an Activity:**\
   Choose one of the available activities depending on the current stage of the microplan.
2. **Proceed to the Next Screen:**\
   Click the activity to access its detailed workflow interface.

### **Notes**

* **Role-based Permissions:** Certain activities might be restricted based on user roles and permissions.
* **Sequential Workflow:** Activities must be completed in sequence for effective campaign execution:
  1. Validate Population Data
  2. Assign Facilities
  3. Approve Microplan Estimations
* **Progress Tracking:** Ensure tasks are not repeated and assignments remain aligned with campaign objectives.

## **API Endpoints**

<table><thead><tr><th width="164.6171875">End Points</th><th width="191.10546875">Purpose</th><th>Role</th></tr></thead><tbody><tr><td><code>/egov-workflow-v2/egov-wf/process/_search</code></td><td>Search process history for this plan</td><td>ROOT_POPULATION_DATA_APPROVER, <br>POPULATION_DATA_APPROVER,<br>ROOT_PLAN_ESTIMATION_APPROVER,<br>PLAN_ESTIMATION_APPROVER,<br>ROOT_FACILITY_CATCHMENT_MAPPER,<br>FACILITY_CATCHMENT_MAPPER,<br>MICROPLAN_VIEWER</td></tr><tr><td><code>/egov-workflow-v2/egov-wf/businessservice/_search</code></td><td>Search workflow business services by tenant ID and plan</td><td>ROOT_POPULATION_DATA_APPROVER, <br>POPULATION_DATA_APPROVER,<br>ROOT_PLAN_ESTIMATION_APPROVER,<br>PLAN_ESTIMATION_APPROVER,<br>ROOT_FACILITY_CATCHMENT_MAPPER,<br>FACILITY_CATCHMENT_MAPPER,<br>MICROPLAN_VIEWER</td></tr><tr><td><code>/plan-service/config/_search</code></td><td>Retrieve plan configuration details by configuration ID</td><td>SUPERUSER,<br>MICROPLAN_ADMIN,<br>MICROPLAN_CAMPAIGN_INTEGRATOR,<br>ROOT_POPULATION_DATA_APPROVER, <br>POPULATION_DATA_APPROVER, <br>ROOT_PLAN_ESTIMATION_APPROVER,<br>PLAN_ESTIMATION_APPROVER,<br>ROOT_FACILITY_CATCHMENT_MAPPER,<br>FACILITY_CATCHMENT_MAPPER,<br>MICROPLAN_VIEWER</td></tr></tbody></table>
