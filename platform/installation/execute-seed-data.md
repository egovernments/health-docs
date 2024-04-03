---
description: >-
  This step involves the execution of the Postman collection for the minimum
  Setup Data required to run a campaign.
---

# Execute Seed Data

## Steps

All file examples in this document refer to the Default branches in the health campaign DevOps and config repositories for the example purposes. If you have replaced these repositories with your fork or clone then refer to the same here also.&#x20;

**Repository details**&#x20;

* [health-demo devops](https://github.com/egovernments/health-campaign-devops/tree/kubernetes-1.27)
  * Branch - kubernetes-1.27
* [config](https://github.com/egovernments/health-campaign-config/tree/DEMO)
  * Branch - DEMO
* [master data](https://github.com/egovernments/health-campaign-mdms/tree/DEMO)
  * Branch - DEMO



**Create an environment variable file and add the below variables in postman**

* Click on New and then Environment, then add the following variables

<div align="left">

<figure><img src="../../.gitbook/assets/Screenshot 2024-04-03 at 1.22.15 AM.png" alt="" width="375"><figcaption></figcaption></figure>

</div>

* **URL**
* **tenantId** - mz
* **apiUserName** and **apiPassword** - newly created superuser credentials
* **startDate** and **endDate** - in epoch format
*   **boundaryCode** -  use the default value (**VFTw0jbRf1y**) if Master data is unchanged \


    <div align="left">

    <figure><img src="../../.gitbook/assets/Screenshot 2024-04-03 at 11.42.14 AM.png" alt="" width="563"><figcaption></figcaption></figure>

    </div>
* **Import the seed data script**
  * [HCM Setup Script](https://api.postman.com/collections/3048487-a47132a6-df14-45f3-b3d3-8eb49afd0fc8?access\_key=PMAT-01HTHKB95286VQ8WZSER5AHMZ4) - This collection includes all the scripts to create users,  Projects, staff and product variants
  * Import the HCM setup script in Postman - [import guide](https://learning.postman.com/docs/getting-started/importing-and-exporting/importing-data/)
* Choose the new environment created in the environment tab ![](../../.gitbook/assets/environment-editor-select-env-v10-20.jpg)
*   Once Env is selected then click on the imported HCM setup collection click run&#x20;

    <div align="left">

    <figure><img src="../../.gitbook/assets/click on run.png" alt="" width="375"><figcaption></figcaption></figure>

    </div>



    <div align="left">

    <figure><img src="../../.gitbook/assets/Screenshot 2024-04-03 at 12.12.32 PM.png" alt="" width="375"><figcaption></figcaption></figure>

    </div>
* Once the Script is executed completely update the following values from the postman environment variable to the project-types.json(**health-campaign-mdms/blob/DEMO/data/mz/health/project-types.json**) master data file - [example link](https://github.com/egovernments/health-campaign-mdms/blob/DEMO/data/mz/health/project-types.json#L13)&#x20;
*   Pick the values by clicking on the eye icon&#x20;

    <div align="left">

    <figure><img src="../../.gitbook/assets/Screenshot 2024-04-03 at 12.22.54 PM.png" alt="" width="142"><figcaption></figcaption></figure>

    </div>
* Pick the value of a postman env variable named **ProductVariantIdBednet1** and replace all occurrences of the text **"PVAR-2024-03-21-000026"** with the copied value in the project-types.json.
* Pick the value of a postman env variable named **ProductVariantIdSP** and replace all occurrences of the text **"PVAR-2024-03-21-000022"** with the copied value in the project-types.json.
* Pick the value of a postman env variable named **ProductVariantIdAQ** and replace all the occurrences of the text **"PVAR-2024-03-21-000024"** with the copied value in the project-types.json.

<div align="left">

<figure><img src="../../.gitbook/assets/Screenshot 2024-04-03 at 12.37.33 PM.png" alt="" width="563"><figcaption></figcaption></figure>

</div>

**Localization scripts are** [**here**](https://api.postman.com/collections/1609763-24e5caf3-0367-47bc-bde5-ab70716f9153?access\_key=PMAT-01HRC8Y7ABSGEKGWYJGNH3DVBH)**, during local execution the script fails because of the Rate limit Exception but it will execute as expected on the server.**&#x20;

* Replace the **URL** variable in the Postman Environment to  your domain url
*   While executing the localisation collection, please execute only five folders at a time by unchecking the box in the run screen to avoid inbuilt rate limiter errors.&#x20;

    <div align="left">

    <figure><img src="../../.gitbook/assets/Screenshot 2024-04-03 at 2.59.53 PM.png" alt="" width="375"><figcaption></figcaption></figure>

    </div>
* Else create a port forward to the localisation pod by executing the below command

```shell
kubectl port-forward svc/egov-localization -n egov 8080:8080
```

* Replace the **URL** variable in the Postman Environment to http://localhost:8080
* Run the collection&#x20;

\
\
