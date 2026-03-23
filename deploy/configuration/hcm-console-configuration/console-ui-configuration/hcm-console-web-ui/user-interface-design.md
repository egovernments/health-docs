# User Interface Design

## Overview

This page is about configuring the front-end (User Interface) of the HCM Console. It covers settings needed in build scripts, Helm charts, environment files, global configuration JS, and asset storage (S3). These are used to customise look, behaviour, logos, roles, localisation, etc., for different environments (dev, test, production).

## MDMS Configuration

To enable and run the **Campaign Module** in an environment, several MDMS configurations must be added or updated.

1\. **Citymodule Configuration** - Add the **Campaign** module in [`citymodule.json`](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/tenant/citymodule.json). The city module is needed to run the campaign module in an environment:&#x20;

```
{
      "module": "Campaign",
      "code": "Campaign",
      "active": true,
      "order": 10,
      "tenants": [
        {
          "code": "mz"
        }
      ]
    },
```

2. **Roleactions Configuration -** Define role-action mappings for user access to Campaign services. 🔗 [roleactions.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ROLEACTIONS/roleactions.json)
3. **Actions Test Configuration -** Configure sidebar actions and service access for users.               🔗 [actions-test.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json).  To enable sidebar actions, add `navigationUrl` and `path`:

````
{
      ```
      "path": "1Campaign.Mycampaign",
      "navigationURL": "/workbench-ui/employee/campaign/my-campaign",
      "leftIcon": "dynamic:EstimateIcon",
      "rightIcon": ""
    }
````

{% hint style="info" %}
📌 Refer to the following Action IDs in QA:

* [1528](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L10660) [1763](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13768) [1764](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13779) [1765](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13790) [1766](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13801) [1767](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13812) [1768](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13823) [1769](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13834) [1770](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13845) [1771](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13856) [1772](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13867) [1773](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13878) [1774](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13889) [1775](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13900) [1776](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13913) [1777](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ACTIONS-TEST/actions-test.json#L13924)
{% endhint %}

4. **Roles Configuration -** Add campaign roles in `roles.json`.

🔗 [roles.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/ACCESSCONTROL-ROLES/roles.json)

```
{
      "code": "CAMPAIGN_MANAGER",
      "name": "Campaign Manager",
      "description": "Campaign Manager"
    }
```

5. **Validation Schemas -** Use the schemas below for validating different uploads in the campaign module:
   1. **Boundary Schema** → For validating boundary sheet uploads\
      🔗 [boundarySchema.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/health/hcm-admin-console/boundarySchema.json)
   2. **Facility Schema** → For validating facility sheet uploads\
      🔗 [facilitySchema.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/health/hcm-admin-console/facilitySchema.json)
   3. **User Schema** → For validating user sheet uploads\
      🔗 [userSchema.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/health/hcm-admin-console/userSchema.json)
6. **Hierarchy Configuration -** Define the lowest hierarchy level for boundary selection in campaigns. 🔗 [hierarchyConfig.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/health/hcm-admin-console/hierarchyConfig.json)

## DevOps Configuration

In addition to MDMS updates, certain **global configurations** and **Helm charts** must be added to ensure the Campaign Module runs properly.

1. Global Configuration -Add the **global configuration** to the environment file. 🔗 [unified-uat.yaml](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/unified-uat.yaml). This ensures the **Campaign Module services and UI** are available across environments (e.g., UAT, QA, Prod).
2. Helm Chart Configuration - Update the Helm charts for the frontend to include **Workbench-UI** (used for Campaign workflows). 🔗 [Chart.yaml](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/charts/frontend/workbench-ui/Chart.yaml). This defines the Helm deployment setup for the Workbench UI, which powers the Campaign management console.

To understand environment setup and Helm deployments in detail, refer here:\
👉 [Setup Environment Guide](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env/deploy-as-code/helm/environments/unified-uat.yaml)

## Localisation

Refer to the different **localisation modules** to manage screen texts, labels, error messages, and schema headers. For the **Campaign Module**, the following modules are relevant:

<table><thead><tr><th width="275.46875">Module</th><th>Use</th><th data-hidden></th></tr></thead><tbody><tr><td>rainmaker-common</td><td>For all common screen localisation messages like login, homepage, sidebar </td><td></td></tr><tr><td>rainmaker-campaignmanager</td><td>For all console-related screens localisation messages  </td><td></td></tr><tr><td><p>rainmaker-hcm-admin-schemas</p><p></p></td><td>For all upload schemas like target, facility, user</td><td></td></tr><tr><td>boundary-${BOUNDARY_HIERARCHY_TYPE}</td><td>For boundary type localisations, we get this BOUNDARY_HIERARCHY_TYPE from the MDMS</td><td></td></tr></tbody></table>

