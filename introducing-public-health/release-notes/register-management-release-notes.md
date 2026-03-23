# Register Management Release Notes

## Release Summary

This release enhances the Attendance module by enabling **field supervisors to independently manage attendance registers** without backend dependency. Supervisors can now edit registers in real time, onboard and disable users directly from HCM, and clearly understand register ownership and composition.

These improvements reduce operational delays, improve adoption, and ensure attendance data remains accurate and fully aligned with downstream **billing and payment workflows**.

{% hint style="info" %}
This release makes **register management faster, safer, and fully self-service**, enabling supervisors to respond quickly to on-ground changes while keeping attendance and payment data reliable and audit-ready.
{% endhint %}

#### In Scope

* Supervisor-led management of attendance registers
* Adding existing or new users directly to registers
* Disabling users mid-campaign while retaining attendance history
* Validation rules to prevent duplicate users and register conflicts

#### Out of Scope

* Multi-team assignment for users (e.g user in two team codes)
* Geo-fencing or GPS validation of register locations
* Real-time sync of register changes during ongoing marking
* Role change impact mid-campaign (e.g CDD  TS)
* Allow cross-boundary supervision(edge case) - The team code may exist in multiple boundaries (e.g TS Megha owns TC001 in village A and TC007 in village B)
* Mobile UI for the supervisor to add folks to the register

## New Capabilities

#### 1. Supervisor-Managed Attendance Registers

**What’s new**\
Proximity Supervisors can now manage attendance registers directly from the UI.

**Key capabilities**

* Edit registers without backend intervention
* View rich register metadata, including:
  * Register ID
  * Campaign and project details
  * Boundary information
  * Event duration
  * Supervisor and attendance officer details
  * Dynamic attendee count

**Impact**

* Eliminates dependency on support teams
* Speeds up operational changes in the field
* Improves clarity around register ownership and scope

#### 2. Add & Register Users Directly from HCM

**What’s new**\
Supervisors can add both **existing and new users** directly to attendance registers.

**How it works**

* Search and add existing users to a register
* Register new users through the integrated HRMS flow
* Newly created users are immediately assigned to the register with:
  * Correct enrolment date
  * Boundary-level validation

**User experience**

* Clear success and error toasts guide supervisors through the process

**Impact**

* Faster onboarding of field staff
* Reduced setup delays during campaign execution
* Ensures accurate and validated register composition

#### 3. Disable Users Without Losing Attendance History

**What’s new**\
Supervisors can safely disable users from the registers during an active campaign.

**Key rules**

* Disabled users:
  * Cannot be re-enabled in the same register
  * Are visually tagged and moved to the bottom of the list
  * Remain included in attendance and payment calculations
* Disabling is blocked if the user data has not yet synced

**Impact**

* Maintains data integrity for attendance and payments
* Prevents accidental loss of historical records
* Provides clear visibility into active vs inactive participants

## Enhancements

#### Strong Validations & Conflict Prevention

The system enforces robust validation rules to avoid register inconsistencies:

* Prevents adding users who are active in another register
* Blocks duplicate mobile numbers
* Restricts multiple users without Team Codes
* Prevents conflicting Team Codes within the same boundary
* Displays clear, actionable error messages when constraints are violated

**Impact**

* Ensures clean, conflict-free attendance data
* Reduces downstream billing and payment errors
* Improves confidence in supervisor-led register management
