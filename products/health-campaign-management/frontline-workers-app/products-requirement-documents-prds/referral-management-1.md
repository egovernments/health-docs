# Referral Management

## Table of Contents

[Background](referral-management-1.md#background)

[Target Audience](referral-management-1.md#target-audience)

[Objectives (of this release)](referral-management-1.md#objectives-of-this-release)

[Assumptions and Validations](referral-management-1.md#assumptions-and-validations)

[Process flow](referral-management-1.md#process-flow)

[Specifications](referral-management-1.md#specifications)

[Design](referral-management-1.md#design)

## Background

This document describes the need and scope of adding a referral management module  within V2.0, explaining the module’s features, specifications, purpose, and functionality. It also provides the descriptive view of the application along with the specification of each element.

In health campaigns, it is common for beneficiaries to show some symptoms against the dose administered, such as fever, body ache, etc., which are not alarming. But for circumstances where the dose may have adverse effects on the beneficiary and they require medical assistance. In such cases, the beneficiaries are referred to a healthcare facility for treatment. This module helps to track the referral details for a beneficiary and ensure the authenticity of genuine referrals done within the campaign.

## Target Audience:

This document is intended for the engineering and platform (tech teams), product management and implementation teams to agree on requirements for the Health Campaign Management (HCM) Platform.

## Objectives (of this release)

1. Referral Management:&#x20;

&#x20;     \- Enable actors to collect referral details of beneficiaries before as well as after administering the dose.

&#x20;    \- Capture details of the referred facility, referring individual, and reasons for referral.

2. Enhance user experience:

&#x20;     \- Simplified forms for capturing referral information.

3. Ensure authenticity of data:

&#x20;      \- Referral details to track the beneficiary and avoid fraudulent referrals by verifying the collected data.

## Assumptions and Validations

| Sr. No. | Theme             | Assumption                                                                                                                                                                                                                                                                                                                      |
| ------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | Refer beneficiary | <ol><li>The beneficiaries may be referred before or after administering the dose.</li><li>The actors must refer the beneficiary to a healthcare facility and collect the data on the same date.</li><li>The reasons for referral can be multiple and the user can elaborate the details within the referral comments.</li></ol> |

## Process Flow

![](https://lh5.googleusercontent.com/3aIsfLUg1n-v5kNmcVxDqX4\_d9vJv62GKo7WWslisD5RfARGtL2D6pwEab0aAMZbSPzLo3QWYRv2bpaXD3sxOtCNkxW442mjH7lhbDUa8R7ncnLuSwPixSexnud09\_hhbcz0pYMZde22s0AZA9YGr7g)

## Specifications

| Field                        | Data type             | Data validation                                                                                           | Required (Y/N) | Comments                                                  |
| ---------------------------- | --------------------- | --------------------------------------------------------------------------------------------------------- | -------------- | --------------------------------------------------------- |
| Refer Beneficiary            | Button                | The user must refer a beneficiary if they require medical support.                                        | NA             | <p><br></p>                                               |
| Date of Referral             | Date                  | The date is populated by the system and must be non-editable.                                             | Y              | <p><br></p>                                               |
| Administrative unit          | String                | The unit is populated by the system and must be non-editable.                                             | Y              | The user can change the boundary from the boundary picker |
| Referred by                  | Search-based dropdown | The system must populate the team code from the user’s profile and it must be editable.                   | Y              | <p><br></p>                                               |
| Referred to                  | Search-based dropdown | The system auto-populates the resource which is editable.                                                 | Y              | <p><br></p>                                               |
| Reason for referral          | Multi-checklist       | The system auto-populates the quantity which is editable.                                                 | Y              | <p><br></p>                                               |
| Referral Comments            | String                | Additional details for referral.                                                                          | N              | <p><br></p>                                               |
| Was the delivery successful? | Binary (Yes/No)       | <p><br></p>                                                                                               | Y              | <p><br></p>                                               |
| Reason for not delivering    | Dropdown              | The field must be dynamic and appear when the user selects ‘No’. The list must be configured in the MDMS. | Y              | <p><br></p>                                               |

## Design

Find the mock ups below:

| <p>Refer Beneficiary(Household Card)</p><p>When the user clicks on ‘Open’ button on the beneficiary card or scans a voucher on the search household screen, the household card is opened, which contains the household details. </p><p>Based on campaign type, the deliver intervention button is displayed either on each individual’s card or the entire household.</p><p>For individual based campaigns, the button appears only on the individual’s card that was searched or scanned. </p><p>The user must click on the ‘Refer Beneficiary’ button in case the beneficiary is suffering from any illness and needs medical treatment before delivering intervention.</p> | ![](https://lh4.googleusercontent.com/E-zN0PSWRsiA6nb5FSZgLdGkV7eTEKYeGLQCRmY7zBg\_dLLco9IrJzNU-QvKyM7dSbLxoC9fent2CadAL1XdbwTPOgMymgs50Ad5dSiFBFAPX3IY44JxxfQ3W41l-ke9p7YAZ47xLwSjGfR4y8dLz-c)                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>Refer Beneficiary(Adverse Events)</p><p><a href="https://docs.google.com/document/d/1Wadir0k1ftXiaPSLdwZGGaiZ9JxYNfYpqKacKxQQAfU/edit">https://docs.google.com/document/d/1Wadir0k1ftXiaPSLdwZGGaiZ9JxYNfYpqKacKxQQAfU/edit</a></p><p>After administering the dose, if the user observes any adverse events, he captures the details on this screen and clicks on ‘Refer Beneficiary’ button which navigates the user to referral management flow.</p>                                                                                                                                                                                                                     | ![](https://lh4.googleusercontent.com/9i4NY0SvS-k0o2Wfp\_Q4vztjsGfQcH-uETsHA6QI8b5mwlMgstOnPWMQp1NWKIDDNv2umkD1EpQ6fSOxjQv4z0ICynrNJH4MqpbdP7\_pqn\_Q-JX6XGPmf7Exy0-ilyts-8xQ8sI1ygGnE5k1Fv8w2AE)                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| <p>Referral Details</p><p>After clicking on ‘Refer Beneficiary’, the referral details screen appears where the user provides information for referral.</p><p>The date and administrative unit fields are auto populated by the system and are non-editable. </p><p>The referred by field automatically captures the team code from the user’s profile but can be edited.</p><p>The user must select a facility where the beneficiary is being referred to.</p>                                                                                                                                                                                                                | <p><img src="https://lh6.googleusercontent.com/KFTcUhrdZOI7u7AXeDXDImwzj-IKBjOivsyoiD_KqDPvHPb6zWCsYUGsYDOoSvFk8UgyiZ9cn99zrT2514K9MHdUML0ugvdIWoHdqccU_sKkyrxpiBuGs-bFoPHhLbkC0l4vMkyHGfJimx7DcAevLsA" alt=""></p><p><img src="https://lh4.googleusercontent.com/_OgIOuXbN8e_XF0J-rBnwE7nFnm1wCpzyOMVsuqLTa70zzr3GqRlyUNiPoncJTvvBcTM1mEWTIv84kRk_8qhOD367YQA8hG90MKRzbPSg7f8qDub91CYrhfVpofFOFytO9E140qfEyyiJNwo3IE2m_Q" alt=""></p>                                                                                                                                                                                                                    |
| <p>Search Facilities</p><p>When the user clicks on search icon in the ‘Referred to’ field, this popup screen appears, which contains the list of all the health facilities within the campaign. The user can search for any facility by typing within the search box, and it will display the related search results.<br>When the user selects any facility, the screen collapses and the value is displayed within the field. The user must click again on the search icon if he wants to change the facility.</p>                                                                                                                                                           | ![](https://lh6.googleusercontent.com/9YbKUNqIhcLPMCB6PXB46xc1EDtANfYraUNu\_4c2cyyDNo7RzXzaYS64zwxnwtJ8DGxQInxNIICmJpLBE2P6ygExLeDLwTR3q-\_XKBAkYUvEMo\_QrYbjBW7VfPfRlpKYQ9eDQn\_F\_VGXK1Od5D2Tl4s)                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| <p>Reason For Referral</p><p>Users must select the reasons for referring the beneficiary. Reasons are basically the adverse events observed in a beneficiary and the user can select multiple values from the list.</p><p>Users can describe the beneficiary's health condition in the referral comments field.</p>                                                                                                                                                                                                                                                                                                                                                           | ![](https://lh6.googleusercontent.com/FtzdMdST0bDyh8uuadgbe8SAjk9YjPYNjKNyr4tgRAnZ8EqnUnYqfuhzDagyr3rpZj-jBSsUtjfj3OlRn57tjDUqjFlmfVj\_YICq8-hwpIBHEpJsb-DtINTv-Vf22F03Z9UKooAfXMhfPAchT5z9Au8)                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| <p>Was the delivery successful<br>The user must provide the details for whether the delivery was successful or not.</p><p>If the user selects ‘No’, an additional field must appear asking for the reason of non-delivery.</p><p>The drop down must have the reasons that are configured in the MDMS.</p><p>After selecting the response, the user must click on the ‘Submit’ button, which opens the acknowledgement screen stating that the delivery is successful, and the user can go back to the search household screen.</p>                                                                                                                                            | <p><img src="https://lh5.googleusercontent.com/3ySRAlYE1Th3zpsUBofqaacjXU--CH_v-p0RxzQSaxoOe2FeoFT2GYR7DX5kXOEZXPTXQr_Rviko1HcYDh8b-UyF6qykRKxP3QVGt_fKXKQ39TFuARJL_o6l2-x8JDi8XcnnIwb2_KGqoOTCjzYGW8I" alt=""></p><p><img src="https://lh6.googleusercontent.com/QTZDBr05t_DpoZ4_7ES3XiX2LTEF2jVMxh8sYl-RNcbOcdAtu1OqS09chVlnjr7WQoxx2EeNtNAGgSfQs8Mno7xJB2WNi_4o0kbndqyLBGqPPJBgbDwSnGtzVGUJvnN11KUKG8CzqP9aw690a8XzflQ" alt=""></p><p><img src="https://lh6.googleusercontent.com/6xajaukxsvhFlQyzsyJGw57sXAvDa4wfo68uzlvHkyqfZ8l-mxpamMcCoQU0ZI-VQer8BCSw9vaCCJq2Rsk90GQPBLSz9RuW7f5WsBP0mGBMjRwbtml2ooN-wSnv_jVIhgg1xOrugyvf7ZQh1UVsXwA" alt=""></p> |

