# Execute Seed Data

## Overview

The second step involves the execution of the Postman collection for the minimum Setup Data required to run a campaign.&#x20;

## Steps

Follow the steps given below to configure the new environment.

This document refers to the DEMO branch in the health campaign DevOps and config repositories for the example purposes. If you have replaced these repositories with your fork or clone then refer to the same here also.&#x20;

Repo details -&#x20;

* [health-demo devops](https://github.com/egovernments/health-campaign-devops/tree/health-demo) -&#x20;
* [config](https://github.com/egovernments/health-campaign-config)
  * Branch - DEMO
* [mdms](https://github.com/egovernments/health-campaign-mdms)
  * Branch - DEMO

### Port-forwarding Steps

1. Configure the kube config file
2. Copy the egov-user pod name by executing this command\
   kubectl get pods -n egov | grep user
3. Port forward by executing the following cmd\
   kubectl port-forward {pod-name} -n egov 8081:8080
   * Ex:  kubectl port-forward -n egov egov-user-7d787d7d59-w7ppz 8081:8080

**Creation of super-user by port-forwarding to the user service**

* Port-forward the user service to 8081&#x20;
* use the below curl to create new super-user

```
curl --location 'http://localhost:8081/user/users/_createnovalidate'
--header 'Content-Type: application/json'
--data-raw '{ "requestInfo": { "apiId": "Rainmaker", "ver": ".01", "ts": null, "action": "_update", "did": "1", "key": "", "msgId": "20170310130900|en_IN", "authToken": "51e00caf-3218-4f15-ba70-a45f7d40abc1" }, "user": { "userName": "<>", "name": "Admin User", "gender": null, "mobileNumber": "9898989898", "type": "EMPLOYEE", "active": true, "password": "<>", "roles": [ { "name": "Super User", "code": "SUPERUSER", "tenantId": "mz" } ], "emailId": "xyz@gmail.com", "tenantId": "mz" } }'
```

* Replace username, password and tenantId with proper values.

**Import the script**

* [Seed data script](https://api.postman.com/collections/1609763-292c726d-a1c8-4c42-ad69-fd53de34a4b0?access\_key=PMAT-01HRSNQ0F3WB5QNEPDX6DMM14T) - This collection includes all the scripts
  * Create users
  * Create Projects and variants

**Changes to be made in the scripts**

* Update the values in Pre-request script - boundary details, start and end date
  * Boundary details can be found in this [file](https://github.com/egovernments/health-campaign-mdms/blob/DEMO/data/mz/egov-location/boundary-data.json#L52)
  * Start and end date should be converted to epoch format (Local Time)
* Project Create Individual API
  * projectTypeIdIndividual - projectTypeId value should be taken from MDMS for [Individual project ](https://github.com/egovernments/health-campaign-mdms/blob/DEMO/data/mz/health/project-types.json#L24)
  * If products are available in MDMS - update tests with actual product variants (pvar1, pvar2, pvar3 and pvar4) from [here](https://github.com/egovernments/health-campaign-mdms/blob/DEMO/data/mz/health/project-types.json#L32)
* Project Create Household API
  * projectTypeIdHousehold - projectTypeId value should be taken from MDMS for [household project](https://github.com/egovernments/health-campaign-mdms/blob/DEMO/data/mz/health/project-types.json#L6)
  * If products are available in MDMS - update tests with actual product variants (pvarbednet1 and pvarbednet2) from [here](https://github.com/egovernments/health-campaign-mdms/blob/DEMO/data/mz/health/project-types.json#L13)

**Create environment variable file and add the below variables**

* URL
* tenantTd
* apiUserName and apiPassword - newly created superuser creds

**If products are created by executing the scripts update the product variant details in MDMS**&#x20;

* Update individual  product variant details [here](https://github.com/egovernments/health-campaign-mdms/blob/DEMO/data/mz/health/project-types.json#L13)
* For household-based projects product variants need to be updated in multiple places
  * Update the [productVariantId](https://github.com/egovernments/health-campaign-mdms/blob/DEMO/data/mz/health/project-types.json#L32) for 2 cycles including multiple doses.

**Localization scripts are** [**here**](https://api.postman.com/collections/1609763-24e5caf3-0367-47bc-bde5-ab70716f9153?access\_key=PMAT-01HRC8Y7ABSGEKGWYJGNH3DVBH)**, during local execution the script fails because of Rate limit Exception but it will execute as expected on the server.**

* Update the tenantID

Repo details

* [devops](https://github.com/egovernments/health-campaign-devops/tree/kubernetes-1.27)
* [config](https://github.com/egovernments/health-campaign-config)
  * Branch - DEMO
* [mdms](https://github.com/egovernments/health-campaign-mdms)
  * Branch - DEMO

Issues observed while configuring new environment -&#x20;

1. egov-user validator property was missing

\
\
