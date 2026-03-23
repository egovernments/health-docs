---
description: Steps to configure HCM to campaign and country needs
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/campaign-and-country-specific-configuration
---

# Campaign & Country Specific Configuration

## Overview

This page covers the steps to configure HCM for a campaign. Every new campaign in a country or province will ideally require a few configurations to be done on the basic HCM application to cater to the exact needs of the campaign.

## Steps

{% stepper %}
{% step %}
### Install the application

Follow the steps given [here](https://health.digit.org/setup/installation/install-using-github-actions-in-aws) to install the app. Refer to [this](https://drive.google.com/drive/folders/1IiUipCq2pvQsd1A4s8r9ki5O_M9qAdPG?usp=sharing) video for easy installation.

Once the application is installed, you will have access to the admin console and workbench using which a campaign can be configured to the needs of the country and campaign.
{% endstep %}

{% step %}
### Load the new boundary hierarchy/boundary

* Each country will have its boundary hierarchy, which must be configured using the console/workbench feature. Refer to the [documentation](https://docs.digit.org/console/technology/architecture/services/hcm-console-web/boundary-data-management) for the steps. The login URL will be the \<domain configured during the installation>/workbench-ui/employee/user/language-selection
* After the hierarchy has been configured, the boundary master data will be uploaded.
{% endstep %}

{% step %}
### Setup a campaign and related master data using HCM Console

* &#x20;Refer to [this](https://egov-digit.gitbook.io/0.1/product-specification/setup-campaigns/user-manual) document for steps to use the console for campaign setup
* Set up users for various roles
* Set up all other masters for HCM
{% endstep %}

{% step %}
### Setup configuration parameters for the App

* Use the workbench link to configure the parameters per the [instructions](https://docs.digit.org/console/setup/configuration) given on this page.
{% endstep %}

{% step %}
### Change the labels and messages as per campaign needs

* &#x20;Login to the workbench URL, select the localisation option, and appropriately change the values for the keys. Refer to [this](https://workbench.digit.org/) document for instructions.
* These localisation changes will apply to both the web and the mobile application.
{% endstep %}

{% step %}
### Make the APK as per the new configuration

* Once the master data and language configuration, including loading of values, are done, you are ready to make an APK.
* Follow the steps mentioned [here](https://health.digit.org/setup/installation/setup-mobile-app) to make the APK, which can then be installed on your Android device.
{% endstep %}

{% step %}
### Install the APK on a device and make it ready for use

* Download and install the APK on the device.
* Enable the permissions to run background services.
* Enable the permission to access the camera.
* Enable location permissions.
*   Check for the other recommended prerequisites mentioned below

    &#x20;            i. ​RAM: Recommended is 6 GB, and minimum is 4 GB.

    &#x20;            ii. Processor: Octa-core processors.

    &#x20;            iii. Battery: Minimum 5000 mAh.
* The higher the mAh, the better it is. Battery consumption is heavily dependent upon phone searching, network searching, and GPS usage.

&#x20;           iv. Screen: Generally, the bigger the better for the field teams, but a minimum 6.5-inch screen size is recommended.

&#x20;            v. Storage: Minimum 32 GB. Typically, 4 GB or 6GB RAM phones are available with more than 32 GB of storage.
{% endstep %}

{% step %}
### Log in to the new application on the device

* &#x20;Click on the icon with the name HCM to open the application.
* Login using the user credentials created using the console.
{% endstep %}

{% step %}
### Log in to the web application

* Use the domain URL configured while installing to log in to the web application.
* Select the language of your choice.
* You can use the user credentials configured using the console.
* Once logged in you can see the menu options are per the roles assigned to this user.
{% endstep %}

{% step %}
### Configure the dashboard

* Kibana will be installed as part of the installation. Visualisations relevant to the campaign can be added to the dashboard by following the steps mentioned [here](https://health.digit.org/setup/installation/setup-kibana-dashboard).
* Follow the Kibana help documents for adding new charts and graphs.
* Log in to the web application using the dashboard role the user created as part of Step 1.     &#x20;
{% endstep %}
{% endstepper %}
