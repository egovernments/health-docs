---
description: >-
  Supports voucher scanning use cases for Beneficiary Registration, Service
  Delivery and Bed Net verification use cases
---

# 2D Voucher Scanning

## Table of Contents

[Background](2d-voucher-scanning.md#background)

[Target Audience](2d-voucher-scanning.md#target-audience)

[Objectives (of this release)](2d-voucher-scanning.md#objectives-of-this-release)

[Assumptions and Validations](2d-voucher-scanning.md#assumptions-and-validations)

[Process flow](2d-voucher-scanning.md#process-flow)

[Specifications](2d-voucher-scanning.md#specifications)

[Design](2d-voucher-scanning.md#design)

## Background

This document describes the need and scope of including the 2D code scanning feature within V2.0, explaining the module’s features, specifications, purpose, and functionality. It also provides the descriptive view of the application along with the specification of each element.

## Target Audience

This document is intended for the engineering and platform (tech teams), product management, and implementation teams to agree on requirements for the Health Campaign Management (HCM) Platform.&#x20;

## Objectives (of this release)

1. Improve accessibility:&#x20;

&#x20;      \- By enabling actors to execute the registration and delivery process efficiently through the use of scanners.

2. Enhance User Experience:

&#x20;      \- Code scanning capability provides better user experience by auto populating the data, thus reducing the time and effort.&#x20;

3. Prevent duplication of records and monitor resources:

&#x20;     \- Linking beneficiaries to their respective codes and reusing it while registering a new beneficiary or distributing resources.

&#x20;    \- Monitoring the quantity of stock distributed by scanning the code available on the stock.

## Assumptions and Validations

<table data-header-hidden><thead><tr><th width="91"></th><th width="179"></th><th></th></tr></thead><tbody><tr><td>Sr. No.</td><td>Theme </td><td>Assumption</td></tr><tr><td>1.</td><td>Device used</td><td>The device is a smartphone with sufficient camera quality and flashlight to scan the code.</td></tr><tr><td>2.</td><td>Linking beneficiary to voucher</td><td><ol><li>Registration vouchers are provided to beneficiaries during household registration/ individual registration, and act as a temporary ID for the campaign.</li><li>The user scans and links the beneficiary to the voucher.</li></ol></td></tr><tr><td>3.</td><td>Scan QR to search beneficiary</td><td>The actors will use scanners frequently to search the beneficiary and deliver intervention.</td></tr><tr><td>4.</td><td>Tracking resource delivery</td><td>The resource has a code provided on the packaging. The distributor must scan those codes while distributing resource to the beneficiary.</td></tr></tbody></table>

## Process flow

![](https://lh3.googleusercontent.com/XN65nA0VqmTGBA9dGw9IHjsIvrtQjFgQDi67mSWrZzyqDXTX9UeiPu1dUsoDKfXnY3SlHHgvsvnhMQUbv0CyydIUpXO\_q9NCGL\_wVnR6ubEW9gzWqqAiETaFiSqUNDjXyoIDU4WMaYycG-tsfZsebXQ)

## High level requirements

1. The HCM flutter mobile application must support an in-app 1D and 2D code scanner launched within the application to scan codes. The following use cases have been identified for implementation in various contexts.
2. QR code scanning: Use case to scan registration or delivery vouchers to be used to redeem benefits (bed nets) by households.
   1. Registration vouchers are provided to beneficiaries during household registration/ individual registration and act as a temporary ID for the campaign.
   2. FLW teams can scan these vouchers to retrieve beneficiary data to provide a benefit or use for longitudinal tracking in a multi-round campaign.
3. Bar codes and 2D [Data matrix](https://en.wikipedia.org/wiki/Data\_Matrix): Use case for supply chain (Global fund traceNet project) to track the individual bed net that is distributed to the household.
   1. Bar code or data matrix on the nets are linked to the delivery record created against the household to track which net was distributed (coupled with GPS and timestamp, this data verifies that the exact net was delivered to which beneficiary, when and where).
4. The application must support scanning from live camera input and from existing images from gallery.
5. The bar code module must support features like flashlight control (in case of low light settings).
6. In case the code is not scannable, an option to skip or manually enter the barcode must be supported.
7. Haptic feedback must be provided, either in the form of vibration or sound, upon successful scan for user’s understanding (Good to have).
8. Toast message upon successful scan must be displayed.
9. App must audit and log all the scanned barcodes and sync this data along with the HCM transaction created (possible changes to the API in case of use case #b above).
10. The scanned code must be associated with the HCM app transaction calling the bar code function. For example:
    1. For registration voucher, the code scanned must be linked to the individual/household head as their temporary ID.
    2. For resource delivery verification, the scanned code must be linked to the service delivery transaction.
11. Upon scanning a code, on the search household screen, the application must use the code scanned to search and retrieve details of beneficiaries.
12. &#x20;The scanner must enable batch scanning.
    1. Ability to assign multiple codes to one transaction.&#x20;
    2. Use case: If the distributor needs to deliver 3 bed nets to a household, the scanner must be able so scan 3 bar codes or data matrixes and link to the delivery transaction.
    3. Scanner must be able to identify duplicate scans- If the user scans multiple items and repeats one, then the scanner must show a message that the item is already scanned.
    4. Scanner must take the “quantity distributed” for resources from the delivery intervention screen and allow the user to scan only x number of resources.- Validation.
13. &#x20;Support landscape and portrait orientations.
14. The application must provide feedback or error messages if barcode scanning fails due to low lighting or camera issues.

## Specifications

| Field                                      | Data type | Data validation                                                                                                                                           | Required (Y/N) | Comments                                                                                                                                                                                                                    |
| ------------------------------------------ | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Beneficiary List                           | List      | Last registered beneficiary to be displayed first                                                                                                         | Y              | The list of beneficiaries registered within the application.                                                                                                                                                                |
| Scan QR code (Search beneficiary)          | Scanner   | <ol><li>Search for a beneficiary by scanning the code</li><li>User can also enter the code if the scanner does not work</li></ol>                         | NA             | Upon scanning the code, it opens the beneficiary card.                                                                                                                                                                      |
| Scan QR code (Link beneficiary to voucher) | Scanner   | <ol><li>Linking a beneficiary to the voucher code</li><li>Can be entered manually as well</li></ol>                                                       | NA             | On individual details screen, the user links the beneficiary to a voucher code for reusing the data in future.                                                                                                              |
| Scan QR code (Track the delivery resource) | Scanner   | <ol><li>Scan the code available on the resource packaging. </li><li>Can scan multiple codes at a time.</li><li>Can be entered manually as well.</li></ol> | NA             | <p>While delivering resources to the beneficiary, the distributor must scan the code for tracking the resources. It must scan multiple resources at a time.</p><p>The scan count must not exceed the quantity provided.</p> |

## Design

Find the mock-ups below:&#x20;

### HCM Home Screen&#x20;

After logging into the application, the user lands on this screen which displays the daily performance (number of households registered). The progress bar must reset daily at 00:00 hours and start from 0 registrations. The action buttons related to the beneficiary include:

* Beneficiaries
* View Reports
* Sync Data
* Call Supervisor
* File Complaint

At the bottom, there is a card that shows how many records are unsynced for the user’s convenience to sync data. If all the records are synced, then the card must say: “All records are synced”.

The help button is on every screen of the application. By clicking on it, a user can get a walkthrough of the elements on that screen.

On the top right, the administrative area assigned to the user is displayed which is based on the level of hierarchy. The hamburger button on the top left corner covers some other actions mentioned further.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 10.50.43 AM.png" alt=""><figcaption></figcaption></figure>

### Search Beneficiary Screen

On this screen, a user can search for a registered beneficiary or register a new one. There are multiple options included to search for a beneficiary: search by name, proximity, and scan a code. The metrics card shows the data for beneficiaries registered and the number of resources delivered, depending on the type of campaign.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.23.39 AM.png" alt=""><figcaption></figcaption></figure>

### Scan Code (Search Beneficiary)

Clicking on the scan button on the search household screen opens a scanner that allows a user to scan the voucher code provided to the beneficiary during registration. The user can also enter the code manually by clicking on the “Enter Beneficiary Code” button, if the device is unable to scan.

Based on the campaign type, the beneficiary card is opened with a set of actions for the scanned beneficiary. The user can close the scanner if needed by clicking on the close button.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.25.10 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.40.05 AM.png" alt=""><figcaption></figcaption></figure>

### Scan Code (Linking Beneficiary)

While creating a beneficiary, the user can link the beneficiary to the voucher card provided during registration by clicking on the “Link Voucher to Individual” button. If the scanner is not able to scan the code, the user can also enter the details manually. Screens for the scanner are same as that for search beneficiary.

On successful scanning, the toast message appears over the individual details screen and the voucher code is displayed. In case the scanned code does not match with the one mentioned in the voucher, the user can click on the edit button and rescan or re-enter the code. The previously scanned value must be overwritten by the latest one (No multiple scanning to be done).

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.44.22 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.45.31 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.46.33 AM (1).png" alt=""><figcaption></figcaption></figure>

### Age Field

The age field must be displayed in months and years on the following screens: beneficiary table on search household screen, beneficiary details screen, and household card, for children below 1 year. On the individual details screen, the age field must have separate fields to capture in years and months. There must be a validation to restrict the user from entering months less than 12. It must show an error message (similar to that for years).

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.52.29 AM.png" alt=""><figcaption></figcaption></figure>

### Scan Code (Track Delivery Resource)

While delivering any resource to the beneficiary, the user must scan the code provided on the packaging of the resource. The scanner must be able to identify duplicate scans and must not scan the same voucher multiple times. The user can perform multiple scans at a time, but the number must not exceed the value provided by the user in the “Quantity Distributed” field.

The scanner screen has an expandable card that provides the list of resources scanned. The card displays the count of resources scanned along with the identification number for each scanned resource. If one is unable to scan, the user can enter the codes manually, but after every code, he/she must click on the enter beneficiary code again and repeat the process. The user can remove any resource by the help of the delete button provided against each resource. Once scanned, the user must click on the submit button which brings him back to the deliver intervention screen. The toast message for successful scan is displayed on the screen.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.57.16 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.58.49 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.59.53 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 12.00.01 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 12.06.18 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 12.07.26 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 12.07.37 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-19 at 12.10.18 PM (1).png" alt=""><figcaption></figcaption></figure>
