# HCM Dashboard - Master Promotion Guide

## Overview

This quick guide helps you set up or promote the HCM Dashboard to higher environments. Use it if you’re on the implementation or external team.

## Release Features

List of core DIGIT services used:

* The HCM Dashboard uses the same core services as the HCM Platform.
* Refer to this [document](https://docs.digit.org/platform/platform/core-services) for the list of core services. Make sure they’re deployed.

## Service Enhancements&#x20;

The following image of the Dashboard analytics service is required for the HCM dashboard:

<table><thead><tr><th width="159.41145833333331">Service</th><th width="216.1484375">Image</th><th>Description</th></tr></thead><tbody><tr><td>Dashboard analytics service</td><td>dashboard-analytics:dashboard-v1.1.0-2ad7482dbd-32</td><td>The core dashboard analytics service with specific enhancements have been added for the HCM Dashboard.</td></tr></tbody></table>

## Release Tags

Deploy the below artefacts in your target environment:

<table><thead><tr><th width="304.7747395833333">Artefact</th><th width="451.27734375">Tag</th></tr></thead><tbody><tr><td>Dashboard chart configurations</td><td><a href="https://github.com/egovernments/health-campaign-config/releases/tag/dashboard-v1.1.0">dashboard-v1.1.0</a></td></tr><tr><td>Dashboard analytics service</td><td><a href="https://github.com/egovernments/health-campaign-services/releases/tag/dashboard-v1.1.0">dashboard-v1.1.0</a></td></tr><tr><td>MDMS</td><td><a href="https://github.com/egovernments/health-campaign-mdms/releases/tag/dashboard-v1.1.0">dashboard-v1.1.0</a></td></tr><tr><td>DIGIT UI</td><td><a href="https://github.com/egovernments/DIGIT-Dev/releases/tag/HCM-v1.5">HCM-v1.5</a></td></tr></tbody></table>

### Backend Configuration&#x20;

Refer to this [document](../deploy/configuration/ui-configuration/dashboard-configuration/dashboard-ui-enhancements.md#backend-enhancements) to promote the backend services and configurations.

### UI Configuration

<table><thead><tr><th width="140.93489583333331">Artefact</th><th>Image</th><th>Description</th></tr></thead><tbody><tr><td>DIGIT UI</td><td>digit-ui:health_v1.1.0-91a6f61fc1-375</td><td>DIGIT micro UI with enhancements specific for the health Dashboard.</td></tr></tbody></table>

* The HCM Dashboard includes UI enhancements that are part of the image mentioned above. The stylesheet and the global config used by the UI are as follows:
* Stylesheet: [https://unpkg.com/@egovernments/digit-ui-css@0.1.0/dist/index.css](https://unpkg.com/@egovernments/digit-ui-css@0.1.0/dist/index.css)
* Global config: [https://egov-health-demo-assets.s3.ap-south-1.amazonaws.com/globalConfigs.js](https://egov-health-demo-assets.s3.ap-south-1.amazonaws.com/globalConfigs.js)&#x20;
* Deploying the above image to the target environment will include the HCM dashboard for eligible users.
