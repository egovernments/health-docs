# Project Factory - Campaign Manager

## Overview

This service is used to create a Project (Campaign), create required resource data, and create a mapping relation between them based on the boundary data.

Project Factory Flow

<figure><img src="https://docs.digit.org/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2FeypOjSDXyVWvcapwLdRO%2FScreenshot%25202024-03-02%2520at%25209.25.14%2520AM.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=4251d3eb&#x26;sv=2" alt=""><figcaption></figcaption></figure>

## **Dependencies**

1. Project
2. Facility
3. Product
4. HRMS
5. MDMS
6. Boundary
7. Localisation
8. Access Control
9. IdGen
10. Individual
11. User

## API Specification <a href="#api-specification" id="api-specification"></a>

Base Path: /project-factory/

API Contract [Link](https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/DIGIT-Specs/hcm-workbench/Domain+Services/Health/project-factory.yaml)

[Swagger Editor](https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/DIGIT-Specs/hcm-workbench/Domain+Services/Health/project-factory.yaml) - Project Factory API Spec

## Data Model <a href="#data-model" id="data-model"></a>

#### DB Schema Diagram <a href="#db-schema-diagram" id="db-schema-diagram"></a>

Project Factory related tables

<figure><img src="https://docs.digit.org/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2F9EoZVNMYeF7Jtspcyi2W%2FScreenshot%25202024-08-30%2520at%25209.32.35%2520AM.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=d8047b90&#x26;sv=2" alt=""><figcaption></figcaption></figure>

<div align="left"><figure><img src="https://docs.digit.org/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2FJwwkgua2MoX8rYqwfXc3%2FScreenshot%25202024-08-30%2520at%25209.22.20%2520AM.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=51e66d7a&#x26;sv=2" alt=""><figcaption><p>Campaign Table</p></figcaption></figure></div>

Table Details

{% tabs %}
{% tab title="Campaign" %}
```dbml
Table eg_cm_campaign_details {
  id varchar(128) [primary key ,not null, unique]
  tenantid varchar(64) [not null ,note: 'Tenant identifier']
  campaignname varchar(250) [not null ,note: 'Name of the campaign']
  projecttype varchar(128) [not null ,note: 'Type of project']
  startdate bigint [note: 'Start date in epoch']
  enddate bigint [note: 'End date in epoch']
  campaigndetails jsonb [note: 'Campaign specific details']
  status varchar(128) [not null ,note: 'Status of the campaign']
  parentid varchar(128) [note: 'refering to the previous campaign id']
  action varchar(64) [not null ,note: 'Action type']
  campaignnumber varchar(128) [not null ,note: 'Campaign number']
  hierarchytype varchar(128) [not null ,note: 'Hierarchy type']
  boundarycode varchar(64) [note: 'Boundary code']
  projectid varchar(128) [note: 'Project identifier']
  createdby varchar(128) [not null ,note: 'Created by user ID']
  lastmodifiedby varchar(128) [note: 'Last modified by user ID']
  createdtime bigint [note: 'Creation timestamp']
  lastmodifiedtime bigint [note: 'Last modification timestamp']
  additionaldetails jsonb [note: 'Additional details']
}
```
{% endtab %}

{% tab title="Process" %}
```dbml
Table eg_cm_campaign_process {
  id varchar(128) [primary key, not null, unique]
  campaignid varchar(128) [not null,note: 'Foreign key to eg_cm_campaign_details.id']
  type varchar(128) [not null,note: 'Type of campaign process']
  status varchar(128) [not null,note: 'Status of the campaign process']
  details jsonb [note: 'Detailed information of the process']
  createdtime bigint [note: 'Creation timestamp']
  lastmodifiedtime bigint [note: 'Last modification timestamp']
  additionaldetails jsonb [note: 'Additional details']
}
Ref: eg_cm_campaign_process.campaignid > eg_cm_campaign_details.id // many-to-one
```
{% endtab %}

{% tab title="Generated Resource" %}
```dbml
Table eg_cm_generated_resource_details {
  id varchar(128) [primary key,not null, unique]
  filestoreid varchar(128) [note: 'File store ID']
  status varchar(128) [not null,note: 'Status of the resource']
  type varchar(128) [not null,note: 'Type of resource']
  tenantid varchar(128) [not null,note: 'Tenant identifier']
  count bigint [note: 'Count of resources']
  createdby varchar(128) [note: 'Created by user ID']
  createdtime bigint [note: 'Creation timestamp']
  lastmodifiedby varchar(128) [note: 'Last modified by user ID']
  lastmodifiedtime bigint [note: 'Last modification timestamp']
  additionaldetails jsonb [note: 'Additional details']
  hierarchytype varchar(128) [not null,note: 'Hierarchy type']
  campaignid varchar(128) [note: 'Foreign key to eg_cm_campaign_details.id']
}
Ref: eg_cm_generated_resource_details.campaignid > eg_cm_campaign_details.id // many-to-one

```
{% endtab %}

{% tab title="Resource Activity" %}
```dbml
Table eg_cm_resource_activity {
  id varchar(128) [primary key,not null, unique]
  retrycount int [note: 'Number of retry attempts']
  type varchar(64) [not null,note: 'Type of activity']
  url varchar(128) [not null,note: 'URL for the activity']
  requestpayload jsonb [note: 'Request payload']
  tenantid varchar(128) [not null,note: 'Tenant identifier']
  responsepayload jsonb [note: 'Response payload']
  status bigint [note: 'Status code']
  createdby varchar(128) [note: 'Created by user ID']
  createdtime bigint [note: 'Creation timestamp']
  lastmodifiedby varchar(128) [note: 'Last modified by user ID']
  lastmodifiedtime bigint [note: 'Last modification timestamp']
  additionaldetails jsonb [note: 'Additional details']
  resourcedetailsid varchar(128) [not null,note: 'Foreign key to eg_cm_resource_details.id']
}
Ref: eg_cm_resource_activity.resourcedetailsid > eg_cm_resource_details.id // many-to-one

```
{% endtab %}

{% tab title="Resource Details" %}
```dbml


Table eg_cm_resource_details {
  id varchar(128) [primary key,not null, unique]
  status varchar(128) [note: 'Status of the resource']
  tenantid varchar(128) [not null,note: 'Tenant identifier']
  filestoreid varchar(128) [note: 'File store ID']
  processedfilestoreid varchar(128) [note: 'Processed file store ID']
  action varchar(128) [not null,note: 'Action type']
  type varchar(64) [not null,note: 'Type of resource']
  createdby varchar(128) [note: 'Created by user ID']
  createdtime bigint [note: 'Creation timestamp']
  lastmodifiedby varchar(128) [note: 'Last modified by user ID']
  lastmodifiedtime bigint [note: 'Last modification timestamp']
  additionaldetails jsonb [note: 'Additional details']
  campaignid varchar(128) [note: 'Foreign key to eg_cm_campaign_details.id']
}

Ref: eg_cm_resource_details.campaignid > eg_cm_campaign_details.id // many-to-one


```
{% endtab %}
{% endtabs %}

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><mark style="color:blue;"><strong>Create Campaign</strong></mark></td><td><a href="create-campaign.md">create-campaign.md</a></td></tr><tr><td><mark style="color:blue;"><strong>Update Campaign</strong></mark></td><td><a href="update-campaign.md">update-campaign.md</a></td></tr><tr><td><mark style="color:blue;"><strong>Manage Resources</strong></mark></td><td><a href="manage-resources.md">manage-resources.md</a></td></tr></tbody></table>

## Web Sequence Diagrams <a href="#web-sequence-diagrams" id="web-sequence-diagrams"></a>

{% tabs %}
{% tab title="Data Create API" %}
<figure><img src="../../../../../.gitbook/assets/image (267).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Generate Data API" %}
<figure><img src="../../../../../.gitbook/assets/image (268).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Process Create Campaign API" %}
<figure><img src="../../../../../.gitbook/assets/image (269).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}
