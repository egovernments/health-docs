# Payments Product Requirement Document

## 1. Purpose

This document serves as a guide to effectively use the Payments module within Health Campaign Management (HCM). It outlines the features and functionalities available to users, clarifying tasks that can be performed and limitations to be aware of. Additionally, it provides essential instructions for critical processes, such as approving attendance and generating payments, including key considerations and best practices. The document also highlights important dos and don'ts to ensure smooth and error-free operations. To enhance understanding, it offers a detailed overview of the Payments module's workflow, supported by illustrative screenshots for better clarity and ease of reference.

## 2. Definitions

* HCM: Health Campaign Management - The tool for managing health campaigns, including modules for various functions such as payments, attendance, enumeration, supervision, etc.
* Event: Key activities during a campaign where attendance is recorded, such as training, enumeration, and distribution.
* Attendance Register: A record of attendance for different campaign events, detailing participant names and attendance dates. Attendance markers use the HCM attendance module to record attendance daily until the event concludes.
* Muster Roll: An official report documenting the daily attendance of workers engaged in a specific project or campaign. It includes essential details such as worker names, roles, work locations, attendance dates, and days worked. The muster roll is created after the attendance register is approved and serves as a reference for validating attendance, calculating wages, and generating payment reports.
* Attendance Marker: The individual responsible for recording event attendance using the HCM mobile app’s attendance module.
* Proximity Supervisor: The person authorised to review and, if necessary, edit attendance records submitted by attendance markers. They approve the records for payment processing.
* Payment Approver: The person tasked with reviewing generated muster rolls, consolidating them into a single payment report for a specific boundary, and sharing it with financial authorities for payment disbursement.
* Boundary: An administrative area used for managing campaigns, such as a province, district, locality, or village. Events and users are assigned to specific boundaries. For instance, a district supervisor assigned to District ABC will oversee district-level training registers created within District ABC.

## 3. Scope

1. Editing Attendance Records Post-Event Completion

* Authorised personnel, such as proximity supervisors, can modify attendance records after an event concludes to correct errors or omissions made during initial data entry.
* Edits include correcting the number of days worked or marking attendance for previously unrecorded participants.
* All edits are tracked and documented within the system for audit purposes.

2. Approval of Attendance Records and Muster Roll Generation

* Once attendance records are reviewed and finalised, they are submitted for approval by proximity supervisors.
* Approved records are used to automatically generate the muster roll, which contains attendance details for the event.
* The muster roll becomes the official document for wage validation and payment processing.

3. Reviewing Approved Registers

* Payment approvers or other authorised stakeholders can access and review attendance registers that have already been approved.
* The review process ensures compliance with organisational guidelines and verifies that data matches muster roll records before payment reports are generated.

4. Viewing Approved and Unapproved Registers

* Users with appropriate permissions can view both approved and pending approval attendance registers.
* This view allows campaign managers to monitor the status of attendance records for all events within a given boundary.
* Filters and search functionalities may be available to help locate specific registers based on event type, date, or boundary.

## 4. Out of Scope

The following features and functionalities are not included in this version of the Payments module and are considered out of scope. Some may be considered for inclusion in future versions.

* Campaign Worker Onboarding: Workers must be onboarded via the HRMS or Console web interfaces, as this is not supported in the app.
* Worker Registry Validation: The module does not support checks for:

&#x20;      \- Duplicate entries or boundary over-allocations.

&#x20;      \- Mobile number authentication (inactive numbers or mismatches).

&#x20;      \- Identity verification or validation of mobile money accounts for status and transaction limits.

* Approval Workflows: Missing workflows for:

&#x20;     \- Payment report approvals

&#x20;     \- Muster roll approvals

* Attendance Corrections: No provision for:

&#x20;      \- Proximity supervisors returning attendance reports to field supervisors for corrections.

&#x20;      \- Payment approvers returning attendance reports to proximity supervisors for corrections or rejections.

* Worker Payment Configuration: Setting different rates for workers with the same role based on location boundaries is not considered for this version.
* Reporting Limitations: Support for generating intermediate reports before event completion is not considered for this version.
* Attendance Evidence: The following capabilities are not in  scope for this release:

&#x20;     \- Photos of workers or ID card

&#x20;     \- Signature, QR code, or biometric-based attendance

* Financial Integrations: No integration with mobile money operators (MMOs), banks, or financial institutions.
* Worker Communication: Automated SMS notifications for payments, attendance tracking, or registrations are not considered for this version.
* KYC and Registry Cross-Checks: No automated cross-checking of failed KYC attempts, name mismatches, or duplicates against MMOs and the worker registry in HCM.

## 5. Roles & Responsibilities

1. Attendance Marker: Responsible for recording attendance at events (e.g., trainings, enumerations). This role may be filled by a field team supervisor or any individual presiding over the event.
2. Proximity Supervisor: Charged with approving the attendance recorded by the attendance marker. They verify attendance details (often via phone outside HCM) if discrepancies arise and have the authority to edit records after the event concludes. This role typically operates at the district level or higher.
3. Payment Approver: Oversees the consolidation of attendance records to generate boundary-specific reports. They are responsible for approving the payment report, forwarding it to higher operations for additional approvals, and liaising with financial institutions to process payments.

## 6. Dos & Don’ts For Key Roles

**1. Attendance Marker**

Do's:

* Mark daily attendance for all assigned registers without fail.
* Sync all records to ensure no pending entries remain on the device before the proximity supervisor edits or approves the attendance records for that event.
* Raise complaints for issues like adding/removing persons or correcting details of the staff using the complaints module or by contacting the system administrator.

Don’ts:

* Submit incorrect attendance—once submitted, corrections are not possible for the attendance marker.

***

**2. Proximity Supervisor**

Do's:

* Verify with the attendance marker for all the districts that all records are synced before editing or approving attendance.
* Make edits as necessary, but ensure all details are accurate before final approval.
* Approve all registers systematically, completing one district before moving to the next.
* Raise complaints for issues like entry corrections via the complaints module or the system administrator.

Don’ts:

* Approve attendance without confirming that all records are synced.
* Assume changes can be made after approval—final approvals are irreversible.

***

**3. Payment Approver**

Do's:

* Double-check all details in the payment report (PDF/Excel) before submission to financial institutions.
* Generate payment reports for each boundary systematically, starting with one district and moving to the next, including provincial/national events.
* Wait 2-3 minutes for report generation before reporting issues.

Don’ts:

* Editing Excel reports after generation is not allowed.
* Submit incomplete or inaccurate reports.

***

**4. System Administrator**

Do's:

* Validate worker information (enumerators, supervisors, etc.) before onboarding them in the system, ensuring correct mobile numbers and IDs.
* Confirm no duplicate personnel or mobile numbers exist in the system.
* Map workers accurately per the microplan, avoiding over or under-allocations
* Verify that mobile and bank account numbers belong to the correct person and not their family members.
* Ensure mobile numbers are active and unrestricted for receiving payments.
* Approve register changes only after supervisory authorisation.

Don’ts:

* Allow unverified or incorrect data to be entered into the system.
* Approve register changes without proper supervisory approval.

***

## 7. Pre-requisites

1. **Before the Campaign or Related Event Starts**

* Ensure all workers, including supervisors as per the microplan, are created in the system.
* Complete all worker validations as outlined in Section 6.
* Confirm that all attendance registers are created and assigned to the appropriate attendance markers and proximity supervisors.
* If payment reports need to be generated mid-event, make it as two separate attendance registers for the event: one for the first half and another for the second half.
* For different wage amounts across specific boundaries for the same role, create separate roles with the appropriate wage amounts and assign workers accordingly.
* Verify that all attendance markers and proximity supervisors can log in and view their assigned attendance registers.

2. **During the Campaign or Related Event**

* Mark attendance diligently for each register daily using the HCM application.
* Perform routine syncs to ensure no unsynced records remain, particularly upon event completion.

3. **After the Campaign Starts or Ends**

* Ensure no registers are pending approval by proximity supervisors.
* Verify the accuracy of the worker and register details before generating the payment report.
* Confirm that payment registers are created for all boundary levels and individual boundaries (e.g., districts, provinces, country).

## 8. Process Flows

1. **Overall process flow diagram:**

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.09.15 AM.png" alt=""><figcaption></figcaption></figure>

2. **Proximity supervisor workflow**

On the language selection screen, select the preferred language from the available options. Select the desired language and click on ‘Continue’ to access the login page.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.10.41 AM.png" alt=""><figcaption></figcaption></figure>

On the login page, enter the credentials for a proximity supervisor and select the assigned boundary. After reading through the privacy policy statement, select the checkbox to accept the terms and conditions and then click on ‘Continue’ to proceed to the landing page for the proximity supervisor.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.12.32 AM.png" alt=""><figcaption></figcaption></figure>

On the landing page for a proximity supervisor, the ‘Payments’ label is displayed along with an option to view the "Attendance Registers". Click on the "Attendance Registers" label to access project-specific attendance registers.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.13.39 AM.png" alt=""><figcaption></figcaption></figure>

Select the desired project name (event name) from the available options in the dropdown and click ‘Next’ to proceed.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.15.04 AM.png" alt=""><figcaption></figcaption></figure>

Following the selection of the project name, you will be navigated to the ‘Inbox’ screen, where, by default, no attendance registers are shown. To view attendance registers, a desired boundary must be selected through a boundary filter (in this case, ‘District’). Once the desired boundary is selected, click on ‘Apply’ to proceed.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.15.53 AM.png" alt=""><figcaption></figcaption></figure>

Post selection of a desired boundary, you will be directed to a screen that shows all the "Pending for approval (#)" and ‘Approved (#)’ attendance registers that have been created within that specific boundary, with "Pending for approval (#)" registers being the default viewing option. ‘Approved (#)’ attendance registers can be accessed through toggling.  Based on the status type (either pending for approval or approved), further discretised information is provided in a tabular format, which includes the following: Attendance ID, Attendance marked by, Boundary, and Number of attendees.&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.17.05 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.17.47 AM.png" alt=""><figcaption></figcaption></figure>

Clicking on the "Attendance ID" on the ‘Inbox’ page will open the "View Attendance" screen, which will provide all the campaign-related details of the registrant and their attendance summary. The ‘Action’ button present on the bottom right of the screen allows the proximity supervisor to either "Edit Attendance" or ‘Approve’ the submitted data.&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.19.15 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.19.47 AM.png" alt=""><figcaption></figcaption></figure>

On clicking "Edit Attendance", a warning message is displayed informing the proximity supervisor that editing the attendance days data will impact the payments, and the same will be frozen for the entire event duration, followed by a confirmation question. This means that if the field supervisor marks the attendance for any further dates, it will not be updated in the register. The proximity supervisor can decide to either ‘Proceed’ to update the attendance data or select ‘Cancel’ to go back to the "View Attendance" page. Click on ‘Proceed’ to confirm the editing of the attendance data.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.21.21 AM.png" alt=""><figcaption></figcaption></figure>

Next, the "Edit Attendance" page is displayed, which will allow the proximity supervisor to update the attendance data for each field supervisor with the help of the ‘+/-’ buttons, or they can enter the count directly within the data entry field. The ‘Submit’ button is disabled until the proximity supervisor updates the attendance for at least one field supervisor.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.23.16 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.24.00 AM.png" alt=""><figcaption></figcaption></figure>

If the "number of days worked" entered exceeds the event duration while updating, an error message will be shown informing the proximity supervisor about it. The system allows marking the number of days as 0, accommodating those who may not have participated for the entire duration of the event.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.24.46 AM.png" alt=""><figcaption></figcaption></figure>

Once the new attendance data has been entered, click on ‘Submit’ to proceed.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.25.23 AM.png" alt=""><figcaption></figcaption></figure>

Subsequently, a toast message is displayed indicating that attendance has been updated successfully. The attendance data can be modified as many times as required until it is approved.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.26.02 AM.png" alt=""><figcaption></figcaption></figure>

Following the successful submission of the new data, the "View Attendance" page will automatically appear, where the updated attendance data is reflected.&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.27.30 AM.png" alt=""><figcaption></figcaption></figure>

Now, click on the ‘Action’ button and then select the ‘Approve’ option. This will open a dialogue box, where mandatory comments should be provided to proceed with the approval process, which is continued by clicking again on ‘Approve’. The approval process can also be cancelled at this stage by clicking on ‘Cancel’.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.32.45 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.34.06 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.34.43 AM.png" alt=""><figcaption></figcaption></figure>

After submitting the mandatory comments, if the ‘Approve’ option is selected, then a confirmation pop-up will appear with a message highlighting that the data, once approved, cannot be modified.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.35.56 AM.png" alt=""><figcaption></figcaption></figure>

On clicking again on ‘Approve’,  a success screen will be displayed for confirmation, and the muster roll will be generated and displayed on the screen. Following this, any other assigned tasks can be carried out by clicking on "View Another Register" or "Go Back to Home".

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.37.06 AM.png" alt=""><figcaption></figcaption></figure>

On the ‘Inbox’ page, the status of the register can now be seen as approved, and when it is opened, no actions are available, except to "Go Back".

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.43.02 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.46.01 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 11.46.40 AM.png" alt=""><figcaption></figcaption></figure>

3. **Payments approver workflow**

The payment approver is responsible for generating and downloading the final payment bill which is further used to disburse the payments to all the campaign workers.

On the language selection screen, select the preferred language from the available options, and click on ‘Continue’.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 1.48.37 PM.png" alt=""><figcaption></figcaption></figure>

Next is the login page, where the credentials for a campaign supervisor are entered and the assigned boundary is selected. After reading through the privacy policy statement, select the checkbox to indicate acceptance. Then click on ‘Continue’ to proceed.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 1.49.51 PM.png" alt=""><figcaption></figcaption></figure>

This is the landing page for a campaign supervisor. On this page, a card is displayed for payments with the options to go to the ‘Inbox’ page to generate bills and to "My Bills" to view and download already generated bills. Click on ‘Inbox’ to proceed.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-14 at 1.51.01 PM.png" alt=""><figcaption></figcaption></figure>

On this page,  the project name (event type name) from the available options must be selected, as well as the aggregation boundary details, whether the bill should be aggregated at the national, province/state, or district level. Select the required aggregation boundary level and click on ‘Next’.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-17 at 9.24.49 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-17 at 9.26.20 AM.png" alt=""><figcaption></figcaption></figure>

Following this, the "Bill Inbox" page will appear, where the specific boundary should be filtered for which the bill has to be generated. Once selected, it will display all the attendance registers, both approved and pending approval, which can be only viewed by the campaign supervisor, along with an option to generate the bill. Click on "Generate Bill".

The campaign supervisor will be able to generate the bill only once for a particular boundary, and this can be done only when all the registers within that boundary have been approved.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-17 at 9.28.49 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-17 at 9.29.32 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-17 at 9.31.02 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-17 at 9.31.42 AM.png" alt=""><figcaption></figcaption></figure>

On clicking  "Generate Bill", a confirmation pop-up is displayed that indicates that the bill cannot be generated again. Click on "Generate Bill" to proceed.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-17 at 9.32.25 AM.png" alt=""><figcaption></figcaption></figure>

This will initiate the bill generation process along with displaying a toast message highlighting the wait time for completion of the process. Click on "My Bills" to proceed.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-17 at 9.34.47 AM.png" alt=""><figcaption></figcaption></figure>

Clicking on "My Bills" will display the bill inbox page, where all the generated bills can be found. On this page,  bills can be searched by the ‘Bill ID’ or a date range based on the date they were generated. The bills which are still being generated can be identified in the ‘Actions’ column.&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-17 at 9.35.50 AM.png" alt=""><figcaption></figcaption></figure>

Once the bill has been generated successfully, it can be downloaded as either an Excel file or a PDF by clicking on the respective action button. Choose the required format for the report to be downloaded.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-17 at 9.38.15 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-17 at 9.41.12 AM.png" alt=""><figcaption></figcaption></figure>

An illustration of the PDF report is given below. The report provides the following information: total amount to be processed, details of each individual, different cost heads that are applicable based on the assigned role, and the sum of the amount to be paid based on the number of days attended.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2025-02-17 at 9.42.17 AM.png" alt=""><figcaption></figcaption></figure>

## 9. FAQs

1. What are the different types of roles available in the HCM payments module\
   Two different types of roles have been made available in the HCM payments module version 1.

&#x20;      a. Proximity Supervisors

&#x20;      They are responsible for making changes in the attendance registers as well as approving them.

&#x20;     b. Payment Approvers&#x20;

&#x20;     They are responsible for generating the bills and are authorised to download them in Excel/PDF formats for further processing.

2. What is the workflow of the payments module in the HCM platform?\
   In the HCM platform, the payments module is coupled with the attendance module. The typical workflow diagram is provided in section 8:
3. How to mark attendance in the HCM platform?\
   There is a dedicated attendance module available in the HCM platform to allow field supervisors to mark the attendance of their team members.
4. What is an attendance register in the HCM platform?\
   An attendance register is a record-keeping tool that is used to track the count of present or absent campaign workers, along with their activities such as training, registration/distribution, etc.&#x20;
5. How can a proximity supervisor edit an attendance register?\
   User Navigation: Login > Home Page > Attendance Registers > Select Project Name > Select Boundary > Click on Attendance Register in ‘Pending for Approval’ state > View Attendance > Action: Edit Attendance > Warning Message: Proceed > Edit Attendance > Submit > Success Message.\
   (Note: You can edit the attendance as many times as required till it is approved).&#x20;
6. How can a proximity supervisor approve an attendance register?\
   User Navigation: Login > Home Page > Attendance Registers > Select Project Name > Select Boundary > Click on Attendance Register in ‘Pending for Approval’ state > View Attendance > Action: Approve > Add Comments and Approve > Confirmation: Approve > Success Screen\
   (Note: Once approved, you cannot take any further action on the register)
7. What are approved and unapproved registers?\
   Approved registers are those that are marked as approved by the proximity supervisors, and they cannot take any further action on these registers.\
   Unapproved registers are the ones that are submitted by the field supervisors to be approved by the proximity supervisor, and their attendance details can be updated by the proximity supervisor before approval.
8. How can I select a different type of attendance register?\
   The first step as a proximity supervisor is to select the type of attendance register from the drop-down after logging in to the payments module.  There will be multiple types of registers, such as Master Training register, Registration team training, Campaign, etc.
9. As a proximity supervisor, I have selected one of the districts as a boundary. Which attendance registers can I manage?\
   You can manage only those registers assigned at the selected district or boundary levels below the district.
10. As a payments supervisor, I have selected the country name. Which muster rolls can I generate the payment report for?&#x20;

&#x20;      You can generate the payment report for all the muster rolls that are assigned at a county level.

11. As a payments supervisor, I have selected a province name. Which muster rolls can I generate the payment report for?

&#x20;      You can generate the payment report for all the muster rolls that are assigned at a province level.

12. As a payments supervisor, I have selected a district name. Which muster rolls can I generate the payment report for?

&#x20;      You can generate the payment report for all the muster rolls that are assigned at a district level or below the district level.

13. What is a muster roll in the HCM payments module?\
    A muster roll is a simple document used to keep track of workers and their activities. It records who showed up for work, the hours they worked, and sometimes their pay. It helps employers know who was present and how much work was done. In campaigns, a muster roll can track attendance and ensure workers are paid correctly for their efforts.
14. What is an event?\
    In the context of attendance for a campaign, an event refers to a specific activity or session where workers or participants are expected to be present. This could include training sessions, daily fieldwork (registration/distribution), or any other scheduled task as part of the campaign.
15. When should I approve an attendance register?\
    You must wait for the event to be completed to review and approve the attendance register.
16. Is it advisable to approve a register before an event is completed? What happens if I edit attendance during an ongoing event?\
    Always approve the attendance register only after the event has fully concluded to ensure data accuracy. Editing attendance during an ongoing event will overwrite the current records, and the system will consider the edited data as final. Additionally, if the attendance register has been edited and approved, attendance markers attempting to record attendance will encounter errors, as there is no downward data flow from the proximity supervisor to the attendance marker
17. Which formats can I download the payment report in?\
    The reports are available for download in Excel and PDF formats.
18. How can I view and download the bills I generated?\
    Navigation: Login > Home Page > My Bills > Actions (Download in Excel/PDF)
19. Can I create bills again for already generated muster rolls?

&#x20;      No, you cannot regenerate bills. However, you can view the generated bills as well as download them as many times as needed.

20. How long will it take to generate a bill?\
    The bill generation can take up to 2-3 minutes, depending on the number of registers collated.
21. How can I aggregate muster rolls into a single bill? Is aggregation mandatory? At what levels can aggregation occur?"\
    \
    Aggregation of muster rolls can be done at different boundary levels, as described below:\
    \
    District Level: Muster rolls from all events created at the district or subordinate levels are aggregated for the selected event type.\
    Example: Aggregating muster rolls for all registration events in the district of Nampula, including those at locality levels within Nampula.\
    \
    Province/State Level: Muster rolls from events across the entire province/state are combined.\
    Example: Aggregating all muster rolls for distribution events across the province of Cabo Delgado.\
    \
    National Level: Muster rolls from events nationwide are collated.\
    Example: Aggregating muster rolls for all master trainer training conducted at the national capital in Mozambique.\
    \
    Aggregation is separated at various levels to ensure there are no duplications of bills generated for the same registers
22. What should I do if bill generation fails?"

* Wait for some time and try generating the bill again.
* Check that all attendance registers have been approved.
* If the issue persists, contact the system administrator for assistance.

23. Can I edit the Excel sheet of the payment report?\
    Payment report sheets are protected and cannot be directly edited. If edits are necessary, duplicate the sheet and make the required changes. Ensure that any modifications are made only with the approval of the respective supervisory authority.
24. How can I change the payment rates for specific roles?\
    If certain roles require different payment rates, you need to define those roles separately and assign individuals accordingly. If people in the same role working across different boundaries need different rates, create distinct roles for each boundary. Ensure any changes are made before generating bills
25. Can I assign different payment rates to the same role for different boundaries?\
    No, the system currently supports assigning rates based on roles, which must remain consistent across all boundaries.
26. How can I generate an intermediate payment report before the event is completed?\
    The current version of the module does not support generating intermediate payment reports during an ongoing event

## 10. Appendix

#### Attendance Management

The Attendance Module enables supervisors to track attendance for their attendees, ensuring accurate records and consistent data for processing payments. This serves as the precursor to the Payments module. For more details, click [here](https://health.digit.org/hcm-product-suite/health-products/hcm-app/user-manual/common-functions/attendance-management).
