---
description: Description of the attendance service
---

# Attendance

## Overview

The Attendance Service is a comprehensive back-end solution designed to support health campaigns by providing efficient and transparent attendance management. It facilitates the streamlined tracking of health campaign workers, volunteers, and contractors, ensuring accurate participation records and enabling informed decision-making.

Note: Deletion of attendees from the system is not recommended, even in cases where participation in the campaign has ceased. Attendance records should instead reflect the status of absent for all days following the departure. This practice ensures the integrity of attendance data, preserves historical records, and supports accurate reporting and auditing processes.

Key functionalities include:

* Maintaining attendance registers.
* Enrolling and managing individuals.
* Creating, updating, and searching attendance logs.
* Managing staff permissions for attendance-related operations.

## API Specifications

**Base Path:** /health-attendance/

### API Contract Link

[https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/DIGIT-Works/f525b183782a353812f7e2432a2989a86c498810/backend/attendance/Attendance-Service-1.0.0.yaml](attendance.md#api-contract-link)

## Data Model

### DB Schema Diagram

<figure><img src="../../../../.gitbook/assets/attendance_db.png" alt=""><figcaption><p>Attendance with Offline Enablement of Logs</p></figcaption></figure>

## Web Sequence Diagrams

#### Attendance Register

{% tabs %}
{% tab title="Create" %}
<figure><img src="../../../../.gitbook/assets/Attendance-Register Create(1).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Update" %}
<figure><img src="../../../../.gitbook/assets/Attendance-Register Update.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Search" %}
<figure><img src="../../../../.gitbook/assets/register_search.png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

#### Staff

{% tabs %}
{% tab title="Create" %}
<figure><img src="../../../../.gitbook/assets/Staff Create.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Update/Delete" %}
<figure><img src="../../../../.gitbook/assets/Screenshot 2024-03-04 at 11.58.48 AM.png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

#### Attendee

{% tabs %}
{% tab title="Create" %}
<figure><img src="../../../../.gitbook/assets/Screenshot 2024-03-04 at 12.00.02 PM.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Delete" %}
<figure><img src="../../../../.gitbook/assets/Screenshot 2024-03-04 at 12.00.39 PM.png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

#### Attendance Log

{% tabs %}
{% tab title="Create" %}
<figure><img src="../../../../.gitbook/assets/Screenshot 2024-03-04 at 12.01.41 PM.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Update" %}
<figure><img src="../../../../.gitbook/assets/Screenshot 2024-03-04 at 12.02.11 PM.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Search" %}
<figure><img src="../../../../.gitbook/assets/Attendance Log Search.png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}
