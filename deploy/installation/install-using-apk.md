---
description: How to Install DIGIT HCM Using APK (Android Installation Guide)
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/installation/install-using-apk
---

# Install Using APK

## Overview

After deploying the DIGIT HCM backend, you need to install the HCM mobile app (APK) on\
Android devices for field operations. Follow the steps below to download, install, and\
configure the HCM APK.

## Pre-requisites

Before installing the APK, ensure:\
✅ Android Device (with at least 4GB RAM, 32GB storage, and Android 8+).\
✅ Stable Internet Connection.\
✅ Flutter Installed (for APK generation).\
✅ APK File (Either pre-built or generated from the source).

## Steps

{% stepper %}
{% step %}
### **Download the APK**

There are two ways to get the APK:

**Option 1: Download Pre-built APK**\
If an APK is already generated, download it from:

* Google Drive / Internal Storage (if shared by the admin).
* Google Play Store (if officially hosted).
* Direct link from the DIGIT HCM server.

**Option 2: Build Your Own APK (For Developers)**\
If you need to generate the APK manually, follow the steps below:

* Clone the HCM Field Worker App Repository: \
  a. git clone https://github.com/egovernments/health-campaign-field-worker-app.git\
  cd health-campaign-field-worker-app\
  b. Create .env File for Configuration\
  Inside apps/health\_campaign\_field\_worker\_app, create .env file:\
  BASE\_URL={replace with base url}\
  MDMS\_API\_PATH='mdms-v2/v1/\_search'\
  TENANT\_ID="mz"\
  ACTIONS\_API\_PATH="access/v1/actions/mdms/\_get"
* Build an APK using Flutter\
  c. flutter build apk --release --no-tree-shake-icons\
  d. Locate the APK\
  The generated APK will be available at:\
  apps/health\_campaign\_field\_worker\_app/build/app/outputs/flutter-apk/app-release.apk
* Transfer the APK to an Android device using:\
  ○ USB Cable.\
  ○ Google Drive/Email.\
  ○ Airdrop/ShareIt.
{% endstep %}

{% step %}
### Install the APK on Android

Install the APK following the steps below:

**Step 1: Allow Installation from Unknown Sources**

Since the APK is not from the Play Store, you must enable third-party installations:

* Open Settings on your Android device.
* Navigate to Security or Privacy.
* Tap Install Unknown Apps (or Unknown Sources).
* Select the File Manager / Browser you’ll use to open the APK.
* Enable Allow from this source.

**Step 2: Install the APK**

* Locate the APK file (from downloads or file manager).
* Tap on the APK file to start installation.
* Click Install.
* Wait for the process to complete.
* Tap Open to launch the app.
{% endstep %}

{% step %}
### First-Time Setup

After installation, configure the HCM mobile app:\
**Step 1: Accept Permissions**

* Allow Camera Access (for barcode scanning).
* Enable Location (if needed for geo-tracking).
* Allow Storage Access (to save files/logs).

**Step 2: Login to the App**

* Enter Username & Password (provided by the Admin).
* Click Login.
* The app will sync project data.
* Wait until the sync is complete before proceeding.

**Step 3: Set Up Campaign Data**

* If required, the system loads boundaries and campaign details.
* Verify that the correct region/campaign is selected.

**Step 4: Test a Sample Entry**

* Navigate to Beneficiary Registration.
* Register a sample household/individual.
* Save and Sync Data.
{% endstep %}
{% endstepper %}

## Update APK

If a new version of the APK is released:

1. Uninstall the old version: adb uninstall com.egov.healthcampaign
2. Download & Install the latest version following the steps above.

## Uninstall APK

To remove and uninstall HCM:

1. Go to Settings > Apps.
2. Find Health Campaign Management (HCM).
3. Tap Uninstall.
4. Confirm OK.

## Troubleshooting Issues During Installation

If the APK does not install:&#x20;

✅ Ensure enough storage space (At least 1GB free).\
✅ Enable "Install Unknown Apps" in Settings.\
✅ Check APK file integrity (Re-download if corrupted).\
✅ Restart the device and try again.\
✅ Enable Developer Mode (if necessary) under Settings > Developer Options.
