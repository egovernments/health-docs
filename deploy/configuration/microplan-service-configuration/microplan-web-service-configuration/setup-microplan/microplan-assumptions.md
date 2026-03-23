# Microplan Assumptions

## Overview

The **Microplan Assumptions** step helps define campaign-specific hypotheses that drive planning and calculations. The assumptions shown to users are dynamically determined based on the **Campaign Type** and **Resource Distribution Strategy** selected earlier.

This configuration is completed in **two substeps**.

## **Steps**

### **Step 1: Registration and Distribution Process Selection**

This screen adapts automatically based on the **Resource Distribution Strategy** chosen in the Campaign Details step.

#### 1. If the Resource Distribution Strategy is **Mixed**

You must define **both** the registration and distribution processes.

**Registration Process**

* Question: **How is the campaign registration process happening?**
* Options:
  * House-to-House
  * Fixed Post
  * Mixed

**Distribution Process**

* Question: **How is the campaign distribution process happening?**
* Options:
  * House-to-House
  * Fixed Post
  * Mixed

**Selection Rules**

* Both registration and distribution **can be mixed**.
* **House-to-House** and **Fixed Post** cannot be selected together for registration and distribution.
* This ensures the two processes are clearly differentiated and correctly configured.

<figure><img src="../../../../../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

#### 2. If the Resource Distribution Strategy is **Fixed Post** or **House-to-House**

You must define how registration and distribution are related.

**Question**

* **Is the registration and distribution process happening together or separately?**

**Options**

* Together
* Separately

The selected option determines how the system pre-configures the assumptions in the next step.

<figure><img src="../../../../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

### Step 2: Configure Assumptions Using the Assumptions Form

After defining the registration and distribution flow, you proceed to the **Assumptions Form**.

The form is **dynamically generated from MDMS**, based on:

* Selected **Campaign Type** (for example, Bednet, SMC)
* Selected **Resource Distribution Strategy** (House-to-House, Fixed Post, Mixed)

<figure><img src="../../../../../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>

#### Assumption Categories

Depending on the campaign configuration, the form may include the following categories:

* **General Assumptions**\
  High-level parameters that apply to the overall campaign.
* **Registration Assumptions**\
  Assumptions related to how and where registration activities are conducted.
* **Distribution Assumptions**\
  Parameters defining distribution methods and operational logistics.
* **Commodities Assumptions**\
  Details related to items being distributed (for example, number of bednets per household).

#### Entering Assumption Values

* Users must enter values for each assumption.
* All assumption fields are **mandatory**.

**Validation Rules**

* Values must be **numeric**.
* Allowed range: **0 to 1000**.
* Maximum of **two decimal places**\
  (for example, `12.34` is valid, `12.345` is not).
* Must follow a valid number format (whole number or decimal).

#### Tooltips and Guidance

* Each assumption field includes a **tooltip**.
* Hovering over a field displays additional information to help users understand the parameter and expected input.

### Managing Assumptions

#### Add a New Assumption

1. Click **Add New Assumption**.
2. A popup/modal appears.
3. Provide the following:
   * **Choose Assumption**: Select an existing assumption or create a new one.
   * **Assumption Name**: Enter a name for the new assumption.
4. Choose:
   * **Add**: Saves the assumption after validation.
   * **Cancel**: Discards changes and closes the popup.

<figure><img src="../../../../../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>

#### Delete an Assumption

1. Click **Delete** next to the assumption.
2. Confirm your action:
   * **Yes**: Deletes the assumption.
   * **No**: Cancels the action.

**Recover a Deleted Assumption**

* Click **Add New Assumption**.
* Select the deleted assumption from the **Choose Assumption** dropdown.
*

    <figure><img src="../../../../../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../../../../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

### Key Behaviour

* Assumption categories and parameters are **fully dynamic**.
* They change automatically based on:
  * Campaign Type
  * Resource Distribution Strategy
* This ensures assumptions remain relevant, consistent, and aligned with the campaign design.
