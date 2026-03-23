---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/low-level-design/services/attendance/attendance-revamp
---

# Attendance Revamp

## **Overview**

The attendance revamp feature adds a **tagging system** to the attendance module. Tags help categorise and group attendees (e.g., by _Skill, Project, Shift_) and make it easier to search or filter attendance records. To support this, new APIs, search options, validation rules, and database changes have been introduced.

***

## **Key Features**

#### **1. Tagging Capability for Attendees**

* **Tag Field**: A new `tag` field is added to attendees, allowing teams to organise and filter data.
* **Bulk Tag Update API** (`POST /attendee/v1/_updateTag`):
  * Allows you to update tags for multiple attendees at once.
  * Validates attendees, tenant IDs, and tag values to ensure data integrity.
* **Tag Enrichment**:
  * Only updates the tag field while keeping audit info (`createdBy`, `createdTime`) intact.
  * Supports idempotent and partial updates.
* **Validation Rules**:
  * Requires `tenantId` in requests.
  * Attendees must exist in the system before updates.
  * Tags must be valid (non-empty).
  * Prevents cross-tenant updates or invalid inputs.

#### **2. Tag-Based Attendee Search Enhancements**

* **Search with Tags**:
  * Tags can be used as an optional filter in `/attendee/v1/_search`.
  * Multiple tags supported, with **AND/OR filtering**.
* **Model Update**:
  * `AttendeeSearchCriteria` now includes a `tags` field (`List<String>`).
  * `tenantId` is mandatory when searching with tags.

#### **3. Database & Persistence Layer Changes**

* **Schema**:
  * Added a `tag` column to `eg_wms_attendance_attendee`.
  * Indexed for faster searches.
* **Persister Config**:
  * Updated `attendance-service-persister.yml` to handle tags in insert, update, and mapping queries.

#### **4. Service, Repository & Model Enhancements**

* **Service Layer**:
  * New method `updateAttendeeTag()` in `AttendeeService` for bulk updates.
* **Repository**:
  * Extended to support tag-based search and updates.
* **Model / DTOs**:
  * Added `tag` field to `IndividualEntry`, `Attendee`, `AttendeeUpdateTagRequest`, `AttendeeUpdateTagResponse`, and `AttendeeSearchCriteria`.
  * Ensures tags flow consistently from request → service → DB → response.

#### **5. Code Cleanups & Improvements**

* Added new error messages for invalid tags, tenant mismatches, and missing attendees.
* Removed unused constants/imports.
* Updated version to **1.3.0** in `pom.xml` to reflect the new feature.

***

## Sequence Diagram

### Mobile User Flow

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdXoizEiPJpiFUSA9aUntqZIkub1IK_oZUBlF_KsNR886s4pHA6t07dssQ9z7ddlSAFD6DeftMtojFwb-bRbpL7x9XBtb_RetWe3Lc8k-cyqYUXlZTru2FP7aRi49jVboKPVqEE8g?key=h6xj56uLHjrcNj0msKKRCQ" alt=""><figcaption></figcaption></figure>

### Supervisor Flow

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeZwLPmizgD47771IXW_7bxalfWoAkZghZ_qdP8QUz9XPPyfUrPKjBZqZj-CRDWWL-_WM44oeyMNwK9a7c9VQesoXNCssATa_wYftXCYuZ4JY7AYCKz1sXjFzD5ImEoam3edVQnpA?key=h6xj56uLHjrcNj0msKKRCQ" alt=""><figcaption></figcaption></figure>
