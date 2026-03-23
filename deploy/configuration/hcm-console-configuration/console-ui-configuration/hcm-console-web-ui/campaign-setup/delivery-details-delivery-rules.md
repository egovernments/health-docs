# Delivery Details - Delivery Rules

In the Delivery Details step, users encounter 3 screens:

* Cycles & Deliveries
* Delivery Screen
* Summary

## **1. Cycle Configuration Screen** &#x20;

On this screen, users specify the number of cycles and deliveries. The number of cycles must be at least 1 and can be up to 5. Once the user has defined the number of cycles and deliveries, they can proceed to enter the start and end dates for each cycle.

The number of cycles and deliveries is configurable based on project type. We can configure it in MDMS. [Click here](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/health/project-types.json) to access the JSON file.

If data is configured, a user will see the number of cycles and deliveries as per the configuration. A user, however, can increase or decrease if they find it necessary.

<figure><img src="../../../../../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

The validations added for the start date and the end date of the cycles should not overlap to each other. [Click here](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/CycleConfiguration.js) to access the config file.&#x20;

After filling in all the cycle details, a user can click on Next and move to the delivery rules screen. Clicking on Next enables a user to store the cycle data in the local storage.

## **2. Delivery Screen**&#x20;

On this screen, users fill in all the delivery details (adding delivery rules, adding conditions in delivery rules, and adding products in the delivery rules) of each cycle and delivery that the user has selected in the cycle details screen.&#x20;

The delivery screen can also be configured based on project type. A user can configure the number of delivery conditions, their attributes, and products. If the data is configured correctly, a user can see the data preloaded in delivery rules, and the user can change, remove, or add if they find it necessary.

<figure><img src="../../../../../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

A user can add up to 5 delivery rules. A user can add conditions in each delivery rule with attribute options having height, weight, gender, and age. For the Project type, the LLIN-mz configuration is passed in the delivery rules, in which two fixed attributes are present for the bednet campaign.

<figure><img src="../../../../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

After filling in all the delivery rules details, when a user clicks on next, the data will be stored in the localStorage as well as in the draft API. The delivery rules data will be validated in the preview screen.

Reference files:

* [Click here](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/SetupCampaign.js) to access the file.&#x20;
* [Click here ](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/deliveryRule/index.js)to access the Delivery rules screen config file.
* [Click here](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/SetupCampaign.js) to access the API call file.&#x20;

### Select / Create Product

If you click on configure resources on the delivery screen, a pop-up appears where a user can either select or create a product:

Product Screen: When a user clicks on "Add Products to be Delivered", a pop-up screen will appear with a list of product variants where a user can add the products and the number of counts in the delivery rules.

<figure><img src="../../../../../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

A user can add multiple products to the product screen after clicking on "add more resources" When the user clicks on confirm resources, products will be added to the delivery rules. The user can remove the products as well.

<figure><img src="../../../../../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

If the product is not present, a user can click on "Add New Product" to create a new product and variant, and subsequently add delivery rules. Clicking on "Add New Product" will open the Create Product screen.

<figure><img src="../../../../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

Users can enter product names, product variants, and product types which are sourced from MDMS data. Additionally, a user can create multiple products using the "Add Products" button. After clicking on 'Confirm,' the product will be created, followed by the creation of product variants.

After successful creation, users will be directed to a success response screen.

<figure><img src="../../../../../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

## 3. Summary

This screen will show the values the user has added in the cycle configuration screen and delivery screen.

<figure><img src="../../../../../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

## Setup Delivery Configuration

[Here](/broken/pages/HOE2bIXaoPn6bibfTTpA#id-1.-project-type-configuration) you can find the config of delivery based on project type, and the same acts as the default template.

This MDMS schema is used to fetch the details for every product type. To convert the data to the required format used by the screen, we are writing the util.

File Path: [https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/utils/getDeliveryConfig.js](https://github.com/egovernments/DIGIT-Frontend/blob/console/health/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/utils/getDeliveryConfig.js)

&#x20;The following is the structure for the delivery configuration:

<details>

<summary>Sample Config</summary>

````
```json
{
      "projectType": "MR-DN",
      "attrAddDisable": false,
      "deliveryAddDisable": false,
      "customAttribute": true,
      "cycleConfig": {
        "cycle": 3,
        "deliveries": 2
      },
      "deliveryConfig": [
        {
          "attributeConfig": [
            {
              "key": 1,
              "label": "Custom",
              "attrType": "dropdown",
              "attrValue": "Age",
              "operatorValue": "GREATER_THAN",
              "value": 10
            },
            {
              "key": 2,
              "label": "Custom",
              "attrType": "dropdown",
              "attrValue": "Height",
              "operatorValue": "LESS_THAN",
              "value": 50
            }
          ],
          "productConfig": [
            {
              "key": 1,
              "count": 1,
              "value": "PVAR-2024-05-15-000044",
              "name": "Paracetamol - 500mg"
            }
          ]
        },
        {
          "attributeConfig": [
            {
              "key": 1,
              "label": "Custom",
              "attrType": "dropdown",
              "attrValue": "Age",
              "operatorValue": "IN_BETWEEN",
              "toValue": 10,
              "fromValue": 20
            }
          ],
          "productConfig": [
            {
              "key": 1,
              "count": 1,
              "value": "PVAR-2024-05-15-000044",
              "name": "Paracetamol - 500mg"
            }
          ]
        }
      ]
    }
```
````

</details>

* projectType: This will be the type of the project. If the selected project type is present in the MDMS, then we use that config. &#x20;
* attrAddDisable: if this is true, we are restricting a user that they cannot add any attribute.
* deliveryAddDisable: if this is true, a user cannot add any further delivery rule conditions.
* cycleConfig: This will be an object containing cycles and deliveries. This refers to the number of cycles and deliveries that will be shown on the cycle screen.

```
 "cycleConfig": {
        "cycle": 3, //no of cycle
        "deliveries": 2 // no of deliveries
      },
```

* deliveryConfig: This will be an array of objects, each object representing one delivery condition.

````
```
"deliveryConfig": [
        {
          "attributeConfig": [ // this represent each attribute in a condition
            {
              "key": 1, // this should be always in sequential order
              "label": "Custom",  // this should be always set to custom
              "attrType": "dropdown", // this represnt the type of component
              "attrValue": "Age", // this is the value of the attribute which show in the attribute component
              "operatorValue": "GREATER_THAN", // this is operator value, it will show in operator component
              "value": 10 // this is the value which will show in value input component
            },
            ....
          ],
          "productConfig": [
            {
              "key": 1, // this will be always in sequential order
              "count": 1, // represent the count of the product
              "value": "PVAR-2024-05-15-000044", // variant id of the product. We need to be careful before adding the id that it should be present in the database 
              "name": "Paracetamol - 500mg" // name should always be adding using "{productName} - {variant}"
            }
          ]
        },
```
]
````

Adding product config is a careful job, adding the wrong product in the config will cause issues while creating a product.

In Value, the product variant ID should be added in the value which will be getting in the below API:`product/variant/v1/_search`

The name will consist of the name of the product and the variant of the product separated with "-"

for name: `product/v1/_search`

for variant: `product/variant/v1/_search`

FilePath:&#x20;

[https://github.com/egovernments/DIGIT-Frontend/tree/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/deliveryRule](https://github.com/egovernments/DIGIT-Frontend/tree/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/deliveryRule)

[https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/AddProduct.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/pages/employee/AddProduct.js)

## Reference links:

**MDMS:**&#x20;

Attribute:  [https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/attributeConfig.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/attributeConfig.json)

Operator: [https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/operatorConfig.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/operatorConfig.json)

Product Type: [https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/productType.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/hcm-admin-console/productType.json)&#x20;

**HOOKS:**&#x20;

[https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useCreateProduct.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useCreateProduct.js)

[https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useCreateProductVariant.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useCreateProductVariant.js)

[https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useProductList.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useProductList.js)

[https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useUpdateCampaign.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/hooks/useUpdateCampaign.js)

### New changes

We have added the **Delivery type** at each delivery condition showing the delivery type of the campaign.

It is configurable in mdms for the SMC project type. We can add a default delivery type for each condition.

<details>

<summary>Sample config</summary>

````
```javascript
deliveryConfig: [
      {
        delivery: 1,
        conditionConfig: [
          {
            deliveryType: "DIRECT",
            attributeConfig: [
              {
                key: 1,
                label: "Custom",
                attrType: "dropdown",
                attrValue: "Age",
                operatorValue: "IN_BETWEEN",
                fromValue: 3,
                toValue: 11,
              },
            ],
            productConfig: [
              {
                key: 1,
                count: 1,
                value: "PVAR-2024-01-24-000079",
                name: "AQ - 75mg",
              },
              {
                key: 1,
                count: 1,
                value: "PVAR-2024-05-03-000305",
                name: "SP - 250mg",
              },
            ],
          },
          {
            deliveryType: "DIRECT",
            attributeConfig: [
              {
                key: 1,
                label: "Custom",
                attrType: "dropdown",
                attrValue: "Age",
                operatorValue: "IN_BETWEEN",
                fromValue: 12,
                toValue: 59,
              },
            ],
            productConfig: [
              {
                key: 1,
                count: 1,
                value: "PVAR-2024-01-24-000078",
                name: "AQ - 150mg",
              },
            ],
          },
        ],
      },
      {
        delivery: 2,
        conditionConfig: [
          {
            deliveryType: "INDIRECT",
            attributeConfig: [
              {
                key: 1,
                label: "Custom",
                attrType: "dropdown",
                attrValue: "Age",
                operatorValue: "IN_BETWEEN",
                fromValue: 3,
                toValue: 11,
              },
            ],
            productConfig: [
              {
                key: 1,
                count: 1,
                value: "PVAR-2024-01-24-000079",
                name: "AQ - 75mg",
              },
            ],
          },
          {
            deliveryType: "INDIRECT",
            attributeConfig: [
              {
                key: 1,
                label: "Custom",
                attrType: "dropdown",
                attrValue: "Age",
                operatorValue: "IN_BETWEEN",
                fromValue: 12,
                toValue: 59,
              },
            ],
            productConfig: [
              {
                key: 1,
                count: 1,
                value: "PVAR-2024-01-24-000078",
                name: "AQ - 150mg",
              },
            ],
          },
        ],
      },
      {
        delivery: 3,
        conditionConfig: [
          {
            deliveryType: "INDIRECT",
            attributeConfig: [
              {
                key: 1,
                label: "Custom",
                attrType: "dropdown",
                attrValue: "Age",
                operatorValue: "IN_BETWEEN",
                fromValue: 3,
                toValue: 11,
              },
            ],
            productConfig: [
              {
                key: 1,
                count: 1,
                value: "PVAR-2024-01-24-000079",
                name: "AQ - 75mg",
              },
            ],
          },
          {
            deliveryType: "INDIRECT",
            attributeConfig: [
              {
                key: 1,
                label: "Custom",
                attrType: "dropdown",
                attrValue: "Age",
                operatorValue: "IN_BETWEEN",
                fromValue: 12,
                toValue: 59,
              },
            ],
            productConfig: [
              {
                key: 1,
                count: 1,
                value: "PVAR-2024-01-24-000078",
                name: "AQ - 150mg",
              },
            ],
          },
        ],
      },
    ],
```
````

</details>

deliveryConfig: It will contain the default data of all deliveries.

conditionConfig: It will contain the default data of each delivery condition of each delivery.

deliveryType: Default value of delivery type.&#x20;

### API Details

<table><thead><tr><th width="462">End Point</th><th>Role</th></tr></thead><tbody><tr><td>product/variant/v1/_search</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>product/v1/_search</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>product/v1/_create</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>product/variant/v1/_create</td><td>CAMPAIGN_MANAGER</td></tr><tr><td>project-factory/v1/project-type/update</td><td>CAMPAIGN_MANAGER</td></tr></tbody></table>
