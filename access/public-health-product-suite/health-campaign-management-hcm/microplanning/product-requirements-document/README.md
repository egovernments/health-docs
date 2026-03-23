# Product Requirements Document

## Background

Health campaign microplanning is a detailed planning approach used to ensure that health interventions, such as immunisations or disease prevention campaigns, are effectively delivered to target populations.&#x20;

#### What assumptions are considered?

Updated registry: Assume that the registry data required for microplanning is accurate and up-to-date. This includes boundary data for countries, provinces, districts, and villages, as well as the location of health facilities and other points of interest. The user can update the registry while setting up the microplan.

User Roles and Access: Assume that users will be assigned specific roles (e.g., system administrator, data collector, reviewer) with corresponding access levels and permissions to ensure data integrity and security.

Data Collection Methodology: Assume that data collection methods are standardized and that data collectors are trained to ensure the consistency and accuracy of the data entered into the system.

Connectivity: Assume that users will have access to the internet or a mobile network to use the platform, although there should be provisions for offline data collection and synchronization when connectivity is limited for certain use cases.

Localization: Assume that the platform will be localized to support multiple languages and adapt to the cultural and linguistic diversity of the target communities. For the first release, the platform will be localised for English, French, and Portuguese languages.

Scalability: Assume that the platform will be scalable to accommodate additional users, data, and campaigns without significant performance degradation.

User Training and Support: Assume that users will receive adequate training on how to use the platform and that support will be available to address any issues or questions that arise.

Sustainability: Assume that the platform will be designed with sustainability in mind, considering the long-term maintenance and updates required to keep the system operational and relevant.

No registry changes: Assume that no new boundary registry or facility registry will be created or updated once the microplan setup is completed.

#### What are the user personas involved in the microplanning process?

Below are the users involved in the microplanning process -

a. System administrator - This user is responsible for setting up the microplanning platform such as selecting campaign boundaries, setting up the data, configuring the microplan assumptions, etc. This user will belong to the national/country-level administrative hierarchy.

b. Data collector - This user is responsible for collecting and validating the population data from every village assigned to him/her. He will also capture the geographical features of the assigned villages such as the accessibility level of the village, the security level of the village, etc.

c. Supervisors - This is a user role that can be defined for multiple users across different administrative hierarchies. Every supervisor will have its action mapping such as supervisors with only data approver access, supervisors with microplan approval access, etc. The different type of supervisors involved are&#x20;

1. Population data approver - This user will have access to the microplan module to view, validate, and approve the population of the assigned boundaries. The approved population will be used for the estimation of resources of the microplan.
2. Facility catchment mapper - This user will have access to the microplan module to map the facilities to their catchment boundaries w.r.t the user’s assigned boundaries.
3. Microplan approver - This user will have access to the microplan module to view, edit, and approve the microplanning estimation concerning the user’s assigned boundaries.
4. Microplan viewer - This user will have access to the microplan module to only view the microplanning estimation concerning the user’s assigned boundaries.

#### Actor-Noun-Verb mapping:

Click [here](https://docs.google.com/spreadsheets/d/1kUe7pScVDv05M_Q2OrZCKrAj9_3Y8eRZrZIXwqRdJYQ/edit?usp=sharing) to view the actor-noun-verb mapping.

#### What are the prerequisites for microplanning?

1. The boundary registry is configured and updated during the instance creation for the country.
2. For defining the campaign facilities, the ‘Facility type’ should be configured in the MDMS during the instance creation for the country.
3. The facility or point of service capacity must be defined for the campaign type during instance creation. For the bednets campaign, the capacity should be ‘Bales’ ideally, for the SMC campaign, the capacity should be ‘Blisters’ ideally. It may change depending on the user’s requirements.
4. While managing the facility registry, the ‘Facility status’ needs to be configured in the MDMS during the instance creation of the country.
5. In the facility upload template, the column ‘Is fixed post?’ column options as ‘Yes’ or ‘No’ need to be configured in the MDMS
6. In the facility upload template, the column ‘Facility usage’ column options as ‘Active’ or ‘Inactive’ need to be configured in the MDMS
7. The capacity of the vehicle needs to be configured in the MDMS during instance setup. For the bednets campaign, the capacity should be ‘Bales’ ideally, for the SMC campaign, the capacity should be ‘Blisters’ ideally. It may change depending on the user’s requirements.

#### Managing registry data:

There will be 3 different registry data that will be used in this version of the microplan:

1. Boundary registry - The boundary registry is defined in the MDMS and the same registry can be used in the microplanning module. The boundary registry will later be created & managed by the admin console in the next version of the admin console.
2. Facility registry - The facility registry is defined in the MDMS and the same registry can be used in the microplanning module. The facility registry will later be created & managed by the admin console in the next version of the admin console.
3. Vehicle registry - The vehicle registry is defined in the MDMS and the same registry can be used in the microplanning module. The vehicle registry will later be created & managed by the admin console in the next version of the admin console.

#### Microplanning roadmap & value bundle:

Click [here](https://docs.google.com/spreadsheets/d/1kUe7pScVDv05M_Q2OrZCKrAj9_3Y8eRZrZIXwqRdJYQ/edit?usp=sharing) to view the detailed roadmap and value bundle

#### User journey workflow:

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 11.37.46 AM.png" alt=""><figcaption></figcaption></figure>

Click [here](https://miro.com/app/board/uXjVKzN48LI=/?share_link_id=504796440221) to view in Miro board

## Functional specifications:

### **System admin’s flow:**

1. **Capturing campaign details -**

Actor: System administrator/Program manager

Administrative boundary: National/Country

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 11.41.05 AM.png" alt=""><figcaption><p>Capturing campaign details</p></figcaption></figure>

Using this screen, the user will be able to capture the campaign details for which the microplanning needs to be done. The components of this screen are -

a. Disease identified for the campaign - By default ‘Malaria’ will be chosen as we are creating the microplanning for the assumptions of malaria. As and when new diseases come into picture and we will have a better understanding of the assumptions and estimation, we will add those diseases in the dropdown.

b. Type of campaign - Upon choosing the disease, the user will be asked to choose the campaign type, which is either ‘Bednet’ or ‘SMC’. New campaign types can be included as and when understanding of the assumptions and estimation for them can be captured.

c. Resource distribution strategy - Upon choosing the campaign type, the user will be asked to choose the distribution strategy, which is either ‘Fixed post’ or ‘House-to-House’ or ‘Fixed post & House-to-House’. Depending on the strategy chosen, the assumptions and resource calculations will be configured by the platform.

d. Next - On click of ‘Next’, the campaign details will be saved and the user will be redirected to the next screen for naming the microplan.

e. Back - On click of ‘Back’, the user will be redirected to the homepage to either create a new microplan or to open a saved microplan.

2. **Capture microplan name -**

Actor: System administrator/Program manager

Administrative boundary: National/Country

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 11.43.42 AM.png" alt=""><figcaption><p>Naming of microplan</p></figcaption></figure>

Using this screen, the user can view the details of the campaign for which the microplanning needs to be done, and the user will be able to name the microplan accordingly for further use. The components of this screen are -

a. Campaign details - The campaign basic details chosen in the previous screen such as campaign disease, campaign type and resource distribution strategy will be shown here.

b. Naming of microplan - The microplan name will be auto suggested by the system. The structure of microplan name is ‘Country-Disease-CampaignType-MonthLast2digitsOfYear’. The name is a suggested name and the user can edit the microplan name if required. It’s a mandatory field.

Validation: The microplan name must be unique and can’t be the same as any previous created microplan name. If the user tries to enter a name that has been used already, show the error message ‘The name you have entered, has already been used. Please try a different name.’

c. Microplan naming format - This segment talks about the criteria for creating a microplan name, if the user wants to self create a microplan name. The naming convention are:

i. The name should be a minimum of 3 characters in length

ii. Only numeric values are not allowed

iii. Special characters -, \_, (, ) are only allowed

Validation: If a user tries to enter a name that doesn’t match with the naming convention, show an error message ‘The name you have entered doesn’t match with the naming convention. Please try a different name.’

The max length of the microplan name is 100 characters.

d. Next - On click of ‘Next’, the microplan name will be saved and unedited. At this stage, the microplan will move to ‘Drafted setup’ status for being re-used or worked upon later.

e. Back - On click of ‘Back’, the user will be redirected to the previous step of capturing campaign details, but the microplan status will not change.&#x20;

3. **Selection of campaign boundary -**

Actor: System administrator/Program manager

Administrative boundary: National/Country

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 11.46.03 AM.png" alt=""><figcaption><p>Selection of campaign boundary</p></figcaption></figure>

This screen will be used for choosing the campaign boundary where the microplanning estimation needs to be done. The below administrative hierarchy is configured for Mozambique, and the same administrative hierarchies will be different for different countries. The administrative hierarchy is defined during the instance setup of a country. The components of this screen are -

a. Selected boundaries count label - There will be a label on top of the screen where user will be able to see count of boundaries chosen as:

1. \# of country chosen&#x20;
2. \# of province chosen&#x20;
3. \# of district chosen
4. \# of admin post chosen&#x20;
5. \# of locality chosen&#x20;
6. \# of the village chosen.

b. Country - Here the user will choose the country where the campaign needs to be executed. It’s a mandatory field.

c. Province - Here the user will choose the province where the campaign needs to be executed. There can be multiple provinces to choose from depending on the country chosen. It will be a multi-select search-enabled dropdown for the user to choose the province(s). It’s a mandatory field.

d. District - Here the user will choose the district(s) where the campaign needs to be executed. There can be multiple districts to choose from depending on the provinces chosen. It will be a multi-select search-enabled dropdown for the user to choose the district(s). It’s a mandatory field.

e. Administrative post - Here the user will choose the admin post(s) where the campaign needs to be executed. There can be multiple admin post(s) to choose from depending on the districts chosen. It will be a multi-select search-enabled dropdown for the user to choose the admin post(s). It’s a mandatory field.

f. Locality - Here the user will choose the locality(s) where the campaign needs to be executed. There can be multiple locality(s) to choose from depending on the admin posts chosen. It will be a multi-select search-enabled dropdown for the user to choose the locality(s). It’s a mandatory field.

g. Village - Here the user will choose the village(s) where the campaign needs to be executed. There can be multiple village(s) to choose from depending on the localities chosen. It will be a multi-select search-enabled dropdown for the user to choose the village(s). It’s a mandatory field.

h. Next - On click of ‘Next’, the campaign boundaries will be chosen for microplanning. The same set of boundaries will be further used for data upload in the next part. All the fields are mandatory for moving to the next screen.

i. Back - On click of ‘Back’, the user will be redirected to the previous screen for naming microplan.

Validation: Once the microplan name is chosen and the user moves to the next screen, the microplan name can’t be changed.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 11.48.47 AM.png" alt=""><figcaption><p>View when the user clicks on ‘+7 selected’ for a specific boundary</p></figcaption></figure>

Users can view all the selected boundaries as an array of lists and clear the selected boundaries if required. The user will be able to see the list of chosen boundaries for the parent boundary in the content box. For example, if the user chooses to see the list of districts chosen, then it will show in the content box with the province name and the list of districts attached to the province, if there are multiple provinces, there will be multiple content boxes.

4. **Data management process (Population upload) -**&#x20;

Actor: System administrator/Program manager

Administrative boundary: National/Country

This screen will be used for uploading the population data for the boundaries chosen for microplanning. When the user chooses the campaign boundaries in the previous step, the user in this step will have to upload the total and target population of the villages chosen in the campaign boundaries. The components of this screen are -

a. Download population template - This component will be used when the user has to download the boundary template to enter the population details for microplan estimation. The template will be separately downloaded & maintained for both bednets and SMC (As of now).&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 11.55.06 AM.png" alt=""><figcaption><p>Download population template pop-up screen</p></figcaption></figure>

* This screen will appear for the user to download the population template to be filled and upload
* The user may skip it if he/she wants to move ahead without downloading the population template

The template for bednets is [here](https://docs.google.com/spreadsheets/d/1SUagzYZTAbHzduXius_bcQAoP5yFvp4kPqR-y-epiyk/edit?usp=sharing).

The content of the downloadable bednet template is as follows -

* Country: This shows the country where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Province: This shows the province(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* District: This shows the district(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Administrative post: This shows the admin post(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Locality: This shows the locality(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Village: This shows the village(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Total population: Here the user will be asked to enter the total village population.
* Target population: Here the user will be asked to enter the target population who will be benefiting from the campaign.
* Latitude & longitude: Here the user will be asked to enter the latitude & longitude of the village to be shown on the map.

For every campaign district, there will be a sheet in the downloadable report that the user needs to fill out and upload.

Note: The template should be configurable depending on the program. For Mozambique, the population template Excel has each sheet for the district. If the program wants to configure and collect data for each administrative post or locality level, the Excel sheets should be configured accordingly to collect population information in the administrative post or locality level.

Validation check:

1. The columns from ‘Country’ or highest administrative boundary to ‘Village’ or lowest administrative boundary should be fixed in the Excel and non-editable
2. The target population column is mandatory & can’t be empty
3. The total population column is mandatory & can’t be empty
4. The population data must only accept a whole number (Eg: 1234 and not 123.4)
5. The population data must be greater than 0
6. The Latitude & Longitude fields should have data in Degree Decimal and Degree Minute Seconds

The template for SMC is [here](https://docs.google.com/spreadsheets/d/1Ol9CWGtRoHf2yESRkUmt78My7xbSD7Et04hVAal9vZk/edit?usp=sharing).

The content of downloadable SMC template is as follows -

* Country: This shows the country where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Province: This shows the province(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* District: This shows the district(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Administrative post: This shows the admin post(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Locality: This shows the locality(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Village: This shows the village(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Total population: Here the user will be asked to enter the total village population.
* Target population (Age 3 - 11 months): Here the user will be asked to enter the target population count of the children between 3 - 11 months in the village.
* Target population (Age 12 - 59 months): Here the user will be asked to enter the target population count of the children between 12 - 59 months in the village.
* Latitude & longitude: Here the user will be asked to enter the latitude & longitude of the village to be shown on the map.

For every campaign district, there will be a sheet in the downloadable report that the user needs to fill out and upload.

Note: The template should be configurable depending on the program. For Mozambique, the population template Excel has each sheet for the district. If the program wants to configure and collect data for each administrative post or locality level, the Excel sheets should be configured accordingly to collect population information at the administrative post or locality level.

Validation check:

1. The columns from ‘Country’ or highest administrative boundary to ‘Village’ or lowest administrative boundary should be fixed in the Excel and non-editable
2. The target population columns (Age 3-11 months and age 12-59 months) are mandatory & can’t be empty
3. The total population column is mandatory & can’t be empty
4. The population data must only accept a whole number (Eg: 1234 and not 123.4)
5. The population data must be greater than 0
6. The Latitude & Longitude fields should have data in Degree Decimal and Degree Minute Seconds

b. Upload population template - This component will be used when the downloaded population excel file is filled and needs to be uploaded for estimating the campaign resource estimation.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 11.58.28 AM.png" alt=""><figcaption><p>Upload population template to capture population data for the boundaries</p></figcaption></figure>



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 11.59.24 AM.png" alt=""><figcaption><p>Uploaded file shown to the user for preview, re-upload, delete or download</p></figcaption></figure>

* The user can preview the uploaded file by clicking on the file name and it will open up the Excel preview
* The user can re-upload the file using the ‘Re-upload’ button
* The user can download the already uploaded file using the ‘Download’ button
* The user can delete the uploaded file using the ‘X’ button, and once deleted, the user will be moved back to the Excel upload screen

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 2.11.40 PM.png" alt=""><figcaption><p>View when the uploaded file has errors</p></figcaption></figure>

* The user will be able to view the number of errors captured in the uploaded file
* The ‘View errors’ button will let the user view the list of errors in a tabular format

Error validation:

1. For bednet and SMC template upload - If the total population data uploaded is empty for any village, then show the error message ‘Total population data can’t be empty, please update the data and re-upload’.
2. For bednet and SMC template upload - If the total population data uploaded is not a whole number, then show the error message ‘Total population data must be a whole number, please update the data and re-upload’.
3. For bednet template upload - If the target population data uploaded is empty for any village, then show the error message ‘Target population data can’t be empty, please update the data and re-upload’.
4. For bednet template upload - If the target population data uploaded is not a whole number, then show the error message ‘Target population data must be a whole number, please update the data and re-upload’.
5. For SMC template upload -  If the target population data (Age 3-11 months or Age 12-59 months) uploaded is empty for any village, then show the error message ‘Target population data can’t be empty, please update the data and re-upload’.
6. For SMC template upload - If the target population data (Age 3-11 months or Age 12-59 months) uploaded is not a whole number, then show the error message ‘Target population data must be a whole number, please update the data and re-upload’.
7. For bednet and SMC template upload - if the lat & long data uploaded does not adhere to the guideline, then show the error message ‘The latitude and longitude data does not comply with the guideline structure, please update the data and re-upload’.
8. The uploaded Excel file must have ‘Readme’ and ‘District sheets chosen in the boundary selection’, or the microplanning system will not validate and approve the file. Error message to be shown ‘One or more data sheets is absent, please update the data and re-upload the file’.

c. Error list view - This component will be shown when the upload file has one or more errors. The user can view the list of errors on the screen as well as download the errors as an Excel to view the error details in each row of Excel sheet.<br>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 2.13.46 PM.png" alt=""><figcaption><p>View when the user clicks on ‘View errors’</p></figcaption></figure>

* The user will be able to navigate through the different errors using the ‘Previous’ or ‘Next’ buttons highlighted during data upload on the error view screen
* All the errors will be highlighted in red color
* On top of the preview screen, the user will be able to view the error details, for example, here the error mentioned that ‘Row 24 is empty!’
* The user can download the Excel file with the detailed error mentioned. There should be an added column called ‘Error details’ that should show the errors in comma-separated format in case a single row has multiple errors
* On click of ‘Back’ the user should be exited from the error preview screen

d. Excel upload guideline - The guideline directs the user on what to keep in mind while entering the population data and uploading it for the microplanning estimation. The guidelines are below for population data upload -

* The mandatory fields such as total population and target population data must be a whole number (For example, population can be 1234 and not 123.5)
* The Latitude & Longitude fields should have data in Degree Decimal and Degree Minute Seconds ( Value should be 12.3455 & not 12° 20' 43.7994")

**e. Data management process (Facility upload) -**&#x20;

Actor: System administrator/Program manager

Administrative boundary: National/Country

This screen will be used to set up the facilities that are required for the campaign execution and microplanning estimation. Every facility to be used in the campaign needs to be added using this screen. The competent of this screen are -&#x20;

a. Download facility template - This component will be used when the user needs to see the list of facilities available for the instance. The user can download the facility template and check out the facility list accordingly for campaign execution.&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 2.16.02 PM.png" alt=""><figcaption><p>Download facilities template pop-up screen</p></figcaption></figure>

* This screen will appear for the user to download the facility template to be updated and upload
* The user may skip it if he/she wants to move ahead without downloading the facility template

The template for the facility is [here](https://docs.google.com/spreadsheets/d/1RqUPo0oXVM2RH3Ts8hI1hx4TpsYY-qD-KzVhm9R-5A4/edit?usp=sharing)

The facility template will have 2 different Excel sheets:

Facility sheet content:

* Facility Name: If the instance already has facilities defined, then the user will be able to see the name of the facilities that are existing.
* Facility Type: If the instance already has facilities defined, then the user will be able to see the type of facilities that are linked to each facility. The facility type for an instance will be defined in the MDMS during instance creation. This will be a dropdown option.
* Facility Status: If the instance already has facilities defined, then the user will be able to see the status of the facilities that are existing. The facility status for an instance will be defined in the MDMS during instance creation. This will be a dropdown option.
* Capacity: If the instance already has facilities defined, then the user will be able to see the capacity of the facilities that are existing. The definition of capacity of the facility is defined in the MDMS during instance creation.&#x20;
* Facility usage: If the instance already has facilities defined, then the user will be able to see the usage status of the facilities that are existing. ‘Active’ usage status means the facility is operational for the campaign and ‘Inactive’ usage status means the facility is non-operational for the campaign. The usage status is defined in the MDMS during instance creation. This will be a dropdown option.
* Is fixed post?: If the instance already has facilities defined, then the user will be able to see if the facilities will be catered as a fixed post. The fixed post tag will only be functional when the resource distribution strategy is either Fixed post or House-to-House & Fixed post (Both). For instance, the fixed post tag will be defined for a facility unless it is manually changed by the user. This will be a dropdown option.
* Residing boundary code: The residing boundary code defines where (Which village) exactly the facility resides. The user will be able to tag the boundary where the facility resides using the residing boundary sheet. The residing boundary of the facilities will be saved for the instance and it can be changed as per the user’s requirement during the facility configuration. This will be a dropdown option.
* Latitude & Longitude: Here the user will be asked to enter the latitude & longitude of the village to be shown on the map.

Residing boundary sheet content:

* Country: This shows the country where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Province: This shows the province(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* District: This shows the district(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Administrative post: This shows the admin post(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Locality: This shows the locality(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Village: This shows the village(s) where the campaign needs to run. This will be pre-defined in the downloaded template as per boundary selection in the previous step.
* Boundary code: This shows the boundary code of the village where the campaign needs to run. The boundary code will be pre-defined for every village during the boundary registry configuration at the instance creation.

b. Upload facility template - This component will be used to upload the facility template to configure the facilities to be used in the campaign. The user can fill the template with the required details and upload the file accordingly. The user can add a new facility as well as deactivate the existing facilities to be used in the campaign.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 2.18.07 PM.png" alt=""><figcaption><p>Upload facility template to create the campaign facilities</p></figcaption></figure>



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 2.18.52 PM.png" alt=""><figcaption><p>Uploaded file shown to the user for preview, re-upload, delete or download</p></figcaption></figure>

* The user can preview the uploaded file by clicking on the file name and it will open up the excel preview
* The user can re-upload the file using the ‘Re-upload’ button
* The user can download the already uploaded file using the ‘Download’ button
* The user can delete the uploaded file using the ‘X’ button, and once deleted, the user will be moved back to the Excel upload screen

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 2.20.10 PM.png" alt=""><figcaption><p>View when the uploaded file has errors</p></figcaption></figure>

* The user will be able to view the number of errors captured in the uploaded file
* The ‘View errors’ button will let the user view the list of errors in a tabular format

Error validation:

1. In the facility sheet, the ‘Facility Name’ is a mandatory field. The user needs to enter the facility name before uploading the file into the system. Error message when there is no facility name defined ‘The facility name doesn’t exist in the uploaded file, please update and re-upload’.
2. In the facility sheet, the ‘Facility Type is a mandatory field. The user needs to enter the facility type before uploading the file into the system. Error message when there is no facility type defined ‘The facility type doesn’t exist for the facility in the uploaded file, please update and re-upload’.
3. In the facility sheet, the ‘Facility Status’ is a mandatory field. The user needs to enter the facility status before uploading the file into the system. Error message when there is no facility status defined ‘The facility status doesn’t exist for the facility in the uploaded file, please update and re-upload’.
4. In the facility sheet, the ‘Capacity’ is a mandatory field. The user needs to enter the facility capacity before uploading the file into the system. The unit of facility capacity needs to be defined in the MDMS during instance creation. Error message when there is no facility capacity defined ‘The facility capacity doesn’t exist for the facility in the uploaded file, please update and re-upload’.
5. In the facility sheet, the ‘Facility usage’ is a mandatory field. The user needs to enter the facility usage before uploading the file into the system. Error message when there is no facility usage defined ‘The facility usage information doesn’t exist for the facility in the uploaded file, please update and re-upload’.
6. In the facility sheet, the ‘Is fixed post?’ is a mandatory field. The user needs to enter the facility-fixed post tag before uploading the file into the system. Error message when there is no fixed post tag defined ‘The facility doesn’t have a fixed post tag defined in the uploaded file, please update and re-upload’.&#x20;

Validation: This validation will be available only when the resource distribution strategy is either Fixed post or Fixed post & H2H.

7. In the facility sheet, the ‘Residing boundary code’ is a mandatory field. The user needs to enter the facility’s residing boundary code before uploading the file into the system. Error message when there is no facility’s residing boundary code defined ‘The facility’ residing boundary code doesn’t exist for the facility in the uploaded file, please update and re-upload’.
8. If the lat & long data uploaded do not adhere to the guideline, then show the error message ‘The latitude and longitude data does not comply with the guideline structure, please update the data and re-upload’.
9. The uploaded Excel file must have ‘Readme’, ‘Facility’, and ‘Residing boundary’ sheets. The residing boundary sheet will have boundaries chosen for the campaign, else the file will not be validated and approved by the microplanning system. Error message to be shown ‘One or more data sheets are absent in the uploaded file, please update the data and re-upload the file’.

c. Error list view - This component will be shown when the upload file has one or more errors. The user can view the list of errors on the screen as well as download the errors as an Excel to view the error details in each row of the Excel sheet.



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-04 at 2.22.20 PM.png" alt=""><figcaption><p>View when the user clicks on ‘View errors’</p></figcaption></figure>

* The user will be able to navigate through the different errors using the ‘Previous’ or ‘Next’ buttons highlighted during data upload on the error view screen
* All the errors will be highlighted in red color
* On top of the preview screen, the user will be able to view the error details, for example, here the error mentioned that ‘Row 24 is empty!’
* The user will be able to download the Excel file with the detailed error mentioned. There should be an added column called ‘Error details’ that should show the errors in comma-separated format in case a single row has multiple errors
* On click of ‘Back’ the user should be exited from the error preview screen

d. Excel upload guideline - The guideline directs the user on what to keep in mind while entering the facility data and uploading it for the microplanning estimation. The guidelines are below for population data upload -

* All the fields are mandatory and can't be empty, except the Latitude and Longitude fields
* The Latitude & Longitude fields should have data in Degree Decimal and Degree Minute Seconds ( Value should be 12.3455 & not 12° 20' 43.7994")

6. **Data management process (Vehicle management) -**&#x20;

Actor: System administrator/Program manager

Administrative boundary: National/Country

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.39.09 AM.png" alt=""><figcaption><p>Managing campaign vehicles</p></figcaption></figure>

This screen will be used to set up the vehicles that are required for the campaign execution and microplanning estimation. Every vehicle to be used in the campaign needs to be added or chosen using this screen. The competent of this screen are -&#x20;

a. Choosing vehicle type - The user will be asked to select the vehicle type to show the list of vehicles that belong to the vehicle type. Choosing of vehicle type is a multi-select dropdown and upon showing the vehicle list for the chosen vehicle type, the user can choose different vehicles that will be used for campaign execution. The user can choose multiple vehicles at a time.

Validation: It is mandatory to choose at least 1 vehicle for the campaign

b. Showing vehicle details - Once the vehicle lists is shown to the user, the user can check-out the vehicle details and then choose which vehicles to be used for the campaign. The basic vehicle details that will be shown to the users per vehicle are:

1. Vehicle type
2. Manufacture
3. Model
4. Vehicle capacity - ‘Bales’ for bednets/ ‘Blisters’ for SMC

c. Adding new vehicle details - If the user doesn’t find the vehicle details, he will be asked to add new vehicle details for the campaign. All the fields are mandatory here for adding a new vehicle.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.40.51 AM.png" alt=""><figcaption><p>Adding a new vehicle</p></figcaption></figure>

The fields that the user can configure while adding new vehicle information are -

a. Vehicle type - If there is no vehicle type registered for the instance, then the user will get only one option to choose ‘Others’ to add the vehicle type.&#x20;

b. Enter vehicle type - If the vehicle type is chosen as ‘Others’, the user will be asked to enter the vehicle type. It’s a mandatory field.

c. Enter vehicle manufacturer - The user will be asked to enter the vehicle manufacturer details. It’s a mandatory field.

d. Enter vehicle model - The user will be asked to enter the vehicle model details here. It’s a mandatory field.

e. Enter vehicle capacity (Bales/Blisters) - The vehicle capacity will be defined as ‘Bales’ for bednets and ‘Blisters’ for SPAQ/SMC. It’s a mandatory field.

Validation: The capacity input value must be numerical. Error message if the capacity is invalid ‘The value must be numerical’.

f. Submit - Once the vehicle details are entered here, the user will be directed to submit the details and the vehicle details will be saved in the MDMS for the instance.

7. **Microplan hypothesis and formula configuration -**

Actor: System administrator/Program manager

Administrative boundary: National/Country

Case A: When the resource distribution strategy is ‘House-to-House’ and the campaign type is either ‘Bednets’ or ‘SMC’

Sub-Case 1:&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.43.49 AM.png" alt=""><figcaption><p>Preliminary questions for configuring microplan hypothesis</p></figcaption></figure>

Figma sample for choosing preliminary questions (Resource distribution strategy = House-to-House):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.44.51 AM.png" alt=""><figcaption></figcaption></figure>

Q1. How is the campaign registration process happening?

* The user will have only one option to choose from the dropdown ‘House-to-House’

Q2. How is the campaign distribution process happening?

* The user will have only one option to choose from the dropdown ‘House-to-House’

Q3. Is the registration and distribution process happening together or separately?

* The user will have one of the two options to choose from the dropdown either ‘Together’ or ‘Separately’. Here, the user will choose ‘Together’.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.46.08 AM.png" alt=""><figcaption><p>Customised ‘BEDNET’ microplan hypothesis depending on the questions answered above</p></figcaption></figure>

\
Figma sample for assumption config 1 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.47.09 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 2 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.47.46 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 3 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.48.59 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 4 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.49.51 AM.png" alt=""><figcaption></figcaption></figure>

Validation: The input value of an assumption must be numerical and mandatory

Error message in case of invalid input “Please enter a numeric value”



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.50.38 AM.png" alt=""><figcaption><p>Customised ‘SMC’ microplan hypothesis depending on the questions answered above</p></figcaption></figure>

Figma sample for assumption config 1 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.51.30 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 2 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.52.25 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 3 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.53.07 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 4 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.53.51 AM.png" alt=""><figcaption></figcaption></figure>

Validation: The input value of an assumption must be numerical and mandatory

Error message in case of invalid input “Please enter a numeric value”

In the above images, all the microplan hypotheses are pre-configured in the MDMS.

The user can add new microplan assumptions or delete an old assumption according to the campaign needs. All the microplan assumptions are configured for the village or lowest boundary level.

Upon adding a new microplan assumption, the user will be asked to enter the assumption and attach a value to it. The same assumption will be used in the microplan resource estimation formula.

If an assumption is deleted, upon adding a new assumption the user will be asked choose to either the deleted assumption or create a new assumption.

Depending on the microplan hypothesis configured, the user will be able to check-out the resource estimation formula and then make changes in the formula configuration accordingly.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.54.52 AM.png" alt=""><figcaption><p>Customised microplan resource estimation formula (For BEDNET)</p></figcaption></figure>

Figma sample for formula config 1 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.56.05 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 2 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.56.47 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 3 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.57.37 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 4 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.58.17 AM.png" alt=""><figcaption></figcaption></figure>



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.58.32 AM.png" alt=""><figcaption><p>Customised microplan resource estimation formula (For SMC)</p></figcaption></figure>

Figma sample for formula config 1 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 9.59.55 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 2 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.00.45 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 3 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.01.34 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 4 (SMC):



\
In the above images, all the microplan resource estimation formulas are pre-configured in the MDMS.

The user can add a new estimation formula or delete an old formula according to the campaign needs. All the microplan estimation formulas are configured on the village or lowest boundary level. All the values shown will be auto reflected in the microplan estimation dashboard, unless the user wants to disable the ‘Show on estimation dashboard’ checkbox.

If a pre-defined formula is deleted, upon adding a new formula, the user should get an option either to add the deleted formula or add a completely new formula.

Upon adding a completely new estimation formula, the user will be asked to -

1. Enter the parameter of the resource estimation
2. Formula inputs
3. Operator (\*,-,+,/)

Eg:  Number of bednets (Resource estimation parameter) = Target population (Input) / Number of people per bednet (Input)

Sub-Case 2:

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.07.05 AM.png" alt=""><figcaption><p>Preliminary questions for configuring microplan hypothesis</p></figcaption></figure>

Figma sample for choosing preliminary questions (Resource distribution strategy = House-to-House):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.08.36 AM.png" alt=""><figcaption></figcaption></figure>

Q1. How is the campaign registration process happening?

* The user will have only one option to choose from the dropdown ‘House-to-House’

Q2. How is the campaign distribution process happening?

* The user will have only one option to choose from the dropdown ‘House-to-House’

Q3. Is the registration and distribution process happening together or separately?

* The user will have one of the two options to choose from the dropdown either ‘Together’ or ‘Separately’. Here, the user will choose ‘Separately’.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.11.12 AM.png" alt=""><figcaption><p>Customised ‘BEDNET’ microplan hypothesis depending on the questions answered above</p></figcaption></figure>

Figma sample for assumption config 1 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.28.15 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 2 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.30.14 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 3 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.30.58 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 4 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.31.40 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 5 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.32.34 AM.png" alt=""><figcaption></figcaption></figure>

Validation: The input value of an assumption must be numerical and mandatory

Error message in case of invalid input “Please enter a numeric value”



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.33.50 AM.png" alt=""><figcaption><p>Customised ‘SMC’ microplan hypothesis depending on the questions answered above</p></figcaption></figure>

Figma sample for assumption config 1 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.34.41 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 2 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.35.20 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 3 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.36.00 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 4 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.36.40 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 5 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.37.56 AM.png" alt=""><figcaption></figcaption></figure>

Validation: The input value of an assumption must be numerical and mandatory

Error message in case of invalid input “Please enter a numeric value”

In the above images, all the microplan hypotheses are pre-configured in the MDMS.

The user can add new microplan assumptions or delete an old assumption according to the campaign needs. All the microplan assumptions are configured on the village or lowest boundary level.

Upon adding a new microplan assumption, the user will be asked to enter the assumption and attach a value to it. The same assumption will be used in the microplan resource estimation formula. If an assumption is deleted, upon adding a new assumption the user will be asked to choose to either the deleted assumption or create a new assumption.

Depending on the microplan hypothesis configured, the user will be able to check-out the resource estimation formula and then make changes in the formula configuration accordingly.



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.45.06 AM.png" alt=""><figcaption><p>Customized microplan resource estimation formula (For Bednets)</p></figcaption></figure>

Figma sample for formula config 1 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.46.12 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 2 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.46.55 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 3 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.47.35 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 4 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.48.25 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 5 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.49.05 AM.png" alt=""><figcaption></figcaption></figure>

\
<br>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.50.53 AM.png" alt=""><figcaption><p>Customised microplan resource estimation formula (For SMC)</p></figcaption></figure>

Figma sample for formula config 1 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.51.44 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 2 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.52.18 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 3 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.52.40 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 4 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 10.58.48 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 5 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.00.00 AM.png" alt=""><figcaption></figcaption></figure>

In the above images, all the microplan resource estimation formulas are pre-configured in the MDMS.

The user can add a new estimation formula or delete an old formula according to the campaign's needs. All the microplan estimation formulas are configured on the village or lowest boundary level. All the values shown will be auto-reflected in the microplan estimation dashboard unless the user wants to disable the "Show on estimation dashboard" checkbox.

If a pre-defined formula is deleted, upon adding a new formula, the user should get an option either to add the deleted formula or add a completely new formula.

Upon adding a new estimation formula, the user will be asked to -

1. Enter the parameter of the resource estimation
2. Formula inputs
3. Operator (\*,-,+,/)

Example:  Number of bednets (Resource estimation parameter) = Target population (Input) / Number of people per bednet (Input)

Case B: When the resource distribution strategy is ‘Fixed post’ and the campaign type is either ‘Bednets’ or ‘SMC’

Sub-case 1:

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.01.32 AM.png" alt=""><figcaption><p>Preliminary questions for configuring microplan hypothesis</p></figcaption></figure>



Figma sample for choosing preliminary questions (Resource distribution strategy = Fixed post):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.06.17 AM.png" alt=""><figcaption></figcaption></figure>

Q1. How is the campaign registration process happening?

* The user will have only one option to choose from the dropdown ‘Fixed post’

Q2. How is the campaign distribution process happening?

* The user will have only one option to choose from the dropdown ‘Fixed post’

Q3. Is the registration and distribution process happening together or separately?

* The user will have one of the two options to choose from the dropdown either ‘Together’ or ‘Separately’. Here, the user will choose ‘Together’.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.08.01 AM.png" alt=""><figcaption><p>Customised ‘BEDNET’ microplan hypothesis depending on the questions answered above</p></figcaption></figure>

Figma sample for assumption config 1 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.09.17 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 2 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.13.55 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 3 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.14.49 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 4 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.15.36 AM.png" alt=""><figcaption></figcaption></figure>

Validation: The input value of an assumption must be numerical and mandatory

Error message in case of invalid input “Please enter a numeric value”

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.16.31 AM.png" alt=""><figcaption><p>Customised ‘SMC’ microplan hypothesis depending on the questions answered above</p></figcaption></figure>

Figma sample for assumption config 1 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.17.27 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 2 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.18.05 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 3 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.18.53 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 4 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.19.35 AM.png" alt=""><figcaption></figcaption></figure>

Validation: The input value of an assumption must be numerical and mandatory

Error message in case of invalid input “Please enter a numeric value”

In the above images, all the microplan hypotheses are pre-configured in the MDMS.

The user can add new microplan assumptions or delete an old assumption according to the campaign needs. All the microplan assumptions are configured on the village or lowest boundary level.

Upon adding a new microplan assumption, the user will be asked to enter the assumption and attach a value to it. The same assumption will be used in the microplan resource estimation formula.

If an assumption is deleted, upon adding a new assumption the user will be asked to choose to either delete the assumption or create a new assumption.

Depending on the microplan hypothesis configured, the user will be able to check the resource estimation formula and then make changes in the formula configuration accordingly.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.21.15 AM.png" alt=""><figcaption><p>Customised microplan resource estimation formula (For Bednet)</p></figcaption></figure>

Figma sample for formula config 1 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.22.17 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 2 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.23.25 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 3 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.24.12 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 4 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.25.00 AM.png" alt=""><figcaption></figcaption></figure>

<br>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.25.27 AM.png" alt=""><figcaption><p>Customised microplan resource estimation formula (For SMC)</p></figcaption></figure>

Figma sample for formula config 1 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.26.20 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 2 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.27.06 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 3 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.27.30 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 4 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.28.34 AM.png" alt=""><figcaption></figcaption></figure>

In the above images, all the microplan resource estimation formula are pre-configured in the MDMS.

The user can add a new estimation formula or delete an old formula according to the campaign's needs. All the microplan estimation formulas are configured on the village or lowest boundary level. All the values shown will be auto-reflected in the microplan estimation dashboard unless the user wants to disable the "Show on estimation dashboard" checkbox.

If a pre-defined formula is deleted, upon adding a new formula, the user should get an option either to add the deleted formula or add a completely new formula.

Upon adding a new estimation formula, the user will be asked to -

4. Enter the parameter of the resource estimation
5. Formula inputs
6. Operator (\*,-,+,/)

Example:  Number of bednets (Resource estimation parameter) = Target population (Input) / Number of people per bednet (Input)

Sub-case 2:



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.30.02 AM.png" alt=""><figcaption><p>Preliminary questions for configuring microplan hypothesis</p></figcaption></figure>

Figma sample for choosing preliminary questions (Resource distribution strategy = Fixed post):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.30.52 AM.png" alt=""><figcaption></figcaption></figure>

Q1. How is the campaign registration process happening?

* The user will have only one option to choose from the dropdown ‘Fixed post’

Q2. How is the campaign distribution process happening?

* The user will have only one option to choose from the dropdown ‘Fixed post’

Q3. Is the registration and distribution process happening together or separately?

* The user will have one of the two options to choose from the dropdown either ‘Together’ or ‘Separately’. Here, the user will choose ‘Separately’.



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.31.38 AM.png" alt=""><figcaption><p>Customised ‘BEDNET’ microplan hypothesis depending on the questions answered above</p></figcaption></figure>

\
Figma sample for assumption config 1 (Bednet):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.32.29 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 2 (Bednet):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.35.30 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 3 (Bednet):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.36.18 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 4 (Bednet):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.36.59 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 5 (Bednet):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.37.48 AM.png" alt=""><figcaption></figcaption></figure>

Validation: The input value of an assumption must be numerical and mandatory

Error message in case of invalid input “Please enter a numeric value”



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.38.52 AM.png" alt=""><figcaption><p>Customised ‘SMC’ microplan hypothesis depending on the questions answered above</p></figcaption></figure>

Figma sample for assumption config 1 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.39.59 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 2 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.40.44 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 3 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.41.27 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 4 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.42.08 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 5 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.42.52 AM.png" alt=""><figcaption></figcaption></figure>

Validation: The input value of an assumption must be numerical and mandatory

Error message in case of invalid input “Please enter a numeric value”

In the above images, all the microplan hypotheses are pre-configured in the MDMS.

The user can add new microplan assumptions or delete an old assumption according to the campaign needs. All the microplan assumptions are configured on the village or lowest boundary level.

Upon adding a new microplan assumption, the user will be asked to enter the assumption and attach a value to it. The same assumption will be used in the microplan resource estimation formula.

If an assumption is deleted, upon adding a new assumption the user will be asked to choose to either the deleted assumption or create a new assumption.

Depending on the microplan hypothesis configured, the user will be able to check the resource estimation formula and then make changes in the formula configuration accordingly.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.44.08 AM.png" alt=""><figcaption><p>Customised microplan resource estimation formula (For Bednets)</p></figcaption></figure>

Figma sample for formula config 1 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.46.11 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 2 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.46.52 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 3 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.47.32 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 4 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.48.14 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 5 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.48.33 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.49.31 AM.png" alt=""><figcaption><p>Customised microplan resource estimation formula (For SMC)</p></figcaption></figure>

Figma sample for formula config 1 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.50.31 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 2 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.51.08 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 3 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.51.58 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 4 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.52.54 AM.png" alt=""><figcaption></figcaption></figure>

Figma sample for formula config 5 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.53.51 AM.png" alt=""><figcaption></figcaption></figure>

In the above images, all the microplan resource estimation formulas are pre-configured in the MDMS.

The user can add a new estimation formula or delete an old formula according to the campaign's needs. All the microplan estimation formulas are configured on the village or lowest boundary level. All the values shown will be auto-reflected in the microplan estimation dashboard unless the user wants to disable the "Show on estimation dashboard" checkbox.

If a pre-defined formula is deleted, upon adding a new formula, the user should get an option either to add the deleted formula or add a completely new formula.

Upon adding a new estimation formula, the user will be asked to -

7. Enter the parameters of the resource estimation
8. Formula inputs
9. Operator (\*,-,+,/)

Example: Number of bednets (Resource estimation parameter) = Target population (Input) / Number of people per bednet (Input)

Case C: When the resource distribution strategy is ‘Fixed post & House-to-House’ and the campaign type is either ‘Bednets’ or ‘SMC’

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.55.23 AM.png" alt=""><figcaption><p>Preliminary questions for configuring microplan hypothesis</p></figcaption></figure>

Figma sample for choosing preliminary questions (Resource distribution strategy = House-to-House & Fixed post):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.56.23 AM.png" alt=""><figcaption></figcaption></figure>

Q1. How is the campaign registration process happening?

* The user can choose either ‘Fixed post’ or ‘House-to-House’ or both

Q2. How is the campaign distribution process happening?

* The user can choose either ‘Fixed post’ or ‘House-to-House’ or both

Depending on the registration and distribution process chosen, the microplan assumption will be shown to the user for configuration.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 11.57.30 AM.png" alt=""><figcaption><p>Customised ‘BEDNET’ microplan hypothesis depending on the questions answered above</p></figcaption></figure>

Figma sample for assumption config 1 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 12.03.05 PM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 2 (Bednets):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 12.03.47 PM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 3 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 12.04.28 PM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 4 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 12.05.13 PM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 5 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 12.05.40 PM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 6 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 12.06.26 PM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 7 (Bednets):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 12.06.50 PM.png" alt=""><figcaption></figcaption></figure>

Validation: The input value of an assumption must be numerical and mandatory

Error message in case of invalid input “Please enter a numeric value”

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 12.09.12 PM.png" alt=""><figcaption><p>Customised ‘SMC’ microplan hypothesis depending on the questions answered above</p></figcaption></figure>

Figma sample for assumption config 1 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 2.16.20 PM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 2 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 2.18.08 PM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 3 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 2.18.49 PM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 4 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 2.19.21 PM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 5 (SMC):



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 2.19.55 PM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 6 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 2.20.57 PM.png" alt=""><figcaption></figcaption></figure>

Figma sample for assumption config 7 (SMC):

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 2.21.21 PM.png" alt=""><figcaption></figcaption></figure>

Validation: The input value of an assumption must be numerical and mandatory

Error message in case of invalid input “Please enter a numeric value”

In the above images, all the microplan hypotheses are pre-configured in the MDMS.

The user can add new microplan assumptions or delete an old assumption according to the campaign needs. All the microplan assumptions are configured on the village or lowest boundary level.

Upon adding a new microplan assumption, the user will be asked to enter the assumption and attach a value to it. The same assumption will be used in the microplan resource estimation formula.

If an assumption is deleted, upon adding a new assumption the user will be asked choose to either the deleted assumption or create a new assumption.

Depending on the microplan hypothesis configured, the user will be able to check the resource estimation formula and then make changes in the formula configuration accordingly.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 2.23.55 PM.png" alt=""><figcaption><p>Customised microplan resource estimation formula (For Bednets)</p></figcaption></figure>



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 2.22.53 PM.png" alt=""><figcaption><p>Customised microplan resource estimation formula (For SMC)</p></figcaption></figure>

In the above images, all the microplan resource estimation formulas are pre-configured in the MDMS.

The user can add a new estimation formula or delete an old formula according to the campaign's needs. All the microplan estimation formulas are configured on the village or lowest boundary level. All the values shown will be auto-reflected in the microplan estimation dashboard unless the user wants to disable the ‘Show on estimation dashboard’ checkbox.

If a pre-defined formula is deleted, upon adding a new formula, the user should get an option either to add the deleted formula or add a completely new formula.

Upon adding a new estimation formula, the user will be asked to -

1. Enter the parameter of the resource estimation
2. Formula inputs
3. Operator (+,-,\*,/)

Example:  Number of bednets (Resource estimation parameter) = Target population (Input 1) / Number of people per bednet (Input 2)

8. **Manage data validation -**

Actor: System administrator/Program manager

Administrative boundary: National/Country

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-09 at 2.27.54 PM.png" alt=""><figcaption><p>Managing the data validation rule to highlight data discrepancies</p></figcaption></figure>

This screen will be used to set up the data validation rule to highlight the population data discrepancies submitted by the ‘Data collector’ from the ground.

This process will help specifically in identifying if the population data collected and validated by the data collector for certain villages is correct or not. For example, the central team called out that a village has a total population of 2,000. However, while validating the data, the data collector at the village level mentioned that the total population of the village is 5000, which is more than 100% of what was earlier uploaded by the central team. With such cases, it becomes important for the data approver to have a second look at the data and make necessary adjustments in the village population data that can be used for microplan resource estimation.

The content of this screen are -

a. Minimum population of a village in Mozambique: In this field, the user needs to enter the minimum possible population of a village within the campaign region. This ensures that if the ‘Data collector’ validates and collects the total and target population for a village, which is less than the minimum village population configured, it should right away be highlighted to the assigned ‘Population data approver’ role. Here, the country name can be different for different countries, so it has to be configurable depending on the instance created for the country.

Validation: The field must accept a whole number value. Throw the error “Please enter a whole number” if an invalid value is entered.

b. The maximum population of a village in Mozambique: In this field, the user needs to enter the maximum possible population of a village within the campaign region. This ensures that if the ‘Data collector’ validates and collects the total and target population for a village, which is more than the maximum village population configured, it should right away be highlighted to the assigned ‘Population data approver’ role. Here, the country name can be different for different countries, so it has to be configurable depending on the instance created for the country.

Validation: The field must accept a whole number value. Throw the error “Please enter a whole number” if an invalid value is entered.

c. Acceptable change percentage (%) concerning population data uploaded for the villages: In this field, the user needs to enter the acceptable buffer % w.r.t to which the system will not highlight the data discrepancies. For example, if the acceptable change percentage is 10%, and the central team uploaded the total village population of Village-1 as 1000, then the acceptable population range is between 900 to 1100. So, if the ‘Data collector’ validates and collects the village-1 population as 1050, the system will not highlight the data discrepancies to the ‘Population data approver’ user, but if the ‘Data collector’ validates and collects the village-1 population as 1200, the system will highlight the data discrepancies to the ‘Population data approver’ user.&#x20;

Validation: The field must accept a numeric value. Throw error “Please enter a numeric value” if invalid value entered.

d. Next: The user can move to the next screen to configure the role-action mapping&#x20;

e. Back: The user can choose to go back to the previous screen of the estimation formula configuration by clicking ‘Back’

Note: The data validation rule configuration isn’t mandatory and the user can move to the next screen without configuration by clicking the ‘Next’ button

9. **Configure access control -**

Actor: System administrator/Program manager

Administrative boundary: National/Country

**Role configuration - National microplan approver**

This role will have access to edit microplan assumptions and approve and finalise microplan estimation for the country.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 9.44.44 AM.png" alt=""><figcaption><p>Screen showing ‘National Microplan Estimation Approver’ role users assigned for the current microplan</p></figcaption></figure>

This screen will be used to configure the ‘National Microplan Estimation Approver’ user role. The assigned user will be able to validate and approve the population data from each village uploaded by the system administrator. The user will only be able to act on the population data of the villages that are assigned to his administrative boundary, i.e., country.

During the configuration of the microplan, there will be no users belonging to the ‘National microplan estimation approver’ role assigned to the ongoing microplan at first. The system administrator will have to click on the button ‘Assign National Microplan Estimation Approvers’ to start assigning the required users to the ongoing microplan.

Once the system administrator clicks on the ‘Assign National Microplan Estimation Approvers’ button, he/she will be prompted a pop-up to assign the users with ‘National Microplan Estimation Approver’ role to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.18.27 AM.png" alt=""><figcaption><p>Pop-up for assigning the national microplan estimation approvers to the microplan</p></figcaption></figure>

Here, the system admin will be able to assign/deassign a user to the ongoing microplan. The content of the pop-up are -

* Search filters - The system admin can search a user using the ‘User’s name’ and ‘User’s contact number’.

&#x20;      Validation: Partial string search should be allowed

* Name of the user - This will be fetched from the user management module for the chosen role.
* Contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - This will be auto chosen as ‘Country’ as this user role belongs to the national level. The system administrator shouldn’t get any other administrative hierarchies to choose from.
* Administrative area - This will be automatically chosen as the country where the microplan is being configured. The system administrator shouldn’t get any other administrative area to choose from.
* Action - This capability will let the system administrator to assign/deassign users of the chosen role to the ongoing microplan. The system administrator can add at least one or more ‘National microplan estimation approver’ users to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.20.54 AM.png" alt=""><figcaption><p>Pop-up for assigning/deassigning the users of the chosen role to the microplan</p></figcaption></figure>

This pop-up shows the actions that the user can take. The ‘Assign’ button should only be enabled if the system administrator has chosen the administrative hierarchy and the administrative area for a particular user belonging to the role chosen.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.22.27 AM.png" alt=""><figcaption><p>Screen showing assigned users to the ongoing microplan</p></figcaption></figure>

Once the system administrator has assigned all the required users to the microplan, the list of assigned users and their details will be displayed on the screen. Content of the screen are -

* Search assigned users - The system admin will be able to search a user using the ‘User’s name’.

&#x20;      Validation: Partial string search should be allowed

* Assign users - This action will let the system administrator to assign/deassign users to the microplan.
* Name of the user - This will be fetched from the user management module for the chosen role.
* Contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - This will be fetched from the user data that will be used while assigning the user to the microplan.
* Administrative area - This will be fetched from the user data that will be used while assigning the user to the microplan.

Once all the required users are added to the microplan, the system administrator will click on the ‘Save And Proceed’ button to go to the next role assignment screen.

Note: It’s mandatory to assign at least 1 ‘National microplan estimation approver’ user to the microplan.

**Role configuration - National facility catchment assigner**

This role will have access to assign & finalize the facility to the catchment areas of the assigned administrative boundary.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.24.06 AM.png" alt=""><figcaption><p>Screen showing ‘National Facility Catchment Assigner’ role users assigned for the current microplan</p></figcaption></figure>

This screen will be used to configure the ‘National facility catchment assigner’ user role. The assigned facility catchment assigner will be allowed to map the campaign facilities or point of services to the catchment areas and to finalize the facility-to-catchment area mapping (Eg: Villages) of the assigned boundaries.

During the configuration of the microplan, there will be no users belonging to the ‘National facility catchment assigner’ role assigned to the ongoing microplan at first. The system administrator will have to click on the button ‘Assign National Facility Catchment Assigner’ to start assigning the required users to the ongoing microplan.

Once the system administrator clicks on the ‘Assign National Facility Catchment Assigner’ button, he/she will be prompted a pop-up to assign the users with the ‘National Facility Catchment Assigner’ role to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.30.07 AM.png" alt=""><figcaption><p>Pop-up for assigning the national facility catchment assigner to the microplan</p></figcaption></figure>

Here, the system admin will be able to assign/deassign a user to the ongoing microplan. The content of the pop-up are -

* Search filters - The system admin can search a user using the ‘User’s name’ and ‘User’s contact number’.

&#x20;      Validation: Partial string search should be allowed

* Name of the user - This will be fetched from the user management module for the chosen role.
* Contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - This will be auto chosen as ‘Country’ as this user role belongs to the national level. The system administrator shouldn’t get any other administrative hierarchies to choose from.
* Administrative area - This will be automatically chosen as the country where the microplan is being configured. The system administrator shouldn’t get any other administrative area to choose from.
* Action - This capability will let the system administrator assign/deassign users of the chosen role to the ongoing microplan. The system administrator can add at least one or more ‘National facility catchment assigner’ users to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.31.34 AM.png" alt=""><figcaption><p>Pop-up for assigning/deassigning the users of the chosen role to the microplan</p></figcaption></figure>

This pop-up shows the actions that the user can take. The ‘Assign’ button should only be enabled if the system administrator has chosen the administrative hierarchy and the administrative area for a particular user belonging to the role chosen.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.32.49 AM.png" alt=""><figcaption><p>Screen showing assigned users to the ongoing microplan</p></figcaption></figure>

Once the system administrator has assigned all the required users to the microplan, the list of assigned users and their details will be displayed on the screen. The content of the screen are -

* Search assigned users - The system admin can search a user using the ‘User’s name’.

&#x20;      Validation: Partial string search should be allowed

* Assign users - This action will let the system administrator assign/deassign users to the microplan.
* Name of the user - This will be fetched from the user management module for the chosen role.
* Contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - This will be fetched from the user data that will be used while assigning the user to the microplan.
* Administrative area - This will be fetched from the user data that will be used while assigning the user to the microplan.

Once all the required users are added to the microplan, the system administrator will click on the ‘Save And Proceed’ button to go to the next role assignment screen.

Note: It’s mandatory to assign at least 1 ‘National facility catchment assigner’ user to the microplan.

**Role configuration - National population data approver**

This role will have access to validate, approve, and finalise the population data for the villages of the assigned administrative boundary.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.36.51 AM.png" alt=""><figcaption><p>Screen showing ‘National Population Data Approver’ role users assigned for the current microplan</p></figcaption></figure>

This screen will be used to configure the ‘National population data approver’ user role. The assigned user will be able to validate, update, and approve the population data of each village uploaded by the system administrator. The user will only be able to act on the population data of the villages that are assigned to his administrative boundary.

During the configuration of the microplan, there will be no users belonging to the ‘National population data approver’ role assigned to the ongoing microplan at first. The system administrator will have to click on the button ‘Assign National Population Data Approver’ to start assigning the required users to the ongoing microplan.

Once the system administrator clicks on the ‘Assign National Population Data Approver’ button, he/she will be prompted a pop-up to assign the users with the ‘National Population Data Approver’ role to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.44.36 AM.png" alt=""><figcaption><p>Pop-up for assigning the national population data approver to the microplan</p></figcaption></figure>

Here, the system admin will be able to assign/deassign a user to the ongoing microplan. The content of the pop-up are -

* Search filters - The system admin can search a user using the ‘User’s name’ and ‘User’s contact number’.

&#x20;      Validation: Partial string search should be allowed

* Name of the user - This will be fetched from the user management module for the chosen role.
* The contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - This will be auto-chosen as ‘Country’ as this user role belongs to the national level. The system administrator shouldn’t get any other administrative hierarchies to choose from.
* Administrative area - This will be automatically chosen as the country where the microplan is being configured. The system administrator shouldn’t get any other administrative area to choose from.
* Action - This capability will let the system administrator assign/deassign users of the chosen role to the ongoing microplan. The system administrator can add at least one or more ‘National population data approver’ users to the ongoing microplan.\\

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.50.09 AM.png" alt=""><figcaption><p>Pop-up for assigning/deassigning the users of the chosen role to the microplan</p></figcaption></figure>

This pop-up shows the actions that the user can take. The ‘Assign’ button should only be enabled if the system administrator has chosen the administrative hierarchy and the administrative area for a particular user belonging to the role chosen.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.52.25 AM.png" alt=""><figcaption><p>Screen showing assigned users to the ongoing microplan</p></figcaption></figure>

Once the system administrator has assigned all the required users to the microplan, the list of assigned users and their details will be displayed on the screen. The content of the screen are -

* Search assigned users - The system admin can search a user using the ‘User’s name’.

&#x20;      Validation: Partial string search should be allowed

* Assign users - This action will let the system administrator assign/deassign users to the microplan.
* Name of the user - This will be fetched from the user management module for the chosen role.
* Contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - This will be fetched from the user data that will be used while assigning the user to the microplan.
* Administrative area - This will be fetched from the user data that will be used while assigning the user to the microplan.

Once all the required users are added to the microplan, the system administrator will click on the ‘Save And Proceed’ button to go to the next role assignment screen.

Note: It’s mandatory to assign at least 1 ‘National population data approver’ user to the microplan.

**Role configuration - Microplan estimation approver**

This role will have access to edit microplan assumptions and approve microplan estimation of assigned administrative boundaries.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.54.23 AM.png" alt=""><figcaption><p>Screen showing ‘Microplan estimation approver’ role users assigned for the current microplan</p></figcaption></figure>

This screen will be used to configure the ‘Microplan estimation approver’ user role. The assigned Microplan estimation approver will be allowed to edit the microplan hypothesis, and validate and approve the microplan for the assigned administrative boundaries.

During the configuration of the microplan, there will be no users belonging to the ‘Microplan estimation approver’ role assigned to the ongoing microplan at first. The system administrator will have to click on the button ‘Assign Microplan Estimation Approvers’ to start assigning the required users to the ongoing microplan.

Once the system administrator clicks on the ‘Assign Microplan Estimation Approvers’ button, he/she will be prompted a pop-up to assign the users with ‘Microplan Estimation Approvers’ role to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 10.59.03 AM.png" alt=""><figcaption><p>Pop-up for assigning the microplan estimation approver to the microplan</p></figcaption></figure>

Here, the system admin will be able to assign/deassign a user to the ongoing microplan. The content of the pop-up are -

* Search filters - The system admin can search a user using the ‘User’s name’ and ‘User’s contact number’.

&#x20;      Validation: Partial string search should be allowed

* Name of the user - This will be fetched from the user management module for the chosen role.
* The contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - The system administrator will be able to choose the administrative hierarchy from the dropdown. The system admin can choose one administrative hierarchy at a time. The system admin can’t choose the highest administrative hierarchy (Eg: Country) and the lowest administrative hierarchy (Eg: Village/Settlement) from the dropdown.
* Administrative area - Upon choosing the administrative hierarchy, the system administrator will be able to choose the administrative areas for the chosen administrative hierarchy. The system administrator will be able to choose one or multiple administrative areas at a time. The list of administrative areas should be shown along with their respective parent boundaries.
* Action - This capability will let the system administrator assign/deassign users of the chosen role to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 11.05.32 AM.png" alt=""><figcaption><p>Pop-up for assigning/deassigning the users of the chosen role to the microplan</p></figcaption></figure>

This pop-up shows the actions that the user can take. The ‘Assign’ button should only be enabled if the system administrator has chosen the administrative hierarchy and the administrative area for a particular user in the selected role.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 11.49.04 AM.png" alt=""><figcaption><p>Screen showing assigned users to the ongoing microplan</p></figcaption></figure>

Once the system administrator has assigned all the required users to the microplan, the list of assigned users and their details will be displayed on the screen. The content of the screen are -

* Search assigned users - The system admin can search a user using the ‘User’s name’.

&#x20;      Validation: Partial string search should be allowed

* Assign users - This action will let the system administrator assign/deassign users to the microplan.
* Name of the user - This will be fetched from the user management module for the chosen role.
* The contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - This will be fetched from the user data that will be used while assigning the user to the microplan.
* Administrative area - This will be fetched from the user data that will be used while assigning the user to the microplan.

Once all the required users are added to the microplan, the system administrator will click on the ‘Save And Proceed’ button to go to the next role assignment screen.

Validations for the ‘Microplan estimation approver’ role:

<table data-header-hidden><thead><tr><th width="155"></th><th width="139"></th><th width="143"></th><th width="175"></th><th width="148"></th><th></th></tr></thead><tbody><tr><td>Role</td><td>User mapped?</td><td>Administrative hierarchy</td><td>Administrative areas assigned?</td><td>Warning message</td><td>Action on warning</td></tr><tr><td>Microplan estimation approver</td><td>No</td><td>-</td><td>-</td><td>There is no ‘Microplan estimation approver’ assigned to the microplan. Are you sure to continue without assigning ‘Microplan estimation approver’?</td><td><p>Choice A (Highlighted button) - No, I don’t want to continue</p><p>Choice B - Yes, I want to continue</p></td></tr><tr><td>Microplan estimation approver</td><td>Yes</td><td>Province/district/Admin post/Locality</td><td>All province/district/Admin post/Locality</td><td><br></td><td><br></td></tr><tr><td>Microplan estimation approver</td><td>Yes</td><td>Province/district/Admin post/Locality</td><td>Some province/district/Admin post/Locality</td><td>‘Microplan estimation approver' role is assigned to only a few 'province/district/Admin post/Locality', would you like to proceed without assigning 'Microplan estimation approver' role to remaining 'province/district/Admin post/Locality'?</td><td><p>Choice A (Highlighted button) - No, I don’t want to proceed</p><p>Choice B - Yes, I want to proceed</p></td></tr></tbody></table>

&#x20;                        (Validation criteria for warning messages (Microplan estimation approver)

**Role configuration - Microplan estimation viewer**

This role will have access to view microplan estimations of assigned administrative boundaries.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-25 at 12.13.14 PM.png" alt=""><figcaption><p>Screen showing ‘Microplan estimation viewer’ role users assigned for the current microplan</p></figcaption></figure>

This screen will be used to configure the ‘Microplan estimation viewer’ user role. The assigned microplan estimation viewer will be allowed to view the microplan estimation for the assigned administrative boundaries.

During the configuration of the microplan, there will be no users belonging to the ‘Microplan estimation viewer’ role assigned to the ongoing microplan at first. The system administrator will have to click on the button ‘Assign Microplan Estimation Viewers’ to start assigning the required users to the ongoing microplan.

Once the system administrator clicks on the ‘Assign Microplan Estimation Viewers’ button, he/she will be prompted a pop-up to assign the users with the ‘Microplan Estimation Viewers’ role to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-27 at 11.11.04 AM.png" alt=""><figcaption><p>Pop-up for assigning the microplan estimation viewer to the microplan</p></figcaption></figure>

Here, the system admin will be able to assign/deassign a user to the ongoing microplan. The content of the pop-up are -

* Search filters - The system admin will be able to search a user using the ‘User’s name’ and ‘User’s contact number’.

&#x20;      Validation: Partial string search should be allowed

* Name of the user - This will be fetched from the user management module for the chosen role.
* Contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - The system administrator will be able to choose the administrative hierarchy from the dropdown. The system admin can choose one administrative hierarchy at a time. The system admin can’t choose the highest administrative hierarchy (Eg: Country) and the lowest administrative hierarchy (Eg: Village/Settlement) from the dropdown.
* Administrative area - Upon choosing the administrative hierarchy, the system administrator will be able to choose the administrative areas for the chosen administrative hierarchy. The system administrator will be able to choose one or multiple administrative areas at a time. The list of administrative areas should be shown along with their respective parent boundaries.
* Action - This capability will let the system administrator to assign/deassign users of the chosen role to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-27 at 12.05.21 PM.png" alt=""><figcaption><p>Pop-up for assigning/deassigning the users of the chosen role to the microplan</p></figcaption></figure>

This pop-up shows the actions that the user can take. The ‘Assign’ button should only be enabled if the system administrator has chosen the administrative hierarchy and the administrative area for a particular user belonging to the role chosen.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-27 at 12.06.47 PM.png" alt=""><figcaption><p>Screen showing assigned users to the ongoing microplan</p></figcaption></figure>

Once the system administrator has assigned all the required users to the microplan, the list of assigned users and their details will be displayed on the screen. Content of the screen are -

* Search assigned users - The system admin will be able to search a user using the ‘User’s name’.

&#x20;      Validation: Partial string search should be allowed

* Assign users - This action will let the system administrator to assign/deassign users to the microplan.
* Name of the user - This will be fetched from the user management module for the chosen role.
* Contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - This will be fetched from the user data that will be used while assigning the user to the microplan.
* Administrative area - This will be fetched from the user data that will be used while assigning the user to the microplan.

Once all the required users are added to the microplan, the system administrator will click on the ‘Save And Proceed’ button to go to the next role assignment screen.

Validations for the ‘Microplan estimation viewer’ role:

<table data-header-hidden><thead><tr><th width="142"></th><th width="141"></th><th width="213"></th><th width="183"></th><th width="153"></th><th></th></tr></thead><tbody><tr><td>Role</td><td>User mapped?</td><td>Administrative hierarchy</td><td>Administrative areas assigned</td><td>Warning message</td><td>Action on warning</td></tr><tr><td>Microplan estimation viewer</td><td>No</td><td>-</td><td>-</td><td>There is no ‘Microplan estimation viewer’ assigned to the microplan. Are you sure to continue without assigning ‘Microplan estimation viewer’?</td><td><p>Choice A (Highlighted button) - No, I don’t want to continue</p><p>Choice B - Yes, I want to continue</p></td></tr><tr><td>Microplan estimation viewer</td><td>Yes</td><td>Province/district/Admin post/Locality</td><td>All province/district/Admin post/Locality</td><td><br></td><td><br></td></tr><tr><td>Microplan estimation viewer</td><td>Yes</td><td>Province/district/Admin post/Locality</td><td>Some province/district/Admin post/Locality</td><td>‘Microplan estimation viewer' role is assigned to only a few 'province/district/Admin post/Locality', would you like to proceed without assigning 'Microplan estimation viewer' role to remaining 'province/district/Admin post/Locality'?</td><td><p>Choice A (Highlighted button) - No, I don’t want to proceed</p><p>Choice B - Yes, I want to proceed</p></td></tr></tbody></table>

&#x20;                                            (Validation criteria for warning messages (Microplan estimation viewer)

Note: It’s not mandatory to assign the Microplan estimation viewer to a microplan. The system administrator can skip and go to the next role management screen without assigning the users with Microplan estimation viewer role.

**Role configuration - Facility catchment assigner**

This role will have access to assign the facility to the catchment areas of the assigned administrative boundary.<br>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-27 at 12.11.13 PM.png" alt=""><figcaption><p>Screen showing ‘Facility catchment assigner’ role users assigned for the current microplan</p></figcaption></figure>

This screen will be used to configure the ‘Facility catchment assigner’ user role. The assigned facility catchment assigner will be allowed to map the campaign facilities or point of services to the catchment areas (Eg: Villages/Settlements) of the assigned boundaries.

During the configuration of the microplan, there will be no users belonging to the ‘Facility catchment assigner’ role assigned to the ongoing microplan at first. The system administrator will have to click on the button ‘Assign Facility Catchment Assigner’ to start assigning the required users to the ongoing microplan.

Once the system administrator clicks on the ‘Assign Facility Catchment Assigner’ button, he/she will be prompted a pop-up to assign the users with ‘Facility Catchment Assigner’ role to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-27 at 2.38.57 PM.png" alt=""><figcaption><p>Pop-up for assigning the facility catchment assigner to the microplan</p></figcaption></figure>

Here, the system admin will be able to assign/deassign a user to the ongoing microplan. The content of the pop-up are -

* Search filters - The system admin will be able to search a user using the ‘User’s name’ and ‘User’s contact number’.

&#x20;      Validation: Partial string search should be allowed

* Name of the user - This will be fetched from the user management module for the chosen role.
* Contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - The system administrator will be able to choose the administrative hierarchy from the dropdown. The system admin can choose one administrative hierarchy at a time. The system admin can’t choose the highest administrative hierarchy (Eg: Country) and the lowest administrative hierarchy (Eg: Village/Settlement) from the dropdown.
* Administrative area - Upon choosing the administrative hierarchy, the system administrator will be able to choose the administrative areas for the chosen administrative hierarchy. The system administrator will be able to choose one or multiple administrative areas at a time. The list of administrative areas should be shown along with their respective parent boundaries.
* Action - This capability will let the system administrator to assign/deassign users of the chosen role to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-27 at 2.39.48 PM.png" alt=""><figcaption><p>Pop-up for assigning/deassigning the users of the chosen role to the microplan</p></figcaption></figure>

This pop-up shows the actions that the user can take. The ‘Assign’ button should only be enabled if the system administrator has chosen the administrative hierarchy and the administrative area for a particular user belonging to the role chosen.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-27 at 2.40.47 PM.png" alt=""><figcaption><p>Screen showing assigned users to the ongoing microplan</p></figcaption></figure>

Once the system administrator has assigned all the required users to the microplan, the list of assigned users and their details will be displayed on the screen. Content of the screen are -

* Search assigned users - The system admin will be able to search a user using the ‘User’s name’.

Validation: Partial string search should be allowed

* Assign users - This action will let the system administrator to assign/deassign users to the microplan.
* Name of the user - This will be fetched from the user management module for the chosen role.
* Contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - This will be fetched from the user data that will be used while assigning the user to the microplan.
* Administrative area - This will be fetched from the user data that will be used while assigning the user to the microplan.

Once all the required users are added to the microplan, the system administrator will click on the ‘Save And Proceed’ button to go to the next role assignment screen.

Validations for ‘Facility catchment assigner’ role:

<table data-header-hidden><thead><tr><th width="154"></th><th width="114"></th><th width="195"></th><th width="183"></th><th width="163"></th><th></th></tr></thead><tbody><tr><td>Role</td><td>User mapped?</td><td>Administrative hierarchy</td><td>Administrative areas assigned</td><td>Warning message</td><td>Action on warning</td></tr><tr><td>Facility catchment assigner</td><td>No</td><td>-</td><td>-</td><td>There is no ‘Facility catchment assigner’ assigned to the microplan. Are you sure to continue without assigning ‘Facility catchment assigner’?</td><td><p>Choice A (Highlighted button) - No, I don’t want to continue</p><p>Choice B - Yes, I want to continue</p></td></tr><tr><td>Facility catchment assigner</td><td>Yes</td><td>Province/district/Admin post/Locality</td><td>All province/district/Admin post/Locality</td><td><br></td><td><br></td></tr><tr><td>Facility catchment assigner</td><td>Yes</td><td>Province/district/Admin post/Locality</td><td>Some province/district/Admin post/Locality</td><td>‘Facility catchment assigner' role is assigned to only a few 'province/district/Admin post/Locality', would you like to proceed without assigning 'Facility catchment assigner' role to remaining 'province/district/Admin post/Locality'?</td><td><p>Choice A (Highlighted button) - No, I don’t want to proceed</p><p>Choice B - Yes, I want to proceed</p></td></tr></tbody></table>

&#x20;                                   (Validation criteria for warning messages (Facility catchment assigner)

Note: It’s not mandatory to assign Facility catchment assigner to a microplan. The system administrator can skip and go to the next role management screen without assigning the users with Facility catchment assigner role.

**Role configuration - Population data approver**

This role will have access to validate & approve the population data for the villages of the assigned administrative boundary.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-27 at 2.42.57 PM.png" alt=""><figcaption><p>Screen showing ‘Population data approver’ role users assigned for the current microplan</p></figcaption></figure>

This screen will be used to configure the ‘Population data approver’ user role. The assigned user will be able to validate and approve the population data uploaded by the system administrator while setting up the microplan. The user will only be able to act on the population data of the villages that are assigned to his administrative boundaries.

During the configuration of the microplan, there will be no users belonging to the ‘Population data approver’ role assigned to the ongoing microplan at first. The system administrator will have to click on the button ‘Assign Population Data Approver’ to start assigning the required users to the ongoing microplan.

Once the system administrator clicks on the ‘Assign Population Data Approver’ button, he/she will be prompted a pop-up to assign the users with ‘Population Data Approver’ role to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-27 at 2.43.57 PM.png" alt=""><figcaption><p>Pop-up for assigning the population data approver to the</p></figcaption></figure>

Here, the system admin will be able to assign/deassign a user to the ongoing microplan. The content of the pop-up are -

* Search filters - The system admin will be able to search a user using the ‘User’s name’ and ‘User’s contact number’.

&#x20;      Validation: Partial string search should be allowed

* Name of the user - This will be fetched from the user management module for the chosen role.
* Contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - The system administrator will be able to choose the administrative hierarchy from the dropdown. The system admin can choose one administrative hierarchy at a time. The system admin can’t choose the highest administrative hierarchy (Eg: Country) and the lowest administrative hierarchy (Eg: Village/Settlement) from the dropdown.
* Administrative area - Upon choosing the administrative hierarchy, the system administrator will be able to choose the administrative areas for the chosen administrative hierarchy. The system administrator will be able to choose one or multiple administrative areas at a time. The list of administrative areas should be shown along with their respective parent boundaries.
* Action - This capability will let the system administrator to assign/deassign users of the chosen role to the ongoing microplan.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-27 at 2.44.52 PM.png" alt=""><figcaption><p>Pop-up for assigning/deassigning the users of the chosen role to the microplan</p></figcaption></figure>

This pop-up shows the actions that the user can take. The ‘Assign’ button should only be enabled if the system administrator has chosen the administrative hierarchy and the administrative area for a particular user belonging to the role chosen.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-27 at 2.45.42 PM.png" alt=""><figcaption><p>Screen showing assigned users to the ongoing microplan</p></figcaption></figure>

Once the system administrator has assigned all the required users to the microplan, the list of assigned users and their details will be displayed on the screen. Content of the screen are -

* Search assigned users - The system admin will be able to search a user using the ‘User’s name’.

Validation: Partial string search should be allowed

* Assign users - This action will let the system administrator to assign/deassign users to the microplan.
* Name of the user - This will be fetched from the user management module for the chosen role.
* Contact number of the user - This will be fetched from the user management module for the chosen role.
* Email ID of the user - This will be fetched from the user management module for the chosen role.
* Administrative hierarchy - This will be fetched from the user data that will be used while assigning the user to the microplan.
* Administrative area - This will be fetched from the user data that will be used while assigning the user to the microplan.

Once all the required users are added to the microplan, the system administrator will click on the ‘Save And Proceed’ button to go to the next role assignment screen.

Validations for ‘Population data approver’ role:

<table data-header-hidden><thead><tr><th width="166"></th><th width="136"></th><th width="146"></th><th width="148"></th><th width="139"></th><th></th></tr></thead><tbody><tr><td>Role</td><td>User mapped?</td><td>Administrative hierarchy</td><td>Administrative areas assigned</td><td>Warning message</td><td>Action on warning</td></tr><tr><td>Population data approver</td><td>No</td><td>-</td><td>-</td><td>There is no ‘Population data approver’ assigned to the microplan. Are you sure to continue without assigning ‘Population data approver’?</td><td><p>Choice A (Highlighted button) - No, I don’t want to continue</p><p>Choice B - Yes, I want to continue</p></td></tr><tr><td>Population data approver</td><td>Yes</td><td>Province/district/Admin post/Locality</td><td>All province/district/Admin post/Locality</td><td><br></td><td><br></td></tr><tr><td>Population data approver</td><td>Yes</td><td>Province/district/Admin post/Locality</td><td>Some province/district/Admin post/Locality</td><td>‘Population data approver' role is assigned to only a few 'province/district/Admin post/Locality', would you like to proceed without assigning 'Population data approver' role to remaining 'province/district/Admin post/Locality'?</td><td><p>Choice A (Highlighted button) - No, I don’t want to proceed</p><p>Choice B - Yes, I want to proceed</p></td></tr></tbody></table>

&#x20;                               (Validation criteria for warning messages (Population data approver

Note: It’s not mandatory to assign Population data approver to a microplan. The system administrator can skip and go to the next role management screen without assigning the users with Population data approver role.

10. **View summary page -**

Actor: System administrator/Program manager

Administrative boundary: National/Country

Once the microplan setup is completed, the user can review all the data configured before finalizing the microplan setup. The summary page will give the user the ability to review the configured data for each module. The summary page will let users edit the configured data if required.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 10.55.02 AM.png" alt=""><figcaption><p>Summary screen (Campaign Boundary)</p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 10.58.35 AM.png" alt=""><figcaption><p>Summary screen (Data management)</p></figcaption></figure>



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.01.05 AM.png" alt=""><figcaption><p>Summary screen (Microplan assumptions)</p></figcaption></figure>



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.03.13 AM.png" alt=""><figcaption><p>Summary screen (Formula configuration)</p></figcaption></figure>



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.04.02 AM.png" alt=""><figcaption><p>Summary screen (Data validation)</p></figcaption></figure>



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.05.14 AM.png" alt=""><figcaption><p>Summary screen (User access management)</p></figcaption></figure>



* The user will be allowed to edit each section of the summary screen as required.
* The user will be allowed to download the uploaded file wherever there is file uploaded.
* Once clicked on the ‘Edit’ button, the user will be redirected to the section of the microplan setup that needs to be edited.
* Upon finalisation, the user will click on the ‘Complete setup’ button to complete the microplan setup for the supervisors to use further.

11. **Sending email notifications to Microplan users -**

Actor: System administrator/Program manager

Administrative boundary: National/Country

Once the microplan setup is completed, the users whose roles are configured by the system administrator will get an email notification mentioning their user login credentials and URL to the microplan platform or the data collection app. The email will be sent to the users who have valid email IDs registered during the role mapping. The email will also be sent to a common email address that is accessible by the supervisors.

Note: This should be configurable. If the implementation partner wants to enable email notification, then we should enable this.

* Email for the microplan platform users



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.08.26 AM.png" alt=""><figcaption><p>Email notification to microplanning users (Except ‘Data collector’ role)</p></figcaption></figure>

Content of the email of microplanning users:

From: Email of the implementation partner

To: Registered microplan user’s email ID and the common email ID of the implementation partner

Subject: Login credentials for microplanning platform

Body:

Hi {User’s name},

Below are the login credentials to access the microplanning platform -

URL: {website URL}

Username: {Username}

Password: {Password}

Thank you,

{Implementation partner}

Validation: If a new user is created post-microplan setup, the email will be sent to the new user only.

* Email for the data collectors



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.11.53 AM.png" alt=""><figcaption><p>Email notification to ‘Data collector’ users</p></figcaption></figure>

Content of the email of data collector users:

From: Email of the implementation partner

To: Registered data collector email ID and the common email ID of the implementation partner

Subject: Login credentials for data collection app

Body:

Hi {User’s name},

Below are the login credentials to access the data collection app -

App link: {App download link}

Username: {Username}

Password: {Password}

Thank you,

{Implementation partner}

12. **Landing page for system administrators -**

Actor: System administrator/Program manager

Administrative boundary: National/Country



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 10.16.58 AM.png" alt=""><figcaption><p>Landing page for the system administrator</p></figcaption></figure>

\
This is the landing page for the system administrator where the user can perform 3 actions:

* Setup Microplan: The system administrator will be able to set up the microplan from scratch for a campaign
* Open microplans: The system administrator will be able to see the list of campaign microplans in this page and perform certain actions on each microplan, if required
* User management: The system administrator will be able to manage microplanning users using the user management module
* Logout: The system administrator will be able to log out from the dashboard if he is not required to perform any action

‘Open saved microplans’ module:

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 10.18.42 AM.png" alt=""><figcaption><p>Screen for ‘Open saved microplan’</p></figcaption></figure>

\
This is the screen for the system administrator to check out the list of microplans and perform certain actions if required

Content of the screen:

* Search microplan: The user can search microplan using the microplan name. The search can be a partial string match to show the list of microplans that have partially matching string that is typed
* Tab filter based on microplan status: The user will be able to filter out and see the list of microplans concerning the microplan status. The microplan status are -

&#x20;       \- All - This is default tab that will be chosen where the user can see the list of all microplans irrespective of their status

&#x20;       \- Drafted setup - This is the status of the microplan when the system admin has partially configured the microplan and hasn’t completed the setup yet

&#x20;       \- Completed setup - This is the status of the microplan when the system admin has created the microplan setup and the microplanning users haven’t yet opened the microplan to perform the activities (approve population data, facility catchment mapping, edit/approve microplan estimation, etc.) defined as per the role. This status will be fetched from the Microplan dashboard of the supervisors.

&#x20;       \- Validation in progress - This is the status of the microplan when the user has started working on the microplan. This status will be fetched from the Microplan dashboard of the microplanning users.

&#x20;      \- Microplan finalised - This is the status of the microplan when the user has performed all the activities on the microplan and finalised the microplan estimation. This status will be fetched from the Microplan dashboard of the microplanning users.

* Microplan name: This shows the name of the microplan that the user has set while setting up the microplan
* Microplan status: This shows the different status of a microplan while the microplan goes through a series of operational changes.
* Campaign disease: This shows the campaign disease for which the microplan is being configured
* Campaign type: This shows the type of campaign for which the microplan is being configured
* Distribution strategy: This shows the distribution strategy to be used for the campaign execution
* Action: The user will be able to perform certain actions on the microplan. The actions are -

&#x20;      \- Edit setup - The user will be able to edit any or all of the segments of the microplan (Except campaign details segment) when the status of the microplan is ‘Drafted setup’. Once the status of the microplan changes to ‘Validation in progress’ or ‘Completed setup’, then the system administrator will be able to edit only the ‘User access management’ segment for edit, add or remove microplanning users.

&#x20;     \- View summary - The user will be able to view a summary of the microplan that is setup successfully. The status of the microplan should be ‘Completed setup’, ‘Validation in progress’ and ‘Finalised microplan’. If microplan status is ‘Drafted setup’, the ‘View summary’ option should be hidden for the microplan from action dropdown.

&#x20;     \- Duplicate setup - The user will be able to copy the setup configuration of the microplan and create a new microplan with a new name and copied microplan data. On click of ‘Copy’, the user will be re-directed to the first screen of the microplan setup with details already filled. The status of the microplan should be ‘Completed setup’, ‘Validation in progress’ and ‘Finalized microplan’. If microplan status is ‘Drafted setup’, the ‘Duplicate setup’ option should be hidden for the microplan from action dropdown.

‘User management’ module:

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 10.26.07 AM.png" alt=""><figcaption><p>Screen for ‘User management’</p></figcaption></figure>

This is the screen for managing the users for the microplanning platform by the system administrator.

Content of the screen -

1. Name search - The system administrator should be able to search for the registered user using his/her name.
2. Contact number search - The system administrator should be able to search for the registered user using his/her mobile number.
3. Role filters - The system administrator should be able to filter the users registered in the microplanning platform using the role filters.
4. User details - This will have the required details of the registered users such as:

* Name
* Email
* Contact number
* Role

5. Edit user details - Each user row should be clickable and on click of that, health HRMS edit user screen will open up. The user can edit below fields -

* Name of the user
* Email ID of the user
* Add/remove user’s role
* Activate/Deactivate the user

6. Bulk upload users - This is the capability that the system admin will have to add new users to the microplanning platform.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 10.28.07 AM.png" alt=""><figcaption><p>Screen for bulk uploading users</p></figcaption></figure>

The template for bulk upload users is [here](https://docs.google.com/spreadsheets/d/1oIPSn-LJV7C3jF6hLv16dGRH5kLNdKfWbJbz0iq1sNg/edit?usp=sharing)

Here, the system admin can upload the user details by filling up the template attached above. All uploaded users will be part of the microplanning platform. The uploaded users will be able to access the microplans that they will be assigned to using the access control configuration.

The content of the template are -

* Read me - This sheet will have the details of how to fill the user template excel and upload it for user registration.
* User roles - This sheet will have the list of roles available for user registration and the description of each role.
* Role mapping for each sheet - There will be a sheet defined in the template for each role available. Inside each of the role sheet, the system admin can fill user details with -

&#x20;      \- Name - Name of the user who will be using the microplanning platform.

&#x20;        Validation: This is a mandatory field in the template.

&#x20;        \- Contact number - Contact number of the person who will be using the microplanning platform.

&#x20;        Validation: This is a mandatory field in the template.

&#x20;       \- Email ID - Email ID of the person who will be using the microplanning platform.

Validation of the template uploaded -

* The name is the mandatory column to be filled by the system admin in the upload template. If the name is missing for the microplanning users while uploading the template, then show error ‘The ‘name’ is a mandatory field in the file, please update and re-upload’.
* The contact number is the mandatory column to be filled by the system admin in the upload template. If the contact number is missing for the microplanning users while uploading the template, then show error ‘The ‘contact number’ is a mandatory field in the file, please update and re-upload’.
* There should be a validation on contact number w.r.t the countries. If the contact number isn’t matching with the country’s standard structure, then show the error message ‘The ‘contact number’ entered is invalid, please update and re-upload’.
* There should be proper regex validation on the emila ID entered. The system should only accept the email ID that matches with the email format such as ‘[abc@abc.abc](mailto:abc@abc.abc)’. If the entered email ID doesn’t match the proper email structure, then show error message ‘The ‘email ID’ entered is invalid, please update and re-upload’.
* There can’t be duplicate users uploaded in the system. If a contact number of a microplanning user is already registered, then show an error message ‘An user with duplicate contact details already exists in the system’.
* While uploading the template, if a user with the same contact number exists in a different role sheet with different name or email ID, show an error message ‘User details for the same contact number isn’t matching. Please check the user’s name or email ID.’
* A user with ‘Microplan approver’ role can’t be assigned to ‘National microplan approver’ role. If this is the case, show an error message ‘An user with Microplan approver role can’t be assigned to National microplan approver role.’
* A user with the ‘Facility catchment assigner’ role can’t be assigned to the ‘National facility catchment assigner’ role. If this is the case, show an error message ‘An user with Facility catchment assigner role can’t be assigned to National facility catchment assigner’.
* A user with the ‘Population data approver’ role can’t be assigned to ‘National population data approver’ role. If this is the case, show an error message ‘An user with Population data approver role can’t be assigned to National population data approver’.

Note: Use the same format of showing errors in the user upload module as the ‘Data management - Population upload’ module.

When the user file is successfully uploaded, below is the UI that shows the file uploaded -

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 10.33.43 AM.png" alt=""><figcaption><p>ScreeScreen showing successful submission of the user data</p></figcaption></figure>

* The user can download the file that is already uploaded
* The user can re-upload the uploaded file if required
* The user can view the content of the uploaded file by clicking on the file name, that is uploaded

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 10.34.33 AM.png" alt=""><figcaption><p>Screen showing successful submission of the user data</p></figcaption></figure>

7. Download user data -&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 10.35.47 AM.png" alt=""><figcaption></figcaption></figure>

This is the capability that will be used by the system administrator to download the user credentials of the registered users.

Content of the screen:

* File name and attachment - This will have the name of the file with a hyperlink to view & download the file.

&#x20;      \- The downloaded file will have all the details of the file that was uploaded, alongwith the user login credentials for each of the users in the file.

&#x20;      \- The downloaded file will have the login credentials that were generated by the system itself for the first time when the file was uploaded and submitted successfully.

* File uploaded by - This will show the name of the system administrator who had uploaded and submitted the file.
* File uploaded time - This will show the timestamp of the file uploaded by the system administrator.&#x20;

Validation: The timestamp needs to be in the international format of “DD MMM YYYY, HH:MM AM/PM”.

**13. Showing ‘Last updated by’ information  -**

There is a possibility that multiple system administrators are working on the same microplan, to keep the traceability of who made the last changes, it’s important to show the ‘Last updated by “user’s name” at DD:MM:YYYY HH:MM’ in the dashboard for easy identification and traceability.&#x20;

14. **Editing of microplan setup -**

Actor: System administrator/Program manager

Administrative boundary: National/Country

This will let the user edit the microplan setup as required.&#x20;

The user will be able to edit any or all of the segments of the microplan (Except campaign details and campaign name segment) when the status of the microplan is ‘Drafted setup’.

Once the status of the microplan changes to ‘Completed setup’, ‘Validation in progress’, then the system administrator will be able to edit only the user access control/role management segment for assign/deassign a user to the microplan.

What are the changes that can be made in the microplan setup and what impact will it have on other modules?

1. The campaign details segment can’t be changed once the user goes to the next screen. There should be a warning pop-up to be shown to the user once the user clicks on the ‘Save & Next’ button.

Warning message: The campaign details can not be changed once saved, please confirm?

Action: The user can either ‘Cancel’ or ‘Confirm’

2. The microplan name can’t be changed once the user goes to the next screen. There should be a warning pop-up to be shown to the user once the user clicks on the ‘Save & Next’ button.

Warning message: The campaign name can not be changed once saved, please confirm?

Action: The user can either ‘Cancel’ or ‘Confirm’

3. The user can come back and make changes or update the boundary data. There should be a one-time pop-up/user consent to be shown to the user once the user tries to select a new boundary or unselect an already selected boundary.

Warning message: The uploaded population and facility data will be affected if you make changes to the boundary.

Action: The user can either click on ‘No, I don’t want to change’ or ‘Yes, I want to change’.

4. The user can come back and make changes or update the data management content. No warning messages will be displayed.
5. The user can come back and make changes or update the microplan assumption questionnaire. There should be a one-time pop-up/user consent to be shown to the user once the user tries to change any of the question’s dropdown or radio buttons.

Warning message: The campaign assumptions and formula configurations will be affected if you make changes to the questions.

Action: The user can either click on ‘No, I don’t want to change’ or ‘Yes, I want to change’.&#x20;

6. The user can come back and make changes or update the microplan assumptions values, if already saved. No warning messages will be displayed.
7. The user can come back and make changes or update the microplan formula configurations. No warning messages will be displayed.
8. The user can come back and make changes or update the user management module such as add/remove users to the microplan. No warning messages will be displayed.

**Data collector’s flow:**

1. **Data collector app -**

Actor: Data collector

Administrative boundary: Village/Lowest boundary hierarchy

This app will be used by the users with the ‘Data collector’ role to collect the village population data, along with other geographical information. The user’s goal is to make sure that the correct population and geographical data have been collected for the villages to make an informed microplan estimation.

Note: The app functionalities should be offline first

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.45.45 AM.png" alt=""><figcaption><p>Login page for the data collector</p></figcaption></figure>

Content of the screen -

1. User ID: The data collector will have to enter the username that he has received for logging in and collecting the village data.
2. Password: The data collector will have to enter the password that he has received for logging in and collecting the village data. The password will be hidden while typing in.
3. View password: The user can view the password that he has entered.
4. Login: This is the action button using which the user will log in and land on the homepage.
5. Forgot password?: If the user forgets his password, the user can click on the ‘Forgot password’ button and the app should give the message “Please connect with your supervisor or administrator to retrieve the password”
6. Choose language: The user will be able to choose the language for the app content.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.46.35 AM.png" alt=""><figcaption><p>Landing page for the data collector</p></figcaption></figure>

Content of the screen -

1. Population: Upon logging in, the user will land on the homepage where the ‘Population’ functionality will let the user collect village population data for the respective villages
2. Data sync: If the data is submitted in the absence of internet connection, the data will not be synced with the server. In such cases, the user can see how many records are being unsynced and needs proper internet connection to sync with the server.

Note: Auto data sync needs to be enabled. So, whenever there is an internet connection, the app should auto sync the unsynced data.

3. Logout: The user can logout from the application by navigating to the hamburger menu and clicking on the logout button. The user will be redirected to the login page accordingly.
4. Help: The user can understand the modules present in the screen by clicking on ‘help’ button. Help information for the ‘Population’ module - ‘The user can collect population and related information for every assigned boundaries’

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.48.14 AM.png" alt=""><figcaption><p>Village selection screen for data collection</p></figcaption></figure>

Content of the screen -

1. Search enabled dropdown: The user will be asked to select the village for which the population data needs to be collected. This will be a search enabled dropdown where the user can search for the specific village assigned to him. All the villages should be listed in the dropdown in alphabetical order.
2. Submitted village data: The user will be able to see the villages whose data has already been submitted. The ‘tick’ mark shows that the village data for that specific village has been collected already. The user can only view the data for those villages where the data has been collected and submitted.
3. Back: The user will be able to go back to the homepage using the ‘Back’ button.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.49.01 AM.png" alt=""><figcaption><p>Population collection form for ‘Bednet’ campaign</p></figcaption></figure>

<br>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.49.42 AM.png" alt=""><figcaption><p>Capturing village accessibility</p></figcaption></figure>



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.51.54 AM.png" alt=""><figcaption><p>Capturing village security - P1</p></figcaption></figure>

<br>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.52.32 AM.png" alt=""><figcaption><p>Capturing village security - P2</p></figcaption></figure>



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 11.53.08 AM.png" alt=""><figcaption><p>Data submission screen</p></figcaption></figure>

\
Content of the screen for bednet campaign data collection form -

1. Village name: The user will be able to see which village he/she has chosen on the screen.
2. Uploaded village population: The user will be able to see the uploaded village population, which is the total village population data that was uploaded by the system admin while setting up the microplan.
3. Uploaded target population: The user will be able to see the uploaded target population of the village, which is the targeted village population data that was uploaded by the system admin while setting up the microplan.
4. Confirm the total population of the village: The user will be asked to confirm the total population of the village. It’s a mandatory input field.

Validation: The input value should be a whole number. If it’s an invalid entry, show the error message ‘Please enter a whole number’.

5. Confirm the target population of the village: The user will be asked to confirm the target population of the village. It’s a mandatory input field.

Validation: The input value should be a whole number. If it’s an invalid entry, show the error message ‘Please enter a whole number’.

6. Accessibility section - Choose village road condition: The user will be asked to choose the village road condition. It’s a dropdown and the user will be given 4 options to choose from -

&#x20;      a. Concrete

&#x20;      b. Gravel

&#x20;      c. Dirt

&#x20;      d. No road

Note: The option can be kept enabled/disabled depending on the program’s requirements.

7. Accessibility section - Choose village terrain:The user will be asked to choose the village terrain structure. It’s a dropdown and the user will be given 4 options to choose from -

&#x20;       a. Mountain

&#x20;       b. Forest

&#x20;       c. Desert

&#x20;       d. Plain

Note: The option can be kept enabled/disabled depending on the program’s requirements.

8. Accessibility section - Choose transportation mode to the village: The user will be asked to choose the transportation access to the village. It’s a checkbox-enabled dropdown and the list will be populated depending on the vehicles configured for the campaign by the system administrator while doing the microplan setup. The data collector can choose multiple transportation options as it’s going to be checkboxes. If the user doesn’t find the option to choose, he will choose ‘Others’.

If the user chooses ‘Others’ as the option, he will be asked to ‘Enter the transportation mode’.

Note: The option can be kept enabled/disabled depending on the program’s requirements.

9. Security section - Is your village prone to civil unrest like violent protests, riots, etc.?: The user will be asked to choose how prone the village is to civil unrest or protest. Below are the options given to the user to choose from -

&#x20;      a. All the time (Atleast once a month)

&#x20;      b. Often (Atleast once a year)

&#x20;      c. Rarely (Once in 2-3 years)

&#x20;      d. Never

Note: The option can be kept enabled/disabled depending on the program’s requirements.

10. Security section - How often do the security forces patrol the village?: The user will be asked how often do the security forces patrol the village. It’s a dropdown option for the user to choose from. Below are the options given to the user to choose from -

&#x20;        a. Everyday

&#x20;       b. Often (Atleast once a week)

&#x20;       c. Rarely (Once in a month)

&#x20;       d. Never

Note: The option can be kept enabled/disabled depending on the program’s requirements.

11. Comment: Before submission of the collected data, the user needs to add a comment. It’s a mandatory input field.

Validation: The maximum length of the comment is 140 characters. If the user tries to submit the data without adding a comment, then show the error message “Please enter comment before submission”.

12. Submit: Once the data form is filled and submitted, the user will be redirected to the village selection page to select a new village for data collection.

Note: If the programme requires deleting existing content or adding new information with multiple dropdown choices or input values in the screen, that should be done by the impel team.

Once the data is filled, the data collector will submit the data, which will be reviewed and taken action by the ‘Population data approver’ role user.<br>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 12.00.11 PM.png" alt=""><figcaption><p>Review submitted data screen</p></figcaption></figure>



* If the user chooses a village, whose data has already been collected and submitted, then he will be able to review the submitted data.
* If the user clicks on ‘Back’, the user will be redirected to the village selection screen to choose a new village for data collection and submission.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 12.07.08 PM.png" alt=""><figcaption><p>Population collection form for ‘SMC’ campaign</p></figcaption></figure>

Content of the screen for SMC campaign data collection form -

1. Village name: The user will be able to see which village he/she has chosen on the screen.
2. Uploaded village population: The user will be able to see the uploaded village population, which is the total village population data that was uploaded by the system admin while setting up the microplan.
3. Uploaded target population (Age 3-11 months): The user will be able to see the uploaded target population between the age 3-11 months of the village, which is the targeted village population data that was uploaded by the system admin while setting up the microplan.
4. Uploaded target population (Age 12-59 months): The user will be able to see the uploaded target population between the ages 12-59 months of the village, which is the targeted village population data that was uploaded by the system admin while setting up the microplan.
5. Confirm the total population of the village: The user will be asked to confirm the total population of the village. It’s a mandatory input field.

Validation: The input value should be a whole number. If it’s an invalid entry, show the error message ‘Please enter a whole number’.

6. Confirm target population of the village (Age 3-11 months): The user will be asked to confirm the target population of the village between the ages 3-11 months. It’s a mandatory input field.

Validation: The input value should be a whole number. If it’s an invalid entry, show the error message ‘Please enter a whole number’.

7. Confirm target population of the village (Age 12-59 months): The user will be asked to confirm the target population of the village between the ages 12-59 months. It’s a mandatory input field.

Validation: The input value should be a whole number. If it’s an invalid entry, show the error message ‘Please enter a whole number’.

8. Accessibility section - Choose village road condition: The user will be asked to choose the village road condition. It’s a dropdown and the user will be given 4 options to choose from -

&#x20;      a. Concrete

&#x20;      b. Gravel

&#x20;      c. Dirt

&#x20;      d. No road

Note: The option can be kept enabled/disabled depending on the program’s requirements.

&#x20;    9\. Accessibility section - Choose village terrain: The user will be asked to choose the village terrain structure. It’s a dropdown and the user will be given 4 options to choose from -

&#x20;       a. Mountain

&#x20;       b. Forest

&#x20;       c. Desert

&#x20;       d. Plain

Note: The option can be kept enabled/disabled depending on the program’s requirements.

10\. Accessibility section - Choose transportation mode to the village: The user will be asked to choose the transportation access to the village. It’s a checkbox-enabled dropdown and the list will be populated depending on the vehicles configured for the campaign by the system administrator. The data collector can choose multiple transportation options as it’s going to be checkboxes. If the user doesn’t find the option to choose, he will choose ‘Others’.

If the user chooses ‘Others’ as the option, he will be asked to ‘Enter the transportation mode’.

Note: The option can be kept enabled/disabled depending on the program’s requirements.

11\. Security section - Is your village prone to civil unrest like violent protests, riots, etc.?: The user will be asked to choose how prone the village is to civil unrest or protest. Below are the options given to the user to choose from -

1. All the time (Atleast once a month)
2. Often (Atleast once a year)
3. Rarely (Once in 2-3 years)
4. Never

Note: The option can be kept enabled/disabled depending on the program’s requirements.

13. Security section - How often do the security forces patrol the village?: The user will be asked how often the security forces patrol the village. It’s a dropdown option for the user to choose from. Below are the options given to the user to choose from -

&#x20;       a. Everyday

&#x20;       b. Often (Atleast once a week)

&#x20;       c. Rarely (Once in a month)

&#x20;       d. Never

Note: The option can be kept enabled/disabled depending on the program’s requirements.

14. Comment: Before submission of the collected data, the user needs to add a comment.

Validation: The maximum length of the comment is 140 characters. If the user tries to submit the data without adding a comment, then show the error message “Please enter comment before submission”.

15. Submit: Once the data form is filled and submitted, the user will be redirected to the village selection page to select a new village for data collection.

Note: If the program requires deleting existing content or adding new information with multiple dropdown choices or input values in the screen, that should be done by the impel team.

Once the data is filled, the data collector will submit the data, which will be reviewed and taken action by the ‘Population data approver’ role user.

**Supervisor’s flow :**

1. **Landing page for the supervisors -**

Actor: Supervisor (Population data approver, Microplan viewer, Microplan approver, and Facility catchment mapper)

Administrative boundary: Country (Highest boundary), Province, Districts, Admin post, Locality (Second lowest boundary)

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 12.16.04 PM.png" alt=""><figcaption><p>Landing page for the supervisor</p></figcaption></figure>

* Once the supervisor logs in using the login credentials received via email, the supervisor will be able to perform only 2 actions here -
* Open microplans: The user will be able to click on ‘My Microplan’ to get the list of all the microplans that he is part of. If a user is a part of 1 or more campaign microplanning processes, he/she will be able to see the list after he clicks on the ‘My Microplan’ link.
* Logout: The supervisor will be able to log out from the dashboard if he is not required to perform any action.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 12.17.08 PM.png" alt=""><figcaption><p>Screen to show the list of microplans assigned to the supervisor</p></figcaption></figure>

Content of the screen:

* Search microplan: The user can search microplan using the microplan name. The search can be a partial string match to show the list of microplans that have a partially matching string that is typed
* Tab filter based on microplan status: The user will be able to filter out and see the list of microplans concerning the microplan status. The status are -

&#x20;      \- All - By default ‘All’ tab will be chosen and the user will be able to see all the microplans that are assigned to him irrespective of the microplan status.

&#x20;     \- Execution to be done - This is the status of the microplan when the user hasn’t yet opened the microplan to perform the activities (approve population data, facility catchment mapping, edit/approve microplan estimation, etc.) defined as per the role.&#x20;

&#x20;      \- Execution in progress - This is the status of the microplan when the user has started working on the microplan by clicking on the ‘Start’ button.

Validation: The user with the ‘Population data approver’ role will be able to click on ‘Start’ as without the population data being approved, the microplan estimation won’t be executed. For other roles, the ‘Start’ button should be disabled.

&#x20;      \- Execution done - This is the status of the microplan when the user has performed all the activities on the microplan and finalized the microplan estimation.

* Microplan name: This shows the name of the microplans that are assigned to the user.
* Microplan status: This shows the different status of a microplan while the microplan goes through a series of operational changes.&#x20;
* Campaign disease: This shows the campaign disease for which the microplan is being configured.
* Campaign type: This shows the type of campaign for which the microplan is being configured.
* Distribution strategy: This shows the distribution strategy to be used for the campaign execution.
* Action: The user will be able to perform certain actions on the microplan. The actions are -

&#x20;     \- Start - When the microplan status is ‘Execution to be done’, that means the work on microplan hasn’t yet started by any of the users. And this is when the ‘Start’ button will be reflected corresponding to the microplan. When the user clicks on the ‘Start’ button, the status will change to ‘Execution in progress’.

&#x20;     \- Edit - When the microplan status is ‘Execution in progress’, that means the working on microplan has started by any of the users. And this is when the ‘Edit’ button will be reflected corresponding to the microplan.

&#x20;    \- Download estimation - When the microplan status is ‘Execution done’, that means the microplan estimation has been finalized by the national level user. And this is when the ‘Download estimation’ button will be reflecting corresponding to the microplan. The user will be able to download the excel file of the microplan estimation.

2. **Multi-role activity view -**

Actor: Supervisor (Population data approver, Microplan viewer, Microplan approver and Facility catchment mapper)

Administrative boundary: Country (Highest boundary), Province, Districts, Admin post, Locality (Second lowest boundary)

This view will give the users the activities they can perform on the platform concerning the role assigned to them. A user can be assigned to multiple roles, and depending on the role assigned the user will be able to see the options on the screen.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-10 at 12.17.08 PM (1).png" alt=""><figcaption><p>Screen showing available activities to the user based on the roles assigned</p></figcaption></figure>

\
Once the user takes an action of ‘Start’ or ‘Edit’ for a microplan, the user will be redirected to this available activity screen where the user will be able to take appropriate actions as per the role defined. The activities that will be listed are -

1. the Approve population data - A user with ‘Population data approver’ role will be able to see the action tab of ‘Approve population data’.
2. Assign facilities to villages - A user with the ‘Facility catchment mapper’ role will be able to see the action tab of ‘Assign facilities to villages’.
3. Geospatial map view - Any microplan user irrespective of role defined will be able to see this action tab.
4. Approve microplan estimations - A user with ‘Microplan approver’ role will be able to see the action tab of ‘Approve microplan estimations’.
5. View microplan estimations - A user with ‘Microplan viewer’ role will be able to see the action tab of ‘View microplan estimations’.

To access the ‘Assign facilities to villages’ tab, it’s important that the country level ‘Population data approver’ finalizes the population data for the campaign boundary. If the population data is not finalized, then the ‘Assign facilities to villages’ tab will be disabled and users will be able to see a message “The population data for the microplan hasn’t been approved yet. Please come back later.” on hovering over the ‘Assign facilities to villages’ tab.

To access the ‘Geospatial map view’, ‘Approve microplan estimations’ and ‘View microplan estimations’ tabs, it’s important that the country level ‘Facility catchment mapper’ finalizes the facility-to-catchment mapping for all the villages within the campaign zone. If the facility-catchment mapping is not finalized, then the ‘Geospatial map view’, ‘Approve microplan estimations’ and ‘View microplan estimations’ tabs will be disabled and users will be able to see a message “The facility to catchment area assignment for the microplan hasn’t been finalised yet. Please come back later.” on hovering over the ‘Assign facilities to villages’ tab.

3. &#x20;**Population data approver flow -**

Actor: Supervisor (Population data approver)

Administrative boundary: Country (Highest boundary), Province, Districts, Admin post, Locality (Second last boundary)

This is the flow for approving the village population data that is either uploaded by the system admin or collected by the data collector. Approving population data is crucial as the microplan estimation will be happening concerning the population of the village that is approved.

Population data approvers can act on different administrative hierarchies and depending on the hierarchy and boundaries assigned, the villages will be assigned to the user for approving the population data. For example, the Population data approver can belong to a country, province, district, administrative post, locality and with respect to the boundaries assigned, he will be able to see the village information.

The final approver for the population data of the country will always be the national level ‘Population data approver’ where all the villages and its population will be added up to show the country level population.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 9.49.36 AM.png" alt=""><figcaption><p>Landing page of the ‘Population data approver’ role</p></figcaption></figure>

Note: The design is showing ‘District’ level population approver screen but a population data approver can belong to any administrative hierarchy of the country.

This is the landing page for the ‘Population data approver’ user where he/she will see the population and related information of the villages that are part of the administrative boundaries assigned to him. The user can check out the detailed information and make changes in the population and related data and send the changes for approval. If no changes are required in the population data, the user can directly validate the village population.

Content of the landing page -

1. Dynamic boundary filters on top concerning parent and child administrative hierarchy - This is a dynamic filter that will be given to the user for filtering out specific boundaries. This will be a search-enabled dropdown for every filter content. The filters will be added or removed depending on the parent hierarchy assigned to the user. For example, if the user belongs to district hierarchy (Parent), then all child hierarchies and their boundaries will be part of the filter. The user can clear the selected filter by clicking on the ‘Clear Filter’ button.
2. Dynamic dashboard metrics - There will be dynamic metrics that will be shown to the user depending on the filters chosen. The important metrics that need to be shown on the dashboard are -

&#x20;       a. Uploaded target population - This metric will show the aggregated target population that is uploaded and it will change as per the filters chosen. This is for a bednet campaign.&#x20;

&#x20;      b. Confirmed target population - This metric will show the aggregated confirmed target population and it will change as per the filters chosen. This is for a bednet campaign. &#x20;

&#x20;      c. Uploaded target population (Age 3 - 11 months) - This metric will show the aggregated target population (Age 3 - 11 months) that is uploaded and it will change as per the filters chosen. This is for a SMC campaign.

&#x20;     d. Confirmed target population (Age 3 - 11 months) - This metric will show the aggregated confirmed target population (Age 3 - 11 months) and it will change as per the filters chosen. This is for a SMC campaign.

&#x20;    e. Uploaded target population (Age 12 - 59 months) - This metric will show the aggregated target population (Age 12 - 59 months) that is uploaded and it will change as per the filters chosen. This is for a SMC campaign.

&#x20;    f. Confirmed target population (Age 12 - 59 months) - This metric will show the aggregated confirmed target population (Age 12 - 59 months) and it will change as per the filters chosen. This is for a SMC campaign.

&#x20;   g. Uploaded total population - This metric will show the aggregated total population that is uploaded and it will change as per the filters chosen.

&#x20;   h. Confirmed total population - This metric will show the aggregated confirmed total population and it will change as per the filters chosen.&#x20;

3. Filters on the action items on the user - This filter will help the user to filter out the villages that need some action. Below are the filters that will be shown to the user:

&#x20;       a. Villages with pending validation - This filter will show the list of villages that are pending to be validated by the user. The user will be able to see the list of villages whose actions are pending on the user as well as on the users that belong to the child boundaries of the parent district level data approver. This filter will be further segregated as -

i. Pending on me - This will show the list of the villages that needs to be validated by the assigned user of the ‘district’. This will also show a metric - the number of villages that are pending to be validated by the user out of the total number of villages belonging to the user’s assigned boundaries, for example, 5/30 villages to be validated. This should be by default chosen when the user lands on the page.

ii. Pending on subordinates - This will show the list of the villages that need to be validated by the users that belong to the child boundaries of the parent ‘district’. This will also show a metric - the number of villages that are pending to be validated by the subordinates out of the total number of villages belonging to the user’s assigned boundaries, for example, 15/30 villages to be validated.

Note: A data approver belonging to a ‘district’ can validate the village population data of the villages that belong to the child boundaries of the ‘district’, even though those villages may have their own data approver assigned.

&#x20;       b. Validated villages - This filter will show the list of villages that are part of the user’s assigned boundary and those have been validated either by the user himself or his subordinates at the lower administrative hierarchy level. This will also show a metric - the number of villages that are validated out of the total number of villages belonging to the user’s assigned boundaries, for example, 25/30 villages are validated.

&#x20;    c. Villages with pending approval - This filter will show the list of villages whose population data (total population or target population) have been changed by the user’s subordinates at the lower administrative hierarchies. This will also show a metric - the number of villages that are pending for approval by the user, for example, 5 villages data to be approved. The assigned user who can see the pending approval villages here can perform 2 activities -

i. Check and approve the recommended village population data

ii. Send back the village data for correction to the user who sent the village data for approval

4. Data content of the landing page -&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 9.50.48 AM.png" alt=""><figcaption></figcaption></figure>

Here the user will be able to see the basic information related to the villages that are part of his administrative hierarchy. The data that will be available are -

a. Village - The list of the villages that are part of the user’s administrative hierarchy. There will be a checkbox beside every village listed.

b. Uploaded total population - This will show the total population of the village whose data has been uploaded by the central team or microplan system administrator.

c. Confirmed total population - This will show the total population of the village whose data has been uploaded by the central team or microplan system administrator. This can later be edited.&#x20;

d. Uploaded target population - This will show the target population of the village whose data has been uploaded by the central team or microplan system administrator. This is specifically for bednet campaigns.

e. Confirmed target population - This will show the target population of the village whose data has been uploaded by the central team or microplan system administrator. This is specifically for bednet campaigns. This can later be edited.

f. Uploaded target population (Age 3-11 months) - This will show the target population between age 3-11 months of the village whose data has been uploaded by the central team or microplan system administrator. This is specifically for SMC campaigns.

g. Confirmed target population (Age 3-11 months) - This will show the target population between age 3-11 months of the village whose data has been uploaded by the central team or microplan system administrator. This is specifically for SMC campaigns. This can later be edited.

h. Uploaded target population (Age 12-59 months) - This will show the target population between age 12-59 months of the village whose data has been uploaded by the central team or microplan system administrator. This is specifically for SMC campaigns.

i. Confirmed target population (Age 12-59 months) - This will show the target population between age 12-59 months of the village whose data has been uploaded by the central team or microplan system administrator. This is specifically for SMC campaigns. This can later be edited.

j. Comment logs - This will show the status flow of a village and comments made while validating or making corrections to the village data. This comment logs will capture the comment made by the users in a timeline manner. For any action that the user takes such as ‘Validate’, ‘Send for data correction’, ‘Send for approval’ and ‘Approve’ the user has to enter a comment.

k. Edit confirmed population - This is an action that the user can take to update the population data of the village, if the user feels that the uploaded data is incorrect or has discrepancies. Upon editing, the village data will be submitted for approval by the user belonging to the next higher hierarchy. This will update the ‘Confirmed total population’ and ‘Confirmed target population’ of the village for the data approver.

Note: Edit population data option will not be provided to the users if they filter the villages by ‘Villages with pending approval’ and ‘Validated villages’ filter.

5. Action on the villages - There will be certain actions that the user can take on the villages depending on the filter chosen. The actions are -

a. Validate data - This action will be available for the filters chosen ‘Villages with pending validation’. More details will be provided below.

b. Send for correction - This action will be available for the filters chosen ‘Villages with pending approval’ and ‘Validated villages’. More details will be provided below.

c. Approve data - This action will be available for the filters chosen ‘Villages with pending approval’. More details will be provided below.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 9.51.43 AM.png" alt=""><figcaption><p>Edit village population pop-up screen</p></figcaption></figure>

This functionality will give access to the assigned user to edit the village population data and submit it for approval to the supervisors belonging to the next higher hierarchy.

Note: The edit population data option will not be provided to the users if they filter the villages by ‘Villages with pending approval’ and ‘Validated villages’ filter.

Content of the screen -

1. Village name - This shows the name of the village that the user wants to edit the population data for.
2. Uploaded total village population - This shows the total village population uploaded by the system admin for the village.
3. Uploaded target village population - This shows the target village population uploaded by the system admin for the village. This is specifically for bednet campaigns.
4. Uploaded target village population (Age 3 - 11 months) - This shows the target village population (Age 3 - 11 months) uploaded by the system admin for the village. This is specifically for SMC campaigns.
5. Uploaded target village population (Age 12 - 59 months) - This shows the target village population (Age 12 - 59 months) uploaded by the system admin for the village. This is specifically for SMC campaigns.
6. Confirm total population of the village - This will have auto filled total population data captured by the data collector or population upload file, in case the village doesn’t have any data collector. The data approver can validate and edit the total population and it will be reflected in the ‘Collected total village population’ data column of the dashboard.

Validation: The field should accept only numeric values and whole numbers. Error message when invalid entry happens “Population data must be a whole number”.

7. Confirm target population of the village - This will have auto filled target population data captured in the population upload file. This is specifically for bednet campaigns.

Validation: The field should accept only numeric values and whole numbers. Error message when invalid entry happens “Population data must be a whole number”.

8. Confirm target population of the village (Age 3 - 11 months) - This will have auto filled target population (Age 3 - 11 months) data captured in population upload file. This is specifically for SMC campaigns.

Validation: The field should accept only numeric values and whole numbers. Error message when invalid entry happens “Population data must be a whole number”.

9. Confirm target population of the village (Age 12 - 59 months) - This will have auto-filled target population (Age 12 - 59 months) data captured in the population upload file. This is specifically for SMC campaigns.

Validation: The field should accept only numeric values and whole numbers. Error message when invalid entry happens “Population data must be a whole number”.

10. &#x20;Actions buttons - The user will be able to perform either of the below actions here:

a. Send for approval - Once the user updates the population data, the user can send the changed data of the village for approval to the next higher administrative hierarchy data approver. To send corrected data for approval, the user must enter a comment sharing the reason for the change.

Validation: The max length of a comment is 140 characters.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 9.53.06 AM.png" alt=""><figcaption><p>Comment box pop-up for ‘Send for approval’ action</p></figcaption></figure>

b. Cancel - The user can cancel the update and return to the landing page.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 9.54.15 AM.png" alt=""><figcaption><p>Screen for comment logs pop-up</p></figcaption></figure>

The user can see the comment logs by clicking on the comment logs link. The user will be able to see the detailed action taken on a village along with the timestamp and comment details. This will help the supervisors to understand what actions have been taken in a village and who took the action. This will help in keeping traceability of the changes happening to a village.

The content of the comment logs are -

1. Status of the action - The user will be able to see the status of the actions taken by the other users. For every action, the status will be captured w.r.t the village and updated in the comment logs. There will be 4 status on a high level:

a. Data submitted - Once the village population data has been uploaded by the central/system admin, the status will be changed to ‘Data submitted’.

b. Sent for approval - Once the village population data has been changed by a user and forwarded for approval, the status will be changed to ‘Sent for approval’.

c. Approved - Once the user approves the recommended changes in the village population, it moves to ‘Approved’ status.

d. Validated - Once the village population data has been validated by the user or by the highest jurisdiction level data approver, the status will be changed to ‘Validated’ and the village will be moved to ‘Validated villages’ bucket.

e. Sent for correction - Once the village population data has been checked by the supervisor and supervisors decide to send the village data for correction, the status will be changed to ‘Sent for correction’.

2. User’s name and role - Whenever a user takes an action on the village and puts a comment, for every action, the user’s name and role will be captured and shown in the comment logs.
3. Timestamp - Whenever a user takes an action on the village and puts a comment, for every action, the timestamp of the action will be captured. It should be in the international timestamp format “YYYY-MM-DD HH:MM”.
4. Comment - Whenever a user takes an action on the village and puts a comment, it will be captured alongside the other details.

Workflow image for data validation and data approval -

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.33.56 AM.png" alt=""><figcaption></figcaption></figure>

1. Workflow for pending data validation - Upon landing, the user will be able to see the list of villages that are part of the administrative hierarchy assigned to the user and his subordinates. There will be a filter called ‘Villages with pending validation’, in this filter, the user will be able to see all the villages that need the user or his subordinates to take action. On this page, the user can take 2 important actions upon checking the village population data -

&#x20;       a. Validate the village data -&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 9.55.26 AM.png" alt=""><figcaption><p>Screen for validating the village data</p></figcaption></figure>

If the user chooses one or more villages and validates their data using the ‘Validate’ button, then the villages will be moved from the bucket of ‘Villages with pending validation’ to ‘Validated villages’. These validated villages will be seen by the user, his subordinates at the child administrative boundaries, and his/her superiors at the parent administrative boundaries. For example, if a district supervisor validates the village data, then it will be seen by the administrative post and locality-level data approvers that are part of the district, also, the validated villages will be seen by the province and country-level data approvers to which the district is linked. For validating a village, the user has to add a reason for validation as a comment. Below is the UI for the comment section to add the validation reason:

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.36.35 AM.png" alt=""><figcaption></figcaption></figure>

&#x20;     b. Send back for correction -&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.37.34 AM.png" alt=""><figcaption><p>Screen for sending back data for correction</p></figcaption></figure>

Once the validated villages start residing in the ‘Validated villages’ bucket, those villages will be shown to every user belonging to the parent and child administrative boundaries. The user at the higher administrative boundaries will have the access to send back the data for correction, in case the higher level supervisors aren’t satisfied with the validated village data. Once the data has been sent back for correction, the village will move from the ‘Validated villages’ bucket to the ‘Villages with pending validation’ bucket of the user who has validated it earlier. For sending back for correction, the user has to add a reason for sending back the data for correction as a comment. Below is the UI for comment section to add the validation reason:

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.38.40 AM.png" alt=""><figcaption></figcaption></figure>

Note: Send back for correction button will only be available to the users who validated the village data and to the users that reside in the higher administrative boundaries.

2. Workflow for pending data approval - Upon landing, the user will be able to see the list of villages that are part of the administrative hierarchy assigned to the user and his subordinates. There will be a filter called ‘Villages with pending validation’, in this filter, the user will be able to see all the villages that need the user or his subordinates to take action. On this page, the user can take 2 important actions upon checking the village population data -

&#x20;       a. Editing the village data - If the user feels that the uploaded data for a certain village is incorrect or out-dated, the user can recommend data changes for the village by clicking on the ‘Edit population data’ button.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.39.55 AM.png" alt=""><figcaption><p>Edit village population pop-up screen</p></figcaption></figure>

Once the user edits the village population data, it will be sent to his next higher level supervisor for approval. The village will be moved from the ‘Villages with pending validation’ bucket to ‘Villages with pending approval’ bucket of the supervisor belonging to the next higher administrative hierarchy. For sending recommended village population data for approval, the user has to add a reason for sending recommended village population data for approval as a comment. Below is the UI for comment section to add the validation reason:

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.41.24 AM.png" alt=""><figcaption></figcaption></figure>

&#x20;     b. Approving the recommended changes in the village data -&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.42.14 AM.png" alt=""><figcaption><p>Screen for approval flow of villages</p></figcaption></figure>



The supervisors will be able to see the list of villages with pending approval in the ‘Villages with pending approval’ bucket. In this bucket, the supervisor can check and compare the village population data that is uploaded and then the recommended population data submitted by the subordinate for approval. Here, upon decision making, the supervisor data approver can take 2 actions:

i. Approve the recommended changes in the village data - If the supervisor data approver feels that the recommended changes in the village population is correct, then the data approver will approve the village population using the ‘Approve’ button (The user can choose multiple villages for approval at once). Upon approving the village population, the village will be moved from the assigned data approver’s ‘Villages with pending approval’ bucket to the next higher administrative hierarchy data approver’s ‘Villages with pending approval’ bucket. This workflow will go on until the national or highest administrative hierarchy level data approver validates the population data of the village. Once the changes reach the highest administrative hierarchy for approval, the village status will be ‘Validated’ and the village will reside in the ‘Validated villages’ bucket once approved by the highest administrative hierarchy. For every approval, the data approver needs to add a reason as a comment and that comment will be seen in the comment logs.

Note: The population data approver will be able to see and take actions on the pending approvals on him as well as the pending approvals on his subordinates.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.44.21 AM.png" alt=""><figcaption></figcaption></figure>

ii. Sending data for correction - If the supervisor data approver at any higher administrative hierarchy feels that the recommended changes in the village population is incorrect, then the data approver will send the village population data for correction using the button ‘Send for correction’. Once the data is sent for correction, the village will be moved from the ‘Villages with pending approval’ bucket of the user to ‘Villages with pending validation’ bucket of the user who submitted the recommended village data changes. For every action of sending for correction, the data approver needs to add a reason as a comment and that comment will be seen in the comment logs.&#x20;

Important validation: The village population data can’t be changed if the village resides in the ‘Villages with pending approval’ bucket.

View of detailed village data -

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.46.33 AM.png" alt=""><figcaption><p>Screen showing detailed content of a village</p></figcaption></figure>



This is the redirected page that shows the detailed information of the village selected. When the user clicks on the village on the landing page, he will be redirected to a new page with the detailed information of the village.&#x20;

Content of the detailed pop-up screen -

1. Boundary details - Depending on the boundary assigned, the user will be able see the boundary hierarchy and assigned boundaries, along with the child boundary hierarchy and their boundaries.
2. Uploaded target village population - This will show the system admin’s uploaded target population of the village. This is specifically for bednet campaigns.
3. Uploaded target village population (Age 3 - 11 months) - This will show the system admin’s uploaded target population (Age 3 - 11 months) of the village. This is specifically for SMC campaigns.
4. Uploaded target village population (Age 12 - 59 months) - This will show the system admin’s uploaded target population (Age 12 - 59 months) of the village. This is specifically for SMC campaigns.
5. Approve target population of the village - This will have auto filled target population data captured in the population upload file. In case the target population of the village is updated by the data approver, then the approved target population will be updated with the new updated target population. This is specifically for bednet campaigns.

Validation: The field should accept only numeric values and whole numbers. Error message when invalid entry happens “Population data must be a whole number”.

6. Approve target population of the village (Age 3 - 11 months) - This will have auto filled target population (Age 3 - 11 months) data captured in population upload file. In case the target population of the village is updated by the data approver, then the approved target population will be updated with the new updated target population. This is specifically for SMC campaigns.

Validation: The field should accept only numeric values and whole numbers. Error message when invalid entry happens “Population data must be a whole number”.

7. Approve target population of the village (Age 12 - 59 months) - This will have auto filled target population (Age 12 - 59 months) data captured in the population upload file. In case the target population of the village is updated by the data approver, then the approved target population will be updated with the new updated target population. This is specifically for SMC campaigns.

Validation: The field should accept only numeric values and whole numbers. Error message when invalid entry happens “Population data must be a whole number”.

8. Uploaded total village population - This will show the uploaded total population of the village by the system admin.
9. Approve total population of the village - This will have auto filled total population data captured in the population upload file. In case the total population of the village is updated by the data approver, then the approved total population will be updated with the new updated total population.

Validation: The field should accept only numeric values and whole numbers. Error message when invalid entry happens “Population data must be a whole number”.

10. Assigned data approver - This will show the person who is assigned to approve the population data of the village.
11. Village accessibility level - This shows the accessibility level to a village. The village accessibility level can be edited by ‘Population data approver’, if required. This is an optional field.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.48.19 AM.png" alt=""><figcaption><p>Village accessibility pop-up</p></figcaption></figure>

There are 3 data parameters to access the accessibility level to the village -

a. Village road condition - The user will be asked to choose the road condition to the village using the data approver dashboard. There will be 4 options given to the user to choose from -

1. Concrete
2. Gravel
3. Dirt
4. No road

b. Village terrain - The user will be asked to choose the village terrain using the data approver dashboard. There will be 4 options given to the user to choose from -

1. Mountain
2. Forest
3. Plain
4. Desert

c. Transportation mode - The user will be asked to choose the transport mode available to reach the village using the data approver dashboard. The transportation mode will be fetched from the vehicle registration page. If the user doesn’t get the option to choose the transport mode, he can choose ‘Others’ as an option to add the transport mode to the vehicle. The new transport mode will be just temporarily created and it will not affect the vehicle registration module.

12. Village security level - The village security level will be edited by the ‘Population data approver’ user if required. This is an optional field.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.51.10 AM.png" alt=""><figcaption><p>Village security pop-up</p></figcaption></figure>

There are 2 data parameters to access the security level of the village -

a. Is your village prone to civil unrest like violent protests, riots, etc.? - The user will be asked this question to answer using the data approver dashboard. There will be 4 options to choose from -

1. All the time (Atleast once a month)
2. Often (Atleast once a year)
3. Rarely (Once in 2-3 years)
4. Never

b. How often do the security forces patrol the village?

1. Everyday
2. Often (Atleast once a week)
3. Rarely (Once in a month)
4. Never



13. Comment logs - The data approver can check the comment logs in case a village is validated or sent for correction or sent for approval.&#x20;

Use-case to cover: What if the country-level data approver changes/edits the village population data?

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.53.31 AM.png" alt=""><figcaption><p>Screen showing the population update process by country data approver</p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.58.32 AM.png" alt=""><figcaption><p>Screen showing the comment box that the country data approver will get post-data changes</p></figcaption></figure>

The country-level data approver can make population data changes for any village under his jurisdiction. Now, since the country-level data approver doesn’t have any superior role assigned above him, the changes will not go through any approval process. The country-level data approver can simply make the changes, add a reason for the changes, and save the changes. The status of the village will remain unchanged but all the changes should be logged in the comment and change logs.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 10.59.46 AM.png" alt=""><figcaption><p>Screen showing the national population data approver to finalise data</p></figcaption></figure>

Note - The final approver of the village population will be the national or highest administrative hierarchy data approver. The national level data approver will have a button called ‘Finalize Population Data’, and the button will only be enabled when the ‘Villages with pending validation’ is 0, ‘Villages with pending approval’ is 0, and ‘Validated villages’ is x/x, that is, if there are 500 villages in the campaign zone, then 500 villages should be in the validated status. Once the population data is finalised, there will be no action allowed on the dashboard. The user can just work with the filters to view the data but can’t make any changes. Once finalized, the estimation of bednets required per village and the total SPAQ required per village will be calculated.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.01.49 AM.png" alt=""><figcaption><p>Screen showing finalised population message to the user</p></figcaption></figure>

\
The user will be able to see the message screen once the population data has been finalized by the national level Population data approver.

14. **Facility catchment mapper flow -**

Actor: Supervisor (Facility catchment mapper)

Administrative boundary: Country (Highest boundary), Province, Districts, Admin post, Locality (Second last boundary)

This is the flow for mapping the campaign facilities/POS to their catchment boundaries (villages). Mapping the facilities/POS to their catchment boundaries (villages) is crucial as the microplan estimation for the boundary (villages) will be happening w.r.t the facility/POS mapped and its type.

Facility catchment mappers can act on different administrative hierarchies and depending on the hierarchy and boundaries assigned, the facility catchment mapper will be able to see their assigned villages and facilities/POS for mapping. For example, the mapper can belong to a country, province, district, administrative post, or locality, and concerning the boundaries assigned, he/she will be able to see the respective villages and facilities/POS within the boundaries assigned.



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.05.51 AM.png" alt=""><figcaption><p>Landing page ‘Facility catchment mapper’ role </p></figcaption></figure>

This screen is the landing page for the mapper. In this screen, the mapper will be able to view all the facilities/POS and their details that are part of his administrative boundaries.&#x20;

Validation: For the mapper to work on mapping facility/POS to their catchment areas, the population data for the campaign must be approved by the national level Population data approver.&#x20;

Content of the screen -

1. Card showing villages with mapped facilities/POS - This card will show the count of the villages that belong to the mapper’s administrative boundary. It also shows the total number of villages (belonging to the mapper’s admin boundary) that have a catchment facility mapped.
2. Card showing facilities with mapped villages - This card will show the count of the facilities that belong to the mapper’s administrative boundary. It also shows the total number of facilities (belonging to the mapper’s admin boundary) that have a catchment village mapped.
3. Facility search - This will give the user the ability to search the specific facility that needs to be mapped to the catchment boundaries. The search needs to accept partial string match as well.
4. Filters - This will let the users to filter out the specific facilities that he needs to do the facility-catchment area mapping for. The user can filter out the facilities that he wants to map the catchment villages to. Below are the multi-select dropdown filters that the user will get -

&#x20;       a. Facility type - This will have the data of facility type defined during the instance creation

&#x20;       b. Facility status - This will have the facility status defined, which is either permanent or temporary

&#x20;      c. Is fixed post? - This will be an optional field. If the campaign distribution strategy is either ‘fixed post’ or ‘house-to-house and fixed post’, then this filter will be available for the user to choose

&#x20;      d. Residing village - This will have the list of all the villages that the facilities in the dashboard are part of

5. Facility name - This field shows the name of the facility that belongs to the user’s defined boundary.
6. Facility type - This field contains the type of the facilities that are listed in the dashboard.
7. Facility status - This field contains the status (Permanent/Temporary) of the facilities that are listed in the dashboard.
8. Capacity - This field contains the capacity of the facilities that are listed in the dashboard. The capacity can be either ‘Bales’ for bed nets or ‘Blisters’ for SMC campaigns. This will also show the out of total capacity, how much is consumed - Aggregated bales or blisters required for the villages assigned to the facility.
9. Assigned villages - This field will show the total number of villages that are assigned to the specific facility.
10. Serving population - This field will show the total population that is being served by the facility out of the total capacity of serving population of the facility. The total population that is served by the facility is the sum of the approver target population of the villages assigned. So, in case of a bednet campaign, the total serving population will be the sum of the target population of all the villages assigned to the facility, and, in case of a SMC campaign, the total serving population will be sum of the target population belonging to age group of 3 to 11 months and age group of 12 to 59 months.
11. Fixed post - This field tells which facilities listed in the dashboard are fixed post facilities.
12. Residing village - This field contains the village name where the facility resides. The user can also view the complete boundary information of the village as a tool-tip by clicking on the ‘i’ icon.
13. Action - Using this the user can map the facilities to their catchment areas for microplanning.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.07.55 AM.png" alt=""><figcaption><p>‘Unassigned villages’ screen for the ‘facility catchment mapper’ user role </p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.08.52 AM.png" alt=""><figcaption><p>Screen showing adding villages to the chosen catchment facility</p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.09.52 AM.png" alt=""><figcaption><p>Content of the ‘Unassigned villages’ dashboard</p></figcaption></figure>

This screen shows the list of villages that are not mapped to any catchment facility.&#x20;

Using this screen, the mapper will be able to map the chosen facility to their respective serviceable villages in the list. The mapper will be able to see all the villages that are part of his administrative boundaries and the villages that are not mapped to any facility.

Content of the screen -

Content of the screen -

1. Card showing villages with mapped facilities/POS - This card will show the count of the villages that belong to the mapper’s administrative boundary. It also shows the total number of villages (belonging to the mapper’s admin boundary) that have a catchment facility mapped.
2. Card showing facilities with mapped villages - This card will show the count of the facilities that belong to the mapper’s administrative boundary. It also shows the total number of facilities (belonging to the mapper’s admin boundary) that have a catchment village mapped.
3. Facility search - This will give the user the ability to search the specific facility that needs to be mapped to the catchment boundaries. The search needs to accept partial string match as well.
4. Filters - This will let the users to filter out the specific facilities that he needs to do the facility-catchment area mapping for. The user can filter out the facilities that he wants to map the catchment villages to. Below are the multi-select dropdown filters that the user will get -

&#x20;      a. Facility type - This will have the data of facility type defined during the instance creation

&#x20;      b. Facility status - This will have the facility status defined, which is either permanent or temporary

&#x20;      c. Is fixed post? - This will be an optional field. If the campaign distribution strategy is either ‘fixed post’ or ‘house-to-house and fixed post’, then this filter will be available for the user to choose

&#x20;       d. Residing village - This will have the list of all the villages that the facilities in the dashboard are part of

5. Facility name - This field shows the name of the facility that belongs to the user’s defined boundary.
6. Facility type - This field contains the type of the facilities that are listed in the dashboard.
7. Facility status - This field contains the status (Permanent/Temporary) of the facilities that are listed in the dashboard.
8. Capacity - This field contains the capacity of the facilities that are listed in the dashboard. The capacity can be either ‘Bales’ for bed nets or ‘Blisters’ for SMC campaigns.&#x20;
9. Assigned villages - This field will show the total number of villages that are assigned to the specific facility.
10. Serving population - This field will show the total population that is being served by the facility out of the total capacity of serving population of the facility. The total population that is served by the facility is the sum of the approver target population of the villages assigned. So, in case of a bednet campaign, the total serving population will be the sum of the target population of all the villages assigned to the facility, and, in case of a SMC campaign, the total serving population will be sum of the target population belonging to age group of 3 to 11 months and age group of 12 to 59 months.
11. Fixed post - This field tells which facilities listed in the dashboard are fixed post facilities.
12. Residing village - This field contains the village name where the facility resides. The user can also view the complete boundary information of the village as a tool tip by clicking on the ‘i’ icon.
13. Action - Using this the user can map the facilities to their catchment areas for microplanning.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 11.37.31 AM.png" alt=""><figcaption><p>‘Unassigned villages’ screen for the ‘facility catchment assigner’ user role </p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 11.38.16 AM.png" alt=""><figcaption><p>Screen showing adding villages to the chosen catchment facility</p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 11.41.59 AM.png" alt=""><figcaption><p>Landing page ‘facility catchment assigner’ role </p></figcaption></figure>

This screen is the landing page for the mapper. In this screen, the mapper will be able to view all the facilities/POS and their details that are part of his administrative boundaries. \
Important validation: For the mapper to work on mapping facility/POS to their catchment areas, the population data for the campaign must be approved by the national-level population data approver.

Content of the screen -

1. Card showing villages with mapped facilities/POS - This card will show the count of the villages that belong to the mapper’s administrative boundary. It also shows the total number of villages (belonging to the mapper’s admin boundary) that have a catchment facility mapped.
2. Card showing facilities with mapped villages - This card will show the count of the facilities that belong to the mapper’s administrative boundary. It also shows the total number of facilities (belonging to the mapper’s admin boundary) that have a catchment village mapped.
3. Facility search - This will give the user the ability to search the specific facility that needs to be mapped to the catchment boundaries. The search needs to accept partial string match as well.
4. Filters - This will let the users to filter out the specific facilities that he needs to do the facility-catchment area mapping for. The user can filter out the facilities that he wants to map the catchment villages to. Below are the multi-select dropdown filters that the user will get -

&#x20;      a. Facility type - This will have the data of facility type defined during the instance creation

&#x20;     b. Facility status - This will have the facility status defined, which is either permanent or temporary

&#x20;     c. Is fixed post? - This will be an optional field. If the campaign distribution strategy is either ‘fixed post’ or ‘house-to-house and fixed post’, then this filter will be available for the user to choose

&#x20;     d. Residing village - This will have the list of all the villages that the facilities in the dashboard are part of

5. Facility name - This field shows the name of the facility that belongs to the user’s defined boundary.
6. Facility type - This field contains the type of the facilities that are listed in the dashboard.
7. Facility status - This field contains the status (Permanent/Temporary) of the facilities that are listed in the dashboard.
8. Capacity - This field contains the capacity of the facilities that are listed in the dashboard. The capacity can be either ‘Bales’ for bed nets or ‘Blisters’ for SMC campaigns.&#x20;
9. Assigned villages - This field will show the total number of villages that are assigned to the specific facility.
10. Serving population - This field will show the total population that is being served by the facility out of the total capacity of serving population of the facility. The total population that is served by the facility is the sum of the approver target population of the villages assigned. So, in case of a bednet campaign, the total serving population will be the sum of the target population of all the villages assigned to the facility, and, in case of a SMC campaign, the total serving population will be sum of the target population belonging to age group of 3 to 11 months and age group of 12 to 59 months.
11. Fixed post - This field tells which facilities listed in the dashboard are fixed post facilities.
12. Residing village - This field contains the village name where the facility resides. The user can also view the complete boundary information of the village as a tool-tip by clicking on the ‘i’ icon.
13. Action - Using this the user can map the facilities to their catchment areas for microplanning.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 2.11.25 PM.png" alt=""><figcaption><p>‘Unassigned villages’ screen for the ‘facility catchment assigner’ user role </p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 2.12.07 PM.png" alt=""><figcaption><p>Screen showing adding villages to the chosen catchment facility</p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 2.12.47 PM.png" alt=""><figcaption><p>Content of the ‘Unassigned villages’ dashboard</p></figcaption></figure>

This screen shows the list of villages that are not mapped to any catchment facility.&#x20;

Using this screen, the mapper will be able to map the chosen facility to their respective serviceable villages in the list. The mapper will be able to see all the villages that are part of his administrative boundaries and the villages that are not mapped to any facility.

Content of the screen -

1. Card with chosen facility details - This card will show the details of the facility that is chosen. This will help the mapper to understand which facility is chosen and which all villages can be mapped to it. Below are the details of the facility that will be shown -

&#x20;       a. Facility name

&#x20;      b. Facility type

&#x20;      c. Facility status

&#x20;     d. Facility capacity

&#x20;     e. Population being served out of the total serving population capacity of the facility

&#x20;     f. Is fixed post? (Optional)

&#x20;     g. Residing village

2. Boundary filter - This user will be able to filter out the boundary that is assigned to him, as well as the child boundaries. For example, if the mapper belongs to a district, then he will be able to see the filters for all the hierarchies and their boundaries at and below the assigned district. The mapper will be able to see the boundaries of the assigned district, their administrative post, their localities and their villages. All the filters will be search enabled multi-select dropdowns.
3. Boundary data - The user will be able to see the boundary data on his screen. Only those boundaries will be visible that are part of his assigned administrative hierarchy and lower hierarchies.
4. Village accessibility level button - Here the user will be able to see the village accessibility level if it was updated by the population data approver. If there is no data available for the village accessibility, then the accessibility data will be empty. Below are the details for village accessibility shown -

&#x20;      a. Village road condition

&#x20;     b. Village terrain

&#x20;     c. Village transport mode

Note: The data will be shown as a non-editable popup

5. Village security level button - Here the user will be able to see the village security level if it was updated by the population data approver. If there is no data available for the village security level, then the security level data will be empty. Below are the details for village security level shown -

&#x20;       a. Is your village prone to civil unrest like violent protests, riots, etc.?

&#x20;       b. How often do the security forces patrol the village?

Note: The data will be shown as a non-editable popup

6. Approved target population - Here the user will be able to see the approved target population of the village. This is for a bednet campaign.
7. Approved target population (Age 3 - 11 months) - Here the user will be able to see the approved target population (Age 3 - 11 months) of the village. This is for a SMC campaign.
8. Approved target population (Age 12 - 59 months) - Here the user will be able to see the approved target population (Age 12 - 59 months) of the village. This is for a SMC campaign.
9. Distance from the catchment facility (KMs) -

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-23 at 10.49.19 AM.png" alt=""><figcaption><p>Edit/Update the distance between catchment village and facility</p></figcaption></figure>

Here the mapper can edit and enter the distance of the facility to the catchment village. This field is optional.

Validation: The field can take only numeric values. Error message when the entered value is invalid “Please enter a numeric value”.

10. Assigned facility - For the ‘Unassigned villages dashboard’, none of the villages should be mapped to any catchment facility.&#x20;
11. ‘Assign to “facility name”’ button - The user will be able to see the list of the villages assigned to his administrative boundaries. The user can choose multiple villages at a time to assign them to the chosen facility. There should be a confirmation pop-up before the user approves the assignment of the facility to their catchment villages. Once confirmed, the villages will be tagged to the chosen facility for microplan.

Pop-up message - Are you sure you want to assign the selected villages to “facility name”? - There will be a Yes/No action button.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-23 at 10.51.09 AM.png" alt=""><figcaption><p>‘Assigned villages’ screen for the ‘facility catchment assigner’ user role</p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-23 at 10.51.57 AM.png" alt=""><figcaption><p>Screen showing removing villages from the chosen catchment facility</p></figcaption></figure>

This screen will show all the villages that are assigned to the chosen facility.

Here, all the content of the dashboard will be the same as the ‘Unassigned village dashboard’, with only a difference -

In place of the ‘Assign’ button, there will be an ‘Remove from “Facility name”’ button and the mapper can choose multiple villages that he wants to unassign from the selected facility. There should be a confirmation pop-up before the user approves the unassignment of the facility to their catchment villages. Once confirmed, the villages will be untagged from the chosen facility and those villages will move to the ‘Unassigned villages dashboard’ of the chosen facility for remapping.

Pop up message - Are you sure you want to remove the selected villages from the mapped “facility name”? - There will be a Yes/No action button.

<br>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-23 at 10.54.12 AM.png" alt=""><figcaption><p>Screen for finalising the facility to village mapping  </p></figcaption></figure>



Note - The final approver of the facility assignment to the villages will be the national or highest administrative hierarchy ‘facility catchment assigner’. The national level ‘facility catchment assigner’ will have a button called ‘Finalize facility to village assignment’, and the button will only be enabled when all the villages under the campaign zone are mapped to their respective facilities/POS. Once the catchment mapping is finalized, there will be no other actions allowed on the dashboard. The user can just work with the filters to view the mapping but can’t make any changes. Once finalised, the microplan estimation should be triggered for the campaign villages.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.23.38 AM.png" alt=""><figcaption><p>Screen showing finalised village-to-facility mapping</p></figcaption></figure>

This screen will be shown to the national level facility catchment mapper once all the campaign villages are assigned to their facilities and the assignment has been finalized by the national level facility catchment mapper.

15. **Geospatial view -**&#x20;

Actor: Supervisor (Population data approver, Microplan viewer, Microplan approver, and Facility catchment mapper)

Administrative boundary: Country (Highest boundary), Province, Districts, Admin post, Locality (Second lowest boundary)

This is the flow that the user will use to visualise the microplan estimation of each village (lowest boundary) and each facility/POS.

Important validation: For the geospatial estimation view to work, it’s important that the facility-catchment area mapping is finalized for the campaign by the national-level facility catchment mapper.&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.25.05 AM.png" alt=""><figcaption><p>Geo-spatial view of the villages and facilities</p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.25.53 AM.png" alt=""><figcaption><p>Tool-tip information on the facility and village information</p></figcaption></figure>

Content of the screen -

1. Boundary filter - The user will be able to filter out the boundaries at each hierarchy and visualise the geo-cords of specific villages or facilities/POS at the chosen boundaries.
2. Map - Here the map can be accessed using the openstreetmap. The integration is already built so that it can be reused.
3. Layers - The user can view the available layers of the map using the layers capability available. The default layer will be of satellite view.
4. Filters - The user will be able to see two filter option on map:

&#x20;       a. Village filter: This will be chosen by default. This will show all the geo-coordinates of the villages (lowest boundary) on the map.

&#x20;      b. Facility/POS filter: This filter, if chosen, will show all the geo-coordinates of the facilities/POS on the map.

Validation: The two options will be checkboxes and a user can choose either or the options or both. By default, the village filter will be enabled.

5. Tool-tip information - This will show the estimate of the resources and other details for each village and facility/POS that the user chooses:

&#x20;       a. Village tool-tip information: The user will be able to view certain important information for the village on click -

1. Village name: The user will be able to see the name of the village on top.
2. Target population: This will show the target population of the village that will receive the bednets. This is specifically for bednet campaigns.
3. Target population (Age 3 - 11 months): This will show the target population of the village within the age group of 3 - 11 months that will receive the SPAQ blisters. This is specifically for the SMC campaign.
4. Target population (Age 12 - 59 months): This will show the target population of the village within the age group of 12 - 59 months that will receive the SPAQ blisters. This is specifically for the SMC campaign.
5. Total bednets: This will show the total bednets that will be required in the village for the campaign. This is specifically for bednet campaigns.
6. Total bales: This will show the total bednets that will be required in the village for the campaign. One bale ideally has 50 bednets in total. This is specifically for bednet campaigns.
7. Total SPAQ blisters (Age 3 - 11 months): This will show the total SPAQ blisters that will be required for the population within the age 3 - 11 months in the village for the campaign. This is specifically for the SMC campaign.
8. Total SPAQ blisters (Age 12 - 59 months): This will show the total SPAQ blisters that will be required for the population within the age 12 - 59 months in the village for the campaign. This is specifically for the SMC campaign.
9. Serving facilities/POS: This will show the total number of facilities/POS that serves the chosen village.

&#x20;       b. Facility/POS tool-tip information: The user will be able to view certain important information for the facility/POS on click -

1. Facility/POS name: The user will be able to see the name of the facility/POS on top.
2. Facility type: The user will be able to see the type of facility on the tool-tip.
3. Facility status: The user will be able to see the status of the facility on the tool-tip.
4. Capacity (Bales or SPAQ blisters): The user will be able to view the capacity of the facility on the tool-tip. For bednet campaign, the capacity will be bales and for the SMC campaign, the capacity will be SPAQ blisters.
5. Is fixed post?: The user will be able to see if the facility/POS a fixed post or not. This will only be shown if the resource distribution strategy for the campaign is either fixed post or mixed (fixed post & H2H).
6. Residing village: The user will be able to see the village at which the facility/POS resides.
7. Catchment villages: This will be the count of the villages (lowest boundaries) that the facility serves.
8. Serving population: This will be the total number of target population that the facility will serve. This is basically the sum of the total serving population of the villages that the facility is mapped to.
9. Serving bednets: This will be the total number of bednets that will be distributed to the villages that are mapped to the chosen facility. This is specifically for the bednet campaign.
10. Serving SPAQ blisters: This will be the total number of SPAQ blisters that will be distributed to the villages that are mapped to the chosen facility. This is specifically for the SMC campaign.

\
16\. **Microplan approver flow -**

Actor: Supervisor (Microplan approver)

Administrative boundary: Country (Highest boundary), Province, Districts, Admin post, Locality (Second last boundary)

This is the flow for approving the microplan estimation for the boundaries that are part of the campaign. It’s an important step to make sure that the microplan estimation done by the system is correct and that the same microplan estimation can be used for campaign setup. So, the microplan estimation must be approved by the designated users at each administrative level.

Microplan approvers can act on different administrative hierarchies and depending on the hierarchy and boundaries assigned, the microplan estimation for those villages will be shown to the user for validation. For example, the Microplan approver can belong to a country, province, district, administrative post, or locality, and concerning the boundaries assigned, he will be able to see the microplan estimation for the assigned villages.

The final approver for the Microplan estimation of the country will always be the national level ‘Microplan approver’ where all the villages of the campaign zone along with their microplan estimation will be shown to the national level microplan approver.

Important validation: For the microplan approver workflow to work, it’s important that the facility-catchment area mapping is finalized for the campaign by the national-level facility catchment mapper.&#x20;

<br>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.31.55 AM.png" alt=""><figcaption><p>Landing page of the ‘Microplan approver’ role</p></figcaption></figure>

This is the landing page for the ‘Microplan approver’ user where he will see the microplan estimation of the villages that are part of the administrative boundaries assigned to him. The user can check out the detailed estimation information and make changes in the microplan assumptions for the selected villages and send the changes for approval. If no changes are required in the microplan estimation, the user can directly validate the microplan estimation for the villages that are part of his assigned administrative boundaries.

Content of the landing page -

1. Filters on the action items on the user - This filter will help the user to filter out the villages that need some action. Below are the filters that will be shown to the user:

&#x20;       a. Villages with pending validation - This filter will show the list of villages whose microplan estimations are pending to be validated by the user. The user will be able to see the list of villages whose actions are pending on the user as well as on the users that belong to the child boundaries of the parent district level data approver. This filter will be further segregated as -

1. Pending on me - This will show the list of the villages whose microplan estimations need to be validated by the assigned user of the ‘district’. This will also show a metric - the number of villages whose microplan estimations are pending to be validated by the user. This should be by default chosen when the user lands on the page.
2. Pending on subordinates - This will show the list of the villages whose microplan estimations need to be validated by the users that belong to the child boundaries of the parent ‘district’. This will also show a metric - the number of villages whose microplan estimations are pending to be validated by the subordinates.

Note: A microplan approver belonging to a ‘district’ can validate the microplan estimations of the villages that belong to the child boundaries of the ‘district’, even though those villages may have their own microplan approvers assigned.

The user filtering out the villages with pending validation can perform 2 different activities -

* Check and validate the microplan estimations for the villages
* Change microplan assumptions for the villages and send the changes for approval to higher authorities

&#x20;     b. Validated villages - This filter will show the list of villages that are part of the user’s assigned boundary and whose microplan estimations have been validated either by the user himself or his subordinates at the lower administrative hierarchy level. This will also show a metric - the number of villages whose microplan estimations are validated.

The user filtering out the validated villages can perform 2 different activities -

* Check and send the villages for correction if the microplan estimations are not proper
* Change microplan assumptions for the villages and send the changes for approval to higher authorities

&#x20;       c. Villages with pending approval - This filter will show the list of villages whose microplan assumptions have been changed by the user’s subordinates at the lower administrative hierarchies. This will also show a metric - the number of villages that are pending for approval by the user.&#x20;

The assigned user who can see the pending approval villages here can perform 2 activities -

* Check and approve the recommended village population data
* Send back the village data for correction to the user who sent the village data for approval

2. Dynamic boundary filters concerning parent and child administrative hierarchy - This is a dynamic filter that will be given to the user for filtering out specific boundaries. This will be a search-enabled dropdown for every filter content. The filters will be added or removed depending on the parent hierarchy assigned to the user. For example, if the user belongs to district hierarchy (Parent), then all child hierarchies and their boundaries will be part of the filter.
3. Additional filters - Apart from the above filters, there will be a couple of more filters that will be available to the users. The filters are -

&#x20;      a. Facility or point of service - This will show the list of facilities that are mapped to the villages that are part of the microplan approver’s jurisdiction.

&#x20;     b. Village road condition - This will show the list of road conditions that are configured and users will be able to filter out the villages with the chosen road condition.

&#x20;      c. Village terrain - This will show the list of terrain types that are configured and users will be able to filter out the villages with the chosen terrain types.

&#x20;     d. Village transport mode - This will show the list of transport modes that are configured during vehicle registration and users will be able to filter out the villages with the chosen transport mode.

&#x20;     e. Civil unrest occurrence - This will show the list of civil unrest occurrence frequencies configured and users will be able to filter out the villages with the chosen civil unrest occurrence frequency.

&#x20;     f. Security forces patrolling -This will show the list of security forces patrolling frequencies configured and users will be able to filter out the villages with the chosen security forces patrolling frequency.

Metrics to be shown - On top of the dashboard, the microplan approver will be able to see the overall metrics for the villages under his jurisdiction. The metrics are dynamic and it will change depending on the filter selected. There will be different metrics captured for different campaign types.

Metrics for Bednet campaign -

a. Target population

b. Total household

c. Bednets required

d. Bales required

Metrics for SMC campaign -

a. Target population (Age 3-11 months)

b. Target population (Age 12-59 months)

c. Total SPAQ-1 required (Age 3-11 months)

d. Total SPAQ-2 required (Age 12-59 months)

e. Total SPAQ-1 required with buffer (Age 3-11 months)

f. Total SPAQ-2 required with buffer (Age 12-59 month)

5. Data content for the microplan approver -&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.38.50 AM.png" alt=""><figcaption><p>Sample screen for the data content of microplan estimation</p></figcaption></figure>

The user will be able to see all the villages that are part of the user’s jurisdiction and the microplan estimations of the villages concerning the configurations chosen by the system administrator while setting up the microplan. The fixed data points in this dashboard are -

1. Boundary data - The user will be able to see the boundary details of the jurisdiction that is assigned to him. For example, if the user belongs to a district, then he will be able to see the boundary data of the district, its admin posts, its localities, and finally villages along with their estimations.
2. Serving facility/POS - The facility is mapped to the village. This data can be fetched from the village facility catchment mapping.
3. Village road condition - This data can be fetched if the population data approver fills in the data for the villages assigned.
4. Village terrain - This data can be fetched if the population data approver fills the data for the villages assigned.
5. Civil unrest occurrence - This data can be fetched if the population data approver fills the data for the villages assigned.
6. Security forces patrolling - This data can be fetched if the population data approver fills the data for the villages assigned.
7. Assigned microplan approver - This will have the information of who is the assigned microplan approver for the village. This will be helpful for validating the villages that are assigned to the user’s child boundary’s microplan approver (subordinates).
8. Total population - This is the total population of the village that is approved by the country level population data approver.
9. Target population - This is the target population of the village that is approved by the country level population data approver. This is for a bednet campaign.
10. Target population (Age 3-11 months) - This is the target population (Age 3-11 months) of the village that is approved by the country level population data approver. This is for a SMC campaign.
11. Target population (Age 12-59 months) - This is the target population (Age 12-59 months) of the village that is approved by the country level population data approver. This is for a SMC campaign.
12. View comment logs - The user will be able to see the comment logs for every action taken on the village using the comment logs button that will be available corresponding to each village.
13. View change logs - The user will be able to see the changes done in the microplan estimations of the villages once the microplan assumptions are updated.

Rest of the data points will be flexible and depending on the configuration chosen by the system admin, those estimation data points will be shown in this dashboard.

6. Action on the villages - There will be certain actions that the user can take on the villages depending on the filter chosen. The actions are -

&#x20; 1\. Validate - This action will be available for the filters chosen ‘Villages with pending validation’. More details will be provided below.

2. Send back for correction - This action will be available for the filters chosen ‘Villages with pending approval’ and ‘Validated villages’. More details will be provided below.
3. Approve - This action will be available for the filters chosen ‘Villages with pending approval’. More details will be provided below.
4. Customise assumptions - This action will be available for the filters chosen ‘Validated villages’ and ‘Villages with pending validation’. More details will be provided below.

Workflow diagram for microplan approver -

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.42.39 AM.png" alt=""><figcaption></figcaption></figure>

Workflow for validating village microplan estimation -

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.43.49 AM.png" alt=""><figcaption><p>Screen for validating microplan estimation for the villages</p></figcaption></figure>

This workflow will let the user validate the microplan estimations for the villages that are under the user’s jurisdiction. This workflow will be a part of the ‘Villages with pending validation’ bucket where the user can multiple villages at once and then validate the villages in bulk if the village microplan estimations seem correct to the user. Once the selected villages are validated, the validated villages will move from the ‘Villages with pending validation’ bucket of the user to the ‘Validated villages’ bucket of the user. Other users who have access to the same jurisdiction will be able to see the validated villages in the ‘Validated villages’ bucket. It’s important that the user adds a comment/reason for validating the microplan estimation of the assigned villages. Any higher authority user will be able to check out the comment logs from the dashboard. Attaching the comment box UI below:

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.45.18 AM.png" alt=""><figcaption><p>Comment box UI for validating the village microplan estimation</p></figcaption></figure>

Workflow for customisation of microplan assumptions -

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.46.26 AM.png" alt=""><figcaption><p>Screen for customising microplan assumptions for the villages (Villages with pending validation bucket)</p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.47.14 AM.png" alt=""><figcaption><p>Screen for customising microplan assumptions for the villages (Validated villages bucket)</p></figcaption></figure>

When the villages are available in the ‘Villages with pending validation’ and ‘Validated villages’ buckets, the microplan approver will be able to choose one or more villages to customize their microplan assumptions as per requirement. The microplan approver will be able to see the list of all villages that are under the microplan approver’s jurisdiction.

Once the user clicks on the ‘Customise assumptions’ button, the microplan approver will be redirected to a screen where the user can play around with the microplan assumptions unless the desired microplan estimation for the chosen villages is achieved.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.48.15 AM.png" alt=""><figcaption><p>Screen for customising microplan assumptions for the villages</p></figcaption></figure>

When the microplan approver chooses the village to customize their microplan assumptions, the user will be able to see the standard or already configured assumption value. The user can change and update the microplan assumption value and see the outcome of the changes in the microplan estimation dashboard by clicking on the ‘Apply’ button.

Once the microplan estimations are updated and finalized, the microplan approver can click on the ‘Confirm customisation’ button to go ahead with the estimation changes for the selected villages.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.49.08 AM.png" alt=""><figcaption><p>Screen for sending the microplan assumption changes for approval</p></figcaption></figure>

Upon clicking the ‘Confirm customisation’, the user will be shown a pop-up showing which all assumptions are being changed and what was their old value and what is their updated value. The old value will be the standard assumption value if the user is changing the microplan assumption for the village for the first time, if the user is changing the microplan assumption for a village for second/third/so on times, then the old value of the microplan assumption will be last saved value of the microplan assumption. For example, for a village, one of the assumptions was changed from 10 to 20 and then saved by a user. Then, for the same village, the same assumption is changed from 20 to 40, so upon confirmation, the user should be able to see the old value as 20 and the new value as 40.

For sending the changes for approval, the microplan approver needs to add a comment/reason. Below is the UI for adding comments before sending the changes for approval:

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.50.32 AM.png" alt=""><figcaption><p>Comment box UI for sending the assumption changes for approval</p></figcaption></figure>

\
Workflow for approving the village microplan estimation -

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.51.45 AM.png" alt=""><figcaption><p>Screen for approving microplan estimation for the villages</p></figcaption></figure>

If the supervisor microplan approver feels that the recommended changes in the village estimations are correct, then the microplan approver will approve the village’s microplan estimation using the ‘Approve’ button (The user can choose multiple villages for approval at once). Upon approving the updated microplan estimation for the villages, the villages will be moved from the assigned microplan approver’s ‘Villages with pending approval’ bucket to the next higher administrative hierarchy microplan approver’s ‘Villages with pending approval’ bucket. This workflow will go on until the national or highest administrative hierarchy level microplan approver approves the microplan estimation changes for the villages. Once the changes reach the highest administrative hierarchy for approval and the national level microplan approver approves the updated microplan estimation changes, the village status will be ‘Validated’ and the village will reside in the ‘Validated villages’ bucket. For every approval, the microplan approver needs to add a reason as a comment and that comment will be seen in the comment logs.&#x20;

Note: The microplan approver will be able to see and take actions on the pending approvals on him as well as the pending approvals on his subordinates.

Comment box UI:

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.52.57 AM.png" alt=""><figcaption><p>Comment box UI for validating the village microplan estimation</p></figcaption></figure>

Workflow for sending back the village microplan estimation for correction -

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.54.04 AM.png" alt=""><figcaption><p>Screen for sending back microplan estimation for the villages (Validated villages bucket)</p></figcaption></figure>

&#x20;This workflow will be available in the ‘Villages with pending approval’ and ‘Validated villages’ bucket of the dashboard.

When the villages are available in the ‘Validated villages’ bucket and the microplan approver feels that the microplan estimation for some of the villages are incorrect or needs correction, the microplan approver can choose those villages and send them back for correction using the ‘Send back for correction’ button. The villages that are sent back for correction by the microplan approver will move from the ‘Validated villages’ bucket to the ‘Villages with pending validation’ bucket of the user, who first validated the microplan estimation of the villages.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.55.01 AM.png" alt=""><figcaption><p>Screen for sending back microplan estimation for the villages (Villages with pending approval bucket)</p></figcaption></figure>

\
When the villages are available in the ‘Villages with pending approval’ bucket and the microplan approver feels that the changed/updated microplan estimation for some of the villages need correction, then the microplan approver chooses those villages and sends them back for correction using the ‘Send back for correction’ button. The villages that are sent back for correction by the microplan approver will move from the ‘Villages with pending approval’ bucket to the ‘Villages with pending validation’ bucket of the user, who first made changes in the microplan assumptions and submitted the data for approval to the higher jurisdiction microplan approver.

It is important that every time the user sends back the data for correction, he needs to add a comment/reason for his action. Attaching the comment box UI below:

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.56.05 AM.png" alt=""><figcaption><p>Comment box UI for sending back the village microplan estimation for correction</p></figcaption></figure>

\
View comment logs for villages -

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.57.05 AM.png" alt=""><figcaption><p>Screen for comment logs pop-up</p></figcaption></figure>

The user can see the comment logs by clicking on the comment logs link. The user will be able to see the detailed action taken on a village along with the timestamp and comment details. This will help the supervisors to understand what actions have been taken in a village and who took the action. This will help in keeping traceability of the changes happening to a village. The button to check the comment logs will be available corresponding to each village in the dashboard.

The content of the comment logs are -

1. Status of the action - The user will be able to see the status of the actions taken by the other users. For every action, the status will be captured w.r.t the village and updated in the comment logs. There will be 4 status on a high level:

&#x20;       a. Sent for approval - Once the microplan assumptions have been changed for one or more villages by a user and forwarded for approval, the status will be changed to ‘Sent for approval’.

&#x20;      b. Approved - Once the user approves the recommended microplan assumption changes for the villages, it moves to ‘Approved’ status.

&#x20;      c. Validated - Once the microplan estimations for the villages have been validated by the user or by the highest jurisdiction level microplan approver, the status will be changed to ‘Validated’ and the village will be moved to ‘Validated villages’ bucket.

&#x20;     d. Sent for correction - Once the microplan estimations for the villages have been checked by the supervisor and supervisors decide to send the village data for correction, the status will be changed to ‘Sent for correction’.

2. User’s name and role - Whenever a user takes an action on the village and puts a comment, for every action, the user’s name and role will be captured and shown in the comment logs.
3. Timestamp - Whenever a user takes an action on the village and puts a comment, for every action, the timestamp of the action will be captured. It should be in the international timestamp format “YYYY-MM-DD HH:MM”.
4. Comment - Whenever a user takes an action on the village and puts a comment, it will be captured alongside the other details.

View microplan estimation change logs for villages -

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 11.58.48 AM.png" alt=""><figcaption><p>Screen for change logs pop-up</p></figcaption></figure>

If a village goes through multiple changes in the assumptions, and as a result of which the microplan estimations for the village changes multiple times, all these changes in the microplan estimations need to be captured in the change logs for the village. The button to check the change logs will be available corresponding to each village in the dashboard. Below are the information that will be shown on the change logs pop-up -

1. Which microplan estimation data points changed? The user should be able to see the microplan estimation data points that have been changed after updating the microplan assumptions.
2. Who updated the microplan assumptions? The user should be able to see who has updated the microplan assumptions as a result of which the microplan estimations got changed for the village.
3. Timestamp of the changes -The user should be able to see at what time the microplan assumptions were changed. It should be in the international timestamp format “YYYY-MM-DD HH:MM”.
4. What’s the change in the microplan estimations? The user should be able to see what was the earlier value of the microplan estimation data point vs the updated value of the microplan estimation data point.

Note on microplan estimation for the villages -

It’s crucial that for doing the human resource microplan estimation, every village needs to have the assigned facility mapped. Depending on the type of facility (fixed post or non-fixed post), the system will calculate the human resource estimations accordingly. But, it shouldn’t affect the medical resource estimation for the village, such as, number of bednets or SPAQ required for the village shouldn’t be dependent on the facility mapped to the village.

Use-case to cover: What if the country-level microplan approver customizes the microplan assumptions?

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 12.07.19 PM.png" alt=""><figcaption><p>Screen showing the confirmation pop-up for the assumption changes to country-level microplan approver</p></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 12.08.17 PM.png" alt=""><figcaption><p>Screen showing the comment/reason box that the country microplan approver has to fill if the assumptions are updated</p></figcaption></figure>

The country-level microplan approver can change microplan assumption for any village under his jurisdiction. Now, since the country-level microplan approver doesn’t have any superior role assigned above him, the changes will not go through any approval process. The country-level microplan approver can simply make the changes, add a reason for the changes, and save the changes. The status of the village will remain unchanged but all the changes should be logged in the comment and change logs.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 12.09.25 PM.png" alt=""><figcaption><p>Screen for finalising microplan by national level Microplan approver</p></figcaption></figure>

Note - The final approver of the microplan estimation for the campaign villages will be the national or highest administrative hierarchy ‘Microplan approver’. The national level ‘Microplan approver’ will have a button called ‘Finalize microplan’ (Irrespective of any filters), and the button will only be enabled when the ‘Villages with pending validation’ is 0, ‘Villages with pending approval’ is 0 and ‘Validated villages’ is x/x, that is, if there are 500 villages in the campaign zone, then 500 villages should be in the validated status. Once the microplan estimation data is finalized, there will be no action allowed on the dashboard. The user can just work with the filters to view the data but can’t make any changes. Once the microplan estimates are finalised, the user can download the Excel for the microplan estimates from the home page.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 12.10.21 PM.png" alt=""><figcaption><p>Screen showing finalised microplan message to the user</p></figcaption></figure>

\
This is the final screen that the country-level microplan approver will be able to see once the microplan is finalised. The user can either download the microplan estimation as an Excel or go to the admin console to set up the campaign for the microplan.

17. **Microplan viewer flow -**

Actor: Supervisor (Microplan viewer)

Administrative boundary: Country (Highest boundary), Province, Districts, Admin post, Locality (Second last boundary)

This is the flow for viewing the microplan estimation for the boundaries that are part of the campaign. It’s an important step to make sure that the microplan estimation done by the system is correct and that the same microplan estimation can be used for campaign setup. So, the microplan estimation must be viewed/reviewed by the designated users at each administrative level.

Microplan viewers can act on different administrative hierarchies and depending on the hierarchy and boundaries assigned, the microplan estimation for those villages will be shown to the user. For example, the Microplan viewer can belong to a country, province, district, administrative post, or locality, and concerning the boundaries assigned, he/she can see the microplan estimation for the assigned villages.

Validation: For the microplan viewer workflow to work, it’s important that the facility-catchment area mapping is finalized for the campaign by the national-level facility catchment mapper.&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-11 at 12.11.57 PM.png" alt=""><figcaption><p>Screen for showing the microplan estimations to microplan viewer</p></figcaption></figure>

This is the landing page for the ‘Microplan viewer’ user where he will see the microplan estimation of the villages that are part of the administrative boundaries assigned to him. Here, the user will only be able to see the villages that have been validated by the assigned microplan approver.

Content of the landing page -

1. Dynamic boundary filters with respect to parent and child administrative hierarchy - This is a dynamic filter that will be given to the user for filtering out specific boundaries. This will be a search-enabled dropdown for every filter content. The filters will be added or removed depending on the parent hierarchy assigned to the user. For example, if the user belongs to district hierarchy (Parent), then all child hierarchies and their boundaries will be part of the filter.
2. Additional filters - Apart from the above filters, there will be a couple of more filters that will be available to the users. The filters are -

&#x20;       \- Facility or point of service - This will show the list of facilities that are mapped to the villages that are part of the microplan approver’s jurisdiction.

&#x20;       \- Village road condition - This will show the list of road conditions that are configured and users will be able to filter out the villages with the chosen road condition.

&#x20;       \- Village terrain - This will show the list of terrain types that are configured and users will be able to filter out the villages with the chosen terrain types.

&#x20;        \- Village transport mode - This will show the list of transport modes that are configured during vehicle registration and users will be able to filter out the villages with the chosen transport mode.

&#x20;        \- Civil unrest occurrence - This will show the list of civil unrest occurrence frequencies configured and users will be able to filter out the villages with the chosen civil unrest occurrence frequency.

&#x20;         \- Security forces patrolling -This will show the list of security forces patrolling frequencies configured and users will be able to filter out the villages with the chosen security forces patrolling frequency.

3. Metrics to be shown - On top of the dashboard, the micro plan viewer will be able to see the overall metrics for the villages under his jurisdiction. The metrics are dynamic, and they will change depending on the filter selected. Different metrics will be captured for different campaign types.

Metrics for Bednet campaign -

&#x20;      \- Target population

&#x20;      \- Total household

&#x20;       \- Bednets required

&#x20;        \- Bales required

Metrics for SMC campaign -

&#x20;       \- Target population (Age 3-11 months)

&#x20;       \- Target population (Age 12-59 months)

&#x20;       \- Total SPAQ-1 required (Age 3-11 months)

&#x20;       \- Total SPAQ-2 required (Age 12-59 months)

&#x20;       \- Total SPAQ-1 required with buffer (Age 3-11 months)

&#x20;       \- Total SPAQ-2 required with buffer (Age 12-59 month)

4. Data content for the microplan viewer -&#x20;



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-09-19 at 9.47.48 AM.png" alt=""><figcaption><p>Sample screen for the data content of the microplan estimation</p></figcaption></figure>

The user will be able to see all the villages that are part of the user’s jurisdiction and the microplan estimations of the villages concerning the configurations chosen by the system administrator while setting up the microplan. The fixed data points in this dashboard are -

1. Boundary data - The user will be able to see the boundary details of the jurisdiction that is assigned to him. For example, if the user belongs to a district, then he will be able to see the boundary data of the district, its admin posts, its localities and finally villages along with their estimations.
2. Serving facility/POS - The facility is mapped to the village. This data can be fetched from the village facility catchment mapping.
3. Village road condition - This data can be fetched if the population data approver fills the data for the villages assigned.
4. Village terrain - This data can be fetched if the population data approver fills the data for the villages assigned.
5. Civil unrest occurrence - This data can be fetched if the population data approver fills the data for the villages assigned.
6. Security forces patrolling - This data can be fetched if the population data approver fills the data for the villages assigned.
7. Assigned microplan approver - This will have the information of who is the assigned microplan approver for the village. This will be helpful for validating the villages that are assigned to the user’s child boundary’s microplan approver (subordinates).
8. Total population - This is the total population of the village that is approved by the country level population data approver.
9. Target population - This is the target population of the village that is approved by the country level population data approver. This is for a bednet campaign.
10. Target population (Age 3-11 months) - This is the target population (Age 3-11 months) of the village that is approved by the country level population data approver. This is for a SMC campaign.
11. Target population (Age 12-59 months) - This is the target population (Age 12-59 months) of the village that is approved by the country level population data approver. This is for a SMC campaign.
12. View comment logs - The user will be able to see the comment logs for every action taken on the village using the comment logs button that will be available corresponding to each village.
13. View change logs - The user will be able to see the changes done in the microplan estimations of the villages once the microplan assumptions are updated.

Rest of the data points will be flexible and depending on the configuration chosen by the system admin, those estimation data points will be shown in this dashboard.

## **Integration with Console:**

It is critical for the program team to set up the campaign as per the microplan created. And in order to do that, the admin console, which sets up the campaign, needs to map the correct microplan for campaign creation. As part of the integration, the Microplanning platform will share the below details with the admin console for campaign setup:

1. Microplan name
2. Campaign details
3. Facility data
4. Administrative boundaries and their targets
5. Number of human resources required as per the campaign distribution strategy chosen

&#x20;       a. Number of fixed post registration members required and boundary

&#x20;       b. Number of fixes post distribution members required and boundary

&#x20;       c. Number of household registration members required and boundary

&#x20;       d. Number of household distribution members required and boundary

&#x20;       e. Number of fixed post registration supervisors required and boundary

&#x20;       f. Number of fixed post distribution supervisors required and boundary

&#x20;       g. Number of household registration supervisors required and boundary

&#x20;       h. Number of household distribution supervisors required and boundary

&#x20;       i. Number of household registration monitors required and boundary

&#x20;       j. Number of household distribution monitors required and boundary

The admin console needs to provide the program team with a screen to choose the microplan for which the campaign needs to be set up.

## **Success metrics for microplanning module v0.1 -**

1. User adoption and engagement -

&#x20;      \- User Registration: The number of microplan users registered on the platform.

&#x20;      \- Session Time: The average amount of time users spend on the platform in minutes.

&#x20;      \- Population coverage accuracy - The total population considered in the microplan vs the total population captured during the campaign execution.

&#x20;      \- Resource utilization accuracy - The total number of resources (bednets, frontline workers, vehicles, etc.) estimated during the microplanning phase versus a total number of resources utilised during campaign execution.

&#x20;      \- Operational efficiency - Time required to finalise a microplan from the created time.

&#x20;      \- Microplan adoption - The number of microplans created w.r.t countries.

&#x20;       \- Reusability of Microplans: The frequency with which previous microplans are reused or adapted for new campaigns.

**System specs & validation for Microplan module v0.1 -**

Find the system specification [here](https://docs.google.com/spreadsheets/d/1kUe7pScVDv05M_Q2OrZCKrAj9_3Y8eRZrZIXwqRdJYQ/edit?gid=476425343#gid=476425343)
