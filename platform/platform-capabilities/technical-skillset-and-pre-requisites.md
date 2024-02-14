---
description: >-
  This page lists the skillset required for anyone to build and support the HCM
  application
---

# Technical Skillset & Pre-requisites

## Introduction <a href="#introduction" id="introduction"></a>

This document lists the technical skillsets required for someone to build and support the Health Campaign Management (HCM) platform. There are distinct skills required to customise the application, and set up and run the infrastructure for this. The basic hardware configuration required for the developer machine is part of this document.

## Technical Skillset <a href="#technical-prerequisites" id="technical-prerequisites"></a>

The technical skillsets that are required to work on the DIGIT HCM stack are listed below. It is expected the team has satisfactory knowledge of the below technologies before they take up DIGIT training.

### Development Team Skillset <a href="#skillset-for-the-development-team" id="skillset-for-the-development-team"></a>

* Open API Contract - Swagger2.0
* YAML/JSON
* Postman
* Postgres
* Java and REST APIS
* Basics of Elasticsearch
* Maven
* Springboot
* Kafka
* Zuul
* ReactJS
* Flutter

### DevOps Team Skillset <a href="#skill-set-for-the-devops-team" id="skill-set-for-the-devops-team"></a>

* Understanding of the micro-service architecture.
* Experience with AWS, Azure, GCP, and NIC Cloud.
* Strong working knowledge of Linux, command, VM Instances, networking, and storage.
* To create Kubernetes cluster on AWS, Azure, and GCP on NIC Cloud.
* Kubectl installation and commands (Apply, get, edit, describe k8s objects).
* Terraform for infra-as-code for cluster or VM provisioning.
* Understanding of VM types, Linux OS types, LoadBalancer, VPC, Subnets, Security Groups, Firewall, Routing, DNS).
* Experience setting up CI like Jenkins and creating pipelines.
* Deployment strategies - Rolling updates, Canary, Blue/Green.
* Artifactory - Nexus, Verdaccio, DockerHub, etc.
* Experience with Kubernetes ingress, setting up SSL certificates, and renewal.
* Understanding of the Zuul gateway.
* Gitops, Git branching, PR review process. Rules, Hooks, etc.
* Experience in Helm, packaging, and deploying.
* Apache, Nginx, Redis, and Postgres.

## Hardware Pre-requisites <a href="#hardware-prerequisites" id="hardware-prerequisites"></a>

Teams are expected to have laptops/desktops configured as mentioned below with all the software required to run the DIGIT application:

* Laptop for hands-on training with 16GB RAM and OS preferably Ubuntu
* All developers need to have Git IDs
* Install VSCode/IntelliJ/Eclipse
* Install [Git](https://git-scm.com/downloads)​
* Install [JDK 8 update 112 or higher](http://www.oracle.com/technetwork/java/javase/downloads)​
* Install [maven v3.2.x](http://maven.apache.org/download.cgi)​
* Install [PostgreSQL v9.](http://www.postgresql.org/download/)6
* Install [Elastic Search v2.4.x](https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-2.4.1.zip)​
* Postman

### Software Assets <a href="#software-assets" id="software-assets"></a>

There are knowledge assets available on the net for general items and eGov assets for DIGIT services. Here you can find references to each of the topics of importance. It is mandated the trainees do a self-study of all the software mentioned in the pre-requisites using the reference materials shared.

<table><thead><tr><th width="146.33333333333331">Topic</th><th>Reference</th><th>Preparedness Check</th></tr></thead><tbody><tr><td>Git</td><td>​<a href="https://www.atlassian.com/git">https://www.atlassian.com/git</a>​​​<a href="https://www.tutorialspoint.com/git/index.htm">https://www.tutorialspoint.com/git/index.htm</a>​​​<a href="https://www.udemy.com/course/git-complete/">https://www.udemy.com/course/git-complete/</a>​</td><td>Do you have a Git account? Do you know how to clone a repository, pull updates, push updates? Do you know how to give a pull request and merge the pull request?</td></tr><tr><td>Microservice Architecture</td><td>​<a href="https://www.tutorialspoint.com/microservice_architecture/index.htm">https://www.tutorialspoint.com/microservice_architecture/index.htm</a>​​​<a href="https://www.udemy.com/course/microservices-with-spring-boot-and-spring-cloud/">https://www.udemy.com/course/microservices-with-spring-boot-and-spring-cloud/</a>​</td><td>Do you know when to create a new service? How to access other services?</td></tr><tr><td>ReactJS</td><td>​<a href="https://reactjs.org/tutorial/tutorial.html">https://reactjs.org/tutorial/tutorial.html</a>​​​<a href="https://www.udemy.com/course/react-the-complete-guide-incl-redux">https://www.udemy.com/course/react-the-complete-guide-incl-redux</a>​​​<a href="https://www.tutorialspoint.com/reactjs/reactjs_overview.htm">https://www.tutorialspoint.com/reactjs/reactjs_overview.htm</a>​</td><td>How to create react app? How to create a stateful and stateless component? How to use HOC as a wrapper?Validations at form level using React.js and Redux.</td></tr><tr><td>Postgres</td><td>​<a href="https://www.postgresqltutorial.com/">https://www.postgresqltutorial.com/</a>​​​<a href="https://www.udemy.com/course/the-complete-python-postgresql-developer-course/">https://www.udemy.com/course/the-complete-python-postgresql-developer-course/</a>​​​<a href="https://www.tutorialspoint.com/postgresql/index.htm">https://www.tutorialspoint.com/postgresql/index.htm</a>​</td><td>How to create a database and set up privileges? How to add an index on a table? How to use aggregation functions in psql?</td></tr><tr><td>Postman</td><td>​<a href="https://www.postman.com/resources/videos-tutorials/">https://www.postman.com/resources/videos-tutorials/</a>​​​<a href="https://www.udemy.com/course/postman-the-complete-guide/">https://www.udemy.com/course/postman-the-complete-guide/</a>​</td><td>Call a REST API from Postman with proper payload and show the responseSetup any service locally (MDMS or user service has least dependencies) and check the API’s using postman.</td></tr><tr><td>REST APIs</td><td>​<a href="https://www.tutorialspoint.com/rest_api/index.asp">https://www.tutorialspoint.com/rest_api/index.asp</a>​​​<a href="https://www.youtube.com/watch?v=rtWH70_MMHM">https://www.youtube.com/watch?v=rtWH70_MMHM</a>​</td><td>What are the principles to be followed when making a REST API? When to use POST and GET? How to define the request and response parameters?</td></tr><tr><td>Kafka</td><td>​<a href="https://www.udemy.com/course/apache-kafka/">https://www.udemy.com/course/apache-kafka/</a>​​<a href="https://kafka.apache.org/intro">https://kafka.apache.org/intro</a>​​​<a href="https://www.tutorialspoint.com/apache_kafka/apache_kafka_introduction.htm">https://www.tutorialspoint.com/apache_kafka/apache_kafka_introduction.htm</a>​</td><td>How to push messages on Kafka topic? How does the consumer group work? What are partitions?</td></tr><tr><td>Docker and Kubernetes</td><td>​<a href="https://www.tutorialspoint.com/kubernetes/index.htm">https://www.tutorialspoint.com/kubernetes/index.htm</a>​​​<a href="https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide/">https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide/</a>​​​<a href="https://www.tutorialspoint.com/docker/index.htm">https://www.tutorialspoint.com/docker/index.htm</a>​</td><td>How to edit deployment configuration? How to read logs? How to go inside a Kubernetes pod? How to create a docker file using a base image? How to port-forward the pod to the local port?</td></tr><tr><td>JSON</td><td>​<a href="https://www.tutorialspoint.com/json/index.htm">https://www.tutorialspoint.com/json/index.htm</a> <a href="https://github.com/json-path/JsonPath">json-path/JsonPath</a>​</td><td>How to write filters to extract specific data using jsonPaths?</td></tr><tr><td>YAML</td><td>​<a href="https://www.udemy.com/course/yaml-essentials/">https://www.udemy.com/course/yaml-essentials/</a>​</td><td>How to read an API contract using swagger?</td></tr><tr><td>Zuul</td><td>​<a href="https://www.javatpoint.com/zuul-api-gateway">https://www.javatpoint.com/zuul-api-gateway</a>s</td><td>What does Zuul do?</td></tr><tr><td>Maven</td><td>​<a href="https://www.udemy.com/course/maven-quick-start/">https://www.udemy.com/course/maven-quick-start/</a>​​​<a href="https://www.tutorialspoint.com/maven/index.htm">https://www.tutorialspoint.com/maven/index.htm</a>​</td><td>What is POM? What is the purpose of maven clean install and how to do it? What is the difference between the version and SNAPSHOT?</td></tr><tr><td>Springboot</td><td>​<a href="https://www.tutorialspoint.com/spring_boot/index.htm">https://www.tutorialspoint.com/spring_boot/index.htm</a>​​​<a href="https://www.udemy.com/course/spring-hibernate-tutorial/">https://www.udemy.com/course/spring-hibernate-tutorial/</a>​</td><td>How does autowiring work in spring? How to write a consumer/producer using spring Kafka? How to make an API call to another service using restTemplate? How to execute queries using JDBC template?</td></tr><tr><td>Elastic search</td><td>​<a href="https://www.udemy.com/course/elasticsearch-complete-guide/">https://www.udemy.com/course/elasticsearch-complete-guide/</a>​​​<a href="https://www.tutorialspoint.com/elasticsearch/index.htm">https://www.tutorialspoint.com/elasticsearch/index.htm</a>​</td><td>How to write the basic queries to fetch data from the elastic search index?</td></tr><tr><td>DIGIT Architecture</td><td>​<a href="https://core.digit.org/focus-areas/platform-orientation-overview">Orientation - Platform Overview</a>​​​<a href="https://core.digit.org/platform/architecture">DIGIT Architecture and Technical overview</a>​</td><td>What comes as part of the core service, business service and municipal service? How to calls APIs from one service in another service?</td></tr><tr><td>DIGIT Core Services</td><td>​<a href="https://core.digit.org/platform/core-services">Product requirements</a>​</td><td>Which are the core services in the DIGIT framework?</td></tr><tr><td>DIGIT DevOps</td><td>​<a href="https://core.digit.org/microservices-and-low-code-no-code">DevOps Partners - KT Content</a>​​​<a href="https://core.digit.org/platform/checklists/deployment-checklist">DIGIT Deployment</a>​</td><td>​</td></tr><tr><td>DIGIT MDMS</td><td>​<a href="https://urban.digit.org/platform/configure-digit/setting-up-master-data/mdms-overview">MDMS Configuration</a>​</td><td>How to read a master date from MDMS? How to add new data in an existing master? Where is the MDMS data stored?</td></tr><tr><td>DIGIT UI Framework</td><td>​<a href="https://core.digit.org/guides/design-guide">Getting started</a>​</td><td>How to add a new component to the framework? How to use an existing component?</td></tr><tr><td>DSS</td><td>​<a href="https://urban.digit.org/platform/configure-digit/configuring-digit-services/dss-configuration-and-setup">Product - DSS</a>​</td><td>​</td></tr></tbody></table>

