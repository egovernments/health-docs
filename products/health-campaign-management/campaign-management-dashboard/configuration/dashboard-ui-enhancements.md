# Dashboard UI Enhancements

## Project Selection

### Overview

After a supervisor logs into the HCM web app, the project services will be invoked to set the locations that are tagged to the user.

#### Initialising Default Campaign Filters

* Based on the details of the user logged in to the dashboard, the project-staff-search is invoked to get the projects associated with the user.&#x20;
* A Project-Search is then invoked to get the complete project-details which includes campaign start and end dates, boundary information, etc.
* The MDMS API is invoked to get more details about the project based on “projectType”.
* The egov-Location service is invoked to get the boundary information based on boundaryCode that was obtained from the project details.
* A supervisor can navigate to their corresponding dashboards (national/ provincial/district) using the following URLs:

&#x20;     \- [https://health-demo.digit.org/digit-ui/employee/dss/dashboard/national-health-dashboard](https://health-demo.digit.org/digit-ui/employee/dss/dashboard/national-health-dashboard)

&#x20;     \- [https://health-demo.digit.org/digit-ui/employee/dss/dashboard/provincial-health-dashboard?province=Tete](https://health-demo.digit.org/digit-ui/employee/dss/dashboard/provincial-health-dashboard?province=Tete)

&#x20;     \- [https://health-demo.digit.org/digit-ui/employee/dss/dashboard/district-health-dashboard](https://health-demo.digit.org/digit-ui/employee/dss/dashboard/district-health-dashboard)

* On the dashboards, users can only view the information which was synced corresponding to the projects they are associated with. As more devices sync, the dashboards will be updated with the latest synced data.

API Requests\



| End point                                                                                                                                     | Request Method | Request Payload                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| /project/staff/v1/\_search                                                                                                                    | POST           | <p>{</p><p>   "ProjectStaff": {</p><p>       "staffId": "loggedInUserId"</p><p>   },</p><p>   "RequestInfo": {</p><p>       "authToken": "string",</p><p>  }</p><p>}</p>                                                                                                                                                                                                                                                 |
| /project/v1/\_search                                                                                                                          | POST           | <p>{</p><p>   "RequestInfo": {</p><p>       "authToken": "string"</p><p>   },</p><p> "Projects": [</p><p>     {      "id":"projectId",</p><p>       "tenantId": "string"</p><p>     }</p><p> ]</p><p>}</p><p><br></p>                                                                                                                                                                                                    |
| /egov-mdms-service/v1/\_search?tenantId=default                                                                                               | POST           | <p>{</p><p>  "MdmsCriteria": {</p><p>    "tenantId": "default",</p><p>    "moduleDetails": [</p><p>      {</p><p>        "moduleName": "HCM-PROJECT-TYPES",</p><p>        "masterDetails": [</p><p>          {</p><p>            "name": "projectTypes"</p><p>          }</p><p>        ]</p><p>      }</p><p>    ]</p><p>  },</p><p>  "RequestInfo": {</p><p>    "authToken": "string"</p><p>  }</p><p>}</p><p><br></p> |
| /egov-location/location/v11/boundarys/\_search?hierarchyTypeCode=ADMIN\&tenantId=default\&codes=\<boundarycode>\&boundaryType=\<boundaryType> | POST           | <p>{</p><p>  "RequestInfo": {</p><p>    "authToken": "string"</p><p>  }</p><p>}</p><p><br></p>                                                                                                                                                                                                                                                                                                                           |

### Date Range Filter Options

The date range can be controlled with the following three options provided to the user: &#x20;

* Custom Date Range
* Today
* Cumulative

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-04-14 at 10.38.04 AM.png" alt=""><figcaption></figcaption></figure>

#### Usage

* Custom Date Range: The user will  be able to choose any date range between the campaign start date and the current day
* Today: The date picker will be disabled and the date range will be set to the current day.
* Cumulative: The date picker will be disabled and the date range will be set for the duration of the campaign start date to the current day.

### New Charts and Enhancements

### Heatmaps

#### Overview

Heatmaps display the boundary-based coverage for a campaign using a relative colours gradient scale. The colour of a boundary changes based on the coverage percentage value, and the user is allowed to click on a higher level boundary (state) to drilldown to the lower level regions (state → district).

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-04-14 at 10.40.03 AM.png" alt=""><figcaption></figcaption></figure>

#### Setup

* The chart component uses a react-simple-maps library to render the geographical map of the target region.
* The component expects a GeoJSON file which is stored as a static file in the MDMS.
* The component fetches the aggregated data from the analytics service and plots it on the geographical map to show the coverage achieved by the boundaries.

The GeoJSON files are stored in MDMS under the “map-config” module:

[https://github.com/egovernments/health-campaign-mdms/tree/DEV/data/default/map-config](https://github.com/egovernments/health-campaign-mdms/tree/DEV/data/default/map-config)

#### API Requests

| End point                                       | Request method | Request payload                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ----------------------------------------------- | -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /egov-mdms-service/v1/\_search?tenantId=default | POST           | <p>{</p><p>   "MdmsCriteria": {</p><p>       "tenantId": "string",</p><p>       "moduleDetails": [</p><p>           {</p><p>               "moduleName": "map-config",</p><p>               "masterDetails": [</p><p>                   {</p><p>                       "name": "national-map"</p><p>                   }</p><p>               ]</p><p>           }</p><p>       ]</p><p>   },</p><p>   "RequestInfo": {</p><p>       "authToken": "string"</p><p>   }</p><p>}</p><p><br></p> |
| /dashboard-analytics/dashboard/getChartV2       | POST           | <p>{</p><p>   "aggregationRequestDto": {</p><p>       "visualizationType": "TABLE",</p><p>       "visualizationCode": "string",</p><p>       "queryType": "",</p><p>       "filters": {},</p><p>       "moduleLevel": "",</p><p>       "aggregationFactors": null</p><p>   },</p><p>   "headers": {</p><p>       "tenantId": "string"</p><p>   },</p><p>   "RequestInfo": {</p><p>       "authToken": "string"</p><p>   }</p><p>}</p>                                                        |

### Stacked Collection

Stacked collection displays the metric data in a columnar fashion on the national dashboard (landing page). It grows vertically based on the length of the metric charts that are configured as part of the collection.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-04-14 at 10.42.42 AM.png" alt=""><figcaption></figcaption></figure>

#### Setup

Setting the vizType field to “stacked-collection” will enable this chart. A stacked view is enabled only on the landing page (Example: National dashboard).

```
{
"id": 201,
"name": "DSS_HEALTH_HOUSEHOLDS",
"label": "DSS_HEALTH_HOUSEHOLDS",
"vizType": "stacked-collection",
"noUnit": true,
"isCollapsible": false,
"charts": [
	{
 "id": "householdVisitsWithinDateRange",
 "name": "DSS_HEALTH_OVERVIEW_HOUSEHOLDS_VISITED_OVER_DATERANGE",
 "code": "",
 "chartType": "metric",
 "filter": "",
 "headers": []
},
{
 "id": "totalVisits",
 "name": "DSS_HEALTH_OVERVIEW_TOTAL_HOUSEHOLD_VISITS",
 "code": "",
 "chartType": "metric",
 "filter": "",
 "headers": []
}
]
}
```

\
\
\
\
