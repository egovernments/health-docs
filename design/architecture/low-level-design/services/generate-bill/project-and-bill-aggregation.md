---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/low-level-design/services/generate-bill/project-and-bill-aggregation
---

# Project & Bill Aggregation

## Overview

This is the initial screen where the user selects:

1. Project: The specific project they are managing.
2. Bill Aggregation Level: The boundary level at which the bill should be generated (Country, Province, or District).

Users cannot proceed without filling out these fields.

<figure><img src="../../../../../.gitbook/assets/image (377).png" alt=""><figcaption></figcaption></figure>

## **Interface Elements**

<table><thead><tr><th width="259">Element</th><th>Details</th></tr></thead><tbody><tr><td><strong>Project Selection</strong></td><td>Dropdown menu to select the project.</td></tr><tr><td><strong>Bill Aggregation Level</strong></td><td>Dropdown menu to select the aggregation level (Country, Province, District).</td></tr><tr><td><strong>Action Buttons</strong></td><td>- Back: Navigate to the previous screen.<br>- Next: Proceed to view registers mapped to the selected project.</td></tr></tbody></table>

## **User Actions Flow**

1. Use the dropdown menu to select the project.
2. Select one of the available aggregation levels (Country, Province, or District) from the dropdown.
3. Click the "Next" button to navigate to the register filtering screen.

***

## **Validations**

* Both fields are mandatory:
* If either the Project or Bill Aggregation Level is not selected, an error toast message is displayed if you try to proceed.
