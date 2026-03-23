---
description: >-
  This module will enable the health facility supervisors to track referrals
  made by on-field health workers to different health facilities digitally via
  the Digit HCM app.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/field-app-architecture/ui-packages/referral-reconciliation-package
---

# Referral Reconciliation Package

To learn more about Referral Reconciliation, [click here.](https://health.digit.org/hcm-product-suite/health-products/frontline-workers-app/user-manual/common-functions/health-facility-referral)\
\
Link to the Pub Package:&#x20;

{% embed url="https://pub.dev/packages/referral_reconciliation" %}

\
The referral reconciliation feature enables the user to track referrals made by on-field health workers to different health facilities digitally via the Digit HCM app capturing all the cases of:

* Beneficiary being referred
* Referral details of the beneficiary
* Reason for referrals and their diagnosis
* Based on the diagnosis, further details, if applicable

### Role

* HEALTH\_FACILITY\_WORKER

### Getting Started

To use this package, add the following dependency to your pubspec.yaml file:

```
dependencies:
  referral_reconciliation: ^latest
  digit_scanner: ^latest
```

## Integrating with the HCM Application&#x20;

1. To integrate this package with the HCM Application, run the main function located in health-campaign-field-worker-app/tools/referral\_reconciliation\_imports.dart.&#x20;
   * This will automatically add the necessary imports, mapper initializers, route config, setting initial data, and repository initialization to the required files.
2. Make sure you are on the path `apps/health_campaign_field_worker_app` and run the command:

```dart
dart run build_runner build --delete-conflicting-outputs
```

This adds a package route to the `main router.gr.dart`&#x20;

3. Install the application and you should have referral reconciliation integrated into your base app.

By following these steps, you can successfully integrate and use the Referral Reconciliation module within your application.

### Sequence Diagram

<figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcs0eKCk9gSGT9FcHFV_qvVu_WQVZuYOlPGmJosdpo4_LZItWNBQvaYyFyYcZx-0TIb3g4BWH-SgtbfLpAbcUvfl2cNf3v5eL_85WA0RKKszxrPA993a21fG1zFnfVQ4BVY7U4FCh6EmpOy2WaQBaiTLsQ?key=drBoBQLkGlWqMmHkJwkgsw" alt=""><figcaption></figcaption></figure>
