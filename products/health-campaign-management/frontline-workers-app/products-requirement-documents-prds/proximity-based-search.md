# Proximity-Based Search

## Table of Contents

[Background](proximity-based-search.md#background)

[Target Audience](proximity-based-search.md#target-audience)

[Objectives (of this release)](proximity-based-search.md#objectives-of-this-release)

[Assumptions and Validations](proximity-based-search.md#assumptions-and-validations)

[Process flow](proximity-based-search.md#process-flow)

[Specifications](proximity-based-search.md#specifications)

[Design](proximity-based-search.md#design)

## Background

This document describes the need and scope of proximity based search included within V2.0, explaining the module’s features, specifications, purpose, and functionality. It also provides the descriptive view of the application along with the specification of each element.

Proximity-based search is a feature implemented in HCM to enhance user experiences and provide relevant results based on last recorded location. It leverages location data to enable the field team to identify a nearby household.

Proximity-based search is designed to address the need for location-specific information and improve the user’s convenience by presenting results that are geographically relevant.

## Target Audience

This document is intended for the engineering and platform (tech teams), product management, and implementation teams to agree on requirements for the Health Campaign Management (HCM) Platform.

## Objectives (of this release)

1. Improve accessibility:&#x20;

&#x20;      \- By enabling actors to easily find nearby households and deliver bed nets accordingly.

2. Enhance user experience:

&#x20;      \- Proximity-based search offers a seamless and intuitive way to find the nearby households based on the latitude, longitude, saved by the application.

3. Enhance offline functionality:

&#x20;      \- Aims to address scenarios where internet connectivity may be limited or unavailable.

## Assumptions and Validations

<table data-header-hidden><thead><tr><th width="78"></th><th width="180"></th><th></th></tr></thead><tbody><tr><td>Sr. No.</td><td>Theme </td><td>Assumption</td></tr><tr><td>1</td><td>Search households</td><td><p>- The “Search Household” feature provides a comprehensive overview of the registered household in the administrative area, including the number of bed nets delivered.</p><p>- It also displays the list of beneficiaries registered within the application, with the most recent beneficiary registered displaying at the top.</p></td></tr><tr><td>2</td><td>Search near me </td><td><p>- By selecting the “Search Near Me” checkbox , the user can retrieve a list of beneficiaries who are in close proximity to the user’s last recorded latitude/longitude coordinates.</p><p>-The “Search Household” screen should organise the displayed list, starting from the beneficiary near the user’s latitude/longitude location and extending to the remaining beneficiary listed on the landing page.</p><p>- When sorting the list based on proximity, prioritise displaying the households that have “not been visited yet”, followed by the visited households in case two households are at the same distance.</p><p>- On unchecking the “Search Near Me” box, the list should reset to its initial list of beneficiaries.</p></td></tr></tbody></table>

## Process flow

<img src="https://lh5.googleusercontent.com/q4E5z5V2AZ2v0Vbe2gbCzUtisvuOEv5ZXY648pMVGjoxrlO-Xzi_bf51NTvt3nK4WA4cV36uT9LY8jISIWEidhKJBM16X61BKLV2qNwXmLLPSWHfq1a4QhzMFKYtiCa0NGMwssdyLll-rC6-Nlr1dUk" alt="" data-size="original">\


## Specifications

<table data-header-hidden><thead><tr><th></th><th width="119"></th><th width="209"></th><th width="106"></th><th></th></tr></thead><tbody><tr><td>Field</td><td>Data type</td><td>Data validation</td><td>Required (Y/N)</td><td>Comments</td></tr><tr><td>Beneficiary List </td><td>List</td><td>Last registered beneficiary to be displayed first</td><td>Y</td><td>The list of beneficiaries registered within the application.</td></tr><tr><td>Search by proximity</td><td>Checkbox</td><td><ol><li>Display the beneficiary in close proximity with the user’s last recorded Lat/Long coordinates (Close-In-to-Far-Out)</li><li>Display the “not visited” household first in case two households are at the same distance.</li></ol></td><td>Y</td><td>List of beneficiaries near to the user’s last recorded latitude/ longitude coordinates.</td></tr></tbody></table>

## Design

Find the mock-ups below:

### HCM Home Screen

After logging into the application, the user lands on this screen which displays the daily performance (number of households registered). The progress bar must reset daily at 00:00 hours and start from zero registrations. The action buttons related to the beneficiary include:

* Beneficiaries
* View Reports
* Sync Data
* Call Supervisor
* File Complaint

At the bottom, there is a card that shows how many records are unsynced for the user’s convenience to sync data. If all the records are synced, then the card must say “All records are synced”.

The help button is on every screen of the application, and by clicking on it, a user can get a walkthrough of the elements on that screen.

On the top right, the administrative area assigned to the user is displayed which is based on the level of hierarchy.

The hamburger button on the top left corner covers some other actions mentioned further.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 10.21.58 AM.png" alt=""><figcaption></figcaption></figure>

### Search Households

During implementation, there must be an option to configure the default view of the search households screen. There are two views:

1. Show results only after searching (current v1 state).
2. Display results (list of households) based on LIFO (last registered households displayed first).

For #2:

The Search Household screen displays the number of households registered along with the number of bed nets delivered in that administrative area. It also displays a comprehensive list of beneficiaries who have been registered within the system. The list is sorted in descending order, with the most recently registered beneficiary appearing at the top, allowing for easy access to the latest beneficiary information. This feature ensures that users can quickly identify and review the most recent additions to the beneficiary database, enabling efficient tracking and management of beneficiary records.

The “Search Near Me” checkbox will allow users to conveniently view the list of beneficiaries who are in close proximity to the user’s last recorded latitude/longitude coordinates.

The register button is primarily disabled to ensure that the user performs the search action.

The search bar allows the user to search by the household head’s name and the system provides the search results. The minimum string length to show results is 2 characters and the order of the results will be the last record displayed first. The ‘Back’ button on the top will navigate to the home screen.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 10.27.46 AM.png" alt=""><figcaption></figcaption></figure>

### Search Near Me

The "Search Near Me" checkbox enables users to find beneficiaries in close proximity to their latitude/longitude location (search radius must be configurable).

1. When the checkbox is enabled, users can access a list of beneficiaries located near their current GPS coordinates - latitude and longitude coordinates - allowing them to identify nearby households.
2. When sorting the list by proximity, prioritise showing the households that have not been visited yet. If two households are at the same distance, display the visited households afterwards. This ensures efficient organisation and visibility of household visits based on the status.
3. When the "Search Near Me" box is unchecked, the list of beneficiaries should revert back to its original state, displaying the initial list of beneficiaries. This allows users to easily reset the search and view all beneficiaries without proximity filtering.
4. The distance must be displayed dynamically, that is, if the distance is less than 1 km, display it in metres, and for distances above 1 km, display it in kilometres.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-07-18 at 10.39.17 AM.png" alt=""><figcaption></figcaption></figure>

\
\






\


