---
description: >-
  An overview of the prerequisites to setup DIGIT and some of the key
  capabilities to understand before provisioning the infra and deploy DIGIT.
---

# Setup Requirements

## Overview <a href="#overview" id="overview"></a>

DIGIT is the largest urban governance platform built for billions and billions of transactions between citizens and the state govt through various municipal services/integration. The platform is built with key capabilities like scale, speed, integration, configurable, customizable, extendable, multi-tenanted, security, etc. Here, we shall discuss the key requirements and capabilities.

#### Pre-requisites <a href="#pre-requisites" id="pre-requisites"></a>

Before proceeding to set up DIGIT, it is essential to know some of the key technical details about DIGIT, like architecture, tech stack and how it is packaged and deployed on various infrastructures. Some of these details are explained in the previous sections. Below are some of the key capabilities to know about DIGIT as a platform.

1. 1.DIGIT is a collection of various services built as RESTFul APIs with OpenAPI standard
2. 2.DIGIT is built as MSA (Microservices Architecture)
3. 3.DIGIT services are packaged as containers and deployed as docker Images.
4. 4.DIGIT is deployed on Kubernetes which abstracts any Cloud/Infra suitable and standardised for DIGIT deployment.
5. 5.DIGIT deployment, configuration and customization are done through Helm Charts.
6. 6.Kubernetes cluster setup is done through code like terraform/ansible suitably.

#### Why [OpenAPI](https://medium.com/@ratrosy/building-apis-with-openapi-ac3c24e33ee3)​ <a href="#why-openapi" id="why-openapi"></a>

The OpenAPI Specification (OAS) defines a standard, programming language-agnostic interface description for REST APIs, which allows both humans and computers to discover and understand the capabilities of a service without requiring access to source code, additional documentation, or inspection of network traffic. When properly defined via OpenAPI, a consumer can understand and interact with the remote service with a minimal amount of implementation logic. Similar to what interface descriptions have done for lower-level programming, the OpenAPI Specification removes the guesswork in calling a service.

#### Why [Microservice Architecture](https://medium.com/hashmapinc/the-what-why-and-how-of-a-microservices-architecture-4179579423a9)​ <a href="#why-microservice-architecture" id="why-microservice-architecture"></a>

Microservices are nothing but breaking big beasts into smaller units that can independently be developed, enhanced and scaled as a categorized and layered stack that gives better control over each component of an application that exists in its own container, independently managed and updated. This means that developers can build applications from multiple components and program each component in the language best suited to its function, rather than having to choose a single less-than-ideal language to use for everything. Optimizing software all the way down to the components of the application helps you increase the quality of your products. No time and resources are wasted managing the effects of updating one application on another.

#### Why [Containerized/Dockerized](https://medium.com/@pablo.iorio/container-based-architecture-i-iii-technical-advantages-7176195456c5)​ <a href="#why-containerized-dockerized" id="why-containerized-dockerized"></a>

Comparatively the best infra choice for running a microservices application architecture is application containers. Containers encapsulate a lightweight runtime environment for the application, presenting a consistent environment that can follow the application from the developer's desktop to testing to final production deployment, and you can run containers on cloud infra with physical or virtual machines.

#### Why [Kubernetes](https://urban.digit.org/platform/installation/more-deploy-docs/setup-digit/why-kubernetes-for-digit)​ <a href="#why-kubernetes" id="why-kubernetes"></a>

As most modern software developers can attest, containers have provided us with dramatically more flexibility for running cloud-native applications on physical and virtual infrastructure. Kubernetes allows you to deploy cloud-native applications anywhere and manage them exactly as you like everywhere. For more details refer to the above link that explains various advantages of Kubernetes.

#### Why [Helm Charts](https://medium.com/@technospace/an-introduction-to-helm-charts-41be1544370c)​ <a href="#why-helm-charts" id="why-helm-charts"></a>

Kubernetes, the popular container orchestration system, is used extensively. However, it can become complex: you have to handle all of the objects (ConfigMaps, pods, etc.), and would also have to manage the releases. Both can be accomplished with [Kubernetes Helm](https://platform9.com/resource/kubernetes-helm-why-it-matters/). It is a Kubernetes package manager designed to easily package, configure, and deploy applications and services onto Kubernetes clusters in a standard way, this helps the ecosystem to adopt the standard way of deployment and customization.For being successful in the DIGIT Setup, below are certain requirements that need to be ascertained:

#### Skills Needed <a href="#skills-needed" id="skills-needed"></a>

| DevOps                        | Text                              | Text                 |
| ----------------------------- | --------------------------------- | -------------------- |
| Scheduled Job Handling        | API Gateway                       | Container Management |
| Resource and Storage Handling | Fault Tolerance                   | Load Balancing       |
| Distributed Metrics           | Application Runtime and Packaging | App Deployment       |
| Configuration Management      | Service Discovery                 | CI / CD              |
| Virtualization                | Hardware & Storage                | OS & Networking      |
| SSL Configuration             | Infra-as-code                     | Dockers              |
| DNS Configuration             | GitOps                            | SecOps               |

* On-premise/private cloud accounts
  * Interface to access and provision required infra
  * In the case of SDC, NIC or private DC, it'll be VPN to an allocated VLAN
  * SSH access to the VMs/machines
* Infra Skills
  * Public cloud
    * Managed Kubernetes services like AKS or EKS or GKE on Azure, AWS and GCP respectively
  * Private Clouds (SDC, NIC)
    * Clouds like VMware, OpenStack, Nutanix and more, may or may not have Kubernetes as a managed service. If yes we may have to estimate only the worker nodes depending on the number of ULBs and DIGIT's municipal services that you opt.
    * In the absence of the above, you have to provision the Kubernetes cluster from the plain VMs as per the general Kubernetes setup instruction and add worker nodes.
* Operations Skills
  * Understanding of Linux, containers, VM Instances, Load Balancers, Security Groups/Firewalls, Nginx, DB Instance, Data Volumes
  * Experience with Kubernetes, Docker, Jenkins, Helm, Infra-as-code, Terraform
  * Experience in DevOps/SRE practice on microservices and modern infrastructure

#### High-level Action To Deploy DIGIT <a href="#high-level-action-to-deploy-digit" id="high-level-action-to-deploy-digit"></a>

1. ​[Provisioning the Kubernetes Cluster](https://medium.com/better-programming/build-your-own-multi-node-kubernetes-cluster-with-monitoring-346a7e2ef6e2) in any of the
   * ​[Commercial cloud](https://learn.hashicorp.com/terraform?track=kubernetes#kubernetes) or
   * ​[Private State datacenter](https://medium.com/faun/10-useful-kubernetes-tools-ddffa62089cc) (SDC) or
   * ​[National Cloud](https://cloud.gov.in/services.php) (NIC)
2. Setting up the [persistent disk volumes](https://medium.com/asl19-developers/create-readwritemany-persistentvolumeclaims-on-your-kubernetes-cluster-3a8db51f98e3) to attach to DIGIT backbone [stateful containers](https://medium.com/swlh/stupid-simple-kubernetes-persistent-volumes-explained-by-examples-29f8fec08c4) like
   * ZooKeeper
   * Kafka
   * Elastic Search
3. Setting up the Postgres DB
   * On a public cloud, provision a Postgres RDS instance.
   * Private cloud, provision a Postgres DB on a VM with the backup, HA/DRS
4. Preparing deployment configuration for required DIGIT services using [Helm](https://medium.com/better-programming/docker-kubernetes-and-helm-4b5a5a87bc8f) templates from the [InfraOps](https://github.com/egovernments/Train-InfraOps) like the following
   * Preparing DIGIT service [helm templates](https://medium.com/ingeniouslysimple/deploying-kubernetes-applications-with-helm-81c9c931f9d3) to deploy on the Kubernetes cluster
   * K8s Secrets
   * K8s ConfigMaps
   * Environment variables of each microservices
5. Deploy the stable released version of DIGIT and the required services
6. Setting up Jenkins job to build, bake images and deploy the components for the rolling updates
7. Setup [Application monitoring](https://medium.com/@Alibaba\_Cloud/system-monitoring-using-prometheus-and-grafana-8007d3aaf400), [Distributed Tracing](https://medium.com/velotio-perspectives/a-comprehensive-tutorial-to-implementing-opentracing-with-jaeger-a01752e1a8ce), [Alert management](https://medium.com/@abhishekbhardwaj510/alertmanager-integration-in-prometheus-197e03bfabdf)​

​
