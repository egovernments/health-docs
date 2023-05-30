# Project Selection

##

## Overview

After a user logs into the HCM app, the project selection screen displays all the projects assigned to the user.

## User actions

On this page, the following actions can be performed:

* A user has to select one project.&#x20;
* After selecting a project, the system downloads the data for the selected project only.

![](<../../../../.gitbook/assets/image (26).png>)

* After every login action, the system will automatically syncs the data with the system.&#x20;
* Since the user will log in only at the start of the day and before going into the field, there must be stable internet connectivity for the device to perform this process.
* &#x20;A “Sync in Progress” window appears on the screen and the user cannot perform any other action until the process is complete.&#x20;

## **API details**

<table><thead><tr><th width="206.33333333333334">End Point</th><th width="149">Request Method</th><th>Request Info</th></tr></thead><tbody><tr><td>/project/staff/v1/_search</td><td><code>POST</code></td><td><pre class="language-json"><code class="lang-json">{
  "RequestInfo": {
    "authToken": "string"
  },
  "ProjectStaff": {
    "staffId": "string",
  }
}
</code></pre></td></tr><tr><td>/project/v1/_search</td><td>POST</td><td><pre class="language-json"><code class="lang-json">{
  "RequestInfo": {
    "authToken": "string"
  },
  "Project": [
    {
      "tenantId": "tenantA",
      "name": "string",
      "projectType": "string",
      }
  ]
}
</code></pre></td></tr></tbody></table>

<table><thead><tr><th width="145.00000000000003">Label</th><th>Path</th><th>Widgets Description</th></tr></thead><tbody><tr><td>Project Selection  Screen </td><td><a href="https://github.com/egovernments/health-campaign-field-worker-app/blob/master/apps/health_campaign_field_worker_app/lib/pages/project_selection.dart">https://github.com/egovernments/health-campaign-field-worker-app/blob/master/apps/health_campaign_field_worker_app/lib/pages/project_selection.dart</a></td><td><ol><li>Digit Project Cell: <a href="https://github.com/egovernments/health-campaign-field-worker-app/blob/master/packages/digit_components/lib/widgets/digit_project_cell.dart">https://github.com/egovernments/health-campaign-field-worker-app/blob/master/packages/digit_components/lib/widgets/digit_project_cell.dart</a></li><li>Digit Elevated Button:<br><a href="https://github.com/egovernments/health-campaign-field-worker-app/blob/master/packages/digit_components/lib/widgets/digit_elevated_button.dart">https://github.com/egovernments/health-campaign-field-worker-app/blob/master/packages/digit_components/lib/widgets/digit_elevated_button.dart</a></li><li>Toaster: <a href="https://github.com/egovernments/health-campaign-field-worker-app/blob/master/packages/digit_components/lib/widgets/atoms/digit_toast_helper.dart">https://github.com/egovernments/health-campaign-field-worker-app/blob/master/packages/digit_components/lib/widgets/atoms/digit_toast_helper.dart</a></li></ol><p></p></td></tr></tbody></table>

