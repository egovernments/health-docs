# Service Delivery

Find the mock ups below:

### HCM Home screen

After logging into the application, the user lands on this screen which displays daily performance (the number of households registered). The progress bar must reset daily at 00:00 hours and start from 0 registration. The action buttons related to the beneficiary are present, which include:

* Beneficiaries
* View Reports
* Sync Data
* Call Supervisor
* File Complaint

At the bottom, there is a card that shows how many records are unsynced for the user’s convenience to sync data. If all the records are synced, then the card must say, “All records are synced”.

The help button is on every screen of the application. By clicking on this button, a user can get a walkthrough of the elements on that screen. On the top right, the administrative area assigned to the user is displayed which will be based on the level of hierarchy. The hamburger button on the top left corner covers other actions.

<figure><img src="../../../../.gitbook/assets/IMG_20230512_232807 (3).jpg" alt="" width="188"><figcaption></figcaption></figure>

### Hamburger Menu

After clicking on the hamburger button, a list of actions appears on the user screen. On top, it displays the user name and contact number, followed by other options such as the home button, language select, edit profile, projects, and logout. The “Edit Profile” option is not in scope for V1, it needs to be taken in V1.1.

If the user clicks on the hamburger button again, it collapses the hamburger menu. The button is available on all screens of the application.

<figure><img src="../../../../.gitbook/assets/IMG_20230512_232739 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

### Edit Profile

The user can edit his/her name, phone number, and select the gender. After updating the details, the user needs to click on the save button which opens a prompt stating “saved successfully”.&#x20;

If the user does not want to make any changes, he/she can click on the back button which will take him/her back to the hamburger menu. This is not in scope for V1.0; it needs to be taken up in V1.1.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-09 at 11.01.44 AM.png" alt=""><figcaption></figcaption></figure>

### Project Selection

When a user clicks on the projects option in the hamburger menu, it navigates them to the project selection screen from where the user can select another project to work on.

Though the automatic sync is triggered by the login action, after selecting another project, the system must now sync the data for the new project, and the same flow must be followed.

<figure><img src="../../../../.gitbook/assets/IMG_20230512_232548 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

### Location

For a user assigned multiple boundaries, after logging in, the boundary selection overlay must appear. This forces the user to select a boundary only after which the user can view the home screen. The user can then change the boundary whenever required from the location picker placed at the top right. It has dropdown fields to select the boundary, which depends upon the hierarchy level of the user. For an FLW, the boundary selection starts from the administrative post. The values in the dropdown are linked to the higher hierarchy and the user cannot select a boundary if the previous field is left blank.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000401 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

The dropdown must only consist of the boundaries which are assigned to the user, not all the boundaries under a particular hierarchy. For example, if the user is assigned localities 1, 2, and 3, and there are a total of 5 localities under admin post 1, then the dropdown must have only 1, 2, and 3 localities. The highest boundary must at least be selected to enable the select button which navigates the user to the home screen. For multiple projects, the sync needs to download the data only for the selected project.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000418 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

### Help Button

If the user clicks on the help button, it will give a walkthrough of the entire screen, including the role of each button placed with two buttons:

* Skip: If the user wants to skip the walkthrough at any point.
* Next: It will proceed to the next action aligned.&#x20;

The text box appears at the bottom of the button.

<figure><img src="../../../../.gitbook/assets/IMG_20230512_232704 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

### Search Households

When a user clicks on the ‘Beneficiaries’ button, he/she will be navigated to this screen. It displays the number of households registered along with the number of bednets delivered in that administrative area. The register button is primarily disabled to ensure that the user performs the search action.

The search bar allows the user to search by the household head’s name, and the system provides the search results. The minimum string length to show results is 2 characters and the order of the results will be the last record displayed first.

Two cases can be generated:

1. No results are displayed.
2. The search results displayed do not match.

Both cases are discussed further. The ‘Back’ button on the top will navigate to the home screen.

When the user searches for a household, there can be two outcomes:

1. The list of households will appear as a search result. The user can then open the household card and proceed with service delivery.
2. No results appear. In this case, the user needs to register the household first, so that he/she can deliver the intervention. (Note: Refer to the [**beneficiary registration**](../products-requirement-documents-prds/beneficiary-registration.md) PRD).

Household Card (For a household-level campaign)

After registering the household, a user can search for the household and open the card. The household name is displayed as household to avoid the risk of names that may be longer. There is an “Edit Household” button for editing the household details which navigates the user to the household location screen. Below the household’s name, the service delivery status is present followed by the administrative area and the number of members.&#x20;

There are cards for each member, starting from the household head. The card consists of the member's name, gender, age, and the ‘Edit’ button for individual-level actions. Age will be denoted in years for this version. This is because, for household-level campaigns, age is not a considerable parameter to provide interventions.

For adding new members to the household, there is an “Add Member” button below the member cards, which navigates the user to the “Individual Details” screen. At the bottom, the “Deliver Intervention” button navigates the user to the update delivery screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000606 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

If the intervention is delivered to that household, a second screen will appear. The deliver intervention button must be replaced by the ‘Update Delivery Details’ button if more interventions are needed to be delivered. The back button at the top takes the user to the list of households screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_233658 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

### Household Card (For an individual-level campaign)

In the case of an individual-level campaign, the household card appears in a similar format with some changes. The “Deliver Intervention” button is present at the bottom of every member’s card. If the intervention is delivered to a member, it will display ‘delivered’ below their details on the card, and the button will be replaced with “Update Delivery Details”. If the intervention is not delivered, it will display “not delivered”.

The deliver intervention button on the individual cards navigates the user to the update delivery screen. The back button navigates the user to the search households screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_233628 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

### Deliver Intervention

The summary of the household is displayed for preview on this screen. At the top, the “Date of Registration” is displayed, followed by the household head’s details, and the number of members in that household.

The “Number of Resources For Delivery” must be automatically calculated by the system based on the value entered in the number of household members, including the household head. For the LLIN campaign, the auto-calculation formula to calculate the number of bednets is in the ratio 1:1.8, that is,  1 bednet for 1.8 members with a maximum cap of 3 bednets per household. For example, if the member count is 7, the calculated value must be 3. The “Resource delivered” field consists of all the possible resources that can be delivered in a particular project. If there is only one resource to be delivered, then the field must be auto-filled by the system.

In the “Quantity distributed” field, the user can decide how many bednets need to be delivered to that household against the value generated by the system. The auto-calculation of the quantity must be hard-coded and can be made configurable in later versions. The user can increase or decrease the count through the ‘+’ or ‘-’ buttons, respectively. The field is mandatory and must be defaulted to 1, but can be reduced to 0 to cater to situations where the household receives no intervention due to stock-out.

<figure><img src="../../../../.gitbook/assets/Android - 481 (1).png" alt=""><figcaption></figcaption></figure>

The user can add a delivery comment if the service is not delivered due to some reason or situation, in the “Delivery Comment” field, which is a dropdown field with a list of possible reasons. The reasons must be configured in the MDMS. After reviewing the details, the user can click on the submit button which will save details of the household in the system. The confirmation screen appears after the details are validated.

<figure><img src="../../../../.gitbook/assets/Android - 542 (2).png" alt=""><figcaption></figcaption></figure>

### Confirmation screen

After submitting the details, a pop-up window appears, asking the user to review the details before submitting.

* If the user clicks on the ‘Submit’ button, the data will be submitted and the next screen will appear.
* If the user clicks on the ‘Cancel’ button, the popup will close and the user will be taken back to the “Deliver Intervention’ screen.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-09 at 12.02.44 PM.png" alt=""><figcaption></figcaption></figure>

### Acknowledgement Screen&#x20;

When the user clicks on submit, this screen appears, confirming to the user that his/her data has been recorded successfully. Below the message, there is a “Back to Search” button which navigates the user to the search households screen for household-level campaigns. The search bar must be blank and previous results must not be displayed. For individual-level campaigns, the user will land on the household card screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000550 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

### Delete Service Delivery Details

The front end must not have the capability to delete any delivery details to avoid any misuse of this function. The backend must be able to delete any delivery record if needed.

### Sync&#x20;

Before going into the field, the user needs to log into the application daily, which will initiate an automatic sync process mentioned in the user login PRD. For manual sync, there is a “Sync Data” button on the home screen which allows the user to sync data according to their convenience. At the bottom of the screen, there is a card that shows the message “Data Unsynced” along with the number of records unsynced.

<figure><img src="../../../../.gitbook/assets/IMG_20230512_232807 (4).jpg" alt="" width="188"><figcaption></figcaption></figure>

When the user clicks on the ‘Sync’ button, the sync action starts along with an overlay showing “Sync in Progress” over the home page. The user cannot perform any other action until the sync is complete or there is some error.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000434 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

### Sync Status&#x20;

Once the data is synced, a pop-up comes up stating “Data Synced” along with a ‘Close’ button. When the user clicks on this button, it navigates them to the home screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_000446 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

If the data did not sync, a popup comes up, stating “Sync Failed” with two buttons below it:

1. Retry: If the user wants to retry syncing the data.
2. Close: Clicking on this will navigate the user back to the home screen.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_233748 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

### Reports

The reports dashboard provides a tabular and visualised representation of user performance. They are generated based on the offline data present in the local device, associated with the user’s login. If a user selects the ‘Data’ option, it will provide a data-wise report of the campaign.&#x20;

The bar graph shows the day-to-day comparison of registered beneficiaries along with a threshold of the daily target for registration. The table, which is added below the graph, displays the households registered as well as bednets distributed.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-14 at 9.45.48 AM (1).png" alt=""><figcaption></figcaption></figure>

In the ‘Leaderboard’ section, the overall number of households registered will be displayed in the form of a milestone. Below that, all the individual users’ performance will be listed separately. The leaderboard option will not be available at the registrar level (field level) but at the field supervisor level.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-14 at 9.45.48 AM.png" alt=""><figcaption></figcaption></figure>

### Call Supervisor&#x20;

If the user is facing any challenge and requires immediate solutions, they can click on the “Call Supervisor” button on the home screen. It will redirect them to their phone’s dial pad with the supervisor’s number auto-filled. By clicking on the ‘Call’ button, the user can contact the supervisor for immediate assistance.

<figure><img src="../../../../.gitbook/assets/IMG_20230513_233810 (1).jpg" alt="" width="188"><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-14 at 9.48.43 AM.png" alt=""><figcaption></figcaption></figure>
