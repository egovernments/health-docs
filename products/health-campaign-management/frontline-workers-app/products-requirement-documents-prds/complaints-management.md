# Complaints Management

## Table of contents&#x20;

Background

Target Audience

Assumptions and Validations

Process flow

Solution - Quick Win

Out of scope

Specifications

## Background

This document describes the need and scope of a digital platform for health campaigns, explaining the product’s features, specifications, purpose, and functionality. It also provides a descriptive view of the application along with the specification of each element.

## Target Audience

This document is intended for the engineering and platform (tech teams), product management, and implementation teams to agree on requirements for the Health Campaign Management Platform (HCM).

## Assumptions and Validations

<table><thead><tr><th width="231.5">Theme</th><th>Assumption</th></tr></thead><tbody><tr><td>Logging complaints</td><td><ul><li>Not all complaints will be logged using the complaints module. Users may prefer raising complaints on WhatsApp groups/calls, and may not be registered in the system.</li><li>Complaints are most likely to be logged by users on behalf of other users (Most common use case: Supervisors raising complaints on behalf of users</li></ul></td></tr><tr><td>Resolving complaints</td><td><ul><li>There is a support helpdesk set up by the program which will receive all complaints raised by system users.</li><li>The support helpdesk must be responsible for reviewing all the complaints in the inbox</li><li>Depending on the complaint, the helpdesk can either resolve, reject or assign the complaint to the respective actor</li><li>Helpdesk users may create complaints on the user’s behalf, which are received over call/WhatsApp messages.</li></ul></td></tr></tbody></table>

### Role-Action Mapping

Registrar: Create, view, update and cancel complaints.

Field Supervisor:

a. Create, view, update, and cancel complaints.

b. Resolve complaints, re-assign complaints back to the helpdesk, and reject complaints.

Supervisor:&#x20;

a. Create, view, update, and cancel complaints.

b. Resolve complaints, re-assign complaints back to the helpdesk, and reject complaints.

Helpdesk user:&#x20;

a. Create, view, update, and cancel complaints.

b.  Resolve complaints, assign complaints, and reject complaints.

### Statuses in the Workflow

<table><thead><tr><th>Status name</th><th width="250.33333333333331">Description</th><th>Leads to (next status)</th></tr></thead><tbody><tr><td>Submitted (TBD depending on design approach)</td><td>Status when a complaint is submitted but hasn’t been received by the helpdesk (to support offline use case).</td><td>Pending Assignment</td></tr><tr><td>Pending Assignment</td><td>Status when the complaint has been received by the helpdesk (in the event of a completely online system), the pending assignment must be the first status in the workflow.</td><td>Resolved, Rejected, Assigned</td></tr><tr><td>Resolved</td><td>Status when the complaint has been addressed and closed successfully.</td><td>NA</td></tr><tr><td>Rejected</td><td>Status when the complaint is found to be invalid and rejected.</td><td>NA</td></tr><tr><td>Assigned To &#x3C; ></td><td>Status when the complaint is assigned by the helpdesk to other roles in the workflow.</td><td>Resolved, Rejected. The possible status will depend on the workflow configured during implementation.</td></tr><tr><td>Cancelled</td><td>Status, when the user decided to delete the complaint, created.</td><td>NA</td></tr></tbody></table>

## Process Flow

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-01-25 at 10.46.33 AM.png" alt=""><figcaption></figcaption></figure>

## Solution

### Complaints: For mobile users

1. Creating a new complaint:

* Any campaign staff (with access to the complaints module) must be able to create a complaint using the mobile app for themselves or on behalf of other users.
* Users can only create complaints for users in the same boundary hierarchy.

&#x20; 2\.  Viewing “My Complaints”:&#x20;

* Users must be able to view the complaints created by themselves in the mobile app and the web portal.
* Users must be able to filter, sort, and search complaints.

Helpdesk View: (Web app and mobile responsive app)&#x20;

1. All complaints raised by any system user in the system must first be routed to the helpdesk.
2. Helpdesk user must be able to filter, sort, and search complaints.
3. The helpdesk user must review all complaints received in the helpdesk’s inbox and perform one of the following actions:

* Resolve: For complaints that can be resolved by the L1 support helpdesk, the helpdesk user must be able to view the details mentioned in the complaints, mark them as “Resolved” and add resolution details.
* Reject: If the helpdesk user determines a complaint to be false, irrelevant, or invalid, the user must be able to mark the complaint as “Rejected” and give proper justification for rejecting the complaint.
* Assign: For complaints that cannot be resolved by the L1 support helpdesk, the helpdesk user must be able to select the appropriate role and assign the complaint. Once the helpdesk user assigns a complaint, the status must be shown as “Assigned."

&#x20;     a. Workflow to be set up during implementation.&#x20;

&#x20;     b. The core product would offer the following workflow: Create→ Submitted to L1 Helpdesk→ Assign to L2 support.

&#x20;     c. The workflow must be configurable to support additions of more workflow states: (For eg. Assign to: Program Managers, Supervisors, etc).

&#x20;4\. Help desk users must be able to create new complaints. The new complaint created must be visible in the helpdesk user’s inbox to take action on (Use case: Helpdesk user receives a complaint over call and creates a complaint in the system for tracking on the user’s behalf).

&#x20; 5\. Report Generation: (Good to have for v1 since already covered in the dashboard)

&#x20;    a. Helpdesk performance report: Report generated on the following parameters:

&#x20;        1\. Time range

&#x20;        2\. Status of complaints

&#x20;        3\. User name

## Risk/Limitations

Addressed in the Out of Scope section.

## Out of Scope

* Re-opening of complaints
* Auto-escalation of complaints
* Auto-routing of complaints
* Sharing feedback on complaint resolution
* Notification to users on status change
* SLA tracking

## Specifications

<table><thead><tr><th width="161">Field</th><th width="114">Data Type</th><th width="153">Data Validation</th><th width="146">Required (Y/N)</th><th width="216">Comment</th></tr></thead><tbody><tr><td>Complaint type</td><td>Dropdown</td><td>Only one complaint type must be selected.</td><td>Y</td><td><p>Values to be configured. </p><p>If type is “Other”: Display text box to enter type.</p><p><br></p></td></tr><tr><td>Date of complaint</td><td>Date</td><td>System fetches the current date.</td><td>Y</td><td>Must be non-editable (no action required by user).</td></tr><tr><td>Administrative area</td><td>String dropdown</td><td></td><td>Y</td><td>For mobile view: Admin area must be populated based on value set in the location picker For Web view: Select from list of assigned projects/ boundaries.</td></tr><tr><td>Complaint raised for</td><td>Boolean</td><td></td><td>Y </td><td>Options available: Self and other.</td></tr><tr><td>Complainant’s name</td><td>String</td><td>If “self”: Name must be populated as entered in the user’s profile.</td><td>Y</td><td>If “Name” is blank in the user’s profile, the text field must be empty.</td></tr><tr><td>Complainant’s contact number</td><td>Numeric</td><td>If “self”: Number must be populated as entered in the user’s profile.</td><td>Y</td><td>If “Number” is blank in the user’s profile, the text field must be empty.</td></tr><tr><td>Supervisor’s name</td><td>String</td><td></td><td>N</td><td></td></tr><tr><td>Supervisor’s contact number</td><td>Numeric</td><td></td><td>N</td><td></td></tr><tr><td>Complaint description</td><td>String</td><td>Max limit of description: TBD</td><td>Y</td><td></td></tr><tr><td>Upload photo</td><td>Media</td><td>Max size of media: TBD</td><td>N</td><td></td></tr><tr><td>Complaint number</td><td>String</td><td></td><td>Y</td><td>Unique ID generated by the system.</td></tr><tr><td>Reason for rejection</td><td>Dropdown</td><td></td><td>Y</td><td>Must be configurable during impel.</td></tr><tr><td>Assign to</td><td>Dropdown</td><td>Mandatory if action taken to assign.</td><td>C(Y)</td><td>Must be configurable during impel depending on the workflow. Default value: Assign to L2.</td></tr></tbody></table>

## Design

Find the mockups below:

### HCM Home screen

After logging into the application, the user lands on this screen which displays daily performance (number of households registered). The progress bar must reset daily at 00:00 hours and start from 0 registrations. The action buttons related to the beneficiary are present,  which include:

* Beneficiaries
* View reports
* Sync data
* Call supervisor
* Complaints

At the bottom, there is a card that shows how many records are unsynced for the user’s convenience to sync data. The help button is on every screen of the application. By clicking on it, a user can get the walkthrough of the elements on that screen.

On the top right, the administrative area assigned to the user is displayed, which will be based on the level of hierarchy. The hamburger button on the top left corner covers some other actions mentioned further.

![](<../../../../.gitbook/assets/IMG\_20230512\_232807 (1).jpg>)

### Complaints

When the user clicks on the complaints, she is navigated to the “My Complaints” screen, which consists of two actions:

* File a complaint (primary action): Clicking on this must open the complaint type screen.
* View previously logged complaints.

![](../../../../.gitbook/assets/IMG\_20230513\_234148.jpg)

## File Complaint Workflow

Complaint Type

When the user clicks on file a complaint, the complaint type screen appears. The user must select the type of complaint from the list, which must be configurable (to be configured during implementation as per program requirements).&#x20;

There is a ‘Next’ button at the bottom of the screen, clicking on which, the user is navigated to the complaint details screen.

![](../../../../.gitbook/assets/IMG\_20230513\_233907.jpg)

Complaint Details

Once the user has selected the type of complaint and clicked on ‘Next’, this screen appears, where they need to provide the complaint details.

The date field is auto-captured by the system, which must be non-editable.&#x20;

The administrative area is also auto-captured but it is editable. It is editable in case the user is creating the complaint on someone’s behalf. The dropdown displays a list of boundaries that are assigned to the user.

The user needs to select whether she is raising a complaint for herself or on behalf of another user.

If the user wants to raise a complaint for herself, then she must provide the following details:

1. Name (must be populated if already available in the user’s profile else must be blank).
2. Contact number (must be populated if already available in the user’s profile else must be blank).
3. Supervisor’s name and contact number.

If the complaint is raised on behalf of another user, then her details must be captured in the above fields. The user has the option to upload images describing the issue along with a text-based description. If the user wants to change the type of complaint, they can click on the ‘Back’ button and return to the previous screen.&#x20;

After filling in all the details, the user needs to click on the ‘Submit’ button to file the complaint.

![](../../../../.gitbook/assets/IMG\_20230513\_233934.jpg)\


<div align="left">

<figure><img src="../../../../.gitbook/assets/Android - 322 (1).png" alt="" width="180"><figcaption></figcaption></figure>

</div>

Confirmation Screen

When the user clicks on the submit button after providing all the complaint details, the confirmation screen appears, which provides information on whether the complaint has been submitted or not.

* If the complaint has been submitted, then it must show the message to sync the data for generating the complaint number. There must be a back to home button below the message. When the user clicks on it, she must be navigated to the home screen.
* If the complaint has not been submitted, then there must be two buttons available; Retry and Back to Home.

![](../../../../.gitbook/assets/IMG\_20230513\_234003.jpg)

### Resolving a complaint (Mobile App View)

Helpdesk

The L1 support helpdesk must be the first point in the complaint management workflow. All complaints created must be first routed to the helpdesk, after which the helpdesk may take an appropriate action (mentioned below).

The helpdesk user must be able to do the following :

* View List of complaints in the inbox
* File a new complaint
* Open a complaint from the inbox and&#x20;

&#x20;      View complaints status

&#x20;      Resolve a complaint&#x20;

&#x20;      Reject a complaint

&#x20;      Assign to other roles

The inbox view for other workflow states must be similar and must be able to view complaints assigned to their respective inbox. The user must also have the option to assign the complaint back to the L1 support helpdesk by selecting the value in the “Assign To” field. The users must be able to view complaints that have been assigned to their role. For example, the L1 helpdesk user must not be able to view complaints assigned to the L2 helpdesk and vice versa.

![](../../../../.gitbook/assets/Screenshot\_2023-05-15-10-20-50-55\_40deb401b9ffe8e1df2f1cc5ba480b12.jpg)

Filters\
The user can apply filters in multiple parameters as follows:

* Complaint Type: The user can select the complaint type from the dropdown
* Administrative Area: The area of complaint.
* Status: Refer to the list of statuses detailed above.

A button to clean all filters must be available at the bottom of the page. An “Apply Filter” button must be available to set the filters and route the user to the inbox and display the filtered complaints.

![](../../../../.gitbook/assets/Screenshot\_2023-05-15-10-20-58-77\_40deb401b9ffe8e1df2f1cc5ba480b12.jpg)

Search By

A user must be able to search for one or more complaints by using the following search parameters (must support passing multiple search parameters):

* Complaint Number
* Mobile Number
* Administrative Area

After providing the appropriate search parameters, the user must click on the “Search” button located at the bottom of the screen and must be routed to the inbox which displays the search-appropriate search results.

![](../../../../.gitbook/assets/Screenshot\_2023-05-15-10-20-53-65\_40deb401b9ffe8e1df2f1cc5ba480b12.jpg)\


Complaint Summary

A summary screen must be displayed when the user clicks on the ‘Open’ button located on the complaints card.

![](../../../../.gitbook/assets/Screenshot\_2023-05-15-10-20-40-87\_40deb401b9ffe8e1df2f1cc5ba480b12.jpg)

Actions

The “Take Action” button at the bottom of the screen must open a pop-up displaying all possible actions that the user can take. The actions available to address the complaint are as follows:

* Resolve Complaint
* Assign to P2
* Reject Complaint
* Close

The close button collapses the overlay and takes the user back to the complaints summary screen.

![](../../../../.gitbook/assets/Screenshot\_2023-05-15-10-21-15-51\_40deb401b9ffe8e1df2f1cc5ba480b12.jpg)\


Assign Complaint

If the user wants to assign any project to P2, she must click on the assign button which opens this screen. The date of assigning the complaint is user input which can be filled in with the help of the calendar icon within the field.&#x20;

In the "assigned to" field, the user needs to select the person to whom she wants to assign that complaint. There is an additional comments field in which the user can provide any remarks if she wants. The user can attach any supporting documents such as photos, documents, etc.&#x20;

At the bottom, there is a cancel button which takes the user back to the complaint summary screen, and an assign button which assigns the complaint to the selected person.

![](../../../../.gitbook/assets/Screenshot\_2023-05-15-10-21-18-54\_40deb401b9ffe8e1df2f1cc5ba480b12.jpg)

Confirmation Screen

If the complaint has been assigned successfully, then the following screen must appear.![](../../../../.gitbook/assets/IMG\_20230515\_103533.jpg)

Landing Page (Common page)

A landing page must be available to the user to access all available modules.\
\
![](<../../../../.gitbook/assets/Screenshot (279) (1).png>)

Helpdesk (Desktop View)

When the user clicks on complaints on the home screen, then this screen must appear. On the top left, there is an option to file a new complaint, view reports. Besides, there are search fields for different parameters, such as complaint number and mobile number, and the search button to execute the search action. There is a clear search button below the search one if the user wants to clear the search parameters.

Below the new complaint and reports buttons, there are filters available to apply over the results. The filter parameters are the same as that for the mobile view.

The complaints are displayed in a horizontal format with the same values for mobile view. The user can click on the entire area of a particular complaint.

At the bottom, there are forward, backward, first page, and last page arrow buttons along with the page number information as displayed on the screen.

![](<../../../../.gitbook/assets/Desktop - 123 (1).png>)\


Complaint Details

When the user clicks on a complaint, the details screen appears which provides the entire information of that complaint. The summary includes the same information mentioned in the card along with the additional comments/remarks, and photos provided by the complainant.

There is a "Take Action" button at the bottom. When the user clicks on it, the actions appear above the button as displayed on the screen. The actions include resolve complaint, assign to P2, and reject complaint. If the user clicks on any blank area on the screen, the actions collapse.

![](<../../../../.gitbook/assets/Frame 1054.png>)

\
![](<../../../../.gitbook/assets/Frame 1053.png>)

Resolve Complaint

If the complaint has been resolved, then the user must click on the "Resolve Complaint" button which opens this screen. There is an "Additional Comments" field in which the user can provide any remarks if he wants. At the bottom, there is a submit button that updates the complaint status as resolved.

![](<../../../../.gitbook/assets/Screenshot (289).png>)

Reject Complaint

If the user has rejected any complaint, then she needs to select the reason for rejection from the dropdown. There is an additional comments field in which the user can provide any remarks if he wants. At the bottom, there is a submit button that updates the complaint status as rejected.

![](<../../../../.gitbook/assets/Screenshot (293).png>)

Assign to P2

If the user wants to assign any project to P2, she must click on the assign button which opens this screen. The date of assigning the complaint is user input which can be filled in with the help of the calendar icon within the field.

In the assigned to field, the user needs to select the person to whom she wants to assign that complaint.

There is an additional comments field in which the user can provide any remarks if he wants. The user can attach any supporting documents such as photos, documents, etc.

At the bottom, there is a cancel button which takes the user back to the complaints screen, and an assign button which assigns the complaint to the selected person.

![](<../../../../.gitbook/assets/Screenshot (290) (1).png>)\
\
Confirmation Screen

If the complaint has been assigned successfully, then the following screen must appear. If the complaint could not be assigned, then the text must say, “Complaint Not Assigned.”![](<../../../../.gitbook/assets/Screenshot (291) (1).png>)\


New Complaint

When the user clicks on the “New Complaint” button on the complaints screen, then this screen appears. The details captured are the same as that entered by the complainant. When the details are entered, the user needs to click on the submit button which opens the confirmation window over the same screen. If the user clicks on the cancel button, then she is navigated back to the complaints screen

![](<../../../../.gitbook/assets/Desktop - 41 (1).png>)\


Confirmation Screen

When the user clicks on the submit button, the system confirms whether the complaint has been submitted successfully or not. There is a back to home button placed on both screens, clicking on which will navigate the user to the home screen of the helpdesk.

![](<../../../../.gitbook/assets/Desktop - 30.png>)

![](<../../../../.gitbook/assets/Desktop - 114.png>)

## Metrics to track: (WIP)

The metrics that will be tracked are as follows:

* Complaints registered.
* Complaints resolved.
