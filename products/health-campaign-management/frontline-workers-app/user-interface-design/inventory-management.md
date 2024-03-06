# Inventory Management

Find the mockups below:

### Home Screen

After successful login, a user lands on the home screen of inventory management which consists of the following actions and elements:

* Manage Stock
* Stock Reconciliation
* View Reports
* Sync Data
* Call Supervisor
* File Complaint

There is a location picker on the top right that displays the assigned boundary for the user. The help button provides a walkthrough of the screen to the user. The hamburger button on the top left consists of a few quick actions. The location picker, help button, and hamburger buttons are available on every screen for a user’s convenience.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_234328.jpg" alt="" width="188"><figcaption></figcaption></figure>

### Hamburger Button

After clicking on the hamburger button, a list of actions appears on the user screen. On top, it displays the user name and contact number, followed by other options such as the home button, language select, edit profile, projects, and logout. The “Edit Profile” option is not in scope for V1; it needs to be taken in V1.1 If the user clicks on the hamburger button again, it collapses the hamburger menu. The button is available on all screens of the application.

<figure><img src="../../../../.gitbook/assets/IMG_20230515_112143.jpg" alt="" width="188"><figcaption></figcaption></figure>

### Manage Stocks

This screen consists of different types of transactions that take place for the inventory. These include:

* Stock Receipt
* Stock Issued
* Stock Returned
* Stock Damaged
* Stock Loss

Every transaction has a separate card with an arrow button, an icon, and a brief description below the title. Clicking on the arrow button will navigate the user to the warehouse details screen. The back button is located below the hamburger button, which takes the user to the previous screen (In this case, it is the home screen).

<figure><img src="../../../../.gitbook/assets/IMG_20230513_234201.jpg" alt="" width="188"><figcaption></figcaption></figure>

### Error Popup

If the user is not assigned any warehouse, then an error popup must appear over the warehouse details screen, asking the user to contact the system administrator to assign a warehouse. The user must be able to close the popup and change the administrative area on the warehouse details screen to check if he/she is assigned any warehouse in any other boundary. This must force the screen to load again and check for the warehouse.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-17 at 4.01.28 PM.png" alt=""><figcaption></figcaption></figure>

### Warehouse Details (Stock Receipt)

When the user clicks on record stock receipt, the warehouse details screen will appear. The latitude/longitude captures the Geo-location of the warehouse which can be fetched with the help of the location icon within the field. It is a mandatory field denoted by \*. The warehouse name/ID is a dropdown field which contains the list of warehouses assigned to the project for a particular user. If there is only one warehouse, the field must be auto-populated by the system.

The date of receipt field captures the date of transaction which can be fetched with the help of a calendar icon placed inside the box. The field must be validated, where the date cannot be in the future. If the user puts a future value, it must show an error message stating “date cannot be in future”. The user must select the administrative unit from the dropdown of the administrative unit field. The next button navigates the user to the stock receipt details screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_234216.jpg" alt="" width="188"><figcaption></figcaption></figure>

### Received Stock Details

The user must provide details of the stock received. The select product field has a dropdown that consists of all the products under a campaign. The user can select from the list the desired product that he has received. The type of transaction is provided to specify whether the stock is being received, issued, or returned.

In the ‘received from’ section, the user needs to select from the dropdown the warehouse from which the stock is being received. The dropdown must contain the list of all the warehouses that are part of the campaign, that is, the list must be of the warehouse assigned to the root project. The list is taken from the facility registry and must be the same for all the transactions. The quantity received field collects the information for how much quantity of stock is being received.

<figure><img src="../../../../.gitbook/assets/Android - 497 (1).png" alt=""><figcaption></figcaption></figure>

For a pack of a certain number of nets, there is a packing slip attached to the packet which indicates the number of nets within that pack. The user needs to mention the value in the number of nets field.

The total number of packing slips must be mentioned in the following field. The user can add any comments/remarks in the additional comments field. The following - select product, type of transaction, received from, and quantity received fields - are mandatory for this screen. When the user has entered all the details, he must click on the submit button which leads to the confirmation screen whether the record has been created successfully or there are some errors.

### Confirmation Screen

When the user clicks on the submit button, he/she lands on this page with the confirmation message “Record created Successfully”. Users can go back to the home screen by clicking on the “Back To Home” button. This screen must appear for every other transaction (issued, returned, damaged, lost, reconciliation).

<figure><img src="../../../../.gitbook/assets/IMG_20230513_234704 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

### Warehouse Details (Stock Issued)

When the user clicks on record stock issued, the warehouse details screen will appear. The screen is similar to the stock receipt one. The only difference is that instead of the date of receipt, the field is the date of issue. The next button navigates the user to the stock issued details screen.

<figure><img src="../../../../.gitbook/assets/Android - 495.png" alt="" width="180"><figcaption></figcaption></figure>

### Issued Stock Details

The user needs to provide details for the stock issued. The select product field acts the same as that for stock receipt. In the destination field, the user needs to select the warehouse where the stock is being sent.  The quantity sent field collects the information on how much quantity of stock is being sent. When the user has entered all the details, he must click on the submit button which leads to the confirmation screen whether the record has been created successfully or there are some errors.

<figure><img src="../../../../.gitbook/assets/Android - 581.png" alt="" width="180"><figcaption></figcaption></figure>

### Warehouse Details (Stock Returned)

When the user clicks on stock returned, the warehouse details screen appears. The fields are similar to that for stock receipt; only the date of receipt label is changed to the date of return. The next button navigates the user to the stock returned details screen.

<figure><img src="../../../../.gitbook/assets/Android - 495 (1).png" alt="" width="180"><figcaption></figcaption></figure>

### Stock Returned Details

The user needs to provide details for the stock returned. The “Select product” field acts the same as that for stock receipt. In the “Returned from” field, the user needs to select the warehouse from where the stock has been returned.  The “Quantity returned” field collects the information for how much quantity of stock has been returned. When the user has entered all the details, he/she must click on the submit button which leads to the confirmation screen that confirms whether the record has been created successfully or there are some errors.

<figure><img src="../../../../.gitbook/assets/Android - 582.png" alt="" width="180"><figcaption></figcaption></figure>

### Warehouse Details (Stock Damaged)

For the damaged stock, the user must provide the details asked on the screen.

<figure><img src="../../../../.gitbook/assets/Android - 495 (2).png" alt="" width="180"><figcaption></figcaption></figure>

### Damaged Stock Details

The user needs to provide the details for the damaged stock. There can be two cases for the damaged stock:

1. If the stock is damaged during transit, then the user must select the warehouse name from where the stock was received.
2. If the stock is damaged during storage, then the user must select N/A from the dropdown.

<figure><img src="../../../../.gitbook/assets/Android - 570 (1).png" alt="" width="180"><figcaption></figcaption></figure>

### Warehouse Details (Stock Loss)&#x20;

The user needs to provide the details for the lost stock.

<figure><img src="../../../../.gitbook/assets/Android - 495 (3).png" alt="" width="180"><figcaption></figcaption></figure>

### Lost Stock Details

The user must provide the details for the stock loss.

<figure><img src="../../../../.gitbook/assets/Android - 583.png" alt="" width="180"><figcaption></figcaption></figure>

### **Bale Scanning:**

**Overview:**&#x20;

Scan the resource code to track the resources delivered

1. Package utilised to parse the barcode : [https://pub.dev/packages/gs1\_barcode\_parser](https://pub.dev/packages/gs1\_barcode\_parser).&#x20;
2. Package utilised  to QR code scanner:   [https://pub.dev/packages/qr\_code\_scanner](https://pub.dev/packages/qr\_code\_scanner)
3. GS1 - standards :   [https://www.gs1.org/docs/barcodes/GS1\_DataMatrix\_Guideline.pdf](https://www.gs1.org/docs/barcodes/GS1\_DataMatrix\_Guideline.pdf)&#x20;
4. Package utilised for barcode scanning

[https://pub.dev/packages/google\_mlkit\_barcode\_scanning](https://pub.dev/packages/google\_mlkit\_barcode\_scanning)

```
google_mlkit_barcode_scanning
```

Given a field value formatted with the GS1 data matrix standard and a string key from the GS1 application identifiers. The function should look and return the value linked to the provided key.

A well-formatted value would look like:

]d20108470006991541211008199619525610DXB200517220228

<div align="left">

<figure><img src="../../../../.gitbook/assets/Screenshot_20231008-132327.png" alt="" width="188"><figcaption></figcaption></figure>

</div>

Stock Reconciliation

When the user clicks on the stock reconciliation button on the home screen, they are navigated to this screen where they need to verify whether the physical count and calculated stock values are the same or not. In the select product field, the user needs to select a product from the dropdown. There are warehouse name and administrative area fields as well, all of which are mandatory. The following details are there:

* Date of Reconciliation
* Received Stock&#x20;
* Issued Stock
* Returned Stock
* Damaged Stock
* Stock Lost
* Stock on Hand- The stock on hand is calculated as incoming stock minus outgoing stock. There is a hint icon for how the stock on hand is calculated. The received and returned stocks will be considered incoming stocks. The issued, damaged and lost stocks will be considered outgoing stocks.

The date of reconciliation is system-generated and non-editable. Other values are calculated based on the data recorded in stock receipts, stock issued, and the stock returned screens. In the manual stock count, the user needs to enter the value for manually counted inventory. If the stock on hand does not match the physical count, then the latter must take precedence, provided the user has submitted the form with a proper reason. In the comments field, the user can add remarks and comments.

<figure><img src="../../../../.gitbook/assets/Android - 497 (2).png" alt="" width="180"><figcaption></figcaption></figure>

### View Reports (Scope for v1.1)

When a user clicks on the view reports button on the home screen, he/she is navigated to this page where he/she has the provision to view the following reports:

* Stock Received
* Stock Issued
* Stock Returned
* Stock Reconciliation

Users can click on the arrow button placed next to every transaction to open the respective report. The back button will navigate them back to the home screen.

<figure><img src="../../../../.gitbook/assets/Android - 578.png" alt="" width="180"><figcaption></figcaption></figure>

### Report (Stock Received)

When the user clicks on the “Stock Received” button, the report for stock received appears which provides a tabular representation of the data. The table is scrollable, both vertically and horizontally, to cater to multiple values and columns. The date column is kept frozen and other columns are scrollable. The first column is for the date of the receipt, followed by units received in the second column, and received from (warehouse name) in the third column. The “Back To Home” button is placed at the bottom of the screen which navigates the user back to the home screen.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-17 at 4.48.32 PM.png" alt=""><figcaption></figcaption></figure>

### Report (Stock Reconciliation)

For the stock reconciliation report, the table consists of the date in the first column and other columns. The “Back To Home” button will navigate users to the home screen.

<figure><img src="../../../../.gitbook/assets/Android - 501.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Frame 675.png" alt=""><figcaption></figcaption></figure>
