# Release Notes

## Release Summary

HCM v2.0 delivers a major step forward in scalability, usability, and operational efficiency. The platform now supports secure BYOD operations with app-level protection, end-to-end campaign configuration through Console v1.0, and periodic wage disbursement during active campaigns via Payment advice v2.0. It also enables supervisor-led, self-service attendance management, seamless referral tracking between distributors and facilities, and an enhanced Complaints Management System (CMS) module for improved transparency and control. Intoduced a unified Excel template for microplan ingestion, enabling the upload of facility details, boundary details, and user data through a single sheet. This eliminates the need to manage multiple upload and download cycles, thereby improving efficiency and user experience.

Alongside these, several targeted enhancements improve reliability, visibility, and user experience for field and administrative users.

## New Capabilities

### 1. Enhanced BYOD Support in HCM

**What’s new**\
HCM now offers an improved BYOD (Bring Your Own Device) deployment model, allowing field users to securely use the HCM mobile application on their personal smartphones — alongside existing MDM-managed device setups.

To ensure enterprise-grade security on personal devices, we have introduced:

* **App-level data encryption** to protect sensitive campaign data
* **Screenshot and screen recording restrictions**
* **Secure authentication and controlled access mechanisms**
* **Device compatibility checks** (OS version, RAM, storage validation)

These enhancements ensure that program data remains protected without requiring full device-level control or ownership.

**Why it matters**

Traditional program-owned, MDM-managed devices come with high costs and operational complexity, including procurement, licensing, maintenance, and logistics.

With enhanced BYOD support, programs can now:

* Reduce device procurement costs (≈ USD 1,400 per device)
* Eliminate recurring MDM licensing costs (≈ USD 8 per device annually)
* Lower logistics and transportation overhead (≈ USD 200 per device)
* Accelerate field user onboarding
* Enable faster campaign rollouts
* Improve scalability for large or concurrent campaigns

**How it works**

* Secure login and app-level data protection on personal devices
* Compatibility checks at the app level (OS version, RAM, storage)
* No dependency on device ownership or full device-level control

### 2. Downsync in Referral Flow

**What’s new**\
HCM now supports **ID-based downsync in the referral workflow**, enabling seamless data continuity between distributors and health facilities.

**Why it matters**\
Previously, there was no reliable way to track whether referred beneficiaries reached health facilities. This resulted in poor visibility, duplicate registrations, and fragmented workflows between distributors and facility staff.

**How it works**

* Referred beneficiary data is **upsynced** from distributor devices
* Health Facility Officers can **downsync referred beneficiaries** at login
* Beneficiary data is stored locally for online and offline access
* Search using a unique **8-character alphanumeric referral ID**
* Referral ID is auto-populated and non-editable at the facility
* Supports cross-LGA, relocation, and offline referral scenarios
* Referral status is automatically updated back to the distributor once completed

**Impact**

* End-to-end visibility of referrals and facility footfall
* Prevents duplicate beneficiary registrations
* Reduces manual data entry at health facilities
* Enables follow-up for beneficiaries who do not reach facilities
* Creates a reusable and scalable referral mechanism across campaigns

### 3. Enhanced Complaints Management&#x20;

**What’s new**\
The Complaints Management has been significantly enhanced to address usability gaps, functional issues, and scalability limitations.

**Why it matters**\
Earlier limitations around boundary visibility, pagination, status handling, and attachments slowed complaint management and reduced transparency.

**What’s improved**

* Boundary-based complaint visibility aligned with user access
* Fixed pagination and dropdown issues in complaint search
* Correct and consistent handling of complaint statuses
* New workflow status: **Assigned**, with a dedicated filter
* Support for media attachments during complaint creation and updates
* Display of boundary hierarchy (highest to lowest level) for better assignment context
* Evaluation of replacing SLA with Created Date in search views

**Impact**

* Faster and more intuitive complaint search and navigation
* Clearer ownership and lifecycle tracking
* Improved transparency through boundary-aware visibility
* Better documentation using attachments
* Reduced manual effort in complaint assignment and management

### 4. [End-to-End Campaign Configuration (Console v1.0)](hcm-console-release-notes.md)

HCM Console v1.0 introduces end-to-end campaign configuration across multiple operational modules, moving beyond limited Bednet-only flows to support additional campaign types, including SMC and selected NTD programmes (e.g., Onchocerciasis). It enables partners to configure complete campaigns—covering registration, delivery, inventory, complaints, and referrals—directly in the Console, without involving the technical team, thereby shifting to a configuration-driven, self-serve model that reduces setup time and improves consistency.

**Key Highlights:**

* End-to-end campaign setup through the Console
* Expanded support for more campaign types, such as Bednet, SMC or selected NTD campaigns
* Multi-module configuration: Registration, Delivery, Inventory, Complaints, Referral
* Advanced form configuration for the mobile application screens (multi-screen forms, validations, field dependencies, localisation)
* Template-based setup and campaign cloning for reuse
* Unified Excel template for microplan ingestion, enabling the upload of facility details, boundary details, and user data through a single sheet

### 5. [Payment Advice v2.0 – Periodic Wage Disbursement](payments-v2.0-release-notes.md)

Payment advice v2 enhances the HCM Payments module by enabling periodic wage disbursement during active campaigns, improving transparency, operational control, and audit readiness. It reduces payment delays and manual tracking through intermediate billing, UI-based payment configuration, KPI dashboards, and stronger validation controls—while remaining compatible with end-of-campaign workflows.

**Key Highlights:**

* Periodic (weekly/monthly/custom) bill generation during active campaigns
* Sequential billing enforcement with overlap prevention
* Campaign-level payment configuration via UI (billing cycles and role-based wages)
* Supervisor and payment approver KPI dashboards with period-based controls
* Strong attendance and billing validations aligned to payment cycles
* Audit logging for payment configuration and bill generation
* UI improvements for billing-aligned attendance review and clearer status tracking

### 6. [Register Management Through HCM](register-management-release-notes.md)

This release enhances the Attendance module by enabling supervisors to manage attendance registers without backend dependency. Supervisors can now edit registers, add or disable users, and maintain accurate register composition in real time—ensuring attendance data remains aligned with billing and payment workflows while improving speed, control, and audit readiness.

**Key Highlights:**

* Supervisor-led register management directly via UI
* Add existing or new users through the integrated HRMS flow
* Disable users in the middle of a campaign while retaining attendance history
* Clear register metadata visibility (campaign, boundary, duration, ownership)
* Strong validation rules to prevent duplicate users and register conflicts
* Maintains alignment between attendance, billing, and payments

## Enhancements

* Stronger data continuity across distributor and facility workflows
* Better scalability for multi-campaign and large-scale deployments
* Improved UI console

## Document Resources & Links

<table><thead><tr><th width="333.30859375">Functional Documents</th><th>Technical Documents</th></tr></thead><tbody><tr><td><ol><li><a href="hcm-console-release-notes.md">Console Release Notes </a></li><li><a href="payments-v2.0-release-notes.md">Payments Release Notes </a></li><li><a href="register-management-release-notes.md">Register Management Release Notes</a></li><li><a href="../../access/public-health-product-suite/health-campaign-management-hcm/hcm-user-manual/">HCM Console User Manual</a></li></ol></td><td><ol><li><a href="../../design/architecture/low-level-design/services/admin-console/">HCM Admin Console Design </a></li><li><a href="../../deploy/configuration/hcm-console-configuration/">HCM Console Configuration</a></li><li><a href="../../deploy/configuration/hcm-console-configuration/digit-frontend-react-19-upgrade.md">DIGIT Front End React 19 Upgrade</a></li><li><a href="../../deploy/configuration/hcm-console-configuration/project-factory-configuration.md">Project Factory Configuration</a></li><li><a href="../../deploy/configuration/hcm-console-configuration/excel-ingestion-configuration.md">Excel Ingestion Configuration</a></li><li><a href="../../deploy/configuration/hcm-console-configuration/enable-new-campaign-type/">Enable new campaign type</a></li><li><a href="../../design/architecture/field-app-architecture/ui-packages/digit-flow-builder.md">DIGIT Flow Builder</a></li><li><a href="../../design/architecture/field-app-architecture/ui-packages/digit-form-engine.md">DIGIT Form Engine</a></li><li><a href="../../design/architecture/field-app-architecture/ui-packages/digit-formula-parser.md">DIGIT Formula Parser</a></li><li><a href="../../design/architecture/field-app-architecture/ui-packages/digit-crud-bloc.md">DIGIT CRUD Bloc</a></li><li><a href="../../design/security.md">Design -Security</a></li></ol></td></tr></tbody></table>
