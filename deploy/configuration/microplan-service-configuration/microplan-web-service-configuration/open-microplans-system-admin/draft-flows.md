# Draft Flows

## Overview

The draft flow enables admins to edit microplans. When a user reopens a microplan via the microplan search, it loads at the last edited page.

## Workflow

1. **Edit Microplans**: Admins edit the microplan, which redirects to`employee/microplan/setup-microplan?key=8&microplanId=c4cb8a1b-ef4f-4998-afe4-5dd0432c1&campaignId=ef3f044f-047f-4eb5-adb1-5dbc92507461` (sample URL).
2. **User Edits**: Users update details such as data management, boundary selection, and user-tagging.
3. **Save Changes**: Changes are saved.
4. **Reopen Microplan**: When reopened, the microplan loads the last edited page for further edits.

## Implementation

1. **Redirection**: When the user clicks "Edit Microplan," they are redirected to the following URL:

```
/employee/microplan/setup-microplan?key=${resolvedKey}&microplanId=${row.id}&campaignId=${row.campaignDetails.id}
```

&#x20;      The row represents a plan object.

2. **Retrieving Last Edited Screen:**\
   The last edited screen is retrieved from the `additionalDetails` field in the `/plan-service/config/search` response.
3. **User Input:**\
   The user fills in the required details on the redirected page. The input is stored in `totalForm` data, which holds the input as key-value pairs.
4. **Updating the Plan:**\
   The `totalForm` data is used to update the plan object. The `useCreateUpdatePlanProject` hook is utilised to update the appropriate attributes of the plan based on the current screen. The updated plan object is then sent to `/plan-service/config/update`. Primarily, the `additional` key is updated to ensure that the user lands on the last edited page during subsequent edits.
5. **Campaign Object Update:**\
   For boundary and microplan details pages, the campaign object is also updated. The updated campaign object is sent to `/project-factory/v1/project-type/update`.

## API Endpoints

<table><thead><tr><th width="182.5625">    Endpoint</th><th width="146">Type of Request</th><th>                                      Payload</th></tr></thead><tbody><tr><td>/plan-service/config/<em>search</em></td><td>POST</td><td><code>{ "PlanConfigurationSearchCriteria": { "tenantId": "mz", "id": "c4cb8a1b-ef4f-4998-afe4-5dd0432c11a2" } }</code></td></tr><tr><td>/plan-service/config/_update</td><td>POST</td><td>[ { "id": "c4cb8a1b-ef4f-4998-afe4-5dd0432c11a2", "tenantId": "mz", "name": "Malaria-SMC Campaign-Fixed Post-07 Jan 25j", "campaignId": "ef3f044f-047f-4eb5-adb1-5dbc92507461", "status": "DRAFT","additionalDetails": { "key": "6", "assumptionsForm": { "selectedRegistrationDistributionMode": { "code": "TOGETHER", "value": "Together" } }, "campaignType": "MR-DN", "DistributionProcess": "FIXED_POST", "RegistrationProcess": "FIXED_POST", "resourceDistributionStrategyCode": "FIXED_POST", "isRegistrationAndDistributionHappeningTogetherOrSeparately": "TOGETHER" }, "workflow": null } ]</td></tr><tr><td>project-factory/v1/project-type/update</td><td>POST</td><td>{ "id": "ef3f044f-047f-4eb5-adb1-5dbc92507461", "tenantId": "mz", "status": "drafted", "action": "draft", "campaignNumber": "CMP-2025-01-07-007018", "isActive": true, "parentId": null, "campaignName": "Malaria-SMC Campaign-Fixed Post-07 Jan 25k", "projectType": "MR-DN", "hierarchyType": "MICROPLAN",  }</td></tr></tbody></table>

