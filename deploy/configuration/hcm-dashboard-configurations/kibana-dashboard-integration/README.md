---
description: Kibana dashboard integration steps with DSS module
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/dashboard-configurations/kibana-dashboard-integration
---

# Kibana Dashboard Integration

## Overview

This page outlines the process for creating a custom Kibana dashboard and integrating it into the DIGIT DSS module.\
The integration enables embedding Kibana visualisations directly into DIGIT’s DSS dashboard using the kibanaComponent chart type.

## Pre-requisites

* Access to a running Kibana instance connected to your Elasticsearch data source
* Permissions to:\
  \- Create dashboards in Kiobana\
  \- Edit MasterDashboardConfig.json in your Chart Configurations repository\
  \- Modify MDMS common-masters.uiCommonConstants schema
* Kibana dashboard link

## Steps

{% stepper %}
{% step %}
### Create the Kibana Dashboard

* Create Data View in Kibana:\
  Follow the Elastic documentation to create data views.\
  [Elastic Data View Creation Guide](https://www.elastic.co/docs/api/doc/serverless/operation/operation-createdataviewdefaultw)
* Build Your Visualization(s):\
  Use Kibana’s chart tools to create the required charts/visualisations.\
  [How to Create Charts in Kibana](https://www.elastic.co/kibana)
* Add Visualisations to Dashboard:
* Create a new Kibana dashboard.
* Add your charts to the dashboard.
* Save the dashboard.
* Copy the Dashboard Link:
* Open your dashboard.
{% endstep %}

{% step %}
### Update DSS Master Dashboard Config

* Open your Chart Configs repository.
* Locate MasterDashboardConfig.json.
* Add your custom chart configuration as follows:

```json
{
  "row": 1,
  "name": "DSS_CUSTOM_CHART",
  "vizArray": [
    {
      "id": 700,
      "name": "DSS_CUSTOM_CHART_LLIN",
      "label": "DSS_CUSTOM_CHART_LLIN",
      "vizType": "chart",
      "noUnit": true,
      "isCollapsible": false,
      "charts": [
        {
          "id": "customChart",
          "name": "DSS_HEALTH_CUSTOM_CHART",
          "code": "",
          "moduleName": "llin",
          "pageName": "custom-chart",
          "chartType": "kibanaComponent",
          "filter": "",
          "headers": []
        }
      ]
    }
  ]
}
```

Key Parameters:

* moduleName: Maps to the MDMS module entry (e.g., "llin").
* pageName: Unique identifier for the chart’s route (used in MDMS).
* chartType: Must be "kibanaComponent" for Kibana integration.
{% endstep %}

{% step %}
### Configure MDMS for Kibana Integration

* You’ll need to update the data for common-masters.uiCommonConstants in the MDMS service database or via the MDMS update API.
* Example JSON entry to add under common-masters.uiCommonConstants:

```json
"llin": {
  "iframe-routes": {
    "custom-chart": {
      "title": "DASHBOARD_CHECKLISTS_FILL",
      "isOrigin": true,
      "routePath": "/kibana/app/dashboards?auth_provider_hint=anonymous1#/view/1077cb40-8a14-11ef-82da-9bbcdc91995d?embed=true&_g=(refreshInterval:(pause:!t,value:60000),time:(from:now-15m,to:now))&_a=()&hide-filter-bar=true",
      "Authorization": true,
      "base-kibana-path": "/kibana/",
      "overwriteTimeFilter": true
    }
  }
}
```

{% hint style="info" %}
Notes:

* routePath should be the Kibana dashboard link starting from /view/....
* overwriteTimeFilter → Ensures DSS time filter syncs with Kibana.
{% endhint %}

Authentication flow:

* The auth\_provider\_hint=anonymous1 parameter and the "Authorisation": true setting enable the DIGIT Auth Proxy to intercept the request.
* When a logged-in DIGIT user accesses the DSS dashboard, their DIGIT authentication token is forwarded to the Auth Proxy.
* The Auth Proxy validates the token and determines whether the user has permission to view the Kibana dashboard.
* If valid, the Auth Proxy proxies the request to Kibana, ensuring only authorised DIGIT users can view embedded dashboards.
{% endstep %}

{% step %}
### Deploy and Validate

* Push changes to your Chart Config repository and make the MDMS changes.
* Redeploy MDMS and DSS services so that updated configs are loaded.
* Open the DSS dashboard.
* Verify that:

Your custom Kibana chart appears in the correct position.\
Copy the shareable link starting from /view/...
{% endstep %}
{% endstepper %}
