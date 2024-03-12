# Configuring Tenants

## Overview <a href="#overview" id="overview"></a>

An Urban Local Body (ULB) is defined as a tenant. Tenant configuration is done in MDMS.

## Pre-requisites <a href="#pre-requisites" id="pre-requisites"></a>

Before proceeding with the configuration, the following pre-requisites are met:

* Knowledge of JSON and how to write a JSON is required.
* Knowledge of MDMS is required.
* User with permission to edit the git repository where MDMS data is configured.

## Key Functionalities <a href="#key-functionalities" id="key-functionalities"></a>

* For the login page, city name selection is required. Tenant added in MDMS shows in the city drop-down of the login page.
* In reports or the employee inbox page, the details related to ULB are displayed from the fetched ULB data which is added in MDMS.
* Modules, that is, TL, PT, and MCS can be enabled based on the requirement for the tenant.

## Deployment Details

* After adding the new tenant, the MDMS service needs to be restarted to read the newly added data.

## Configuration Details <a href="#configuration-details" id="configuration-details"></a>

1. Tenant is added in tenant.json.\
   In MDMS, file **tenant.json**, under the **tenant** folder holds the details of the state and ULBs to be added in that state.&#x20;

```
{
  "tenantId": "uk",  //<ReplaceWithDesiredTenantId>
  "moduleName": "tenant",
  "tenants": [ {
      "code": "uk.citya", //<state.ulbname>
      "name": "City A",  //<name of the ulb>
      "description": "City A", //<ulb description>
      "logoId": "https://s3.ap-south-1.amazonaws.com/uk-egov-assets/uk.citya/logo.png",  //<ulb logo path - To display ulb logo on login>
      "imageId": null,
      "domainUrl": "", //<ulb website url>
      "type": "CITY",
      "twitterUrl": null,
      "facebookUrl": null,
      "emailId": "complaints.citya@gmail.com",  //<ulb email id>
      "OfficeTimings": {
        "Mon - Sat": "10.00 AM - 5.00 PM"
      },
"city": {
"name": "City A",
"localName": null,
"districtCode": "CITYA",
"districtName": null,
"regionName": null,
"ulbGrade": "Municipal Corporation",
"longitude": 78.0322,
"latitude": 30.3165,
"shapeFileLocation": null,
"captcha": null,
"code": "248430"
},
"address": "City A Municipal Cornoration Address",
"contactNumber": "91 (135) 2653572"
}]}
```

#### Note:&#x20;

* To enable the tenant the above data should be pushed in the tenant.json file. Here "ULB Grade" and City  "Code" are important fields. **ULB Grade** can have a set of allowed values that determines the ULB type, ([Municipal corporation (Nagar Nigam)](https://en.wikipedia.org/wiki/Municipal\_Corporations\_in\_India), Municipality (municipal council, municipal board, municipal committee) (Nagar Parishad), etc). City "**Code**" has to be unique to each tenant.  This city-specific code is used in all transactions. Not permissible to change the code. If changed we will lose the data of the previous transactions done.
* Naming Convention for **Tenants Code**

&#x20;      **“Code”:“uk.citya”** is **StateTenantId.ULBTenantName"**

* **"logoId": "**[**https://s3.ap-south-1.amazonaws.com/uk-egov-assets/uk.citya/logo.png**](https://s3.ap-south-1.amazonaws.com/pb-egov-assets/pb.citya/logo.png)**",**  Here the last section of the path should be "/\<tenantId>/logo.png". If we use anything else, the logo will not be displayed on the UI. **\<tenantId>** is the tenant code ie **“uk.citya”.**

2\. Localisation should be pushed for ULB grade and ULB name.  The format is given below.\
&#x20;   **Localisation for ULB Grade:**

```
{
     "code": "ULBGRADE_MUNICIPAL_CORPORATION",
     "message": "MUNICIPAL CORPORATION",
     "module": "rainmaker-common",
     "locale": "en_IN"
  }
```

**Localisation for ULB Name:**

```
{
     "code": "TENANT_TENANTS_UK_HALDWANI",    
     "message": "Haldwani",
     "module": "rainmaker-tl",
     "locale": "en_IN"
}
```

Format of localisation code for tenant name : <**MDMS\_State\_Tenant\_Folder\_Name**>\_<**Tenants\_Fille\_Name**>\_<**Tenant\_Code**>(replace dot with underscore)

2. Boundary data should be added for the new tenant.

## Reference Docs <a href="#reference-docs" id="reference-docs"></a>

| **Title**        | **Link**                                                                                                                                                                       |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| tenant json file | [https://github.com/egovernments/ukd-mdms-data/blob/master/data/uk/tenant/tenants.json](https://github.com/egovernments/ukd-mdms-data/blob/master/data/uk/tenant/tenants.json) |
| content          | [MDMS Configuration](mdms-configuration.md)                                                                                                                                    |
