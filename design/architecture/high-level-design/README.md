# High Level Design

## **Overview**

The Health Campaign System provides:

* **Campaign Configuration**: Create and manage different health campaigns with specific attributes and goals.
* **Survey Management**: Define and assign surveys tailored to each campaign.
* **Progress Monitoring**: Enable real-time data collection and tracking via dashboards.
* **Integration Support**: Connects with other DIGIT modules (like Health Registry, Facility Registry) and third-party systems.

***

## **Architectural Design**

### Architecture Diagram

<figure><img src="../../../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

### Components Overview

<table><thead><tr><th width="212.6953125">Component</th><th>Description</th></tr></thead><tbody><tr><td>Campaign Service</td><td>Core backend service to manage campaign lifecycle</td></tr><tr><td>Survey Service</td><td>Enables survey creation, scheduling, and data collection</td></tr><tr><td>Notification Service</td><td>Supports citizen/staff outreach via SMS, IVR, or digital channels</td></tr><tr><td>Workflow Engine</td><td>Orchestrates the approval and campaign progression states</td></tr><tr><td>Analytics Module</td><td>Collects and visualizes campaign progress and outcomes</td></tr><tr><td>Registry Integrations</td><td>Interfaces with Facility, Staff, and Health registries</td></tr><tr><td>Mobile/Web Frontends</td><td>Interfaces for field workers, supervisors, and administrators</td></tr></tbody></table>

***

## **Design Considerations**

* **Security**: Role-based access control for different user types (field staff, admin, supervisors). Data encryption in transit and at rest.
* **Scalability**: Built on DIGIT Core microservices, supporting large-scale deployments across districts/states.
* **Extensibility**: Config-driven campaign types, reusable workflows, and pluggable registries.
* **Offline Support**: Field apps support offline data collection and sync.

***

## **Data Design**

### High-Level Data Flow

1. Admin configures a campaign.
2. Surveys are created and assigned to health workers.
3. Data collected in the field is synced to the backend.
4. Dashboards and analytics display progress and coverage.

### Key Data Entities

<table><thead><tr><th width="236.51953125">Entity</th><th>Description</th></tr></thead><tbody><tr><td>Campaign</td><td>Metadata including type, target groups, area</td></tr><tr><td>Survey</td><td>Questions and structure tailored to campaign</td></tr><tr><td>Responses</td><td>Data collected from field execution</td></tr><tr><td>User</td><td>Health worker, supervisor, admin roles</td></tr></tbody></table>

***

## **Technology Stack**

<table><thead><tr><th width="242.19921875">Layer</th><th>Technology</th></tr></thead><tbody><tr><td>Frontend</td><td>React / Mobile App Framework</td></tr><tr><td>Backend</td><td>Java Spring Boot Microservices</td></tr><tr><td>Messaging</td><td>Apache Kafka</td></tr><tr><td>Workflow</td><td>DIGIT Workflow Engine</td></tr><tr><td>Database</td><td>PostgreSQL / ElasticSearch</td></tr><tr><td>Deployment</td><td>Docker, Kubernetes</td></tr><tr><td>Infra-as-Code</td><td>Terraform</td></tr></tbody></table>

***

## **Deployment Architecture**

The solution is deployed using Kubernetes clusters managed via Helm and Terraform. It supports multi-environment setups (dev, staging, production). Key services are containerised, and CI/CD is managed via GitHub Actions.

***

## **Assumptions & Dependencies**

* Facility, Staff, and User registries are available and populated.
* Campaign types and workflows are pre-configured by the admin.
* Field devices have intermittent internet access to support data sync.

***

## **Risks & Mitigation**

<table><thead><tr><th width="222.61328125">Risk</th><th width="224.046875">Impact</th><th>Mitigation</th></tr></thead><tbody><tr><td>Internet Unavailability in Fields</td><td>Delayed data sync</td><td>Offline data capture support</td></tr><tr><td>Workflow Misconfiguration</td><td>Blocked campaign progress</td><td>Pre-deployment validations and sandbox environment</td></tr><tr><td>Incomplete Registry Data</td><td>Inaccurate campaign targeting</td><td>Periodic registry audits and fallback mechanisms</td></tr></tbody></table>

***
