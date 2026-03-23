---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/installation/production-setup/installing-monitoring-stack
---

# Install Monitoring Stack

## Overview

This page explains how to upgrade monitoring services in a Kubernetes cluster—Grafana for dashboards, Loki for logs, and Prometheus for metrics and alerts. It walks you through the upgrade steps using Helmfile and the required configurations.

## Prerequisites <a href="#prerequisites" id="prerequisites"></a>

Before proceeding with the upgrade, ensure you have the following tools installed and configured:

* **Helmfile**: A declarative spec for deploying Helm charts, which manages and deploys Helm releases via a simple, unified YAML file. [Installing Helmfile](https://helmfile.readthedocs.io/en/latest/#installation)
* **Helm**: A package manager for Kubernetes, used to define, install, and upgrade complex Kubernetes applications. [Installing Helm](https://helm.sh/docs/intro/install/)
* **kubectl**: A command-line tool for interacting with a Kubernetes cluster, allowing you to deploy applications, manage cluster resources, and view logs. [Installing Kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)

## Steps

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><ol><li><strong>Configure Stack</strong></li></ol></td><td><a href="1.-configure.md">1.-configure.md</a></td></tr><tr><td><ol start="2"><li><strong>Deploy Stack</strong></li></ol></td><td><a href="2.-deploy.md">2.-deploy.md</a></td></tr></tbody></table>

