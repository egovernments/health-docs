# User Tagging

## Overview

The **User Tagging** screen allows the Microplan Admin to assign registered users to specific roles for the microplan being configured. These users will be responsible for approvals, data validation, and operational tasks.

User assignments are restricted to:

* Users uploaded through **User Management (Bulk Upload)**
* Jurisdictions selected during the **Boundary Selection** step

## Steps

### Step 1: Understand Available Roles

Each microplan includes the following configurable roles:

* National Microplan Estimation Approver
* National Facility Catchment Assigner
* National Population Data Approver
* Microplan Estimation Approver
* Facility Catchment Assigner
* Population Data Approver

Each role has:

* Its own assignment screen
* Its own user list
* Jurisdiction-specific tagging rules

> **Important:** Assigning users to **national-level roles is mandatory**.

<figure><img src="../../../../../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>

### Step 2: Open the Role Assignment Screen

1. Navigate to the **Assign** button for the applicable role in the **User Access Management** screen. For example, click on the _Assign National Microplan Estimation Approver button._

<figure><img src="../../../../../.gitbook/assets/image (139).png" alt=""><figcaption></figcaption></figure>

A pop-up window opens where you can assign or unassign users.

### Step 3: Search for Available Users

The system automatically:

* Fetches users registered under the selected role.
* Filters users based on:
  * Role
  * Selected jurisdiction boundaries

#### How Search Works (System Behaviour)

* The search request is made via `/health-hrms/employees/_search`, using roles as query parameters (e.g., `roles: ROOT_PLAN_ESTIMATION_APPROVER`). This returns all registered users with the specified role.
* When the page loads, a request to `/plan-service/employee/_search` retrieves all users currently assigned to the current microplan.

### Step 4: Assign a User

To assign a user to the microplan:

1. Locate the user from the available list.
2. Click **Assign**.

#### What Happens in the Background

* Upon clicking the assign button, the `userServiceUuid` from the search response (/health-hrms/employees/\_search) is used as the payload, along with the jurisdiction and role. For the National Microplan Estimation Approver role, the jurisdiction is pre-selected as the national level by default.
* For other roles, the jurisdiction is automatically pre-selected based on the boundaries set in the Boundary Selection screen. This information is then sent to /plan-service/employee/\_create to assign the user to the current microplan.

#### Jurisdiction Rules

* **National roles:**\
  Jurisdiction is automatically set to the **national level**.
* **Other roles:**\
  Jurisdiction is automatically derived from the boundaries selected in the **Boundary Selection** step.

Once saved, the user becomes officially assigned to the microplan.

### Step 5: Unassign a User

To remove a user from the microplan:

1. Click **Unassign** next to the assigned user.
2. Confirm the action.

#### What Happens in the Background

Clicking the unassign button sets the `active` attribute of `PlanEmployeeAssignment` to `false` via `/plan-service/employee/_create`, updating the microplan accordingly.

### Step 6: Repeat for Other Roles

The process is identical for all roles:

1. Open the role screen.
2. Search available users.
3. Assign or unassign as required.
4. Ensure jurisdiction alignment.
5. Save changes.

## API Details

<table><thead><tr><th width="354.265625">URL</th><th>Role</th></tr></thead><tbody><tr><td>/plan-service/employee/_search</td><td>MICROPLAN_ADMIN</td></tr><tr><td>/health-hrms/employees/_search</td><td>MICROPLAN_ADMIN</td></tr><tr><td>/plan-service/employee/_create </td><td>MICROPLAN_ADMIN</td></tr></tbody></table>
