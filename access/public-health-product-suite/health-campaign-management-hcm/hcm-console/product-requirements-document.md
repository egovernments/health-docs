---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/access/public-health-product-suite/health-campaign-management-hcm/hcm-console/product-requirements-document
---

# Product Requirements Document

The challenge is around the ability of the user to use and understand technology. The user is not tech-savvy and is not expected to know concepts of JSON Files, Schemas, APIs, MDMS, Services, and any other such terms. The user is also not expected to be well-versed in high-fidelity UX/UI and needs every bit of hand-holding possible during the process of creating and running a campaign.

## Objectives&#x20;

1. Reduce set-up time for new campaigns.
2. Reduce dependence on engineering resources for setting up a new campaign.&#x20;
3. Provide the power to the end user for customising campaigns.

## Assumptions & Validations

<table data-header-hidden><thead><tr><th width="82"></th><th width="204"></th><th></th></tr></thead><tbody><tr><td>Sr. No.</td><td>Theme </td><td>Assumption</td></tr><tr><td>1</td><td>User persona</td><td>The user is well-versed with campaign terminologies and has some level of previous campaign management experience.</td></tr><tr><td>2</td><td>Device type</td><td>The product will be used as a web-based application with an internet connection.</td></tr></tbody></table>

## Role-Action Mapping

<table><thead><tr><th width="79.3828125">S.No</th><th width="256.42578125">Role</th><th>Action</th></tr></thead><tbody><tr><td>1</td><td>Campaign Manager</td><td><p></p><ol><li>Select Campaign Type</li><li>Assign Campaign Name</li><li>Set Campaign Dates</li><li>Configure Boundary Data</li><li>Configure Facilities</li><li>Configure Users</li><li>Set Rules for Delivery</li></ol></td></tr></tbody></table>

## Specifications

| Question                                                                                                                                                                                                    | Input Field Type                                                              | Validations / Limitations                                                                                                                                                                                                                                                  |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ol><li>Which campaign type do you want to run?</li></ol>                                                                                                                                                   | Dropdown single selection                                                     | Users can select only one campaign at a time. The entries in this drop-down will be pre loaded from the back end. Will provide the functionality of updating the list to the users from UI.                                                                                |
| <ol start="2"><li>What is the name of your campaign? </li></ol>                                                                                                                                             | Open text field                                                               | Limit of 50 characters.                                                                                                                                                                                                                                                    |
| <ol start="3"><li>Beneficiary type for the selected campaign is </li></ol>                                                                                                                                  | Non-editable field                                                            | The answer to this question can only be household or individual based on the campaign name selected in the previous question.                                                                                                                                              |
| <ol start="4"><li>Select the start and end dates of the campaign for the boundaries selected above. Note: This date range will be applicable to all boundaries selected in the previous question.</li></ol> | <p>Calendar selection Icon with 2 inputs:</p><p>Start Date</p><p>End Date</p> | <p>The selection will ask for 2 inputs from the user:</p><p>Start and end dates. The user cannot select start or end dates from the past. only future date selections should be allowed. By default, when the selection opens, the date should be set to today's date.</p> |

## Risk & Limitations

1. Boundary data: If the boundary data is updated regularly, then the analytics for the long-term will not have data sanity.
2. Users might have issues uploading multiple Excel sheets for targets, facility, and user data.
