# Forgot Password

## Overview

The Forgot Password screen is used to reset the user's password in the event the password is forgotten.

***

## 🔁 Workflow Details

* User Entry Point: The "Forgot Password" link is accessible on the **login screen**.
* User Action: Clicking on **“Forgot Password”** triggers a dialogue with the message:

> _“Please contact your administrator if you have forgotten your password.”_

<div align="left"><figure><img src="../../../.gitbook/assets/image (28).png" alt="" width="188"><figcaption></figcaption></figure></div>

***

## ⚙️ Technical Implementation

#### Code References:

* **Login Page Location**:\
  [`login.dart`](https://github.com/egovernments/health-campaign-field-worker-app/blob/master/apps/health_campaign_field_worker_app/lib/pages/login.dart)
* **Dialogue Widget**:\
  [`digit_dialog.dart`](https://github.com/egovernments/health-campaign-field-worker-app/blob/master/packages/digit_components/lib/widgets/digit_dialog.dart)

#### Components Used:

* **DigitDialog Widget**: Custom reusable dialogue box component from `digit_components`.

***

## 🔐 API Role–Action Mapping

**None**

* No backend API calls are triggered.
* No role-action mapping is required, as the feature is informational only.
