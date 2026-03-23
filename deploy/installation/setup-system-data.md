---
description: Post installation steps
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/installation/setup-system-data
---

# Setup System Data

## Overview

Before you run the DIGIT HCM product, you need to set up the basic system data, such as boundaries of the geography and the master data. Follow the steps on this page to load the base data into the server.

## **Steps**

{% stepper %}
{% step %}
### Download the database dump file

* Download the `seed_data_dump_2.0.sql` file into your local system and save it in a folder/directory.

{% file src="../../.gitbook/assets/seed_data_dump_v2.0.sql" %}
{% endstep %}

{% step %}
### Load the backup file into the database

* Execute the below command to fetch the database **pod name.**

```
  kubectl get pods -n playground
```

* Copy the **NAME** from the output. Refer to the screenshot below:

<figure><img src="../../.gitbook/assets/image (206).png" alt=""><figcaption><p>Sample screenshot of database pod</p></figcaption></figure>

* Navigate to `infra-as-code/terraform/sample-aws`
* Open `input.yaml`and note down **db\_username**, **db\_name** configured earlier.

{% hint style="info" %}
The **db\_username and db\_name** values were configured earlier in the forked repository **infra-as-code/terraform/sample-aws/input.yaml** file.
{% endhint %}

* Get {DB\_HOST} value by executing the below command.

```
 kubectl describe cm -n egov egov-config
```

* Find and copy the "db-host" value. Refer to the screenshot below for the select and copy command for "db-host". This will be used in the next commands.&#x20;

<figure><img src="../../.gitbook/assets/image (207).png" alt=""><figcaption><p>Sample Screenshot of command output for db_host</p></figcaption></figure>
{% endstep %}

{% step %}
### Load data into the database

* Go to the folder/directory where the dump file was downloaded and open the terminal in that folder or use the '`cd`' command to change to that directory:

<figure><img src="../../.gitbook/assets/image (208).png" alt=""><figcaption><p>Example screenshot with cd command to download folder</p></figcaption></figure>

* Replace the values for these - `{PLAYGROUND_POD_NAME}` ,  `{DATABASE_HOST}`,  {`DATABASE_USERNAME}`,  {`DB_NAME}` in the command given below and run it:

```
kubectl cp seed_data_dump_1.7.sql playground/{PLAYGROUND_POD_NAME}:/home/seed_data_dump_1.7.sql && kubectl exec -n playground {PLAYGROUND_POD_NAME} -- sh -c "PGPASSWORD=demo123456 psql -h {DATABASE_HOST} -p 5432 -U {DATABASE_USERNAME} -d {DATABASE_NAME} -f /home/seed_data_dump_1.7.sql"
```
{% endstep %}

{% step %}
### Verify the output

* The output should look similar to the screenshot given below:

<figure><img src="../../.gitbook/assets/image (209).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Redeploy services

* Run the below command to delete and restart all the services

```
kubectl delete pods --all -n egov
```

* Run the command below to check if all pods/services are running. If not, wait for some time and check again:

```
kubectl get pods -n egov
```
{% endstep %}

{% step %}
### Setup Complaints & Payments workflow

Follow the steps given below to activate the Complaints Module.

* Port Forward workflow v2 service using the below command

```
kubectl port-forward svc/egov-workflow-v2 -n egov 8080:8080
```

* Run the below cURL to create a business service for the Complaints workflow.

```
curl --location 'http://localhost:8080/egov-workflow-v2/egov-wf/businessservice/_create' \
--header 'Content-Type: application/json' \
--data-raw '{"RequestInfo":{"apiId":"Rainmaker","action":"","did":1,"key":"","msgId":"20170310130900|en_IN","requesterId":"","ts":1513579888683,"ver":".01","authToken":"67f85f54-5cac-4aa6-b90f-828996cc2e30","userInfo":{"id":24226,"uuid":"11b0e02b-0145-4de2-bc42-c97b96264807","userName":"amr001","name":"leela","mobileNumber":"9814424443","emailId":"leela@llgmail.com","locale":null,"type":"EMPLOYEE","roles":[{"name":"CSC Collection Operator","code":"CSC_COLL_OPERATOR","tenantId":"pb.amritsar"},{"name":"Employee","code":"EMPLOYEE","tenantId":"pb.amritsar"},{"name":"Grievance Routing Officer","code":"GRO","tenantId":"pb.amritsar"},{"name":"NoC counter employee","code":"NOC_CEMP","tenantId":"pb.amritsar"},{"name":"TL Counter Employee","code":"TL_CEMP","tenantId":"pb.amritsar"},{"name":"TL Field Inspector","code":"TL_FIELD_INSPECTOR","tenantId":"pb.amritsar"},{"name":"TL Creator","code":"TL_CREATOR","tenantId":"pb.amritsar"},{"name":"Customer Support Representative","code":"CSR","tenantId":"pb.amritsar"},{"name":"NoC counter Approver","code":"NOC_APPROVER","tenantId":"pb.amritsar"},{"name":"TL Approver","code":"TL_APPROVER","tenantId":"pb.amritsar"},{"name":"Super User","code":"SUPERUSER","tenantId":"pb"},{"name":"BPA Services Approver","code":"BPA_APPROVER","tenantId":"pb.amritsar"},{"name":"Field Employee","code":"FEMP","tenantId":"pb.amritsar"},{"name":"Counter Employee","code":"CEMP","tenantId":"pb.amritsar"},{"name":"NoC Field Inpector","code":"NOC_FIELD_INSPECTOR","tenantId":"pb.amritsar"},{"name":"NOC Department Approver","code":"NOC_DEPT_APPROVER","tenantId":"pb.amritsar"},{"name":"Super User","code":"SUPERUSER","tenantId":"pb.amritsar"},{"name":"Grievance Officer","code":"GO","tenantId":"pb.amritsar"},{"name":"Anonymous User","code":"ANONYMOUS","tenantId":"pb.amritsar"},{"name":"Collection Operator","code":"COLL_OPERATOR","tenantId":"pb.amritsar"},{"name":"NoC Doc Verifier","code":"NOC_DOC_VERIFIER","tenantId":"pb.amritsar"},{"name":"TL doc verifier","code":"TL_DOC_VERIFIER","tenantId":"pb.amritsar"}],"active":true,"tenantId":"mz"}},"BusinessServices":[{"tenantId":"mz","businessService":"PGR","business":"pgr-services","businessServiceSla":432000000,"states":[{"tenantId":"mz","sla":null,"state":null,"applicationStatus":null,"docUploadRequired":false,"isStartState":true,"isTerminateState":false,"isStateUpdatable":true,"actions":[{"tenantId":"mz","action":"CREATE","nextState":"PENDING_ASSIGNMENT","roles":["REGISTRAR","DISTRIBUTOR","WAREHOUSE_MANAGER","HELPDESK_USER","SYSTEM_ADMINISTRATOR","PGR-ADMIN"],"active":true}]},{"tenantId":"mz","sla":null,"state":"PENDING_ASSIGNMENT","applicationStatus":"PENDING_ASSIGNMENT","docUploadRequired":false,"isStartState":false,"isTerminateState":false,"isStateUpdatable":false,"actions":[{"tenantId":"mz","currentState":"PENDING_ASSIGNMENT","action":"RESOLVE","nextState":"RESOLVED","roles":["HELPDESK_USER","L2_SUPPORT","SYSTEM_ADMINISTRATOR","PGR-ADMIN"],"active":true},{"tenantId":"mz","currentState":"PENDING_ASSIGNMENT","action":"ASSIGN","nextState":"PENDING_ASSIGNMENT","roles":["HELPDESK_USER","L2_SUPPORT","SYSTEM_ADMINISTRATOR","PGR-ADMIN"],"active":true},{"tenantId":"mz","currentState":"PENDING_ASSIGNMENT","action":"REJECT","nextState":"REJECTED","roles":["HELPDESK_USER","SYSTEM_ADMINISTRATOR","PGR-ADMIN"],"active":true}]},{"tenantId":"mz","sla":null,"state":"RESOLVED","applicationStatus":"RESOLVED","docUploadRequired":false,"isStartState":false,"isTerminateState":true,"isStateUpdatable":false,"actions":null},{"tenantId":"mz","sla":null,"state":"REJECTED","applicationStatus":"REJECTED","docUploadRequired":false,"isStartState":false,"isTerminateState":true,"isStateUpdatable":false,"actions":null},{"tenantId":"mz","sla":null,"state":"CANCELLED","applicationStatus":"CANCELLED","docUploadRequired":false,"isStartState":false,"isTerminateState":true,"isStateUpdatable":false,"actions":null}]}]}'
```

* Run the below cURL to create a business service for the payments workflow.

```
curl --location 'http://localhost:8080/egov-workflow-v2/egov-wf/businessservice/_create' \
--header 'Content-Type: application/json' \
--data '{
    "RequestInfo": {
        "apiId": "muster-roll",
        "action": "",
        "did": 1,
        "key": "",
        "msgId": "20170310130900|en_IN",
        "requesterId": "",
        "ts": 1513579888683,
        "ver": "1.0.0",
        "authToken": "94ecb06f-8e5b-4798-af8f-56a987560209",
        "userInfo": {
            "uuid": "5e6aad61-021b-4f0b-affe-e2cf306f2d6b"
        }
    },
    "BusinessServices": [
        {
            "tenantId": "mz",
            "businessService": "HCMMUSTERROLL",
            "business": "health-muster-roll",
            "businessServiceSla": null,
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
                            "action": "SUBMIT",
                            "nextState": "APPROVAL_PENDING",
                            "roles": [
                                "PROXIMITY_SUPERVISOR"
                            ]
                        }
                    ]
                },
                {
                    "sla": null,
                    "state": "APPROVAL_PENDING",
                    "applicationStatus": "INWORKFLOW",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": false,
                    "isStateUpdatable": true,
                    "actions": [
                        {
                            "action": "EDIT",
                            "nextState": "APPROVAL_PENDING",
                            "roles": [
                                "PROXIMITY_SUPERVISOR"
                            ]
                        },
                        {
                            "action": "APPROVE",
                            "nextState": "APPROVED",
                            "roles": [
                                "PROXIMITY_SUPERVISOR"
                            ]
                        }
                    ]
                },
                {
                    "sla": null,
                    "state": "APPROVED",
                    "applicationStatus": "ACTIVE",
                    "docUploadRequired": false,
                    "isStartState": false,
                    "isTerminateState": true,
                    "isStateUpdatable": false,
                    "actions": null
                }
            ]
        }
    ]
}'

```
{% endstep %}

{% step %}
### Create Superuser

* Run the below command to check if the egov-user service is running.

```
kubectl get pods -n egov | grep egov-user
```

<div align="left"><figure><img src="../../.gitbook/assets/Screenshot 2024-08-01 at 2.22.40 PM.png" alt="" width="563"><figcaption></figcaption></figure></div>

* If the egov-user service is running with Ready 1/1, then connect to it by port forwarding:

```
kubectl port-forward svc/egov-user -n egov 8080:8080
```

* Import the below curl in Postman or execute it in another terminal window:

```
curl --location 'http://localhost:8080/user/users/_createnovalidate' \
--header 'Content-Type: application/json' \
--data-raw '{
    "requestInfo": {
        "apiId": "Rainmaker",
        "ver": ".01",
        "ts": null,
        "action": "_update",
        "did": "1",
        "key": "",
        "msgId": "20170310130900|en_IN",
        "authToken": "51e00caf-3218-4f15-ba70-a45f7d40abc1"
    },
    "user": {
        "userName": "testuser2",
        "name": "Admin User 2",
        "gender": null,
        "mobileNumber": "9898989899",
        "type": "EMPLOYEE",
        "active": true,
        "password": "eGov@1234",
        "roles": [
            {
                "name": "Super User",
                "code": "SUPERUSER",
                "tenantId": "mz"
            },
             {
                "name": "CAMPAIGN_MANAGER",
                "code": "CAMPAIGN_MANAGER",
                "tenantId": "mz"
            },
            { 
                "name": "BOUNDARY_MANAGER",
                "code": "BOUNDARY_MANAGER",
                "tenantId": "mz"
            },
            {
                "name": "System Administrator",
                "code": "SYSTEM_ADMINISTRATOR",
                "tenantId": "mz"
            },
            {
                "name": "National Supervisor",
                "code": "NATIONAL_SUPERVISOR",
                "tenantId": "mz"
            },
            {
                "name": "Localisation admin",
                "code": "LOC_ADMIN",
                "tenantId": "mz"
            },
            {
                "name": "Distributor",
                "code": "DISTRIBUTOR",
                "tenantId": "mz"
            },
            {
                "name": "MDMS ADMIN",
                "code": "MDMS_ADMIN",
                "tenantId": "mz"
            },
            {
                "name": "HELPDESK USER",
                "code": "HELPDESK_USER",
                "tenantId": "mz"
            },
            {
                "name": "HRMS Admin",
                "code": "HRMS_ADMIN",
                "tenantId": "mz"
            },
            {
                "name": "Microplan Campaign integrator",
                "code": "MICROPLAN_CAMPAIGN_INTEGRATOR",
                "tenantId": "mz"
            },
            {
                "name": "Microplan Admin",
                "code": "MICROPLAN_ADMIN",
                "tenantId": "mz"
            }
        ],
        "emailId": "xyz@gmail.com",
        "tenantId": "mz"
    }
}'

```

* Replace the username, password, and tenantId with the required values. (Keep tenantid as 'mz' if master data is loaded in the database unchanged).
{% endstep %}

{% step %}
### Create new boundary data

* The initial seed boundary data includes a default boundary master dataset.&#x20;
* To configure a **custom boundary hierarchy and data**, refer to the detailed setup guide provided in the link below:&#x20;

{% embed url="https://docs.digit.org/console/setup/configuration#boundary-master-setup" %}
{% endstep %}
{% endstepper %}
