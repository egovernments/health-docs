---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/ui-configuration/dashboard-configuration/dashboard-ui-enhancements
---

# Dashboard UI Enhancements

## Overview

Dashboard UI enhancements allow administrators to tailor the visual layout, widgets, and interactive elements of the HCM dashboard to specific use cases. This includes the ability to add custom widgets, reorganise components, and apply UI theming.

## Key Parameters &#x20;

<table><thead><tr><th width="142.8671875">Parameter</th><th width="124.6875">Type</th><th width="266.5390625">Description</th><th>Example</th></tr></thead><tbody><tr><td><code>widgets</code></td><td>Array</td><td>List of dashboard widgets to display</td><td>See sample above</td></tr><tr><td><code>id</code></td><td>String</td><td>Unique identifier for the widget</td><td><code>"totalPatients"</code></td></tr><tr><td><code>type</code></td><td>String</td><td>Widget type (<code>stat</code>, <code>chart</code>, <code>table</code>, etc.)</td><td><code>"stat"</code></td></tr><tr><td><code>label</code></td><td>String</td><td>Display name for the widget</td><td><code>"Total Patients"</code></td></tr><tr><td><code>dataSource</code></td><td>String</td><td>Backend service providing data</td><td><code>"patientService"</code></td></tr><tr><td><code>options</code></td><td>Object</td><td>Widget-specific options (icon, color, etc.)</td><td><code>{ "icon": "user" }</code></td></tr><tr><td><code>layout</code></td><td>Object</td><td>Controls column count and widget order</td><td><code>{ "columns": 2 }</code></td></tr><tr><td><code>theme</code></td><td>Object</td><td>Theme customization for the dashboard</td><td><code>{ "primaryColor": ...}</code></td></tr></tbody></table>

## Configuration Steps

{% stepper %}
{% step %}
### Locate Configuration

* Navigate to the dashboard configuration file&#x20;
{% endstep %}

{% step %}
### Edit Widgets

* Add or remove widgets by editing the `widgets` array.
* Configure `id`, `type`, `label`, `dataSource`, and `options`.
{% endstep %}

{% step %}
### Adjust Layout

* Change the number of columns or the display order in the `layout` object.
{% endstep %}

{% step %}
### Set Theme

* Update primary/secondary colours and other theme properties in the `theme` object.
{% endstep %}

{% step %}
### Save & Deploy

* Save the configuration file.
* Redeploy or restart the frontend service if required.
{% endstep %}
{% endstepper %}

## Project Selection

### Overview

After a supervisor logs into the HCM web app, the project services will be invoked to set the locations that are tagged to the user.

#### Initialising Default Campaign Filters

* Based on the details of the user logged in to the dashboard, the project-staff-search is invoked to get the projects associated with the user.&#x20;
* A Project-Search is then invoked to get the complete project details, which include campaign start and end dates, boundary information, etc.
* The MDMS API is invoked to get more details about the project based on “projectType”.
* The boundary-service is invoked to get the boundary information based on boundaryCode that was obtained from the project details.
* A supervisor can navigate to their corresponding dashboards (national/ provincial/district) using the following URLs:

&#x20;     \- [https://health-demo.digit.org/digit-ui/employee/dss/dashboard/national-health-dashboard](https://health-demo.digit.org/digit-ui/employee/dss/dashboard/national-health-dashboard)

&#x20;     \- [https://health-demo.digit.org/digit-ui/employee/dss/dashboard/provincial-health-dashboard?province=Tete](https://health-demo.digit.org/digit-ui/employee/dss/dashboard/provincial-health-dashboard?province=Tete)

&#x20;     \- [https://health-demo.digit.org/digit-ui/employee/dss/dashboard/district-health-dashboard](https://health-demo.digit.org/digit-ui/employee/dss/dashboard/district-health-dashboard)

* On the dashboards, users can only view the information which was synced corresponding to the projects they are associated with. As more devices sync, the dashboards will be updated with the latest synced data.

## API Requests

<table><thead><tr><th width="191.42708333333331">Endpoint</th><th width="170.89453125">Request Method</th><th>Request Payload</th></tr></thead><tbody><tr><td>/project/staff/v1/_search</td><td>POST</td><td><p>{</p><p>   "ProjectStaff": {</p><p>       "staffId": "loggedInUserId"</p><p>   },</p><p>   "RequestInfo": {</p><p>       "authToken": "string",</p><p>  }</p><p>}</p></td></tr><tr><td>/project/v1/_search</td><td>POST</td><td><p>{</p><p>   "RequestInfo": {</p><p>       "authToken": "string"</p><p>   },</p><p> "Projects": [</p><p>     {      "id":"projectId",</p><p>       "tenantId": "string"</p><p>     }</p><p> ]</p><p>}</p></td></tr><tr><td>/egov-mdms-service/v1/_search?tenantId=default</td><td>POST</td><td><p>{</p><p>  "MdmsCriteria": {</p><p>    "tenantId": "default",</p><p>    "moduleDetails": [</p><p>      {</p><p>        "moduleName": "HCM-PROJECT-TYPES",</p><p>        "masterDetails": [</p><p>          {</p><p>            "name": "projectTypes"</p><p>          }</p><p>        ]</p><p>      }</p><p>    ]</p><p>  },</p><p>  "RequestInfo": {</p><p>    "authToken": "string"</p><p>  }</p><p>}</p></td></tr><tr><td>/boundary-service/boundary-relationships/_search?tenantId=&#x3C;tenant_ID>&#x26;hierarchyType=&#x3C;herirarchy_type></td><td>POST</td><td><p>{</p><p>  "RequestInfo": {</p><p>    "authToken": "string"</p><p>  }</p><p>}</p><p><br></p></td></tr></tbody></table>

### Date Range Filter Options

The date range can be controlled with the following three options provided to the user: &#x20;

* Custom Date Range
* Today
* Cumulative

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-04-14 at 10.38.04 AM.png" alt=""><figcaption></figcaption></figure>

#### Usage

* Custom Date Range: The user will  be able to choose any date range between the campaign start date and the current day
* Today: The date picker will be disabled, and the date range will be set to the current day.
* Cumulative: The date picker will be disabled, and the date range will be set for the duration of the campaign start date to the current day.

### New Charts and Enhancements

### Heatmaps

#### Overview

Heatmaps display the boundary-based coverage for a campaign using a relative colour gradient scale. The colour of a boundary changes based on the coverage percentage value, and the user is allowed to click on a higher-level boundary (state) to drill down to the lower-level regions (state → district).

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-04-14 at 10.40.03 AM.png" alt=""><figcaption></figcaption></figure>

#### Setup

* The chart component uses a react-simple-maps library to render the geographical map of the target region.
* The component expects a GeoJSON file, which is stored as a static file in the MDMS.
* The component fetches the aggregated data from the analytics service and plots it on the geographical map to show the coverage achieved by the boundaries.

The GeoJSON files are loaded to s3 assets.

These file references are stored in MDMS under the “map-config” module and "GeoJsonMapping" master:

```
{
  "tenantId": "mz",
  "moduleName": "map-config",
  "GeoJsonMapping": [
          {
            "code": "gaza",
            "url": "https://egov-demo-assets.s3.ap-south-1.amazonaws.com/health/map/gaza.json"
          },
          {
            "code": "rivercess",
            "url": "https://egov-demo-assets.s3.ap-south-1.amazonaws.com/health/map/rivercess.json"
          },
          {
            "code": "national-map",
            "url": "https://egov-demo-assets.s3.ap-south-1.amazonaws.com/health/map/national-map.json"
          },
          {
            "code": "nampula",
            "url": "https://egov-demo-assets.s3.ap-south-1.amazonaws.com/health/map/nampula.json"
          },
          {
            "code": "iccd_mb",
            "url": "https://egov-demo-assets.s3.ap-south-1.amazonaws.com/health/map/national-map.json"
          }
      ]
}
```

API Requests

<table><thead><tr><th width="184.30598958333331">Endpoint</th><th width="150.75390625">Request Method</th><th>Request Payload</th></tr></thead><tbody><tr><td>/mdms-v2/v1/_search?tenantId=mz</td><td>POST</td><td><p>{</p><p>   "MdmsCriteria": {</p><p>       "tenantId": "string",</p><p>       "moduleDetails": [</p><p>           {</p><p>               "moduleName": "map-config",</p><p>               "masterDetails": [</p><p>                   {</p><p>                       "name": "GeoJsonMapping"</p><p>                   }</p><p>               ]</p><p>           }</p><p>       ]</p><p>   },</p><p>   "RequestInfo": {</p><p>       "authToken": "string"</p><p>   }</p><p>}</p></td></tr><tr><td>/dashboard-analytics/dashboard/getChartV2</td><td>POST</td><td><p>{</p><p>   "aggregationRequestDto": {</p><p>       "visualizationType": "TABLE",</p><p>       "visualizationCode": "string",</p><p>       "queryType": "",</p><p>       "filters": {},</p><p>       "moduleLevel": "",</p><p>       "aggregationFactors": null</p><p>   },</p><p>   "headers": {</p><p>       "tenantId": "string"</p><p>   },</p><p>   "RequestInfo": {</p><p>       "authToken": "string"</p><p>   }</p><p>}</p></td></tr></tbody></table>

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

### Rich Summary Card

A collection of metrics which are displayed in a grid-based fashion. If the “valueType” of a metric is ‘percentage’, then this chart will display a circular progressbar for the metric. This is a vizType which accepts one or more ‘metric’ charts as children.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-04-14 at 10.46.19 AM.png" alt=""><figcaption></figcaption></figure>

#### Setup

Setting the vizType field to "stacked-collection" will enable this chart on the dashboard pages (Example: Provincial dashboard).

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
   },
   {
     "id": "householdVisitsTargetProvince",
     "name": "DSS_HEALTH_OVERVIEW_TARGET_HOUSEHOLD_VISITS",
     "code": "",
     "chartType": "metric",
     "filter": "",
     "headers": []
   },
   {
     "id": "totalHouseholdCoverageProvince",
     "name": "DSS_HEALTH_OVERVIEW_TOTAL_COVERAGE_HOUSEHOLD_VISITS",
     "code": "",
     "chartType": "metric",
     "filter": "",
     "headers": []
   }
 ]
}
```

### Vertically Growing Card List

A list of cards inside a container that grows vertically. The container displays a vertical scrollbar if the number of items in the container is more than the height of the container.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-04-14 at 10.47.47 AM.png" alt=""><figcaption></figcaption></figure>

#### Setup

Setting the vizType field to "stacked-table" will enable this chart on the landing page (Example: National dashboard). The vizType accepts a ‘table’ chart as its child and uses the table chart data to render the list of cards on the page.

```
{
 "id": 301,
 "name": "DSS_COVERAGE_BY_PROVINCE",
 "label": "DSS_COVERAGE_BY_PROVINCE",
 "vizType": "stacked-table",
 "noUnit": true,
 "isCollapsible": false,
 "ref": {
   "url": "provincial-health-dashboard",
   "logoUrl": "",
   "type": "internal"
 },
 "charts": [
   {
     "id": "coverageByProvince",
     "name": "DSS_COVERAGE_BY_PROVINCE",
     "code": "",
     "chartType": "table",
     "filter": "",
     "headers": []
   }
 ]
}
```

### Banner Card

A card with a horizontal list of items displayed on top of the dashboard. It displays the items in a single row with the labels on top and the value at the bottom.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-04-14 at 10.49.34 AM.png" alt=""><figcaption></figcaption></figure>

#### Setup

This chart can be enabled by setting the “vizType” to “bannercard”. This visualisation accepts a ‘table’ chart as its child, and the table chart’s response should include only a single row.

```
{
 "id": 200,
 "name": "DSS_HEALTH_USER_SYNC_OVERVIEW",
 "label": "DSS_HEALTH_USER_SYNC_OVERVIEW",
 "vizType": "bannercard",
 "noUnit": true,
 "isCollapsible": false,
 "charts": [
   {
     "id": "userSyncSummaryProvince",
     "name": "DSS_HEALTH_USER_SYNC_SUMMARY",
     "code": "",
     "chartType": "table",
     "filter": "",
     "headers": []
   }
 ]
}
```

### Bar Charts with Brush

The brush component enabled for bar charts will let the users zoom and pan a bar chart without losing view of any data item. This enables the chart to have any number of bars, and the user can focus on the selected range by adjusting the brush displayed at the bottom of the charts.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-04-14 at 10.50.58 AM.png" alt=""><figcaption></figcaption></figure>

#### Setup

No additional setup is required for enabling the brush component. It is enabled on bar charts by default if the chart contains more than one bar.

Reference: [https://recharts.org/en-US/examples/BrushBarChart](https://recharts.org/en-US/examples/BrushBarChart)

### Config to Hide Filters&#x20;

The visibility of the default filters displayed on the dashboard page can be controlled using a new configuration field introduced in the “MasterDashboardConfig.json” file.

#### Setup&#x20;

Include the filters that need to be hidden from the dashboard within the “hideFilterFields” array. The UI has the logic to conditionally show/hide the filters based on this field. Allowed elements in the array: ModuleFilter, DateRange, DDR, Ulb, Denomination.

```
{
 "name": "DSS_HEALTH_OVERVIEW_DASHBOARD_LLIN_HEADING",
 "id": "district-health-dashboard",
 "isActive": "",
 "hideFilterFields": ["DDR", "Ulb", "Denomination", "ModuleFilter"],
 "style": "linear",
 "visualizations": []
}
```

## Pie Chart with a Label in the Centre

The pie chart component can be made to display the cumulative value in the centre of the chart based on the “showLabel” config field set for pie charts.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-04-14 at 10.55.56 AM.png" alt=""><figcaption></figcaption></figure>

#### Setup

Set the “showLabel” field for a pie chart (ChartApiConfig.json) to ‘true’ to enable the label.

```
{
"samplePieChart": {
"chartName": "CHART",
"queries": [],
"chartType": "pie",
"valueType": "number",
"showLabel": true,
"drillChart": "none",
"documentType": "_doc",
"action": "",
"aggregationPaths": [],
"insight": {},
"_comment": " “
}
}
```

## Line Chart with Prediction

The line chart can be configured to display future projections based on the existing data set by enabling a configuration field in the respective chart configuration.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-04-14 at 10.57.07 AM.png" alt=""><figcaption></figcaption></figure>

#### Setup

Set the “predictionPath” field in the line chart configuration to point to a specific aggregation path from which the prediction data needs to be calculated. If the “predictionPath” is not available for a line chart, then the prediction will be skipped for the respective chart.

```
{
"actualVsPlannedLineGraph": {
 "chartName": "DSS_HEALTH_ACTUAL_VS_PLANNED_LINE_GRAPH",
 "queries": [
   {
...
     "aggrQuery": "QUERY_WITH_THE_AGGREGATE_PATH_FOR_PREDICTION”
   }
 ],
 "chartType": "line",
 "isCumulative": true,
 "valueType": "number",
 "drillChart": "none",
 "documentType": "_doc",
 "action": "",
 "predictionPath" : "Target_Path",
 "aggregationPaths": [
   "Target_Path"
 ],
 "insight": { },
 "_comment": " "
}
}
```

### Table Chart with Footer

The table chart can be configured to display a footer row at the bottom to show the cumulative total of the row values for all columns with numeric values. Percentages and non-numeric values will not be included in the total value.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-04-14 at 10.58.28 AM.png" alt=""><figcaption></figcaption></figure>

#### Setup

Set the “showFooter” field in the line chart configuration to ‘true’. This will enable the footer row for the respective table chart.

```
{
"tableChart": {
 "chartName": "CHART_WITH_FOOTER",
 "queries": [],
 "chartType": "xtable",
 "valueType": "number",
 "documentType": "_doc",
 "action": "",
 "hideInsights": true,
 "showFooter": true,
 "_comment": " “
}
}
```

## Backend Enhancements

### Filter Data for the Current Day

The charts can be configured to filter the data only for the current day without hard-coding the date range in the aggregation query.

#### Setup

Set the “filterForCurrentDay” field in the line chart configuration to ‘true’. This will override the date range in the backend and filter only the data that are inserted for the current day.

```
{
"todaysVisits": {
 "chartName": "DSS_HEALTH_NATIONAL_HOUSEHOLDS_VISITED_TODAY",
 "chartType": "metric",
 "valueType": "number",
 "drillChart": "none",
 "documentType": "_doc",
 "filterForCurrentDay": true,
 "action": "",
 "_comment": " “
}
}
```

### Percentage Calculation for Line Charts & Bar Charts

Line charts can be configured to display percentages calculated based on the results from two aggregation paths.

#### Setup

* Ensure that there are exactly two aggregation queries.&#x20;
* The result from the first query will be used as the numerator, and the second result set will be used as the denominator for the percentage calculation.
* Set ‘percentage’ as the value of the ‘action’ field in the chart configuration.

```
{
"barChartWithPercentage": {
 "chartName": "BAR_CHART_WITH_PERCENTAGE",
 "queries": [
   {
     "module": "COMMON",
     "aggrQuery": "NUMERATOR"
   },
   {
     "module": "COMMON",
     "aggrQuery": "DENOMINATOR"
   }
 ],
 "chartType": "line",
 "valueType": "percentage",
 "documentType": "_doc",
 "action": "percentage",
 "aggregationPaths": ["Quantity","Target"],
}
}
```

### Division Calculation for Line/Bar Charts

Line charts can be configured to divide one dataset by another to calculate the quotient value.&#x20;

**Example:** This is used in the inventory chart on the health dashboard to calculate the number of days the stock will last in an inventory by dividing the existing count by the target value.

#### Setup

* Ensure that there are exactly two aggregation queries.
* The result from the first query will be used as the numerator, and the second result set will be used as the denominator to calculate the quotient.
* Set ‘division’ as the value of the ‘action’ field in the chart configuration.

```
{
"barChartWithPercentage": {
 "chartName": "BAR_CHART_WITH_PERCENTAGE",
 "queries": [
   {
     "module": "COMMON",
     "aggrQuery": "NUMERATOR"
   },
   {
     "module": "COMMON",
     "aggrQuery": "DENOMINATOR"
   }
 ],
 "chartType": "line",
 "valueType": "number",
 "documentType": "_doc",
 "action": "division",
 "aggregationPaths": ["Quantity","Target"],
}
}
```

### Calculate Sum of 2 Datasets for Line/Bar Charts

Line charts can be configured to calculate the sum of two aggregated datasets returned by the aggregation queries.&#x20;

**Example:** This is used in the inventory chart that displays the number of stocks that are available in hand by calculating the sum of the incoming stocks.

#### Setup

* Ensure that there is more than one aggregation query preset to calculate the sum.
* Mention the “actionName” as “SumComputedField” within the chart’s computedFields.
* Include the aggregation paths that are required to calculate the sum.

```
{
"chartWithSumOfBuckets": {
 "chartName": "LINE_CHART",
 "queries": [
   {
     "module": "COMMON",
     ...
     "aggrQuery": "QUERY_1"
   },
   {
     "module": "COMMON",
     ...
     "aggrQuery": "QUERY_2"
   }
 ],
 "chartType": "line",
 "computedFields": [
   {
     "postAggregationTheory": "",
     "actionName": "SumComputedField",
     "fields": [
       "Result 1",
       "Result 2"
     ],
     "newField": "Sum",
     "_comments": ""
   }
 ],
...
}
}
```

### Divide Bucket Data by a Constant

Line charts can be configured to perform the division on a bucket of data by a constant value. This can be used to calculate the percentage share of individual bucket items by comparing with the total sum of data.&#x20;

**Example:** This is used in the complaints chart, which displays the district-wise share of complaints by comparing against the overall number of complaints registered for the entire province.

#### Setup

* Ensure that there are exactly two aggregation queries. The first should return the aggregation results in a bucket. The second result should be the sum of the values.
* Set “divisionbyconstant” as the value of the ‘action’ field.

```
{
"chartWithDivideByConstant": {
 "chartName": "DIVIDE_BY_CONSTANT",
 "queries": [
   {
     "module": "COMMON",
     ...
     "aggrQuery": "BUCKET_RESULTS"
   },
   {
     "module": "COMMON",
     ...
     "aggrQuery": "CONSTANT_VALUE"
   }
 ],
 "chartType": "line",
 "isCumulative": false,
 "valueType": "number",
 "action": "divisionbyconstant",
 "aggregationPaths": ["BUCKET_RESULTS","CONSTANT_VALUE"],
 "insight": { },
 "_comment": " “
}
}
```

### Enable Sorting for Post-Computed Results

Line charts do not retain the original sort order after performing the computation. Using the sort action, the computed results can be sorted based on the bucket keys or values in both ascending and descending order.

#### Setup

* The “computedFields” object accepts the ‘sort’ field, and the value should denote the order of the sorting expected.
* The ‘sort’ field accepts four values:

&#x20;      \- sortValueAsc: To sort based on the increasing order of the values.

&#x20;      \- sortValueDesc: To sort based on the decreasing order of the values.

&#x20;      \- sortKeyAsc: To sort based on the increasing order of the keys.

&#x20;      \- sortKeyDesc: To sort based on the decreasing order of the keys.

```
{
"sortedChart":{
 "chartName": "CHART_WITH_SORT",
 "queries": [
   {
     "module": "COMMON",
     ...
     "aggrQuery": "QUERY_1"
   },
   {
     "module": "COMMON",
     ...
     "aggrQuery": "QUERY_2"
   }
 ],
 "chartType": "line",
 "isCumulative": false,
 "valueType": "percentage",
 "action": "percentage",
 "aggregationPaths": ["AGGR1","AGGR2"],
 "computedFields": [
   {
     "postAggregationTheory" : "repsonseToDifferenceOfDates",
     "actionName": "",
     "sort": "sortValueDesc",
     "fields" : ["AGGR1"],
     "newField" : "RESULT",
     "_comments": ""
   }
 ],
 "insight": { },
 "_comment": " "
}
}
```

### Day-Wise Insights for Metric Charts

Enabling insights’ calculation based on the day shows the comparison between the current day’s data and the previous day’s data.

#### Setup

* Setting the ‘interval’ field to ‘day’ inside the ‘insight’ object will enable day-wise insight calculation
* The date range selected for fetching the data should not be more than a single day to calculate day-wise insights.

```
"insight": {
 "chartResponseMap": "todaysVisits",
 "action": "differenceOfNumbers",
 "upwardIndicator": "positive",
 "downwardIndicator": "negative",
 "textMessage": "$indicator$value% than last $insightInterval",
 "colorCode": "#228B22",
 "insightInterval": "day”
}
```

### Date-Range Insights for Metric charts

Enabling Insights calculation for a date range shows the comparison between the Data from (project start date to the current date) and (project start date to the previous day).

#### Setup

* Setting the ‘insightInterval’ field to “dateRange” inside the “insight” object will enable date-range insight calculation.
* The date range Insight interval can be applied only for date ranges more than one day.

```
"insight": {
      "chartResponseMap": "bednetsDistributionCoverage",
      "action": "differenceOfNumbers",
      "upwardIndicator": "positive",
      "downwardIndicator": "negative",
      "textMessage": "$indicator$value% than last $insightInterval",
      "colorCode": "#228B22",
      "insightInterval": "dateRange"
}
```
