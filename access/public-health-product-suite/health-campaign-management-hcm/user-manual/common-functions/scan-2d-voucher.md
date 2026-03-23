---
description: An illustrative guide to using the Voucher Scanning feature
---

# Scan 2D Voucher

## Overview

The 2D voucher scanning feature supports voucher scanning for Beneficiary Registration, Service Delivery and Bed Net verification use cases.&#x20;

## Key Features

* Enables actors to execute the registration and delivery process efficiently through the use of scanners.
* Code scanning capability provides a better user experience by auto-populating the data, thus reducing the time and effort.
* Allows manual entry of codes to ensure maximum data collection, with defined validations.
* Prevents duplication of records and monitors resources by linking beneficiaries to their respective codes and reusing them while registering a new beneficiary or distributing resources. One can also monitor the quantity of stock distributed by scanning the code available on the stock.
* Allows multiple scanning of resources at once.

## User Roles

| User Role               | Scope of Action                                                                                                                                                                                                                       | Role Description                                                                                                                                        |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Registrars/Distributors | <ul><li>Scan and link vouchers to households during registration</li><li>Enter the voucher code manually</li><li>Scan and retrieve household details to deliver intervention</li><li>Scan the resource code during delivery</li></ul> | Provide direct healthcare services, communicate SBCC information, and support to communities. Usually operate in teams and within a specified boundary. |
| Warehouse Managers      | <ul><li>Scan the stock resource cards while receiving (Can be used for other transactions but is not preferred)</li><li>Scan multiple resources at once.</li><li>Enter the code manually</li></ul>                                    | A warehouse manager is responsible to manage the stock and record all the transactions that take place within the assigned warehouse/facility.          |

## Steps&#x20;

{% hint style="info" %}
**Note:** After logging into the application, the user lands on this screen, which displays the daily performance (number of households registered). The progress bar must reset daily at 00:00 hours and start from 0 registrations. The action buttons related to the beneficiary include:

* Beneficiaries
* View Reports
* Sync Data
* Call Supervisor
* File Complaint

At the bottom, there is a card that shows how many records are unsynced for the user’s convenience to sync data. If all the records are synced, then the card must say: “All records are synced”.
{% endhint %}



* Click on the **Scan QR code** button on the **Search Households** screen.

{% columns %}
{% column %}
<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.23.39 AM.png" alt="" width="188"><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.25.10 AM.png" alt="" width="188"><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

* Scan the **Voucher Code** provided to the beneficiary during registration. Alternatively, users can click on the **Enter Beneficiary Code** button to manually enter the voucher code.&#x20;

<div align="left"><figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.40.05 AM.png" alt="" width="188"><figcaption></figcaption></figure></div>

* This opens the beneficiary card with a set of actions for the scanned beneficiary.&#x20;
* Click on the close button to close the scanner if needed.

### Link Voucher To Individual

To link the beneficiary -

* Click on the **Link Voucher to Individual** button to link the beneficiary to the voucher card provided during registration.
* The voucher is linked successfully, and the voucher code is displayed on the screen.

{% columns %}
{% column %}
<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.44.22 AM.png" alt="" width="188"><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.46.33 AM (1).png" alt="" width="188"><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

### Track Delivery Resource

While delivering any resource to the beneficiary, the user must scan the code provided on the resource package.

To track a delivery resource -

* Scan the code available on the resource package.

{% hint style="info" %}
**Note:** The user can perform multiple scans at a time, but the number must not exceed the value provided by the user in the “Quantity Distributed” field.
{% endhint %}

* The scanner screen has an expandable card that provides the list of resources scanned. The card displays the count of resources scanned along with the identification number for each scanned resource.&#x20;

{% columns %}
{% column %}
<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.57.16 AM.png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.58.49 AM.png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

* In case one is unable to scan, the user can enter the codes manually, but after every code, they have to click on the **Enter Beneficiary Code** again and repeat the process.&#x20;

{% columns %}
{% column %}
<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 11.59.53 AM.png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 12.00.01 PM.png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

* Click on the **Delete** button to remove any resource.&#x20;

{% columns %}
{% column %}
<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 12.06.18 PM.png" alt=""><figcaption></figcaption></figure>



<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 12.07.37 PM.png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}


<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 12.07.26 PM.png" alt=""><figcaption></figcaption></figure>



<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-07-19 at 12.10.18 PM (1).png" alt="" width="188"><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

* Click on the **Submit** button to navigate back to the **Deliver Intervention** screen.&#x20;
* The toast message for a successful scan is displayed on the screen.
