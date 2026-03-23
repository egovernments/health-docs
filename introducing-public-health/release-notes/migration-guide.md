---
description: Steps to migrate from HCM v1.7 to v1.8
---

# Migration Guide

## HCM Upgrade Guide

{% stepper %}
{% step %}
### Update Health Campaign Configurations

* Open the health-campaign-config repository.
* Merge the following PR changes into the appropriate branch:\
  🔗[ HCM v1.8 Config Changes](https://github.com/egovernments/health-campaign-config/pull/446/files)
* After merging, apply the Project Factory V2 API Persister changes:\
  🔗[ Project-factory Persister Changes](https://github.com/egovernments/configs/pull/3698/files)
{% endstep %}

{% step %}
### Apply DevOps Changes

* Go to the health-campaign-devops repository.
* Check out the release-github-actions branch.
* Apply the following commits in order (very important):
  * [Commit 1](https://github.com/egovernments/health-campaign-devops/commit/435456c98b654720f4a52d1c6f00a912dc45c35c)
  * [Commit 2](https://github.com/egovernments/health-campaign-devops/commit/b89d802cd20bd71eb9f94b3772fea31d87d388e6)
  * [Commit 3](https://github.com/egovernments/health-campaign-devops/commit/0a2e032166da5bba3cdef4cf7c36c39a3d79dfef)
  * [Commit 4](https://github.com/egovernments/health-campaign-devops/commit/3928af6925a4563a3eb89eba13fe3443cc69de30)
* Add DevOps updates on top of the branch that holds the HCM v1.7 DevOps changes.
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
### Update Project Builds

Update the build versions in dependency-chart-v1.8.yaml:

<table><thead><tr><th width="219.6796875">Service</th><th>New version</th></tr></thead><tbody><tr><td>workbench-ui</td><td>v0.4.0-51d99a279e-514</td></tr><tr><td>project-factory</td><td>v0.4.0-ac42230ae7-576</td></tr></tbody></table>
{% endstep %}

{% step %}
### Final Verification

* Ensure all the above changes are committed and pushed to the correct branches.
* Deploy the updated version in the new environment.
* Test the environment for:
  * Functionality changes from v1.8 configs.
  * Project Factory V2 API functionality.
  * Seed data correctness.
  * UI rendering in the workbench.
* If all tests pass, proceed to promote changes to the required environments.
{% endstep %}
{% endstepper %}

## APK Upgrade Guide

Below are the steps to upgrade from v1.7.0 → v0.2.0.

{% stepper %}
{% step %}
### Upgrade app version

The app version has been bumped: version: 1.7.0   →   version: 0.2.0
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

* App version bumped: 1.7.0 → 0.2.0

To update locally:

```
flutter pub upgrade
flutter clean
flutter pub get
flutter pub outdated
```

| Package                  | Old version   | New version          |
| ------------------------ | ------------- | -------------------- |
| digit\_ui\_components    | ^0.0.2-dev.14 | ^0.2.2+4             |
| sync\_service            | ^1.0.0        | ^1.0.2               |
| attendance\_management   | ^1.0.4+1      | ^1.0.5+1             |
| digit\_scanner           | ^1.0.5        | ^1.0.6+1             |
| inventory\_management    | ^1.0.5        | ^1.0.6               |
| referral\_reconciliation | ^1.0.4        | ^1.0.6               |
| digit\_data\_model       | ^1.0.6        | ^1.2.0-dev.1-console |
| registration\_delivery   | ^1.0.6        | ^1.1.0-dev.5-console |
| digit\_dss               | ^1.0.4        | ^1.0.4+2             |
| closed\_household        | ^1.0.5        | ^1.1.0-dev.1-console |
| survey\_form             | ^1.0.1        | ^1.0.3               |
| complaints               | ^1.0.2        | ^1.0.3               |

{% hint style="info" %}
The following new packages were introduced in 0.2.0:
{% endhint %}

| Package                | Version    |
| ---------------------- | ---------- |
| digit\_crud\_bloc      | ^0.0.2-dev |
| digit\_data\_converter | ^0.0.2-dev |
| digit\_forms\_engine   | ^0.0.2-dev |
{% endstep %}
{% endstepper %}
