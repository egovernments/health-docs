---
description: Create and configure health dashboards in Kibana
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/installation/setup-kibana-dashboard
---

# Setup Kibana Dashboard

## Overview

This document outlines the steps required to create and configure health campaign dashboards in a different space within Kibana.

## Pre-requisites

* Knowledge of creating dashboards in Kibana. - [Dashboard and visualisations](https://www.elastic.co/guide/en/kibana/8.11/dashboard.html)
* Transformer and indexer services are up and running to enrich data for KPI creation and push data to Elastic Search.

## Steps

{% stepper %}
{% step %}
### &#x20;Access Kibana

* URL: \{{HOST NAME\}}/kibana
* Replace the \{{HOST NAME\}} with your domain URL.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 11.29.36 AM.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Verify installation & service setup

* Check the Kibana version through the UI in the Help section.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 11.31.58 AM.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Create or select a space

* By default, users will have access to the default space.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 11.33.45 AM.png" alt=""><figcaption></figcaption></figure>

* To create a new space or edit, open the main menu, then click Stack Management → Spaces for an overview of your spaces. This view provides actions to create, edit, and delete spaces.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 11.35.24 AM.png" alt=""><figcaption></figcaption></figure>

* Switch to or create a new space where the dashboards will be configured.
{% endstep %}

{% step %}
### Visualise data views & dashboards

{% hint style="info" %}
You can import and use the existing data views and dashboards from the product environment. To import existing data views, follow the steps given below.
{% endhint %}

* Navigate to the “Stack Management” in the sidebar.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 11.37.18 AM.png" alt=""><figcaption></figcaption></figure>

* Click on “Saved Objects” under Kibana.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 11.38.17 AM.png" alt=""><figcaption></figcaption></figure>

* Import the data views file here. Data views contain the queries and charts needed to fetch data from the indexes. The file to be imported:&#x20;

{% file src="../../../.gitbook/assets/export.ndjson" %}

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 11.39.14 AM.png" alt=""><figcaption></figcaption></figure>

* If you need to create your own data views, follow this guide:[ Creating Data Views in Kibana](https://www.elastic.co/guide/en/kibana/current/data-views.html).
* All dashboards and data views will be imported here and can be viewed under “Saved Objects”.

<figure><img src="../../../.gitbook/assets/image (204).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}
