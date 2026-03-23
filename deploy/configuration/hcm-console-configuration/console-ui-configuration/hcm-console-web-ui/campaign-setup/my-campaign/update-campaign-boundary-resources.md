# Update Campaign - Boundary/Resources

This flow allows the user to update campaign boundary, facility, user, and target details once the campaign is created.

<figure><img src="../../../../../../../.gitbook/assets/image (45).png" alt=""><figcaption><p>My campaign</p></figcaption></figure>

Users can go to update campaign flow from the action button present in my campaigns screen.

Updating the campaign is possible only for ongoing and upcoming campaigns.

Screens coming for this update campaign are-

* Selecting Boundary&#x20;
* Update Facility details&#x20;
* Update User details
* Update Target&#x20;
* Summary&#x20;

## 1. Selecting Boundary

This is the first screen that is displayed to the user when they try to update the campaign from the My Campaigns screen. This screen is already pre-filled with the boundary data which is selected during the campaign creation.&#x20;

It is impossible to delete the already selected boundaries, user can always add new boundaries if they want to update.

<figure><img src="../../../../../../../.gitbook/assets/image (46).png" alt=""><figcaption><p>Boundary details</p></figcaption></figure>

File Path: - [https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/UpdateBoundaryWrapper.js](https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/UpdateBoundaryWrapper.js)

## 2. Update Facility Data

This screen allows the user to update the facility details:

<figure><img src="../../../../../../../.gitbook/assets/image (47).png" alt=""><figcaption><p>Update Facility Data</p></figcaption></figure>

When the user downloads the current facility template, then that template is already filled with the facility details that the user has entered during the time of campaign creation.

In this user can add the new facilities.

## 3. Upload User Details

This screen allows the user to update the facility details:

<figure><img src="../../../../../../../.gitbook/assets/image (48).png" alt=""><figcaption><p>Update user details</p></figcaption></figure>

When the user downloads the current user template, then that template is already filled with the user details that the user has entered during the time of campaign creation.

In this user can add a new user.

## 4. Update Targets

This screen allows the user to update targets:

<figure><img src="../../../../../../../.gitbook/assets/image (49).png" alt=""><figcaption><p>Update target details</p></figcaption></figure>

When the user downloads the current target template then that template is already filled with the target details that the user has entered during the time of campaign creation.

In this user can add the new targets or change the existing ones.

The file path of all the upload screens:&#x20;

[https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/UploadData.js](https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/UploadData.js)

## 5. Summary

This helps the user to view the summary of all the entered details in the previous screens:

<figure><img src="../../../../../../../.gitbook/assets/image (50).png" alt=""><figcaption><p>Summary</p></figcaption></figure>

File path - [https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/CampaignUpdateSummary.js](https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/CampaignUpdateSummary.js)

## Working of the update campaign flow-

The update campaign flow works similarly to the setup campaign. But the difference is that here we send the parentId in the URL and fetch it from there.

When the user clicks on next after the boundary details screen, the create API is called with parentID in the params and with action = draft.\
Then for the subsequent steps update API is called.\
In the summary screen again create API is called again but with action = 'create'. This action updates the campaign.

File Path: - [https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/UpdateCampaign.js](https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/UpdateCampaign.js)

### Validation of the update campaign

1. If no new boundary selected - If the user has not selected any new boundary then, to update the campaign at least one data upload is necessary.
2. New Boundaries Added - If the user has selected new boundaries then all the 3 data uploads are necessary for the user.

## API Details

<table><thead><tr><th width="257">Action</th><th>Role</th><th>Payload</th></tr></thead><tbody><tr><td>/project-factory/v1/project-type/create</td><td>CAMPAIGN_MANAGER</td><td>"action": "draft", <br>"action": "create", to update the campaign</td></tr><tr><td>/project-factory/v1/project-type/search</td><td>CAMPAIGN_MANAGER</td><td>only id is required in params</td></tr><tr><td>/project-factory/v1/project-type/update</td><td>CAMPAIGN_MANAGER</td><td></td></tr><tr><td>/project-factory/v1/data/_download</td><td>CAMPAIGN_MANAGER</td><td><p>Params will be different for different types-<br><br>1) boundary<br>tenantId:mz</p><p>type:boundary</p><p>hierarchyType:ADMIN</p><p>id:987eadc3-55a0-4553-925d-bf8087f57e5a<br><br>2) facilityWithBoundary<br>tenantId:mz</p><p>type:facilityWithBoundary</p><p>hierarchyType:ADMIN</p><p>id:052f59fc-18a7-4e07-816a-f5d8062b56b5<br><br>3) userWithBoundary<br>tenantId:mz</p><p>type:userWithBoundary</p><p>hierarchyType:ADMIN</p><p>id:fbfbd393-d053-4f51-9e12-1068b97da292</p></td></tr><tr><td></td><td></td><td></td></tr></tbody></table>
