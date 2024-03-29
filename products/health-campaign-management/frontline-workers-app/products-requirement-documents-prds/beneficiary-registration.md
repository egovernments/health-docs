# Beneficiary Registration

## Table of Contents

Background

Target Audience

Objectives (of this release)

Assumptions and Validations

Out of Scope

Specifications

Design

Success Criteria

Metrics to Track

## Background

This document describes the need and scope of a digital platform for health campaigns, explaining the product’s features, specifications, purpose, and functionality for beneficiary registration. It also provides a descriptive view of the application along with the specification of each element within the flow.

## Target Audience

The document is intended for the engineering and platform (tech teams), product management, and implementation teams to agree on the requirements for the Health Campaign Management Platform (HCM).

## Objectives (of this release)

1. To enable actors with a digital system to manage and implement health campaign activities.&#x20;

&#x20;      a. Facilitate FLWs, supervisors, district officers, and other actors to collect and analyse data accurately, along with monitoring registration tasks. Regular progress checks can also be performed at any time and a comparative analysis can be derived at the district levels for different teams in terms of beneficiaries registered.

2. To increase the adoption of the HCM platform for multiple health campaigns by providing flexibility in the UI and UX as well as product specifications.

&#x20;      a. Emphasis on adopting digital systems by collaborating with several healthcare initiative bodies.

&#x20;      b. Provide scope for future changes and improvements in the upcoming versions of the application.

Assumptions and Validations

<table><thead><tr><th width="253">Theme</th><th>Assumption</th></tr></thead><tbody><tr><td>Customer persona</td><td><ul><li>The actors using the application are not digitally literate and need training before they can use the application independently.</li></ul></td></tr><tr><td>Device and services</td><td><ul><li>The actors have a smartphone and there should be internet connectivity to enable syncing of data from the mobile application to the server for populating the dashboards.</li><li>The actors using the mobile application must sync at least once daily.</li><li>Logging into the application needs internet connectivity.</li></ul></td></tr><tr><td>Identifiers for individuals</td><td><ul><li>The type of identifiers and their validations must be configured during implementation. If there is no ID collected during registration, the system will generate a unique ID while persisting the record into the registry.</li></ul></td></tr><tr><td>Registration of households and individuals</td><td><ul><li>A household can be created only if there is at least one individual associated with the household.</li><li>Only one member within the household can be marked as the household’s head, which is the first member being registered.</li><li>A user will be able to register a new household only after attempting a search (the register button will be disabled until the search is completed).</li></ul></td></tr><tr><td>Peer-to-peer sync</td><td><ul><li>For v1.0, the product will not support peer-to-peer sync, either by directly syncing phones or routing traffic through the server.</li></ul></td></tr><tr><td>Location picker</td><td><ul><li>The user must select at least the highest boundary to proceed with registration and delivery.</li></ul></td></tr><tr><td>Date of birth</td><td><ul><li>The system captures only the date at the backend, irrespective of whether the user enters the date of birth or age.</li><li>For date of birth, the system captures the exact date, and for age (eg 23), the date must be 01-01-2000.</li><li>The reason why the system captures only the date is that in health campaigns, the approximate age can be used for providing interventions. The exact age is required in periodic campaigns, where an individual’s dosage depends upon his age, gender, height, weight, and other factors. Another reason for capturing the date is that it is easier to update the age for future use cases.</li><li>The date of birth must be validated to restrict the users from entering a future date value.</li></ul></td></tr><tr><td>Additional fields</td><td><ul><li>All the non-mandatory fields must be taken care of during implementation. This must be done across all the flows.</li></ul></td></tr></tbody></table>

## Risk/Limitations&#x20;

* Addressed in the out-of-scope section.

## Out of scope&#x20;

* Search and view beneficiaries on the map based on proximity.&#x20;
* Filter and sort beneficiaries.&#x20;
* Generate QR codes for registered beneficiaries.&#x20;
* Edit the user profile.

## Specifications

<table><thead><tr><th width="177">Field</th><th width="181">Data type</th><th width="186">Data validation</th><th>Required (Y/N)</th><th width="296">Comments</th><th></th></tr></thead><tbody><tr><td>Location picker</td><td>Dropdown</td><td>Select at least the highest boundary.</td><td>Y</td><td>The area boundary assigned to a specific user.</td><td></td></tr><tr><td>Search for a household</td><td>String</td><td>Search by the household head.</td><td>Y</td><td>After 2 characters, it will start showing related search results.</td><td></td></tr><tr><td>Administrative area</td><td>String</td><td>NA</td><td>Y</td><td>The administrative boundary of the household. Auto-populated by the system and it is non-editable.</td><td></td></tr><tr><td>Address line 1</td><td>Alphanumeric</td><td>Min. length: 2.  Max. length: 64.</td><td>N</td><td>Household address.</td><td></td></tr><tr><td>Address line 2</td><td>Alphanumeric</td><td>Min. length: 2. Max. length: 64.</td><td>N</td><td>Additional information of the address.</td><td></td></tr><tr><td>Landmark</td><td>String</td><td>Min. length: 2. Max. length: 64.</td><td>N</td><td>Additional landmark to help locate the household.</td><td></td></tr><tr><td>Postal code</td><td>String</td><td>Min. length: 2. Max. length: 64.</td><td>N</td><td>Postal code of the house. </td><td></td></tr><tr><td>Lat</td><td>Numeric</td><td>Min. value: -90. Max. value: 90.</td><td>N</td><td>Latitude of the household.  It is fetched by the system.</td><td></td></tr><tr><td>Long</td><td>Numeric</td><td>Min. value: -180 Max. value: 180.</td><td>N</td><td>Longgitude of the household. It is fetched by the system.</td><td></td></tr><tr><td>Date of registration</td><td>Date</td><td>Cannot be in the future.</td><td>N</td><td>The date when a new beneficiary is registered. It is fetched by the system and it is non-editable.</td><td></td></tr><tr><td>Number of members living in the household</td><td><p></p><p>Numeric:</p><p>Increment/decrement</p><p><br></p></td><td>Min. member: 1 Max. members: 1,000.</td><td>Y</td><td>The number of members living in a particular household. It is defaulted to 1.</td><td></td></tr><tr><td>Name of the individual</td><td>String</td><td>Min. length: 2 Max. length: 200.</td><td>Y</td><td>The name of the individual belonging to a particular household. It is captured from the search bar and is editable. The first name will be head of the household by default.</td><td></td></tr><tr><td>ID type</td><td>Dropdown</td><td>NA</td><td>Y</td><td>The ID type of the individual.</td><td></td></tr><tr><td>ID number</td><td>Alphanumeric</td><td>10-digit ID number.</td><td>Y</td><td>The ID number of the individual. If the individual does not have an ID, a system-generated ID will be provided.</td><td></td></tr><tr><td>Date of birth</td><td>Date</td><td>Cannot be in the future.</td><td>Y</td><td>The date of birth of the individual.</td><td></td></tr><tr><td>Age</td><td>Numeric</td><td>Min. length: 1. Max. length: 64.</td><td>Y</td><td>The age of the individual. The individual needs to provide either her/his age or date of birth. The date of birth takes precedence over age. If the date of birth is entered, the user must not be able to enter age.</td><td></td></tr><tr><td>Gender</td><td>Dropdown</td><td>NA</td><td>N</td><td>Gender of the individual.</td><td></td></tr><tr><td>Mobile number</td><td>Numeric</td><td>Length: 10 digits.</td><td>N</td><td>Mobile number of the individual if they have a mobile phone.</td><td></td></tr><tr><td>Reasoon for deletion</td><td>Select from the options</td><td>NA</td><td>Y</td><td>Select the reason for deleting the household/individual.</td><td></td></tr></tbody></table>

## Design

Find the mock-ups below:

### HCM Home screen

After logging into the application, the user lands on this screen which displays the daily performance (number of households registered). The progress bar must reset daily at 00:00 hours and start from 0 registrations.&#x20;

The action buttons related to the beneficiary are present, which include:&#x20;

* Beneficiaries
* Sync Data&#x20;
* Call Supervisor&#x20;
* File Complaint&#x20;

At the bottom, there is a card that shows how many records are unsynced for the user’s convenience to sync data. If all the records are synced, then the card must say “All records are synced”. The help button is on every screen of the application, clicking on which a user can get a walkthrough of the elements on that screen.&#x20;

On the top right, the administrative area assigned to the user is displayed, which will be based on the level of hierarchy. The hamburger button on the top left corner covers some other actions mentioned further.

<figure><img src="../../../../.gitbook/assets/IMG_20230512_232807 (2).jpg" alt="" width="375"><figcaption></figcaption></figure>

### Hamburger Menu

After clicking on the hamburger button, a list of actions appears on the user screen. The top displays the user name and contact number, followed by other options such as the home button, language select, edit profile, projects, and logout. The ‘Edit Profile’ option is not in scope for V1, it needs to be taken in V1.1

If the user clicks on the hamburger button again, it collapses the hamburger menu. The button is available on all screens of the application.

<figure><img src="../../../../.gitbook/assets/IMG_20230512_232739.jpg" alt="" width="375"><figcaption></figcaption></figure>

### Edit Profile

The user can edit his/her name, and phone number, and select the gender. After updating the details, the user needs to click on the save button which opens a prompt stating “saved successfully”.&#x20;

If the user does not want to make any changes, he/she can click on the back button, which will take them back to the hamburger menu. Not in scope for V1.0, needs to be taken in V1.1.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-02-22 at 2.27.44 PM.png" alt=""><figcaption></figcaption></figure>

### Project Selection

When a user clicks on the projects option in the hamburger menu, it navigates them to the project selection screen, from where the user can select another project to work on.

Though the automatic sync is triggered by the login action, after selecting another project, the system must now sync the data for the new project, and the same flow must be followed.

<figure><img src="../../../../.gitbook/assets/IMG_20230512_232548.jpg" alt="" width="188"><figcaption></figcaption></figure>

### Location

For a user assigned multiple boundaries, after logging in, the boundary selection overlay must appear. This forces the user to select a boundary, only after which the user will be able to view the home screen. The user can then change the boundary whenever required from the location picker placed on the top right.

It has dropdown fields to select the boundary, which depends on the hierarchy level of the user. For example, in the case of an FLW, the boundary selection starts from the administrative post. The values in the dropdown are linked to the higher hierarchy and the user cannot select a boundary if the previous field is left blank.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000401.jpg" alt="" width="188"><figcaption></figcaption></figure>

The dropdown must only consist of the boundaries that are assigned to the user, not all the boundaries under a particular hierarchy. For example, if the user is assigned localities 1, 2, and 3, and there are 5 localities in all under admin post 1, then the dropdown must have only 1, 2, and 3 localities.&#x20;

At least the highest boundary must be selected to enable the select button, which navigates the user to the home screen. For multiple projects, sync needs to download the data only for the selected project.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000418.jpg" alt="" width="188"><figcaption></figcaption></figure>

### Help Button&#x20;

If the user clicks on the help button, it will give a walkthrough of the entire screen, including the role of each button placed with two buttons:&#x20;

* Skip: If the user wants to skip the walkthrough at any point.&#x20;
* Next: It will proceed to the next action aligned.&#x20;

The text box appears at the bottom of the button.

<figure><img src="../../../../.gitbook/assets/IMG_20230512_232704.jpg" alt="" width="375"><figcaption></figcaption></figure>

### Search Households

When a user clicks on the ‘Beneficiaries’ button, they will be navigated to this screen. It displays the number of households registered along with the number of bednets delivered in that administrative area.

The register button is primarily disabled to ensure that the user performs the search action.

The search bar allows the user to search by the household head’s name and the system provides the search results. The minimum string length to show results is 2 characters and the order of the results will be the last record displayed first. Two cases can be generated:

1. No results are displayed.
2. The search results displayed do not match.

Both cases are discussed further. The ‘Back’ button on the top will navigate to the home screen.

<figure><img src="../../../../.gitbook/assets/Android - 518.png" alt="" width="180"><figcaption></figcaption></figure>

### Case 1: No match found&#x20;

If a user is searching for a household and there are no households registered by that name, it will display: “Match not found! Register New Household button to add details”. The register button is enabled to proceed with the household registration. When the user clicks on the “Register New Household” button, it takes them to the “Household Location” screen.

<figure><img src="../../../../.gitbook/assets/Android - 521 (1).png" alt="" width="180"><figcaption></figcaption></figure>

### Case 2: Results do not match&#x20;

If the user searches for a household by the name Jose, for example, all the household cards by the name Jose will be displayed. The cards will provide details such as the household name, members in the household, service delivery status, administrative area, and a dropdown arrow at the centre.&#x20;

The open button at the right corner of each card is for the user’s understanding to open the household card. The search results displayed must be 10 at a time followed by pagination for the next 10 results.&#x20;

At the end of the search results, a query message is displayed stating “Match not found” and the register button is enabled. If the results do not match, the user can click on the register button for household registration. The back button will take them to the home screen.

<figure><img src="../../../../.gitbook/assets/Android - 519 (1).png" alt="" width="188"><figcaption></figcaption></figure>

### Household Dropdown (for household-level campaigns)&#x20;

After the user searches for a household, the search results are displayed with a dropdown arrow. The dropdown has a significant circular area of touch response for the user. When the user clicks on the dropdown, it will expand and display the tabular data of all the members in that particular household. The table is scrollable, both vertically as well as horizontally, but the card dimension of the dropdown must remain fixed to show 5 members.&#x20;

The table must not display the household head icon ‘H’, as shown on the individual level screen. This will help the user to verify whether it is their household or not. In the beneficiary column, only the first 14 characters will be displayed.&#x20;

Since there are no separate fields for first name and last name, the cell will count 14 characters, counting space as 1 character. If it is the same household, the user can click on the ‘Open’ button on the card, which will open the household card. The ‘Back’ button will take the user to the home screen.

<figure><img src="../../../../.gitbook/assets/Android - 520.png" alt="" width="180"><figcaption></figcaption></figure>

### Household Dropdown (for individual-level campaigns)

In this case, a column for delivery status is added to the table. The format for the delivery status must be the same for every screen wherever the status needs to be displayed. The format is check mark+status. The household-level delivery status is omitted in this case.

<figure><img src="../../../../.gitbook/assets/Android - 554.png" alt="" width="180"><figcaption></figcaption></figure>

### Location

Household registration begins from this screen. The user needs to provide the location details of the household. The administrative area field must be auto-captured from the boundary selected, which is mandatory, denoted by \* and is non-editable. If the user wants to change the area, he/she can click on the location picker on the top, which opens the boundary selection screen.

The system must fetch the lat/long coordinates of the household. If it is unable to detect the coordinates, it will be left blank in the dashboard to avoid errors.&#x20;

The back button takes the user to the “List of Households”  screen. The ‘Next’ button at the bottom takes them to the “Household Details” screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000456.jpg" alt="" width="375"><figcaption></figcaption></figure>

### Household Details

The “Date of Registration” is auto-populated by the system, and is non-editable. The user provides the details on the total number of members in a particular household with the help of the increment/decrement buttons on both sides. The field must default to one and validation must be applied, where at least one member should be there in a household for registration.

After providing the numbers, the user clicks on the ‘Next’ button at the bottom of the screen, which will navigate them to the ‘Individual Details’ screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000508.jpg" alt="" width="375"><figcaption></figcaption></figure>

### Individual Details&#x20;

In the name field, the system fetches the name from the search action performed on the beneficiaries screen, which is editable. The first individual will be the head of the household by default, denoted by a checkbox below the field. The checkbox must be non-editable as the users are trained in such a way that the first member registered should always be the household head.&#x20;

The name, ID type, and ID number fields are kept mandatory for data collection. The ID type is a dropdown field where the individual must provide the type of ID they hold if any. The ID types must be configured in the MDMS.&#x20;

If the individual does not hold any ID, an option for ‘System generated ID’ must be there, which will inform the system to generate an ID for that individual. In “ID Number”, the user needs to enter the individual’s ID number. If the user selects a system-generated ID, then this field must be disabled. The system must capture the ID number when the device is online and sync can take place.

<figure><img src="../../../../.gitbook/assets/household edit (4).png" alt=""><figcaption></figcaption></figure>

The “Date of birth” is a calendar input field, where the individual’s birth date is entered. If the individual does not know his/her date of birth, there is an option to enter the age. The system captures only the date of birth at the backend, which is described in the two cases below:

1. If the user enters the date of birth,  the age field is disabled. The system captures the exact date entered.&#x20;
2. If the user has entered the age, the date of birth field must remain editable (date of birth takes precedence over age).
3. If age has been entered, the date captured by the system must be the first day of January and the year must be the difference between the current year and age. For example, if the user has entered the age 23, then the date captured must be 01-01-2000 (as of 2023).
4. During the edit flow, the application user must not see the system-derived date. This means that while creating the record, the user had input age and the system calculated the date of birth as 01-01-XXXX, but during the edit flow, only the data entered by the user while creating the record must be visible to the user.
5. If the user has entered age (Eg. 23) in the current year, the system must derive the date as 01-01-2000. After a year, during the edit flow, the age displayed must be 24 (incremented by 1 year).&#x20;

The date of birth field must be validated where the value cannot be in the future, and if a user has entered a future date, then an error message must appear stating the date cannot be in the future. Gender is a dropdown field to select the individual’s gender. The user needs to enter the mobile number of the individual if they have a mobile phone.

At the bottom, there is a ‘Submit’ button, clicking on which the user can register the beneficiary into the system. For every submit action, the system validates the information entered. If the user enters incomplete or incorrect data, clicking on the submit button will show an error message above it, along with the validated message below the field (as shown in the adjacent screen).

<figure><img src="../../../../.gitbook/assets/household edit (3).png" alt=""><figcaption></figcaption></figure>

### Confirmation Screen&#x20;

When the user clicks on the ‘Submit’ button, a popup appears asking for confirmation. If the user wants to edit any detail, they can click on the ‘Cancel’ button, which will take the user back to the previous screen. If the user clicks on ‘Submit’, the household is registered and the household card is opened.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000537.jpg" alt="" width="375"><figcaption></figcaption></figure>

### Acknowledgement Screen&#x20;

Once the user clicks on the submit button, the acknowledgement screen appears providing the information that the data has been recorded successfully. When the user clicks on “Back to Search”, he/she must be navigated to the search household screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000550.jpg" alt="" width="375"><figcaption></figcaption></figure>

### Household Card (for a household-level campaign)&#x20;

After registering the household, the user can search for the household and open the card. The household name is displayed as household only, to avoid the risk of names that may be longer. There is also an ‘Edit Household’ button for editing household details, which navigates the user to the household location screen.&#x20;

The service delivery status is present below the household’s name followed by the administrative area and the number of members. There are cards for each member, starting from the household head. The card consists of the member's name, gender, age, and the ‘Edit’ button for individual-level actions. Age will be denoted in years for this version, as for household-level campaigns, age is not a considerable parameter for providing interventions.&#x20;

For adding new members to the household, there is the ‘Add Member’ button below the member cards, which navigates the user to the ‘Individual Details’ screen. At the bottom, the ‘Deliver Intervention’ button navigates the user to the update delivery screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000606.jpg" alt="" width="375"><figcaption></figcaption></figure>

If the intervention is delivered to that household, the second screen will appear. The deliver intervention button must be replaced by the ‘Update Delivery Details’ button in case more interventions are needed to be delivered. The back button on top takes the user to the list of households screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_233658.jpg" alt="" width="375"><figcaption></figcaption></figure>

### Household Card (for an individual-level campaign)&#x20;

If the campaign is at an individual level, the household card appears in a similar format with some changes. The ‘Deliver Intervention’ button is present at the bottom of every member’s card. If the intervention is delivered to a member, it will display ‘Delivered’ below their details on the card and the button will be replaced with ‘Update Delivery Details’. If the intervention is not delivered, it will display “Not Delivered”. The ‘Deliver Intervention’ button in this case navigates the user to the update delivery screen. The back button navigates the user to the search households screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_233628.jpg" alt="" width="375"><figcaption></figcaption></figure>

Household-Level Actions When the user clicks on the “Edit Household” button, the actions appear on the screen.&#x20;

<figure><img src="../../../../.gitbook/assets/IMG_20230513_233712.jpg" alt="" width="375"><figcaption></figcaption></figure>

* Edit Household: The user is navigated to the household location screen followed by household details. In this screen, the ‘Next’ button is now replaced by the ‘Save’ button.&#x20;
* Delete Household: If the user wants to delete the entire household.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000659.jpg" alt="" width="375"><figcaption></figcaption></figure>

### Delete Household&#x20;

After a user clicks on the “Delete Household”’ button, an overlay appears with a message asking whether he/she wants to delete that beneficiary. It has two buttons: Delete: This will delete the beneficiary from the system records. Cancel: if the user does not want to delete the beneficiary, clicking on this button will collapse the overlay.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000713.jpg" alt="" width="188"><figcaption></figcaption></figure>

### Reason for Deletion (household)&#x20;

If a user selects the delete option, it will bring them to this screen, where he/she must select the reason for deleting a particular household. The screen will be the same as that of individual deletion, only the reasons will vary. The reasons may include the household having relocated, the household does not exist, etc. The reasons must be configured in the MDMS.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000727.jpg" alt="" width="375"><figcaption></figcaption></figure>

### Individual-Level Actions

When a user clicks on the ‘Edit’ button on an individual’s card, an overlay screen appears with the following actions:&#x20;

* Assign as household head: If the user wants to change the head of household, they can select this option and that member will be assigned as household head. The option must be disabled for the household head.
* Edit individual details: If the user wants to edit the member’s details. It will navigate them to the individual details screen and the same flow is to be followed.
* Delete individual: This option allows the user to delete a particular member. A user must not be able to delete the household head and hence the delete individual button must be disabled if the beneficiary is marked as the head of the household. If the user wants to delete the beneficiary marked as a household head,  the user must assign another member in the household as the head and then delete the beneficiary.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_233839.jpg" alt="" width="375"><figcaption></figcaption></figure>

### Edit Individual Details&#x20;

When a user clicks on edit individual details, he/she navigates to the individual details screen where he/she can edit the previously entered data. For edit flow, all the fields must be editable at the front end.&#x20;

For the date of birth and age fields, the date of birth must always be given precedence over age. If the user has entered the date of birth while creating an individual, only that field must be editable, and the age field must be disabled. If the user has entered age, then the age entered must be visible, and the date of birth field must be blank, but editable. If the user wants to enter the exact date of birth, then he/she must be able to enter the value, in which case the age field is disabled (as in create flow).

<figure><img src="../../../../.gitbook/assets/household edit (5).png" alt="" width="180"><figcaption></figcaption></figure>

### Delete Individual&#x20;

Clicking on the delete button opens a popup that asks whether the user wants to delete that member. If the user clicks on the delete button, it will proceed further to delete the member. If the user clicks on cancel, it will take him/her back to the household card.&#x20;

If the member is the household head, a popup should appear stating that deletion cannot happen unless some other member is assigned the household head. If there is only one member in a household, a popup should appear stating that there should be at least one member for creating a household. The user needs to either add another member or delete the entire household.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000744.jpg" alt="" width="188"><figcaption></figcaption></figure>

### Reason for Deletion (Individual)&#x20;

If the user selects the delete option, it will bring him/her to this screen, where he/she needs to select the reason for deleting a member. The reasons must be configured in the MDMS.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000752.jpg" alt="" width="375"><figcaption></figcaption></figure>

### Sync&#x20;

Before going into the field, the user needs to log into the application every day, which will initiate an automatic sync process (mentioned in the user login PRD). For manual sync, there is a ‘Sync Data’ button on the home screen, which allows the user to sync data according to his/her convenience. At the bottom of the screen, there is a card that shows the message “Data unsynced” along with the number of records unsynced.

<figure><img src="../../../../.gitbook/assets/IMG_20230512_232807.jpg" alt="" width="375"><figcaption></figcaption></figure>

When the user clicks on the ‘Sync’ button, the sync action starts along with an overlay showing “Sync in Progress” over the home page. The user cannot perform any other action until the sync is complete or there is some error.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000434.jpg" alt="" width="188"><figcaption></figcaption></figure>

### Sync Status&#x20;

Once the data is synced, it will show a popup, stating “Data Synced” along with a ‘Close’ button at the bottom. When the user clicks on close, it navigates him/her to the home screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000446.jpg" alt="" width="188"><figcaption></figcaption></figure>

If the data is not synced due to any error, it will show a popup stating “Sync Failed” with two buttons below it:&#x20;

1. Retry: If the user wants to retry syncing the data.&#x20;
2. Close: Clicking on this will navigate the user back to the home screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_233748.jpg" alt="" width="188"><figcaption></figcaption></figure>

### Reports&#x20;

The reports dashboard provides a tabular and visualised representation of user performance. The reports are not in V1.0 for mobile applications, except for the stock reconciliation. They are generated based on the offline data present in the local device, associated with the user’s login.&#x20;

If a user selects the ‘Data’ option, it will provide a data-wise report of the campaign. The bar graph shows the day-to-day comparison of registered beneficiaries along with a threshold of the daily target for registration. Below the graph, the table is added which displays the households registered as well as bednets distributed.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-02-27 at 4.48.01 PM.png" alt=""><figcaption></figcaption></figure>

In the leaderboard section, the overall number of households registered will be displayed in the form of a milestone. Below that, all the individual users’ performance will be listed separately. The leaderboard option will not be available at the registrar level (field level) but at the field supervisor level.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-02-27 at 4.49.52 PM.png" alt=""><figcaption></figcaption></figure>

### Call Supervisor&#x20;

If the user is facing any challenge and requires an immediate solution, he/she can click on the call supervisor button on the home screen, which will redirect them to their phone’s dial pad with the supervisor’s number auto-filled. By clicking on the ‘Call’ button, the user can contact the supervisor for immediate assistance.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_233810.jpg" alt="" width="188"><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-02-27 at 4.52.20 PM.png" alt=""><figcaption></figcaption></figure>

## Success Criteria

1. Various actors involved in the process will be able to collect, track, and analyse the data for beneficiaries registered using a bug-free platform.
2. The supervisors, district officers, and program managers will be able to monitor team performance, which will help them understand the problems and challenges faced by the teams.
3. Digital records will result in maximum coverage with fewer chances of households being missed during a certain campaign.

## Metrics to Track

The following metrics will be tracked:

1. Households registered.
2. Individuals registered in households.
