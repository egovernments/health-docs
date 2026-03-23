---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/field-app-architecture/ui-packages/digit-dss-package
---

# DIGIT DSS Package

**Link to the Pub Package:**

{% embed url="https://pub.dev/packages/digit_dss" %}

digit\_dss is a Flutter package designed to facilitate the seamless integration of dynamic dashboards into your mobile application. This package allows developers to configure and render various types of charts directly from a dashboard configuration, enabling a flexible and customizable approach to data visualization.

## **Features**

* Dynamic charts configuration
* Support for Metric Charts
* Support for Table Charts

### Role

* **DISTRICT\_SUPERVISOR**

### Getting Started

To use this package, add the following dependency to your pubspec.yaml file:

| <p><code>dependencies:</code><br>  <code>digit_dss: ^latest</code></p> |
| ---------------------------------------------------------------------- |

## Integrating with the HCM Application&#x20;

1. To integrate this package with the HCM Application, run the main function located in health-campaign-field-worker-app/tools/digit\_dss\_imports.dart.&#x20;
2.
   1. This will automatically add the necessary imports, mapper initialisers, and repository initialisations to the required files.
3. Run the build runner command to add routes at your main app level:

| `flutter packages run build_runner build --delete-conflicting-outputs`  |
| ----------------------------------------------------------------------- |

\
This adds a package route to the main router.gr.dart&#x20;

Install the application and you should have `digit_dss` integrated into your base app.

By following these steps, you'll successfully integrate and navigate to the digit\_dss dashboard  module within your application.

Sequence Diagram <br>
---------------------

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe3niDeHo4koPngf0INIC54IjlXaogbvw4hbBF3wpXL10uQ7PT7NH6AyJJkoWSGvAYE0qCPrFJHV6BF6N36m6qBpuu_U9LyJTO1ZxTnBwfKGkLXNiEu5loXLfVAX9EU9dQIo8xPzE4hWPubAiERgnHSuaQT?key=2hQ0DQefMA7gu91mQr8Emw" alt=""><figcaption></figcaption></figure>
