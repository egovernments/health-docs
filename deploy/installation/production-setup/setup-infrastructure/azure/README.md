---
description: Provision infra for DIGIT HCM on Azure using Terraform
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/installation/production-setup/infrastructure-setup/azure
---

# Azure

## Overview

[Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/) manages your hosted Kubernetes environment. AKS enables you to deploy and manage containerised applications without requiring container orchestration expertise. AKS also enables you to do many common maintenance operations without taking your app offline. These operations include provisioning, upgrading, and scaling resources on demand.

<figure><img src="../../../../../.gitbook/assets/image (485).png" alt=""><figcaption></figcaption></figure>

## Installation Steps

{% content-ref url="1.-azure-pre-requisites.md" %}
[1.-azure-pre-requisites.md](1.-azure-pre-requisites.md)
{% endcontent-ref %}

{% content-ref url="2.-infra-as-code-terraform.md" %}
[2.-infra-as-code-terraform.md](2.-infra-as-code-terraform.md)
{% endcontent-ref %}
