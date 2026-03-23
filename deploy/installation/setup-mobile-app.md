# Setup Mobile App

## Overview

This guide provides step-by-step instructions to clone and run the DIGIT Health Campaign Management (HCM) App locally on your machine. The app is a Flutter application developed for health campaigns.

## Pre-requisites

Before you begin, ensure that you have the following installed on your PC:

* Flutter 3.22.2 version&#x20;
  * Flutter setup for Linux and Android - [flutter documentation](https://docs.flutter.dev/get-started/install/linux/android)
  * Flutter setup for Windows and Android - [flutter documentation](https://docs.flutter.dev/get-started/install/windows/mobile)
* Android device

## Steps

{% stepper %}
{% step %}
### Clone the repository

Open a terminal and run the following commands:

1. git clone [https://github.com/egovernments/health-campaign-field-worker-app.git](https://github.com/egovernments/health-campaign-field-worker-app.git)
2. git checkout to the branch `1.8-installation-demo`
{% endstep %}

{% step %}
### Open the project in the preferred IDE

* Open the project in your preferred IDE (Android Studio, Visual Studio Code). Make sure that your IDE is configured with the Flutter and Dart plugins.
{% endstep %}

{% step %}
### Configure .env file

* Create a .env file inside the apps/health\_campaign\_field\_worker\_app  folder.
* Copy the below content to your newly created .env file.

```
BASE_URL={replace with base url}
MDMS_API_PATH='mdms-v2/v1/_search'
TENANT_ID="mz"`
ACTIONS_API_PATH="access/v1/actions/mdms/_get"
SYNC_DOWN_RETRY_COUNT="3"
RETRY_TIME_INTERVAL="5"
CONNECT_TIMEOUT="120000"
RECEIVE_TIMEOUT="120000"
SEND_TIMEOUT="120000"
CHECK_BANDWIDTH_API="/project/check/bandwidth"
ENV_NAME="DEMO"
```
{% endstep %}

{% step %}
### Generate APK

* After successfully setting up the env file, navigate to **apps/health\_campaign\_field\_worker\_app** folder in the terminal,
*   &#x20;Run the following command to generate the APK:&#x20;

    `flutter build apk --release --no-tree-shake-icons`
*   &#x20;After successfully running the above command, the APK will be generated in the path

    **apps/health\_campaign\_field\_worker\_app/build\app\outputs\flutter-apk\app-release.apk**
* Install the generated APK on your preferred Android device.
{% endstep %}
{% endstepper %}

