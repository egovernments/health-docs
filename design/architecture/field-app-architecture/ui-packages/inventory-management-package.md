---
description: >-
  This enables the user to manage the stocks of a health campaign. The user can
  record the stocks received, issued, returned, damaged and lost.
---

# Inventory Management Package

To known more about Inventory Management, [click here.](https://health.digit.org/hcm-product-suite/health-products/frontline-workers-app/user-manual/common-functions/inventory-management)

Link to the Pub Package:

{% embed url="https://pub.dev/packages/inventory_management" %}

## Role

* DISTRIBUTOR, WAREHOUSE\_MANAGER

## Features

* Manage Stocks: Receipt, issued, returned, damaged, and loss of stocks.
* Stock Reconciliation: Reconcile the stock data.
* View Reports: View the reports of the stocks.

## Getting Started

To use this package, add the following dependency to your pubspec.yaml file:

```
dependencies:
  inventory_management: ^latest
  digit_scanner: ^latest
```

## Integrating with the HCM Application:&#x20;

1. To integrate this package with the HCM Application, run the main function located in `health-campaign-field-worker-app/tools/inventory_management_imports.dart.`&#x20;
   * This will automatically add the necessary imports, mapper initializers, route config, setting initial data, and repository initialization to the required files.
2.  Make sure you are on the path `apps/health_campaign_field_worker_app` and run the command:

    ```dart
    dart run build_runner build --delete-conflicting-outputs
    ```

    This adds a package route to the `main router.gr.dart`&#x20;


3. Install the application and you should have Inventory Management integrated into your base app.

By following these steps, you can successfully integrate and use the Inventory Management module within your application.

## Sequence Diagram&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXf0lvNJIU-1hAxQpU5w5j-IOAphpJJcZ9ep4wECqF-jm4lF_4bZ4pP-cRa0kbXtmYgW-oLjf0iQmoY-xMBqMOZlhyvlwe7XKHF9pyJItv2TZvz2BRh0b4G5aQ22dMuYaHU-_xEHv6LfjpbLwHRK9L9MJ0TF?key=ywC-xFdrBsgjDW7J5HkN3w" alt=""><figcaption></figcaption></figure>

\
<br>
