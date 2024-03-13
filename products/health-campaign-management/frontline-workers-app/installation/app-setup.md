# App Setup

## Demo Video

[DIGIT Health Campaign Management Demo | DIGIT HCM](https://youtu.be/NB54Ve\_smv0?si=4sjmLWk5YZgCJRdF)

## Setup Guide

Database (DB) Restore (Providing a DB backup to avoid hassle since the automation of the seed data creation is a work in progress):

To restore the database, you can access the DB dump file. Use the following link to download the SQL file. [https://drive.google.com/file/d/1u2eljinnCCJAxUGCHRHHfnDQ5-WMZWIo/view?usp=sharing](https://drive.google.com/file/d/1u2eljinnCCJAxUGCHRHHfnDQ5-WMZWIo/view?usp=sharing)

### Steps to Restore Database Data

* Run Kubectl, and copy cmd to copy the file to the server (playground pod where DB runs).
* Execute the restore command inside the playground pod.

{% hint style="info" %}
psql -h {host} -U {username} -d {dbname} -f /path/in/pod/seed\_data.sql
{% endhint %}

#### Note:&#x20;

* Once the DB is restored, redeploy the MDMS service, persister, and indexer services using the config flag since we have updated a few links in the DevOps repository.&#x20;
* The Postgres version should be 14.8 or later.

{% hint style="info" %}
kubectl apply -f /path/to/your/pod-config.yaml
{% endhint %}

## Frontline Worker's App Setup

This guide provides step-by-step instructions to clone and run the Health Campaign Frontline Worker's App locally on your machine. The app is a Flutter application developed for health campaigns.

### Pre-requisites

Before you begin, ensure that you have the following installed on your PC:

* Flutter 3.10.0 version - [Flutter SDK ](https://docs.flutter.dev/release/archive?tab=macos)
* Android Studio or VS Code, any preferred IDE for Flutter development.
* Android device or emulator for testing.
* Run the flutter doctor command to ensure all the required checklists are marked.&#x20;

### Steps to Run the Application

1. Open a terminal and run the following commands:

&#x20;git clone https://github.com/egovernments/health-campaign-field-worker-app.git

cd health-campaign-field-worker-app

Product Repo: [egovernments/health-campaign-field-worker-app](https://github.com/egovernments/health-campaign-field-worker-app)

2. Open the project in your preferred IDE (Android Studio, Visual Studio Code). Make sure that your IDE is configured with the Flutter and Dart plugins.
3. Now, create a .env file inside the apps/health\_campaign\_field\_worker\_app  folder.

&#x20;      Sample .env file:&#x20;

```
BASE_URL={replace with base url}
MDMS_API_PATH='egov-mdms-service/v1/_search'
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

4. Create another file as pubspec\_overrides.yaml in the same folder:

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

Note: Check that all the folder names are present in the packages folder before overriding the dependencies.

5. Create another file as pubspec\_overrides.yaml in **packages/attendance\_management/pubspec\_overrides.yaml**

```
# melos_managed_dependency_overrides: dart_mappable_builder
# melos_managed_dependency_overrides: digit_components
dependency_overrides:
  dart_mappable_builder:
    path: ../dart_mappable_builder
  digit_components:
    path: ../digit_components
```

6.  Create another file as pubspec\_overrides.yaml in **packages/forms\_engine/pubspec\_overrides.yaml**

    ```
    # melos_managed_dependency_overrides: digit_components
    dependency_overrides:
      digit_components:
        path: ..\\digit_components
    ```
7. Run install\_bricks.sh bash script which is located in the tools folder. This script fetches and links all the necessary dependencies for the project.
8.  After successfully running the script and setting up the env file, navigate to the app's folder from the terminal:

    cd apps/health\_campaign\_field\_worker\_app
9.  Connect your Android device or start an emulator. Ensure that it is visible by running

    flutter devices.
10. Now, run the following command to launch the app:

    flutter run

    \
    This command will build the app and install it on the connected device or emulator.

### Steps to Generate APK

* Create a .env file inside the apps/health\_campaign\_field\_worker\_app folder.&#x20;

&#x20;      Sample .env file:

```
BASE_URL={replace with base url}
MDMS_API_PATH='egov-mdms-service/v1/_search'
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

* Create another file as pubspec\_overrides.yaml in the same folder.

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

*   Create another file as pubspec\_overrides.yaml in **packages/attendance\_management/pubspec\_overrides.yaml**

    ```
    # melos_managed_dependency_overrides: dart_mappable_builder
    # melos_managed_dependency_overrides: digit_components
    dependency_overrides:
      dart_mappable_builder:
        path: ../dart_mappable_builder
      digit_components:
        path: ../digit_components
    ```
*   Create another file as pubspec\_overrides.yaml in **packages/forms\_engine/pubspec\_overrides.yaml**

    ```
    # melos_managed_dependency_overrides: digit_components
    dependency_overrides:
      digit_components:
        path: ..\\digit_components
    ```
* Run install\_bricks.sh bash script which is located in the tools folder. This script fetches and links all the necessary dependencies for the project.
*   After successfully running the script and setting up the env file, navigate to: apps/health\_campaign\_field\_worker\_app folder in the terminal, and run the following command to generate the APK:&#x20;

    `flutter build apk --release --no-tree-shake-icons`


*   &#x20;After successfully running the above command , the apk will be generated in the path

    **apps/health\_campaign\_field\_worker\_app/build\app\outputs\flutter-apk\app-release.apk**
* Install the generated APK in your preferred android device

How to change the master data:\
All the Master data persist in MDMS under the tenant folders.

Sample:\
[https://github.com/egovernments/health-campaign-mdms/tree/DEV/data/default](https://github.com/egovernments/health-campaign-mdms/tree/DEV/data/default).\
\
App master data persist in:&#x20;

[https://github.com/egovernments/health-campaign-mdms/tree/DEV/data/default/health](https://github.com/egovernments/health-campaign-mdms/tree/DEV/data/default/health)

\
Consist of service register: All the APIs that the app utilises to call the server:\
[https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/service-registry.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/service-registry.json)

\
App configuration: Primary details required to run the app:&#x20;

[https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/field-app-configuration.json\
\
](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/field-app-configuration.json)Project types: Details of the projects are listed here:\
[https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/project-types.json\
](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/project-types.json)

Additional static  configs: [https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/symptoms\_types.json](https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/health/symptoms\_types.json)

## Upserting Localisation

1. Import the following curl in Postman:

#### Note: &#x20;

* Replace the {URL} with the required environment.
* Get the {authToken} of SUPER\_USER.
* Replace the {tenantId} with the required tenant.
* Each message object should have a unique code and module.

Sample message to upsert:

```
{
            "code": "ADMINISTRATION_UNIT_FORM_LABEL",
            "message": "Administrative Unit",
            "module": "hcm-beneficiary",
            "locale": "en_MZ"
      }
```

#### API curl:

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

Link for Localisation:&#x20;

{% embed url="https://docs.google.com/spreadsheets/d/e/2PACX-1vSb3QDXs7kK_6Oqurakr_AJf-XyOXWBOW9w-2iiwlmgvh-iXzOvFGYKdzuH5inV2xQGmTxwAQ57pcZB/pubhtml" %}

Consolidated: [https://github.com/egovernments/releasekit/blob/master/localisation/HCM/consolidated/en\_MZ/consolidated.json\
\
](https://github.com/egovernments/releasekit/blob/master/localisation/HCM/consolidated/en\_MZ/consolidated.json)Module’s Localisation:[https://github.com/egovernments/releasekit/tree/master/localisation/HCM/V1.3](https://github.com/egovernments/releasekit/tree/master/localisation/HCM/V1.3)
