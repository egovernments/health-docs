# User Login

Find the mock-ups below:

### Language Select

When the user opens the application, it asks them to first select the language. The selected language is highlighted in orange color. Once the user selects a language, he/she must click on the ‘Continue’ button which opens the login page.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.51.35 PM.png" alt=""><figcaption></figcaption></figure>

### Login

The user will be provided a unique system-generated ID and password manually for first-time login. After logging in, the user is taken to the password reset page where they need to enter a new password of their choice. The password reset is not in scope for V1.0. If a user enters an incorrect username, it should show an error message below the field saying “username does not match”. For an incorrect password, it should show the message “incorrect password” below the password field.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.53.16 PM.png" alt=""><figcaption></figcaption></figure>

If an existing user does not remember his/her password, they must click on “Forgot Password”. This will open a popup asking the user to contact the administrator. The ‘OK’ button will collapse the popup.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.53.24 PM.png" alt=""><figcaption></figcaption></figure>

### Reset Password (Not in V1.0)

After the user logs in for the first time, a screen appears where he/she needs to create a new password. There are two fields, “Enter new password” and “Confirm password”, with the eye button present in both.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.55.04 PM.png" alt=""><figcaption></figcaption></figure>

After entering and reviewing the new password, the user clicks on the submit button which opens a screen with the message “New password created successfully” along with a “Back to Login” button below the text. Clicking on this button will take the user back to the login page. The password reset flow is not in scope for V1.0.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.55.12 PM.png" alt=""><figcaption></figcaption></figure>

### Project Selection

If the user is assigned to multiple projects, they need to select a particular project on this page by clicking on the arrow in front of each project name. Once the user has selected a project, it will open the application’s home page. After selecting a project, the system must download the data for the selected project only. For single-project users, the sync action takes place directly after the login action. There can be multiple cases for projects assigned to a user:

* If the user is assigned 0 projects, an overlay must appear saying “Please contact the system administrator for a project”  after logging in, and the user must log out of the application.
* If the user is assigned multiple projects as mentioned above.
* If the user has been assigned a project but later the project has been unassigned. In this case, if the user logs in and selects that project, an error message must appear stating “the project is not assigned to you, please select another project”. When the user clicks on the ‘OK’ button, he/she must be navigated to the updated project selection screen which must not display the unassigned project.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 1.56.50 PM.png" alt=""><figcaption></figcaption></figure>

### Sync

After every login action, the system will automatically sync the data with the system. Since the user will log in only at the start of the day and before going into the field, there must be stable internet connectivity for the device to perform this process. A “Sync in Progress” window will appear on the screen and the user cannot perform any other action until the process is complete.&#x20;

The overlay will appear over the previous screen. For users assigned to multiple projects, the overlay appears over the project selection screen when the user selects one project from the list.  For single-project users, the overlay must appear over the login page.

### Sync Status

Once the data is synced, it will show a popup that the data is successfully synced, with a ‘Close’ button at the bottom. When the user clicks on this button, it will navigate him/her to the homepage. These overlays also appear over the previous screens.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 2.01.10 PM.png" alt=""><figcaption></figcaption></figure>

If the data is not synced due to an error, it will show a popup stating “Sync Failed” with two buttons below it:

1. Retry: If the user wants to retry syncing the data. This will open the sync in progress window.
2. Close: Clicking on this will navigate the user back to the login page and he/she is required to log in again.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-03-20 at 2.01.17 PM.png" alt=""><figcaption></figcaption></figure>

\
[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
