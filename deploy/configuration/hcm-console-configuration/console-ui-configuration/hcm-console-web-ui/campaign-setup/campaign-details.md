---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-console-configuration/console-ui-configuration/hcm-console-web-ui/campaign-setup/campaign-details
---

# Campaign Details

## Overview

The Campaign Details feature has 4 screens:

* Campaign Type
* Campaign Name
* Campaign Dates
* Campaign Details Summary

## Steps

### 1.  Campaign Type

This is the first screen that appears when the user clicks "set up campaign". In this screen, the user can select the campaign type, and the beneficiary will be prepopulated from the MDMS. This field is mandatory to set up a campaign.

<figure><img src="../../../../../../.gitbook/assets/image (157).png" alt=""><figcaption><p>Campaign Type</p></figcaption></figure>

Here, the dropdown will show the list of campaign types in the MDMS. We will fetch the MDMS data from. For more information, check the configurations from the link [here](/broken/pages/HOE2bIXaoPn6bibfTTpA#id-1.-project-type-configuration)

File Path: [https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/CampaignType.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/CampaignType.js)

### 2. Campaign Name&#x20;

This screen comes after the campaign type. This step is crucial for saving your campaign as a draft, as the name serves as a unique identifier. After clicking on 'Next', the name will be saved, and the user can check the draft.

<figure><img src="../../../../../../.gitbook/assets/image (158).png" alt=""><figcaption><p>Camapign Name</p></figcaption></figure>

File Path: [https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/CampaignName.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/CampaignName.js)

### 3. Campaign Dates

This screen asks a user to fill in the start and end dates of the campaign.&#x20;

<figure><img src="../../../../../../.gitbook/assets/image (159).png" alt=""><figcaption><p>Campaign Dates</p></figcaption></figure>

FilePath: [https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/CampaignDates.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/CampaignDates.js)

### 4. Summary

This screen will show the summary of the campaign details screen

<figure><img src="../../../../../../.gitbook/assets/image (160).png" alt=""><figcaption><p>Campaign details summary</p></figcaption></figure>

## API Details

<table><thead><tr><th width="396.69140625">Action</th><th>Role</th></tr></thead><tbody><tr><td>project-factory/v1/project-type/create</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>project-factory/v1/project-type/search</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>/project-factory/v1/project-type/search</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>/project-factory/v1/project-type/update</td><td>CAMPAIGN_MANAGER</td></tr></tbody></table>
