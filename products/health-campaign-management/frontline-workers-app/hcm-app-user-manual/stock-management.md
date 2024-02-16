# Stock Management

## Overview

This enables a user to manage stocks, besides facilitating stock reconciliation.

## User actions

On this page, the following actions can be performed:

* After a successful login as a warehouse manager, a user lands on the home screen which consists of "Manage Stock", and "Stock Reconciliation".-&#x20;

![](<../../../../.gitbook/assets/image (20) (1).png>)

### Manage Stocks

This screen consists of the following types of transactions that take place for the the inventory:

* Stock Receipt
* Stock Issued
* Stock Returned
* Stock Damaged
* Stock Loss

![](<../../../../.gitbook/assets/image (19) (1).png>)

#### Stock Receipt

* When a user clicks on record stock receipt, the warehouse details screen will appear.
* The latitude/longitude captures the geo-location of the warehouse which can be fetched with the help of the location icon within the field.

![](<../../../../.gitbook/assets/image (13) (1).png>)

* Clicking on the next button will navigate the user to the "Received Stock" details screen.&#x20;

![](<../../../../.gitbook/assets/image (24) (1).png>)\


* The "Receipt Stock Details" form has some mandatory fields: product, received from warehouse, and quantity received.&#x20;
* The optional fields include waybill number, quantity indicated on waybill, transport type, vehicle number, and comments. &#x20;
* Clicking on the submit button will take the user to the success page.

#### Record Stock Issued

* This screen captures the mandatory fields: Product, Issued to warehouse, and the quantity.&#x20;
* The optional fields include waybill number, quantity indicated on waybill, transport type, vehicle number and comments. &#x20;
* Clicking on the submit button will go to the success page.

![](<../../../../.gitbook/assets/image (2) (1).png>)\


#### Returned Stock Details

This screen captures the mandatory fields: Product, returned to warehouse, and quantity returned.&#x20;

The optional fields are waybill number, quantity indicated on waybill, transport type, vehicle number, and comments. &#x20;

Clicking on the submit button will take the user to the success page.

![](<../../../../.gitbook/assets/image (12) (1).png>)\
\


#### Damaged Stock Details

* This screen captures the mandatory fields: Product, damaged during, received  from, and quantity damaged.
* The optional fields include waybill number, quantity indicated on waybill, transport type, vehicle number, and comments. &#x20;
* Clicking on the submit button will take he user to the success page.

![](<../../../../.gitbook/assets/image (4) (1).png>)

#### Lost Stock Details

This screen captures the mandatory fields: Product, lost during, received from, and quantity lost.&#x20;

The optional fields are wWaybill Number, quantity indicated on waybill, transport type, vehicle number, and comments. &#x20;

Clicking on the submit button will take the user to the success page.

![](<../../../../.gitbook/assets/image (11) (1).png>)\
\


## Stock Reconciliation

* When the user clicks on the stock reconciliation button on the home screen, he/she is navigated to this screen where he/she needs to verify whether the physical count and calculated stock values are the same or not.&#x20;
* In the select product field, the user needs to select a product from the dropdown.&#x20;
* There are warehouse name and administrative area fields as well, all of which are mandatory.&#x20;

![](<../../../../.gitbook/assets/image (22) (1).png>)

## API details

<table><thead><tr><th width="206.33333333333334">End Point</th><th width="149">Request Method</th><th>Request Info</th></tr></thead><tbody><tr><td>/stock/v1/bulk/_create</td><td><code>POST</code></td><td><pre class="language-json"><code class="lang-json">{
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
</code></pre></td></tr><tr><td>/stock/v1/bulk/_update</td><td>POST</td><td><pre class="language-json"><code class="lang-json">{
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
</code></pre></td></tr><tr><td>/stock/v1/bulk/_search</td><td>POST</td><td><pre><code>{
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
</code></pre></td></tr><tr><td>/stock/reconciliation/v1/bulk/_create</td><td>POST</td><td><pre><code>{
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
</code></pre></td></tr><tr><td>/stock/reconciliation/v1/_search</td><td>POST</td><td><pre><code>{
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
</code></pre></td></tr></tbody></table>

File Path : [https://github.com/egovernments/health-campaign-field-worker-app/tree/master/apps/health\_campaign\_field\_worker\_app/lib/pages/inventory](https://github.com/egovernments/health-campaign-field-worker-app/tree/master/apps/health\_campaign\_field\_worker\_app/lib/pages/inventory)\
