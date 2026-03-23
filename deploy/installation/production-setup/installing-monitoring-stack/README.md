# Installing Monitoring Stack

This document provides a comprehensive guide to upgrading monitoring services in Kubernetes cluster, including Grafana for visualization, Loki for log management, and Prometheus for metrics and alerting. The guide covers the essential steps for upgrading these services using Helmfile, along with the necessary configurations.



#### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

Before proceeding with the upgrade, ensure you have the following tools installed and configured:

* **Helmfile**: A declarative spec for deploying Helm charts, which manages and deploys Helm releases via a simple, unified YAML file. [Installing Helmfile](https://helmfile.readthedocs.io/en/latest/#installation)
* **Helm**: A package manager for Kubernetes, used to define, install, and upgrade complex Kubernetes applications. [Installing Helm](https://helm.sh/docs/intro/install/)
* **kubectl**: A command-line tool for interacting with Kubernetes cluster, allowing you to deploy applications, manage cluster resources, and view logs. [Installing Kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)
