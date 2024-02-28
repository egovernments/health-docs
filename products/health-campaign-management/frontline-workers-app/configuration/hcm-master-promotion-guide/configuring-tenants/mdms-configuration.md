# MDMS Configuration

## Steps to Setup State/Urban Local Body (ULB):

### Adding a Tenant:

In MDMS, the file tenant.json under the tenant folder holds the details of the state and ULBs to be enabled in that state.

```
{

  "tenantId": "pb",  //<ReplaceWithDesiredTenantId>

 "moduleName": "tenant",

 "tenants": [ {

      "code": "pb.citya", //<state.ulbname>

      "name": "City A",  //<name of the ulb>

      "description": "City A", //<ulb description>

      "logoId": "https://s3.ap-south-1.amazonaws.com/pb-egov-assets/pb.citya/logo.png",  //<ulb logo path - To display ulb logo on login>

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

"longitude": 75.5761829,

"latitude": 31.3260152,

"shapeFileLocation": null,

"captcha": null,

"code": "1013"

},

"address": "City A Municipal Cornoration Address",

"contactNumber": "001-2345876"

}]}
```

Note:

To enable a state and a ULB, the above data should be pushed in tenant.json file. Here "ULB Grade" and City 'Code' are important fields. ULB Grade can have a set of allowed values that determines the ULB type, (Municipal corporation (Nagar Nigam), Municipality (municipal council, municipal board, municipal committee) (Nagar Parishad), etc). City 'Code' has to be unique to each tenant. This city-specific code is used in all transactions. It is not permissible to change the code. If changed, we will lose the data of the previous transactions done.

Localisation should be pushed for ULB grade and ULB name. The formats are given below:

**Localisation for ULB Grade**

```
{

            "code": "ULBGRADE_MUNICIPAL_CORPORATION",

            "message": "MUNICIPAL CORPORATION",

            "module": "rainmaker-common",

            "locale": "en_IN"

        }
```

**Localisation for ULB Name**

```
{

            "code": "TENANT_TENANTS_UK_HALDWANI",    

            "message": "Haldwani",

            "module": "rainmaker-tl",

            "locale": "en_IN"

        }
```

Format of localization code for tenant name:

<**MDMS\_State\_Tenant\_Folder\_Name**>\_<**Tenants\_Fille\_Name**>\_<**Tenant\_Code**>(replace dot with underscore)

1.  Naming Convention for **Tenants Code**

    * \>

    **“Code”:“pb.citya”** is **StateTenantId.ULBTenantName"**
2. **"logoId": "**[**https://s3.ap-south-1.amazonaws.com/pb-egov-assets/pb.citya/logo.png**](https://s3.ap-south-1.amazonaws.com/pb-egov-assets/pb.citya/logo.png)**",**  Here the last section of the path should be "/\<tenantId>/logo.png". If we use anything else, the logo will not be displayed on the UI. **\<tenantId>** is the tenant code ie **“pb.citya”.**

* **citymodule.json** file under the **tenant** folder used to activate modules in specific ulb. Example:

```
{

  "module": "TL",

  "code": "TL",   

    "tenants": [{ "code": "pb.citya"},   

            {"code": "pb.cityb"}]

            }


```

Module **TL** is enabled in ULB **City A** and **City B. Modules** mentioned in this file appear in the menu tree of the application.  A ULB-level module enable or disable is handled here.

### Adding a State

In MDMS, the file **StateInfo.json**, under the **common-masters** folder holds the state data.&#x20;

```
{ 

"tenantId": "pb"  ,  //<ReplaceWithDesiredTenantId>

"moduleName": "common-masters",

"StateInfo": [   {

"name": "punjab",

"code":"pb"  , //<ReplaceWithDesiredTenantId>  "bannerUrl":https://amazonaws-url/foldername/file.jpg",  <bannerimage file path>

"logoUrl":"https://amazonaws-url/foldername/file.jpg", <state logo image file path>

"hasLocalisation" : true, <if true, enables multilingual support mentioned below. Or else by default english>

      "languages" : [ {   <languages to be supported are listed here>

          "label": "ENGLISH",

          "value": "en_IN"

        }, {

          "label": "हिंदी",

          "value": "hi_IN"

        }  ],

      "defaultUrl" : {

          "citizen" : "/user/register",

          "employee" : "/user/login"

}  } ]

}
```

**Boundary Data Load:**

* Boundary is ULB-specific master data. For revenue modules, we use the revenue boundary.  It is pushed under each ULB.

The file path would be: [https://github.com/egovernments/state-mdms-data/tree/master/data/tenant/ulb/egov-location/boundary-data.json](https://github.com/egovernments/state-mdms-data/tree/master/data/tenant/sonpur/egov-location)

**Boundary Hierarchy** :  Zone -> Ward -> Locality -> Area

Boundary data json is generated using the implementation kit.&#x20;

**Trade License  Master Data Load:**

**Trade Type Master:**

* Trade Types of all ULBs are pushed under the “Trade License” folder of the MDMS repo.

The file path would be:

{% embed url="https://github.com/egovernments/state-mdms-data/tree/master/data/tenant/TradeLicense/TradeType.json" %}

Example:

```
{

  "tenantId": "xyz",  //<ReplaceWithDesiredTenantId>

  "moduleName": "TradeLicense",

  "TradeType": [

    {

      "code": "TRADE.INDUSTRY.FM", //<Trade Type Code is mentioned here>

      "uom": null,

      "applicationDocument": [

        "IDPROOF",

        "OTHER"

      ],

      "verificationDocument": [],

      "active": true

    }]

}


```

For each trade type, sub-types are defined. Each sub-type has mandatory documents to be attached. A unique code will be defined for each trade type, sub-type and document. &#x20;

**"code": "**[**TRADE.INDUSTRY.FM**](http://trade.industry.fm/)**"  // Defines Category -> Trade Type -> Trade Sub Type** &#x20;

**TRADE is category**&#x20;

**INDUSTRY is a Trade Type**

**FM is a Trade Subtype (Floor Mill)**

**Note:** Code defines the levels of hierarchy. Dots define the number of hierarchy levels.  TRADE.INDUSTRY specifies two levels, which means TradeType INDUSTRY falls under the TRADE category. [TRADE.INDUSTRY.FM](http://trade.industry.fm/) specifies three levels, which means FM is a sub-type under INDUSTRY.

For all the master data, we are pushing localisation messages. An explanation on inserting localisation for master data is given in the localisation section below:

**Trade Rates:**

* Trade Rates for each trade subtype are stored in the database. Rest endpoints are available to create trade rates and search existing trade rates. Can use the below curl command for create and search trade rates.
* \-------------------------- Search Trade Rates ------------------------------------

curl -X POST \  '[https://APPLICATION-URL/tl-calculator/billingslab/\_search?tenantId=state.ulbname](https://application-url/tl-calculator/billingslab/\_search?tenantId=state.ulbname)' \\

* H 'Content-Type: application/json' \\
* H 'Postman-Token: 80d84c50-b16e-44dd-9cc5-544def2ecd81' \\

"RequestInfo": {

"authToken": "3bad8c62-b769-4a69-bf8b-0c6f008a5f01"

}

}'

* \-------------------------- Create Trade Rates ------------------------------------

curl -X POST \  '[https://APPLICATION-URL/tl-calculator/billingslab/\_create?tenantId=state.ulbname](https://application-url/tl-calculator/billingslab/\_create?tenantId=state.ulbname)' \\

* H 'Content-Type: application/json' \\
* H 'Postman-Token: 59653a46-0a96-4eb0-a1cd-3e6c47f67aa0' \\

"RequestInfo": {

"authToken": "796978d5-47d4-48b0-8995-f9e3fbfc32d8"

},

"billingSlab": \[

&#x20; {

&#x20;   "tenantId": "state.ulbname",

&#x20;   "licenseType": "PERMANENT",

&#x20;   "structureType": "IMMOVABLE.SHED",

&#x20;   "tradeType": "TRADE.HOTELS.HL30B",

&#x20;   "accessoryCategory": null,

&#x20;   "type": "FLAT",

&#x20;   "uom": null,

&#x20;   "fromUom": 0,

&#x20;   "toUom": 0,

&#x20;   "rate": 1000

&#x20; }

]&#x20;

}’  //\<Replacewith proper application URL and the tenantid>

Note: Currently, the delete rate is not supported. To delete any specific rate, updating 'rate' to null using the update endpoint will inactivate the rate for a specific sub-type.

### **Adding role, and actions to MDMS**

* **Actions** are the features like “Create”, ”Update”, “Search” and so on. Action JSON file maps all the actions, that is, URLs. [**https://github.com/egovernments/state-mdms-data/tree/master/data/tenant/ACCESSCONTROL-ACTIONS-TEST**](https://github.com/egovernments/state-mdms-data/tree/master/data/tenant/ACCESSCONTROL-ACTIONS-TEST)

**Actions-test.json:**&#x20;

```
{

      "id": 1685,  //<Unique identifier>

      "name": "Create TradeLicense",

      "url": "/tl-services/v1/_create", //<url of the feature>

      "parentModule": "",

      "displayName": "Create TradeLicense",

      "orderNumber": 0,

      "enabled": false,

      "serviceCode": "tl-services",

      "code": "null",

      "path": ""

}
```

* **Role-based actions** will have mappings between actions and roles. It specifies which role can perform what actions. Example: A user with a TLCreator role mapped to the **“Create Trade License”** action/feature, can only perform the create TL application.  A user can have multiple roles and multiple actions mapped.

**Roleactions.json:**

```
"roleactions": [

    {

      "rolecode": "TL_CREATOR",

      "actionid": 1685,

      "actioncode": "",

      "tenantId": "pb"  //<ReplacewithTenantId> 




    }]
```

**Localisation**

* All the master data, labels, notifications, validation/success messages are localised. To support multi-lingual, we use a common code for each field for which messages in different languages will be pushed using endpoints. Create, upsert, and search endpoints are used to create/update localisation messages.
* Need to push localisation messages for newly-added master data.

Localisation code format for Masters:  **\<ModuleName\_MasterName\_Code>**

Example: Trade Type Master -

```
{

            "code": "TRADELICENSE_TRADETYPE_INDUSTRY",

            "message": "Industry/Factory/Mill",

            "module": "rainmaker-tl",

            "locale": "en_IN"

        }
```

Trade Sub-Type:

```
{

            "code": "TRADELICENSE_TRADETYPE_TRADE_INDUSTRY_FM",

            "message": "Flour mill, spice mill,cotton machine",

            "module": "rainmaker-tl",

            "locale": "en_IN"

        }
```

Use the below rest endpoints to push these data:

* Only boundary localization messages are pushed at the ULB level. Rest all are pushed at the state level.
* \-----------------------

**Upsert: Update and Insert Localization**

* \-------------------------
* \--------

**This API, updates if code already exists or else inserts newly**

* \----------------

curl -X POST \  '[https://APPLICATION-URL/localization/messages/v1/\_upsert?tenantId=XYZ\&locale=en\_IN](https://application-url/localization/messages/v1/\_upsert?tenantId=XYZ\&locale=en\_IN)' \\

* H 'Content-Type: application/json' \\
* H 'Postman-Token: 39264728-2857-4cb4-825c-53612fce51c0' \\

&#x20; "RequestInfo": {

&#x20;   "api\_id": "org.egov.pgr",

&#x20;   "ver": "1.0",

&#x20;   "ts": "16-03-2017 12:09:14",

&#x20;   "action": null,

&#x20;   "did": "4354648646",

&#x20;   "key": "xyz",

&#x20;   "msg\_id": "654654",

&#x20;   "requester\_id": "61",

&#x20;   "authToken": "8850660e-7d35-4e8e-9d8b-9656c1a91d30"

&#x20; },

&#x20; "tenantId": "XYZ",

&#x20;   "messages":\[

&#x20;   {

&#x20;   "code": "TL\_OWNER\_NAME",

&#x20;   "message": "OWNER",

&#x20;   "module": "rainmaker-tl",

&#x20;   "locale": "en\_IN"

&#x20; }

&#x20; ]

}'

* \-----------------------Search Localisation--------------------------

curl -X POST \  '[https://APPLICATION-URL/localization/messages/v1/\_search?locale=en\_IN\&tenantId=XYZ](https://application-url/localization/messages/v1/\_search?locale=en\_IN\&tenantId=XYZ)' \\

* H 'Content-Type: application/json' \\
* H 'Postman-Token: 8fae6bd4-17ae-4fa5-afc4-a692f2c74064' \\

&#x20;   "RequestInfo": {

&#x20;       "api\_id": "org.egov.pgr",

&#x20;       "ver": "1.0",

&#x20;       "ts": "16-03-2017 12:09:14",

&#x20;       "action": null,

&#x20;       "did": "4354648646",

&#x20;       "key": "xyz",

&#x20;       "msg\_id": "654654",

&#x20;       "requester\_id": "61",

&#x20;       "authToken": "7315d713-773c-4282-97a1-b69b95895711"

&#x20;   },

&#x20;   "tenantId": "XYZ"

}'

Note: Product-level localised messages are attached in this link. [Localisation\_Messages](https://drive.google.com/file/d/1bTaXAhZrWPD0d7QcBD2He0r638E66\_3s/view?usp=sharing)  Use this json to load the labels and the basic master data with the above endpoints.

### **Employee Creation**

**HRMS Admin and SUPERUSER**

* "CreateNoValidate" api is used to create admin and superuser for the first time when no users exists. This endpoint is for User Creation only.
* For Employee creation, Separate endpoint or UI used. HRMS admin is responsible for employee creation.
* \----------------------

**Create No Validate Api to create first time employees**

* \---------------------

curl -X POST \\

&#x20;[http://localhost:8088/user/users/\_createnovalidate](http://localhost:8088/user/users/\_createnovalidate) \\

* H ‘Content-Type: application/json’ \\
* H ‘Postman-Token: 3c8eb85e-877e-4b0a-a1db-60676fa5eb45’ \\
* H ‘cache-control: no-cache’

```
{

"RequestInfo": {

  "apiId": "ap.public",

  "ver": "1",

  "ts": null,

  "action": "POST",

  "did": null,

  "key": null,

  "msgId": "8c11c5ca-03bd-11e7-93ae-92361f002671",

  "userInfo": {

    "type" : "SYSTEM",

    "name" : "kiran",

    "id" : 32  },

  "authToken": "{{access_token}}"

},

 "user": {

          "id": 3,

          "userName": "EMP3_SUPER",

          "salutation": "MR",

          "name": "PB_SUPERUSER",

          "gender": "MALE",

          "mobileNumber": "9898989897",

          "emailId": "jamalbhai@maildrop.cc",

          "altContactNumber": "",

          "password": "PBEGOV123",

          "pan": "AITGC5624P",

          "aadhaarNumber": "96a70",

          "permanentAddress": "Dawakhana",

          "permanentCity": "Kaikoo",

          "permanentPinCode": "111111",

          "correspondenceAddress": "correAddress",

          "correspondenceCity": "banglore",

          "correspondencePinCode": "1234",

          "addresses": [

              {

                  "pinCode": "1234",

                  "city": "banglore",

                  "address": "correAddress",

                  "type": "CORRESPONDENCE",

                  "id": 1,

                  "tenantId": "pb.citya",

                  "userId": 1,

                  "addressType": "CORRESPONDENCE",

                  "lastModifiedDate": null,

                  "lastModifiedBy": null

              },

              {

                  "pinCode": "111111",

                  "city": "Kaikoo",

                  "address": "Dawakhana",

                  "type": "PERMANENT",

                  "id": 2,

                  "tenantId": "pb.citya",

                  "userId": 1,

                  "addressType": "PERMANENT",

                  "lastModifiedDate": null,

                  "lastModifiedBy": null

              }

          ],

          "active": true,

          "locale": "string",

          "type": "EMPLOYEE",

          "accountLocked": false,

          "accountLockedDate": 0,

          "fatherOrHusbandName": "Hamaal",

          "signature": "",

          "bloodGroup": "O+",

          "photo": "photo1",

          "identificationMark": null,

          "createdBy": 32,

          "lastModifiedBy": 32,

          "tenantId": "pb.citya",

          "roles": [

              {

                  "code": "SUPERUSER",

                  "tenantId": "pb"

              }

          ],

          "uuid": "1fae1f10-f398-4d05-83f5-7457a946aef9",

          "createdDate": "22-05-2019 12:49:07",

          "lastModifiedDate": "22-05-2019 12:49:07",

          "dob": "03/08/1971",

          "pwdExpiryDate": "20-08-2020 12:49:07"

      }

}
```

**Online Payment Gateway Integration :**

Refer to the following link for documentation:&#x20;

{% embed url="https://github.com/egovernments/core-services/blob/master/egov-pg-service/Readme.md" %}

**SMS Gateway Integration :**

* Set the below configurations in the **application.properties** file of **egov-notification-sms** service&#x20;
* Below configuration holds service provider details.
* \---------------------------

**application.properties**

* \---------------------------------------

sms.enabled=true

sms.provider.url=http://placeholder

sms.sender.username=placeholder

sms.sender.password=placeholder

sms.sender=placeholder

\#Parameter names are kept compatible with sms service provider(SMSCountry gateway).&#x20;

sms.sender.req.param.name=sid

sms.sender.username.req.param.name=user

sms.sender.password.req.param.name=passwd

sms.destination.mobile.req.param.name=mobilenumber

sms.message.req.param.name=message

sms.extra.req.params=smsservicetype=singlemsg

sms.error.codes=401,403,404,405,406,407,408,409,410,411,412,413,414

\#SMS priority settings if available

sms.priority.enabled=false

sms.priority.param.name=

sms.high.priority.param.value=

sms.medium.priority.param.value=

sms.low.priority.param.value=



sms.verify.response = false

sms.verify.responseContains=Message submitted successfully

sms.verify.ssl = false

sms.url.dont\_encode\_url = true



\# POST or GET requests

sms.sender.requestType=POST

* Add the below environment variables to your egov-user deployment. This will enable your login without OTP.&#x20;

&#x20;     CITIZEN\_LOGIN\_PASSWORD\_OTP\_FIXED\_VALUE:       123456

&#x20;     CITIZEN\_LOGIN\_PASSWORD\_OTP\_FIXED\_ENABLED:     true

### **Implementation Kit Usage Steps**

**Pre-requisites:**

* Install the Python 3.7.0 version using the following link (cannot be installed in Windows version older than Windows XP):[ https://www.python.org/downloads/](https://www.python.org/downloads/)\
  Set Python environment variables and Path using the following help doc:[ https://docs.python.org/3/using/windows.html](https://docs.python.org/3/using/windows.html)
* Clone the implementation kit repo using the following link:

{% embed url="https://github.com/egovernments/digit-implementation-kit" %}
