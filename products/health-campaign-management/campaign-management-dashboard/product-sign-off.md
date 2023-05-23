# Product Sign-Off

A formal sign-off came from the product team after completing the functional, UI, and data testing of the dashboard for V 1.0 capabilities. No critical show-stopper issues were observed.&#x20;

The dashboard has been tested on the following aspects:

1. Data Accuracy:

* Data ingested from the HCM App is reflected correctly on the dashboard.
* Accuracy of calculations and aggregations.
* Data displayed is up-to-date and correctly refreshed.

2. Data Completeness:

* All data ingested from the app is reflected in the dashboard.
* Presence of all metrics, and dimensions as expected.

3. Functionality:

* Data filter, search, sort, drill-downs (tabular charts), data export, download, hover, date picker, and navigation functionalities.

4. UI:

* The UI elements match the design in Figma.
* All the widgets, graphs, and charts as per the design are present on the dashboard.

The other set of features that were part the testing include:

* Lat-long maps&#x20;
* Multi-level drilldowns for bar charts&#x20;
* Supervision module&#x20;
* About, FAQ, and Calculation pages&#x20;
* Heat/Lat-long maps, re-centre button&#x20;
* Bar chart with target line on the Registration & Delivery page

The data testing was done by ingesting the micro plan data and transactional data for 1 province. However, testing with high-volume data (ingestion through Kibana) to simulate the scenario of Group IV distribution (3 provinces) and for outliers is pending and will be completed by June 1st half. All the known functional and UI bugs, and enhancements were noted during testing. The estimated resolution timeline is as follows:&#x20;

Medium priority Bugs - May 25th

Low-priority bugs and enhancements Mid-June

Planned vs Actual graph - May 19th
