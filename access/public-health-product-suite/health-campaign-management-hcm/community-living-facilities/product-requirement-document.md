---
description: Scope of Community Living Facilities
---

# Product Requirement Document

## Introduction

In health campaigns, HCM has primarily supported house-to-house delivery, where the distribution was tied to a specific household or individual. For fixed post mode, HCM has done only household-based campaigns where enumeration was done house-to-house and distribution was done at a fixed post. Even in individual-based campaigns, the beneficiaries were usually part of a household with a limited number of members, with the largest households we’ve encountered being up to 30 members.

During the discussions for the polio campaign in Nigeria, there was a need to administer vaccines in fixed locations like schools, community centers, or in transit settings. In these scenarios, delivery agents are mobile, administering vaccines on the go, such as along roadsides or under trees.

There is now a growing demand for addressing similar alternative delivery modes in other health campaigns. For example, in Nigeria's Schistosomiasis campaign, medicines had to be delivered to children residing in Madrassas (residential schools), where they were permanent residents. Other similar use cases could include:

* Nursing homes and long-term care facilities
* Orphanages
* Military camps
* Police camps
* Retirement homes
* Religious community living facilities with permanent residents
* Refugee camps
* Jails
* Schools (Residential and Non-residential)
* Bus stands / railway stations

As these use cases expand, it is essential for HCM to adapt to cater to these modes of delivery as well and also ensure the HCM Console enables the same.

#### Value Proposition

As a campaign manager, I can configure different modes of delivery (fixed locations or transit points) in HCM, so that I can ensure efficient and adaptable health interventions across diverse settings like schools, refugee camps, or transit locations.

As a field worker, I can easily administer vaccines or medicines on the go using HCM, so that I can reach beneficiaries efficiently in non-household environments, such as roadsides, schools, or community centers.

## Goals and Objectives

Primary Goals:

* Enable HCM to cater to all modes of service delivery.
* Enable HCM to cater to Polio campaigns.
* Increase coverage during campaigns by delivering to non-household entities and populations.

Key Metrics:&#x20;

* Number of implementations with non-household-based campaigns
* Percentage of beneficiaries' coverage achieved through non-household-based campaigns.
* The number of Polio campaigns.

## Key Terminologies

1. Fixed Post: This is a collective term for a location where an intervention is delivered or where a campaign worker goes to deliver an intervention. The details of this place are normally available as part of the microplan. For example: For a bednet campaign, the households are enumerated door to door and provided QR code vouchers and later the beneficiaries come to a fixed post to collect the bed nets. This was the mode for the Liberia ITN campaign in 2024.
2. For example: For a bednet campaign, the households are enumerated door to door and provided QR code vouchers, and later the beneficiaries come to a fixed post to collect the bed nets. This was the mode for the Liberia ITN campaign in 2024.

&#x20;     Note: Any mention of a facility is analogous to community living facilities for the current context.

3. Community living facilities: A location with a permanent structure where there is a population residing such as jails/schools/refugee camps. The details of this place are normally available as part of the microplan.  For example: A campaign worker goes to a school to vaccinate the children for an STH campaign.&#x20;
4. House to House/ Door to Door: Mode of campaign delivery where a campaign worker goes from house to house enumerating and delivering interventions.
5. Transit Post: Mode of the campaign where the target population is not estimated prior and the beneficiaries are not enumerated. Only the aggregate count of the beneficiaries is captured along with the coordinates of the location. This can be a bus stop/railway station or even a health facility. The location of the transit post may be known prior or may not be known prior depending on different programs. The key point is only the count is captured and there is no residence of the population at this place.

## Assumptions

* The logic for the delivery of intervention for different categories of community living facilities will be different.
* The modes of delivery for a user may or may change during different days of the campaigns.
* The scope is formulated based on the discussion and validations with NMEP Burundi, Nigeria(Polio), field visit (Kano Nigeria), and Malaria Consortium. The scope discussed in this document is assumed to cover all requirements for any mode of campaign delivery.
* The user assigned to a community living facility will select the cluster/division and downsync the data only for that particular cluster/division respectively to the selected community living facility.&#x20;

## Prioritisation

Feature set:

* Search within Community living facilities
* Filter search results
* Map between FP and D2D
* Remove duplicates
* Campaign in transit posts
* Logic for delivery based on type
* Compliance for transit post
* Show separate coverage cards for D2D and FP

<figure><img src="../../../../.gitbook/assets/Screenshot 2025-04-07 at 1.19.34 PM.png" alt=""><figcaption></figcaption></figure>

## Out of Scope

* Adding new Community living facilities on the field. Any new community living facilities will need to be added in the backend and will need to be down-synced. This will be considered.

User Personas\
\
![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeW3ZSBJa46Q4WUrKGBfFFu_4Ol98xhT3m_Z36qJOt-JJQOl8FPm4FzZCKzS-l1nuifxQK15GDkTu_FDhbu8u7XaolfCePrGMIlEzQ7wz9xwdxMqxYmsjWHoBihGZnRhZyVwBrp0SBQTvOhgHnor1Zgj6ET?key=aenjfHB4Yu2N8XjHnkSTWQ)
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

#### Community Drug Distributors

The CDDs are responsible for household enumeration, beneficiary enumeration within both households and community living facilities, and delivering interventions even without prior enumeration. Users can add beneficiaries to households, administer interventions, record adverse events for SMC and NTDs, and refer beneficiaries as needed for the programmes.

## User Needs and Pain Points

* For a frontline worker who needs to register a large number of individuals for entities that are not a house such as schools etc, it is difficult to find a registered individual as the number of individuals increases within a facility.
* For certain campaigns such as Polio, the delivery of interventions also happens in transit such as at bus stops, railway stations, etc. Enumerating the beneficiaries is not the primary motivation here rather it is to administer doses to the maximum population.&#x20;
* The current household-based delivery UI cannot be modified for Community living facilities-based delivery because it is not designed to search for any Community living facilities, and adapting it would make the entire interface heavy and cluttered.

## Console Capabilities

* Able to identify duplicates based on a pre-defined algorithm.
* Can merge/map the duplicates created at a household and a facility together.
* Adding new community living facilities.

## Specifications

| Field                                                             | Data Type | Validation                                                                                                                                                                                   | Comments    |
| ----------------------------------------------------------------- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| Search bar                                                        | String    | <ul><li>Allow the user to search by name or beneficiary id</li><li>Display results after 3 characters</li><li>Show results if the user enters full name (First name and last name)</li></ul> | <p><br></p> |
| Landmark                                                          | String    | <ul><li>Allow up to 100(configurable) characters for the landmark description.</li><li>Only alphanumeric characters are allowed.</li></ul><p><br></p>                                        | <p><br></p> |
| Name of Community living facilities head                          | String    | <ul><li>Allow up to 50(configurable) characters.</li><li>Only alphabetic characters and spaces allowed.</li></ul><p><br></p>                                                                 | <p><br></p> |
| Mobile Number                                                     | Numeric   | <ul><li>This field must be configurable - configure the mobile number field to 10 digits</li><li>Only numeric input allowed.</li></ul><p><br></p>                                            | <p><br></p> |
| Total number of beneficiaries in the Community living facilities  | Numeric   | <ul><li>Must be a positive integer.</li><li>Maximum value - <a href="mailto:abhishek.suresh@equidhi.org">Abhishek Suresh</a> to confirm</li></ul><p><br></p>                                 | <p><br></p> |
| Name of the transit post                                          | String    | <p><br></p><p>- Only alphabetic characters and spaces allowed.</p><p><br></p>                                                                                                                | <p><br></p> |
| Batch Number                                                      | String    | <ul><li>Allow up to 20 alphanumeric characters.</li><li>No special characters allowed.</li></ul><p><br><br></p>                                                                              | <p><br></p> |
| Voucher serial number                                             | String    | <ul><li>Allow up to 15 alphanumeric characters.</li><li>No spaces or special characters allowed.</li></ul><p><br></p>                                                                        | <p><br></p> |
| Expiry Date                                                       | Date      | <p><br></p><ul><li>Cannot be a past date.</li></ul><p><br></p>                                                                                                                               | <p><br></p> |

## Functional Requirements

#### Registration (of an individual) at a registered entity (household, hospital, etc.)&#x20;

#### (Door to Door / Community living facilities Mode )

* In this mode, there are 2 possibilities:

&#x20;      1\. Individuals are registered (individual registry) and linked to other entities (like hospitals, or schools) - eg: Individual campaigns such as SMC, NTD

&#x20;      2\. Individuals are not registered and only the count is maintained and linked to an entity (hospital, school), for example, household campaigns such as ITN.

* I as a frontline worker should be able to add individuals to a structure/household and then be able to search for those individuals within an entity.
* Able to navigate through search results through infinite scroll.
* Need to mark the entity as a facility (not needed).

#### Registration (of individuals) without linking to an entity (household, hospital, etc.)&#x20;

#### (Transit Post )

* Individuals are not registered and the count is maintained but not linked to an entity (hospital, school). It is merely recorded with (perhaps) a geolocation.
* Only the count needs to be captured at a location with the option of capturing the details of the location.

Non-functional Requirements

#### Performance:

* The application should consume minimal battery and data, comparable to existing HCM versions.
* Data aggregation and synchronization between field devices and the main server should occur seamlessly, providing near real-time updates of intervention data with stable internet connectivity.
* The app should work offline, capturing required data at regular intervals and synchronizing automatically when the internet is available.

#### Usability:

* The user interface should be intuitive, enabling ease of use for individuals with varying levels of digital literacy.
* Design should avoid dropdowns with fewer than five options and limit open-text fields to reduce user input time.
* Screen layout should avoid vertical scrolling, displaying no more than two data fields per screen.
* Visual aids (e.g., icons or images) should be present on screens to guide users in understanding their tasks.
* Help text under each data input field should explain the purpose of the field.
