# Stock Management

### 1. Overview

The **Stock Management screen** in the DIGIT HCM app enables users to manage medical or inventory stock items within healthcare facilities. The screen provides capabilities for adding, updating, tracking, and viewing stock levels, as well as recording stock transactions (such as receipts, issues, and transfers). The goal is to ensure transparency, traceability, and effective management of health-related inventories.

***

### 2. Workflow Details

* The home screen contains 2 options - Manage Stock and Stock Reconciliation.

<div align="left"><figure><img src="../../../.gitbook/assets/image (246).png" alt="" width="288"><figcaption></figcaption></figure></div>

**Manage Stock** screen -&#x20;

This screen consists of the following types of transactions that take place for the inventory:

* Stock Receipt
* Stock Issued
* Stock Returned
* Stock Damaged
* Stock Loss

<div align="left"><figure><img src="../../../.gitbook/assets/image (247).png" alt="" width="288"><figcaption></figcaption></figure></div>

**Stock Receipt screen -**

* When a user clicks on record stock receipt, the warehouse details screen will appear.
* The latitude/longitude captures the geo-location of the warehouse, which can be fetched with the help of the location icon within the field.

<div align="left"><figure><img src="../../../.gitbook/assets/image (248).png" alt="" width="288"><figcaption></figcaption></figure></div>

* Clicking on the Next button navigates the user to the "Received Stock" details screen.

<div align="left"><figure><img src="../../../.gitbook/assets/image (249).png" alt="" width="288"><figcaption></figcaption></figure></div>

* The "Receipt Stock Details" form has some mandatory fields: product, received from the warehouse, and quantity received.
* The optional fields include waybill number, quantity indicated on the waybill, transport type, vehicle number, and comments.
* Clicking on the submit button will take the user to the success page.

**Record Stock Issued**

* This screen captures the mandatory fields: Product, Issued to warehouse, and the quantity.
* The optional fields include waybill number, quantity indicated on waybill, transport type, vehicle number and comments.
* Clicking on the submit button will go to the success page.

<div align="left"><figure><img src="../../../.gitbook/assets/image (250).png" alt="" width="288"><figcaption></figcaption></figure></div>

**Returned Stock Details**

This screen captures the mandatory fields: Product, returned to warehouse, and quantity returned.

The optional fields are waybill number, quantity indicated on the waybill, transport type, vehicle number, and comments.

Clicking on the **Submit** button will take the user to the success page.

<div align="left"><figure><img src="../../../.gitbook/assets/image (251).png" alt="" width="288"><figcaption></figcaption></figure></div>

**Damaged Stock Details**

* This screen captures the mandatory fields: Product, damaged during, received from, and quantity damaged.
* The optional fields include waybill number, quantity indicated on the waybill, transport type, vehicle number, and comments.
* Clicking on the submit button will take he user to the success page.

<div align="left"><figure><img src="../../../.gitbook/assets/image (252).png" alt="" width="288"><figcaption></figcaption></figure></div>

**Lost Stock Details**

This screen captures the mandatory fields: Product, lost during, received from, and quantity lost.

The optional fields are Waybill Number, quantity indicated on the waybill, transport type, vehicle number, and comments.

Clicking on the **Submit** button will take the user to the success page.

<div align="left"><figure><img src="../../../.gitbook/assets/image (253).png" alt="" width="288"><figcaption></figcaption></figure></div>

### Stock Reconciliation <a href="#stock-reconciliation" id="stock-reconciliation"></a>

* When the user clicks on the stock reconciliation button on the home screen, he/she is navigated to this screen where he/she needs to verify whether the physical count and calculated stock values are the same or not.
* In the select product field, the user needs to select a product from the dropdown.
* There are warehouse name and administrative area fields as well, all of which are mandatory.

<div align="left"><figure><img src="../../../.gitbook/assets/image (254).png" alt="" width="288"><figcaption></figcaption></figure></div>

***

### 3. Technical Implementation

* **MDMS Configuration**
  * Stock item master data, stock categories, and relevant dropdowns are configured in MDMS under appropriate modules (e.g., `StockItem`, `StockCategory`).
  * UI reads master data via the MDMS API to populate dropdowns and options.
* **UI Components**
  * Implemented using React (or similar frameworks) as modular components:
    * Stock Dashboard/List (table/grid)
    * Stock Transaction Forms (Add, Issue, Transfer, Adjust)
    * Stock Detail and History views
  * Validation and error handling for all form fields.
  * File upload support for transaction documents (if applicable).
* **State Management**
  * Use Redux (or context API) to manage stock state, transaction drafts, and API responses.
  * Filters and pagination for lists.
* **Localization**
  * All labels, messages, and dropdown options are localised using the localisation service.
* **Sample API Integrations**
  * Fetch stock: `/stock/v1/_search`
  * Create receipt: `/stock/v1/_create`
  * Update stock: `/stock/v1/_update`
  * Stock transactions: `/stock/transaction/v1/_create`
* **Navigation Logic**
  * After each transaction (create/update/transfer), the user is redirected to the dashboard or item detail with a success message.
  * Errors and validation issues are displayed inline.
* Code References
  * [digit\_divider.dart](https://github.com/egovernments/DIGIT-UI-LIBRARIES/blob/master/flutter/digit-ui-components/digit_components/lib/widgets/atoms/digit_divider.dart)
  * [input\_wrapper.dart](https://github.com/egovernments/DIGIT-UI-LIBRARIES/blob/master/flutter/digit-ui-components/digit_components/lib/widgets/atoms/input_wrapper.dart)
  * [label\_value\_list.dart](https://github.com/egovernments/DIGIT-UI-LIBRARIES/blob/master/flutter/digit-ui-components/digit_components/lib/widgets/atoms/label_value_list.dart)
  * [pop\_up\_card.dart](https://github.com/egovernments/DIGIT-UI-LIBRARIES/blob/master/flutter/digit-ui-components/digit_components/lib/widgets/atoms/pop_up_card.dart)
  * [digit\_card.dart](https://github.com/egovernments/DIGIT-UI-LIBRARIES/blob/master/flutter/digit-ui-components/digit_components/lib/widgets/molecules/digit_card.dart)
  * [show\_pop\_up](https://github.com/egovernments/DIGIT-UI-LIBRARIES/blob/master/flutter/digit-ui-components/digit_components/lib/widgets/molecules/show_pop_up.dart)

***

### 4. API Role Action Mapping

* **Relevant APIs and Actions:**
  * `/stock/v1/bulk/_search` — Fetch the required stock item details

```
{
  "RequestInfo": {
    "authToken": "string"
  },
  "Stock": {
    "id": [
      "string"
    ],
    "clientReferenceId": [
      "string"
    ],
    "facilityId": "FacilityA",
    "productVariantId": "string",
    "referenceId": "C-1",
  }
}
```

* `/stock/v1/bulk/_create` — Add new stock&#x20;

```
{
  "RequestInfo": {
    "authToken": "string"
  },
  "Stock": [
    {
      "clientReferenceId": "string",
      "tenantId": "tenantA",
      "facilityId": "FacilityA",
      "productVariantId": "string",
      "quantity": 0,
      "wayBillNumber": "string",
      "referenceId": "C-1",
      "referenceIdType": "PROJECT",
      "transactionType": "RECEIVED",
      "transactionReason": "RECEIVED",
      "transactingPartyId": "string",
      "transactingPartyType": "WAREHOUSE",
    }
  ]
}
```

* `/stock/v1/bulk/_update` — Update existing stock&#x20;

```
{
  "RequestInfo": {
    "authToken": "string"
  },
  "Stock": [
    {
      "id":"UUID"
      "clientReferenceId": "string",
      "tenantId": "tenantA",
      "facilityId": "FacilityA",
      "productVariantId": "string",
      "quantity": 0,
      "wayBillNumber": "string",
      "referenceId": "C-1",
      "referenceIdType": "PROJECT",
      "transactionType": "RECEIVED",
      "transactionReason": "RECEIVED",
      "transactingPartyId": "string",
      "transactingPartyType": "WAREHOUSE",
    }
  ]
}      
```

* `/stock/reconciliation/v1/bulk/_create` — Record stock transactions&#x20;

```
{
  "RequestInfo": {
    "authToken": "string"
  },
  "StockReconciliation": [
    {
      "clientReferenceId": "string",
      "tenantId": "tenantA",
      "facilityId": "FacilityA",
      "productVariantId": "string",
      "referenceId": "C-1",
      "referenceIdType": "PROJECT",
      "physicalCount": 0,
      "calculatedCount": 0,
      "commentsOnReconciliation": "string",
      "dateOfReconciliation": 1663218161,
      "rowVersion": 0
    }
  ]
}
```

* `/stock/reconciliation/v1/_search` — Fetch reconciled stock details

```
{
  "RequestInfo": {
    "authToken": "string"
  },
  "StockReconciliation": {
    "id": [
      "string"
    ],
    "clientReferenceId": [
      "string"
    ],
    "facilityId": "FacilityA",
    "productVariantId": "string"
  }
}
```

*   **Role-Action Mapping Example:**

    ```
    [
      { "rolecode": "STOCK_MANAGER", "actionid": 2010, "tenantId": "default" }, // /stock/v1/_search
      { "rolecode": "STOCK_MANAGER", "actionid": 2011, "tenantId": "default" }, // /stock/v1/_create
      { "rolecode": "STOCK_MANAGER", "actionid": 2012, "tenantId": "default" }, // /stock/v1/_update
      { "rolecode": "STOCK_MANAGER", "actionid": 2013, "tenantId": "default" }, // /stock/transaction/v1/_create
      { "rolecode": "ANONYMOUS", "actionid": 1001, "tenantId": "default" },     // /mdms/v1/_search
      { "rolecode": "ANONYMOUS", "actionid": 1002, "tenantId": "default" }      // /localization/messages/v1/_search
    ]
    ```

{% hint style="info" %}
**Notes:**

* Ensure all actions are included and enabled in the MDMS action master.
* Map necessary roles (e.g., `STOCK_MANAGER`, `ADMIN`, etc.) to each API action for detailed access control.

This allows a user to manage stocks and also facilitates stock reconciliation.
{% endhint %}
