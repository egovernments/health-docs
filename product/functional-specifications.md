# Functional Specifications

## Campaign Setup

| Name of the field                                    | Description                                                                                      | Mandatory | Input   | Data type |
| ---------------------------------------------------- | ------------------------------------------------------------------------------------------------ | --------- | ------- | --------- |
| Campaign ID                                          | Campaign identifier                                                                              | R         | User    | String    |
| Campaign type                                        | Type of campaign- LLIN, vaccination                                                              | R         | User    | String    |
| Beneficiary type                                     | Household, individual, structure                                                                 | R         | User    | String    |
| Eligibility criteria                                 | <p>Universal, </p><p>age-based</p>                                                               | R         | User    | String    |
| Delivery mode                                        | Is registration and delivery combined as per campaign protocol or different: Together/separately | R         | User    | Dropdown  |
| Start date                                           | When does the campaign start: Set up by the national programme manager                           | R         | User    | Date      |
| End date                                             | When does the campaign end: Set up by the national programme manager                             | R         | User    | Date      |
| Delivery strategy: Fixed/mobile (door-to-door)       | The way in which the campaign staff will deliver as per the campaign protocol                    | R         | User    | Dropdown  |
| Delivery procedure                                   | Instructions on how to deliver the resources                                                     | R         | User    | String    |
| Number of Rounds                                     | 2 rounds                                                                                         | R         | User    | Numeric   |
| Duration between the rounds                          | 30 days                                                                                          | R         | User    | String    |
| Recurrence/ repeatable                               | Repeat for 5 years                                                                               |           |         |           |
| Recurrence or repeat frequency (if yes to the above) | Annual                                                                                           |           | User    | String    |
| Disease area                                         | Malaria                                                                                          | R         | User    | Dropdown  |
| Desired target                                       |                                                                                                  | R         | User    |           |
| Team target (absolute number)                        |                                                                                                  | R         | User    | Numeric   |
| Coverage target (in percentage)                      |                                                                                                  | R         | User    | Numeric   |
| Total population targeted (number)                   |                                                                                                  | R         | User    | Numeric   |
| Campaign state                                       | Created, In progress, completed, abandoned                                                       | R         | User    | Dropdown  |
|                                                      |                                                                                                  |           |         |           |
| Resource setup                                       |                                                                                                  |           |         |           |
| Resource details \[]                                 |                                                                                                  | O         |         |           |
| Type of resources delivered                          | Net, vaccine, spray, medicine                                                                    | R         | User    | String    |
| Name of the resource                                 | Bednet x                                                                                         | R         | User    | String    |
| Quantity procured                                    | 1000000                                                                                          | R         | User    | String    |
| Unit of measurement                                  | Bales, cartons, litres, kg                                                                       | R         | User    | Dropdown  |
|                                                      |                                                                                                  |           |         |           |
| Boundary setup                                       |                                                                                                  |           |         |           |
| Boundary: Start date                                 | The date on which the campaign is supposed start in the area selected above                      | R         | User    | String    |
| Boundary: End date                                   | The date on which the campaign is supposed to end in the area selected above                     | R         | User    | Date      |
| Desired target for boundary                          | Targets estimated for the area that the programme wants to achieve                               | R         | User    |           |
| Coverage target (in percentage)                      | Targeted beneficiaries as per the micro-plan against the total population                        | R         | User    | Numeric   |
| Total population targeted                            | Targeted beneficiaries as per the micro-plan                                                     | R         | User    | Numeric   |
| Actual target achieved for the boundary              | Actual target achieved for the area (fetch from dashboard after the campaign is over             | R         | System  |           |
| Coverage target (in percentage)                      | Beneficiaries covered as per the service delivery data against the targeted beneficiaries        | R         | System  | Numeric   |
| Total population targeted (number)                   | Beneficiaries covered as per service the delivery data                                           | R         | System  | Numeric   |

## Registration

| Name of the field                      | Description                                                     | Mandatory | Input        | Data type | Validation                                                            | Comments                     |
| -------------------------------------- | --------------------------------------------------------------- | --------- | ------------ | --------- | --------------------------------------------------------------------- | ---------------------------- |
| Define beneficiary type                |                                                                 |           |              |           |                                                                       |                              |
| Type of registration                   | Household, individual                                           | R         | User         | Dropdown  |                                                                       |                              |
| Number of individuals in the household | Number of individuals staying in the house                      | R         | User         | Numeric   | Applicable only when the type of registration is household            |                              |
|                                        |                                                                 |           |              |           |                                                                       |                              |
| Beneficiary address and location       |                                                                 |           |              |           |                                                                       |                              |
| Address of the household               |                                                                 |           |              |           |                                                                       |                              |
| Address                                | Enter the address of the household                              | R         | User         | String    |                                                                       |                              |
| Location                               |                                                                 | O         |              |           |                                                                       |                              |
| Latitude                               |                                                                 | O         | System       | Numeric   |                                                                       |                              |
| Longitude                              |                                                                 | O         | System       | Numeric   |                                                                       |                              |
| Accuracy                               | Accuracy of the GPS coordinates in meters                       | O         | System       | Numeric   |                                                                       |                              |
| Administrative unit                    | Name of the geographic area where the household is located      | R         | User/ system | Dropdown  |                                                                       |                              |
|                                        |                                                                 |           |              |           |                                                                       |                              |
| Beneficiary Details (PII)              |                                                                 |           |              |           |                                                                       |                              |
| Name of the  individual: First name    | Name of the individual eligible to receive the service          | R         | User         | String    |                                                                       |                              |
| Name of the individual: Middle name    |                                                                 |           |              |           |                                                                       |                              |
| Name of the individual: Last name      |                                                                 |           |              |           |                                                                       |                              |
| Head of the household                  |                                                                 | R         | User         | Checkbox  |                                                                       |                              |
| Date of birth                          | Date of birth of the registered individual in YYYY/MM/DD format | O         | User         | Date      |                                                                       | What date format is followed |
| Gender                                 | Male, Female, Other                                             | O         | User         | Dropdown  |                                                                       |                              |
| Type of ID                             | System generated, national ID                                   | R         | User         | Dropdown  | If a user does not select any ID, the system must assign an unique ID |                              |
| ID number                              |                                                                 | R         | User/ system | String    |                                                                       |                              |
| Custom fields                          | Any other campaign-specific data fields collected               | O         | User         | String    |                                                                       |                              |
| Individual's weight                    |                                                                 | O         |              |           |                                                                       |                              |
| Individual's height                    |                                                                 | O         |              |           |                                                                       |                              |

## Inventory Flow

| Name of the field                                | Description                                   | Mandatory | Input  | Data type | Validation | Comments |
| ------------------------------------------------ | --------------------------------------------- | --------- | ------ | --------- | ---------- | -------- |
| Warehouse details and location                   |                                               |           |        |           |            |          |
| Administrative unit                              | Administrative jurisdiction of the warehouse  | R         | User   |           | Dropdown   |          |
| Warehouse ID                                     | Identifier for the warehouse                  | R         | User   |           | Dropdown   |          |
| Warehouse location                               |                                               |           |        |           |            |          |
| Latitude                                         |                                               | O         | System |           | Numeric    |          |
| Longitude                                        |                                               | O         | System |           | Numeric    |          |
| Accuracy                                         | Accuracy of the GPS coordinates in meters     | O         | System |           | Numeric    |          |
| Received from                                    | Enter details of the sending entity           | R         | User   |           | String     |          |
| Dispatched to                                    | Enter details of the receiving entity         | R         | User   |           | String     |          |
|                                                  |                                               |           |        |           |            |          |
| Resource details                                 |                                               |           |        |           |            |          |
| Type of resource                                 | Bed nets                                      | R         | User   | Dropdown  |            |          |
| Name of the resource                             | LLIN                                          | R         | User   | String    |            |          |
| Quantity received                                | 100                                           | R         | User   | Numeric   |            |          |
| Unit of measurement                              | Nets, vials, litres                           | R         | User   | String    |            |          |
| Transaction type                                 | Received, dispatched                          | R         | User   | Dropdown  |            |          |
| Reason for transaction                           | Received, returned, dispatched                | R         | User   | Dropdown  |            |          |
| Date of transaction                              |                                               | R         | User   | Date      |            |          |
|                                                  |                                               |           |        |           |            |          |
| Audit details                                    |                                               |           |        |           |            |          |
| Transaction logged by                            | Name or ID of the individual filling the form | R         | System | String    |            |          |
| Transaction logged on                            | Timestamp when the form was filled            | R         | System | Date      |            |          |
| Custom fields                                    |                                               |           |        |           |            |          |
| Type of vehicle used for transport               |                                               | O         | User   | String    |            |          |
| Vehicle registration number                      |                                               | O         | User   | String    |            |          |
|                                                  |                                               |           |        |           |            |          |
| Resource reconciliation                          |                                               |           |        |           |            |          |
| Reconciliation                                   |                                               |           |        |           |            |          |
| Warehouse ID                                     |                                               | R         | System | String    |            |          |
| Date of reconciliation                           |                                               | R         | System | Date      |            |          |
| Resources reconciled                             |                                               |           |        |           |            |          |
| Resource ID                                      |                                               | R         | System | String    |            |          |
| Resource type                                    |                                               | R         | User   | Dropdown  |            |          |
| Resource name                                    |                                               | R         | User   | String    |            |          |
| Calculated count                                 |                                               | R         | System | Numeric   |            |          |
| Physical count                                   |                                               | R         | User   | Numeric   |            |          |
| Difference between calculated and physical count |                                               | R         | System | Numeric   |            |          |
| Comment                                          |                                               | O         | User   | String    |            |          |

## Service Delivery

| Field name               | Description                                                            | Mandatory | Input   | Data type | Validation                                     | Comments                                                                                                                                           |
| ------------------------ | ---------------------------------------------------------------------- | --------- | ------- | --------- | ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Registration ID          | Details of the registered beneficiary to whom a service is delivered   | R         | System  | String    |                                                | Will be retrieved from list of beneficiaries registered before delivering a service, or will create a new beneficiary if not registered previously |
| Name of the individual   | Name of the individual receiving the service                           | R         | System  | String    |                                                |                                                                                                                                                    |
| Type of resource         | Type of resource delivered as a part of the campaign: Bed net, vaccine | R         | User    | Dropdown  |                                                |                                                                                                                                                    |
| Quantity to be delivered | Quantity estimated to be delivered as per the delivery instructions    | R         | System  | Numeric   |                                                |                                                                                                                                                    |
| Quantity delivered       | Actual quantity of the resource delivered                              | R         | User    | Numeric   |                                                |                                                                                                                                                    |
| Reason if not delivered  | Justification if the resource was not delivered                        | O         | User    | Dropdown  |                                                |                                                                                                                                                    |
| Comment                  |                                                                        | O         | User    | String    | Applicable only when the delivery was not done |                                                                                                                                                    |
| Delivery details         |                                                                        |           |         |           |                                                |                                                                                                                                                    |
| Date of delivery         | Date of service delivery                                               | R         | System  | Date      |                                                |                                                                                                                                                    |
| Delivered by             | Details of the campaign staff delivering resources                     | R         | System  | String    |                                                |                                                                                                                                                    |
| Audit details            |                                                                        |           |         |           |                                                |                                                                                                                                                    |
| Transaction logged by    |                                                                        | R         | System  | String    |                                                |                                                                                                                                                    |
| Transaction log time     |                                                                        | R         | System  | Date      |                                                |                                                                                                                                                    |



[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._