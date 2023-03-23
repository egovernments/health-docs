# Project Selection

## Overview

After a user logs into the HCM app, the project selection screen displays all the projects assigned to the user.

## User actions

On this page, the following actions can be performed:

* A user has to select one project.&#x20;
* After selecting a project, the system downloads the data for the selected project only.

![](<../../.gitbook/assets/image (26).png>)

* After every login action, the system will automatically syncs the data with the system.&#x20;
* Since the user will log in only at the start of the day and before going into the field, there must be stable internet connectivity for the device to perform this process.
* &#x20;A “Sync in Progress” window appears on the screen and the user cannot perform any other action until the process is complete.&#x20;

## **API details**

| End Point                  | Request Method | Request Info                                                                                                                                                                                                                                |
| -------------------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /project/staff/v1/\_search | `POST`         | <pre class="language-json"><code class="lang-json">{
  "RequestInfo": {
    "authToken": "string"
  },
  "ProjectStaff": {
    "staffId": "string",
  }
}
</code></pre>                                                                     |
| /project/v1/\_search       | POST           | <pre class="language-json"><code class="lang-json">{
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
</code></pre> |
