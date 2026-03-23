---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-console-configuration/console-ui-configuration/hcm-console-web-ui/campaign-setup/my-campaign/actions
---

# Actions

## Overview

The **My Actions** feature adds an **Actions** column to the **My Campaign** screen. This column allows users to perform context-specific tasks on a campaign—based on its current status—using a simple action menu.

## Steps

### Step 1: Enable the Actions Column

**Purpose:** Add an Actions column to the My Campaign table.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfkH3JKtFe5SWQopCQYO7kKPSwdcns2WRTZ4Ph9suRGJj3we1F4SZRjrJxbBUDyAv64dEiXcoIKtF5lGyNn9oQEcVwgUpPSg9y_AHsAMoCuiymb0qEkkPtD5F4uUEMlgpY-2O2el8dI0VejMCHUA4apTp6I?key=oCaYcIUXE6aGO0fM5H8mfQ" alt=""><figcaption></figcaption></figure>

#### Configuration

* The Actions column is defined in `myCampaignConfig.js`.

```javascript
 {
                label: "CAMPAIGN_ACTIONS",
                jsonPath: "actions",
                additionalCustomization: true,
 }
```

**Outcome**

* An Actions column is rendered for each campaign row.
* The column supports custom UI rendering.

### Step 2: Render the Actions Button

**Purpose:** Display an interactive action menu for each campaign.

#### Implementation

* In `UICustomizations.js`, a custom component is rendered using `additionalCustomizations`.

```javascript
case "CAMPAIGN_ACTIONS":
          return (
              <Button
                className="custom-className"
                type="actionButton"
                variation="secondary"
                label={"Action"}
                options={[{ key: 1, code: "OPTION", i18nKey: t("OPTION") }]}
                optionsKey="i18nKey"
                showBottom={true}
                isSearchable={false}
                onOptionSelect={(item) => onActionSelect(item, row)}
              />
          );
```

**Outcome**

* Each campaign row displays an **Action** button.
* Clicking the button opens a dropdown menu with available actions.

### Step 3: Handle Action Selection

**Purpose:** Trigger the correct behaviour when a user selects an action.

#### Implementation

* An `onActionSelect` function is used to handle user selections.
* The function:
  * Reads the selected option
  * Determines the campaign status
  * Executes the corresponding action

### Step 4: Configure Actions by Campaign Status

Available actions vary depending on the campaign’s current state.

{% tabs %}
{% tab title="Ongoing" %}
**Available Actions:**

* Update campaign
* Configure checklist
* View user credentials\
  ➡️ All actions are enabled.

<figure><img src="../../../../../../../.gitbook/assets/image (184).png" alt=""><figcaption><p>Action Ongoing</p></figcaption></figure>
{% endtab %}

{% tab title="Completed" %}
**Available Actions:**

* View user credentials\
  ➡️ Update and configuration actions are disabled.

<figure><img src="../../../../../../../.gitbook/assets/image (185).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Upcoming" %}
**Available Actions:**

* Update campaign
* Configure checklist
* View user credentials\
  ➡️ All actions are enabled.

<figure><img src="../../../../../../../.gitbook/assets/image (186).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Drafts" %}
**Available Actions:**

* No action button is shown.
{% endtab %}

{% tab title="Failed" %}
**Available Actions:**

* No action button is shown.
{% endtab %}
{% endtabs %}

#### Reference Links

* [MyCampaign.js](https://github.com/egovernments/DIGIT-Frontend/blob/8e56e756453222445162013fec7d16ab227b85c5/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/MyCampaign.js)
* [Campaign Configuration](https://github.com/egovernments/DIGIT-Frontend/blob/f00410f4d8198d8eebfaf7d7655661c64aff2397/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/configs/myCampaignConfig.js)
* [UI Customisation](https://github.com/egovernments/DIGIT-Frontend/blob/8e56e756453222445162013fec7d16ab227b85c5/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/configs/UICustomizations.js)
