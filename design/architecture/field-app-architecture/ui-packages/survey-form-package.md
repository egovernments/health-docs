# Survey Form Package

The Survey Form package enables users to fill out questionnaires. It provides a user-friendly interface for submitting responses, and ensures that health campaign-related feedback and data are collected efficiently and accurately.

Link to the pub package:&#x20;

{% embed url="https://pub.dev/packages/survey_form" %}

## Role

* DISTRIBUTOR

## Features

* Provides selection box, check-box, and text field to support various data types.
* Accurately capture employee-specific boundaries for relevant survey responses.
* Allows employees to view their submitted responses.

## Getting Started

To use this package, add the following dependency to your pubspec.yaml file:

```
dependencies:
    survey_form: ^latest
```

## Integrating with the HCM Application

1. To integrate this package with the HCM Application, run the main function located in `health-campaign-field-worker-app/tools/survey_form_package_imports.dart`
   * This will automatically add the necessary imports, mapper initializers, route config, setting initial data, and repository initialization to the required files.
2. Make sure you are on the path `apps/health_campaign_field_worker_app` and run the command:

```
dart run build_runner build --delete-conflicting-outputs
```

This adds a package route to the `main router.gr.dart`

3. Install the application and you should have complaints integrated into your base app.

By following these steps, you can successfully integrate and use the Survey Form module within your application.

## Sequence Diagram

<figure><img src="../../../../.gitbook/assets/image (170).png" alt=""><figcaption></figcaption></figure>
