# Checklist

## Overview

The "My Checklist" screen allows supervisors to perform random or scheduled inspections, and record observations of the inspection activity.

![](https://lh5.googleusercontent.com/qtKMdKMut8JY6VYnkBSKw4Visepz15wf-y-Ij2foOM9IrrODwIPj74g5VS8s-pl7E-ZDHWJgesqDhr4onPBNf7JVuPM2xfwRibQcYm7Xgeq9O0Hq-p0AeT4awt6ZTw5vzNE7i5bWYJlZ1Ux4ue3jbpw)

## User actions

On this page, the following actions can be performed:

* Clicking on "My Checklist," will display the checklists assigned to the user role.

![](https://lh3.googleusercontent.com/\_y963QR2vmvgdJKq7fFeLuGSdi2-oJJhNpRicQZaS7iR0ILsJd4afTRYUTkJoUVFdsBIti6z4hMaIIWEV03U8m60MWSrpFB\_2Bx47YitftvZx4\_I9aDYLZLPlVNqLjT-696hzQEmS8R-wrIvJzfbprQ)![](<../../../../.gitbook/assets/image (13).png>)

* Clicking on any checklist will show a popup with

&#x20;    \- Create Checklist

&#x20;    \- View Submitted Checklists&#x20;

File Path : [https://github.com/egovernments/health-campaign-field-worker-app/tree/master/apps/health\_campaign\_field\_worker\_app/lib/pages/checklist](https://github.com/egovernments/health-campaign-field-worker-app/tree/master/apps/health\_campaign\_field\_worker\_app/lib/pages/checklist)

* The "Create Checklist" option will allow the supervisor to fill the checklist against the date and the administrative area.

![](https://lh6.googleusercontent.com/wYAR7sY3g4U\_prDFvzNiW1J7dd6cEpsGgDcutW4io154s3th\_knEzp0XTtG\_iAaY\_Aq7lNMUf3KEktfXq9CgtSPi5CnBMHIkfAht8yJM6tFWjVwbI6xTUFOck1Ebo175erG2GZSMPy2xZGQ2s8Axujc)\


* The "View Submitted Checklists" will show the checklists submitted by the supervisor.

![](<../../../../.gitbook/assets/image (16).png>)\


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

