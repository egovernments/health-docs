# My Bills

The "My Bills" section serves as a centralised dashboard for campaign supervisors to view and manage all bills associated with their assigned projects. By default, the dashboard displays all bills related to the projects under their supervision. Supervisors can search for specific bills or filter them using date ranges or by bill ID.

<figure><img src="../../../../../.gitbook/assets/image (231).png" alt=""><figcaption></figcaption></figure>

**Interface Elements**

**Search Filters**

1. **Bill ID**: Enter a specific Bill ID.
2. **Date Range**: Select a start and end date to filter bills within a specific time frame.
3. **Action Buttons**:
   * **Search**: Filters the results based on the provided criteria.
   * **Clear Search**: Resets the filters and shows all assigned bills.

***

**Bill List**

A table format displays the bills with the following columns:

<table><thead><tr><th width="231">Field Name</th><th>Description</th></tr></thead><tbody><tr><td><strong>Bill ID</strong></td><td>A unique identifier assigned to each bill (e.g., WB-YYYY-MM-DD-XXXXX).</td></tr><tr><td><strong>Date</strong></td><td>The creation date of the bill.</td></tr><tr><td><strong>Boundary</strong></td><td>The geographic boundary associated with the bill (e.g., District, Province).</td></tr><tr><td><strong>Project Name</strong></td><td>The name of the project for which the bill was generated.</td></tr><tr><td><strong>Workers</strong></td><td>The total number of workers covered under the bill.</td></tr><tr><td><strong>No of Registers</strong></td><td>The total number of registers associated with the bill</td></tr><tr><td><strong>Status</strong></td><td>The current status of the bill (e.g., Generated, In Progress, Failed).</td></tr></tbody></table>

***

&#x20;**Status Descriptions**

* **Generated**: The bill has been successfully generated. The user can download it in **PDF** or **Excel** format.
* **In Progress**: The report is still being generated. The user should wait for completion.
* **Failed**: The report generation failed. The user can:
  * **Retry** the process.
  * Contact support if the issue persists.

***

**API Endpoints**

| EndPoint                           | Purpose                             |
| ---------------------------------- | ----------------------------------- |
| `/health-expense/bills/v1/_search` | Search bills by project id          |
| `/filestore/v1/files/{id}`         | Download details of a specific bill |
