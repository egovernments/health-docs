# Product Registry

## Overview

The product registry provides APIs to create products and product variants for HCM. This document provides the configuration details for setting up products and product variants.

## Pre-requisites

* Knowledge of Java/J2EE (preferably Java 8 version).
* Knowledge of Spring Boot and Spring Boot microservices.
* Knowledge of Git or any version control system.
* Knowledge of RESTful web services.
* Knowledge of the Lombok library is helpful.
* Knowledge of eGov-mdms service, eGov-persister, eGov-idgen, eGov-indexer, and eGov-user will be helpful.

## Functionalities

1. Provides APIs to create, update, and search products.
2. Provides APIs to create, update, and search product variants.

## **Setup**&#x20;

{% stepper %}
{% step %}
### Clone or download the code from the GitHub repository

The source code for the Product registry is located in the [Git repository here](https://github.com/egovernments/health-campaign-services/tree/v1.1.0/health-services/product). Clone or download the code from this repository before proceeding.
{% endstep %}

{% step %}
### Add the Lombok extension/plugin&#x20;

The Product registry is a Spring Boot application that uses Lombok, a Java library. Add the Lombok extension/plugin to open and build the project in your IDE (like IntelliJ or Eclipse).
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

## API

Refer to the Swagger API for YAML file details: [Product.yaml](https://github.com/egovernments/health-campaign-services/blob/v1.1.0/docs/health-api-specs/contracts/registries/product.yml)

**Application.properties file information**_**:**_

Kafka topics persister configs for eGov persister

```
product.kafka.create.topic=save-product-topic
product.kafka.update.topic=update-product-topic
product.variant.kafka.create.topic=save-product-variant-topic
product.variant.kafka.update.topic=update-product-variant-topic

```

### External Service URLs

Below are the URLs for external services that the Product registry interacts with:

| Service            | Property Key    | URL                                                          |
| ------------------ | --------------- | ------------------------------------------------------------ |
| eGov MDMS          | egov.mdms.host  | [https://health-dev.digit.org](https://health-dev.digit.org) |
| eGov ID Generation | egov.idgen.host | [https://health-dev.digit.org](https://health-dev.digit.org) |
| User Service       | egov.user.host  | [https://health-dev.digit.org](https://health-dev.digit.org) |

## Configuration Details

Follow the details outlined below to configure and enable Product registry API actions and access control using MDMS, role-action mapping, persister, and indexer configurations.

### **MDMS Configurations**

#### Define Action URLs

Add new actions in the MDMS actions configuration (e.g., `action-test.json`). Each action represents an API endpoint you wish to secure and manage: [**Action-test.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ACTIONS-TEST/actions-test.json)

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

#### Assign Actions to Roles

Configure which user roles can access which API actions in `roleaction.json`. Map each action ID to the required roles: [**Roleaction.json**](https://github.com/egovernments/health-campaign-mdms/blob/v1.1.0/data/default/ACCESSCONTROL-ROLEACTIONS/roleactions.json)**.** Refer example below:

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

## **Persister Configuration**

[Product Persister Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-persister/product-persister.yml)

## **Indexer Configuration**

[Product Indexer Yaml](https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-indexer/product-indexer.yml)

## Database Schema

<figure><img src="https://lh6.googleusercontent.com/ON9ysxqa544TPaFSB9Ewhh0q72Wmy6vdaJFH0M2jBVPHeJj-blWUu14V9H0LBsDFg-AqeyGhDwICPxlmFaD8908ldxaqWccVMKuiVf0tO7Y0-O0ymutx5XGkzZgByWBnZMyuNQQ0OtVSWhDaI8UNcO0" alt=""><figcaption></figcaption></figure>

## **Postman Collection**

[**Link**](https://www.postman.com/lunar-resonance-126497/workspace/hcm/environment/24751924-61d3084a-c7bf-4591-8b7d-2ec5828d96b1)
