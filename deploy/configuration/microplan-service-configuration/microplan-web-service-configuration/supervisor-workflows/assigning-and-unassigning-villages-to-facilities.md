# Assigning & Unassigning Villages To Facilities

## **Overview**

When the user clicks on a facility, this pop-up window opens, displaying essential details about the selected facility, as well as options for managing unassigned and assigned villages for this facility.

## Interface Elements

<figure><img src="../../../../../.gitbook/assets/image (476).png" alt=""><figcaption></figcaption></figure>

**Facility Details Card**

Upon selecting a facility, a **Facility Details** pop-up displays the following:

* **Facility Name:** Name of the selected facility.
* **Facility Type:** Type of facility, such as "Warehouse" or "Health Post."
* **Facility Status:** Indicates whether the facility is temporary or permanent.
* **Capacity:** Displays the capacity of the facility (e.g., the number of bales for bednet distribution or blisters for SMC campaigns).
* **Serving Population:** The serving population currently being served by the facility.
* **Fixed Post:** Indicates if the facility is a fixed post, which is typically a permanent, stationary facility.
* **Residing Village:** The village where the facility is located or based.

<table><thead><tr><th width="248.49609375">Field Name</th><th>Description</th></tr></thead><tbody><tr><td>Village Name</td><td>The name of the village (e.g., Tendeken-01, Dutorken).</td></tr><tr><td>Administrative Hierarchy</td><td>The administrative hierarchy to which the village belongs (e.g., Country, Province, District).</td></tr><tr><td>Administrative Area</td><td>The specific area within the hierarchy (e.g., Locality, Village).</td></tr><tr><td>Accessibility Level</td><td>Indicates the ease of accessing the village (e.g., View Details).</td></tr><tr><td>Security Level</td><td>The security conditions of the village (e.g., View Details).</td></tr><tr><td>Confirmed Target Population</td><td>The population size confirmed for the village.</td></tr><tr><td>Assignment Status</td><td>Indicates whether the village is currently assigned or unassigned to a facility.</td></tr><tr><td>Assigned Facility</td><td>Name of the facility to which the village is assigned (if applicable).</td></tr><tr><td>Actions</td><td>Options for assigning or unassigning a village.</td></tr></tbody></table>

**Filter Options:**

* **Select Administrative Hierarchy:** Dropdown menu for selecting an administrative level (e.g., Country, Province, District).
* **Select Administrative Area:** Dropdown menu for selecting a specific area within the hierarchy (e.g., Locality, Village).
* **Search:** Search for villages by name or code.
* **Clear:** Clears all selected filters and resets the search options.

#### **Unassigned Villages and Assigned Villages**

**Unassigned Villages**

This section allows the user to manage villages that have not yet been assigned to any facility. Users can select villages from this list and assign them to a facility.

**Assigned Villages**

This section displays the villages that have already been assigned to a facility. Users can manage these assignments, including unassigning a village if necessary.

**Actions:**

* **Assign:** To assign a facility to a village, select the village from the unassigned list and click the **"Assign"** button.
* **Unassign:** If a village is already assigned to a facility, users can unassign it by selecting the village and clicking the **"UnAssign"** button.

{% hint style="info" %}
**Notes:**

* **Unassign:** Clicking on the unassign button shows an alert message that you want to unassign this village from the current selected facility.
* **Close:** Clicking **"Close"** exits the page without making any changes.
{% endhint %}

## **API Endpoints**

<table><thead><tr><th width="127">Purpose</th><th width="120">Endpoint</th><th width="104">Method</th><th>Payload</th></tr></thead><tbody><tr><td>Search census data</td><td><code>/census-service/_search</code></td><td>POST</td><td> <code>{"CensusSearchCriteria":{"tenantId":"mz","source":"0dfe322d-727c-489f-a5a8-e8b7a0a43cc4","facilityAssigned":false,"jurisdiction":["MICROPLAN_MO"],"limit":10,"offset":0}</code></td></tr><tr><td>Update facility plan mapping data</td><td><code>/plan-service/plan/facility/_update</code></td><td>POST</td><td> <code>{"PlanFacility":{"id":"11aa5150-0c6c-42ed-adb5-775fc02bfbbb","tenantId":"mz","planConfigurationId":"0dfe322d-727c-489f-a5a8-e8b7a0a43cc4","planConfigurationName":"bednetmixed-togregish2hdis name-1733377290309-8722","boundaryAncestralPath":"MICROPLAN_MO"}</code></td></tr></tbody></table>

***
