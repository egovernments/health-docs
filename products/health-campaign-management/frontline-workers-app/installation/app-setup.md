# App Setup

## Overview

The guide provides step-by-step instructions on how to clone and run the Field Worker's App locally on your machine. This Flutter application is specifically designed for health campaigns.

## Pre-requisites

Before you begin, ensure that you have the following installed on your PC:

* Flutter 3.10.0 version - [Flutter SDK. ](https://docs.flutter.dev/release/archive?tab=macos)
* Android Studio or VS Code, any preferred IDE for Flutter development.
* Android device or emulator for testing.
* Run the flutter doctor command to ensure all the required checklists are tick-marked.&#x20;

## Run the Application

1. Open the terminal and run the following commands:

&#x20;       git clone https://github.com/egovernments/health-campaign-field-worker-app.git

cd health-campaign-field-worker-app

&#x20;       Product repo: [egovernments/health-campaign-field-worker-app](https://github.com/egovernments/health-campaign-field-worker-app)

2. Open the project in your preferred IDE (Android Studio, Visual Studio Code). Make sure that your IDE is configured with the Flutter and Dart plugins.
3. Run install\_bricks.sh bash script which is located in the tools folder.&#x20;
4.  Navigate to the root folder of the project in the terminal and run the following command to initialize the packages using Melos:

    melos bootstrap&#x20;

    (-or-)

    melos bs

&#x20;       This command fetches and links all the necessary dependencies for the project.

5. Create a .env file inside the apps/health\_campaign\_field\_worker\_app folder.

&#x20;       Sample .env file:

```
BASE_URL={replace with base url}
MDMS_API_PATH="egov-mdms-service/v1/_search"
TENANT_ID="default"
SYNC_DOWN_RETRY_COUNT="3"
RETRY_TIME_INTERVAL="5"
CONNECT_TIMEOUT="120000"
RECEIVE_TIMEOUT="120000"
SEND_TIMEOUT="120000"
```

6. Create another file as pubspec\_overrides.yaml in the same folder.

```
# melos_managed_dependency_overrides: digit_components,digit_firebase_services,forms_engine,intl, digit_showcase
dependency_overrides:
 digit_components:
   path: ..\\..\\packages\\digit_components
 attendance_management:
   path: ../../packages/attendance_management
 dart_mappable_builder:
   path: ..\\..\\packages\\dart_mappable_builder
 digit_firebase_services:
   path: ..\\..\\packages\\digit_firebase_services
 digit_showcase:
   path: ..\\..\\packages\\digit_showcase
 forms_engine:
   path: ..\\..\\packages\\forms_engine
 intl: ^0.18.0
```

Note: All the folder names should be present in the packages folder, before overriding the dependencies.

7. Navigate to the app's folder from the terminal:&#x20;

&#x20;       cd apps/health\_campaign\_field\_worker\_app

&#x20; 8\.  Connect your Android device or start an emulator. Ensure that it is visible by running:

&#x20;     flutter devices

&#x20; 9\.  Now, run the following command to launch the app:

&#x20;      flutter run

&#x20;     This command will build the app and install it on the connected device or emulator.&#x20;

## Steps to Generate APK

* Create a .env file inside the apps/health\_campaign\_field\_worker\_app  folder&#x20;

&#x20;      Sample .env file:

```
BASE_URL="https://unified-qa.digit.org/"
MDMS_API_PATH="egov-mdms-service/v1/_search"
TENANT_ID="mz"
SYNC_DOWN_RETRY_COUNT="3"
RETRY_TIME_INTERVAL="5"
CONNECT_TIMEOUT="120000"
RECEIVE_TIMEOUT="120000"
SEND_TIMEOUT="120000"
ENV_NAME="QAT"
```

*   Navigate to the root folder of the project in the terminal and run the following command:

    melos clean

    melos bs
* After successfully running melos bs, navigate to: apps/health\_campaign\_field\_worker\_app folder in the terminal, and run the following command to generate the APK:&#x20;

&#x20;      flutter build apk --release

### How to Change the Master Data:

All the master data persist in MDMS under tenant folders.

Sample:&#x20;

[https://github.com/egovernments/health-campaign-mdms/tree/DEV/data/default](https://github.com/egovernments/health-campaign-mdms/tree/DEV/data/default)&#x20;

App Master data persist in:&#x20;

[https://github.com/egovernments/health-campaign-mdms/tree/DEV/data/default/health](https://github.com/egovernments/health-campaign-mdms/tree/DEV/data/default/health)

Consists of service register: All the APIs which the app utilises to call the server:\
[https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/service-registry.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/service-registry.json)

App configuration:  Primary Details required to run the app:&#x20;

[https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/field-app-configuration.json\
\
](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/field-app-configuration.json)Project types: Details of the projects are listed below:\
[https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/project-types.json\
\
](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/project-types.json)Additional static configs:\
1[https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/symptoms\_types.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/symptoms\_types.json)

## Upserting Localisation

* Replace the {URL} with the required environment.
* Get the {authToken} of SUPER\_USER
* Replace the {tenantId} with the required tenant.
* Each message object should have a unique code and module.

Sample message to upsert:&#x20;

```
{
            "code": "ADMINISTRATION_UNIT_FORM_LABEL",
            "message": "Administrative Unit",
            "module": "hcm-beneficiary",
            "locale": "en_MZ"
      }
```

API curl:

```
curl --location '{URL}/localization/messages/v1/_upsert' \
--header 'Content-Type: application/json' \
--data '{
    "RequestInfo": {
        "apiId": "emp",
        "ver": "1.0",
        "ts": "10-03-2017 00:00:00",
        "action": "create",
        "did": "1",
        "key": "abcdkey",
        "msgId": "20170310130900",
        "requesterId": "rajesh",
        "authToken": "{authToken}",
        "userInfo": {
            "id": 128
        }
    },
    "tenantId": "{tenantId}",
    "locale": "{locale}", // Eg. en_MZ
    "module": "hcm-common",
    "messages": [
        {
            "code": "ADMINISTRATION_UNIT_FORM_LABEL",
            "message": "Administrative Unit",
            "module": "hcm-beneficiary",
            "locale": "en_MZ"
        }
    ]
}'
```

Link for localisation:&#x20;

[https://docs.google.com/spreadsheets/d/12Fqe2\_g5as8VidxoVsB-DJsAyGY51Ft89-AIR3inBSk/edit#gid=1621214620\
\
](https://docs.google.com/spreadsheets/d/12Fqe2\_g5as8VidxoVsB-DJsAyGY51Ft89-AIR3inBSk/edit#gid=1621214620)Consolidated: [https://github.com/egovernments/releasekit/blob/master/localisation/HCM/consolidated/en\_MZ/consolidated.json\
\
](https://github.com/egovernments/releasekit/blob/master/localisation/HCM/consolidated/en\_MZ/consolidated.json)Module’s localisation:\
[https://github.com/egovernments/releasekit/tree/master/localisation/HCM/V1.2](https://github.com/egovernments/releasekit/tree/master/localisation/HCM/V1.2)
