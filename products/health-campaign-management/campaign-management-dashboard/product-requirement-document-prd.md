# Product Requirement Document (PRD)

## Table of Contents

* Background&#x20;
* Design

## Background&#x20;

This document describes the need and scope of a dashboard for executing digital health campaigns, explaining the product’s features, specifications, purpose, and functionalities. It also provides a descriptive view of the dashboard portal along with the specification of each element, and the analytics data involved in it.

## Design

### Card Layout: Landing Page

<figure><img src="../../../.gitbook/assets/Screenshot 2023-04-28 at 11.01.27 AM.png" alt=""><figcaption></figcaption></figure>

#### Description

When the country-level/province-level/district-level/administrative- level of the user login to the HCM admin account as assigned, they can navigate to the following sections:

1. Dashboard
2. User management
3. Complaints

We will also discuss and focus on the ‘dashboard’ service that has been provided to all the admin-level users as per their roles and hierarchy in the system

#### Users

<figure><img src="../../../.gitbook/assets/Screenshot 2023-04-28 at 11.04.37 AM.png" alt=""><figcaption></figcaption></figure>

#### Navigation

When the user logins to the admin page, he/she will be able to see a dashboard card, which will list all the campaigns that are currently running and that they have been assigned to.

| User type                   | Role description                                                                                                                                                                            | Navigation                                                                                                 | Description                                                                                                                                                                                                                                                                                    |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Country                     | The country-level user is the super admin who can view the performance and manage the campaign running.                                                                                     | Login < Dashboard < Select the Campaign < View National Level dashboard data                               | The country-level admin user will be able to see the national-level dashboard, which will display the data of all the campaigns running countrywide with respect to all the provinces and districts. They can drill down the dashboard to view the details of the campaigns in each province.  |
| Province                    | The province-level admin user can view the performance of the ongoing campaign for their province.                                                                                          | Login < Dashboard < Select the Campaign < View Campaign dashboard data                                     | The province-level admin user views the campaign dashboard, which has the data aggregated across all the districts where the campaign is going on.                                                                                                                                             |
| District Officer            | There can be various districts under a province. Therefore, a district-level officer has the responsibility of managing the campaign running for their allotted district.                   | Login < Dashboard < Select the Campaign < View Campaign dashboard data for the allotted district           | The district-level admin officer views the campaign dashboard. This campaign-level dashboard has the data of the specific district that they have been allotted.                                                                                                                               |
| Supervisor                  | Role-based admins are the users who manage the campaigns running in a specific administrative block to which they have been assigned to.                                                    | Do not have access to the dashboard, They only use the mobile application that has been provided to them.  | As the supervisor warehouse manager does not have dashboard access, they only use the mobile application that has been provided to them where the application has the option to view the report of all the FLW's working under them and monitor their performance.                             |
| <p>Locality</p><p>(FLW)</p> | Field-level workers are the ground-level workers who distribute the campaign inventory to the citizens, thereby fulfilling the campaign's requirements and making the campaign successful.  | Do not have access to the dashboard. They only used the mobile application that has been provided to them. | The field-level workers have a registration and delivery mobile application that have been provided to them, where in the ‘report’ section they can view the analytics of their performance only.                                                                                              |

#### Filters

| Indicator/ visualisation | Drill-down                                                                                                                                                              | Description                                                                                                                                                                                                                           | Actions a user can take                                                                                                                                                                                                                      |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Homepage                 | <p>After logging in, the admin lands on the home screen where he/she can view the cards for:</p><ul><li>Dashboard</li><li>User management </li><li>Complaints</li></ul> | In the ‘Dashboard’ card, the user can view the list of all the different campaigns that are running with respect to the users’ account. They can also access the about, FAQ, and calculation pages related to the dashboard from here | <ul><li>Can view the HCM landing page.</li><li>View the dashboard card with the list of campaigns in which the user is involved.</li><li>Click on the “Campaign Name” to view the specific campaign-related data in the dashboard.</li></ul> |



#### &#x20;

\


\
