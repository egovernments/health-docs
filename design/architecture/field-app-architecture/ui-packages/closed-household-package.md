---
description: >-
  It’s been built as a new module (pub package)- closed_household and It will be
  a dependency of registration and delivery package.
---

# Closed HouseHold package

To learn more about Registration and Delivery, [click here.](https://pub.dev/packages/closed_household)\
\
Link to the pub package:

{% embed url="https://pub.dev/packages/closed_household" %}

## Role

* DISTRIBUTOR

## **Features**

* Create a closed household
* Update task if closed household gets registered

## Getting Started

To use this package, add the following dependency to your pubspec.yaml file:

```
dependencies:
  closed_household: ^latest
```

## Integrating with the HCM Application:&#x20;

1. To integrate this package with the HCM Application, run the main function located in `health-campaign-field-worker-app/tools/closed_household_imports.dart.`&#x20;
   * This will automatically add the necessary imports, mapper initializers, route config, setting initial data, and repository initialization to the required files.
2. Make sure you are on the path `apps/health_campaign_field_worker_app` and run the command:

```dart
dart run build_runner build --delete-conflicting-outputs
```

This adds a package route to the `main router.gr.dart`&#x20;

3. Install the application and you should have Registration and Delivery integrated into your base app.

By following these steps, you can successfully integrate and use the closed household module within your application.



**Sequence  Diagram**\
\
<br>

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeAfzq8R3vsLSszhLHRgzKBPFWvaAXcmRZnHHvFuDol_Fa8yOHgsFIk9QuGnIhPQzlTov827uLcR71S1PpfHxmDoiJp3vZo6pVy6DC2oagFboHJb-dMeRY8P0eDPvlWPgQoD8KfhoBzWSkoNIE_S975nTuE?key=9Nh1qYotTAKkaU2_CLeYjA" alt=""><figcaption></figcaption></figure>

Package published : [https://pub.dev/packages/closed\_household](https://pub.dev/packages/closed_household)
