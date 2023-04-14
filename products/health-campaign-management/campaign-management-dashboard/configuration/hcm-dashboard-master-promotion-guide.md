# HCM Dashboard Master Promotion Guide

## Overview

This document is a step-by-step promotion guide to setup/promote the Health Campaign Management (HCM) Dashboard to higher environments. The guide can be used by implementation teams and other external teams to set up the product.

## Release Notes for 1.0

| Version | Date       | Description                                            |
| ------- | ---------- | ------------------------------------------------------ |
| 1.0     | 03/04/2023 | This version covers the HCM Dashboard promotion guide. |

## Release Features

List of core digit services used:

* The HCM Dashboard consumes the same core services that are used by HCM Platform services.
* Refer to this [document](https://health.digit.org/platform/configuration/hcm-master-promotion-guide#release-features-list-of-core-digit-services-used) for the list of core services to be deployed for the HCM dashboard.

## Service enhancements for HCM Dashboard

The following image of the Dashboard analytics service is required for the HCM dashboard:

| Service                     | Tag                                                | Description                                                                                            |
| --------------------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Dashboard analytics service | dashboard-analytics:dashboard-v1.0.0-e4b882b67f-22 | The core dashboard analytics service with specific enhancements have been added for the HCM Dashboard. |

## Promotion guide

This section will detail the promotion guide steps for the HCM Dashboard.

Tags created for the release artefacts:

| Artefact                       | Tag              | URL                                                                                                                                                                                                |
| ------------------------------ | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dashboard chart configurations | dashboard-v1.0.0 | <p><a href="https://github.com/egovernments/health-campaign-config/releases/tag/dashboard-v1.0.0">https://github.com/egovernments/health-campaign-config/releases/tag/dashboard-v1.0.0<br></a></p> |
| Dashboard analytics service    | dashboard-v1.0.0 | [https://github.com/egovernments/health-campaign-services/releases/tag/dashboard-v1.0.0](https://github.com/egovernments/health-campaign-services/releases/tag/dashboard-v1.0.0)                   |
| MDMS                           | dashboard-v1.0.0 | [https://github.com/egovernments/health-campaign-mdms/releases/tag/dashboard-v1.0.0](https://github.com/egovernments/health-campaign-mdms/releases/tag/dashboard-v1.0.0)                           |
| DIGIT UI                       | health\_v1.0.0   | [https://github.com/egovernments/DIGIT-Dev/releases/tag/health\_v1.0.0](https://github.com/egovernments/DIGIT-Dev/releases/tag/health\_v1.0.0)                                                     |

### Backend and configuration promotion guide

Refer to this [document](https://health.digit.org/platform/configuration/hcm-master-promotion-guide#promotion-guide) to promote the backend services and configurations.

### UI promotion guide

| Artefact | Image                                  | Description                                                         |
| -------- | -------------------------------------- | ------------------------------------------------------------------- |
| DIGIT UI | digit-ui:health\_v1.0.0-da4c8a14b4-216 | DIGIT micro UI with enhancements specific for the health Dashboard. |

* The HCM Dashboard includes UI enhancements that are part of the image mentioned above. The stylesheet and the global config used by the UI are as follows:
* Stylesheet: [https://unpkg.com/@egovernments/digit-ui-css@0.0.8/dist/index.css](https://unpkg.com/@egovernments/digit-ui-css@0.0.8/dist/index.css)
* Global config: [https://egov-health-demo-assets.s3.ap-south-1.amazonaws.com/globalConfigs.js](https://egov-health-demo-assets.s3.ap-south-1.amazonaws.com/globalConfigs.js)&#x20;
* Deploying the above image to the target environment will include the HCM dashboard for eligible users.
