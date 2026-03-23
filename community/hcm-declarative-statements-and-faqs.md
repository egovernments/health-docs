---
hidden: true
---

# HCM Declarative Statements & FAQs

## HCM Overview

### Mobile App

* The mobile application is offline first and needs the internet to log in and initialise it once, after which, it can be used offline.
* All workflows in the application have some mandatory fields, which can be disabled by updating the code configuration (Needs a technical resource to make the changes- UI will be available from March 2025 onwards through HCM Console).
*   All workflow screens have the flexibility of additional data fields, which can be configured by updating the code configuration (Needs a technical resource to make the changes- UI will be available from March 2025 onwards through HCM Console).

    * Note: Additional fields configured will not be available as KPI’s on the dashboards by default. Any KPIs that need data from the additional fields will need configuration effort (Needs a technical resource to make the changes- UI will be available from March 2025 onwards through HCM Console). The new KPIs can be configured through the Kibana dashboard integrated within the DSS dashboard.


*   Fields in the any mobile app workflows can be enabled/disabled or made mandatory or optional by updating the code configuration (Needs a technical resource to make the changes- UI will be available from March 2025 onwards through HCM Console).


* Adding and updating validation to any field in the workflow can be done by updating the code configuration (Needs a technical resource to make the changes- UI will be available from March 2025 onwards through HCM Console).
*   Sync:

    * Since the mobile app is offline first, all the data collected while offline is transmitted to the server upon connecting to the internet. Two types of sync approaches are implemented.

    1\. Auto Sync: The application smartly checks if the internet is available and what the bandwidth is. Based on the network strength, it creates a batch of records (Batch size is proportional to the internet bandwidth) and sends the records to the server. Auto-sync can be configured to run at a periodic interval.

    &#x20;      \- Auto sync is used for up sync (data from the mobile is sent to the server).

&#x20;            \- Auto sync is automatically disabled once the battery percentage falls below the configured threshold.

&#x20;            \- Auto sync runs in the background and does not block the user from creating new records.

&#x20;      2\. Manual Sync: The user may choose to initiate a sync manually. Manual sync will only be triggered when the background auto sync is not active.

&#x20;          \- Manual sync is based on user input/user action.

&#x20;          \- Manual sync is used for up-syncing and down-syncing.

&#x20;          \- Downsync is used to download the master data which will be required when the device goes offline. Downsync is triggered on every login.

### Web App

The web app provides the following capabilities:

* Dashboards: Users having access to dashboards can view the dashboards using the web app.
* User management and complaint management (help desk features) are also available via the web application.
* Console: A UI interface for setting up campaigns for system administrators.

## Modules in HCM

#### Module 1: DIGIT and Campaign Setup

* DIGIT HCM supports all types of campaigns. This includes configuring -

&#x20;      \- Single round, household campaigns like a Bednet campaign, IRS campaigns

&#x20;      \- Single round individual campaigns like MDA campaigns for Neglected Tropical Diseases (NTD), etc.

&#x20;       \- Multi-round individual campaign like SMC campaigns.

&#x20;       \- Managing campaigns at facilities such as schools, orphanages, and at transit posts will be available in the 1.6 version

* HCM has been used for ITN, SMC, NTD campaigns, and supports IRS campaigns too with the [1.5 version](https://health.digit.org/hcm-product-suite/health-products/hcm-app/user-manual/single-round-campaigns/registration-and-delivery/registration-and-delivery-irs).

#### Module 2: User and Role Management:

* HCM provides a UI to create and manage users and assign them to campaigns.
* Bulk user creation is possible but via backend configuration (Needs a technical resource, but UI based bulk uploads can be handled through the HCM Console).
* HCM provided RBAC (Role-based access control). There are a couple of default roles configured with the product (Registrar, Distributor, Warehouse Manager, Supervisors at various levels, system administrator).&#x20;

&#x20;      \- New roles can be configured by backend configuration (Needs a technical resource, but UI based configuration will be through the HCM Console in the future).

* HCM uses master data to set up the campaign system. This is possible by backend configuration as well as via the UI as a part of workbench v1.2.

#### Module 3: Microplanning

* HCM v1.5 cannot support the microplanning process (this includes creation, update, and sharing of microplan).

&#x20;      \- Will be available in v1.6 as a web app.

* In its current version, the product can ingest the outputs of the microplan (which includes boundary list, targets, and duration for each boundary.

&#x20;      \- These boundaries and their targets/periods are used to set up the dashboard KPIs.

#### Module 4: HCM Console

HCM Console is designed for individuals familiar with the on-ground execution of health campaigns. These users understand key terms like cycles, deliveries, doses, boundaries, and campaign hierarchies. However, they are not expected to be tech-savvy, and we aim to eliminate the need for them to grasp technical concepts like JSON files, schemas, APIs, MDMS, services, or intricate UI/UX designs. In short, HCM Console prioritises intuitive user experience with extensive guidance throughout the campaign creation and execution process.

Campaign Setup Process:

* HCM Console is an online-first desktop web application, which can be used by personas like programme managers, system administrators, or implementation partners to create, manage, and configure campaigns on HCM.&#x20;
* As of [version 0.3](https://docs.digit.org/console/v0.3), HCM Console supports the creation, management and configuration of three campaign types: SMC Campaign, Bednet Campaign, and IRS Campaign.
* The process of campaign creation comprises the following steps:
  * Selecting Campaign Type - SMC, Bednet, IRS (or any other campaigns enabled in later versions).
  * Assigning campaign names.
  * Boundary selection from preloaded set of boundaries.
  * Selecting campaign start and end dates.
  * Setting the number of cycles and the number of deliveries in each cycle.
  * Setting cycle dates.
  * Set delivery rules/eligibility criteria for each delivery.
  * Set target data at the lowest level of boundary hierarchy for the campaign being created.
  * Create facility data for the campaign being created.
  * Create an app user data for the campaign being created.<br>
* Console also supports saving campaigns in draft state, where the users can choose to upload campaign meta data to create campaigns on Console bit by bit as they collect/receive the relevant data needed for each step of the campaign creation process.

Modify Campaign Set Up:

Once the campaign is created, the user can manage/update data around the ongoing campaigns. The data that can be updated during campaign runtime are:

* Edit campaign and cycle dates.
* Add new boundaries during campaign runtime.
* Edit target data during campaign runtime.
* Edit the facility data during campaign runtime.
* Edit app user data during campaign runtime.

App Configuration Through Console:      &#x20;

* After a campaign is created, the user needs to define the app configuration for a given campaign that is created. The app configurations that can be defined in this version are:

&#x20;      \- Create checklists for all actors in a campaign.

&#x20;      \- Activate/deactivate post intervention flow - Refusal, Referral, and Side Effects, and define reasons for each.

Master Data Management Through Console:\
\
Boundary Data Management: The Console user can set up boundary data through either ShapeFiles or through Excel. The user can choose to import ShapeFiles from GeoPoDe or create their own ShapeFiles and upload them on the Console. Either way, the user will have to follow the schema defined by GeoPoDe for uploading ShapeFiles.Alternatively, the Console user can also set up boundary data through Excel, which will be a basic line by line mapping of all the boundary data available in a given province or a country.\
Actions available to the user: The user can choose to create new data from scratch once and then edit the same data again using Console. The user can also view data from other programmes and download it (as Shapefiles or Excel) if they feel the data is useful.

#### Module 5: Supply Chain

The HCM Supply chain module supports two primary use cases:&#x20;

* Stock Management for warehouses (Used by the warehouse manager)
* HCM can be used to track movement of stock throughout the supply chain to record stock transactions (all the below mentioned transactions) between:&#x20;

&#x20;      \- Two warehouses (Upstream, downstream, or lateral movement).&#x20;

&#x20;      \- Warehouse and field teams, and vice versa.

* Automatically calculate the available stock on hand based on transactions created by the warehouse manager (specific for stock transactions created for a particular product at the warehouse, which are available locally in the mobile device).
* DIGIT HCM mobile application can be used by the warehouse manager to scan the bales (Container for bed nets) and link the scanned 2D codes to the stock transactions if the 2D bar codes are compliant with GS1 standards.

#### Module 6: Training

* The demo/UAT versions of the application can be used to train the campaign staff on the application and dashboard.

#### Module 7: Registration

* Field teams can use the HCM mobile application to register beneficiaries for the campaign.
* In HCM, users must create a household with its location and then add at least one individual to the household (individuals cannot exist without the household).
* HCM by default supports door-to-door registration, but can be configured to support fixed-post registration as well (Needs a technical resource to make the changes, to manage through Console in the future).
* HCM can support QR code/ 2D bar code based registration by linking a unique voucher to the registered beneficiary within the application.
* HCM can support location tracking and visualisation by recording and linking latitude and longitudinal coordinates for each household registered.
* HCM captures the location of the users at frequent intervals, which will help to track the time spent on the field and hence adherence to the SOPs during campaigns.
* In the 1.7 version, HCM allows enumeration of members belonging to communal living facilities such as orphanages, refugee camps, schools, etc.

#### Module 8: Service Delivery & Distribution

* Field teams can use the HCM mobile application to search previously registered beneficiaries (local device offline search) and record service delivery.
* The HCM app by default, supports registration and delivery as two separate flows (both the activities happen at different points in time), but can be configured to support a workflow where registration and delivery are done together (Needs a technical resource to make the changes, to manage through the Console in the future).
* Field teams can scan 2D code printed on the resources to link the resources with the delivery transaction (Provided the code is compliant with GS1 standards).
* HCM can support location tracking and visualisation by recording and linking latitude and longitudinal coordinates for each service delivery transaction.
* In the 1.7 version, DIGIT HCM allows distribution of services to members belonging to communal living facilities such as orphanages, refugee camps, schools, etc.
* With the latest version, the eligibility criteria can be determined through a checklist and based on which the beneficiary can be administered, referred to a health facility or marked as ineligible.

#### Module 9: Monitoring & Evaluation

Monitoring and Evaluation (MnE) is supporting via two major use cases:

* Supervision: HCM allows creation of checklists for supervision/inspections to be filled using the mobile app.

&#x20;      \- Checklists can be created via backend configurations (This can be done through the UI using HCM Console).&#x20;

&#x20;      \- The checklists are basic forms that support the following question-answer type: Short answer, long answer, radio buttons, and multiple choice answers.

&#x20;      \- Geo-tagging of checklists will be available in v1.5 onwards.

&#x20;      \- The current checklists support conditional login and validations such as mandatory/ optional, min and max length, skip logic, etc.

* Dashboards: HCM offers an out-of-the-box dashboard for key metrics and indicators (Metric available for ITN, SMC, IRS campaigns. Metrics for NTD campaigns will be available from January 2025 onwards).
* Dashboard metrics and indicators are created/updated via backend configurations. The dashboard has a Kibana integration that can be used to configure any custom KPIs and charts.
* Mobile dashboards: An online mobile dashboard is available for the team supervisors to track key performance metrics of the field teams. This dashboard is accessible on the app based on the configured role.
* A help text can be provided to the checklists questions with the latest update.
* Custom reports can be generated via backend configurations (Needs a technical resource to make the changes, UI to be provided in the future).

#### Module 10: Attendance

* The Attendance module will allow supervisors to mark attendance for their attendees, which will, in turn, help the system maintain the authenticity of records and provide consistent data for payments to the attendees.&#x20;
* The module enables supervisors to mark attendance for their attendees in an offline-first manner. The attendance can be marked in 2 ways, based on the type of attendance structure chosen by the programme team: Attendance recording once a day, and attendance recording twice a day (morning and evening).
* HCM can be used to track attendance of campaign staff during various events such as training, microplanning, or actual campaigns.&#x20;
* The attendance register is created by a technical resource for each of the events. This will be managed through the HCM Console in the future.

#### Module 11: Payments

* The payments module will allow a supervisor at a ground level to view, edit, and approve the attendance for different events across boundaries.
* Create a muster roll based on the approval of a register.
* The module will allow for viewing the approved registers, collating them together at a boundary and event level, and generating a payment report.
* Allows the user to download the payment report in Excel/PDF formats.
* For more details, click [here](https://health.digit.org/hcm-product-suite/health-products/hcm-app/user-manual/common-functions/payments/guide-to-hcm-payments).

## Frequently Asked Questions (FAQs)

1. Can this application be migrated to DHIS2 for better M\&E control at the national level?

* HCM is interoperable with other health information systems such as DHIS2 and the data can flow between the systems.

2. Can the website be shared to learn more about the system?

* More details on HCM can be found on this website [https://health.digit.org/](https://health.digit.org/)&#x20;

3. Regarding warehouses, what has your strategy been? For example, are nets from a given province concentrated in the provincial warehouse, and then this warehouse distributes them to district warehouses?

* HCM can be set up to manage stocks at all levels of facilities. The flow of inventory from a provincial warehouse to the lowest level warehouse at a community is tracked in the HCM and the data thus captured is displayed in the dashboard which helps in tracking the movement of nets or other commodities across the entire supply chain.

4. Could you explain how the commodity management system functions regarding shipments of nets to facilities and field teams?

* The inventory management module in HCM can be used to track all forms of inventory movements in a warehouse/facility or with a field team. The following inventory movements can be tracked in HCM:

&#x20;      \- Stock received

&#x20;      \- Stock returned

&#x20;      \- Stock dispatched

&#x20;      \- Stock damaged

&#x20;      \- Stock lost

&#x20;      \- Stock reconciliation

* Using all of these functionalities will help the facility managers to adequately track the stock movements and also ensure sufficient stock is maintained throughout the campaign

5. What controls are in place to prevent field teams from over-registering or distributing nets beyond the available stock?

* HCM can be configured to add validations that prevent the user from registering a new beneficiary once the stock is run out. An exemplar for this was done for the SMC campaign in Kebbi state of Nigeria in October 2024.

6. Are all teams holding individual stock or pulling from a central location?

* HCM has the flexibility to configure the stock movement in whichever way the program decides. The teams can receive the stocks from the team leads who in turn receive it from a community level warehouse which in turn receives it from a district level warehouse. At each level, HCM is used to capture the inflow and outflow of stocks.

7. I would like to know, for example, when registrars log into their accounts, besides registering households, can they make changes after form submission? Do they have access to other users' records, or can they manage previously entered data? The same question applies to monitors and warehouse managers.

* The front-line workers can edit the details of a household or an individual such as changing the household head, updating the phone number, name, deleting the household or an individual. However, the programme can decide if this needs to be allowed for the frontine worker or not.
* The warehouse managers cannot edit the stock details once its submitted. This is to prevent stock manipulations. If during the campaign for any reason a stock entry needs to be edited, this can be done in the backend after a written request with approval from the designated authority.

8. Does the platform work where there is no internet?

* Yes. The platform supports both offline and online. Internet access is required only once when you need to log in. Post that you can work in offline mode.

&#x20;9\. Is the number of daily household registrations limited to 40?

* No. The daily target can be configured to any value based on the requirements of the program. The standard value set in HCM is 40 for ITN, 10 for IRS, and 65 for SMC. These can be changed to suit the conditions of the campaign. However this value will be constant for all the front-line workers irrespective of the boundary they are operating in.

10. Are the QR codes printed? Also, what value is assigned to each QR code: one-to-one or does it depend on the household size? If it’s by household size, how is the reconciliation of nets vs. QR codes done?

* The QR codes can be printed and can be used as a unique ID against which all future service deliveries against that household or individual can be done. The QR code encapsulates all the information regarding the household and individual details.&#x20;
* For distributing bed nets against a QR code voucher, the following process is done:

&#x20;      \- The QR code captures the number of members in a household and the number of nets to be provided is computed based on the number of members and the maximum limit. This information also resides in the QR code. During distribution, the QR code is scanned to know how many nets are to be delivered against that.

11. Will there be a process to integrate this data into DHIS2?

* HCM is interoperable with other health information systems such as DHIS2 and the data can flow to and fro between the systems.

12. HCM is interoperable with other health information systems such as DHIS2 and the data can flow to and fro between the systems.

* You can do a reconciliation of the nets or any commodities through the inventory management module in HCM. The reconciliation flow helps to compare the stock counted by the warehouse manager and the system-calculated value of the stock in hand

13. How is the tracking of nets done on the platform?

* The nets or any commodities can be tracked at 2 levels:

&#x20;      \- The scan functionality in the inventory management module can be used to scan a barcode on a bednet bale or any other GS1-compliant goods. This helps to track the movement of the commodity through the supply chain.

&#x20;      \- The scan functionality in the registration and delivery module helps to scan the QR code on a bednet or other commodity. This along with the coordinates captured at the household helps to track the last-mile delivery and ensure the services are delivered to each household/individual.

14. Is the platform configured to limit the maximum number of nets to be distributed?

* The number of nets to be delivered or similar logic for other commodities can be configured as per the requirements of the program. This can be set with a maximum limit and also based on the number of members in a household. For eg: for Mozambique, the protocol was 1 net for 2 individuals, and the maximum number of nets to be delivered per household was limited to 3.&#x20;

15. Is there one team lead for every five registrars or five teams?

* The number of team teams per team lead is decided by the programme and the HCM application can be configured to accommodate this.

16. Is there any contingency plan for phones in case the battery dies or if there is a problem with the phones?

* The data collected in HCM is not lost if the battery dies or there is a problem with the phones, if there is continuous internet access, then the data is automatically synced to the server and there is no data loss.&#x20;
* If the internet is off and there is pending data to be synced in the devices, then the data can be synced whenever the device is recharged.&#x20;
* If the phone is lost/damaged, the internet is off and there is pending data to be synced, then there is potential for data loss.

17. What are the different types of roles available in the HCM payments module?

* Two different types of roles have been made available in the HCM payments module version:

&#x20;      a. Proximity Supervisors: They are responsible for making changes in the attendance registers as well as approving them.

&#x20;     b. Payment Approvers: They are responsible for generating the bills and are authorised to download them in Excel/PDF formats for further processing.

18. What is the workflow of the payments module in the HCM platform?

* In the HCM platform, the payments module is coupled with the attendance module. The typical workflow diagram is provided in section 8.

19. How to mark attendance in the HCM platform?

* There is a dedicated attendance module available in the HCM platform to allow field supervisors to mark the attendance of their team members.

20. What is an attendance register in the HCM platform?

* An attendance register is a record-keeping tool that is used to track the count of present or absent campaign workers, along with their activities such as training, registration/distribution, etc.

21. How can a proximity supervisor edit an attendance register?

* User Navigation: Login > Home Page > Attendance Registers > Select Project Name > Select Boundary > Click on Attendance Register in ‘Pending for Approval’ state > View Attendance > Action: Edit Attendance > Warning Message: Proceed > Edit Attendance > Submit > Success Message.\
  (Note: You can edit the attendance as many times as required till it is approved).&#x20;

22. How can a proximity supervisor approve an attendance register?

* User Navigation: Login > Home Page > Attendance Registers > Select Project Name > Select Boundary > Click on Attendance Register in ‘Pending for Approval’ state > View Attendance > Action: Approve > Add Comments and Approve > Confirmation: Approve > Success Screen.\
  (Note: Once approved, you cannot take any further action on the register).

23. What are approved and unapproved registers?

* Approved registers are those that are marked as approved by the proximity supervisors, and they cannot take any further action on these registers. Unapproved registers are the ones that are submitted by the field supervisors to be approved by the proximity supervisor, and their attendance details can be updated by the proximity supervisor before approval.

24. How can I select a different type of attendance register?

* The first step as a proximity supervisor is to select the type of attendance register from the drop-down after logging in to the payments module. There will be multiple types of registers such as Master Training register, Registration team training, Campaign, etc.

25. As a proximity supervisor, I have selected one of the districts as a boundary. Which attendance registers can I manage?

* You can manage only those registers assigned at the selected district or boundary levels below the district.

26. As a payments supervisor, I have selected the country name. Which muster rolls can I generate the payment report for?

* You can generate the payment report for all the muster rolls that are assigned at a county level.

27. As a payments supervisor, I have selected a province name. Which muster rolls can I generate the payment report for?

* You can generate the payment report for all the muster rolls that are assigned at a province level.

28. As a payments supervisor, I have selected a district name. Which muster rolls can I generate the payment report for?

* You can generate the payment report for all the muster rolls that are assigned at a district level or below the district level.

29. What is a muster roll in the HCM payments module?

* A muster roll is a simple document used to keep track of workers and their activities. It records who showed up for work, the hours they worked, and sometimes their pay. It helps employers know who was present and how much work was done. In campaigns, a muster roll can track attendance and ensure workers are paid correctly for their efforts.

30. What is an event?

* In the context of attendance for a campaign, an event refers to a specific activity or session where workers or participants are expected to be present. This could include training sessions, daily fieldwork (registration/distribution), or any other scheduled task as part of the campaign.

31. When should I approve an attendance register?

* You must wait for the event to be completed to review and approve the attendance register.

32. Is it advisable to approve a register before an event is completed? What happens if I edit attendance during an ongoing event?

* Always approve the attendance register only after the event has fully concluded to ensure data accuracy. Editing attendance during an ongoing event will overwrite the current records, and the system will consider the edited data as final. Additionally, if the attendance register has been edited and approved, attendance markers attempting to record attendance will encounter errors, as there is no downward data flow from the proximity supervisor to the attendance marker.

33. Which formats can I download the payment report in?

* The reports are available for download in Excel and PDF formats.

34. How can I view and download the bills I generated?

* Navigation: Login > Home Page > My Bills > Actions (Download in Excel/PDF).

35. Can I create bills again for already generated muster rolls?

* No, you cannot regenerate bills. However, you can view the generated bills as well as download them as many times as needed.

36. How long will it take to generate a bill?

* The bill generation can take up to 2-3 minutes depending on the number of registers collated.

37. How can I aggregate muster rolls into a single bill? Is aggregation mandatory? At what levels can aggregation occur?

* Aggregation of muster rolls can be done at different boundary levels, as described below:

&#x20;     \- District Level: Muster rolls from all events created at the district or subordinate levels are aggregated for the selected event type.\
&#x20;      \- Example: Aggregating muster rolls for all registration events in the district of Nampula, including those at locality levels within Nampula.

&#x20;      \- Province/State Level: Muster rolls from events across the entire province/state are combined.\
&#x20;      \- Example: Aggregating all muster rolls for distribution events across the province of Cabo Delgado.

&#x20;      \- National Level: Muster rolls from events nationwide are collated.\
&#x20;       \- Example: Aggregating muster rolls for all Master trainer training conducted at the national capital in Mozambique.

* Aggregation is separated at various levels to ensure there are no duplications of bills generated for the same registers.

38. What should I do if bill generation fails?

* Wait for some time and try generating the bill again.
* Check that all attendance registers have been approved.
* If the issue persists, contact the system administrator for assistance.

39. Can I edit the Excel sheet of the payment report?

* Payment report sheets are protected and cannot be directly edited. If edits are necessary, duplicate the sheet and make the required changes. Ensure that any modifications are made only with the approval of the respective supervisory authority.

40. How can I change the payment rates for specific roles?

* If certain roles require different payment rates, you need to define those roles separately and assign individuals accordingly. If people in the same role working across different boundaries need different rates, create distinct roles for each boundary. Ensure any changes are made before generating bills.

41. Can I assign different payment rates to the same role for different boundaries?

* No, the system currently supports assigning rates based on roles, which must remain consistent across all boundaries.

42. How can I generate an intermediate payment report before the event is completed?

* The current version of the module does not support generating intermediate payment reports during an ongoing event.
