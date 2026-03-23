# Boundary Details - Selection

In this step, the user will encounter 2 screens:

* Boundary Details
* Boundary Details Summary

## Boundary Details

This screen allows users to select the boundaries according to their requirements.

<figure><img src="../../../../../../.gitbook/assets/image (16).png" alt=""><figcaption><p>Boundary details</p></figcaption></figure>

The working of this screen is given below.

The system fetches the boundary data according to the hierarchy saved in the MDMS.

The file where data is fetched - [https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/Module.js](https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/Module.js)

The hierarchy structure and the lowest boundary will be fetched from the MDMS&#x20;

```
HCM-ADMIN-CONSOLE.HierarchySchema
```

For more information on the master data, refer [here](../../../../../../access/public-health-product-suite/health-campaign-management-hcm/hcm-console/).&#x20;

File Path - [https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/SelectingBoundariesDuplicate.js](https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/SelectingBoundariesDuplicate.js)

Which internally calls the - Selecting boundary component&#x20;

{% embed url="https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/SelectingBoundaryComponent.js" %}

**Validation:** \
The user must select boundaries down to the lowest level. If the parent boundary is selected, then the user should select at least one of the child options.

#### Summary

<figure><img src="../../../../../../.gitbook/assets/image (17).png" alt=""><figcaption><p>Summary</p></figcaption></figure>

This screen displays all the boundaries selected in the previous step.

### Localisation Details

Boundary localisation for this screen happens by using the combination of hierarchy type and boundary type

```
 {t((hierarchyType + "_" +boundaryType).toUpperCase())}
```

**It should be in the above-given format.**

### **API Details**

<table><thead><tr><th width="397.94140625">EndPoint</th><th>Role </th></tr></thead><tbody><tr><td>boundary-service/boundary-relationships/_search</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>/boundary-service/boundary-hierarchy-definition/_search</td><td>CAMPAIGN_MANAGER</td></tr><tr><td></td><td></td></tr></tbody></table>
