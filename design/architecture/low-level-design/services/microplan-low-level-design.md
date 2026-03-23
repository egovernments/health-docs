# Microplan - Low Level Design

## Overview

The Low Level Design (LLD) details on this page provide a detailed technical blueprint for implementing the **Microplanning** system. It translates functional requirements into concrete technical components, including APIs, service responsibilities, sequence flows, and database schemas.

The LLD covers:

* Internal architecture of Microplanning services
* API specifications at a component level
* Asynchronous processing flows
* Sequence diagrams for key workflows
* Database schema design and entity relationships

## System Overview

The Microplanning system enables planning, estimation, and allocation of resources across administrative units, employees, and facilities. It is composed of two core backend services:

1. **Resource Generator Service** – Responsible for generating resource estimations asynchronously.
2. **Plan Management Service** – Manages the lifecycle of micro plans, including configuration, assignments, validation, and approval.

Both services follow DIGIT’s event-driven, microservices-based architecture.

## Resource Management <a href="#overview" id="overview"></a>

The Draft API is part of the **Resource Generator Service**. It initiates the resource estimation process for a given micro plan configuration.

**Key Characteristics**

* Fully asynchronous processing
* Designed for large datasets
* Non-blocking client interaction

**Processing Flow**

1. Client invokes Draft API with plan configuration reference
2. Request is validated and accepted
3. The estimation job is triggered asynchronously
4. Input data is parsed and business logic applied
5. Output file is generated and uploaded to File Store
6. Plan configuration is updated with estimation metadata

### API Specification <a href="#api-specification" id="api-specification"></a>

​[Resource Generator API Specification](https://github.com/egovernments/DIGIT-Specs/blob/grouped-service-contracts/Domain%20Services/Resource%20Generator/resource-1.0.0.yaml)&#x20;

​​[Postman Collection](https://api.postman.com/collections/13428435-c702603a-b3c5-4954-9f67-17c06e41d225?access_key=PMAT-01JRA0QCZE111Z3JQSM4R8KZEP)​

### Sequence Diagrams <a href="#sequence-diagrams" id="sequence-diagrams"></a>

#### Draft API <a href="#draft-api" id="draft-api"></a>

<figure><img src="../../../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

## Plan Management

The Plan Management Service handles the complete lifecycle of micro plans, including:

* Micro plan creation and configuration
* Employee assignment to plans
* Facility linkage
* Validation and approval of estimations

Key Characteristics

**Plan Configuration**

* Create and update micro plans
* Store administrative hierarchy and planning parameters

**Plan Employee Assignment**

* Assign employees to micro plans
* Validate role and jurisdiction alignment

**Plan Facility Linkage**

* Link facilities (e.g., schools, health centres) to plans
* Support one-to-many and many-to-many mappings

**Plan Estimation Management**

* Store estimation references
* Track draft vs approved estimations

**Validation & Approval**

* Rule-based validation of estimation data
* Approval workflows for finalised plans

### API Specification

[Plan Management API Specification](https://github.com/egovernments/DIGIT-Specs/blob/grouped-service-contracts/Domain%20Services/Plan%20Service/plan-1.0.0.yaml)

### Sequence Diagrams

#### Plan Configuration APIs

<figure><img src="../../../../.gitbook/assets/image (64).png" alt=""><figcaption><p><em>Plan Configuration Create API Sequence Diagram</em></p></figcaption></figure>

<div align="left"><figure><img src="../../../../.gitbook/assets/image (65).png" alt=""><figcaption><p><em>Plan Configuration Search API Sequence Diagram</em></p></figcaption></figure></div>

<figure><img src="../../../../.gitbook/assets/image (66).png" alt=""><figcaption><p><em>Plan Configuration Update API Sequence Diagram</em></p></figcaption></figure>

### Plan Employee Assignment APIs

<figure><img src="../../../../.gitbook/assets/image (67).png" alt=""><figcaption><p><em>Plan Employee Assignment Create API Sequence Diagram</em></p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (68).png" alt=""><figcaption><p><em>Plan Employee Assignment Search API Sequence Diagram</em></p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (69).png" alt=""><figcaption><p><em>Plan Employee Assignment Update API Sequence Diagram</em></p></figcaption></figure>

### Plan Facility APIs

<figure><img src="../../../../.gitbook/assets/image (70).png" alt=""><figcaption><p><em>Plan Facility Create API Sequence Diagram</em></p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (71).png" alt=""><figcaption><p><em>Plan Facility Search API Sequence Diagram</em></p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (72).png" alt=""><figcaption><p><em>Plan Facility Update API Sequence Diagram</em></p></figcaption></figure>

### Plan Management APIs

<figure><img src="../../../../.gitbook/assets/image (73).png" alt=""><figcaption><p><em>Plan Create API Sequence Diagram</em></p></figcaption></figure>

<div align="left"><figure><img src="../../../../.gitbook/assets/image (74).png" alt=""><figcaption><p><em>Plan Search API Sequence Diagram</em></p></figcaption></figure></div>

<figure><img src="../../../../.gitbook/assets/image (75).png" alt=""><figcaption><p><em>Plan Update API Sequence Diagram</em></p></figcaption></figure>

## Database Schemas

<figure><img src="../../../../.gitbook/assets/image (76).png" alt=""><figcaption><p><em>Plan Configuration Database Schema</em></p></figcaption></figure>

<div align="left"><figure><img src="../../../../.gitbook/assets/image (77).png" alt=""><figcaption><p><em>Plan Employee Assignment Database Schema</em></p></figcaption></figure></div>

<div align="left"><figure><img src="../../../../.gitbook/assets/image (78).png" alt=""><figcaption><p><em>Plan Facility Database Schema</em></p></figcaption></figure></div>

<figure><img src="../../../../.gitbook/assets/image (81).png" alt=""><figcaption><p><em>Plan Database Schema</em></p></figcaption></figure>

## Census Management

### Overview

The **Census Management Service** is responsible for managing population census data used as a key input for microplanning and resource estimation. It supports capture, validation, approval, and versioning of census data across administrative hierarchies.

Census data acts as a foundational dataset for estimation logic and must pass through defined validation and approval workflows before it can be consumed by downstream services such as the Resource Generator.

**Key Characteristics**

* Capture population census data at multiple administrative levels
* Maintain draft and approved versions of census datasets
* Validate census data against configured rules
* Support approval workflows for finalised census data
* Expose approved census data to dependent services

### API Specifications

[Census Management API Specification](https://github.com/egovernments/DIGIT-Specs/blob/grouped-service-contracts/Domain%20Services/Census/census-v1.0.0.yaml)

### Sequence Diagrams <a href="#sequence-diagrams" id="sequence-diagrams"></a>

#### Census Management APIs <a href="#census-management-apis" id="census-management-apis"></a>

<figure><img src="../../../../.gitbook/assets/image (56).png" alt=""><figcaption><p><em>Census Create API Sequence Diagram</em></p></figcaption></figure>

<br>

<div align="left"><figure><img src="../../../../.gitbook/assets/image (57).png" alt=""><figcaption><p><em>Census Search API Sequence Diagram</em></p></figcaption></figure></div>

<figure><img src="../../../../.gitbook/assets/image (58).png" alt=""><figcaption><p><em>Census Update API Sequence Diagram</em></p></figcaption></figure>

### Database Schemas

<figure><img src="../../../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>
