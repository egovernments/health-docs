# Inventory Management

## Table of Contents

Background

Target Audience

Objectives (of this release)

Assumptions and Validations&#x20;

Process flow

## Background

This document describes the need and scope of a digital platform for health campaigns, explaining the product’s features, specifications, purpose, and functionality.

The module focuses on the design and features of the user interface of HCM for beneficiary registration and service delivery. It provides a detailed description of the elements and the process flow of the application along with a wireframe model for easier comprehension. The module aims to reduce the risks of data redundancy., besides providing better service delivery tracking and visibility into the services provided for maximum area coverage, and in the quickest time possible.

## Target Audience

This document is intended for the engineering and platform (tech teams), product management, and implementation teams to agree on requirements for the Health Campaign Management (HCM) Platform.

## Objectives (of this release)

1\. To enable actors with a digital system to manage and implement health campaign activities.&#x20;

a. Facilitate FLWs, supervisors, district officers, and other actors to collect and analyse data accurately, along with monitoring the tasks from registration to service delivery. Regular progress checks can be performed at any time and a comparative analysis can be derived at the district levels for different teams.&#x20;

b. Facilitate better diagnostics with improved access to healthcare interventions for the general public.

2\. To increase the adoption of the HCM platform for multiple health campaigns by providing flexibility in the UI and UX, as well as product specifications.

a. Emphasis on adopting digital systems by collaborating with several healthcare initiatives.

b. Provide scope for future changes and improvements in the application.

## Assumptions and Validations

| Assumption                      | Validation                                                                                                                                                                                                                                                                                                                                |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Customer persona                |                                                                                                                                                                                                                                                                                                                                           |
| Device and services             |                                                                                                                                                                                                                                                                                                                                           |
| Contact numbers                 |                                                                                                                                                                                                                                                                                                                                           |
| Product details                 | Multiple product details cannot be captured within the same form in any transaction. A user needs to fill separate forms for each product.                                                                                                                                                                                                |
| Dropdown fields                 | <p>If the dropdown consists of only one value, then the field must be auto-populated.<br>In the warehouse details screen, there is a search field that must contain only those values which are assigned to the project.</p><p>In the received stock details screen, the list must contain all the warehouses along with ‘N/A’ value.</p> |
| Additional/Non-mandatory fields | All the additional and non-mandatory fields across all the flows must be taken care of during implementation.                                                                                                                                                                                                                             |

## Process flow

<figure><img src="../../.gitbook/assets/Screenshot 2023-03-16 at 3.05.37 PM.png" alt=""><figcaption></figcaption></figure>

Specifications

| Field                                   | Data type    | Data validation         | Required (Y/N) | Comments                                                                                                                                                                                                  |
| --------------------------------------- | ------------ | ----------------------- | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Latitude/ Longitude                     | Numeric      | NA                      | Y              | The geographical coordinates of the house/household. It is captured by the system at the backend.                                                                                                         |
| Warehouse name/ID                       | Search text  | NA                      | Y              | The warehouse name/ID where the transaction is taking place. The search field must contain the values assigned to the project.                                                                            |
| Date of receipt                         | Date         | Cannot be in the future | Y              | The date when a receipt was created. It is system-generated and non-editable.                                                                                                                             |
| Administrative unit                     | String       | NA                      | Y              | The area boundary assigned to a specific user. It is captured from the location picker and is non-editable.                                                                                               |
| Select product                          | Dropdown     | NA                      | Y              | This describes the type of resources needed.                                                                                                                                                              |
| Received from                           | Search text  | NA                      | Y              | The warehouse name from where the stock is received. The list must consist of all the warehouses, irrespective of the boundary and the distribution team value on top. This applies to every transaction. |
| Waybill number                          | Numeric      | NA                      | N              | The unique packing slip number.                                                                                                                                                                           |
| Number of nets indicated on the waybill | Numeric      | NA                      | N              | The total number of bed net counts indicated on the waybill.                                                                                                                                              |
| Quantity received                       | Numeric      | NA                      | Y              | The total number of bed nets received.                                                                                                                                                                    |
| Type of transport                       | Dropdown     | NA                      | N              | The type of transport which is used for delivery.                                                                                                                                                         |
| Comments                                | String       | NA                      | N              | Additional comments for the transaction.                                                                                                                                                                  |
| Vehicle number                          | String       | NA                      | N              | Vehicle number                                                                                                                                                                                            |
| Date of issue                           | Date         | Cannot be in the future | Y              | The date when the stock is being issued. It is system-generated and non-editable.Search text                                                                                                              |
| Destination                             | Search text  | NA                      | Y              | The warehouse name where the stock is being sent.                                                                                                                                                         |
| Quantity sent                           | Numeric      | NA                      | Y              | The total number of bed nets sent.                                                                                                                                                                        |
| Return date                             | Date         | Cannot be in the future | Y              | The date when the stock is being returned. It is system-generated and non-editable.                                                                                                                       |
| Returned from                           | Search text  | NA                      | Y              | The warehouse from where the stock is being returned.                                                                                                                                                     |
| Quantity returned                       | Numeric      | NA                      | Y              | The date of filing the damage. It is auto-captured by the system.                                                                                                                                         |
| Damage date                             | Date         | Cannot be in the future | Y              | The date of filing the damage. It is auto-captured by the system.                                                                                                                                         |
| Damaged during                          | Dropdown     | NA                      | Y              | Select from the dropdown when the stock was damaged.                                                                                                                                                      |
| Received from                           | Search text  | NA                      | Y              | The warehouse from where the stock was received. If the stock is damaged in the same warehouse (storage), then select ‘NA’.                                                                               |
| Quantity damaged                        | Numeric      | NA                      | Y              | The quantity of stock that has been damaged.                                                                                                                                                              |
| Loss date                               | Date         | Cannot be in the future | Y              | The date of filing the loss. It is auto-captured by the system.                                                                                                                                           |
| Lost during                             | Dropdown     | NA                      | Y              | Select from the dropdown when the stock was lost.                                                                                                                                                         |
| Received from                           | Search text  | NA                      | Y              | The warehouse from where the stock was received. If the stock is lost in the same warehouse (storage), then select ‘NA’.                                                                                  |
| Quantity lost                           | Numeric      | NA                      | Y              | The count of stock lost.                                                                                                                                                                                  |
| Warehouse                               | Dropdown     | NA                      | Y              | Select the warehouse for reconciliation.                                                                                                                                                                  |
| Select product                          | Dropdown     | NA                      | Y              | Select the product for reconciliation.                                                                                                                                                                    |
| Manual stock count                      | Numeric      | NA                      | Y              | Manual count of the stock.                                                                                                                                                                                |
| Comments                                | String       | NA                      | N              | If needed, comments can be manually added.                                                                                                                                                                |

