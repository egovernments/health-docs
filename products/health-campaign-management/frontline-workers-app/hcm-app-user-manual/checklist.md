# Checklist

## Overview

The "My Checklist" screen allows supervisors to perform random or scheduled inspections, and record observations of the inspection activity.

<figure><img src="../../../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

## User actions

On this page, the following actions can be performed:

* Clicking on "My Checklist," will display the checklists assigned to the user role.

<figure><img src="../../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

* Clicking on any checklist will show a popup with

&#x20;    \- Fill Checklist

&#x20;    \- View Submitted Checklists&#x20;

File Path : [https://github.com/egovernments/health-campaign-field-worker-app/tree/master/apps/health\_campaign\_field\_worker\_app/lib/pages/checklist](https://github.com/egovernments/health-campaign-field-worker-app/tree/master/apps/health\_campaign\_field\_worker\_app/lib/pages/checklist)

* The "Fill Checklist" option will allow the supervisor to fill the checklist against the date and the administrative area.



<figure><img src="../../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

* The "View Submitted Checklists" will show the checklists submitted by the supervisor.

<figure><img src="../../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

## **API details**

<table><thead><tr><th width="206.33333333333334">End Point</th><th width="149">Request Method</th><th>Request Info</th></tr></thead><tbody><tr><td>/service/v1/_create</td><td><code>POST</code></td><td><pre class="language-json"><code class="lang-json">{
  "requestInfo": {
    "authToken": "string"
  },
  "service": {
    "tenantId": "pb.amritsar",
    "serviceDefId": "string",
    "referenceId": "string",
    "attributes": [
      {
        "attributeCode": "string",
        "value": {},
        "additionalDetails": {}
      }
    ],
    "additionalDetails": {}
  }
}
</code></pre></td></tr><tr><td>/service/v1/_search</td><td>POST</td><td><pre class="language-json"><code class="lang-json">{
  "requestInfo": {
    "authToken": "string"
  },
  "serviceDefinition": {
    "tenantId": "pb.amritsar",
    "serviceDefIds": [
      "string"
    ],
    "referenceIds": [
      "string"
    ]
  }
}
</code></pre></td></tr></tbody></table>

