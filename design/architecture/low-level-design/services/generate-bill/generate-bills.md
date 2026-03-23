# Generate Bills

## **Overview**

This screen allows Campaign Supervisors to:

1. Filter attendance registers based on boundaries (Country, Province, and District) tied to the selected project and aggregation level.
2. View the list of registers within the selected boundary.
3. Generate bills for the selected boundary if all registers are approved.

***

## Interface Elements

<figure><img src="../../../../../.gitbook/assets/image (177).png" alt=""><figcaption></figcaption></figure>

**Filters Section**

no of levels will vary based on the aggregation level selection:

* **Country**:\
  Dropdown menu to select the country (e.g., _Mbazi Highlands_).
  * **Mandatory Field**: Must be selected before applying filters.
* **Province**:\
  Dropdown menu to select the province (e.g., _Nampula_).
  * **Mandatory Field**: Must be selected before applying filters.
* **District**:\
  Dropdown menu to select the district (e.g., _Murrupula_).
  * **Mandatory Field**: Must be selected before applying filters.
* **Apply Button**:\
  Triggers the filter to display attendance registers for the selected boundary.

***

**Register Inbox**

* **Project Name**:\
  Displays the selected project name.
* **Aggregation Level**:\
  Displays the selected aggregation level (e.g., _District level_).
* **Register Status Summary**:
  * **Approved Registers**: Shows the count of approved registers (e.g., _18_).
  * **Pending Registers**: Shows the count of pending registers (e.g., _0_).

**Registers Table**

Displays a tabular list of attendance registers for the filtered boundary, with the following columns:

<table><thead><tr><th width="249">Element</th><th>Description</th></tr></thead><tbody><tr><td><strong>Register ID</strong></td><td>Unique identifier for each attendance register</td></tr><tr><td><strong>Boundary</strong></td><td>Indicates the boundary associated with the register</td></tr><tr><td><strong>Supervisor Name</strong></td><td>Displays the name of the supervisor associated with the register </td></tr><tr><td><strong>Number of Workers</strong></td><td>Displays the total number of workers in the register</td></tr></tbody></table>

***

**Action Section**

* **Generate Bill Button**:
  * **Enabled State**: If all registers are approved, this button becomes active, allowing users to trigger the bill generation process and the bill is not already generated.
  * **Disabled State**: If any registers are pending approval, the button remains inactive.

***

**User Actions Flow:**

1. Filter Attendance Registers:
   * Mandatory Filters: The user must select a Country, Province, and District before clicking "Apply".
   * After clicking Apply, the attendance registers for the selected boundary are displayed.
2. View Attendance Registers:
   * The filtered registers are shown in a tabular format.
3. Generate Bill:
   * The Generate Bill button is enabled only if all the registers within the selected boundary are approved and the bill has not been generated already.
   * Clicking Generate Bill triggers the bill generation process:
     * A confirmation pop-up appears with the warning.
     * Buttons:
       * Cancel: Returns to the register list.
       * Proceed: Starts the bill generation process.
   * A toast message will be shown whether the bill generation started or failed. And an info message will be displayed with the same.

<figure><img src="../../../../../.gitbook/assets/image (178).png" alt=""><figcaption></figcaption></figure>

***

#### Scenarios and System Responses:

1. If all registers within the selected boundary are approved:
   * The Generate Bill button is enabled.
   * Upon clicking Generate Bill, an info message is displayed:\
     "Bill generation in progress. Please wait."
2. Bill Already Generated:
   * If all registers within the selected boundary are approved, but a bill has already been generated:
   * An info message is displayed:\
     "Bill has already been generated for this boundary."
3. Pending Registers:
   * If some registers within the selected boundary are still pending approval:
   * An info message is displayed:\
     "Bill cannot be generated until all the registers are approved."

***

### Validations

1. Boundary Selection:
   * All three boundary levels (Country, Province, and District) are mandatory for filtering attendance registers.
   * Error toast message if you click on apply without selecting all mandatory boundaries.
2. The system verifies the approval status of all registers in the selected boundary before enabling the **Generate Bill** button.

***

## API Endpoints

<table><thead><tr><th width="358.15234375">EndPoint</th><th>Purpose</th></tr></thead><tbody><tr><td><code>/health-attendance/v1/_search</code></td><td>Retrieve attendance registers by boundary</td></tr><tr><td><code>/health-expense/bill/v1/_search</code></td><td>Checks if bill is already generated or not</td></tr><tr><td><code>/health-expense-calculator/v1/_calculate</code></td><td>Trigger bill generation for selected boundary</td></tr></tbody></table>
