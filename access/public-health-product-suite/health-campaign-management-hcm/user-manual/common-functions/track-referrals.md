---
description: An illustrative guide to using the Health Facility Referral feature
---

# Track Referrals

## Overview

This feature enables the health facility supervisors to track referrals made by on-field health workers to different health facilities digitally via the DIGIT-HCM app.

## Key Features

&#x20;It captures all the cases of:

1. Beneficiaries referred
2. Referral details of the beneficiary
3. Reason for referrals and its diagnosis
4. Based on the diagnosis chosen, further details are provided if applicable

## User Roles

| User Role                  | Scope of Action                        | Role Description                                                                          |
| -------------------------- | -------------------------------------- | ----------------------------------------------------------------------------------------- |
| Health Facility Supervisor | Record referrals made by field workers | Record data of beneficiaries, reason for referral and diagnosis, and any further details. |

## Steps

Log in as a health facility worker. The Health Facility Referral feature enables workers at the given Health Facility (HF) to provide a diagnosis based on the type of symptoms they observe and prescribe the appropriate drugs.

* Click on **Beneficiary Referral.**

{% columns %}
{% column %}
<figure><img src="../../../../../.gitbook/assets/image (148).png" alt="" width="188"><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src="../../../../../.gitbook/assets/image (150).png" alt="" width="188"><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

* Enter the beneficiary name in the Search Beneficiary screen to filter the view of the beneficiary. &#x20;
* Click on the **Open** button on the beneficiary card to view the specific details.
* Click on the **Create New Referral** button to add a new entry in the Referral module, in case the beneficiary is available in the search.

{% columns %}
{% column %}
<figure><img src="../../../../../.gitbook/assets/image (149).png" alt="" width="188"><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src="../../../../../.gitbook/assets/image (152).png" alt="" width="188"><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

* Enter the details of the health facility the beneficiary is mapped to in the **Facility Details** screen. The details include:
  * **Administrative Unit:** This field will be auto-filled from the value available from the role-action mapping, and will be non-editable.
  * **Date of Evaluation:** This field will be auto-filled with a system value and will be non-editable.
  * **Evaluation Facility:** This will be a mandatory field for the health facility worker to search and add. It is the ID used for a given health facility.
  * **Name of Health Facility Coordinator:** This is a non-mandatory field that will capture the name of the health facility coordinator who is attending the referred beneficiary.
  * **Referred By (CDD Team Code):** This is a non-mandatory field that will capture the CDD team code of the field worker who referred the beneficiary.
* Click on the **Next** button.
* Enter the **Referral Details**. Referral details include:
  * **Select Cycle:** This will be a dropdown selector which will have the cycle numbers. This is a mandatory field and cannot be left empty.
  * **Name of the child:** The user needs to add the name of the referred beneficiary. This field is mandatory.
  * **Beneficiary ID:** This will be added by the user with the beneficiary ID of the referred Beneficiary. This is a mandatory field.
  * **Age in Months:** This will be a mandatory field that will capture the age of the beneficiary being referred in months.
  * **Gender:** This is a mandatory field with a dropdown having values: Male, Female, Other.
* Select the applicable option to answer **What is the reason for referral.**
* Click on **Next** to proceed. Select the relevant options based on the selected reason for referral.

{% columns %}
{% column %}
<figure><img src="../../../../../.gitbook/assets/image (153).png" alt="" width="188"><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src="../../../../../.gitbook/assets/image (154).png" alt="" width="188"><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

* **If the selected option was Sick:** Below are the options available if the user selects Sick as the reason for referral:
  * **Child evaluated to determine cause of illness:** This will be a mandatory question to be answered with 2 options in the form of a radio button: Yes or No.
  * **Enter Comment for Diagnosis:** The answer to this question should be entered by the user in a free-text form, which will be a mandatory field.
  * **Was the Child Treated?:** This question will be answered by the user using a radio button option of 'Yes' or 'No', and it will be a mandatory question
  * **Name and Dose of the Drug:** Provide an open text field that will be mandatory.
  * **Was the child admitted/transferred to the hospital due to serious illness?**: This question will have a Yes/No radio button selection for it. This is a mandatory field.
* **If the selected option was Fever:** If the user selects 'Fever' as the reason for referral, the following options are available:
  * **Was the child tested for malaria?:** This question has a Yes/No radio button option. This is a mandatory field.
  * **Result of Malaria Diagnostic Test?:** This is a mandatory field, and based on the response to this question, the next set of questions opens up as a nested form.
    * **If the user chooses 'Positive' as the answer for “Result of Malaria Diagnostic Test? then  the following questions are displayed:**
      * **Was the child admitted/transferred to the hospital due to a serious illness?:** Answer  Yes/No. This is a mandatory field.
      * **Child with positive malaria test treated with anti-malarial?:** Answer Yes/No. This is a mandatory field.
      * **Name and Dose of Anti-Malarial:** Respond with the name and dose details.

{% columns %}
{% column %}
<figure><img src="../../../../../.gitbook/assets/image (155).png" alt="" width="188"><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src="../../../../../.gitbook/assets/image (156).png" alt="" width="256"><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}



* **If the user chooses “Negative” for “Result of Malaria Diagnostic Test?, following questions are displayed:**
  * “**Child with negative malaria test received SPAQ in this cycle**“: Answer Yes/No.
* **If “Drug side effect in current/previous cycle” was chosen as a reason:** If the user selects “Drug side effect in current/previous cycle” as the reason, the“Referral due to adverse drug reaction” screen appears with the following questions:
  * **Child evaluated for adverse reaction for SP and AQ?:** Answer Yes/No.
  * **The National Pharmacovigilance has been filled out?:** Answer Yes/No.
  * **Was the child admitted/transferred to the hospital due to serious illness?:** Answer Yes/No.

Once all the questions in one of these flows are answered, a pop-up frame asking for confirmation will be shown for submission as given below:

{% columns %}
{% column %}
<figure><img src="../../../../../.gitbook/assets/image (157).png" alt="" width="255"><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src="../../../../../.gitbook/assets/image (158).png" alt="" width="254"><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

The message Data Recorded Successfully appears on clicking the Submit button.
