# Complaints

## Overview <a href="#overview" id="overview"></a>

The complaints registry allows employees to lodge complaints regarding health campaigns. An employee can track the complaint, upload an image related to it, and reopen the complaint if they are dissatisfied, as well as rate the service. This document details how to set up the complaints registry (pgr-service) and outlines the functionalities it offers.

## Pre-requisites <a href="#pre-requisites" id="pre-requisites"></a>

Before you proceed with the configuration, make sure the following pre-requisites are met:&#x20;

* _Java 8._
* Kafka server is up and running.
* The egov-persister service is running and has the pgr-services persister config path added in it.
* The PSQL server is running, and the database is created to store complaint data.
* _(Optional)_ Indexer config for pgr-services is added in the egov-indexer yaml paths to index the generated data. The index is required for data visualisation in Kibana or DSS.
* _(Optional)_ Report config for pgr-services is added in the Report service config paths. Required if reports are to be provided to the user.
* The following services should be up and running:
  * egov-user
  * egov-workflow-v2
  * egov-perister
  * egov-localization
  * egov-notification-sms
  * egov-mdms
  * egov-idgen
  * egov-url-shortening
  * egov-hrms

## Key Functionalities <a href="#key-functionalities" id="key-functionalities"></a>

* Citizens/employees can file, track and rate the complaint.
* Citizens/employees can add images and comments related to the complaint.
* Citizens/employees can reopen the complaint within a certain period after resolution.
* Campaign supervisors can set up the complaint workflow according to their requirements and staff capacity.
* Can track the SLA for resolving each complaint, and can use it as a metric to streamline the process for resolving complaints.
* Department-wise assignment of the complaint to the LME.

## **Setup**&#x20;

{% stepper %}
{% step %}
### Clone or download the code from the GitHub repository

The source code for the Complaints registry is located in the [Git repository here](https://github.com/egovernments/health-campaign-services/tree/v1.1.0/core-services/pgr-services). Clone or download the code from this repository before proceeding.
{% endstep %}

{% step %}
### Add the Lombok extension/plugin&#x20;

The Complaints registry is a Spring Boot application that uses Lombok, a Java library. Add the Lombok extension/plugin to open and build the project in your IDE (like IntelliJ or Eclipse).
{% endstep %}

{% step %}
### Setup Lombok in IDEs

Install the Lombok plugin directly from the IntelliJ plugins marketplace.&#x20;

* Download the Lombok jar file.
*   Add the following line to your `eclipse.ini` file (replace `lombok.jar` with the correct path to your Lombok jar):

    ```
    -javaagent:lombok.jar
    ```
{% endstep %}

{% step %}
### Run application

Once Lombok is set up and the application is running (using your IDE or command line), you can start making API requests to the Individual service’s endpoints.
{% endstep %}

{% step %}
### Generate IDs

When you send API requests, the system generates the required IDs automatically as part of its normal operation.
{% endstep %}
{% endstepper %}

## API Details

Refer to the Swagger API for YAML file details: [Complaints.yaml](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/docs/health-api-specs/contracts/complaints-v2.yaml)

**Application.properties file information**_**:**_

Kafka topics for eGov persister

```
pgr.kafka.create.topic=save-pgr-request
pgr.kafka.update.topic=update-pgr-request
```

## Configuration Details <a href="#configuration-details" id="configuration-details"></a>

Follow the details outlined below to configure and enable complaints registry API actions and access control using MDMS, role-action mapping, persister, and indexer configurations.

### **MDMS Configurations**

Add the master data in the MDMS service with the module name as `RAINMAKER-PGR`. Below is a sample master data for the service:

```
{
  "tenantId": "default",
  "moduleName": "RAINMAKER-PGR",
  "ServiceDefs": [
    {
      "serviceCode": "SyncNotWorking",
      "name": "Sync Not Working",
      "keywords": "sync, not, working",
      "department": "TECH",
      "slaHours": 336,
      "menuPath": "Sync",
      "active": true,
      "order": 1
    },
    {
      "serviceCode": "NotEnoughStock",
      "name": "Not Enough Stock",
      "keywords": "not, enough, stock",
      "department": "WAREHOUSE",
      "slaHours": 336,
      "menuPath": "Sync",
      "active": true,
      "order": 1
    },
    {
      "serviceCode": "Other",
      "name": "Other",
      "keywords": "other",
      "department": "ADM",
      "slaHours": 336,
      "menuPath": "Sync",
      "active": true,
      "order": 1
    }
  ]
}
```

### Workflow Configurations

Create businessService (workflow configuration) using the  `/businessservice/_create`. Following is the product configuration for PGR:

```
{
  "RequestInfo": {
    "apiId": "Rainmaker",
    "action": "",
    "did": 1,
    "key": "",
    "msgId": "20170310130900|en_IN",
    "requesterId": "",
    "ts": 1513579888683,
    "ver": ".01",
    "authToken": "{{devAuth}}",
    "userInfo": {
      "id": 73,
      "userName": null,
      "name": null,
      "type": "EMPLOYEE",
      "mobileNumber": null,
      "emailId": null,
      "roles": [
        {
          "id": 2,
          "name": "Customer Support Representative",
          "code": null,
          "tenantId": null
        }
      ],
      "tenantId": null,
      "uuid": "uuid"
    }
  },
  "BusinessServices": [
   {
    "tenantId": "default",
    "businessService": "PGR",
    "business": "pgr-services",
    "businessServiceSla": 432000000,
    "states": [
      {
        "sla": null,
        "state": null,
        "applicationStatus": null,
        "docUploadRequired": false,
        "isStartState": true,
        "isTerminateState": false,
        "isStateUpdatable": true,
        "actions": [
          {
            "action": "CREATE",
            "nextState": "PENDING_ASSIGNMENT",
            "roles": [
              "REGISTRAR",
              "DISTRIBUTOR",
              "WAREHOUSE_MANAGER",
              "HELPDESK_USER",
              "SYSTEM_ADMINISTRATOR"
            ]
          }
        ]
      },
      {
        "sla": null,
        "state": "PENDING_ASSIGNMENT",
        "applicationStatus": "PENDING_ASSIGNMENT",
        "docUploadRequired": false,
        "isStartState": false,
        "isTerminateState": false,
        "isStateUpdatable": false,
        "actions": [
          {
            "action": "RESOLVE",
            "nextState": "RESOLVED",
            "roles": [
              "HELPDESK_USER",
              "L2_SUPPORT",
              "SYSTEM_ADMINISTRATOR"
            ]
          },
          {
            "action": "ASSIGN",
            "nextState": "PENDING_ASSIGNMENT",
            "roles": [
              "HELPDESK_USER",
              "L2_SUPPORT",
              "SYSTEM_ADMINISTRATOR"
            ]
          },
          {
            "action": "REJECT",
            "nextState": "REJECTED",
            "roles": [
              "HELPDESK_USER",
              "SYSTEM_ADMINISTRATOR"
            ]
          }
        ]
      },
      {
        "sla": null,
        "state": "RESOLVED",
        "applicationStatus": "RESOLVED",
        "isStateUpdatable": false,
        "docUploadRequired": false,
        "isStartState": false,
        "isTerminateState": true
      },
      {
        "sla": null,
        "state": "REJECTED",
        "applicationStatus": "REJECTED",
        "isStateUpdatable": false,
        "docUploadRequired": false,
        "isStartState": false,
        "isTerminateState": true
      }
    ]
  }
  ]
}
```

**Define Action URLs**&#x20;

Add new actions in the MDMS actions configuration (e.g., `action-test.json`). Each action represents an API endpoint you wish to secure and manage: [**Action-test.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)

```
{
  {
      "id": {{ID_PLACEHOLDER}},
      "name": "Create PGR Request",
      "url": "/pgr-services/v2/request/_create",
      "parentModule": "",
      "displayName": "Create PGR Request",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "pgr-services",
      "code": "null",
      "path": ""
    },
    {
      "id": {{ID_PLACEHOLDER}},
      "name": "Update PGR Request",
      "url": "/pgr-services/v2/request/_update",
      "parentModule": "",
      "displayName": "Update PGR Request",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "pgr-services",
      "code": "null",
      "path": ""
    },
    {
      "id": {{ID_PLACEHOLDER}},
      "name": "Search PGR Request",
      "url": "/pgr-services/v2/request/_search",
      "parentModule": "",
      "displayName": "Search PGR Request",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "pgr-services",
      "code": "null",
      "path": ""
    },
    {
      "id": {{ID_PLACEHOLDER}},
      "name": "Search PGR Request",
      "url": "/pgr-services/v2/request/_count",
      "parentModule": "",
      "displayName": "Count PGR Request",
      "orderNumber": 0,
      "enabled": false,
      "serviceCode": "pgr-services",
      "code": "null",
      "path": ""
    }
```

## **Persister Configuration**

Configure the persister service for the Complaints registry. This is typically done by adding/updating a YAML file (e.g., `pg-service-persister.yml`) - [pg-service-persister Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-persister/pg-service-persister.yml). This YAML maps API operations to database persistence logic (topics, queries, etc.).

## **Indexer Configuration**

Configure the indexer for the Complaints registry (e.g., `individual-indexer.yml`) -[Complaints Indexer Config](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-indexer/pgr-services.yml). This will ensure individual data is indexed and searchable as per business requirements.

## **Postman Collection**

[Click here](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/core-services/pgr-services/src/test/resources/postman/pgr-services.postman_collection.json)

{% hint style="info" %}
**Note:** The Complaints module is the digits pgr-services. Refer to [this](https://docs.digit.org/local-governance/local-governance-product-suite/local-governance-stack/public-grievances-and-redressal/pgr-service-configuration) doc for more information.
{% endhint %}
