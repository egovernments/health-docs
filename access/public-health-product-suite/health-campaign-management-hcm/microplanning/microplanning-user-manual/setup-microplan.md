---
description: Step-by-Step Guide to Set Up a Microplan - only for administrators
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/access/public-health-product-suite/health-campaign-management-hcm/microplanning/setup-microplan
---

# Setup Microplan

**Roles involved:**

* System Administrator

### Step 1: Select Language & Log In

1.  Select a preferred language:

    * English
    * Portuguese
    * French

    <figure><img src="../../../../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>
2. Click **Continue** to proceed to the login page.
3.  Enter the following details:

    * **Username**
    * **Password**
    * **City**

    <figure><img src="../../../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>
4. Click **Login**.

{% hint style="info" %}
📌 _Note:_ User accounts for system administrators are created by the implementation team. Login credentials are shared separately.
{% endhint %}

***

### Step 2: Access the Home Page

After logging in, you can access the following actions:

* **Set Up Microplan** – Create and configure a new microplan
* **Open Microplans** – View drafted or completed microplans
* **User Management** – Register and manage users and roles

<figure><img src="../../../../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

***

### Step 3: Create Users (Mandatory for First-Time Setup)

Before setting up a microplan, users with the required roles must be created.

#### 3.1 Open User Management

* Click **User Management** from the home page.
*   The dashboard displays registered users with:

    * Name
    * Email
    * Contact Number
    * Assigned Role

    <figure><img src="../../../../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

You can:

* Search users by name or contact number
* Filter users by role

***

#### 3.2 Bulk Upload Users

1. Click **Bulk Upload Users**.
2. Download the user registration Excel template.

<figure><img src="../../../../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

**Template Structure**

* **Read Me** – Instructions to fill and upload the template
* **User Roles** – List and description of available roles
*   **Role-wise Sheets** – One sheet per role with fields:

    * Name
    * Contact Number
    * Email ID

    <figure><img src="../../../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

3. Fill in user details as per the role sheets.
4. Upload the completed file.
5. Submit the file to complete user registration.

#### 3.3 Download User Credentials

After successful submission:

* Download generated user credentials

<figure><img src="../../../../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

* View:
  * Uploaded file name
  * Upload timestamp
  * Uploaded by (system admin)
  * Login credentials for each user

***

### Step 4: Start Microplan Setup

Click **Set Up Microplan**.

***

### Step 5: Capture Campaign Details

Enter the following details:

* **Disease** (default: Malaria)
* **Campaign Type** (e.g., Bednet, SMC)
*   **Resource Distribution Strategy**

    * Fixed Post
    * House-to-House
    * Fixed Post & House-to-House

    <figure><img src="../../../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
📌 Assumptions and estimation formulas are auto-configured based on selections.
{% endhint %}

Click **Save and Proceed**.

***

### Step 6: Name the Microplan

* Review selected campaign details.

<figure><img src="../../../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

* Provide a **Microplan Name**:
  * Auto-suggested format:\
    `Disease–CampaignType–DistributionStrategy–MonthYY`
  * Editable and mandatory
* Naming rules:
  * Minimum 3 characters
  * Cannot be only numeric
  * Allowed special characters: `- _ ( ) &`

Click **Save and Proceed**.

{% hint style="info" %}
⚠️ Campaign details cannot be edited after this step.
{% endhint %}

***

### Step 7: Select Campaign Boundaries

* Select administrative boundaries using hierarchical checkboxes.

<figure><img src="../../../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

* Selection must proceed top-down (country → province → district → village).
* Only pre-configured boundary data can be selected.

Click **Save and Proceed**.

***

### Step 8: Upload Population Data

Population data is uploaded at the lowest administrative level.

<figure><img src="../../../../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

#### 8.1 Download Population Template

* Click **Download Template**.
* Each campaign has a separate template.
* Structure:
  * **Read Me** tab with instructions
  * One sheet per district containing villages

#### 8.2 Populate & Upload Data

Required guidelines:

* Population values must be whole numbers
* No empty or negative values
* Latitude/Longitude must be in decimal format
* Do not modify columns, sheets, or structure

Upload the completed template and click **Save and Proceed**.

***

### Step 9: Upload Facility Data

#### 9.1 Download Facility Template

* Existing facilities (if any) are pre-filled.
* New facilities can be added.

<figure><img src="../../../../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

**Template Sheets**

* **Read Me**
* **Facility List**
* **Boundary Data**

Facility fields include:

* Facility Name, Type, Status
* Capacity
* Usage status
* Fixed post flag
* Residing boundary code
* Latitude & Longitude (optional)

#### 9.2 Validate & Upload

Validation rules:

* All fields are mandatory except latitude/longitude
* Dropdown values must be used
* No structural changes to the template
* No negative capacity values

Upload the file and click **Save and Proceed**.

***

### Step 10: Configure Microplan Assumptions

1. Answer preliminary questions (based on distribution strategy).

<figure><img src="../../../../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

1.  Configure assumptions under:

    * General
    * Registration
    * Distribution
    * Commodities
    * Vehicles

    <figure><img src="../../../../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

You can:

* Add new assumptions
* Delete existing assumptions

<figure><img src="../../../../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

Click **Save and Proceed**.

***

### Step 11: Configure Estimation Formulas

* Review auto-configured formulas based on campaign and strategy:
  * General
  * Registration
  * Distribution
  * Commodities
  * Vehicles
* Add or delete formulas if required.

<figure><img src="../../../../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

Click **Save and Proceed**.

***

### Step 12: Assign Users

Assign users to the microplan by role:

* National Microplan Estimation Approver
* National Facility Boundary Assigner
* National Population Data Approver
* Microplan Estimation Approver
* Facility Boundary Assigner
* Population Data Approver

<figure><img src="../../../../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

For each role:

1. Click **Assign**
2. Search and select users
3. Assign or unassign as needed

Click **Save and Proceed**.

***

### Step 13: Review & Finalise Microplan

* Review all configuration tabs in the summary screen.
* Make final edits if required.
* Finalise the microplan.

<figure><img src="../../../../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
⚠️ Once finalised, the microplan cannot be edited.
{% endhint %}

***

### Step 14: View Microplans

Click **Open Microplan** to view all microplans.

#### Microplan Statuses

* **Drafted** – Setup incomplete
* **Completed Setup** – Ready for execution
* **Validation in Progress**
* **Microplan Finalised**

<figure><img src="../../../../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

#### Available Actions

* **Edit Microplan:** Edit the microplan while it is in **Draft** status.
* **View Summary:** View the microplan details once setup is complete; editing is not allowed.
* **Download:** Download the finalised microplan estimation in **Excel** format.
