# Formula Configuration

## Overview

The **Formula Configuration** screen allows you to define and manage resource estimation formulas based on campaign assumptions and distribution strategies. These formulas determine how resources are calculated and whether results appear on the **Estimation Dashboard (Population Inbox Screen)**.

## Steps

### Step 1: Review Autofilled Formulas

**MDMS Integration for Autofilled Configurations**

* The formulas on the **Formula Configuration Screen** are dynamically autofilled based on data from the  [MDMS](https://unified-qa.digit.org/workbench-ui/employee/workbench/mdms-search-v2?moduleName=hcm-microplanning\&masterName=AutoFilledRuleConfigurations).
* These configurations are tailored using specific keys that define the **campaign type, distribution strategies, and processes**.

These predefined formulas can be reviewed, edited (if permitted), deleted, or supplemented with new formulas.

<figure><img src="../../../../../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>

### Step 2: Add a New Formula

To create a new formula:

1. Click **Add Formula**.
2. Enter the **Formula Name**.
3. Select the required **Input Parameters** (assumptions or derived values).
4. Choose the appropriate **Operator** (for example: divide, multiply).
5. Save the formula.

After saving, decide whether the formula should be visible on the Estimation Dashboard (see Step 4).

<figure><img src="../../../../../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>

### Step 3: Delete an Existing Formula

To remove a formula:

1. Click **Delete** next to the formula.
2. If the formula is currently being used in the campaign:
   * The system prompts you to either:
     * Reuse the deleted formula, or
     * Define a replacement formula.

This ensures campaign estimations remain valid and consistent.

### Step 4: Control Dashboard Visibility

Each formula includes a **Show on Estimation Dashboard** option.

* ✔ **Checked** → The formula result appears on the Estimation Dashboard (Population Inbox Screen).
* ✖ **Unchecked** → The formula remains active for internal calculations but will not be displayed on the dashboard.

This allows you to control which outputs are visible to operational users.

### Sample Formula Configurations

Below are examples of how formulas may be configured.

#### Example 1: Total Number of Bednets per Boundary

**Formula:**

```
Total Number of Bednets = Target Population ÷ Number of Persons per Bednet
```

**Dependencies:**

* Target Population (assumption)
* Number of Persons per Bednet (assumption)

**Optional Action:**

* Select **Show on Estimation Dashboard** if the result should be visible to users.

***

#### Example 2: Total Number of Bales per Boundary

**Formula:**

```
Total Number of Bales = Total Number of Bednets ÷ Number of Bednets per Bale
```

**Dependencies:**

* Total Number of Bednets (derived formula)
* Number of Bednets per Bale (assumption)

**Optional Actions:**

* Display it on the Estimation Dashboard, or
* Delete it if not required.
