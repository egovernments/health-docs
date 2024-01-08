# Architect Sign-off

## Project

HCM

### Release version: 1.0

### Date: March 23, 2023

## Modules Released

* Individual Registry
* Household Registry
* Facility Registry
* Product Registry
* Project Service
* Stock and Inventory Management
* Supervision
* HCM mobile app

&#x20;     \- Registration and service delivery flows

&#x20;     \- Inventory management

&#x20;     \- Supervision flow

&#x20;     \- Sync data

&#x20;     \- Login and projects details flow

### All known issues

* [HLM-2235](https://digit-discuss.atlassian.net/browse/HLM-2235) - During sync at the backend, the address update and individual ID updates are failing.
* [HLM-2094](https://digit-discuss.atlassian.net/browse/HLM-2094) - Pop-ups for sync to happen do not appear when a project is selected during the login process on the mobile app.
* [HLM-2236](https://digit-discuss.atlassian.net/browse/HLM-2236) - While the boundary data is integrated and working fine, the locality picker issue is critical from a dashboard standpoint.
* [HLM-2268](https://digit-discuss.atlassian.net/browse/HLM-2268) - Integration issue-lower boundary levels are showing NULL, even if the boundary is selected from the dropdown (MobileApp).
* [HLM-2093](https://digit-discuss.atlassian.net/browse/HLM-2093) - The help icon is not active and does not work.
* [HLM-2267](https://digit-discuss.atlassian.net/browse/HLM-2267) - MobileApp: Even the quality is selected as 0, and the delivery comment selected as “Unsuccessful delivery”", the task is marked ‘Delivered’.

## Automation test Report

* [Health UAT API Execution Report](health-uat-api-execution-report.md)

### Performance test Report

* Click [here](performance-report.md) for more details.

### GO/No-Go:&#x20;

Go

### Comments

The modules are released with very few bugs. Performance testing was also performed on the bulk create APIs. Performance tests are not done on bulk update and delete APIs as they are designed the same as create APIs, and they are less used. The HCM v1.0 is released as per the architecture design.
