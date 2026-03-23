# Manage Dependent Fields

## Overview

The **Dependent Field** feature allows administrators to control the visibility of a field based on the value of another field.

Using display logic, a field can dynamically appear or remain hidden depending on user input. This helps:

* Simplify data entry screens
* Reduce data entry errors
* Ensure only relevant information is captured

## Steps

### Step 1: Select the Field

* Navigate to the **Page Properties** panel on the relevant screen.
* Select the field for which you want to configure dependency.

<figure><img src="../../../../.gitbook/assets/unknown (19).png" alt=""><figcaption></figcaption></figure>

### Step 2: Open Field Logic Settings

* In the **Field Properties** panel, go to the **Logic** tab.
* Enable the **Dependent Field** toggle.
* Click **Add Display Logic** to open the configuration pop-up.

### Step 3: Configure the Display Condition

In the **If** section of the pop-up:

* Select the **Page** where the controlling field is located.
* Select the **Field** that will control visibility.
* Choose the appropriate **Operator** (e.g., Equals to, Not equals, Greater than).
* Specify the comparison value:
  * Enter a fixed value, **or**
  * Select **Use Another Field** to compare against another field in the form.

If needed, click **Add Condition** to define additional rules.

<figure><img src="../../../../.gitbook/assets/unknown (20).png" alt=""><figcaption></figcaption></figure>

### Step 4: Review and Confirm Logic

* Review the **logic summary** displayed at the bottom of the pop-up.
* Verify that the rule correctly reflects the intended behaviour.
* Click **Confirm Logic** to apply the dependency.

### Step 5: Save Configuration

* Click **Save Configuration** to apply the changes.

The configured display logic will now be reflected in the mobile application (APK) during campaign execution.
