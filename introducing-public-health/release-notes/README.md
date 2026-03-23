# Release Notes

## **Release Summary**

The **DIGIT HCM v1.8 release** introduces a **Central Instance Deployment Model**—running services for multiple countries (**Mozambique, Liberia, Nigeria**) on a single Kubernetes cluster.\
Data for each country is **securely isolated** at both:

* **Namespace level** (Kubernetes separation)
* **Database schema level** (PostgreSQL schemas)

**Goals:**

* Reduce ongoing maintenance
* Standardise configurations across countries
* Avoid duplication of services
* Still allow country-specific customisations where required
* Save infrastructure costs by leveraging a central instance capability

{% hint style="info" %}
**Note:** This update applies **only** to application-facing services. **Admin Console** and **Micro-Planning services** are not included.
{% endhint %}

***

## **New Capabilities**

#### 1. Admin Console (v0.4)

* **What it is:** A no-code, configurable console.
* **Purpose:** Allows partners and field teams to independently design, localise, and deploy campaigns **without engineering help**.

#### 2. Server-Generated Beneficiary IDs

* **What it is:** Pre-generated Beneficiary IDs created on the server.
* **How it works:** Synced to the app during login.
* **Benefit:** Enables **registry reuse across campaigns** by giving each household/individual a unique ID.

#### 3. Enumeration Tool

* **What it is:** A Tool for capturing household- and individual-level data.
* **Features:** Supports conditional questions and structured relationships (e.g., parent-child).
* **Purpose:** Flexible community health enumeration in areas without standard formats.

#### 4. Transit Tool

* **What it is:** New "Transit Post" campaign mode.
* **Use case:** For locations where pre-enumeration isn’t possible (e.g., bus stops, parks).
* **Purpose:** Records **aggregate counts with location details** instead of individual records.

#### 5. Attendance Proof of Work

* **What it is:** QR Code Scanning for employee attendance.
* **Benefit:** Improves **reliability and accountability** in campaign deployments where supervisor-marked attendance lacked verification.

#### 6. Peer-to-Peer (P2P) Data Sharing

* **What it is:** P2P downsync sharing between devices via Wi-Fi Direct.
* **Purpose:** Enables offline data sharing to keep field work running in **low/no-connectivity** areas.

***

## **Enhancements**

#### 1. Centralised Multi-Tenant Deployment

* Single Kubernetes cluster for Mozambique, Liberia, and Nigeria.
* **Common namespace:** Shared core services (e.g., egov-user, workflow, egov-otp, MDMS V2).
* **Dedicated tenant namespaces:** Country-specific services (e.g., Liberia HRMS, Nigeria HRMS).

#### 2. Multi-Schema Database Support

* Single PostgreSQL instance with separate schemas (public, liberia, nigeria).
* **Automated Flyway migration** using `migrate.sh` for all schemas.
* Schema lists and enablement flags are configurable via Helm & environment YAML.

#### 3. Mobile App Endpoint Segregation

* Separate apps per country (example: Mozambique - mz, Liberia - lb, Nigeria - ng).
* Each app connects to tenant-specific URLs for correct routing.

#### 4. Standardised Kafka Topic Naming

* Tenant-prefixed format prevents collisions.
* Example: `mz-save-household-topic`, `lb-save-household-topic`, `ng-save-household-topic`.

#### 5. Helm & Configuration Improvements

* **Common `values.yml`** for baseline DB/service settings.
* App-specific `values.yml` overrides for schema/multi-schema flags.
* Backwards-compatible for services without multi-schema needs.

#### 6. Centralised Internal Gateway & MDMS v2

* Internal gateway configurations are stored centrally for easier updates.
* MDMS v2 configs consolidated per tenant for **consistent metadata**.

#### 7. Shared vs. Tenant-Specific Services

* **Shared services:** Household, Individual, Stock, Facility, Product, Service Request, Egov-HRMS, Project, Referral.
* **Tenant-specific services:** Deployed only where needed (e.g., Liberia HRMS, Nigeria HRMS).

***

## Document Resources & Links <a href="#document-resources-and-links" id="document-resources-and-links"></a>

| Technical Documents                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Functional Documents                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ol><li><a href="attendance-release-notes.md">Attendance Revamp</a></li><li><a href="migration-guide.md">Migration Guide</a></li><li><a href="../../design/architecture/low-level-design/services/project-factory-campaign-manager/project-factory.md">Project Factory - Campaign Manager</a></li><li><a href="../../design/architecture/low-level-design/services/admin-console/">Admin Console Design Documents</a></li><li><a href="../../design/architecture/low-level-design/services/central-instance.md">Central Instance</a></li><li><a href="../../deploy/configuration/hcm-console-configuration/">HCM Console Configuration</a></li></ol> | <ol><li><a href="../../access/public-health-product-suite/health-campaign-management-hcm/transit-post/transit-post-user-manual.md">Transit Post User Manual</a></li><li><a href="../../access/public-health-product-suite/health-campaign-management-hcm/enumeration-checklist/enumeration-checklist-user-manual.md">Enumeration User Manual</a></li><li><a href="../../access/public-health-product-suite/health-campaign-management-hcm/device-tracking-user-manual.md">Device Tracking User Manual</a></li><li><a href="../../access/public-health-product-suite/health-campaign-management-hcm/peer-to-peer-data-transfer-user-manual.md">Peer to Peer Data Transfer User Man</a>ual</li><li><a href="../../access/public-health-product-suite/health-campaign-management-hcm/attendance-management.md">Attendance Management User Manual</a></li><li><a href="../../access/public-health-product-suite/health-campaign-management-hcm/beneficiary-id/beneficiary-id-user-manual.md">Beneficiary ID User Manual</a></li></ol> |

