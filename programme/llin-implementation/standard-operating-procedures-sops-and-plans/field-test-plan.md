# Field Test Plan

## Overview

The objective of field testing is to determine how the application works on field before releasing it to end-users in phase 4. The field testing will be performed during phase 3 distribution. The team will accompany the phase 3 distribution team, test the mobile app, and report their observations on the behaviour of the application. This SOP describes the process and prerequisites for field testing.&#x20;

## Prerequisites for Field Testing&#x20;

#### Feature/Module&#x20;

The field testing will be performed for the following modules:&#x20;

* HCM 1.0: Inventory, Registration, Supervision
* HCM 1.1: Complaints

#### Test Cases

Test cases provide a high-level description of the functionality to be tested. The team will leverage relevant QA test cases for project specific functionality. Each test case based on new functionality will reference a specific functional requirement.

#### Functionality

Every new function or functionality must be tested before the release, and most need to be continuously tested.

Steps:

* Identify the name of the function or feature.
* Pre-conditions for being able to test it (such as being logged in as a user with a certain access level or paid subscription plan).
* The steps required to test it.
* The expected result.

#### Offline capability

Before launching the application, it is advisable to understand offline capability.&#x20;

Steps:

* Identify the features which will work after the application goes to the offline mode.
* Test the non-functional features of the application.
* Identify the steps required to test it and expected results.

#### Synch capability&#x20;

This refers to syncing data from a remote server to a mobile device and stores the data locally.

Steps:

* Identify how the data is synchronised in offline and online modes.
* Understand the time period which is required for synchronising data.
* Identify the steps required to test it, and the expected results.

## Infrastructure

#### Test environment (Server)

A test environment is a nearly exact replica of a production (live) environment. It is created by integrating hardware, software, proper network configurations, and data necessary to run the tests. The infrastructure which we use for testing is comparatively less.

The test environment (sometimes referred to as a test bed) must be configured according to the needs of the software being tested. The test environment is set up with the requisite database before running the tests.

#### Sim Card and Internet

* Sim card internet 2G/3G/4G/5G or no internet network to check the usability of the application.
* Main target is to seek the best app performance with whatever internet connection they’re currently able to access.

#### Mobile app

* It is not necessary that every time one will have a strong Wifi or hotspot around. Hence, one has to rely on your phone’s mobile network.
* Field testing for a mobile app should be treated just as a routine test like regression, automation and should never be ignored.

## Team Identification and Alignment

* Create teams of 4-5 people and have them do the field test in different areas. Try to use the app while driving and while in a place with a low data range.&#x20;
* Every team aligns a particular person (team leader) for creating a document with the details of the test cases, the person executing it, an area where it was tested, and the bugs reported.
* As the app is yet to launch in phase 4, it helps you and your team to analyse the performance by using the app like a normal user.

## Province and Location Identification

* For better field-testing results, do this testing in different geographic locations, different phone models, and network modes. For example, high data network location (strong Wifi zone, 5G or 4G), low data network location (2G, 3G), or offline mode. You may try using the app while driving your car (fast or slow), or while taking a walk or sitting at home according to your comfort.
* Note: Field testing campaign will be organised for 3 days and this is not a formal testing event. Majorly, it will be conducted with eGov and CHAI staff. Funding the visit (per diems, venue cost, etc.) to be confirmed/determined.

## Timeline and Duration

* Field testing duration: 3 days.
* Field testing deadline: May 8, 2023.
* Mode and location: Will be shared by eGov and CHAI teams.

## Categorisation of Test Observations&#x20;

#### Operational

Operational testing refers to the evaluation of a software application before the production phase.

Steps:

* Resource check.
* Prepare test script.
* Execute the test script in phases.
* Note the observations.
* Follow-up bug fixing.

#### Functional

Functional testing is done to verify all the functionality of an application. You need to:

* Create test data (input values).
* Execute test cases.
* Compared actual and expected test cases.&#x20;
* Note the observations.

Steps:

* Determine the functionality of the product that needs to be tested. It includes testing the main functionalities, error condition, messages, and usability testing, that is, whether the product is user-friendly or not.
* The next step is to create the input data for the functionality to be tested as per the requirement specification.
* From the requirement specification, the output is determined for the functionality under test.
* Prepared test cases are executed.
* Actual output, that is, the output after executing the test case and the expected output (determined from the requirement specification) are compared to find out whether the functionality is working as expected or not.
* Required observations are noted, and the report is compiled.

#### Non-Functional

Non-functional testing is done to verify the non-functional requirement of the application like performance, usability, etc. A checklist is used to ensure that no important aspect is left without testing.

Non-functional testing features:

* Security
* Scalability
* Efficiency
* Disaster recovery
* Maintainability
* Endurance
* Failover
* Portability
* Finally, prepare the performance report.

Non-functional testing tools:

* JMeter
* Loadster
* Loadrunner
* Loadstorm
* Neoload
* Forecast
* Load Complete
* Webserver Stress Tool
* WebLoad Professional
* Loadtracer
* vPerformer

## Process of Observation Reporting and Resolution

#### App observation report (Bug tracking)

Steps:

* What needs to be tested: The scope of testing, including clear identification of what will be tested, and what will not be tested.
* How the testing is going to be performed: Breaking down the testing into small and manageable tasks, and identifying the strategies to be used for carrying out the tasks.
* Resource needed for testing.
* The timelines by which the testing activities will be performed.
* Risks that may be faced in all of the above, with appropriate mitigation and contingency plans.

#### Reporting process:

* With the help from above the section, a bug report will be prepared.&#x20;
* Bug report will be shared with the BA+Dev teams for bug fixing.
* Another copy of the bug report will be shared with the CHAI and NMCP teams.

#### Process for resolution based on the  type of observations&#x20;

<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-12 at 10.35.37 AM.png" alt=""><figcaption></figcaption></figure>
