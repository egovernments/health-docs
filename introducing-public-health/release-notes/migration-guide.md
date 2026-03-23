---
description: Steps to migrate from HCM v1.8 to v2.0
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/introducing-public-health/release-notes/migration-guide
---

# Migration Guide

## HCM Upgrade Guide

{% stepper %}
{% step %}
### Latest Health Campaign Configurations

* Open the health-campaign-config repository.
* Check out the DEMO branch.
* latest HCM-v2.0 release configs changes\
  🔗 [HCM v2.0 Config Changes](https://github.com/egovernments/health-campaign-config/tree/DEMO)
{% endstep %}

{% step %}
### Latest DevOps Changes

* Go to the health-campaign-devops repository.
* Check out the release-github-actions branch.
* latest HCM-v2.0 release devops changes

&#x20;      🔗[HCM-v2.0 release devops changes](https://github.com/egovernments/health-campaign-devops/tree/release-githubactions)
{% endstep %}

{% step %}
### Update Seed Data & Localisation

* **Seed Data Update**
  * Use the updated seed data dump provided here:\
    🔗[ Seed Data File](../../deploy/installation/setup-project-data.md#seed-data-in-the-postman-script)
  * Import this dump into the environment. This will **replace/upgrade the existing seed data** with the updated version needed for HCM v1.8.
  * No manual picking of changes from the document is required.
* **Localization Update**
  * The reference document lists the updated translations/localization changes:\
    🔗 [Reference Document](../../deploy/installation/setup-project-data.md#load-localisation)
  * Use the finalized localization files (JSON/CSV) that are shared along with the migration package. These files should be applied directly to update the localization.
{% endstep %}

{% step %}
### Latest Project Builds

all the latest build for HCM-v2.0 release&#x20;

🔗 [HCM-v2.0 latest builds](https://github.com/egovernments/health-campaign-devops/blob/release-githubactions/config-as-code/product-release-charts/Health/dependancy_chart-health-demo-v2.0.yaml)
{% endstep %}
{% endstepper %}

## APK Upgrade Guide

Below are the steps to upgrade from v1.7.0 → v0.2.0.

{% stepper %}
{% step %}
### Upgrade app version

The app version has been bumped: version: 0.2.0   →   version: 2.0.0
{% endstep %}

{% step %}
### How to Apply These Updates

#### Step 1 — Update dependencies

Run:

```
flutter pub upgrade
```

{% hint style="info" %}
👉 This updates all packages to the latest versions that match your [pubspec.yam](https://github.com/egovernments/health-campaign-field-worker-app/blob/console-master/apps/health_campaign_field_worker_app/pubspec.yaml)l.
{% endhint %}

Step 2 — Clean project (to avoid old cached versions)

```
flutter clean

flutter pub get
```

#### Step 3 — Verify updates

Run:

```
flutter pub outdated
```

{% hint style="info" %}
👉 This shows you if any dependencies are still behind the latest release.
{% endhint %}
{% endstep %}

{% step %}
### &#x20; Summary

* App version bumped: 0.2.0 → 2.0.0

To update locally:

```
flutter pub upgrade
flutter clean
flutter pub get
flutter pub outdated
```

<table><thead><tr><th>Package</th><th width="208.3203125">Old version</th><th>New version</th></tr></thead><tbody><tr><td>digit_ui_components</td><td>^0.2.2+4</td><td>^0.3.0</td></tr><tr><td>sync_service</td><td>^1.0.2</td><td>^1.0.3</td></tr><tr><td>attendance_management</td><td>^1.0.5+1</td><td>^1.0.6</td></tr><tr><td>digit_scanner</td><td>^1.0.6+4</td><td>^1.0.7</td></tr><tr><td>digit_data_model</td><td>^1.2.0-dev.2-console</td><td>^1.3.0</td></tr><tr><td>digit_dss</td><td>^1.0.4+2</td><td>^1.0.5</td></tr><tr><td>survey_form</td><td>^1.0.3</td><td>^1.0.4</td></tr></tbody></table>

{% hint style="info" %}
The following new packages were introduced in 2.0.0:
{% endhint %}

| Package              | Version |
| -------------------- | ------- |
| digit\_flow\_builder | ^1.0.0  |
{% endstep %}
{% endstepper %}
