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

<figure><img src="../../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

### Components Overview

| Component             | Description                                                       |
| --------------------- | ----------------------------------------------------------------- |
| Campaign Service      | Core backend service to manage campaign lifecycle                 |
| Survey Service        | Enables survey creation, scheduling, and data collection          |
| Notification Service  | Supports citizen/staff outreach via SMS, IVR, or digital channels |
| Workflow Engine       | Orchestrates the approval and campaign progression states         |
| Analytics Module      | Collects and visualizes campaign progress and outcomes            |
| Registry Integrations | Interfaces with Facility, Staff, and Health registries            |
| Mobile/Web Frontends  | Interfaces for field workers, supervisors, and administrators     |

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

| Entity    | Description                                  |
| --------- | -------------------------------------------- |
| Campaign  | Metadata including type, target groups, area |
| Survey    | Questions and structure tailored to campaign |
| Responses | Data collected from field execution          |
| User      | Health worker, supervisor, admin roles       |

***

## **Technology Stack**

| Layer         | Technology                     |
| ------------- | ------------------------------ |
| Frontend      | React / Mobile App Framework   |
| Backend       | Java Spring Boot Microservices |
| Messaging     | Apache Kafka                   |
| Workflow      | DIGIT Workflow Engine          |
| Database      | PostgreSQL / ElasticSearch     |
| Deployment    | Docker, Kubernetes             |
| Infra-as-Code | Terraform                      |

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

| Risk                              | Impact                        | Mitigation                                         |
| --------------------------------- | ----------------------------- | -------------------------------------------------- |
| Internet Unavailability in Fields | Delayed data sync             | Offline data capture support                       |
| Workflow Misconfiguration         | Blocked campaign progress     | Pre-deployment validations and sandbox environment |
| Incomplete Registry Data          | Inaccurate campaign targeting | Periodic registry audits and fallback mechanisms   |

***
