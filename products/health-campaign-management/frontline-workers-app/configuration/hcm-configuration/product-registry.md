# Product Registry

## Overview

The product service helps and provides APIs to create products and product variants to the HCM. This document provides the configuration details for setting up products and product variants.

## Pre-requisites

* Knowledge of Java/J2EE (preferably Java 8 version).
* Knowledge of spring boot and spring-boot micro-services.
* Knowledge of Git or any version control system.
* Knowledge of RESTful web services.
* Knowledge of the Lombok library is helpful.
* Knowledge of eGov-mdms service, eGov-persister, eGov-idgen, eGov-indexer, and eGov-user will be helpful.

## Functionalities

1. Provides APIs to create, update, and search products.
2. Provides APIs to create, update, and search product variants.

### Setup details

The source code for a [Product](https://github.com/egovernments/health-campaign-services/tree/v1.1.0/health-services/product) is present in the health-campaign-services Git repo. The spring boot application needs the Lombok\* extension added to the IDE to load it. Once the application is up and running, the API requests can be posted to the URL and the IDs can be generated.

**\***In the case of IntelliJ, the plugin can be installed directly. For eclipse, the Lombok jar location has to be added in the eclipse.ini file in this format javaagent:lombok.jar.

## API details

Refer to the Swagger API for YAML file details: [Product.yaml](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/docs/health-api-specs/contracts/registries/product.yml)

**Application.properties file information**_**:**_

Kafka topics persister configs for eGov persister

```
product.kafka.create.topic=save-product-topic
product.kafka.update.topic=update-product-topic
product.variant.kafka.create.topic=save-product-variant-topic
product.variant.kafka.update.topic=update-product-variant-topic

```

#### URLs for the external API references:

* eGvo mdms :-> egov.mdms.host =[ https://health-dev.digit.org](https://health-dev.digit.org)/
* eGov -idGen :-> egov.idgen.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)
* eGov-User Service -> egov.user.host =[ ](https://health-dev.digit.org)[https://health-dev.digit.org/](https://health-dev.digit.org/)

## Configuration details

#### Access MDMS configurations

**Action test: URL actions adding**

[**Action-test.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)

```
{
 "id": 1536,
 "name": "Product Variant Create",
 "url": "/product/variant/v1/_create",
 "displayName": "Product Variant Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "product",
 "code": "null",
 "path": ""
},
{
 "id": 1537,
 "name": "Product Create",
 "url": "/product/v1/_create",
 "displayName": "Product Create",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "product",
 "code": "null",
 "path": ""
},
{
 "id": 1541,
 "name": "Product Update",
 "url": "/product/v1/_update",
 "displayName": "Product Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "product",
 "code": "null",
 "path": ""
},
{
 "id": 1542,
 "name": "Product Search",
 "url": "/product/v1/_search",
 "displayName": "Product Search",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "product",
 "code": "null",
 "path": ""
},
{
 "id": 1543,
 "name": "Product Variant Update",
 "url": "/product/variant/v1/_update",
 "displayName": "Product Variant Update",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "product",
 "code": "null",
 "path": ""
},
{
 "id": 1544,
 "name": "Product Variant Search",
 "url": "/product/variant/v1/_search",
 "displayName": "Product Variant Search",
 "orderNumber": 0,
 "parentModule": "",
 "enabled": false,
 "serviceCode": "product",
 "code": "null",
 "path": ""
},

```

**Access to role-based actions**

[**Roleaction.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ROLEACTIONS/roleactions.json)

```
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1536,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1537,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1541,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1542,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1543,
 "actioncode": "",
 "tenantId": "default"
},
{
 "rolecode": "SYSTEM_ADMINISTRATOR",
 "actionid": 1544,
 "actioncode": "",
 "tenantId": "default"
}
```

**Persister configuration**

[Product Persister Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-persister/product-persister.yml)

**Indexer configuration**

[Product Indexer Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-indexer/product-indexer.yml)

#### Database schema

<figure><img src="https://lh6.googleusercontent.com/ON9ysxqa544TPaFSB9Ewhh0q72Wmy6vdaJFH0M2jBVPHeJj-blWUu14V9H0LBsDFg-AqeyGhDwICPxlmFaD8908ldxaqWccVMKuiVf0tO7Y0-O0ymutx5XGkzZgByWBnZMyuNQQ0OtVSWhDaI8UNcO0" alt=""><figcaption></figcaption></figure>

**Postman collection**

[https://www.postman.com/lunar-resonance-126497/workspace/hcm/environment/24751924-61d3084a-c7bf-4591-8b7d-2ec5828d96b1](https://www.postman.com/lunar-resonance-126497/workspace/hcm/environment/24751924-61d3084a-c7bf-4591-8b7d-2ec5828d96b1)

[\
](https://github.com/egovernments/health-campaign-services/blob/demo/health-services/individual/src/main/resources/individual-persister.yml)[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
