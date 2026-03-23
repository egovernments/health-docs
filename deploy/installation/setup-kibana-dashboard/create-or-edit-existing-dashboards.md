---
description: How to create or edit HCM product dashboards in Kibana
---

# Create or Edit Existing Dashboards

## Steps

{% stepper %}
{% step %}
### &#x20;Create dashboards&#x20;

* To understand how to create dashboards in Kibana, refer to this guide:[ Create a Dashboard of Panels](https://www.elastic.co/guide/en/kibana/current/create-a-dashboard-of-panels-with-web-server-data.html).
{% endstep %}

{% step %}
### Edit existing dashboards

* Open the desired dashboard.

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

* Click on the 'Edit' button.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 1.24.07 PM.png" alt=""><figcaption></figcaption></figure>

* Click on the “Edit Visualisation” option on the specific chart you want to edit.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 1.43.10 PM.png" alt=""><figcaption></figcaption></figure>

* Check the chart type and data view from which the data is being fetched.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 1.44.01 PM.png" alt=""><figcaption></figcaption></figure>

* Click on “Edit Lens” to get an overview of the available and selected fields in the respective data view.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 1.45.56 PM.png" alt=""><figcaption></figcaption></figure>

* You can go to the respective data view under Stack Management -> Saved Objects, update the indexes, and add a timestamp filter for the respective chart.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 1.47.05 PM.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### View or edit queries to fetch metric data

* After going back to the “Edit Visualisation”, you can see the metrics that are shown in the chart here, as shown in the image below:

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 1.48.03 PM.png" alt=""><figcaption></figcaption></figure>

* Click on the desired metric for which you want to view/edit the query.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-29 at 1.48.42 PM.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### View data sources

* To see which index a data view is pulling the data from, check the respective data views in Stack Management -> Data Views.
* If you need to create your own data views, follow this guide:[ Creating Data Views in Kibana](https://www.elastic.co/guide/en/kibana/current/data-views.html).
* For example, if you click on “Edit Visualisation” on a chart, you will see that the table chart is getting data from the DV-PT-PJT data view.&#x20;
* You can then view the DV-PT-PJT data, check the indices from where the data is getting pulled, and add a timestamp filter according to your requirements.
{% endstep %}
{% endstepper %}
