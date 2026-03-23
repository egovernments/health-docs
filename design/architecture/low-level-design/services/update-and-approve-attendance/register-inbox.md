# Register Inbox

## Overview

Enables supervisors to view attendance registers filtered by selected boundaries (e.g., district).

## **Interface Elements**

<figure><img src="../../../../../.gitbook/assets/image (182).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="206.62890625">Element</th><th>Description</th></tr></thead><tbody><tr><td>Filters</td><td>Boundary selection dropdown (e.g., district) and "Apply" button to filter results.</td></tr><tr><td>Results Display</td><td>Shows registers with details such as Project Name, Status, Supervisor Name, and Entries.</td></tr><tr><td>Status Filters</td><td>Groups results by register status (e.g., Pending for Approval, Approved).</td></tr></tbody></table>

## **User Actions Flow**

1. Select Boundary: Choose a district from the dropdown.
2. Apply Filter: Click "Apply" to filter results.
3. View Results: Access filtered attendance registers for the selected district.

## **API Endpoints**

<table><thead><tr><th width="218.00390625">Endpoint</th><th width="277.5546875">Purpose</th><th>Role</th></tr></thead><tbody><tr><td>/registers-inbox/v2/filters/_search</td><td>Search registers by filter (district)</td><td>PROXIMITY_SUPERVISOR</td></tr><tr><td>/registers-inbox/v2/registers/{boundary}/_search</td><td>Retrieve registers for a selected boundary</td><td>PROXIMITY_SUPERVISOR</td></tr></tbody></table>
