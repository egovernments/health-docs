# Assumptions & Formulae Data

## Overview

The **Assumptions and Formulae** step helps the system automatically load campaign-specific logic based on the choices you make earlier. These configurations define how resources are calculated and distributed during the campaign.

The data shown in this step is **pre-configured and auto-loaded** from MDMS, based on your selections.

## Steps

### Step 1: Select the Campaign Type

* Choose a **Campaign Type** (for example, _Bednet Campaign_).
* Campaign types are loaded from [**MDMS**](https://unified-dev.digit.org/workbench-ui/employee/workbench/mdms-search-v2?moduleName=HCM-PROJECT-TYPES\&masterName=projectTypes).
* This selection acts as the primary driver for which assumptions and formulae are applicable.

<figure><img src="../../../../../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>

### Step 2: Select the Resource Distribution Strategy

Choose how resources will be distributed during the campaign:

* **House to House**
* **Fixed Post**
* **Mixed**

Your selection here determines what additional details the system asks for and how assumptions and formulae are pre-configured.

<figure><img src="../../../../../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>

### Step 3: Define Registration and Distribution Flow

If the Resource Distribution Strategy is **Mixed**

* You must configure **both**:
  * Registration process
  * Distribution process
* For each process, choose one of the following:
  * Mixed
  * House to House
  * Fixed Post
* Rules:
  * Both registration and distribution can be **mixed**.
  * **House-to-House** and **Fixed Post** cannot be selected together for registration and distribution.

{% hint style="info" %}
If the Resource Distribution Strategy is **House-to-House** or **Fixed Post**

* Specify whether:
  * Registration and distribution happen **together**, or
  * Registration and distribution happen **separately**.
* This choice controls how the campaign workflow is structured.
{% endhint %}

<figure><img src="../../../../../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>

### Step 4: System Loads Assumptions Automatically

* Based on:
  * Campaign type
  * Resource distribution strategy
  * Registration and distribution flow
* The system auto-loads the relevant assumptions from [**`HypothesisAssumptions`**](https://unified-dev.digit.org/workbench-ui/employee/workbench/mdms-search-v2?moduleName=hcm-microplanning\&masterName=HypothesisAssumptions) **(MDMS)**.
* These assumptions define campaign hypotheses such as coverage, effort, and operational constraints.

<figure><img src="../../../../../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>

### Step 5: System Loads Formulae Automatically

* Using the same selections, the system loads calculation rules from [**`AutoFilledRuleConfigurations`**](https://unified-dev.digit.org/workbench-ui/employee/workbench/mdms-view?moduleName=hcm-microplanning\&masterName=AutoFilledRuleConfigurations\&uniqueIdentifier=LLIN-mz.MIXED.SEPARATELY.MIXED.MIXED) **(MDMS)**.
* These formulae control how:
  * Resource quantities
  * Workforce requirements
  * Operational timelines are calculated in the microplan.

<figure><img src="../../../../../.gitbook/assets/image (114).png" alt=""><figcaption></figcaption></figure>

### Example Flow

1. Campaign Type: **Bednet Campaign**
2. Resource Distribution Strategy: **Mixed**
3. Registration Process: **House to House**
4. Distribution Process: **Fixed Post**

Based on these selections:

* **Assumptions** are loaded from [`HypothesisAssumptions`](https://unified-dev.digit.org/workbench-ui/employee/workbench/mdms-view?moduleName=hcm-microplanning\&masterName=HypothesisAssumptions\&uniqueIdentifier=LLIN-mz.MIXED.SEPARATELY.MIXED.MIXED)
* **Formulae** are loaded from [`AutoFilledRuleConfigurations`](https://unified-dev.digit.org/workbench-ui/employee/workbench/mdms-view?moduleName=hcm-microplanning\&masterName=AutoFilledRuleConfigurations\&uniqueIdentifier=LLIN-mz.MIXED.SEPARATELY.MIXED.MIXED)

No manual configuration is required—the system selects the correct data automatically.
