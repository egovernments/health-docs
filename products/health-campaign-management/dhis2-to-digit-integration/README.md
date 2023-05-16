# DHIS2 to DIGIT Integration

## Integration & Interoperability with DHIS2:

[https://dhis2.org/integration/](https://dhis2.org/integration/)

## Basic features

Data Capture

Validation

Analysis

Presentation

## Points to explore

SDMX-HD and ADX standards for interoperability

SDMX: [https://ec.europa.eu/eurostat/web/sdmx-infospace/trainings-tutorials](https://ec.europa.eu/eurostat/web/sdmx-infospace/trainings-tutorials)

SDMX-HD:[https://wiki.openmrs.org/display/docs/SDMX-HD#:\~:text=SDMX%2DHD%20(Health%20Domain),and%20metadata%20between%20medical%20organizations](https://wiki.openmrs.org/display/docs/SDMX-HD).

ADX: Aggregate Data Exchange

### Modules of concern

DHIS2 Web API

DHIS2 Core

### How can we use it?

It exposes REST API(s) over DHIS2 Core which we can utilise.

### Web API Integration

[https://docs.dhis2.org/en/full/develop/dhis-core-version-master/developer-manual.html](https://docs.dhis2.org/en/full/develop/dhis-core-version-master/developer-manual.html)

### Authentication

DHIS2 provides Basic Auth, Two Factor Auth, Personal Access Token(PAT) and OAuth2. Basic Auth is the least secure and Two Factor Auth is for direct DHIS2 users.

**PAT**

By default PAT will have all the authorizations that the user has. This can be configured or a special user can be created having only the required permissions.

The token is configurable via API and only the constraints can be modified after a token is created.

Token key is returned only once when the token is generated.

Expiry of the token can be configured via Web API along with other constraints.

**OAuth2**

We can go with grant\_type as password. This can be configured via Web API too. Grant\_type password would involve sharing username and password. However, this will be in a POST call body.

### Login Credentials

[http://43.205.92.152/dhis-web-commons/security/login.action](http://43.205.92.152/dhis-web-commons/security/login.action)

User: admin

Pass: district

### DHIS2 Fields and Mappings

[DHIS2 Fields Extract](https://docs.google.com/spreadsheets/d/1aXzaUUgqQE0LmFt44zf9wq6lynkYlVj3EROZtYdOvOs/edit?usp=sharing)

List of the metadata which are required and there attributes

Note this data is extracted from the schemas endpoint of DHIS2

DHIS2 is District Health Information Software 2.

### Some Details

The DHIS 2 is a routine data based health information system which allows for:&#x20;

* data capture,&#x20;
* aggregation,&#x20;
* analysis, and&#x20;
* reporting of data.

## Data Model

The data model is generic in all dimensions in order to allow for capture of any item of data.&#x20;

The model is based on the notion of a DataValue.

&#x20;A DataValue can be captured for&#x20;

* any DataElement (which represents the captured item, occurrence or phenomena),
* Period (which represents the time dimension), and&#x20;
* Source (which represents the space dimension, i.e. an organisational unit in a hierarchy).

<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-16 at 2.22.39 PM.png" alt=""><figcaption></figcaption></figure>

| Meta Data          | Understanding on this                                                                                                                                                                                                                               | Remarks                                                                                                                                           |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| DataSet            | <p>The DataSet is a collection of DataElements for which there is entered data presented as a list, a grid and a custom designed form. </p><p>A DataSet is associated with a PeriodType, which represents the frequency of data capture. </p>       | This is what is a campaign as per current understanding                                                                                           |
| Data Element       | Basically a Form Field                                                                                                                                                                                                                              | The data element often represents a count of something, and its name describes what is being counted, e.g. "BCG doses given" or "Malaria cases".  |
| Data Element Group | Group of Data Element                                                                                                                                                                                                                               |                                                                                                                                                   |
| Indicator          | <p>Allows for data analytics and reporting. Its basically output of data capture. An Indicator is basically a mathematical formula consisting of DataElements and numbers.</p><p> </p><p>The formula is split into a numerator and denominator.</p> |                                                                                                                                                   |
| IndicatorType      | <p>An Indicator is associated with an IndicatorType, which indicates the factor of which the output should be multiplied with. </p><p> </p><p>A typical IndicatorType is percentage, which means the output should be multiplied by 100.</p>        |                                                                                                                                                   |
| OrgUnit            | Source or manageable area under which the data is captured                                                                                                                                                                                          |                                                                                                                                                   |
| Category           |                                                                                                                                                                                                                                                     |                                                                                                                                                   |

METADATA Diagram taken from the DHIS2 technical documentation

<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-16 at 2.23.39 PM.png" alt=""><figcaption></figcaption></figure>

The diagram is taken from the core technical documentation for understanding the relationships between the DHIS2:

<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-16 at 2.24.29 PM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-16 at 2.25.41 PM.png" alt=""><figcaption></figcaption></figure>

While adding dhis2 client [https://github.com/dhis2/dhis2-java-client](https://github.com/dhis2/dhis2-java-client)\


<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-16 at 2.26.36 PM.png" alt=""><figcaption></figcaption></figure>
