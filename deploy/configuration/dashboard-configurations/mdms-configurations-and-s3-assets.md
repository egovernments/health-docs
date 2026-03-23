# MDMS Configurations & S3 Assets

The Geo JSON assets files need to be loaded to the S3 bucket, and the reference URLs need to be mapped in the map-config.GeoJsonMapping MDMS schema data.

| Master            | Module           | Reference Link                                                                                                                                                                                     |
| ----------------- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| map-config        | GeoJsonMapping   | [https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.7/geo-json-mapping.json](https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.7/geo-json-mapping.json)           |
| dss-dashboard     | dashboard-config | [https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.7/dashboard-config.json](https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.7/dashboard-config.json)           |
| HCM-PROJECT-TYPES | projectTypes     | [https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.7/project-types.json](https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.7/project-types.json)                 |
| HCM               | dashboardConfig  | [https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.7/hcm\_dashboard\_config.json](https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.7/hcm_dashboard_config.json) |

To configure dashboard links, add the dashboard URLs to the project type in MDMS
