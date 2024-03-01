# Health Facility Referral Module

## Key Features

This module will enable the health facility supervisors to track referrals made by on-field health workers to different health facilities digitally via the Digit HCM app capturing all the cases of:

1. Beneficiary being referred.
2. Referral details of the beneficiary.
3. Reason for referrals and its diagnosis.
4. Based on the diagnosis chosen further details if applicable.

## User Roles

| User Role                  | Scope of Action                        | Role Description                                                                          |
| -------------------------- | -------------------------------------- | ----------------------------------------------------------------------------------------- |
| Health Facility Supervisor | Record referrals made by field workers | Record data of beneficiaries, reason for referral and diagnosis, and any further details. |

## Using the Health Facility Referral Management Module

**User Persona:** This feature will be used by workers working at a given Health Facility (HF) who will be responsible for giving the diagnosis based on the type of symptoms they observe and then do a diagnosis and provide the appropriate drugs.

**Steps for Referral Flows:**

**Step 1:**&#x20;

Login for a HF worker who will see the home screen options based on the role-action mapping and will see the option which says “Beneficiary Referral“. The options available on the home screen for HF workers apart from the Beneficiary Referral option will be defined based on the role-action mapping provided for them.

<figure><img src="../../../../.gitbook/assets/image (90).png" alt="" width="322"><figcaption></figcaption></figure>

**Step 2:**&#x20;

When the user clicks on the “Beneficiary Referral” button in the previous screen, the user will be taken to the “Search Beneficiary” screen where he/she can search for a given beneficiary by their name or a QR code voucher provided to the beneficiary.

**Search Produces Result:** If the user searches for a given beneficiary name and finds a match, he/she can click on the 'Open' button in the card for that beneficiary and view their details.

<figure><img src="../../../../.gitbook/assets/image (92).png" alt="" width="316"><figcaption></figcaption></figure>

**Search Does Not Produce Result:** If the search does not provide any results, the user can click on the “Create New Referral" button to add a new entry under the Referral module.

<figure><img src="../../../../.gitbook/assets/image (91).png" alt="" width="311"><figcaption></figcaption></figure>

**Step 3:**&#x20;

Once the user creates a new referral or opens an existing one in the previous step, he/she is taken to the Facility Details screen first where he/she needs to enter the details of the health facility they are in to attend the beneficiary. This screen will have the following fields:

1. **Administrative Unit:** This field will be auto-filled from the value available from the role-action mapping, and will be non-editable.
2. **Date of Evaluation:** This field will be auto-filled with system value and will be non-editable.
3. **Evaluation Facility:** This will be a mandatory field for the health facility worker to search and add. It is the ID used for a given health facility.
4. **Name of Health Facility Coordinator:** This is a non-mandatory field that will capture the name of the health facility coordinator who is attending the referred beneficiary.
5. **Referred By (CDD Team Code):** This is a non-mandatory field that will capture the CDD team code of the field worker who referred the beneficiary.

Once the user has filled all the fields with the relevant information, he/she must click on the 'Next' button.

<figure><img src="../../../../.gitbook/assets/image (94).png" alt="" width="364"><figcaption></figcaption></figure>

**Step 4:**&#x20;

After the user has clicked on submit, he/she will come to the screen called “Referral Details”. On this screen, the user is supposed to enter details into sections, that is, “Referral Details” and “What is the reason for referral”.

**Section 1: Referral Details**

In this section, the user must add the details to the following fields:

* **Select Cycle:** This will be a dropdown selector which will have the cycle numbers. This is a mandatory field and cannot be left empty.
* **Name of the child:** The user needs to add the name of the referred beneficiary. This field is mandatory.
* **Beneficiary ID:** This will be added by the user with the beneficiary ID of the referred Beneficiary. This is a mandatory field.
* **Age in Months:** This will be a mandatory field that will capture the age of the beneficiary being referred in months.
* **Gender:** This is a mandatory field with a dropdown having values: Male, Female, Other.

**Section 2: Reason for Referral**

In this section, the user must capture the data as to why the beneficiary was referred. The field will capture data with the help of the radio button option selector. The options are:

* Sick
* Fever
* Drug side effect in current cycle
* Drug side effect in previous cycle

After selecting one of the reasons for referral, the user needs to press 'Next' which will navigate the user to 3 different screens based on what they select in the “Reason for Referral” section.

<figure><img src="../../../../.gitbook/assets/image (95).png" alt="" width="252"><figcaption></figcaption></figure>

**Step 5:**&#x20;

Based on what the user selects in the previous step in the “Reason for Referral” section, the following 3 flows could be shown to the user:

* **If “Sick” was chosen as a reason:** If the user selects 'Sick' as the reason for eeferral in Step 4, he/she will be taken to “Referral Due to Illness” screen, where he/she will see the following list of questions:
  * **“Child evaluated to determine cause of illness”:** This will be a mandatory question to be answered with 2 options in the form of a radio button: Yes or No.
  * **Enter Comment for Diagnosis:** The answer to this question should be entered by the user in a free text form which will be a mandatory field.
  * **“Was the Child Treated?”:** This question will be answered by the user using a radio button option of 'Yes' or 'No', and it will be a mandatory question
  * **Name and Dose of the Drug:** Provide an open text field that will be mandatory.
  * **“Was the child admitted / transferred to the hospital due to serious illness?**”: This question will have a Yes/No radio button selection for it. This is a mandatory field.

<figure><img src="../../../../.gitbook/assets/image (96).png" alt="" width="254"><figcaption></figcaption></figure>

* **If “Fever” was chosen as a reason:** If the user selects 'Fever' as the reason for referral in Step 4, the user will be taken to the “Referral Due to Fever” screen, where he/she will see the following list of questions:
  * **“Was the child tested for malaria?”:** This question will have a Yes/No radio button option. This will be a mandatory field.
  * **“Result of Malaria Diagnostic Test? “:** This will be a mandatory field and based on what the user answers to this question the next set of questions for the user will open up as a nested form.
    *   **If the user chooses 'Positive' as the answer for “Result of Malaria Diagnostic Test? then he/shewill see the following questions:**

        * **Was the child admitted/transferred to the hospital due to serious illness?:** This will be answered with a simple Yes/No radio button and will be a mandatory field.
        * **Child with positive malaria test treated with anti-malarial?:** This will be answered with a simple Yes/No radio button and will be a mandatory field.
        * **Name and Dose of Anti Malarial:** This will be answered with an open text form and will be a mandatory field.



        <figure><img src="../../../../.gitbook/assets/image (97).png" alt="" width="252"><figcaption></figcaption></figure>
    *   **If the user chooses “Negative” for “Result of Malaria Diagnostic Test?, then he/she will see the following questions as a nested fForm:**

        * “**Child with negative malaria test received SPAQ in this cycle**“: This will be a Yes/No Radio button question, and is a non-mandatory field.



        <figure><img src="../../../../.gitbook/assets/image (98).png" alt="" width="256"><figcaption></figcaption></figure>


* **If “Drug side effect in current/previous cycle” was chosen as a reason:** If the user selects “Drug side effect in current/previous cycle” as the reason for referral in Step 4, he/she will be taken to  the“Referral due to adverse drug reaction” screen, where he/she will see the following list of questions:
  * **Child evaluated for adverse reaction for SP and AQ?:** This will be a simple Yes/No radio button in the form and it will not be a mandatory field.
  * **The National Pharmacovigilance has been filled out?:** This will be a simple Yes/No radio button in the form, and it will not be a mandatory field.
  * **Was the child admitted/transferred to the hospital due to serious illness?:** This will be a simple Yes/No radio button in the form, and it will not be a mandatory field.

Once all the questions in one of these flows are answered, a pop-up frame asking for confirmation will be shown for submission as shown below:

<figure><img src="../../../../.gitbook/assets/image (99).png" alt="" width="255"><figcaption></figcaption></figure>

Once the user clicks on submit, he/she will see the ”Data Recorded Successfully” screen, and the option to navigate to the home screen.



<figure><img src="../../../../.gitbook/assets/image (100).png" alt="" width="254"><figcaption></figcaption></figure>
