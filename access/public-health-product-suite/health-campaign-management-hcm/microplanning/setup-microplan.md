# Setup Microplan

**System role involved: System Administrator**

Select the language before you can log in. Currently, three languages are supported:

* English
* Portuguese
* French

Select the preferred language and click on 'Continue' to go to the login page.

{% hint style="info" %}
**Note:** Getting an account on HCM Microplanning: The implementation team will create the account for the system admin, and the admin will be provided with a username and password to log into the account.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.25.35 AM.png" alt=""><figcaption></figcaption></figure>

On the login page, enter the 'Username', 'Password', and the 'City' you are working in to log in to HCM Microplanning.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.26.18 AM.png" alt=""><figcaption></figcaption></figure>

Once you land on the homepage, you will see 3 different actions to choose from:

* Set Up Microplan: This is the capability to set up the microplan for a health campaign.
* Open Microplans: This is the capability to view the drafted and already created microplans.
* User management: You will use this capability to register the users with different roles that are part of the microplanning process.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.27.06 AM.png" alt=""><figcaption></figcaption></figure>

If this is the first time a microplan is being set up, you must create the users who will be primarily working on the different microplanning activities.

As a system administrator:

1. You must click on the "User Management" module to start with.
2. Once you click on the "User Management" module, you can see the list of users who are already registered for different microplanning roles. The user details that you will be able to see are:

* Name: Name of the microplanning user
* Email: Email ID of the microplanning user
* Contact Number: Contact number of the microplanning user
* Role: The role that is assigned to the microplanning user

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.28.01 AM.png" alt=""><figcaption></figcaption></figure>

This is the dashboard view that you will get once you land on the user management module. If this is a first-time setup, there will be no user details available in the dashboard.

3. You can search users using the ‘Name’ or ‘Contact Number’ search fields.
4. You can filter out some users belonging to a role using the role filter available in the dashboard.
5. If you need to add new users to the microplanning module, then click on the "Bulk Upload Users" feature.<br>

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.28.57 AM.png" alt=""><figcaption></figcaption></figure>

6. In the bulk upload user page, you can see a button called "Download Template", which will be used to register new users to the microplanning module.
7. Once you click on the ‘Download Template’ button, you will be able to download an Excel sheet that you will use to enter the new user details that are part of the Microplanning module.

The content of the template is:

* Read me: This sheet will have the details of how to fill out the user template Excel and upload it for user registration.
* User roles: This sheet will have the list of roles available for user registration and the description of each role.
* Role mapping for each sheet: There will be a sheet defined in the template for each role available. Inside each of the role sheets, the system admin can fill in user details with -

&#x20;      \- Name: Name of the user who will use the microplanning platform.

&#x20;      \- Contact number: Contact number of the person who will use the microplanning platform.

&#x20;       \- Email ID: Email ID of the person who uses the microplanning platform.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.29.58 AM.png" alt=""><figcaption></figcaption></figure>

This is the template structure for adding the new user details.

8. Once the template is filled, you can upload the data and see a success message that the file has been uploaded successfully.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.31.16 AM.png" alt=""><figcaption></figcaption></figure>

This is the screen that you will see when the template file is successfully uploaded.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.31.55 AM.png" alt=""><figcaption></figcaption></figure>

This is the screen that you will see when the uploaded template file is successfully submitted.

9. Once the file is uploaded, you will be able to download the user credentials of the new users who are registered.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.33.33 AM.png" alt=""><figcaption></figcaption></figure>

This is the capability that you will be able to download the user credentials of the registered users.

Content of the screen:

* File name and attachment: This will have the name of the file with a hyperlink to view and download the file.
* The downloaded file will have all the details of the file that was uploaded, along with the user login credentials for each of the users in the file.
* The downloaded file will have the login credentials that were generated by the system itself for the first time when the file was uploaded and submitted successfully.
* File uploaded by: This will show the name of the system administrator who uploaded and submitted the file.
* File uploaded time: This will show the timestamp of the file uploaded by the system administrator.&#x20;

5. Once the user creation step is completed, you can start with the microplan setup process.

As a system administrator:

1. Using this screen, you can capture the campaign details for which the microplanning needs to be done. The components of this screen are -

* Disease identified for the campaign - By default, ‘Malaria’ will be chosen as we are creating the microplanning for the assumptions of malaria. As and when new diseases come into the picture, we will add those diseases to the dropdown.
* Type of campaign - Upon choosing the disease, you will be asked to choose the campaign type, which is either ‘Bednet’ or ‘SMC’. As and when new campaign types come into the picture, we will add those campaign types to the dropdown.
* Resource distribution strategy - Upon choosing the campaign type, you will be asked to choose the distribution strategy, which is either ‘Fixed post’ or ‘House-to-House’ or ‘Fixed post & House-to-House’. Depending on the strategy chosen, the assumptions and resource estimation formula will be auto-configured in the platform.

Once you have chosen the required details, you can click on the "Save and Proceed" button to move to the next screen.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.37.19 AM.png" alt=""><figcaption></figcaption></figure>

This is the screen that you will use to fill in the campaign details.

2. Using this screen, you can view the details of the campaign for which the microplanning needs to be done, and the user will be able to name the microplan accordingly for further use. The components of this screen are -

* Campaign details - The campaign's basic details chosen in the previous screen, such as campaign disease, campaign type, and resource distribution strategy, will be shown here.
* Naming of microplan - The microplan name will be auto-suggested by the system. The structure of the microplan name is "Disease-CampaignType-Resource distribution strategy-MonthLast2digitsOfYear". The name is a suggested name, and you can edit the microplan name if required. It’s a mandatory field.
* Microplan naming format - This segment talks about the criteria for creating a microplan name if you want to self-create a microplan name. The naming conventions are:

&#x20;      \- The name should be a minimum of 3 characters in length

&#x20;      \- Only numeric values are not allowed

&#x20;      \- Special characters -, \_, (, ),& are only allowed

Once you have finalised the microplan name, you will have to click on the "Save and Proceed" button to move to the next screen.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.38.32 AM.png" alt=""><figcaption></figcaption></figure>

This is the screen that you will use to edit and finalise the microplan name.

3. Once you have finalised the microplan name and campaign details, you will not be allowed to edit the campaign details if you save the details and move to the next screen.

You will see a warning pop-up to confirm if you want to save and move to the next screen:

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.39.16 AM.png" alt=""><figcaption></figcaption></figure>

This is the warning pop-up that you will see before you move to the next screen.

4. This step will let you select the existing boundary data in the system. (This is a mandatory field for moving to the next screen.) The boundary data will have to be set up in the system beforehand at the time of instance creation, and the same boundary data should be reused by the user for all campaigns in a given instance.

{% hint style="info" %}
Note: If you have not selected boundaries, you will not be allowed to move on to the next steps. For example, if the boundary data is set up for Mozambique, the user will see the whole boundary mapping for Mozambique that is available on the system. If there is a need for change, we will provide the contact information for the support team to update the boundary, and the support team will update the boundary data.
{% endhint %}

The boundary selection for a campaign will happen through a mapped checkbox field, as shown below. There is a drop-down-based selection for each level of the hierarchy:

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.40.06 AM.png" alt=""><figcaption></figcaption></figure>

This is the boundary selection screen that you will need to configure.

If a given boundary is selected in one level of the hierarchy, the next level will show boundaries mapped to only the ones selected in the previous level. You will not be able to make any selection at a given level without selecting the boundaries in the level above.

After you have selected the boundaries, click on the "Save and Proceed" button.

5. Here, you will set target and total population data for the microplan by default at the lowest level of the administrative hierarchy boundaries. This will be achieved by an Excel upload as explained below:

To set target and total population data, click on “Download Template” on this screen. You will download the template having all the boundaries in Excel with an empty column for setting population data.

{% hint style="info" %}
Note: Each campaign will have its target-setting template. For example, the bednet campaign will have its template, and the SMC campaign will have its template.
{% endhint %}

The first tab/sheet will be the “Read Me” tab and will have the information on how you can set the targets for each village selected in the boundary selection screen.

The district-wise sheets will have the following structure:

* [Target Data Template (Bednet Campaign)](https://docs.google.com/spreadsheets/d/1SUagzYZTAbHzduXius_bcQAoP5yFvp4kPqR-y-epiyk/edit?usp=sharing)
* [Target Data Template (SMC Campaign)](https://docs.google.com/spreadsheets/d/1Ol9CWGtRoHf2yESRkUmt78My7xbSD7Et04hVAal9vZk/edit?usp=sharing)

{% hint style="info" %}
Note: All the villages in the Excel will be listed based on the district they belong to, with one tab for each district having a list of the villages under it. For example, if you have selected 20 districts, you will see 20 tabs (one for each district), having all the villages belonging to that particular district.&#x20;
{% endhint %}

You must adhere to the guidelines while entering the population data and uploading it for the microplanning estimation. The guidelines are below for population data upload -

* The mandatory fields, such as total population and target population data, must be a whole number (For example, population can be 1234 and not 123.5)
* The Latitude & Longitude fields should have data in Degree Decimal and Degree Minute Seconds (Value should be 12.3455 & not 12° 20' 43.7994")

Some of the validation you need to take care of while uploading the population Excel file:

* You can’t upload a file with empty population data for one or more villages in the sheet
* The population data for a village must be a whole number; else the file will not be uploaded
* You can’t delete any of the columns in the file before uploading it
* You can’t change the column structure in the file before uploading it
* You can’t delete any of the sheets in Excel before uploading it
* You can’t upload a file with negative population data for a village in the sheet
* You must adhere to the standard structure of the latitude & longitude before you upload the file with the latitude and longitude of the villages

Once you have uploaded the population data, click on "Save and Proceed" to move to the facility upload page.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.52.07 AM.png" alt=""><figcaption></figcaption></figure>

This screen will be used for uploading the population data.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 11.53.42 AM.png" alt=""><figcaption></figcaption></figure>

This screen shows the validation when the population file is uploaded successfully.

6. Once the population file is uploaded, you need to upload the facility sheet to configure the facilities that will be used in the microplanning process.

To configure the facility data for the microplan, you will have to download the facility upload sheet using the ‘Download Template’ button.&#x20;

If you already have a facility registry set up in the instance where the microplan is getting configured, those facilities will be pre-populated in the downloaded template. You can also add new facilities in the template, which will be considered for the current microplan.

The facility template structure is below:

* [Facility Upload Template](https://docs.google.com/spreadsheets/d/1RqUPo0oXVM2RH3Ts8hI1hx4TpsYY-qD-KzVhm9R-5A4/edit?usp=sharing)

The facility template will have 3 different Excel sheets:

\- Read me: This will help you know the steps to configure the facilities required for microplanning.-&#x20;

&#x20;\- List of available facilities:

* Facility Name: If the instance already has facilities defined, then you will be able to see the names of the facilities that are existing.
* Facility Type: If the instance already has facilities defined, then you will be able to see the type of facilities that are linked to each facility. The facility type for an instance will be defined in the MDMS during instance creation.&#x20;
* Facility Status: If the instance already has facilities defined, then you will be able to see the status of the existing facilities. The facility status for an instance will be defined in the MDMS during instance creation.
* Capacity: If the instance already has facilities defined, then you will be able to see the capacity of the existing facilities. The definition of the capacity of the facility is defined in the MDMS during instance creation.
* Facility usage: If the instance already has facilities defined, then you will be able to see the usage status of the existing facilities. ‘Active’ usage status means the facility is operational for the campaign, and ‘Inactive’ usage status means the facility is non-operational for the campaign. The usage status is defined in the MDMS during instance creation.
* Serving population per campaign: This will define the total population that can be served by the facility in a campaign.&#x20;
* Is fixed post?: If the instance already has facilities defined, then you will be able to see if the facilities will be catered as a fixed post. The fixed post tag will only be functional when the resource distribution strategy is either Fixed post or House-to-House & Fixed post (Mixed). For instance, the fixed post tag will be defined for a facility unless it is manually changed by the user.&#x20;
* Residing boundary code: The residing boundary code defines where exactly the facility resides. The user can tag the boundary where the facility resides using the residing boundary sheet. The residing boundary of the facilities will be saved for the instance, and it can be changed as per the user’s requirement during the facility configuration. This will be a dropdown option.
* Latitude & Longitude: Here, the user will be asked to enter the latitude & longitude of the facility to be shown on the map. This is optional data.

\- Boundary data: This sheet will give you the administrative boundary where the microplan is being set up. This will also give the boundary codes for each administrative boundary, which can be used for tagging the facilities to their respective boundaries.

You must adhere to the guidelines while entering the facility data and uploading it for the microplanning estimation. The guidelines are below for population data upload -

* All the fields are mandatory and can't be empty, except the Latitude and Longitude fields
* The Latitude & Longitude fields should have data in Degree Decimal and Degree Minute Seconds (Value should be 12.3455 & not 12° 20' 43.7994")

Some of the validation you need to take care of while uploading the population Excel file:

* You must fill in all the mandatory fields before uploading the facility Excel file
* For all the values of each column of data, you must choose the value from the dropdown to upload the Excel file
* You can’t delete any of the columns in the file before uploading it
* You can’t change the column structure in the file before uploading it
* You can’t delete any of the sheets in Excel before uploading them
* You can’t upload a file with a negative facility capacity for a facility in the Excel sheet
* You must adhere to the standard structure of the latitude & longitude before you upload the file with the latitude and longitude of the villages
* You must choose the correct facility residing code from the Boundary code sheet, for tagging the facility to its boundary&#x20;

Once you have uploaded the facility template, click on "Save and Proceed" to move to the facility upload page.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.28.29 PM.png" alt=""><figcaption></figcaption></figure>

This screen will be used for uploading the facility data.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.29.10 PM.png" alt=""><figcaption></figcaption></figure>

This screen shows the validation when the facility file is uploaded successfully.

7. Once the data management step is completed, you will be directed to the microplan assumption module.

Here, you will be asked some preliminary questions, the answers to which will provide an ideal estimate assumption form for you.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.30.48 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen for answering the preliminary questions.

Since you have chosen the resource distribution strategy as "House-to-House & Fixed post", you will have to answer the following questions:

* How is the campaign registration process happening?
* How is the campaign distribution process happening?

You can choose either House-to-House or Fixed post, and depending on what you have selected, the microplan assumptions will be configured on the next page accordingly.

Here, once the previous questions are answered, you will move to the microplan assumption page to enter the microplan assumptions as per the campaign requirements.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.32.05 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen for entering the general assumptions for the microplan.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.33.27 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen for entering the registration assumptions for the microplan.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.34.16 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen for entering the distribution assumptions for the microplan.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.35.48 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen for entering the commodities assumptions for the microplan.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.36.32 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen for entering the vehicle assumptions for the microplan.

Here is the sheet containing the information for all the assumptions as per the campaign type and the distribution strategy:

* [Microplan Assumptions](https://docs.google.com/spreadsheets/d/104awZH37HUyWzXmZNvkLAzaL9exrWXpEYuS6P8RmagI/edit?usp=sharing)

All the assumptions shown above are configured as per the campaign type and distribution strategy chosen.

You can add a new assumption, if required, using the "Add assumption" button.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.39.43 PM.png" alt=""><figcaption></figcaption></figure>

You can delete the already configured assumptions, if required, using the ‘Delete’ button beside the assumption.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.40.26 PM.png" alt=""><figcaption></figcaption></figure>

Once all the assumptions are configured, click on "Save and Proceed" to move to the next section of the microplan formula configuration.

8. Once the assumptions are configured, you will be moved to the microplan formula configuration.

Here, you will be able to see the formulas that are pre-configured for the campaign type and distribution strategy chosen.

And you must configure the microplan assumptions properly as the formulas will be dependent on the assumptions you have configured.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.43.32 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen for viewing the general estimation formula.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.44.15 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen for viewing the registration estimation formula.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.44.55 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen for viewing the distribution estimation formula.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.45.22 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen for viewing the commodities estimation formula.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.46.02 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen for viewing the vehicle estimation formula.

Here is the sheet containing the information for all the estimation formulas as per the campaign type and the distribution strategy:

* [Microplan Estimation Formula](https://docs.google.com/spreadsheets/d/104awZH37HUyWzXmZNvkLAzaL9exrWXpEYuS6P8RmagI/edit?gid=1706240338#gid=1706240338)

All the estimation formulas shown above are configured as per the campaign type and distribution strategy chosen.

You can add a new estimation formula, if required, using the "Add formula" button.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.49.18 PM.png" alt=""><figcaption></figcaption></figure>

You can delete the already configured estimation formula, if required, using the ‘Delete’ button beside the pre-configured formula.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.49.56 PM.png" alt=""><figcaption></figcaption></figure>

Once all the estimation formulas are configured, click on "Save and Proceed" to move to the next section of user access management.

9. Once the formula configuration has been completed, you will be moved to the user access management for configuring the users who will be performing the microplanning activities.

Here, you can choose and attach the selected users to the microplan.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.50.32 PM.png" alt=""><figcaption></figcaption></figure>

This screen is for adding the users belonging to the ‘National Microplan estimation approver’ to the microplan using the "Assign National Microplan Estimation Approver" button.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.51.12 PM.png" alt=""><figcaption></figcaption></figure>

This is the pop-up that you will use to search for the user to whom you want to assign the microplan.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.52.05 PM.png" alt=""><figcaption></figcaption></figure>

This screen shows the users with the "National microplan estimation approver" role you added to this microplan. You can also unassign the assigned users from the microplan using the ‘Unassign’ button.

***

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.54.46 PM.png" alt=""><figcaption></figcaption></figure>

This screen is for adding the users belonging to the "National facility boundary assigner" to the microplan using the "Assign National Facility Boundary Assigner" button.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.55.56 PM.png" alt=""><figcaption></figcaption></figure>

This is the pop-up that you will use to search for the user to whom you want to assign the microplan.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.56.29 PM.png" alt=""><figcaption></figcaption></figure>

This screen shows the users with the "National facility boundary assigner" role you added to this microplan. You can also unassign the assigned users from the microplan using the ‘Unassign’ button.

\-------------------------------------------------------------------------------------------------------------------  &#x20;

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.57.28 PM.png" alt=""><figcaption></figcaption></figure>

This screen is for adding the users belonging to the "National population data approver" to the microplan using the "Assign National Population Data Approver" button.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.58.13 PM.png" alt=""><figcaption></figcaption></figure>

This is the pop-up that you will use to search for the user to whom you want to assign the microplan.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.59.00 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen that shows the users with the "National population data approver" role that you have added to this microplan. You can also unassign the assigned users from the microplan using the ‘Unassign’ button.

***

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 1.59.52 PM.png" alt=""><figcaption></figcaption></figure>

This screen is for adding the users belonging to the "Microplan estimation approver" to the microplan using the ‘Assign Microplan Estimation Approver’ button.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 2.00.34 PM.png" alt=""><figcaption></figcaption></figure>

This is the pop-up that you will use to search for the user to whom you want to assign the microplan.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 2.01.16 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen that shows the users with the "Microplan estimation approver" role that you have added to this microplan. You can also unassign the assigned users from the microplan using the ‘Unassign’ button.

***

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 2.06.47 PM.png" alt=""><figcaption></figcaption></figure>

This screen is for adding the users belonging to the "Facility boundary assigner" to the microplan using the "Assign Facility Boundary Assigner" button.



<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 2.07.43 PM.png" alt=""><figcaption></figcaption></figure>

This is the pop-up that you will use to search for the user to whom you want to assign the microplan.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 2.08.17 PM.png" alt=""><figcaption></figcaption></figure>

This screen shows the users with the "Facility boundary assigner" role you added to this microplan. You can also unassign the assigned users from the microplan using the ‘Unassign’ button.

***

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 2.08.57 PM.png" alt=""><figcaption></figcaption></figure>

This screen is for adding the users belonging to "Population data approver" to the microplan using the "Assign Population Data Approver" button.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 2.09.33 PM.png" alt=""><figcaption></figcaption></figure>

This is the pop-up that you will use to search for the user to whom you want to assign the microplan.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 2.10.18 PM.png" alt=""><figcaption></figcaption></figure>

This is the screen that shows the users with the "Population data approver" role that you have added to this microplan. You can also unassign the assigned users from the microplan using the ‘Unassign’ button.

Now that you have assigned the required users to the microplan, you can click on "Save and Proceed" to go to the next and final phase of the microplan setup.

10. You are now at the last leg of setting up the microplan.

In the summary screen, you can view all the tabs and make edits before finalising the microplan setup.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 2.11.14 PM.png" alt=""><figcaption></figcaption></figure>

This summary screen shows you all the tabs of the microplan configuration.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 2.11.42 PM.png" alt=""><figcaption></figcaption></figure>

This is the finalised microplan setup screen. Once the microplan setup is done, you cannot make any changes to the microplan. Now the microplan is ready for the next set of activities to be executed.

6. Here, you will click on "Open Microplan" to view the list of the microplans that are either in created or in drafted status.

The microplan can be in any of the following statuses at a time:

* Drafted: This status indicates that the microplan is partially configured, and the setup isn’t completed yet.
* Completed setup: This status indicates that the microplan setup has been completed, and now the microplanning activities can be started.
* Validation in progress: This status indicates that the microplan validation process has started.
* Microplan finalised: This status indicates that the microplan estimation has been finalised and completed.

The dashboard has a total of 6 columns:

* Name of the microplan: It indicates the name of the microplan
* Status of microplan: It indicates the current status of the microplan
* Campaign disease: It indicates the campaign disease for the microplan
* Campaign type: It indicates the type of campaign for the microplan
* Distribution strategy: It indicates the distribution strategy of the campaign for the microplan
* Action: It indicates the action that can be taken in the microplan.&#x20;

Available actions are -

1. Edit microplan: If the microplan status is drafted, you can edit the microplan before finalising it.
2. View summary: If the microplan setup is completed, you can only view the summary of the microplan. You will not be able to edit the microplan.
3. Download: If the microplan estimation is finalised, you can download the microplan estimation in Excel format.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-11-26 at 2.13.02 PM.png" alt=""><figcaption></figcaption></figure>

This is the view of the ‘Open microplan’ dashboard.

####

