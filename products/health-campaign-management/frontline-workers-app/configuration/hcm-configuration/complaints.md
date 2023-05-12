# Complaints

### Overview <a href="#overview" id="overview"></a>

Complaint Management is a system that enables employees to raise a complaints related to health campaigns . Employee can track the complaint, upload image related to the complaint, re-open the complaint if he/she is not satisfied and rate the service. This document contains the details about how to setup complaints module (pgr-service )and describes the functionalities it provides.

### Pre-requisites <a href="#pre-requisites" id="pre-requisites"></a>

Before you proceed with the configuration, make sure the following pre-requisites are met -

* _Java 8_
* Kafka server is up and running
* egov-persister service is running and has pgr-services persister config path added in it
* PSQL server is running and database is created to store complaint data
* _(Optional)_ Indexer config for pgr-services is added in egov-indexer yaml paths to index the generated data. Index are required for data visualisation in kibana or in DSS.
* _(Optional)_ Report config for pgr-services is added in Report service config paths. Required if reports are to be provided to the user.
* Following services should be up and running:
  * egov-user
  * egov-workflow-v2
  * egov-perister
  * egov-localization
  * egov-notification-sms
  * egov-mdms
  * egov-idgen
  * egov-url-shortening
  * egov-hrms

### Key Functionalities <a href="#key-functionalities" id="key-functionalities"></a>

* Citizen/Employee can file, track and rate the complaint
* Citizen/Employee can add image and comments related to the complaint
* Citizen/Employee can re-open the complaint in certain given period of time after resolution
* Campaign Supervisors can setup the complaint workflow according to their requirements and staff capacity
* Can track the SLA for resolving each complaint and can use it as a metric to streamline the process for resolving complaints
* Department wise assignment of the complaint to the LME

**Setup Details**

The source code for an [Complaints](https://github.com/egovernments/health-campaign-services/tree/v1.1.0/core-services/pgr-services)(pgr-service) is present in the health-campaign-services Git repo. The spring boot application needs the **Lombok\*** extension added to the IDE to load it. Once the application is up and running, the API requests can be posted to the URL and the IDs can be generated.&#x20;

* In the case of IntelliJ, the plugin can be installed directly. For eclipse, the Lombok jar location has to be added in the eclipse.ini file in this format javaagent:lombok.jar.

## API Details

Refer to the Swagger API for YAML file details: [Complaints.yaml](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/docs/health-api-specs/contracts/complaints-v2.yaml)

**Application.properties file information**_**:**_

Kafka topics for eGov persister

```
pgr.kafka.create.topic=save-pgr-request
pgr.kafka.update.topic=update-pgr-request
```

### Configuration Details <a href="#configuration-details" id="configuration-details"></a>

1. Add master data in MDMS service with module name as `RAINMAKER-PGR`. Following is some sample master data for the service:

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

2. Create businessService (workflow configuration) using the  `/businessservice/_create`. Following is the product configuration for PGR:

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

## Configuration details



**Action test: URL actions adding**

[**Action-test.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)

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

**Persister configuration**

[Complaints Persister Config](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-persister/pg-service-persister.yml)

**Indexer configuration**

[Complaints Indexer Config](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-indexer/pgr-services.yml)

**Postman collection**

[Click here](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/core-services/pgr-services/src/test/resources/postman/pgr-services.postman\_collection.json)

Note: Complaints module is digits pgr-services. Refer to [this](https://digit-discuss.atlassian.net/wiki/spaces/DD/pages/684392464/PGR+Services+v2.0?NO\_SSR=1) doc for more information
