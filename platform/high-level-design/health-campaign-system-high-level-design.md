# Health Campaign System High Level Design

Health Campaign - High Level Design

The high level design is divided into:

1. Master Data
2. Registries / Entities
3. Reusable DIGIT Services
4. Form engine support
5. Multi tenancy
6. Android offline first app
7. Web app - Campaign planning + dashboard
8. External integration - DHIS2

\


Base Health Campaign on DIGIT Core 2.8.

## Master Data

Master data categorized on the complexity required to maintain them from the technical perspective.&#x20;



1. Simple Masters
   1. Roles
   2. Additional Field schemas for different entities
   3. Project Task configurations
   4. Project Type
   5. Role-Actions
   6. Actions
2. Hierarchical Masters
   1. Administrative Boundary and Hierarchy
3. Inter linking Masters
   1. Field app config
   2. Service Registry

\


## Services/Registries

### Individual Registry

* New service
* As users are registered to campaigns, populate the individual registry with basic information about them.
* This registry is the first step towards the long term plans in DIGIT to move non users of the system away from the User service. However, due to the current dependency on User service for authN and authZ among other things, this registry will be a wrapper over the User service.

### Household Registry

* New service
* Collection of Individuals living together (potentially receiving shared campaign intervention)

### Facility Registry

* New service
* Needed to model storage Warehouses through which stock moves.

\


### Product Registry

* New service
* Needed to model the resources that are distributed as part of projects both as part of stock movement and actual distribution to beneficiaries.

\


### Project Service

* New service
* Models how services and benefits are typically distributed to citizens by governments
* Contains multiple endpoints within the service to map other entities such as beneficiaries, staff, facilities, resources to the projects.

\


### Stock Service

* New service
* Track inflow and outflow of stock resources

\


## Reusable DIGIT Services

Many of the DIGIT-Core services can be reused without any changes. Some of them could be extended and enhanced to support the required features.&#x20;

### DIGIT Services reused as-is

* digit-mdms-service
* Digit-location / boundary service
* digit-access-control
* Zuul API Gateway
* digit-idgen&#x20;
* digit-persister
* digit-indexer
* digit-localization
* DSS
* Signed Audit

### DIGIT Services reused with enhancements&#x20;

No existing services being enhanced.

\
\


## Workflow

The Health Campaign system does not make heavy use of workflows. Most flows in v1 are single actor and end after a single step (i.e. submitting collected data).

\


## High Level Design Diagram

![](https://lh6.googleusercontent.com/Gnv9XNSQA1UoCQ59jh2CaPAulwd6q0eXClhR3YsLr211Tn4mYJ1PvoUlNi\_d86GgWGj9SNcRgBqM-aU5UzCfcSXaGD289IxKR3oZtKq2gpx-dThnOos3r\_ngIof9cHXYPO51IWxUpRgZ-R3M62Of3gDrT\_0gph0XxPfqLANCE\_k\_y7dpfVj7B1HJ7Zd1JA)

\
**ER Diagram**
--------------

![](https://lh4.googleusercontent.com/Ac3FtywEjTuUL35VLbvbOAIrdq1J7PfwOj4-QWvjMs78kdPdTMk791UqHUahQIyR3dZH40YPlMAKvIptBW835ACKWPFfJ4iFQX8DVj\_k6R72MyzlHWF7PNpmTC8PVLbPKRtiLp4OhhMBeeknsGZesjtbFAfM8Ueb2AHR1smw6dpoa1T37UZjOeIeBpc-Tw)

\


## Form Engine support

Form engine support was pushing out timelines and has been dropped from v1 scope.

## Multi tenancy

The proposal is to have a single installation to support multiple countries and multiple health campaigns within these countries. Different campaigns will need to share registries.

Leveraging multi tenancy support in DIGIT for this.

\


## Android App

### Offline First

Android app is proposed to be modeled on mGramSeva app and will be built in Flutter.

This app will be used in areas with limited or no internet connectivity and hence will need to work while offline. Users will sync the data collected offline when they are in an area with network connectivity.

SQLite will be used to model structured data and ISAR will be used for unstructured data.

### Form Renderer

Out of scope for v1.

### Offline Dashboards

The field workers will need to see dashboards based on the data stored in the offline database. Library - TBD&#x20;

## Web App

### Campaign Planning App

Out of scope for v1.

### Dashboards App

The app will have some custom screens to capture information around the campaign plan.

DSS dashboards are planned to be leveraged for reporting dashboards.&#x20;

## External Integration

### DHIS2

This will be added to implementation scope.

