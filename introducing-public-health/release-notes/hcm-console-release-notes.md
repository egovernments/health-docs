---
description: HCM Console v1.0
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/introducing-public-health/release-notes
---

# HCM Console Release Notes

## **Release Summary**

The HCM Console v1.0 release is the first version to support end-to-end campaign configuration across multiple operational modules. Earlier Console versions supported Bednet campaigns with limited configuration flows.

Console v1.0 continues to support Bednet campaigns and extends the Console to enable full configuration for additional campaign types, including SMC and selected NTD programs (for example, Onchocerciasis). Partners can now configure complete campaigns—covering registration, delivery, inventory, complaints, and referrals—directly through the Console, without engineering involvement.

The focus of this release is to move campaign setup from custom development to a configuration-driven, self-serve model, reducing setup time and improving consistency across campaigns.

**Scope**

* Refer to the [Capabilities](hcm-console-release-notes.md#new-capabilities) section to browse the features that are now configurable via the Console.

**Out of scope**

* Infrastructure and deployment changes
* External system integrations (for example, DHIS2, payments)<br>

***

## **New Capabilities**

HCM Console v1.0 significantly expands the scope of the Console while retaining support for existing campaign types.

#### **End-to-End Campaign Configuration**

1. Full campaign setup can now be completed through the Console without engineering support.
2. Covers the complete lifecycle across enabled modules.

#### Expanded Campaign Coverage

1. Continued support for Bednet campaigns.
2. New support for configuring additional campaign types, including:
   1. SMC
   2. Selected NTD campaigns (for example, Onchocerciasis)

#### Multi-Module Configuration

The console enables multiple modules to be configured, which is required for a campaign. Below are the modules that can be configured using the HCM console:

* Registration
* Delivery
* Inventory
* Complaints
* Referral

## **Enhancements**

#### App Configuration Enhancements

* Configure multi-screen forms across modules.
* Add, remove, and reorder fields.
* Define field-level validations and dependencies.
* Configure reusable structures where applicable.
* Localise labels and content for multiple languages.

#### Templates and Reuse

* Use pre-built templates for common campaign types - such as Bednets, SMC, and NTD (e.g., Onchocerciasis)- to accelerate campaign setup.
* Clone existing campaigns to reuse configurations across rounds or geographies.

**Not configurable via Console v1.0**

* Attendance configuration
* Enumeration setup
* Transit Post campaign setup
* Peer-to-peer data sharing
* Microplanning
