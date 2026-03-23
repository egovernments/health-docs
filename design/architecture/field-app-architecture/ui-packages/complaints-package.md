---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/field-app-architecture/ui-packages/complaints-package
---

# Complaints Package

The Complaints package provides a streamlined way for users to register complaints related to health campaign. It allows users to file complaints by specifying the type of complaint, and detailed information about the concern.

Link to the pub package:&#x20;

{% embed url="https://pub.dev/packages/complaints" %}

## Role

* DISTRIBUTOR

## Features

* Register complaints
* Access past complaint records
* Choose from predefined categories to classify complaints

## Getting Started

To use this package, add the following dependency to your pubspec.yaml file:

```
dependencies:
    complaints: ^latest
```

## Integrating with the HCM Application

1. To integrate this package with the HCM Application, run the main function located in `health-campaign-field-worker-app/tools/complaints_package.dart`
   * &#x20;This will automatically add the necessary imports, mapper initializers, route config, setting initial data, and repository initialization to the required files.
2. Make sure you are on the path `apps/health_campaign_field_worker_app` and run the command:

```
dart run build_runner build --delete-conflicting-outputs
```

This adds a package route to the `main router.gr.dart`

3. Install the application and you should have complaints integrated into your base app.

By following these steps, you can successfully integrate and use the complaints module within your application.

## Sequence Diagram

<figure><img src="../../../../.gitbook/assets/image (370).png" alt=""><figcaption></figcaption></figure>
