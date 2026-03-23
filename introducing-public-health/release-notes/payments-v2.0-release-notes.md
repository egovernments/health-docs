# Payments v2.0 Release Notes

## Release Summary

Payments v2.0 strengthens the HCM Payments module by enabling **timely, periodic wage disbursement during active campaigns** while improving operational visibility for supervisors and payment approvers.\
Payments can be made at different stages of a campaign, such as training, registration, service delivery, and stock management. Payments can also be processed either during the campaign at regular intervals, or after the campaign ends.\
This release helps reduce payment delays, avoids manual tracking, and makes the process more transparent through intermediate bill generation, campaign-level payment setup in the UI, and simple in-module KPIs, while still supporting the existing end-of-campaign payment process.

{% hint style="info" %}
In short, Payments v2 significantly improves **payment timeliness, transparency, and operational control**, making it easier to manage wages accurately during long-running campaigns while maintaining strong audit and governance standards.
{% endhint %}

#### In Scope

* Periodic (intermediate) bill generation during active campaigns
* Campaign-level payment setup via UI (billing cycles and role-based wages)
* Attendance and billing period validations
* Audit logging for payment configuration and bill generation
* UI enhancements to support period-based attendance review and billing
  * Billing period can be set weekly (every 7 days), every 10 days, fortnightly (15 days), monthly (30 days), or end of campaign.
  * Supervisors review and approve attendance only for the current period, and payments are calculated for that specific period.

#### Out of Scope

* Geography-based wage differentiation
* Holiday/break handling in wage calculations
* Performance-based incentives and proof-of-work checks
* Multi-level approval workflows
* Payment disbursement integrations (banks/MMOs)
* Notifications (SMS / in-app), wallet management, KYC, fraud detection
* Bulk uploads and role/permission changes
* Operational metrics to track payment status<br>

## New Capabilities

#### 1. Intermediate Bill Generation

**What’s new**\
Payments can now be processed **periodically during an ongoing campaign**, instead of waiting until campaign completion.

**How it works**

* Generate bills on a **weekly, monthly, custom, or end-of-campaign** basis
* Bills can be created while the campaign is active
* Sequential billing is enforced (previous cycle must be completed first)
* Prevents overlapping billing periods and duplicate bill generation
* Supports post-campaign consolidated billing for audit and reconciliation

**Impact**

* Enables faster wage disbursement to field staff
* Reduces the accumulation of unpaid attendance over long campaigns
* Improves auditability and financial control

#### 2. Payment Setup using an interface

**What’s new**\
Campaign managers can now configure payment rules directly from the UI during campaign setup.

**Configuration options**

* Billing frequency (weekly, monthly, custom, end-of-campaign)
* Role-based wage configuration

**Key controls**

* Payment configuration is **locked once the campaign starts**
* All configuration changes are **audit logged**

**Impact**

* Eliminates dependency on the technical team for configuration
* Improves governance and traceability of payment rules
* Ensures consistency across billing cycles (same wages and billing periods across the entire campaign).

## Enhancements

#### Improved Attendance Review & Validation

* Clear display of attendance duration (start date, end date, total days)
* Validation updated to restrict attendance edits to the defined billing period: Supervisors can update attendance only within the current billing period. They cannot modify attendance for days outside that period, so they also cannot enter more days than allowed (e.g., more than 7 days in a weekly cycle).
* Contextual guidance messages when actions from previous cycles are pending

#### Audit & Compliance Improvements

* Audit logging for payment configuration changes
* Audit logging for bill generation events

#### UI Enhancements

* Period-based attendance review
* Billing-aligned navigation and filters
* Clear status indicators for pending and completed actions

<br>
