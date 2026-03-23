# User Management

## Overview

The **User Management** screen allows the **Microplan Admin** to manage and review users assigned to microplan-related roles (such as Population Data Approver and other campaign roles).

Only roles relevant to the microplan are displayed on this screen.

## **Steps** <a href="#path" id="path"></a>

### Step 1: Access the User Management Screen

1. Log in as **MICROPLAN\_ADMIN**.
2. Navigate to the **Setup Microplan** card.
3. Click on the **User Management** link.

You will be redirected to the User Management dashboard.

<figure><img src="../../../../../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>

### Step 2: View Registered Users

On loading the page:

* All users uploaded through **Bulk User Upload** are displayed.
* By default, users from **all microplan-related roles** are shown.
* The displayed roles are configured in MDMS under:
  * `hcm-microplanning.rolesformicroplan`

The system retrieves users using the employee search API - `/health-hrms/employees/_search`

### Step 3: Search for Users

To find a specific user:

1. Use the **Search** bar.
2. Enter:
   * Name, or
   * Contact Number
3. Partial matching is supported (you do not need the full name or number).

The system refreshes the table with matching results.

### Step 4: Filter Users by Role

To filter users based on role:

1. Use the **role checkboxes** on the left panel.
2. Select one or more roles.
3. The table updates to display only users assigned to those selected roles.

#### How Filtering Works (System Behaviour)

* Roles are dynamically fetched from MDMS.
* When checkboxes are selected:
  * The selected roles are passed as query parameters.
  * The employee search API returns only users matching those roles.

If no filter is selected, all roles are displayed by default.

### Step 5: View Employee Details

To see detailed information about a user:

1. Click on the user’s row in the table.
2. The system redirects to the employee details page.
3. You can review:
   * Role
   * Contact details
   * Assigned jurisdiction
   * Other profile information

### Step 6: Bulk Upload Users

To create multiple users at once:

1. Click the **Bulk Upload Users** link.
2. Download the user template.
3. Fill in required details (role, contact info, jurisdiction, etc.).
4. Upload the completed file.

This creates multiple users for various microplan roles in a single action.

### Step 7: Download User Data

To review or export user information:

1. Click **Download Users' Data**.
2. Download:
   * User templates
   * Existing employee records
   * Credentials created through bulk upload (if applicable)

This helps with auditing or verification.

Click on the link below to access the configuration files for roles for microplan&#x20;

{% embed url="https://github.com/egovernments/releasekit/blob/5a32e825df702d996d834a9986b3722c422db972/mdms/HCM/HCM%20Microplanning%20v0.1/JSON%20Data/Common%20UI%20Config/rolesForMicroplan.json#L4" %}

