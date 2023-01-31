# Complaints Management v1

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

| Theme                | Assumption                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Logging complaints   | <ul><li>Not all complaints will be logged using the complaints module. Users may prefer raising complaints on WhatsApp groups/calls, and may not be registered in the system.</li><li>Complaints are most likely to be logged by users on behalf of other users (Most common use case: Supervisors raising complaints on behalf of users</li></ul>                                                                                                                          |
| Resolving complaints | <ul><li>There is a support helpdesk set up by the program which will receive all complaints raised by system users.</li><li>The support helpdesk must be responsible for reviewing all the complaints in the inbox</li><li>Depending on the complaint, the helpdesk can either resolve, reject or assign the complaint to the respective actor</li><li>Helpdesk users may create complaints on the user’s behalf, which are received over call/WhatsApp messages.</li></ul> |

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

### Statuses in the workflow

| Status name                                  | Description                                                                                                                                                                | Leads to (next status)                                                                                |
| -------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Submitted (TBD depending on design approach) | Status when a complaint is submitted but hasn’t been received by the helpdesk (to support offline use case).                                                               | Pending Assignment                                                                                    |
| Pending Assignment                           | Status when the complaint has been received by the helpdesk (in the event of a completely online system), the pending assignment must be the first status in the workflow. | Resolved, Rejected, Assigned                                                                          |
| Resolved                                     | Status when the complaint has been addressed and closed successfully.                                                                                                      | NA                                                                                                    |
| Rejected                                     | Status when the complaint is found to be invalid and rejected.                                                                                                             | NA                                                                                                    |
| Assigned To < >                              | Status when the complaint is assigned by the helpdesk to other roles in the workflow.                                                                                      | Resolved, Rejected. The possible status will depend on the workflow configured during implementation. |
| Cancelled                                    | Status, when the user decided to delete the complaint, created.                                                                                                            | NA                                                                                                    |

## Process Flow

<figure><img src="../.gitbook/assets/Screenshot 2023-01-25 at 10.46.33 AM.png" alt=""><figcaption></figcaption></figure>

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

## Risk/ Limitations:&#x20;

Addressed in the Out of Scope section.

## Out of scope:

* Re-opening of complaints
* Auto-escalation of complaints
* Auto-routing of complaints
* Sharing feedback on complaint resolution
* Notification to users on status change
* SLA tracking

## Specifications

| Field                        | Data Type       | Data Validation                                                       | Required (Y/N) | Comment                                                                                                                                                  |
| ---------------------------- | --------------- | --------------------------------------------------------------------- | -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Complaint type               | Dropdown        | Only one complaint type must be selected.                             | Y              | <p>Values to be configured. </p><p>If type is “Other”: Display text box to enter type.</p><p><br></p>                                                    |
| Date of complaint            | Date            | System fetches the current date.                                      | Y              | Must be non-editable (no action required by user).                                                                                                       |
| Administrative area          | String dropdown |                                                                       | Y              | For mobile view: Admin area must be populated based on value set in the location picker For Web view: Select from list of assigned projects/ boundaries. |
| Complaint raised for         | Boolean         |                                                                       | Y              | Options available: Self and other.                                                                                                                       |
| Complainant’s name           | String          | If “self”: Name must be populated as entered in the user’s profile.   | Y              | If “Name” is blank in the user’s profile, the text field must be empty.                                                                                  |
| Complainant’s contact number | Numeric         | If “self”: Number must be populated as entered in the user’s profile. | Y              | If “Number” is blank in the user’s profile, the text field must be empty.                                                                                |
| Supervisor’s name            | String          |                                                                       | N              |                                                                                                                                                          |
| Supervisor’s contact number  | Numeric         |                                                                       | N              |                                                                                                                                                          |
| Complaint description        | String          | Max limit of description: TBD                                         | Y              |                                                                                                                                                          |
| Upload photo                 | Media           | Max size of media: TBD                                                | N              |                                                                                                                                                          |
| Complaint number             | String          |                                                                       | Y              | Unique ID generated by the system.                                                                                                                       |
| Reason for rejection         | Dropdown        |                                                                       | Y              | Must be configurable during impel.                                                                                                                       |
| Assign to                    | Dropdown        | Mandatory if action taken to assign.                                  | C(Y)           | Must be configurable during impel depending on the workflow. Default value: Assign to L2.                                                                |

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

![](https://lh4.googleusercontent.com/qba1SMZr7clIqFQkM2jrCv-nA7muWXN5B43yxYNMS-iIKUCL8eJKsONmUJ8bhquxLhEPI7JWSE2kOnGuq8Xdd0gMP0SOL2SFSZ5Mt1QeOrxorAI47DNoRhxOuBsux9B0RUKlou\_14gCtwb3eSqbbrTxgwrtum4TAPHtq1y5vOTJcRTVOY9ag6shnbtPVkw)

### Complaints

When the user clicks on the complaints, she is navigated to the “My Complaints” screen, which consists of two actions:

* File a complaint (primary action): Clicking on this must open the complaint type screen.
* View previously logged complaints.

![](https://lh3.googleusercontent.com/jPFx80yQfJmuLhqGTQpaXbw4L2Av5B0jgZ7lLwgLWJh3hOLLCb7eN-YLHo2XOi9qsJedDWjrQEAJuRCD62\_cVk5hjdL1wiqKmNtGZKbdi2KmJ9pwYrkSu3QjRQR-LUrq5fDOxa\_2V2XyR2i42aOw-IkLoJfn-Yb9uLk2c\_B0yrMGR4NKvi2Ykv8p-1s6nQ)

## File Complaint Workflow

Complaint Type

When the user clicks on file a complaint, the complaint type screen appears. The user must select the type of complaint from the list, which must be configurable (to be configured during implementation as per program requirements).&#x20;

There is a ‘Next’ button at the bottom of the screen, clicking on which, the user is navigated to the complaint details screen.

![](https://lh3.googleusercontent.com/R1bIO15j-Aar3yxPjYYnxYFn4Uz9r-GwzdgXHU-yOYE4U1GOBgXEW3puIypHa7Xh4u5E5wFXU2ETaAZttq\_olt6V7agP3rZRsvntW47DsksyGxDxAB60iRJGLVMG9-DtRscH5pKgywFTcOvtb8iXNCXV7KdYbmufOHGT1jvQib-Q04RkFASTR7TSEIFJpw)

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

![](https://lh3.googleusercontent.com/lzHyVio2kwsmMnqijOwFWMHOAcR25I-KDLaKDt-BNnyG\_K4pu5OnblpB3svi6uTOn4qfstYrdKq8U\_pmMx\_fJDAgTdxCaVC3jnvhOBKddn609Y053u6MmdqdZxv73bghnmeZX2-nwRNBMA8JhlV1PHPvBFzkmuIZRPRwr10zY5nDUU5nhtG0UdAYnHW6Xg)\


Confirmation Screen

When the user clicks on the submit button after providing all the complaint details, the confirmation screen appears, which provides information on whether the complaint has been submitted or not.

* If the complaint has been submitted, then there must be a back to home button below the message. When the user clicks on it, she must be navigated to the home screen.
* If the complaint has not been submitted, then there must be two buttons available; Retry and Back to Home.

![](https://lh4.googleusercontent.com/UEcCOFO7O6xjJepgKWLGXKOH\_9om8ZPj-nXwOaZnzTJLIhW\_KUTvq15LZV4IcotlRbXG-y1bp14NAWdC9-RggC9lIoSFxDH-sePaIeAhJtUx3HRxgK6YH96ddim5pplSxUJUXvFACkwTm8f3yJsaqsehbWSqwmN9oEfsGmjMRp0chukqU3cQdq8NuKCm4Q)

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

![](https://lh4.googleusercontent.com/LfJGfBINQK83IlDuUUDmQawdelnGoVM7h9\_FQWCR04EoWmJ72ZD6GoySkB1AC4sa3Y02LnDipyXbszMmm4aZyyaWjFqVWZUMz6fLcFe9sZuhkx2-Pitl7zoWRg5Sf2Xs--EXCZfD-JpCxsZ\_CqdurdLC0RLRX9zsPurb4ofFLgWte8mqtIqVskjwiKy77A)

Filters\
The user can apply filters in multiple parameters as follows:

* Complaint Type: The user can select the complaint type from the dropdown
* Administrative Area: The area of complaint.
* Status: Refer to the list of statuses detailed above.

A button to clean all filters must be available at the bottom of the page. An “Apply Filter” button must be available to set the filters and route the user to the inbox and display the filtered complaints.

![](https://lh6.googleusercontent.com/tNyBsVXFi1a\_SOe2d-8vU86VPYLbh9k6K1uZ\_ZN8WkQpxy\_wrBiBTnN74oyegsrB2l6HDICFV1BwEIx6pQQt--lAhWaNW39PU7xsUbvB66XD3nfOGC\_JsDuy13gPHoqx2qx8SFUXhmHAuw3QZ1YPzM9Mgusx2AZnHjGmGy2ua98g7z3lZ1R7K9WDbxr9Nw)

Search By

A user must be able to search for one or more complaints by using the following search parameters (must support passing multiple search parameters):

* Complaint Number
* Mobile Number
* Administrative Area

After providing the appropriate search parameters, the user must click on the “Search” button located at the bottom of the screen and must be routed to the inbox which displays the search-appropriate search results.

![](https://lh3.googleusercontent.com/hHDLcxEOfRSfkT7AmU8ccOdkHwniBuK5A2SObxP9hHsou-qRTPoE9vCMv-0y8SuoLQIV4jToqvwCtea3zLG6\_SL6nfE1rwmQAdr8\_fOEAv6cCwGspQ2--aAybgDcyKeuErlJVRY7o1ZugiAjtaxBuY-m6VataHgGWggAsApiHjP7gIOnsiZhwqRnsQAxSA)\


Complaint Summary

A summary screen must be displayed when the user clicks on the ‘Open’ button located on the complaints card.

![](https://lh3.googleusercontent.com/C7ix80lv5XPkrmalCP\_IfdpDeyQQ2eNmcHMqFKzWa-y9HF8GoVDMwdKKW5YDc3akEOibyK9J5fJCz04QDUj1OMnbsZ5L1gsV2rtWvTeAX-mf8IOvvwgBR4yn37xmj8mUQx6Jym0rmHefXdHQrm02wLg1u4UPBsWjGIUkfRstCU5JCB25xgE\_C1aj2mhx8A)

Actions

The “Take Action” button at the bottom of the screen must open a pop-up displaying all possible actions that the user can take. The actions available to address the complaint are as follows:

* Resolve Complaint
* Assign to P2
* Reject Complaint
* Close

The close button collapses the overlay and takes the user back to the complaints summary screen.

![](https://lh6.googleusercontent.com/VzYV1yo1h\_miOzuK3W23xCyoNbejsfku3Mev5ELwVOO9Fnm8l7iJEPomcS\_CLxqrA9jqt8Y585PQm3h9TfJ\_LmX-ptBhb\_csIAe7bMwVAKlw\_\_FRPVZJQKIblOzOHqIzTzaIdJXpA-9SBsKSq-ObWwsJ5Qxu4veCpw6WSjjrpGOKB08Ba8LeyeQ8fp0tzw)\


Assign Complaint

If the user wants to assign any project to P2, she must click on the assign button which opens this screen. The date of assigning the complaint is user input which can be filled in with the help of the calendar icon within the field.&#x20;

In the "assigned to" field, the user needs to select the person to whom she wants to assign that complaint. There is an additional comments field in which the user can provide any remarks if she wants. The user can attach any supporting documents such as photos, documents, etc.&#x20;

At the bottom, there is a cancel button which takes the user back to the complaint summary screen, and an assign button which assigns the complaint to the selected person.

![](https://lh5.googleusercontent.com/p-zkbQ76ivQ1c8SQEq0fleUlE-OMJrc7AoxeJcAC3bVumQxztCb\_NbB9RcgoKgSxADzWwMe5XTTpFVetQLIFZBhXnK0XpEs1i-YbbAifFeHaveFm0VeVXNel3zaC\_DImP--RJpuQZwlLR35ER3rMpkhzDGiOT4RgsUZF0h-aKryhFxySqEL5oWt5OOIWdQ)

Confirmation Screen

If the complaint has been assigned successfully, then the first screen must appear. If the complaint could not be assigned, then the second screen must appear. There is a "Back to Complaints" button on both screens which navigates the user to the complaints screen.

![](https://lh6.googleusercontent.com/Lixo5ZC-BgUxcUBk9sQ-e4IYULbCdEgfiIed6OsQsPmvzthBueWe9Vx5FV1mDXU74hVmC5vWVg6tGxzSb0xtq7upT6UX4gIttpboc2aGVXWK28BYuxfpkmMWy-FwraQkuPSr-F\_Yp8pHzWu-YWfdyvwgRO6tBM6Gl4UFHG4Pomg98UTaadoJzJIjPlQbIQ)

Landing Page (Common page)

A landing page must be available to the user to access all available modules.\
\
![](https://lh5.googleusercontent.com/ADi\_OBX6mxS-EfsjqxkegiWnu7s85pg5LknFq0j1wHgvk2mpLmSelwu\_lDUQwX7q0Xa4TjPjVZw8JCw5QxZNOKES1EnO2P4w-bbHmeY1SfNSgyicrzuTww-0Z217kl2kcd0Z7Jx238jOK4w9tymJoP1IhqHwsUleX5PQfDdh8mUi2Rx33ZZTsUnUlTQOqg)

Helpdesk (Desktop View)

When the user clicks on complaints on the home screen, then this screen must appear. On the top left, there is an option to file a new complaint, view reports. Besides, there are search fields for different parameters, such as complaint number and mobile number, and the search button to execute the search action. There is a clear search button below the search one if the user wants to clear the search parameters.

Below the new complaint and reports buttons, there are filters available to apply over the results. The filter parameters are the same as that for the mobile view.

The complaints are displayed in a horizontal format with the same values for mobile view. The user can click on the entire area of a particular complaint.

At the bottom, there are forward, backward, first page, and last page arrow buttons along with the page number information as displayed on the screen.

![](https://lh3.googleusercontent.com/9vRIqJxlB1WJnhfjfG\_aNskp5mSJ\_2nZ\_PtXy-ecGI7iwy59GQNjhaMc6FodsF7VZbVOBHjzrmGbBxYylrANrE31wVGj6gW8HXxBzn74IVQcJqK-9Tt6S6OfTTc-TQ8zBAKNlF7mTjjjZ8GELFSu30x3lmVKmxRmSrZecztdwHdvaHdDKo-Y2UewcH-oZQ)\


Complaint Details

When the user clicks on a complaint, the details screen appears which provides the entire information of that complaint. The summary includes the same information mentioned in the card along with the additional comments/remarks, and photos provided by the complainant.

There is a "Take Action" button at the bottom. When the user clicks on it, the actions appear above the button as displayed on the screen. The actions include resolve complaint, assign to P2, and reject complaint. If the user clicks on any blank area on the screen, the actions collapse.

![](https://lh6.googleusercontent.com/mjN6ctLMI3EepxMKVpcGAnaz3ukkBA994Y1GFDRaxynpgZW6UrJwTD5ncdaNeMx9E49KiQPdkdpC2IwM8uTUKu09E4nJJEa0UkCaYUOwwovXAwH4bcXwgP03LzMfRrRJm0riRgwAJkMYxPsplKklExtOIDdB7p1HcF4JR2OhC8\_Y\_M542PY1zap\_QLrQIw)

\
![](https://lh5.googleusercontent.com/uSwuZbrNY7zao28OaIGBiMeTt0IXmWZktnutsdOHIQCG0qJhomBocQ2hqf9l\_Z7ejoh9M7jt1jumXh40GmGd\_iCXvKivGJDVHIlejRLlhs83lLN34AQFZWv9MWNru0NEIm7rk45tCt\_JBJO2SGjAYy9wVoF3WwSBmSuavgsJxQL9u4izGfB1gOUYiAeffQ)

Resolve Complaint

If the complaint has been resolved, then the user must click on the "Resolve Complaint" button which opens this screen. There is an "Additional Comments" field in which the user can provide any remarks if he wants. At the bottom, there is a submit button that updates the complaint status as resolved.

![](https://lh3.googleusercontent.com/63lOU1UE5ygWt5cVqnyzWwsa6NjrbWe3Hbd3O0a2bfvzCiQXqvrqQreE4dkJ1h6F8Bx2l57RRuMdc8tgbPPmwrjObiF9bcXIJ0qZ0eYAJ8NwwqoDoHUxwTwBZbD6ebWdk5vO5azrQRW3XxwIqpv\_8KBNUDlZ9-uz6t9W4ayJ\_7TGcSnQ2NFZGJwwBTDwuw)

Reject Complaint

If the user has rejected any complaint, then she needs to select the reason for rejection from the dropdown. There is an additional comments field in which the user can provide any remarks if he wants. At the bottom, there is a submit button that updates the complaint status as rejected.

![](https://lh4.googleusercontent.com/eTO3DZD21y9R36PzVCKhcPEMgnbYxKD2I3MRZXmkKJ8zsHAhheJAQGRPCMP\_jDBcFuGwkcjI\_q8ARyz-4RQdUVPefYYyzs9K\_40Um9g6xPBNOlnrYWhpqa32OWnndE7z3w\_bOocXDcOHyGlWrTfNscXbGiLf65ldSE0Tpt1eUxeAUiXWPhUzGGdWUpoghA)

Assign to P2

If the user wants to assign any project to P2, she must click on the assign button which opens this screen. The date of assigning the complaint is user input which can be filled in with the help of the calendar icon within the field.

In the assigned to field, the user needs to select the person to whom she wants to assign that complaint.

There is an additional comments field in which the user can provide any remarks if he wants. The user can attach any supporting documents such as photos, documents, etc.

At the bottom, there is a cancel button which takes the user back to the complaints screen, and an assign button which assigns the complaint to the selected person.

![](https://lh4.googleusercontent.com/6PpBGC808uwstKS5dMxbBvRLkgZ6O2g5PlZqDHGE0cTBu8DQdFVKVdsRpLMSX14nj8kJ0vWTu5262fJBtaZ1v6A5OPushhGlw1geggsBQjQ7EEc2qcH4UYG5Rt5aK800F6QOFehN-nYpvm47uvnvv4kI6jfYsJimjzvZFClo8CeTwl-Q3QYIvVlz2kOBhg)\
\
Confirmation Screen

If the complaint has been assigned successfully, then the first screen must appear. If the complaint could not be assigned, then the text must say, “Complaint Not Assigned.” There is a back to complaints button on both screens which navigates the user to the complaints screen.

![](https://lh5.googleusercontent.com/Pfjeh5HGBODqcgV5f7Lbi-n3lDnh0aKSeViZuPM-kLnPKDhA\_nt19iqxqVVBrsMDBj7tjCWgoy-KoINqS3E4EEDTYdR8UwQlYW3MM84JnwOzVfjP645M2q1\_FeNv00IiX9T99FeU4CKVXgDa1C2xFMI0uU7npgJ7AKMoGuseTNMvinx64nhRY-QIx1Quow)\


New Complaint

When the user clicks on the “New Complaint” button on the complaints screen, then this screen appears. The details captured are the same as that entered by the complainant. When the details are entered, the user needs to click on the submit button which opens the confirmation window over the same screen. If the user clicks on the cancel button, then she is navigated back to the complaints screen

![](https://lh5.googleusercontent.com/RurBQArJceJzb4YsplA7RU47QcA-HRyLgeZbsXN1oQW-Tm-th1cdZtQ3ceRaWRP8lrmi6pgenNlEoHBznVQOsvpuBf7EBqfPJNb1wQEtZbrAKpSIQapGx6F6xwNMQgK8dbmYYwHrU6brWLbr6VCuqys3Ag6JRnBQk-hguo2n7lvj7K9rxoIr6-AonLr0Ew)\


Confirmation Screen

When the user clicks on the submit button, the system confirms whether the complaint has been submitted successfully or not. There is a back to home button placed on both screens, clicking on which will navigate the user to the home screen of the helpdesk.

![](https://lh4.googleusercontent.com/Mq44hartNKb5FGraapEHnHtf3nozeB\_PNDUQHMlcTbubOIkxDfb8wLuI8DvaNGvtbJ6cfIKPyhXA6UgoX7xcoBWsqAAhpdSmcoqo3t2s9FZHHsFomw671LoKOkLCCKq7DuKsekNzj6phk3FYMaDti0z6dZeqMauOms2oiKLhF-X47gFi-HvMpX-YA-NMVg)

![](https://lh6.googleusercontent.com/FONMRZDFCmkHIOL56kV7wKx858LxPo8BJWo7z6GOZgx29H\_OMECqpRlWx9KT8vq-UCraV9pruCuu38qUbxWj2HSZdbpacuiCwzjMgGzw5TmiWIMlg2z--CnS1UiaOecX6IgK4N96o-Ko1B3zXS4yr9EDt-ND1h6Iyy8rFurw46ZLp8eiSV1UI1l9LN8bpA)

## Metrics to track: (WIP)

The metrics that will be tracked are as follows:

* Complaints registered.
* Complaints resolved.\


[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
