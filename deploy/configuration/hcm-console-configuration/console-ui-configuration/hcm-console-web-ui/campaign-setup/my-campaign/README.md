# My Campaign

## Overview

My campaign screen allows users to see the list of campaigns that are in Ongoing, Completed, or Draft status. Users can search campaign by using the campaign name or campaign type. Users can also see a summary of the campaign and complete the campaign creation if it is draft status.

The list of statuses showing in the "My Campaign" screen are:&#x20;

1. Ongoing
2. Completed
3. Drafts
4. Failed
5. Upcoming&#x20;

<figure><img src="../../../../../../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

## User actions

After clicking on the My Campaign link from the HCM Campaign module card, the user lands on the My Campaign screen where the user can see all the lists of campaigns of each action in the tab.

File Path: [https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/MyCampaign.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/MyCampaign.js)

On my campaign screen, we are sending the payload:

* Campaigns with an end date that has passed the current date are marked as 'Completed'.
* Campaigns with a status of 'Started' and no end date, or with an end date in the future, are labeled as 'Ongoing'."
* The logic is written in UICustomizations.js
* File path: [https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/configs/UICustomizations.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/configs/UICustomizations.js)

Clicking on campaigns other than draft status will redirect to the summary page of the campaign where the user can see the complete details of the respective campaign.

<figure><img src="../../../../../../../.gitbook/assets/Screenshot from 2024-05-07 02-36-14.png" alt=""><figcaption></figcaption></figure>

File Path: [https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/CampaignSummary.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/CampaignSummary.js)

## **Ongoing Campaign Filtering**

For the ongoing campaign filtering functionality, we are utilizing the campaignsIncludeDates parameter set to true. The startDate and endDate parameters are both set to the current date. This configuration ensures that the API will return any campaign where the specified startDate or endDate falls within the campaign's defined start and end dates. Additionally, the campaign status is filtered to include campaigns with statuses of created or creating.

### **Parameters**&#x20;

* campaignsIncludeDates: This boolean parameter is set to true to enable date range filtering.
* startDate: The start date for the filter, is set to today's date.&#x20;
* endDate: The end date for the filter, is also set to today's date.&#x20;
* status: The campaign status filter, including the statuses created and creating.

### Implementation&#x20;

To filter the ongoing campaigns based on the criteria mentioned above, ensure that your request payload includes the following parameters:

```
{ 
   "campaignsIncludeDates": true, 
   "startDate": "", // Use the current epoch date dynamically 
   "endDate": "2024-05-23", // Use the current epoch date dynamically 
   "status": ["created", "creating"] 
}
```

### Logic Explanation&#x20;

* campaignsIncludeDates = true: This activates the date range filtering feature.&#x20;
* startDate and endDate = today: By setting both the start and end dates to today's date, the filter will capture any campaigns that are active today.&#x20;
* status = \["created", "creating"]: Filters the campaigns to only include those that are currently in the created or creating status.

## Completed **Campaign Filtering**

For filtering completed campaigns, we use a similar approach with a slight modification to the date parameters and status. Specifically, we will set the `endDate` parameter to yesterday's date. This configuration ensures that the API returns campaigns that have ended as of yesterday. The statuses to filter will remain `creating` and `created`.

### **Parameters**&#x20;

* **endDate**: The end date for the filter, is set to yesterday's date.
* **status**: The campaign status filter, including the statuses `creating` and `created`.

### Implementation&#x20;

To filter the ongoing campaigns based on the criteria mentioned above, ensure that your request payload includes the following parameters:

```
{
   "endDate": "", // Use the yesterday epoch date dynamically 
   "status": ["created", "creating"] 
}
```

### Logic Explanation&#x20;

1. **endDate = yesterday**: By setting the end date to yesterday's date, the filter will capture any campaigns that have ended by the end of the previous day.
2. **status = \["created", "creating"]**: Filters the campaigns to include only those that were in the `created` or `creating` status when they ended.

When a user clicks on the completed campaign, they will be redirected to the summary page displaying the campaign details. The success toast message will appear If the user credential sheet is generated successfully. Users can view or download the sheet from the user credential card or download button which appears at the top.

## Upcoming **Campaign Filtering**

For filtering upcoming campaigns, we use a different approach by setting the `campaignsIncludeDates` parameter to `false` and specifying the `startDate` parameter to tomorrow's date in epoch format. This configuration ensures that the API returns campaigns scheduled to start tomorrow. The statuses to filter will remain `creating` and `created`.

### **Parameters**&#x20;

* **campaignsIncludeDates**: This boolean parameter is set to `false` as we are not filtering based on a date range but rather a specific start date.
* **startDate**: The start date for the filter, is set to tomorrow's date in epoch format.
* **status**: The campaign status filter, including the statuses `creating` and `created`.

### Implementation&#x20;

To filter the upcoming campaigns based on the criteria mentioned above, ensure that your request payload includes the following parameters:

```
{
  "campaignsIncludeDates": false,
  "startDate": 1716748800,  // Use tomorrow's epoch date dynamically
  "status": ["created", "creating"]
}
```

#### Logic Explanation

1. **campaignsIncludeDates = false**: This deactivates the date range filtering feature, focusing the filter on a specific start date.
2. **startDate = tomorrow (epoch date)**: By setting the start date to tomorrow's date in epoch format, the filter will capture any campaigns scheduled to start tomorrow.
3. **status = \["created", "creating"]**: Filters the campaigns to include only those that are in the `created` or `creating` status and scheduled to start tomorrow.

When a user clicks on an upcoming campaign, they will be redirected to the summary page displaying the campaign details.

## Drafts **Campaign Filtering**

**For the drafts campaign, we are passing the status as drafted. It will return all the drafts that are in drafted status**

## Failed **Campaign Filtering**

**For failed campaigns, we are passing the status as failed. It will return all the drafts that are in failed status**

When a user clicks on a failed campaign, they will be redirected to the summary page displaying the campaign details. Additionally, a toast message will appear, showing the error that caused the campaign to fail.

<figure><img src="../../../../../../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

## MDMS

Path: [https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/project-types.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/project-types.json)

## API Details

<table><thead><tr><th width="220">End Point</th><th>Payload</th></tr></thead><tbody><tr><td>/project-factory/v1/project-type/search</td><td>{ "RequestInfo": { }, "CampaignDetails": { "tenantId": "mz", "status": [ "failed" ], "createdBy": "ff98f9f6-192b-4e12-8e90-7b73dcd0ad4d", "pagination": { "sortBy": "createdTime", "sortOrder": "desc", "limit": 10, "offset": 0 } } }</td></tr></tbody></table>
