---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/ui-configuration/login
---

# Login

### 📘 Overview

The **Login** screen enables users to access the DIGIT HCM app by entering their User ID and password. It also provides a **Forgot Password** option that informs users to contact their administrator since the app doesn’t handle password resets directly.

***

### 🔁 Workflow Details

#### Entry Point

* Users are redirected to the login screen immediately after selecting their preferred language.

<div align="left"><figure><img src="../../../.gitbook/assets/image (203).png" alt="" width="207"><figcaption></figcaption></figure></div>

#### User Actions

* **Input Credentials**: User enters **User ID** and **Password**.
* **Login**: Clicks **"Log In"** to authenticate with the backend.
* **Forgot Password**: Clicks the **"Forgot Password"** button (no password reset performed within the app; displays informational dialogue).



***

### ⚙️ Technical Implementation

#### UI Components

* **Login Screen**: Defined in\
  `health_campaign_field_worker_app/lib/pages/login.dart`  \
  Login Page Location: [login.dart](https://github.com/egovernments/health-campaign-field-worker-app/blob/master/apps/health_campaign_field_worker_app/lib/pages/login.dart)
* **Widgets Used**:
  * **DigitTextFormField**: Input fields for user ID and password:  [digit\_text\_form\_input.dar](https://github.com/egovernments/DIGIT-UI-LIBRARIES/blob/master/flutter/digit-ui-components/digit_components/lib/widgets/atoms/digit_text_form_input.dart)
  * **DigitElevatedButton**: Login button component: [digit\_button.dart](https://github.com/egovernments/DIGIT-UI-LIBRARIES/blob/master/flutter/digit-ui-components/digit_components/lib/widgets/atoms/digit_button.dart)
  * **DigitToaster (SnackBar)**: Notification for login success, failure, or errors: [digit\_toast.dart](https://github.com/egovernments/DIGIT-UI-LIBRARIES/blob/master/flutter/digit-ui-components/digit_components/lib/widgets/atoms/digit_toast.dart)

#### Dialogue Integration

* The “Forgot Password” button triggers a **DigitDialog**, displaying a message prompting users to contact their administrator.

***

### 🔐 API Role–Action Mapping

| Action               | API Endpoint                       | Description                                                                               |
| -------------------- | ---------------------------------- | ----------------------------------------------------------------------------------------- |
| Login Authentication | `POST /auth/login` (or equivalent) | Sends credentials (`userID`, `password`) to authenticate user and return a session token. |
| Forgot Password      | –                                  | No backend call; purely client‑side informational dialog                                  |

*   **Login Payload Example**:

    ```json
    {
      "RequestInfo": { "authToken": "" },
      "User": {
        "userId": "string",
        "password": "string"
      }
    }
    ```
* **Login Response**: Returns a user token and possibly user role/context data to establish a session and navigation flow.
* **Access Management**: The returned authentication token governs user access across the application.
