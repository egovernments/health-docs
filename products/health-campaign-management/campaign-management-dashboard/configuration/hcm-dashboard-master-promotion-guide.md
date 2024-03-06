# HCM Dashboard Master Promotion Guide

## Overview

This document is a step-by-step promotion guide to setup/promote the Health Campaign Management (HCM) Dashboard to higher environments. The guide can be used by implementation teams and other external teams to set up the product.

## Release Notes

<table><thead><tr><th width="183.33333333333331">Version</th><th>Date</th><th>Description</th></tr></thead><tbody><tr><td>1.0</td><td>10/05/2023</td><td>This version covers the HCM Dashboard promotion guide.</td></tr></tbody></table>

## Release Features

List of core digit services used:

* The HCM Dashboard consumes the same core services that are used by HCM Platform services.
* Refer to this [document](https://health.digit.org/products/health-campaign-management/frontline-workers-app/configuration/hcm-master-promotion-guide#release-features-list-of-core-digit-services-used) for the list of core services to be deployed for the HCM dashboard.

## Service enhancements for HCM Dashboard

The following image of the Dashboard analytics service is required for the HCM dashboard:

| Service                     | Tag                                                | Description                                                                                            |
| --------------------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Dashboard analytics service | dashboard-analytics:dashboard-v1.1.0-2ad7482dbd-32 | The core dashboard analytics service with specific enhancements have been added for the HCM Dashboard. |

## Promotion guide

This section will detail the promotion guide steps for the HCM Dashboard.

Tags created for the release artefacts:

| Artefact                       | Tag              | URL                                                                                                                                                                                                |
| ------------------------------ | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dashboard chart configurations | dashboard-v1.1.0 | <p><a href="https://github.com/egovernments/health-campaign-config/releases/tag/dashboard-v1.1.0">https://github.com/egovernments/health-campaign-config/releases/tag/dashboard-v1.1.0<br></a></p> |
| Dashboard analytics service    | dashboard-v1.1.0 | [https://github.com/egovernments/health-campaign-services/releases/tag/dashboard-v1.1.0](https://github.com/egovernments/health-campaign-services/releases/tag/dashboard-v1.1.0)                   |
| MDMS                           | dashboard-v1.1.0 | [https://github.com/egovernments/health-campaign-mdms/releases/tag/dashboard-v1.1.0](https://github.com/egovernments/health-campaign-mdms/releases/tag/dashboard-v1.1.0)                           |
| DIGIT UI                       | health\_v1.1.0   | [https://github.com/egovernments/DIGIT-Dev/releases/tag/health\_v1.1.0](https://github.com/egovernments/DIGIT-Dev/releases/tag/health\_v1.1.0)                                                     |

### Backend and configuration promotion guide

Refer to this [document](https://health.digit.org/products/health-campaign-management/frontline-workers-app/configuration/hcm-master-promotion-guide#release-features-list-of-core-digit-services-used) to promote the backend services and configurations.

### UI promotion guide

<table><thead><tr><th width="184.33333333333331">Artefact</th><th>Image</th><th>Description</th></tr></thead><tbody><tr><td>DIGIT UI</td><td>digit-ui:health_v1.1.0-91a6f61fc1-375</td><td>DIGIT micro UI with enhancements specific for the health Dashboard.</td></tr></tbody></table>

* The HCM Dashboard includes UI enhancements that are part of the image mentioned above. The stylesheet and the global config used by the UI are as follows:
* Stylesheet: [https://unpkg.com/@egovernments/digit-ui-css@0.1.0/dist/index.css](https://unpkg.com/@egovernments/digit-ui-css@0.1.0/dist/index.css)
* Global config: [https://egov-health-demo-assets.s3.ap-south-1.amazonaws.com/globalConfigs.js](https://egov-health-demo-assets.s3.ap-south-1.amazonaws.com/globalConfigs.js)&#x20;
* Deploying the above image to the target environment will include the HCM dashboard for eligible users.
