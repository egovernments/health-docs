# Health UAT API Execution Report

```


<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
<title>eGov Extent Report</title>
<link rel="apple-touch-icon" href="https://cdn.jsdelivr.net/gh/extent-framework/extent-github-cdn@b00a2d0486596e73dd7326beacf352c639623a0e/commons/img/logo.png">
<link rel="shortcut icon" href="https://cdn.jsdelivr.net/gh/extent-framework/extent-github-cdn@b00a2d0486596e73dd7326beacf352c639623a0e/commons/img/logo.png">
<link href="https://cdn.jsdelivr.net/gh/extent-framework/extent-github-cdn@c43b89d03a7c43dae8bb8f0f078bad1997af6b3b/spark/css/spark-style.css" rel="stylesheet" />
<link href="https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet">
<script src="https://cdn.rawgit.com/extent-framework/extent-github-cdn/7cc78ce/spark/js/jsontree.js"></script>
<style type="text/css"></style></head><body class="spa -report standard">
  <div class="app">
    <div class="layout">
<div class="header navbar">
<div class="vheader">
<div class="nav-logo">
<a href="#">
<div class="logo" style="background-image: url('https://cdn.jsdelivr.net/gh/extent-framework/extent-github-cdn@b00a2d0486596e73dd7326beacf352c639623a0e/commons/img/logo.png')"></div>
</a>
</div>
<ul class="nav-left">
<li class="search-box">
<a class="search-toggle" href="#">
<i class="search-icon fa fa-search"></i>
<i class="search-icon-close fa fa-close"></i>
</a>
</li>
<li class="search-input"><input id="search-tests" class="form-control" type="text" placeholder="Search..."></li>
</ul>
<ul class="nav-right">
<li class="m-r-10">
<a href="#"><span class="badge badge-primary">eGov Automation Results</span></a>
</li>
<li class="m-r-10">
<a href="#"><span class="badge badge-primary">03/28/2023 01:16:32 PM</span></a>
</li>
</ul>
</div>
</div><div class="side-nav">
<div class="side-nav-inner">
<ul class="side-nav-menu">
<li class="nav-item dropdown" onclick="toggleView('dashboard-view')">
<a id="nav-dashboard" class="dropdown-toggle" href="#">
<span class="ico"><i class="fa fa-bar-chart"></i></span>
</a>
</li>
<li class="nav-item dropdown" onclick="toggleView('category-view')">
<a id="nav-category" class="dropdown-toggle" href="#">
<span class="ico"><i class="fa fa-tag"></i></span>
</a>
</li>
<li class="nav-item dropdown" onclick="toggleView('test-view')">
<a id="nav-test" class="dropdown-toggle" href="#">
<span class="ico"><i class="fa fa-list"></i></span>
</a>
</li>
</ul>
</div>
</div>      <div class="vcontainer">
        <div class="main-content">
<div class="container-fluid p-4 view dashboard-view">
<div class="row">
<div class="col-md-3">
<div class="card"><div class="card-body">
<p class="m-b-0">Started</p>
<h3>03/28/2023 01:16:32 PM</h3>
</div></div>
</div>
<div class="col-md-3">
<div class="card"><div class="card-body">
<p class="m-b-0">Ended</p>
<h3>03/28/2023 01:20:14 PM</h3>
</div></div>
</div>
<div class="col-md-3">
<div class="card"><div class="card-body">
<p class="m-b-0 text-pass">Tests Passed</p>
<h3>278</h3>
</div></div>
</div>
<div class="col-md-3">
<div class="card"><div class="card-body">
<p class="m-b-0 text-fail">Tests Failed</p>
<h3>0</h3>
</div></div>
</div>
</div>
<div class="row">
<div class="col-md-4">
<div class="card">
<div class="card-header">
<h6 class="card-title">Tests</h6>
</div>
<div class="card-body">
<div class="">
<canvas id='parent-analysis' width='115' height='90'></canvas>
</div>
</div>
<div class="card-footer">
<div><small data-tooltip='100%'>
<b>278</b> tests passed
</small>
</div>
<div>
<small data-tooltip='0%'><b>0</b> tests failed,
<b>0</b> skipped, <b data-tooltip='0%'>0</b> others
</small>
</div>
</div>
</div>
</div>
<div class="col-md-4">
<div class="card">
<div class="card-header">
<h6 class="card-title">Steps</h6>
</div>
<div class="card-body">
<div class="">
<canvas id='child-analysis' width='115' height='90'></canvas>
</div>
</div>
<div class="card-footer">
<div><small data-tooltip='100%'><b>556</b> steps passed</small></div>
<div>
<small data-tooltip='0%'><b>0</b> steps failed,
<b>0</b> skipped, <b data-tooltip='%'>0</b> others
</small>
</div>
</div>
</div>
</div>
<div class="col-md-4">
<div class="card">
<div class="card-header">
<h6 class="card-title">Log events</h6>
</div>
<div class="card-body">
<div class="">
<canvas id='events-analysis' width='115' height='90'></canvas>
</div>
</div>
<div class="card-footer">
<div><small data-tooltip='98%'><b>27,765</b> events passed</small></div>
<div>
<small data-tooltip='0%'><b>0</b> events failed,
<b data-tooltip='%'>556</b> others
</small>
</div>
</div>
</div>
</div>
</div>
<div class="row"><div class="col-md-12">
<div class="card"><div class="card-header"><p>Timeline</p></div>
<div class="card-body pt-0"><div>
<canvas id="timeline" height="120"></canvas>
</div></div>
</div>
</div></div>
<script>
var timeline = {
"<b>SCENARIO : </b>Test to create a household member with auth token of a registrar":0.049,"<b>SCENARIO : </b>Test to create a household with auth token of a distributor":0.014,"<b>SCENARIO : </b>Test to create a household member with invalid tenantId":0.003,"<b>SCENARIO : </b>Test to create a household member with a null tenantId":0.001,"<b>SCENARIO : </b>Test to create a household member with empty string for tenantId":0,"<b>SCENARIO : </b>Test to create a household member with householdClientReferenceId having a size less than minimum allowed number of characters":0,"<b>SCENARIO : </b>Test to create a household member with householdClientReferenceId having a size more than maximum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to create a household member with householdClientReferenceId being an empty string":0.001,"<b>SCENARIO : </b>Test to create a household member with individualClientReferenceId having a size less than minimum allowed number of characters":0,"<b>SCENARIO : </b>Test to create a household member with individualClientReferenceId having a size more than maximum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to create a household member with individualClientReferenceId being an empty string":0.001,"<b>SCENARIO : </b>Test to search for a household member without passing query parameters":0,"<b>SCENARIO : </b>Test to search for a household member by passing only limit query parameter":0.001,"<b>SCENARIO : </b>Test to search for a household member by passing only offset query parameter":0.001,"<b>SCENARIO : </b>Test to search for a household member by passing only tenantId query parameter":0,"<b>SCENARIO : </b>Test to search for a household member by passing only limit and offset query parameter":0.001,"<b>SCENARIO : </b>Test to search for a household member by passing only tenantId and offset query parameter":0.001,"<b>SCENARIO : </b>Test to search for a household member by passing only tenantId and limit query parameter":0.001,"<b>SCENARIO : </b>Test to search for a household member using different criteria":0.005,"<b>SCENARIO : </b>Test to update an existing household member with auth token of a distributor":0.005,"<b>SCENARIO : </b>Test to update an existing household member with id being an empty string":0.001,"<b>SCENARIO : </b>Test to update an existing household member with id having a size less than minimum allowed number of characters":0,"<b>SCENARIO : </b>Test to update an existing household member with id having a size more than maximum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to update an existing household member with a null tenantId":0.002,"<b>SCENARIO : </b>Test to update an existing household member with householdClientReferenceId having a size less than minimum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to update an existing household member with householdClientReferenceId having a size more than maximum allowed number of characters":0.002,"<b>SCENARIO : </b>Test to update an existing household member with householdClientReferenceId being an empty string":0.001,"<b>SCENARIO : </b>Test to update an existing household member with individualClientReferenceId having a size less than minimum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to update an existing household member with individualClientReferenceId having a size more than maximum allowed number of characters":0,"<b>SCENARIO : </b>Test to update an existing household member with individualClientReferenceId being an empty string":0.001,"<b>SCENARIO : </b>Test to delete an existing household member with auth token of a distributor":0.005,"<b>SCENARIO : </b>Test to delete an existing household member with id being an empty string":0,"<b>SCENARIO : </b>Test to delete an existing household member with id having a size less than minimum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to delete an existing household member with id having a size more than maximum allowed number of characters":0.002,"<b>SCENARIO : </b>Test to delete an existing household member with a null tenantId":0,"<b>SCENARIO : </b>Test to delete an existing household member with householdClientReferenceId having a size less than minimum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to delete an existing household member with householdClientReferenceId having a size more than maximum allowed number of characters":0,"<b>SCENARIO : </b>Test to delete an existing household member with householdClientReferenceId being an empty string":0.001,"<b>SCENARIO : </b>Test to delete an existing household member with individualClientReferenceId having a size less than minimum allowed number of characters":0,"<b>SCENARIO : </b>Test to delete an existing household member with individualClientReferenceId having a size more than maximum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to delete an existing household member with individualClientReferenceId being an empty string":0.001,"<b>SCENARIO : </b>Test to test household API CRUD operations":0.007,"<b>SCENARIO : </b>Test to create a household member with auth token of a distributor":0.013,"<b>SCENARIO : </b>Test to create a household with auth token of a registrar":0.001,"<b>SCENARIO : </b>Test to create a household with auth token of a distributor":0.001,"<b>SCENARIO : </b>Test to create a household with invalid tenantId":0,"<b>SCENARIO : </b>Test to create a household with a null tenantId":0,"<b>SCENARIO : </b>Test to create a household with empty string for tenantId":0.001,"<b>SCENARIO : </b>Test to create a household with clientReferenceId having a size less than minimum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to create a household with clientReferenceId having a size more than maximum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to create a household with memberCount being null":0.001,"<b>SCENARIO : </b>Test to create a household with memberCount having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to create a household with memberCount having a range more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to create a household with empty doorNo":0.001,"<b>SCENARIO : </b>Test to create a household with doorNo having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to create a household with doorNo having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to create a household with empty addressLine1":0,"<b>SCENARIO : </b>Test to create a household with addressLine1 having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to create a household with addressLine1 having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to create a household with empty addressLine2":0,"<b>SCENARIO : </b>Test to create a household with addressLine2 having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to create a household with addressLine2 having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to create a household with empty landmark":0.001,"<b>SCENARIO : </b>Test to create a household with landmark having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to create a household with landmark having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to create a household with empty pincode":0.001,"<b>SCENARIO : </b>Test to create a household with pincode having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to create a household with pincode having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to create a household with empty buildingName":0.001,"<b>SCENARIO : </b>Test to create a household with buildingName having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to create a household with buildingName having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to create a household with empty street":0.001,"<b>SCENARIO : </b>Test to create a household with street having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to create a household with street having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to search for a household without passing query parameters":0,"<b>SCENARIO : </b>Test to search for a household by passing only limit query parameter":0.002,"<b>SCENARIO : </b>Test to search for a household by passing only offset query parameter":0,"<b>SCENARIO : </b>Test to search for a household by passing only tenantId query parameter":0,"<b>SCENARIO : </b>Test to search for a household by passing only limit and offset query parameter":0.001,"<b>SCENARIO : </b>Test to search for a household by passing only tenantId and offset query parameter":0.001,"<b>SCENARIO : </b>Test to search for a household by passing only tenantId and limit query parameter":0.001,"<b>SCENARIO : </b>Test to search for a household using different criteria":0.006,"<b>SCENARIO : </b>Test to update an existing household with auth token of a distributor":0.001,"<b>SCENARIO : </b>Test to update an existing household by passing an empty id value for the household":0,"<b>SCENARIO : </b>Test to update an existing household by passing an id value for the household which is less than required minimum length":0,"<b>SCENARIO : </b>Test to update an existing household by passing an id value for the household which is more than alowed maximum length":0.001,"<b>SCENARIO : </b>Test to update an existing household by passing a null value for id":0.001,"<b>SCENARIO : </b>Test to update an existing household by passing a null value for hcmTenantId":0,"<b>SCENARIO : </b>Test to update an existing household by passing an clientReferenceId value for the household which is less than required minimum length":0,"<b>SCENARIO : </b>Test to update an existing household by passing an clientReferenceId value for the household which is more than allowed maximum length":0,"<b>SCENARIO : </b>Test to update an existing household by passing an empty value for clientReferenceId":0,"<b>SCENARIO : </b>Test to update an existing household by passing an clientReferenceId value for the address of the household which is less than required minimum length":0.001,"<b>SCENARIO : </b>Test to update an existing household by passing an clientReferenceId value for the household which is more than allowed maximum length":0.001,"<b>SCENARIO : </b>Test to update an existing household by passing an empty value for clientReferenceId":0.001,"<b>SCENARIO : </b>Test to update an existing household by passing a null value for address object tenantid":0.001,"<b>SCENARIO : </b>Test to update an existing household with empty doorNo":0.001,"<b>SCENARIO : </b>Test to update an existing household with doorNo having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing household with doorNo having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing household with empty addressLine1":0.001,"<b>SCENARIO : </b>Test to update an existing household with addressLine1 having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing household with addressLine1 having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing household with empty addressLine2":0,"<b>SCENARIO : </b>Test to update an existing household with addressLine2 having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing household with addressLine2 having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing household with empty landmark":0.001,"<b>SCENARIO : </b>Test to update an existing household with landmark having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing household with landmark having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing household with empty pincode":0,"<b>SCENARIO : </b>Test to update an existing household with pincode having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing household with pincode having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing household with empty buildingName":0.001,"<b>SCENARIO : </b>Test to update an existing household with buildingName having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing household with buildingName having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing household with empty street":0.001,"<b>SCENARIO : </b>Test to update an existing household with street having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing household with street having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to delete an existing household with auth token of a distributor":0.002,"<b>SCENARIO : </b>Test to delete an existing household by passing an empty id value for the household":0,"<b>SCENARIO : </b>Test to delete an existing household by passing an id value for the household which is less than required minimum length":0,"<b>SCENARIO : </b>Test to delete an existing household by passing an id value for the household which is more than alowed maximum length":0.001,"<b>SCENARIO : </b>Test to delete an existing household by passing a null value for id":0,"<b>SCENARIO : </b>Test to delete an existing household by passing a null value for hcmTenantId":0.001,"<b>SCENARIO : </b>Test to delete an existing household by passing an clientReferenceId value for the household which is less than required minimum length":0.001,"<b>SCENARIO : </b>Test to delete an existing household by passing an clientReferenceId value for the household which is more than allowed maximum length":0.002,"<b>SCENARIO : </b>Test to delete an existing household by passing an empty value for clientReferenceId":0,"<b>SCENARIO : </b>Test to delete an existing household by passing an clientReferenceId value for the address of the household which is less than required minimum length":0.001,"<b>SCENARIO : </b>Test to delete an existing household by passing an clientReferenceId value for the household which is more than allowed maximum length":0,"<b>SCENARIO : </b>Test to delete an existing household by passing an empty value for clientReferenceId":0.001,"<b>SCENARIO : </b>Test to delete an existing household by passing a null value for address object tenantid":0.001,"<b>SCENARIO : </b>Test to delete an existing household with empty doorNo":0.001,"<b>SCENARIO : </b>Test to delete an existing household with doorNo having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to delete an existing household with doorNo having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to delete an existing household with empty addressLine1":0.001,"<b>SCENARIO : </b>Test to delete an existing household with addressLine1 having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to delete an existing household with addressLine1 having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to delete an existing household with empty addressLine2":0.001,"<b>SCENARIO : </b>Test to delete an existing household with addressLine2 having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to delete an existing household with addressLine2 having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to delete an existing household with empty landmark":0,"<b>SCENARIO : </b>Test to delete an existing household with landmark having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to delete an existing household with landmark having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to delete an existing household with empty pincode":0,"<b>SCENARIO : </b>Test to delete an existing household with pincode having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to delete an existing household with pincode having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to delete an existing household with empty buildingName":0.001,"<b>SCENARIO : </b>Test to delete an existing household with buildingName having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to delete an existing household with buildingName having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to delete an existing household with empty street":0,"<b>SCENARIO : </b>Test to delete an existing household with street having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to delete an existing household with street having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to test household API CRUD operations":0.005,"<b>SCENARIO : </b>Test to create a household with auth token of a distributor":0.004,"<b>SCENARIO : </b>Test to create a product":0.001,"<b>SCENARIO : </b>Test to create a product with an unauthorised user":0,"<b>SCENARIO : </b>Test to create a product with an unauthorised user":0,"<b>SCENARIO : </b>Test to create a product with null product name":0,"<b>SCENARIO : </b>Test to create a product with null tenantId":0,"<b>SCENARIO : </b>Test to create a product with null type":0,"<b>SCENARIO : </b>Test to create a product with null apiOperation":0,"<b>SCENARIO : </b>Test to create a product with invalid tenantId":0,"<b>SCENARIO : </b>Test to create a product to verify the minimum value needed for the type":0.001,"<b>SCENARIO : </b>Test to create a product to verify the maximum value needed for the type":0,"<b>SCENARIO : </b>Test to create a product to verify the minimum value needed for the name":0.001,"<b>SCENARIO : </b>Test to create a product to verify the maximum value needed for the name":0,"<b>SCENARIO : </b>Test to create a product to verify the invalid value for apiOperation":0,"<b>SCENARIO : </b>Test to create a product to verify empty string value for apiOperation":0,"<b>SCENARIO : </b>Test to create an individual with auth token of a registrar":0.001,"<b>SCENARIO : </b>Test to create an individual with auth token of a distributor":0,"<b>SCENARIO : </b>Test to create an individual with null tenantId":0,"<b>SCENARIO : </b>Test to create an individual with empty string as tenantId":0.001,"<b>SCENARIO : </b>Test to create an individual with empty clientReferenceId":0,"<b>SCENARIO : </b>Test to create an individual with clientReferenceId having a size less than minimum allowed number of characters":0,"<b>SCENARIO : </b>Test to create an individual with clientReferenceId having a size less than maximum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to create an individual with empty givenName":0,"<b>SCENARIO : </b>Test to create an individual with givenName having a size less than minimum allowed number of characters":0,"<b>SCENARIO : </b>Test to create an individual with givenName having a size less than maximum allowed number of characters":0,"<b>SCENARIO : </b>Test to create an individual with empty familyName":0,"<b>SCENARIO : </b>Test to create an individual with familyName having a size less than minimum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to create an individual with givenName having a size less than maximum allowed number of characters":0.001,"<b>SCENARIO : </b>Test to create an individual with otherNames having a size less than maximum allowed number of characters":0,"<b>SCENARIO : </b>Test to search for an individual without passing query parameters":0.001,"<b>SCENARIO : </b>Test to search for an individual by passing only limit query parameter":0,"<b>SCENARIO : </b>Test to search for an individual by passing only offset query parameter":0,"<b>SCENARIO : </b>Test to search for an individual by passing only tenantId query parameter":0,"<b>SCENARIO : </b>Test to search for an individual by passing only limit and offset query parameter":0,"<b>SCENARIO : </b>Test to search for an individual by passing only tenantId and offset query parameter":0,"<b>SCENARIO : </b>Test to search for an individual by passing only tenantId and limit query parameter":0.001,"<b>SCENARIO : </b>Test to search for an individual using different criteria":0.012,"<b>SCENARIO : </b>Test to update an existing individual with auth token of a distributor":0.005,"<b>SCENARIO : </b>Test to update an existing individual by passing an empty id value for the individual":0,"<b>SCENARIO : </b>Test to update an existing individual by passing an id value for the individual which is less than required minimum length":0.001,"<b>SCENARIO : </b>Test to update an existing individual by passing an id value for the individual which is more than alowed maximum length":0.001,"<b>SCENARIO : </b>Test to update an existing individual by passing a null value for id":0,"<b>SCENARIO : </b>Test to update an existing individual by passing a null value for hcmTenantId":0.001,"<b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the individual which is less than required minimum length":0,"<b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the individual which is more than allowed maximum length":0,"<b>SCENARIO : </b>Test to update an existing individual by passing an empty value for clientReferenceId":0.001,"<b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the address of the individual which is less than required minimum length":0,"<b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the individual which is more than allowed maximum length":0,"<b>SCENARIO : </b>Test to update an existing individual by passing an empty value for clientReferenceId":0,"<b>SCENARIO : </b>Test to update an existing individual with empty doorNo":0.001,"<b>SCENARIO : </b>Test to update an existing individual with doorNo having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with doorNo having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with empty addressLine1":0.001,"<b>SCENARIO : </b>Test to update an existing individual with addressLine1 having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with addressLine1 having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with empty addressLine2":0.002,"<b>SCENARIO : </b>Test to update an existing individual with addressLine2 having a value less than minimum allowed number":0.007,"<b>SCENARIO : </b>Test to update an existing individual with addressLine2 having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with empty landmark":0,"<b>SCENARIO : </b>Test to update an existing individual with landmark having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with landmark having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with empty pincode":0.001,"<b>SCENARIO : </b>Test to update an existing individual with pincode having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with pincode having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with empty buildingName":0,"<b>SCENARIO : </b>Test to update an existing individual with buildingName having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with buildingName having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with empty street":0.001,"<b>SCENARIO : </b>Test to update an existing individual with street having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with street having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with empty givenName":0,"<b>SCENARIO : </b>Test to update an existing individual with givenName having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with givenName having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with empty familyName":0.001,"<b>SCENARIO : </b>Test to update an existing individual with familyName having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with familyName having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with mobileNumber having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with altContactNumber having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with empty email":0.001,"<b>SCENARIO : </b>Test to update an existing individual with email having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with email having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with auth token of a distributor":0.003,"<b>SCENARIO : </b>Test to update an existing individual by passing an empty id value for the individual":0.002,"<b>SCENARIO : </b>Test to update an existing individual by passing an id value for the individual which is less than required minimum length":0.001,"<b>SCENARIO : </b>Test to update an existing individual by passing an id value for the individual which is more than alowed maximum length":0,"<b>SCENARIO : </b>Test to update an existing individual by passing a null value for id":0,"<b>SCENARIO : </b>Test to update an existing individual by passing a null value for hcmTenantId":0,"<b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the individual which is less than required minimum length":0,"<b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the individual which is more than allowed maximum length":0.001,"<b>SCENARIO : </b>Test to update an existing individual by passing an empty value for clientReferenceId":0,"<b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the address of the individual which is less than required minimum length":0.001,"<b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the individual which is more than allowed maximum length":0.001,"<b>SCENARIO : </b>Test to update an existing individual by passing an empty value for clientReferenceId":0,"<b>SCENARIO : </b>Test to update an existing individual with empty doorNo":0,"<b>SCENARIO : </b>Test to update an existing individual with doorNo having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with doorNo having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with empty addressLine1":0,"<b>SCENARIO : </b>Test to update an existing individual with addressLine1 having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with addressLine1 having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with empty addressLine2":0.001,"<b>SCENARIO : </b>Test to update an existing individual with addressLine2 having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with addressLine2 having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with empty landmark":0,"<b>SCENARIO : </b>Test to update an existing individual with landmark having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with landmark having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with empty pincode":0.001,"<b>SCENARIO : </b>Test to update an existing individual with pincode having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with pincode having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with empty buildingName":0.004,"<b>SCENARIO : </b>Test to update an existing individual with buildingName having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with buildingName having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with empty street":0.001,"<b>SCENARIO : </b>Test to update an existing individual with street having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with street having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with empty givenName":0.001,"<b>SCENARIO : </b>Test to update an existing individual with givenName having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with givenName having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with empty familyName":0,"<b>SCENARIO : </b>Test to update an existing individual with familyName having a value less than minimum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with familyName having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with mobileNumber having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to update an existing individual with altContactNumber having a value more than maximum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with empty email":0.001,"<b>SCENARIO : </b>Test to update an existing individual with email having a value less than minimum allowed number":0,"<b>SCENARIO : </b>Test to update an existing individual with email having a value more than maximum allowed number":0.001,"<b>SCENARIO : </b>Test to test individual API CRUD operations":0.013,"<b>SCENARIO : </b>Test to create a individual with auth token of a distributor":0.016
};
</script>
<div class="row">
<div class="col-md-4 category-container">
<div class="card">
<div class="card-header"><p>Tags</p></div>
<div class="card-body pb-0 pt-0"><table class="table table-sm table-bordered">
<thead><tr class="bg-gray"><th>Name</th><th>Passed</th><th>Failed</th><th>Skipped</th><th>Others</th><th>Passed %</th></tr></thead><tbody>
<tr>
<td>HouseholdMemberServices-HCM</td>
<td>43</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>100%</td>
</tr>
<tr>
<td>IndividualServices-HCM</td>
<td>112</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>100%</td>
</tr>
<tr>
<td>HouseholdServices-HCM</td>
<td>109</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>100%</td>
</tr>
<tr>
<td>ProductServices-HCM</td>
<td>14</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>100%</td>
</tr>
</tbody>
</table></div>
</div>
</div>
<div class="col-md-4 sysenv-container">
<div class="card">
<div class="card-header"><p>System/Environment</p></div>
<div class="card-body pb-0 pt-0"><table class="table table-sm table-bordered">
<thead><tr class="bg-gray"><th>Name</th><th>Value</th></tr></thead>
<tbody>
<tr>
<td>Created By</td>
<td>eGov Automation</td>
</tr>
<tr>
<td>Autmation Type</td>
<td>Karate Framework</td>
</tr>
</tbody>
</table></div>
</div>
</div>
</div>
</div>
<script>
var statusGroup = {
parentCount: 5,
passParent: 278,
failParent: 0,
warningParent: 0,
skipParent: 0,
childCount: 5,
passChild: 556,
failChild: 0,
warningChild: 0,
skipChild: 0,
infoChild: 0,
grandChildCount: 5,
passGrandChild: 0,
failGrandChild: 0,
warningGrandChild: 0,
skipGrandChild: 0,
infoGrandChild: 0,
eventsCount: 5,
passEvents: 27765,
failEvents: 0,
warningEvents: 0,
skipEvents: 0,
infoEvents: 556
};
</script><div class="test-wrapper row view category-view attributes-view">
<div class="test-list">
<div class="test-list-tools">
<ul class="tools pull-left"><li><a href=""><span class="font-size-14">Category</span></a></li></ul>
<ul class="tools text-right"><li><a href="#"><span class="badge badge-primary">4</span></a></li></ul>
</div>
<div class="test-list-wrapper scrollable">
<ul class="test-list-item">
<li class="test-item">
<div class="test-detail">
<span class="meta">
<span class='badge log pass-bg'>43</span>
</span>
<p class="name">HouseholdMemberServices-HCM</p>
<p class="duration text-sm">43 tests</p>
</div>
<div class="test-contents d-none">
<div class="info">
<h4>HouseholdMemberServices-HCM</h4>
<span status="pass" class='badge log pass-bg'>43 passed</span>
</div>
<table class='table table-sm mt-4'>
<thead>
<tr>
<th class="status-col">Status</th>
<th class="timestamp-col">Timestamp</th>
<th>TestName</th>
</tr>
</thead>
<tbody>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:47 PM</td>
<td>
<a href="#" class="linked" test-id='1' id='1'><b>SCENARIO : </b>Test to create a household member with auth token of a registrar</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:49 PM</td>
<td>
<a href="#" class="linked" test-id='4' id='4'><b>SCENARIO : </b>Test to create a household with auth token of a distributor</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:50 PM</td>
<td>
<a href="#" class="linked" test-id='7' id='7'><b>SCENARIO : </b>Test to create a household member with invalid tenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:51 PM</td>
<td>
<a href="#" class="linked" test-id='10' id='10'><b>SCENARIO : </b>Test to create a household member with a null tenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:51 PM</td>
<td>
<a href="#" class="linked" test-id='13' id='13'><b>SCENARIO : </b>Test to create a household member with empty string for tenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:52 PM</td>
<td>
<a href="#" class="linked" test-id='16' id='16'><b>SCENARIO : </b>Test to create a household member with householdClientReferenceId having a size less than minimum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:53 PM</td>
<td>
<a href="#" class="linked" test-id='19' id='19'><b>SCENARIO : </b>Test to create a household member with householdClientReferenceId having a size more than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:53 PM</td>
<td>
<a href="#" class="linked" test-id='22' id='22'><b>SCENARIO : </b>Test to create a household member with householdClientReferenceId being an empty string</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:53 PM</td>
<td>
<a href="#" class="linked" test-id='25' id='25'><b>SCENARIO : </b>Test to create a household member with individualClientReferenceId having a size less than minimum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:54 PM</td>
<td>
<a href="#" class="linked" test-id='28' id='28'><b>SCENARIO : </b>Test to create a household member with individualClientReferenceId having a size more than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:54 PM</td>
<td>
<a href="#" class="linked" test-id='31' id='31'><b>SCENARIO : </b>Test to create a household member with individualClientReferenceId being an empty string</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:55 PM</td>
<td>
<a href="#" class="linked" test-id='34' id='34'><b>SCENARIO : </b>Test to search for a household member without passing query parameters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:55 PM</td>
<td>
<a href="#" class="linked" test-id='37' id='37'><b>SCENARIO : </b>Test to search for a household member by passing only limit query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:56 PM</td>
<td>
<a href="#" class="linked" test-id='40' id='40'><b>SCENARIO : </b>Test to search for a household member by passing only offset query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:56 PM</td>
<td>
<a href="#" class="linked" test-id='43' id='43'><b>SCENARIO : </b>Test to search for a household member by passing only tenantId query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:57 PM</td>
<td>
<a href="#" class="linked" test-id='46' id='46'><b>SCENARIO : </b>Test to search for a household member by passing only limit and offset query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:57 PM</td>
<td>
<a href="#" class="linked" test-id='49' id='49'><b>SCENARIO : </b>Test to search for a household member by passing only tenantId and offset query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:16:58 PM</td>
<td>
<a href="#" class="linked" test-id='52' id='52'><b>SCENARIO : </b>Test to search for a household member by passing only tenantId and limit query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:00 PM</td>
<td>
<a href="#" class="linked" test-id='55' id='55'><b>SCENARIO : </b>Test to search for a household member using different criteria</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:02 PM</td>
<td>
<a href="#" class="linked" test-id='58' id='58'><b>SCENARIO : </b>Test to update an existing household member with auth token of a distributor</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:03 PM</td>
<td>
<a href="#" class="linked" test-id='61' id='61'><b>SCENARIO : </b>Test to update an existing household member with id being an empty string</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:03 PM</td>
<td>
<a href="#" class="linked" test-id='64' id='64'><b>SCENARIO : </b>Test to update an existing household member with id having a size less than minimum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:04 PM</td>
<td>
<a href="#" class="linked" test-id='67' id='67'><b>SCENARIO : </b>Test to update an existing household member with id having a size more than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:04 PM</td>
<td>
<a href="#" class="linked" test-id='70' id='70'><b>SCENARIO : </b>Test to update an existing household member with a null tenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:04 PM</td>
<td>
<a href="#" class="linked" test-id='73' id='73'><b>SCENARIO : </b>Test to update an existing household member with householdClientReferenceId having a size less than minimum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:05 PM</td>
<td>
<a href="#" class="linked" test-id='76' id='76'><b>SCENARIO : </b>Test to update an existing household member with householdClientReferenceId having a size more than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:05 PM</td>
<td>
<a href="#" class="linked" test-id='79' id='79'><b>SCENARIO : </b>Test to update an existing household member with householdClientReferenceId being an empty string</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:06 PM</td>
<td>
<a href="#" class="linked" test-id='82' id='82'><b>SCENARIO : </b>Test to update an existing household member with individualClientReferenceId having a size less than minimum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:06 PM</td>
<td>
<a href="#" class="linked" test-id='85' id='85'><b>SCENARIO : </b>Test to update an existing household member with individualClientReferenceId having a size more than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:07 PM</td>
<td>
<a href="#" class="linked" test-id='88' id='88'><b>SCENARIO : </b>Test to update an existing household member with individualClientReferenceId being an empty string</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:10 PM</td>
<td>
<a href="#" class="linked" test-id='91' id='91'><b>SCENARIO : </b>Test to delete an existing household member with auth token of a distributor</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:10 PM</td>
<td>
<a href="#" class="linked" test-id='94' id='94'><b>SCENARIO : </b>Test to delete an existing household member with id being an empty string</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:11 PM</td>
<td>
<a href="#" class="linked" test-id='97' id='97'><b>SCENARIO : </b>Test to delete an existing household member with id having a size less than minimum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:11 PM</td>
<td>
<a href="#" class="linked" test-id='100' id='100'><b>SCENARIO : </b>Test to delete an existing household member with id having a size more than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:11 PM</td>
<td>
<a href="#" class="linked" test-id='103' id='103'><b>SCENARIO : </b>Test to delete an existing household member with a null tenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:12 PM</td>
<td>
<a href="#" class="linked" test-id='106' id='106'><b>SCENARIO : </b>Test to delete an existing household member with householdClientReferenceId having a size less than minimum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:12 PM</td>
<td>
<a href="#" class="linked" test-id='109' id='109'><b>SCENARIO : </b>Test to delete an existing household member with householdClientReferenceId having a size more than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:13 PM</td>
<td>
<a href="#" class="linked" test-id='112' id='112'><b>SCENARIO : </b>Test to delete an existing household member with householdClientReferenceId being an empty string</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:13 PM</td>
<td>
<a href="#" class="linked" test-id='115' id='115'><b>SCENARIO : </b>Test to delete an existing household member with individualClientReferenceId having a size less than minimum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:13 PM</td>
<td>
<a href="#" class="linked" test-id='118' id='118'><b>SCENARIO : </b>Test to delete an existing household member with individualClientReferenceId having a size more than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:14 PM</td>
<td>
<a href="#" class="linked" test-id='121' id='121'><b>SCENARIO : </b>Test to delete an existing household member with individualClientReferenceId being an empty string</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:16 PM</td>
<td>
<a href="#" class="linked" test-id='124' id='124'><b>SCENARIO : </b>Test to test household API CRUD operations</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:21 PM</td>
<td>
<a href="#" class="linked" test-id='127' id='127'><b>SCENARIO : </b>Test to create a household member with auth token of a distributor</a>
</td>
</tr>
</tbody>
</table>
</div>
</li>
<li class="test-item">
<div class="test-detail">
<span class="meta">
<span class='badge log pass-bg'>112</span>
</span>
<p class="name">IndividualServices-HCM</p>
<p class="duration text-sm">112 tests</p>
</div>
<div class="test-contents d-none">
<div class="info">
<h4>IndividualServices-HCM</h4>
<span status="pass" class='badge log pass-bg'>112 passed</span>
</div>
<table class='table table-sm mt-4'>
<thead>
<tr>
<th class="status-col">Status</th>
<th class="timestamp-col">Timestamp</th>
<th>TestName</th>
</tr>
</thead>
<tbody>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:31 PM</td>
<td>
<a href="#" class="linked" test-id='499' id='499'><b>SCENARIO : </b>Test to create an individual with auth token of a registrar</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:32 PM</td>
<td>
<a href="#" class="linked" test-id='502' id='502'><b>SCENARIO : </b>Test to create an individual with auth token of a distributor</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:32 PM</td>
<td>
<a href="#" class="linked" test-id='505' id='505'><b>SCENARIO : </b>Test to create an individual with null tenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:33 PM</td>
<td>
<a href="#" class="linked" test-id='508' id='508'><b>SCENARIO : </b>Test to create an individual with empty string as tenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:33 PM</td>
<td>
<a href="#" class="linked" test-id='511' id='511'><b>SCENARIO : </b>Test to create an individual with empty clientReferenceId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:34 PM</td>
<td>
<a href="#" class="linked" test-id='514' id='514'><b>SCENARIO : </b>Test to create an individual with clientReferenceId having a size less than minimum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:34 PM</td>
<td>
<a href="#" class="linked" test-id='517' id='517'><b>SCENARIO : </b>Test to create an individual with clientReferenceId having a size less than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:35 PM</td>
<td>
<a href="#" class="linked" test-id='520' id='520'><b>SCENARIO : </b>Test to create an individual with empty givenName</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:35 PM</td>
<td>
<a href="#" class="linked" test-id='523' id='523'><b>SCENARIO : </b>Test to create an individual with givenName having a size less than minimum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:36 PM</td>
<td>
<a href="#" class="linked" test-id='526' id='526'><b>SCENARIO : </b>Test to create an individual with givenName having a size less than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:36 PM</td>
<td>
<a href="#" class="linked" test-id='529' id='529'><b>SCENARIO : </b>Test to create an individual with empty familyName</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:37 PM</td>
<td>
<a href="#" class="linked" test-id='532' id='532'><b>SCENARIO : </b>Test to create an individual with familyName having a size less than minimum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:38 PM</td>
<td>
<a href="#" class="linked" test-id='535' id='535'><b>SCENARIO : </b>Test to create an individual with givenName having a size less than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:38 PM</td>
<td>
<a href="#" class="linked" test-id='538' id='538'><b>SCENARIO : </b>Test to create an individual with otherNames having a size less than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:39 PM</td>
<td>
<a href="#" class="linked" test-id='541' id='541'><b>SCENARIO : </b>Test to search for an individual without passing query parameters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:40 PM</td>
<td>
<a href="#" class="linked" test-id='544' id='544'><b>SCENARIO : </b>Test to search for an individual by passing only limit query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:41 PM</td>
<td>
<a href="#" class="linked" test-id='547' id='547'><b>SCENARIO : </b>Test to search for an individual by passing only offset query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:41 PM</td>
<td>
<a href="#" class="linked" test-id='550' id='550'><b>SCENARIO : </b>Test to search for an individual by passing only tenantId query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:42 PM</td>
<td>
<a href="#" class="linked" test-id='553' id='553'><b>SCENARIO : </b>Test to search for an individual by passing only limit and offset query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:43 PM</td>
<td>
<a href="#" class="linked" test-id='556' id='556'><b>SCENARIO : </b>Test to search for an individual by passing only tenantId and offset query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:44 PM</td>
<td>
<a href="#" class="linked" test-id='559' id='559'><b>SCENARIO : </b>Test to search for an individual by passing only tenantId and limit query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:49 PM</td>
<td>
<a href="#" class="linked" test-id='562' id='562'><b>SCENARIO : </b>Test to search for an individual using different criteria</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:51 PM</td>
<td>
<a href="#" class="linked" test-id='565' id='565'><b>SCENARIO : </b>Test to update an existing individual with auth token of a distributor</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:52 PM</td>
<td>
<a href="#" class="linked" test-id='568' id='568'><b>SCENARIO : </b>Test to update an existing individual by passing an empty id value for the individual</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:53 PM</td>
<td>
<a href="#" class="linked" test-id='571' id='571'><b>SCENARIO : </b>Test to update an existing individual by passing an id value for the individual which is less than required minimum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:53 PM</td>
<td>
<a href="#" class="linked" test-id='574' id='574'><b>SCENARIO : </b>Test to update an existing individual by passing an id value for the individual which is more than alowed maximum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:54 PM</td>
<td>
<a href="#" class="linked" test-id='577' id='577'><b>SCENARIO : </b>Test to update an existing individual by passing a null value for id</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:55 PM</td>
<td>
<a href="#" class="linked" test-id='580' id='580'><b>SCENARIO : </b>Test to update an existing individual by passing a null value for hcmTenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:55 PM</td>
<td>
<a href="#" class="linked" test-id='583' id='583'><b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the individual which is less than required minimum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:56 PM</td>
<td>
<a href="#" class="linked" test-id='586' id='586'><b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the individual which is more than allowed maximum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:57 PM</td>
<td>
<a href="#" class="linked" test-id='589' id='589'><b>SCENARIO : </b>Test to update an existing individual by passing an empty value for clientReferenceId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:58 PM</td>
<td>
<a href="#" class="linked" test-id='592' id='592'><b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the address of the individual which is less than required minimum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:58 PM</td>
<td>
<a href="#" class="linked" test-id='595' id='595'><b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the individual which is more than allowed maximum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:59 PM</td>
<td>
<a href="#" class="linked" test-id='598' id='598'><b>SCENARIO : </b>Test to update an existing individual by passing an empty value for clientReferenceId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:00 PM</td>
<td>
<a href="#" class="linked" test-id='601' id='601'><b>SCENARIO : </b>Test to update an existing individual with empty doorNo</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:01 PM</td>
<td>
<a href="#" class="linked" test-id='604' id='604'><b>SCENARIO : </b>Test to update an existing individual with doorNo having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:01 PM</td>
<td>
<a href="#" class="linked" test-id='607' id='607'><b>SCENARIO : </b>Test to update an existing individual with doorNo having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:02 PM</td>
<td>
<a href="#" class="linked" test-id='610' id='610'><b>SCENARIO : </b>Test to update an existing individual with empty addressLine1</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:03 PM</td>
<td>
<a href="#" class="linked" test-id='613' id='613'><b>SCENARIO : </b>Test to update an existing individual with addressLine1 having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:04 PM</td>
<td>
<a href="#" class="linked" test-id='616' id='616'><b>SCENARIO : </b>Test to update an existing individual with addressLine1 having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:04 PM</td>
<td>
<a href="#" class="linked" test-id='619' id='619'><b>SCENARIO : </b>Test to update an existing individual with empty addressLine2</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:05 PM</td>
<td>
<a href="#" class="linked" test-id='622' id='622'><b>SCENARIO : </b>Test to update an existing individual with addressLine2 having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:06 PM</td>
<td>
<a href="#" class="linked" test-id='625' id='625'><b>SCENARIO : </b>Test to update an existing individual with addressLine2 having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:07 PM</td>
<td>
<a href="#" class="linked" test-id='628' id='628'><b>SCENARIO : </b>Test to update an existing individual with empty landmark</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:07 PM</td>
<td>
<a href="#" class="linked" test-id='631' id='631'><b>SCENARIO : </b>Test to update an existing individual with landmark having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:08 PM</td>
<td>
<a href="#" class="linked" test-id='634' id='634'><b>SCENARIO : </b>Test to update an existing individual with landmark having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:09 PM</td>
<td>
<a href="#" class="linked" test-id='637' id='637'><b>SCENARIO : </b>Test to update an existing individual with empty pincode</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:10 PM</td>
<td>
<a href="#" class="linked" test-id='640' id='640'><b>SCENARIO : </b>Test to update an existing individual with pincode having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:11 PM</td>
<td>
<a href="#" class="linked" test-id='643' id='643'><b>SCENARIO : </b>Test to update an existing individual with pincode having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:12 PM</td>
<td>
<a href="#" class="linked" test-id='646' id='646'><b>SCENARIO : </b>Test to update an existing individual with empty buildingName</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:13 PM</td>
<td>
<a href="#" class="linked" test-id='649' id='649'><b>SCENARIO : </b>Test to update an existing individual with buildingName having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:13 PM</td>
<td>
<a href="#" class="linked" test-id='652' id='652'><b>SCENARIO : </b>Test to update an existing individual with buildingName having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:14 PM</td>
<td>
<a href="#" class="linked" test-id='655' id='655'><b>SCENARIO : </b>Test to update an existing individual with empty street</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:15 PM</td>
<td>
<a href="#" class="linked" test-id='658' id='658'><b>SCENARIO : </b>Test to update an existing individual with street having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:16 PM</td>
<td>
<a href="#" class="linked" test-id='661' id='661'><b>SCENARIO : </b>Test to update an existing individual with street having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:17 PM</td>
<td>
<a href="#" class="linked" test-id='664' id='664'><b>SCENARIO : </b>Test to update an existing individual with empty givenName</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:18 PM</td>
<td>
<a href="#" class="linked" test-id='667' id='667'><b>SCENARIO : </b>Test to update an existing individual with givenName having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:19 PM</td>
<td>
<a href="#" class="linked" test-id='670' id='670'><b>SCENARIO : </b>Test to update an existing individual with givenName having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:21 PM</td>
<td>
<a href="#" class="linked" test-id='673' id='673'><b>SCENARIO : </b>Test to update an existing individual with empty familyName</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:21 PM</td>
<td>
<a href="#" class="linked" test-id='676' id='676'><b>SCENARIO : </b>Test to update an existing individual with familyName having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:22 PM</td>
<td>
<a href="#" class="linked" test-id='679' id='679'><b>SCENARIO : </b>Test to update an existing individual with familyName having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:24 PM</td>
<td>
<a href="#" class="linked" test-id='682' id='682'><b>SCENARIO : </b>Test to update an existing individual with mobileNumber having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:24 PM</td>
<td>
<a href="#" class="linked" test-id='685' id='685'><b>SCENARIO : </b>Test to update an existing individual with altContactNumber having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:25 PM</td>
<td>
<a href="#" class="linked" test-id='688' id='688'><b>SCENARIO : </b>Test to update an existing individual with empty email</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:25 PM</td>
<td>
<a href="#" class="linked" test-id='691' id='691'><b>SCENARIO : </b>Test to update an existing individual with email having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:26 PM</td>
<td>
<a href="#" class="linked" test-id='694' id='694'><b>SCENARIO : </b>Test to update an existing individual with email having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:28 PM</td>
<td>
<a href="#" class="linked" test-id='697' id='697'><b>SCENARIO : </b>Test to update an existing individual with auth token of a distributor</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:29 PM</td>
<td>
<a href="#" class="linked" test-id='700' id='700'><b>SCENARIO : </b>Test to update an existing individual by passing an empty id value for the individual</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:29 PM</td>
<td>
<a href="#" class="linked" test-id='703' id='703'><b>SCENARIO : </b>Test to update an existing individual by passing an id value for the individual which is less than required minimum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:30 PM</td>
<td>
<a href="#" class="linked" test-id='706' id='706'><b>SCENARIO : </b>Test to update an existing individual by passing an id value for the individual which is more than alowed maximum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:31 PM</td>
<td>
<a href="#" class="linked" test-id='709' id='709'><b>SCENARIO : </b>Test to update an existing individual by passing a null value for id</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:31 PM</td>
<td>
<a href="#" class="linked" test-id='712' id='712'><b>SCENARIO : </b>Test to update an existing individual by passing a null value for hcmTenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:32 PM</td>
<td>
<a href="#" class="linked" test-id='715' id='715'><b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the individual which is less than required minimum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:33 PM</td>
<td>
<a href="#" class="linked" test-id='718' id='718'><b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the individual which is more than allowed maximum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:34 PM</td>
<td>
<a href="#" class="linked" test-id='721' id='721'><b>SCENARIO : </b>Test to update an existing individual by passing an empty value for clientReferenceId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:34 PM</td>
<td>
<a href="#" class="linked" test-id='724' id='724'><b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the address of the individual which is less than required minimum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:35 PM</td>
<td>
<a href="#" class="linked" test-id='727' id='727'><b>SCENARIO : </b>Test to update an existing individual by passing an clientReferenceId value for the individual which is more than allowed maximum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:36 PM</td>
<td>
<a href="#" class="linked" test-id='730' id='730'><b>SCENARIO : </b>Test to update an existing individual by passing an empty value for clientReferenceId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:36 PM</td>
<td>
<a href="#" class="linked" test-id='733' id='733'><b>SCENARIO : </b>Test to update an existing individual with empty doorNo</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:37 PM</td>
<td>
<a href="#" class="linked" test-id='736' id='736'><b>SCENARIO : </b>Test to update an existing individual with doorNo having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:38 PM</td>
<td>
<a href="#" class="linked" test-id='739' id='739'><b>SCENARIO : </b>Test to update an existing individual with doorNo having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:39 PM</td>
<td>
<a href="#" class="linked" test-id='742' id='742'><b>SCENARIO : </b>Test to update an existing individual with empty addressLine1</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:39 PM</td>
<td>
<a href="#" class="linked" test-id='745' id='745'><b>SCENARIO : </b>Test to update an existing individual with addressLine1 having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:40 PM</td>
<td>
<a href="#" class="linked" test-id='748' id='748'><b>SCENARIO : </b>Test to update an existing individual with addressLine1 having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:41 PM</td>
<td>
<a href="#" class="linked" test-id='751' id='751'><b>SCENARIO : </b>Test to update an existing individual with empty addressLine2</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:41 PM</td>
<td>
<a href="#" class="linked" test-id='754' id='754'><b>SCENARIO : </b>Test to update an existing individual with addressLine2 having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:43 PM</td>
<td>
<a href="#" class="linked" test-id='757' id='757'><b>SCENARIO : </b>Test to update an existing individual with addressLine2 having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:44 PM</td>
<td>
<a href="#" class="linked" test-id='760' id='760'><b>SCENARIO : </b>Test to update an existing individual with empty landmark</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:44 PM</td>
<td>
<a href="#" class="linked" test-id='763' id='763'><b>SCENARIO : </b>Test to update an existing individual with landmark having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:45 PM</td>
<td>
<a href="#" class="linked" test-id='766' id='766'><b>SCENARIO : </b>Test to update an existing individual with landmark having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:46 PM</td>
<td>
<a href="#" class="linked" test-id='769' id='769'><b>SCENARIO : </b>Test to update an existing individual with empty pincode</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:47 PM</td>
<td>
<a href="#" class="linked" test-id='772' id='772'><b>SCENARIO : </b>Test to update an existing individual with pincode having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:48 PM</td>
<td>
<a href="#" class="linked" test-id='775' id='775'><b>SCENARIO : </b>Test to update an existing individual with pincode having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:49 PM</td>
<td>
<a href="#" class="linked" test-id='778' id='778'><b>SCENARIO : </b>Test to update an existing individual with empty buildingName</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:50 PM</td>
<td>
<a href="#" class="linked" test-id='781' id='781'><b>SCENARIO : </b>Test to update an existing individual with buildingName having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:51 PM</td>
<td>
<a href="#" class="linked" test-id='784' id='784'><b>SCENARIO : </b>Test to update an existing individual with buildingName having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:52 PM</td>
<td>
<a href="#" class="linked" test-id='787' id='787'><b>SCENARIO : </b>Test to update an existing individual with empty street</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:53 PM</td>
<td>
<a href="#" class="linked" test-id='790' id='790'><b>SCENARIO : </b>Test to update an existing individual with street having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:54 PM</td>
<td>
<a href="#" class="linked" test-id='793' id='793'><b>SCENARIO : </b>Test to update an existing individual with street having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:55 PM</td>
<td>
<a href="#" class="linked" test-id='796' id='796'><b>SCENARIO : </b>Test to update an existing individual with empty givenName</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:56 PM</td>
<td>
<a href="#" class="linked" test-id='799' id='799'><b>SCENARIO : </b>Test to update an existing individual with givenName having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:58 PM</td>
<td>
<a href="#" class="linked" test-id='802' id='802'><b>SCENARIO : </b>Test to update an existing individual with givenName having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:19:59 PM</td>
<td>
<a href="#" class="linked" test-id='805' id='805'><b>SCENARIO : </b>Test to update an existing individual with empty familyName</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:20:00 PM</td>
<td>
<a href="#" class="linked" test-id='808' id='808'><b>SCENARIO : </b>Test to update an existing individual with familyName having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:20:01 PM</td>
<td>
<a href="#" class="linked" test-id='811' id='811'><b>SCENARIO : </b>Test to update an existing individual with familyName having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:20:01 PM</td>
<td>
<a href="#" class="linked" test-id='814' id='814'><b>SCENARIO : </b>Test to update an existing individual with mobileNumber having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:20:02 PM</td>
<td>
<a href="#" class="linked" test-id='817' id='817'><b>SCENARIO : </b>Test to update an existing individual with altContactNumber having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:20:03 PM</td>
<td>
<a href="#" class="linked" test-id='820' id='820'><b>SCENARIO : </b>Test to update an existing individual with empty email</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:20:03 PM</td>
<td>
<a href="#" class="linked" test-id='823' id='823'><b>SCENARIO : </b>Test to update an existing individual with email having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:20:04 PM</td>
<td>
<a href="#" class="linked" test-id='826' id='826'><b>SCENARIO : </b>Test to update an existing individual with email having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:20:09 PM</td>
<td>
<a href="#" class="linked" test-id='829' id='829'><b>SCENARIO : </b>Test to test individual API CRUD operations</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:20:13 PM</td>
<td>
<a href="#" class="linked" test-id='832' id='832'><b>SCENARIO : </b>Test to create a individual with auth token of a distributor</a>
</td>
</tr>
</tbody>
</table>
</div>
</li>
<li class="test-item">
<div class="test-detail">
<span class="meta">
<span class='badge log pass-bg'>109</span>
</span>
<p class="name">HouseholdServices-HCM</p>
<p class="duration text-sm">109 tests</p>
</div>
<div class="test-contents d-none">
<div class="info">
<h4>HouseholdServices-HCM</h4>
<span status="pass" class='badge log pass-bg'>109 passed</span>
</div>
<table class='table table-sm mt-4'>
<thead>
<tr>
<th class="status-col">Status</th>
<th class="timestamp-col">Timestamp</th>
<th>TestName</th>
</tr>
</thead>
<tbody>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:21 PM</td>
<td>
<a href="#" class="linked" test-id='130' id='130'><b>SCENARIO : </b>Test to create a household with auth token of a registrar</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:22 PM</td>
<td>
<a href="#" class="linked" test-id='133' id='133'><b>SCENARIO : </b>Test to create a household with auth token of a distributor</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:23 PM</td>
<td>
<a href="#" class="linked" test-id='136' id='136'><b>SCENARIO : </b>Test to create a household with invalid tenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:23 PM</td>
<td>
<a href="#" class="linked" test-id='139' id='139'><b>SCENARIO : </b>Test to create a household with a null tenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:24 PM</td>
<td>
<a href="#" class="linked" test-id='142' id='142'><b>SCENARIO : </b>Test to create a household with empty string for tenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:24 PM</td>
<td>
<a href="#" class="linked" test-id='145' id='145'><b>SCENARIO : </b>Test to create a household with clientReferenceId having a size less than minimum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:25 PM</td>
<td>
<a href="#" class="linked" test-id='148' id='148'><b>SCENARIO : </b>Test to create a household with clientReferenceId having a size more than maximum allowed number of characters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:25 PM</td>
<td>
<a href="#" class="linked" test-id='151' id='151'><b>SCENARIO : </b>Test to create a household with memberCount being null</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:26 PM</td>
<td>
<a href="#" class="linked" test-id='154' id='154'><b>SCENARIO : </b>Test to create a household with memberCount having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:26 PM</td>
<td>
<a href="#" class="linked" test-id='157' id='157'><b>SCENARIO : </b>Test to create a household with memberCount having a range more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:27 PM</td>
<td>
<a href="#" class="linked" test-id='160' id='160'><b>SCENARIO : </b>Test to create a household with empty doorNo</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:27 PM</td>
<td>
<a href="#" class="linked" test-id='163' id='163'><b>SCENARIO : </b>Test to create a household with doorNo having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:28 PM</td>
<td>
<a href="#" class="linked" test-id='166' id='166'><b>SCENARIO : </b>Test to create a household with doorNo having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:28 PM</td>
<td>
<a href="#" class="linked" test-id='169' id='169'><b>SCENARIO : </b>Test to create a household with empty addressLine1</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:29 PM</td>
<td>
<a href="#" class="linked" test-id='172' id='172'><b>SCENARIO : </b>Test to create a household with addressLine1 having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:29 PM</td>
<td>
<a href="#" class="linked" test-id='175' id='175'><b>SCENARIO : </b>Test to create a household with addressLine1 having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:30 PM</td>
<td>
<a href="#" class="linked" test-id='178' id='178'><b>SCENARIO : </b>Test to create a household with empty addressLine2</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:31 PM</td>
<td>
<a href="#" class="linked" test-id='181' id='181'><b>SCENARIO : </b>Test to create a household with addressLine2 having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:31 PM</td>
<td>
<a href="#" class="linked" test-id='184' id='184'><b>SCENARIO : </b>Test to create a household with addressLine2 having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:32 PM</td>
<td>
<a href="#" class="linked" test-id='187' id='187'><b>SCENARIO : </b>Test to create a household with empty landmark</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:32 PM</td>
<td>
<a href="#" class="linked" test-id='190' id='190'><b>SCENARIO : </b>Test to create a household with landmark having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:33 PM</td>
<td>
<a href="#" class="linked" test-id='193' id='193'><b>SCENARIO : </b>Test to create a household with landmark having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:33 PM</td>
<td>
<a href="#" class="linked" test-id='196' id='196'><b>SCENARIO : </b>Test to create a household with empty pincode</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:34 PM</td>
<td>
<a href="#" class="linked" test-id='199' id='199'><b>SCENARIO : </b>Test to create a household with pincode having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:35 PM</td>
<td>
<a href="#" class="linked" test-id='202' id='202'><b>SCENARIO : </b>Test to create a household with pincode having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:35 PM</td>
<td>
<a href="#" class="linked" test-id='205' id='205'><b>SCENARIO : </b>Test to create a household with empty buildingName</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:36 PM</td>
<td>
<a href="#" class="linked" test-id='208' id='208'><b>SCENARIO : </b>Test to create a household with buildingName having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:36 PM</td>
<td>
<a href="#" class="linked" test-id='211' id='211'><b>SCENARIO : </b>Test to create a household with buildingName having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:37 PM</td>
<td>
<a href="#" class="linked" test-id='214' id='214'><b>SCENARIO : </b>Test to create a household with empty street</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:37 PM</td>
<td>
<a href="#" class="linked" test-id='217' id='217'><b>SCENARIO : </b>Test to create a household with street having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:37 PM</td>
<td>
<a href="#" class="linked" test-id='220' id='220'><b>SCENARIO : </b>Test to create a household with street having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:38 PM</td>
<td>
<a href="#" class="linked" test-id='223' id='223'><b>SCENARIO : </b>Test to search for a household without passing query parameters</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:39 PM</td>
<td>
<a href="#" class="linked" test-id='226' id='226'><b>SCENARIO : </b>Test to search for a household by passing only limit query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:39 PM</td>
<td>
<a href="#" class="linked" test-id='229' id='229'><b>SCENARIO : </b>Test to search for a household by passing only offset query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:40 PM</td>
<td>
<a href="#" class="linked" test-id='232' id='232'><b>SCENARIO : </b>Test to search for a household by passing only tenantId query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:40 PM</td>
<td>
<a href="#" class="linked" test-id='235' id='235'><b>SCENARIO : </b>Test to search for a household by passing only limit and offset query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:40 PM</td>
<td>
<a href="#" class="linked" test-id='238' id='238'><b>SCENARIO : </b>Test to search for a household by passing only tenantId and offset query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:41 PM</td>
<td>
<a href="#" class="linked" test-id='241' id='241'><b>SCENARIO : </b>Test to search for a household by passing only tenantId and limit query parameter</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:43 PM</td>
<td>
<a href="#" class="linked" test-id='244' id='244'><b>SCENARIO : </b>Test to search for a household using different criteria</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:45 PM</td>
<td>
<a href="#" class="linked" test-id='247' id='247'><b>SCENARIO : </b>Test to update an existing household with auth token of a distributor</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:45 PM</td>
<td>
<a href="#" class="linked" test-id='250' id='250'><b>SCENARIO : </b>Test to update an existing household by passing an empty id value for the household</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:46 PM</td>
<td>
<a href="#" class="linked" test-id='253' id='253'><b>SCENARIO : </b>Test to update an existing household by passing an id value for the household which is less than required minimum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:46 PM</td>
<td>
<a href="#" class="linked" test-id='256' id='256'><b>SCENARIO : </b>Test to update an existing household by passing an id value for the household which is more than alowed maximum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:47 PM</td>
<td>
<a href="#" class="linked" test-id='259' id='259'><b>SCENARIO : </b>Test to update an existing household by passing a null value for id</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:47 PM</td>
<td>
<a href="#" class="linked" test-id='262' id='262'><b>SCENARIO : </b>Test to update an existing household by passing a null value for hcmTenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:48 PM</td>
<td>
<a href="#" class="linked" test-id='265' id='265'><b>SCENARIO : </b>Test to update an existing household by passing an clientReferenceId value for the household which is less than required minimum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:48 PM</td>
<td>
<a href="#" class="linked" test-id='268' id='268'><b>SCENARIO : </b>Test to update an existing household by passing an clientReferenceId value for the household which is more than allowed maximum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:49 PM</td>
<td>
<a href="#" class="linked" test-id='271' id='271'><b>SCENARIO : </b>Test to update an existing household by passing an empty value for clientReferenceId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:49 PM</td>
<td>
<a href="#" class="linked" test-id='274' id='274'><b>SCENARIO : </b>Test to update an existing household by passing an clientReferenceId value for the address of the household which is less than required minimum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:50 PM</td>
<td>
<a href="#" class="linked" test-id='277' id='277'><b>SCENARIO : </b>Test to update an existing household by passing an clientReferenceId value for the household which is more than allowed maximum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:50 PM</td>
<td>
<a href="#" class="linked" test-id='280' id='280'><b>SCENARIO : </b>Test to update an existing household by passing an empty value for clientReferenceId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:51 PM</td>
<td>
<a href="#" class="linked" test-id='283' id='283'><b>SCENARIO : </b>Test to update an existing household by passing a null value for address object tenantid</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:51 PM</td>
<td>
<a href="#" class="linked" test-id='286' id='286'><b>SCENARIO : </b>Test to update an existing household with empty doorNo</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:52 PM</td>
<td>
<a href="#" class="linked" test-id='289' id='289'><b>SCENARIO : </b>Test to update an existing household with doorNo having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:52 PM</td>
<td>
<a href="#" class="linked" test-id='292' id='292'><b>SCENARIO : </b>Test to update an existing household with doorNo having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:53 PM</td>
<td>
<a href="#" class="linked" test-id='295' id='295'><b>SCENARIO : </b>Test to update an existing household with empty addressLine1</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:53 PM</td>
<td>
<a href="#" class="linked" test-id='298' id='298'><b>SCENARIO : </b>Test to update an existing household with addressLine1 having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:54 PM</td>
<td>
<a href="#" class="linked" test-id='301' id='301'><b>SCENARIO : </b>Test to update an existing household with addressLine1 having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:55 PM</td>
<td>
<a href="#" class="linked" test-id='304' id='304'><b>SCENARIO : </b>Test to update an existing household with empty addressLine2</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:55 PM</td>
<td>
<a href="#" class="linked" test-id='307' id='307'><b>SCENARIO : </b>Test to update an existing household with addressLine2 having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:56 PM</td>
<td>
<a href="#" class="linked" test-id='310' id='310'><b>SCENARIO : </b>Test to update an existing household with addressLine2 having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:56 PM</td>
<td>
<a href="#" class="linked" test-id='313' id='313'><b>SCENARIO : </b>Test to update an existing household with empty landmark</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:57 PM</td>
<td>
<a href="#" class="linked" test-id='316' id='316'><b>SCENARIO : </b>Test to update an existing household with landmark having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:57 PM</td>
<td>
<a href="#" class="linked" test-id='319' id='319'><b>SCENARIO : </b>Test to update an existing household with landmark having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:58 PM</td>
<td>
<a href="#" class="linked" test-id='322' id='322'><b>SCENARIO : </b>Test to update an existing household with empty pincode</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:58 PM</td>
<td>
<a href="#" class="linked" test-id='325' id='325'><b>SCENARIO : </b>Test to update an existing household with pincode having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:59 PM</td>
<td>
<a href="#" class="linked" test-id='328' id='328'><b>SCENARIO : </b>Test to update an existing household with pincode having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:17:59 PM</td>
<td>
<a href="#" class="linked" test-id='331' id='331'><b>SCENARIO : </b>Test to update an existing household with empty buildingName</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:00 PM</td>
<td>
<a href="#" class="linked" test-id='334' id='334'><b>SCENARIO : </b>Test to update an existing household with buildingName having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:00 PM</td>
<td>
<a href="#" class="linked" test-id='337' id='337'><b>SCENARIO : </b>Test to update an existing household with buildingName having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:01 PM</td>
<td>
<a href="#" class="linked" test-id='340' id='340'><b>SCENARIO : </b>Test to update an existing household with empty street</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:02 PM</td>
<td>
<a href="#" class="linked" test-id='343' id='343'><b>SCENARIO : </b>Test to update an existing household with street having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:02 PM</td>
<td>
<a href="#" class="linked" test-id='346' id='346'><b>SCENARIO : </b>Test to update an existing household with street having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:04 PM</td>
<td>
<a href="#" class="linked" test-id='349' id='349'><b>SCENARIO : </b>Test to delete an existing household with auth token of a distributor</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:05 PM</td>
<td>
<a href="#" class="linked" test-id='352' id='352'><b>SCENARIO : </b>Test to delete an existing household by passing an empty id value for the household</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:05 PM</td>
<td>
<a href="#" class="linked" test-id='355' id='355'><b>SCENARIO : </b>Test to delete an existing household by passing an id value for the household which is less than required minimum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:07 PM</td>
<td>
<a href="#" class="linked" test-id='358' id='358'><b>SCENARIO : </b>Test to delete an existing household by passing an id value for the household which is more than alowed maximum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:07 PM</td>
<td>
<a href="#" class="linked" test-id='361' id='361'><b>SCENARIO : </b>Test to delete an existing household by passing a null value for id</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:08 PM</td>
<td>
<a href="#" class="linked" test-id='364' id='364'><b>SCENARIO : </b>Test to delete an existing household by passing a null value for hcmTenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:08 PM</td>
<td>
<a href="#" class="linked" test-id='367' id='367'><b>SCENARIO : </b>Test to delete an existing household by passing an clientReferenceId value for the household which is less than required minimum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:09 PM</td>
<td>
<a href="#" class="linked" test-id='370' id='370'><b>SCENARIO : </b>Test to delete an existing household by passing an clientReferenceId value for the household which is more than allowed maximum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:09 PM</td>
<td>
<a href="#" class="linked" test-id='373' id='373'><b>SCENARIO : </b>Test to delete an existing household by passing an empty value for clientReferenceId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:10 PM</td>
<td>
<a href="#" class="linked" test-id='376' id='376'><b>SCENARIO : </b>Test to delete an existing household by passing an clientReferenceId value for the address of the household which is less than required minimum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:10 PM</td>
<td>
<a href="#" class="linked" test-id='379' id='379'><b>SCENARIO : </b>Test to delete an existing household by passing an clientReferenceId value for the household which is more than allowed maximum length</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:11 PM</td>
<td>
<a href="#" class="linked" test-id='382' id='382'><b>SCENARIO : </b>Test to delete an existing household by passing an empty value for clientReferenceId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:11 PM</td>
<td>
<a href="#" class="linked" test-id='385' id='385'><b>SCENARIO : </b>Test to delete an existing household by passing a null value for address object tenantid</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:12 PM</td>
<td>
<a href="#" class="linked" test-id='388' id='388'><b>SCENARIO : </b>Test to delete an existing household with empty doorNo</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:12 PM</td>
<td>
<a href="#" class="linked" test-id='391' id='391'><b>SCENARIO : </b>Test to delete an existing household with doorNo having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:13 PM</td>
<td>
<a href="#" class="linked" test-id='394' id='394'><b>SCENARIO : </b>Test to delete an existing household with doorNo having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:13 PM</td>
<td>
<a href="#" class="linked" test-id='397' id='397'><b>SCENARIO : </b>Test to delete an existing household with empty addressLine1</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:14 PM</td>
<td>
<a href="#" class="linked" test-id='400' id='400'><b>SCENARIO : </b>Test to delete an existing household with addressLine1 having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:14 PM</td>
<td>
<a href="#" class="linked" test-id='403' id='403'><b>SCENARIO : </b>Test to delete an existing household with addressLine1 having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:15 PM</td>
<td>
<a href="#" class="linked" test-id='406' id='406'><b>SCENARIO : </b>Test to delete an existing household with empty addressLine2</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:15 PM</td>
<td>
<a href="#" class="linked" test-id='409' id='409'><b>SCENARIO : </b>Test to delete an existing household with addressLine2 having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:16 PM</td>
<td>
<a href="#" class="linked" test-id='412' id='412'><b>SCENARIO : </b>Test to delete an existing household with addressLine2 having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:16 PM</td>
<td>
<a href="#" class="linked" test-id='415' id='415'><b>SCENARIO : </b>Test to delete an existing household with empty landmark</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:17 PM</td>
<td>
<a href="#" class="linked" test-id='418' id='418'><b>SCENARIO : </b>Test to delete an existing household with landmark having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:17 PM</td>
<td>
<a href="#" class="linked" test-id='421' id='421'><b>SCENARIO : </b>Test to delete an existing household with landmark having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:18 PM</td>
<td>
<a href="#" class="linked" test-id='424' id='424'><b>SCENARIO : </b>Test to delete an existing household with empty pincode</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:18 PM</td>
<td>
<a href="#" class="linked" test-id='427' id='427'><b>SCENARIO : </b>Test to delete an existing household with pincode having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:19 PM</td>
<td>
<a href="#" class="linked" test-id='430' id='430'><b>SCENARIO : </b>Test to delete an existing household with pincode having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:19 PM</td>
<td>
<a href="#" class="linked" test-id='433' id='433'><b>SCENARIO : </b>Test to delete an existing household with empty buildingName</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:20 PM</td>
<td>
<a href="#" class="linked" test-id='436' id='436'><b>SCENARIO : </b>Test to delete an existing household with buildingName having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:20 PM</td>
<td>
<a href="#" class="linked" test-id='439' id='439'><b>SCENARIO : </b>Test to delete an existing household with buildingName having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:21 PM</td>
<td>
<a href="#" class="linked" test-id='442' id='442'><b>SCENARIO : </b>Test to delete an existing household with empty street</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:21 PM</td>
<td>
<a href="#" class="linked" test-id='445' id='445'><b>SCENARIO : </b>Test to delete an existing household with street having a value less than minimum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:22 PM</td>
<td>
<a href="#" class="linked" test-id='448' id='448'><b>SCENARIO : </b>Test to delete an existing household with street having a value more than maximum allowed number</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:25 PM</td>
<td>
<a href="#" class="linked" test-id='451' id='451'><b>SCENARIO : </b>Test to test household API CRUD operations</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:27 PM</td>
<td>
<a href="#" class="linked" test-id='454' id='454'><b>SCENARIO : </b>Test to create a household with auth token of a distributor</a>
</td>
</tr>
</tbody>
</table>
</div>
</li>
<li class="test-item">
<div class="test-detail">
<span class="meta">
<span class='badge log pass-bg'>14</span>
</span>
<p class="name">ProductServices-HCM</p>
<p class="duration text-sm">14 tests</p>
</div>
<div class="test-contents d-none">
<div class="info">
<h4>ProductServices-HCM</h4>
<span status="pass" class='badge log pass-bg'>14 passed</span>
</div>
<table class='table table-sm mt-4'>
<thead>
<tr>
<th class="status-col">Status</th>
<th class="timestamp-col">Timestamp</th>
<th>TestName</th>
</tr>
</thead>
<tbody>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:28 PM</td>
<td>
<a href="#" class="linked" test-id='457' id='457'><b>SCENARIO : </b>Test to create a product</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:28 PM</td>
<td>
<a href="#" class="linked" test-id='460' id='460'><b>SCENARIO : </b>Test to create a product with an unauthorised user</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:28 PM</td>
<td>
<a href="#" class="linked" test-id='463' id='463'><b>SCENARIO : </b>Test to create a product with an unauthorised user</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:28 PM</td>
<td>
<a href="#" class="linked" test-id='466' id='466'><b>SCENARIO : </b>Test to create a product with null product name</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:29 PM</td>
<td>
<a href="#" class="linked" test-id='469' id='469'><b>SCENARIO : </b>Test to create a product with null tenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:29 PM</td>
<td>
<a href="#" class="linked" test-id='472' id='472'><b>SCENARIO : </b>Test to create a product with null type</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:29 PM</td>
<td>
<a href="#" class="linked" test-id='475' id='475'><b>SCENARIO : </b>Test to create a product with null apiOperation</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:29 PM</td>
<td>
<a href="#" class="linked" test-id='478' id='478'><b>SCENARIO : </b>Test to create a product with invalid tenantId</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:29 PM</td>
<td>
<a href="#" class="linked" test-id='481' id='481'><b>SCENARIO : </b>Test to create a product to verify the minimum value needed for the type</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:29 PM</td>
<td>
<a href="#" class="linked" test-id='484' id='484'><b>SCENARIO : </b>Test to create a product to verify the maximum value needed for the type</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:29 PM</td>
<td>
<a href="#" class="linked" test-id='487' id='487'><b>SCENARIO : </b>Test to create a product to verify the minimum value needed for the name</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:30 PM</td>
<td>
<a href="#" class="linked" test-id='490' id='490'><b>SCENARIO : </b>Test to create a product to verify the maximum value needed for the name</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:30 PM</td>
<td>
<a href="#" class="linked" test-id='493' id='493'><b>SCENARIO : </b>Test to create a product to verify the invalid value for apiOperation</a>
</td>
</tr>
<tr class="tag-test-status" status="pass">
<td><span class="badge log pass-bg">Pass</span></td>
<td>13:18:30 PM</td>
<td>
<a href="#" class="linked" test-id='496' id='496'><b>SCENARIO : </b>Test to create a product to verify empty string value for apiOperation</a>
</td>
</tr>
</tbody>
</table>
</div>
</li>
</ul>
</div>
</div>
<div class="test-content scrollable">
<div class="test-content-detail">
<div class="detail-body"></div>
</div>
</div>
</div><div class="test-wrapper row view test-view">
  <div class="test-list">
    <div class="test-list-tools">
<ul class="tools pull-left">
<li><a href="#"><span class="font-size-14">Tests</span></a></li>
</ul>
<ul class="tools text-right">
<li class="dropdown">
<a href="#" class="dropdown-toggle" data-toggle="dropdown"><i class="fa fa-exclamation-circle"></i></a>
<ul id="status-toggle" class="dropdown-menu dropdown-md p-v-0">
<a class="dropdown-item" status="pass" href="#"><span>Pass</span><span class="status success"></span></a>
<div class="dropdown-divider"></div>
<a status="clear" class="dropdown-item" href="#"><span>Clear</span><span class="pull-right"><i class="fa fa-close"></i></span></a>
</ul>
</li>
<li class="dropdown">
<a href="#" class="dropdown-toggle" data-toggle="dropdown"><i class="fa fa-tag"></i></a>
<ul id="tag-toggle" class="dropdown-menu dropdown-md p-v-0">
<a class="dropdown-item" href="#">HouseholdMemberServices-HCM</a><a class="dropdown-item" href="#">IndividualServices-HCM</a><a class="dropdown-item" href="#">HouseholdServices-HCM</a><a class="dropdown-item" href="#">ProductServices-HCM</a>
</ul>
</li>
</ul>
</div>    <div class="test-list-wrapper scrollable">
      <ul class="test-list-item">
        <li class="test-item"  status="pass" test-id="1"
          author=""
          tag="HouseholdMemberServices-HCM"
          device="">
          <div class="test-detail">
            <p class="name"><b>SCENARIO :   </b>Test to create a household member with auth token of a registrar</p>
            <p class="text-sm">
              <span>13:16:47 PM</span> / <span>30:00:049</span>
              <span class="badge pass-bg log float-right">Pass</span>
            </p>
          </div>
          <div class="test-contents d-none">
<div class="detail-head">
<div class="p-v-10">
<div class="info">
<h5 class="test-status text-pass"><b>SCENARIO : </b>Test to create a household member with auth token of a registrar</h5>
<span class='badge badge-success'>03.28.2023 13:16:47</span>
<span class='badge badge-danger'>03.28.2023 13:16:47</span>
<span class='badge badge-default'>30:00:049</span>
&middot; <span class='uri-anchor badge badge-default'>#test-id=1</span>
</div>
<div class="m-t-15"><span class="badge badge-pill badge-default">HouseholdMemberServices-HCM</span></div>
</div>
</div><div class="detail-body mt-4">
<table class="table table-sm">
  <thead><tr><th class="status-col">Status</th><th class="timestamp-col">Timestamp</th><th class="details-col">Details</th></tr></thead>
  <tbody>
      <tr class="event-row">
        <td><span class="badge log info-bg">Info</span></td>
        <td>1:16:47 PM</td>
        <td>
          <b>FEATURE :   </b>Household Member Services - HCM
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log info-bg">Info</span></td>
        <td>1:16:47 PM</td>
        <td>
          <b>TAGS :   </b> @HCM_household_member_create_01, @healthServices, @regression, @positive, @smoke, @hcm_household_member_create, @hcm, @householdMemberService
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          <span class='badge white-text green'><b>STATUS :   </b>PASSED</span>
        </td>
      </tr>
  </tbody>
</table>
</div>
  <div class="mt-4">  <div class="accordion">
      <div class="card">
        <div class="card-header">
          <div class="card-title">
            <div class="node" id="2">BACKGROUND:</div>
            <div class="node-status float-right"><span class="badge pass-bg log ">Pass</span></div>
            <div class="node-time">
              <span class='badge badge-default'>30:00:004</span>
            </div>
            <div class="node-attr">
<span class="badge badge-pill badge-default">HouseholdMemberServices-HCM</span>            </div>
          </div>
        </div>
        <div class="collapse">
          <div class="card-body">
<table class="table table-sm">
  <thead><tr><th class="status-col">Status</th><th class="timestamp-col">Timestamp</th><th class="details-col">Details</th></tr></thead>
  <tbody>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def jsUtils = read('classpath:com/egov/utils/jsUtils.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
           com/egov/health-services/tests/../../common-services/pretests/authenticationToken.feature
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * configure headers = read('classpath:com/egov/utils/oauthTokenHeader.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * configure headers = read('classpath:com/egov/utils/oauthTokenHeader.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > Given url authTokenUrl
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field username = sysAdminUsername
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field password = sysAdminPassword
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field grant_type = 'password'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field scope = 'read'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field tenantId = sysAdminTenant
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field userType = sysAdminUserType
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > When method post
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > Then status 200
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And def authResponseBody = response
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And def authResponseHeader = responseHeaders
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And def authToken = authResponseBody.access_token
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * print authResponseBody.access_token
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * match authResponseBody.access_token == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
           com/egov/health-services/tests/../../common-services/pretests/authenticationToken.feature
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * configure headers = read('classpath:com/egov/utils/oauthTokenHeader.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * configure headers = read('classpath:com/egov/utils/oauthTokenHeader.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > Given url authTokenUrl
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field username = registrarUsername
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field password = registrarPassword
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field grant_type = 'password'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field scope = 'read'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field tenantId = registrarTenant
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field userType = registrarUserType
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > When method post
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > Then status 200
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And def authResponseBody = response
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And def authResponseHeader = responseHeaders
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And def authToken = authResponseBody.access_token
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * print authResponseBody.access_token
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * match authResponseBody.access_token == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
           com/egov/health-services/tests/../../common-services/pretests/authenticationToken.feature
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * configure headers = read('classpath:com/egov/utils/oauthTokenHeader.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * configure headers = read('classpath:com/egov/utils/oauthTokenHeader.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > Given url authTokenUrl
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field username = distributorUsername
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field password = distributorPassword
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field grant_type = 'password'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field scope = 'read'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field tenantId = distributorTenant
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And form field userType = distributorUserType
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > When method post
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > Then status 200
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And def authResponseBody = response
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And def authResponseHeader = responseHeaders
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And def authToken = authResponseBody.access_token
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * print authResponseBody.access_token
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * match authResponseBody.access_token == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def commonConstants = read('../../common-services/constants/genericConstants.yaml')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def householdClientReferenceId = getUUID()
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def memberCount = ranInteger(1)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def addressClientReferenceId = getUUID()
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def doorNo = "Door No " + intergerToString(retMax(1000))
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def type = getRandomArrayElement([ "PERMANENT", "CORRESPONDENCE", "OTHER" ])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def addressLine1 = "Auto_" + randomString(9) + "_Addressline1"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def addressLine2 = "Auto_" + randomString(9) + "_Addressline2"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def landmark = "Near " + randomString(9)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def city = "Auto_" + randomString(9)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def pincode = convertIntegerToString(generateRandomNumberInRange(1,999999))
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def buildingName = "Auto_" + randomString(5) + "_BuildingName"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def street = "Street " + randomNumber(2)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def localityCode = "Auto_" + getUnixEpochTime() + randomString(5) + "_LocalityCode"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def localityName = "Auto_" + randomNumber(5) + "_LocalityName"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def localityLabel = "Auto_" + randomNumber(5) + "_LocalityLabel"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def localityLatitude = convertIntegerToString(generateRandomNumberInRange(-90,90))
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def localityLongitude = convertIntegerToString(generateRandomNumberInRange(180,180))
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def hcmTenantId = "default"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def givenName = 'Auto_' + randomString(6)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def familyName = 'Auto_' + randomString(6)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def otherNames = 'Auto_' + randomString(6)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def clientReferenceId = getUUID()
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def bloodGroup = getRandomArrayElement(["O+", "O-", "A+", "A-", "B+","B-","AB+","AB-"])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def gender = getRandomArrayElement(["MALE","FEMALE","OTHER"])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def mobileNumber = ranInteger(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def altContactNumber = ranInteger(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def email = 'auto_' + getUnixEpochTime() + '@gmail.com'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def dateOfBirth = getDateInFormat("dd/MM/yyyy", generateRandomNumberInRange(1000,36500))
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def code = 'Auto_' + randomString(5)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def name = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def label = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def latitude = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def longitude = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def materializedPath = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def fatherName = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def husbandName = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def individualIdentifierClientReferenceId = getUUID()
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def individualSkillClientReferenceId = getUUID()
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def individualIdentifierType = getRandomArrayElement(["AADHAAR", "PAN", "DL", "VOTERID","PASSPORT"])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def individualIdentifierId = ranInteger(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def individualSkillType = getRandomArrayElement(["Type Writing", "Computer", "Science", "Singing", "Dancing", "Event Organizer"])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def individualSkillLevel = getRandomArrayElement(["Novice", "Learner", "Profecient", "Expert"])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def individualSkillExperience = getRandomArrayElement(["1 Year", "2 Years", "3 Years", "4 Years", "5 Years", "6 Years", "7 Years", "8 Years", "9 Years", "10 Years", "10+ Years"])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def photo = getUUID()
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def hcmAuthToken = registrarAuthToken
        </td>
      </tr>
  </tbody>
</table>
          </div>
        </div>
      </div>
      <div class="card">
        <div class="card-header">
          <div class="card-title">
            <div class="node" id="3">SCENARIO STEPS:</div>
            <div class="node-status float-right"><span class="badge pass-bg log ">Pass</span></div>
            <div class="node-time">
              <span class='badge badge-default'>30:00:014</span>
            </div>
            <div class="node-attr">
<span class="badge badge-pill badge-default">HouseholdMemberServices-HCM</span>            </div>
          </div>
        </div>
        <div class="collapse">
          <div class="card-body">
<table class="table table-sm">
  <thead><tr><th class="status-col">Status</th><th class="timestamp-col">Timestamp</th><th class="details-col">Details</th></tr></thead>
  <tbody>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * call read('../../health-services/pretest/householdServicePretest.feature@createHouseholdSuccess')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
           com/egov/health-services/tests/../../health-services/pretest/householdServicePretest.feature
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * def createHouseholdRequest = read('../../health-services/requestPayload/household-service/create.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * def searchHouseholdRequest = read('../../health-services/requestPayload/household-service/search.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * def updateHouseholdRequest = read('../../health-services/requestPayload/household-service/update.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * def deleteHouseholdRequest = read('../../health-services/requestPayload/household-service/delete.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * configure headers = read('classpath:com/egov/utils/websCommonHeaders.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > Given url createHouseholdURL
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And request createHouseholdRequest.householdCreateBody
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > When method post
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > Then status 202
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And def householdResponseBody = response
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * call read('../../health-services/pretest/householdServicePretest.feature@SuccessHouseholdSchemaValidation')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > com/egov/health-services/tests/../../health-services/pretest/householdServicePretest.feature
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * def createHouseholdRequest = read('../../health-services/requestPayload/household-service/create.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * def searchHouseholdRequest = read('../../health-services/requestPayload/household-service/search.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * def updateHouseholdRequest = read('../../health-services/requestPayload/household-service/update.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * def deleteHouseholdRequest = read('../../health-services/requestPayload/household-service/delete.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * configure headers = read('classpath:com/egov/utils/websCommonHeaders.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household == '#object'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.id == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.id != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.id == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.id == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.id != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.id == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.clientReferenceId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.clientReferenceId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.clientReferenceId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.clientReferenceId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.memberCount == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address == '#object'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.id == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.tenantId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.doorNo == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.type == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.addressLine1 == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.addressLine2 == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.landmark == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.city == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.buildingName == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.street == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.locality.code == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.locality.name == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.locality.label == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.locality.latitude == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.locality.longitude == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.isDeleted == '#boolean'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.rowVersion == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails == '#object'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails.createdBy == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails.createdBy != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails.createdBy == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails.lastModifiedBy == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails.lastModifiedBy != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails.lastModifiedBy == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails.createdTime == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails.createdTime != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails.createdTime == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails.lastModifiedTime == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails.lastModifiedTime != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdResponseBody.Household.auditDetails.lastModifiedTime == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.ResponseInfo.status == commonConstants.expectedStatus.success
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.tenantId == hcmTenantId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.clientReferenceId == householdClientReferenceId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.memberCount == memberCount
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.address.clientReferenceId == addressClientReferenceId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.address.doorNo == doorNo
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.address.type == type
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.address.addressLine1 == addressLine1
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.address.addressLine2 == addressLine2
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.address.landmark == landmark
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.address.city == city
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.address.pincode == pincode
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.address.buildingName == buildingName
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.address.street == street
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.address.locality.code == localityCode
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.isDeleted == false
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdResponseBody.Household.rowVersion == 1
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def householdClientReferenceId = householdClientReferenceId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def householdId = householdResponseBody.Household.id
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * call read('../../health-services/pretest/individualServicePretest.feature@createIndividualSuccess')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
           com/egov/health-services/tests/../../health-services/pretest/individualServicePretest.feature
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * def createIndividualRequest = read('../../health-services/requestPayload/individual-service/create.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * def searchIndividualRequest = read('../../health-services/requestPayload/individual-service/search.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * def updateIndividualRequest = read('../../health-services/requestPayload/individual-service/update.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * def deleteIndividualRequest = read('../../health-services/requestPayload/individual-service/delete.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * configure headers = read('classpath:com/egov/utils/websCommonHeaders.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > Given url createIndividualURL
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And request createIndividualRequest.individualCreateBody
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > When method post
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > Then status 202
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And def createIndividualResponseBody = response
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * call read('../../health-services/pretest/individualServicePretest.feature@SuccessIndividualSchemaValidation')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > com/egov/health-services/tests/../../health-services/pretest/individualServicePretest.feature
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * def createIndividualRequest = read('../../health-services/requestPayload/individual-service/create.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * def searchIndividualRequest = read('../../health-services/requestPayload/individual-service/search.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * def updateIndividualRequest = read('../../health-services/requestPayload/individual-service/update.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * def deleteIndividualRequest = read('../../health-services/requestPayload/individual-service/delete.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * configure headers = read('classpath:com/egov/utils/websCommonHeaders.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual == '#object'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.id == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.id != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.id == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.tenantId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.tenantId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.tenantId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.clientReferenceId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.userId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.name == '#object'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.name == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.name != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.name.givenName == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.name.familyName == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.name.otherNames == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.dateOfBirth == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.gender == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.bloodGroup == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.mobileNumber == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.altContactNumber == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.email == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address == '#array'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].clientReferenceId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].id == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].id != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].id == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].tenantId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].doorNo == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].type == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].addressLine1 == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].addressLine2 == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].landmark == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].city == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].buildingName == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].street == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].locality.code == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].locality.name == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].locality.label == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].locality.latitude == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].locality.longitude == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.address[0].isDeleted == '#boolean'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.fatherName == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.husbandName == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers == '#array'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].id == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].id != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].id == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].clientReferenceId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].clientReferenceId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].clientReferenceId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].individualId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].individualId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].individualId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].identifierType == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].identifierType != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].identifierType == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].identifierId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].identifierId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].identifierId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].isDeleted == '#boolean'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].isDeleted == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails == '#object'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails.createdBy == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails.createdBy != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails.createdBy == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails.lastModifiedBy == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails.lastModifiedBy != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails.lastModifiedBy == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails.createdTime == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails.createdTime != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails.createdTime == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails.lastModifiedTime == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails.lastModifiedTime != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.identifiers[0].auditDetails.lastModifiedTime == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills == '#array'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].id == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].id != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].id == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].clientReferenceId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].clientReferenceId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].clientReferenceId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].individualId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].individualId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].individualId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].type == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].type == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].type != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].level == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].level == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].level != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].experience == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].experience == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].experience != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].isDeleted == '#boolean'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].isDeleted == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails == '#object'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails.createdBy == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails.createdBy != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails.createdBy == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails.lastModifiedBy == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails.lastModifiedBy != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails.lastModifiedBy == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails.createdTime == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails.createdTime != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails.createdTime == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails.lastModifiedTime == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails.lastModifiedTime != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.skills[0].auditDetails.lastModifiedTime == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.photo == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.isDeleted == '#boolean'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.rowVersion == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.isDeleted == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.rowVersion == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails == '#object'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails.createdBy == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails.createdBy != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails.createdBy == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails.lastModifiedBy == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails.lastModifiedBy != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails.lastModifiedBy == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails.createdTime == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails.createdTime != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails.createdTime == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails.lastModifiedTime == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails.lastModifiedTime != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match createIndividualResponseBody.Individual.auditDetails.lastModifiedTime == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.ResponseInfo.status == commonConstants.expectedStatus.success
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.name.givenName == givenName
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.name.familyName == familyName
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.name.otherNames == otherNames
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.dateOfBirth == dateOfBirth
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.bloodGroup == bloodGroup
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.gender == gender
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.mobileNumber == mobileNumber
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.altContactNumber == altContactNumber
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.email == email
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].doorNo == doorNo
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].addressLine1 == addressLine1
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].addressLine2 == addressLine2
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].landmark == landmark
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].city == city
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].pincode == pincode
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].buildingName == buildingName
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].street == street
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].locality.code == code
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].locality.name == name
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].locality.label == label
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].locality.latitude == latitude
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].locality.longitude == longitude
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.address[0].locality.materializedPath == materializedPath
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.fatherName == fatherName
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.husbandName == husbandName
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.identifiers[0].clientReferenceId == individualIdentifierClientReferenceId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.identifiers[0].individualId == createIndividualResponseBody.Individual.id
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.identifiers[0].identifierType == individualIdentifierType
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.identifiers[0].identifierId == individualIdentifierId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.skills[0].clientReferenceId == individualSkillClientReferenceId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.skills[0].individualId == createIndividualResponseBody.Individual.id
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.skills[0].type == individualSkillType
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.skills[0].level == individualSkillLevel
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.skills[0].experience == individualSkillExperience
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert createIndividualResponseBody.Individual.photo == photo
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def individualClientReferenceId = clientReferenceId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def individualId = createIndividualResponseBody.Individual.id
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * def isHeadOfHousehold = true
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * call read('../../health-services/pretest/householdMemberServicePretest.feature@createHouseholdMemberSuccess')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
           com/egov/health-services/tests/../../health-services/pretest/householdMemberServicePretest.feature
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * def createHouseholdMemberRequest = read('../../health-services/requestPayload/household-member-service/create.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * def searchHouseholdMemberRequest = read('../../health-services/requestPayload/household-member-service/search.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * def updateHouseholdMemberRequest = read('../../health-services/requestPayload/household-member-service/update.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * def deleteHouseholdMemberRequest = read('../../health-services/requestPayload/household-member-service/delete.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * configure headers = read('classpath:com/egov/utils/websCommonHeaders.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > Given url createHouseholdMemberURL
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And request createHouseholdMemberRequest.createHouseholdMemberBody
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > When method post
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > Then status 202
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > And def householdMemberResponseBody = response
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > * call read('../../health-services/pretest/householdMemberServicePretest.feature@SuccessHouseholdMemberSchemaValidation')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          > com/egov/health-services/tests/../../health-services/pretest/householdMemberServicePretest.feature
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * def createHouseholdMemberRequest = read('../../health-services/requestPayload/household-member-service/create.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * def searchHouseholdMemberRequest = read('../../health-services/requestPayload/household-member-service/search.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * def updateHouseholdMemberRequest = read('../../health-services/requestPayload/household-member-service/update.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * def deleteHouseholdMemberRequest = read('../../health-services/requestPayload/household-member-service/delete.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * configure headers = read('classpath:com/egov/utils/websCommonHeaders.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember == '#object'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.id == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.id != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.id == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.householdId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.householdId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.householdId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.householdClientReferenceId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.householdClientReferenceId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.householdClientReferenceId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.individualId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.individualId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.individualId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.individualClientReferenceId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.individualClientReferenceId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.individualClientReferenceId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.isHeadOfHousehold == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.isHeadOfHousehold != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.isHeadOfHousehold == '#boolean'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.tenantId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.tenantId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.tenantId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.isDeleted == '#boolean'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.rowVersion == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails == '#object'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails.createdBy == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails.createdBy != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails.createdBy == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails.lastModifiedBy == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails.lastModifiedBy != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails.lastModifiedBy == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails.createdTime == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails.createdTime != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails.createdTime == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails.lastModifiedTime == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails.lastModifiedTime != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          >> * match householdMemberResponseBody.HouseholdMember.auditDetails.lastModifiedTime == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdMemberResponseBody.ResponseInfo.status == commonConstants.expectedStatus.success
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdMemberResponseBody.HouseholdMember.householdId == householdId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdMemberResponseBody.HouseholdMember.householdClientReferenceId == householdClientReferenceId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdMemberResponseBody.HouseholdMember.individualId == individualId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdMemberResponseBody.HouseholdMember.individualClientReferenceId == individualClientReferenceId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdMemberResponseBody.HouseholdMember.isHeadOfHousehold == true
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdMemberResponseBody.HouseholdMember.tenantId == hcmTenantId
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdMemberResponseBody.HouseholdMember.isDeleted == false
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:47 PM</td>
        <td>
          * assert householdMemberResponseBody.HouseholdMember.rowVersion == 1
        </td>
      </tr>
  </tbody>
</table>
          </div>
        </div>
      </div>
  </div>
</div>
          </div>
        </li>
        <li class="test-item"  status="pass" test-id="4"
          author=""
          tag="HouseholdMemberServices-HCM"
          device="">
          <div class="test-detail">
            <p class="name"><b>SCENARIO :   </b>Test to create a household with auth token of a distributor</p>
            <p class="text-sm">
              <span>13:16:49 PM</span> / <span>30:00:014</span>
              <span class="badge pass-bg log float-right">Pass</span>
            </p>
          </div>
          <div class="test-contents d-none">
<div class="detail-head">
<div class="p-v-10">
<div class="info">
<h5 class="test-status text-pass"><b>SCENARIO : </b>Test to create a household with auth token of a distributor</h5>
<span class='badge badge-success'>03.28.2023 13:16:49</span>
<span class='badge badge-danger'>03.28.2023 13:16:49</span>
<span class='badge badge-default'>30:00:014</span>
&middot; <span class='uri-anchor badge badge-default'>#test-id=4</span>
</div>
<div class="m-t-15"><span class="badge badge-pill badge-default">HouseholdMemberServices-HCM</span></div>
</div>
</div><div class="detail-body mt-4">
<table class="table table-sm">
  <thead><tr><th class="status-col">Status</th><th class="timestamp-col">Timestamp</th><th class="details-col">Details</th></tr></thead>
  <tbody>
      <tr class="event-row">
        <td><span class="badge log info-bg">Info</span></td>
        <td>1:16:49 PM</td>
        <td>
          <b>FEATURE :   </b>Household Member Services - HCM
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log info-bg">Info</span></td>
        <td>1:16:49 PM</td>
        <td>
          <b>TAGS :   </b> @HCM_household_member_create_02, @healthServices, @regression, @positive, @smoke, @hcm_household_member_create, @hcm, @householdMemberService
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          <span class='badge white-text green'><b>STATUS :   </b>PASSED</span>
        </td>
      </tr>
  </tbody>
</table>
</div>
  <div class="mt-4">  <div class="accordion">
      <div class="card">
        <div class="card-header">
          <div class="card-title">
            <div class="node" id="5">BACKGROUND:</div>
            <div class="node-status float-right"><span class="badge pass-bg log ">Pass</span></div>
            <div class="node-time">
              <span class='badge badge-default'>30:00:000</span>
            </div>
            <div class="node-attr">
<span class="badge badge-pill badge-default">HouseholdMemberServices-HCM</span>            </div>
          </div>
        </div>
        <div class="collapse">
          <div class="card-body">
<table class="table table-sm">
  <thead><tr><th class="status-col">Status</th><th class="timestamp-col">Timestamp</th><th class="details-col">Details</th></tr></thead>
  <tbody>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def jsUtils = read('classpath:com/egov/utils/jsUtils.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def commonConstants = read('../../common-services/constants/genericConstants.yaml')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def householdClientReferenceId = getUUID()
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def memberCount = ranInteger(1)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def addressClientReferenceId = getUUID()
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def doorNo = "Door No " + intergerToString(retMax(1000))
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def type = getRandomArrayElement([ "PERMANENT", "CORRESPONDENCE", "OTHER" ])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def addressLine1 = "Auto_" + randomString(9) + "_Addressline1"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def addressLine2 = "Auto_" + randomString(9) + "_Addressline2"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def landmark = "Near " + randomString(9)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def city = "Auto_" + randomString(9)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def pincode = convertIntegerToString(generateRandomNumberInRange(1,999999))
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def buildingName = "Auto_" + randomString(5) + "_BuildingName"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def street = "Street " + randomNumber(2)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def localityCode = "Auto_" + getUnixEpochTime() + randomString(5) + "_LocalityCode"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def localityName = "Auto_" + randomNumber(5) + "_LocalityName"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def localityLabel = "Auto_" + randomNumber(5) + "_LocalityLabel"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def localityLatitude = convertIntegerToString(generateRandomNumberInRange(-90,90))
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def localityLongitude = convertIntegerToString(generateRandomNumberInRange(180,180))
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def hcmTenantId = "default"
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def givenName = 'Auto_' + randomString(6)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def familyName = 'Auto_' + randomString(6)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def otherNames = 'Auto_' + randomString(6)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def clientReferenceId = getUUID()
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def bloodGroup = getRandomArrayElement(["O+", "O-", "A+", "A-", "B+","B-","AB+","AB-"])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def gender = getRandomArrayElement(["MALE","FEMALE","OTHER"])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def mobileNumber = ranInteger(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def altContactNumber = ranInteger(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def email = 'auto_' + getUnixEpochTime() + '@gmail.com'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def dateOfBirth = getDateInFormat("dd/MM/yyyy", generateRandomNumberInRange(1000,36500))
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def code = 'Auto_' + randomString(5)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def name = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def label = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def latitude = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def longitude = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def materializedPath = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def fatherName = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def husbandName = 'Auto_' + randomString(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def individualIdentifierClientReferenceId = getUUID()
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def individualSkillClientReferenceId = getUUID()
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def individualIdentifierType = getRandomArrayElement(["AADHAAR", "PAN", "DL", "VOTERID","PASSPORT"])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def individualIdentifierId = ranInteger(10)
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def individualSkillType = getRandomArrayElement(["Type Writing", "Computer", "Science", "Singing", "Dancing", "Event Organizer"])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def individualSkillLevel = getRandomArrayElement(["Novice", "Learner", "Profecient", "Expert"])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def individualSkillExperience = getRandomArrayElement(["1 Year", "2 Years", "3 Years", "4 Years", "5 Years", "6 Years", "7 Years", "8 Years", "9 Years", "10 Years", "10+ Years"])
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def photo = getUUID()
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def hcmAuthToken = registrarAuthToken
        </td>
      </tr>
  </tbody>
</table>
          </div>
        </div>
      </div>
      <div class="card">
        <div class="card-header">
          <div class="card-title">
            <div class="node" id="6">SCENARIO STEPS:</div>
            <div class="node-status float-right"><span class="badge pass-bg log ">Pass</span></div>
            <div class="node-time">
              <span class='badge badge-default'>30:00:012</span>
            </div>
            <div class="node-attr">
<span class="badge badge-pill badge-default">HouseholdMemberServices-HCM</span>            </div>
          </div>
        </div>
        <div class="collapse">
          <div class="card-body">
<table class="table table-sm">
  <thead><tr><th class="status-col">Status</th><th class="timestamp-col">Timestamp</th><th class="details-col">Details</th></tr></thead>
  <tbody>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * def hcmAuthToken = distributorAuthToken
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          * call read('../../health-services/pretest/householdServicePretest.feature@createHouseholdSuccess')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
           com/egov/health-services/tests/../../health-services/pretest/householdServicePretest.feature
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          > * def createHouseholdRequest = read('../../health-services/requestPayload/household-service/create.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          > * def searchHouseholdRequest = read('../../health-services/requestPayload/household-service/search.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          > * def updateHouseholdRequest = read('../../health-services/requestPayload/household-service/update.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          > * def deleteHouseholdRequest = read('../../health-services/requestPayload/household-service/delete.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          > * configure headers = read('classpath:com/egov/utils/websCommonHeaders.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          > Given url createHouseholdURL
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          > And request createHouseholdRequest.householdCreateBody
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          > When method post
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          > Then status 202
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          > And def householdResponseBody = response
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          > * call read('../../health-services/pretest/householdServicePretest.feature@SuccessHouseholdSchemaValidation')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          > com/egov/health-services/tests/../../health-services/pretest/householdServicePretest.feature
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * def createHouseholdRequest = read('../../health-services/requestPayload/household-service/create.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * def searchHouseholdRequest = read('../../health-services/requestPayload/household-service/search.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * def updateHouseholdRequest = read('../../health-services/requestPayload/household-service/update.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * def deleteHouseholdRequest = read('../../health-services/requestPayload/household-service/delete.json')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * configure headers = read('classpath:com/egov/utils/websCommonHeaders.js')
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household == '#object'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.id == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.id != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.id == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.id == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.id != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.id == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.clientReferenceId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.clientReferenceId != null
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.clientReferenceId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.clientReferenceId == '#present'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.memberCount == '#number'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.address == '#object'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.id == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
        <td>
          >> * match householdResponseBody.Household.address.tenantId == '#string'
        </td>
      </tr>
      <tr class="event-row">
        <td><span class="badge log pass-bg">Pass</span></td>
        <td>1:16:49 PM</td>
      
```

\
[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
