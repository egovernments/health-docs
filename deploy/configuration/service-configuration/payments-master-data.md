---
description: Health payments master data configuration details
---

# Payments Master Data

<table><thead><tr><th width="157.73828125">Master</th><th width="155.4921875">Module</th><th width="210.1875">Reference Link</th><th>Description</th></tr></thead><tbody><tr><td>HCM</td><td>paymentsConfig</td><td><a href="https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/health/payments-config.json">HCM.paymentsConfig</a></td><td>UI Configs</td></tr><tr><td>HCM</td><td>WORKER_RATES</td><td><a href="https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/health/workerRates.json">HCM.WORKER_RATES</a></td><td>Rate Master Configs</td></tr><tr><td>common-masters</td><td>MusterRoll</td><td><a href="https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/common-masters/MusterRoll.json">common-masters.MusterRoll</a></td><td>Muster Roll and Attendance Configs</td></tr></tbody></table>

```
{
  "tenantId": "{{tenantId}}", 
  "moduleName": "HCM", 
  "paymentsConfig": [ 
    { 
      "tenantId": "{{tenantId}}", 
      "enableApprovalAnyTime": "{{boolean}}", // e.g., true - Allows approval at any time. To restrict approval to only validate through the campaign endDate, set to false.
      "lowestLevelBoundary": "{{boundaryType}}" // e.g., "DISTRICT" - Specifies the lowest-level dropdown option in boundary selection
    } 
  ] 
}

```
