# Inventory Management: Last Mile Delivery

## Table of Contents

[Background](inventory-management-last-mile-delivery.md#background)

[Target Audience](inventory-management-last-mile-delivery.md#target-audience)

[Objectives (of this release)](inventory-management-last-mile-delivery.md#objectives)

[Assumptions and Validations](inventory-management-last-mile-delivery.md#assumptions-and-validations)

[Process flow](inventory-management-last-mile-delivery.md#process-flow)

[Specifications](inventory-management-last-mile-delivery.md#specifications)

[Design](inventory-management-last-mile-delivery.md#design)

## Background

This document describes the need and scope of adding a module for tracking resources till the last mile delivery within V2.0, explaining the module’s features, specifications, purpose, and functionality. It also provides the descriptive view of the application along with the specification of each element.

In health campaigns, it is crucial to keep track of the resources delivered to prevent stock mis-handlings and for maximising the coverage. The form helps to track the resource till the last mile delivery, that is, it captures the stock till it reaches the distributor, and the distributor can record the quantity of stock received along with other stock transactions.

## Target Audience

This document is intended for the engineering and platform (tech teams), product management and implementation teams to agree on requirements for the Health Campaign Management Platform (HCM).

## Objectives (of this release)

1. Tracking stock till the last mile
2. Capture stock details till the end user to keep a track of the transactions that take place
3. Enable actors to record the stock transactions during a campaign
4. Ensure the safety of stock
5. Keep a track of the stock count and verify from both ends (received versus issued) to prevent the misuse of stocks&#x20;

## Assumptions and Validations

<table data-header-hidden><thead><tr><th width="82"></th><th width="204"></th><th></th></tr></thead><tbody><tr><td>Sr. No.</td><td>Theme </td><td>Assumption</td></tr><tr><td>1</td><td>Manage Stock</td><td><ol><li>The distributor must record the stock details that is received, consumed, returned, or damaged/lost.</li><li>The distributor must enter the supervisor details in case the stock is issued by him/her.</li><li>For v2, stock used will be automatically calculated from the delivery transactions only if the SKU of the resource received from the warehouse is the same as the SKU distributed to the beneficiary. For example, if a field team received bed nets from the upstream and distributed the same unit (that is, bed nets), the app will automatically calculate the stock used. However, if the drug received from the warehouse is in a box and drug distributed are individual capsules/ tablets, the app will not automatically calculate usage.</li><li>Turning off the auto-calculation logic must be done during the implementation phase.</li></ol></td></tr></tbody></table>

## Process flow

![](https://lh3.googleusercontent.com/M5rbJrVwbalDWgDpY6T3cKvKjon6-Ga-3HHeqzmX1Pmeuy9t4-KmJ-t2-wB5q3eYlGcKMNnc4azdF0UC4gA5kV\_UrrBKchEqfozLQYShcHVtdxuTmhTqjMDBClfzdlO2YZCLcBrHQNrGSIYiiycLDbA)

## Specifications

| Field               | Data type             | Data validation                                                                                               | Required (Y/N) | Comments                                                   |
| ------------------- | --------------------- | ------------------------------------------------------------------------------------------------------------- | -------------- | ---------------------------------------------------------- |
| Manage stock        | Button                | The user must record the stock transaction.                                                                   | NA             | <p><br></p>                                                |
| Date of receipt     | Date                  | <p>The date is populated by the system and must be non-editable.<br>Applicable for all transaction types.</p> | Y              | <p><br></p>                                                |
| Administrative unit | String                | The unit is populated by the system and must be non-editable.                                                 | Y              | The user can change the boundary from the boundary picker. |
| Team identifier     | String                | The system must populate the identifier from the user’s profile and it must be editable.                      | Y              | <p><br></p>                                                |
| Select product      | Dropdown              | <p><br></p>                                                                                                   | Y              | <p><br></p>                                                |
| Received from       | Search-based dropdown | <p><br></p>                                                                                                   | Y              | <p><br></p>                                                |
| Supervisor’s name   | String                | If the stock is received from a supervisor, enter his/her name.                                               | Y              | <p><br></p>                                                |
| Quantity received   | Numeric               | <p><br></p>                                                                                                   | Y              | <p><br></p>                                                |
| Comments            | String                | <p><br></p>                                                                                                   | N              | <p><br></p>                                                |

## Design

Find the mock-ups below:

### HCM Home Screen

After logging into the application, the user lands on this screen which displays daily performance (number of households registered). The progress bar must reset daily at 00:00 hours, and start from 0 registrations. The action buttons related to the beneficiary are present  which include:

* Beneficiaries
* View Reports
* Sync Data
* Call Supervisor
* File Complaint
* Manage Stock

On the bottom, there is a card that shows how many records are unsynced for the user’s convenience to sync data. If all the records are synced, then the card must say “All records are synced”.

The help button is on every screen of the application, and by clicking on it, a user can get a walkthrough of the elements on that screen.

On the top right, the administrative area assigned to the user is displayed which will be based on the level of hierarchy.

The hamburger button on the top left corner covers some other actions mentioned further.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-17 at 10.07.42 AM.png" alt=""><figcaption></figcaption></figure>

### Manage Stock&#x20;

This includes all the stock transactions that can be captured by the distributor.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-17 at 10.09.24 AM.png" alt=""><figcaption></figcaption></figure>

### Transaction Details

The transaction details are captured on this screen. The date and administrative unit fields are auto captured by the system and are non-editable. The team code/identifier is captured from the user profile and it must be editable.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-17 at 10.10.57 AM.png" alt=""><figcaption></figcaption></figure>

### Received Stock Details&#x20;

The stock related details are captured on this screen. “Select product” is a dropdown field that includes the resource that has been received. “Received from” is a search-based dropdown field, clicking on which navigates the user to the search facility screen that includes the facilities along with ‘Supervisor’ as the value. If the user selects ‘Supervisor’ then he/she must enter the supervisor’s name. The user must enter the quantity received, and if any additional comments are needed, they can be added.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-17 at 10.14.17 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-17 at 10.17.29 AM.png" alt=""><figcaption></figcaption></figure>

### Acknowledgement Screen

Once the user clicks on ‘Submit’, the confirmation pop-up appears. If the user clicks on the ‘Submit’ button, the acknowledgement screen appears and ‘Cancel’ takes the user back to the previous screen.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-17 at 10.19.12 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-17 at 10.19.22 AM.png" alt=""><figcaption></figcaption></figure>

### Transaction Details (Stock Consumed)

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-17 at 10.21.08 AM (1).png" alt=""><figcaption></figcaption></figure>

### Consumed Stock Details&#x20;

This screen includes all the fields except for the facility field.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-17 at 10.23.24 AM.png" alt=""><figcaption></figcaption></figure>

### Transaction Details (Stock Returned)

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-17 at 10.24.38 AM.png" alt=""><figcaption></figcaption></figure>

### Returned Stock Details

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-17 at 10.25.24 AM.png" alt=""><figcaption></figcaption></figure>
