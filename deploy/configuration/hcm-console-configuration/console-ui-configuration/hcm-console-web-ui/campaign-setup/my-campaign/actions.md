# Actions

A new '**Actions'** column has been added to the **"My Campaign"** screen, allowing users to perform some tasks skillfully.

Users can click on '**Actions'** to choose from the available action options in the menu.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfkH3JKtFe5SWQopCQYO7kKPSwdcns2WRTZ4Ph9suRGJj3we1F4SZRjrJxbBUDyAv64dEiXcoIKtF5lGyNn9oQEcVwgUpPSg9y_AHsAMoCuiymb0qEkkPtD5F4uUEMlgpY-2O2el8dI0VejMCHUA4apTp6I?key=oCaYcIUXE6aGO0fM5H8mfQ" alt=""><figcaption></figcaption></figure>

### Implementation:

We've added config for column actions in myCampaignConfig.js

```javascript
 {
                label: "CAMPAIGN_ACTIONS",
                jsonPath: "actions",
                additionalCustomization: true,
 }
```

In UICustomization.js, we have added a component that needs to be rendered for the action column under _**additionalCustomizations**_.

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

We have added an _**onActionSelect**_ function which acts based on the selected option.

Actions are different according to the different campaign status



{% tabs %}
{% tab title="Ongoing" %}
Here user will get all the actions such as:

For the case of ongoing campaigns user is able to update the campaign , configure checklist and to view user credentials , all the 4 options will be visible.

<figure><img src="../../../../../../../.gitbook/assets/image (39).png" alt=""><figcaption><p>Action Ongoing</p></figcaption></figure>
{% endtab %}

{% tab title="Completed" %}
For the case of  completed campaings user will not be able to update the campaign. Only view the user credentials:

<figure><img src="../../../../../../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Upcoming" %}
Here user will get all the actions such as:\
For the case of upcoming campaigns user is able to update the campaign , configure checklist and to view user credentials ,all the 4 options will be visible.

<figure><img src="../../../../../../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Drafts" %}
Draft state will have no action button.
{% endtab %}

{% tab title="Failed" %}
Failed state will have no action button.
{% endtab %}
{% endtabs %}

File Path:

[https://github.com/egovernments/DIGIT-Frontend/blob/8e56e756453222445162013fec7d16ab227b85c5/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/MyCampaign.js](https://github.com/egovernments/DIGIT-Frontend/blob/8e56e756453222445162013fec7d16ab227b85c5/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/MyCampaign.js)

Config:

[https://github.com/egovernments/DIGIT-Frontend/blob/f00410f4d8198d8eebfaf7d7655661c64aff2397/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/configs/myCampaignConfig.js](https://github.com/egovernments/DIGIT-Frontend/blob/f00410f4d8198d8eebfaf7d7655661c64aff2397/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/configs/myCampaignConfig.js)

UICustomisation:

[https://github.com/egovernments/DIGIT-Frontend/blob/8e56e756453222445162013fec7d16ab227b85c5/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/configs/UICustomizations.js](https://github.com/egovernments/DIGIT-Frontend/blob/8e56e756453222445162013fec7d16ab227b85c5/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/configs/UICustomizations.js)
