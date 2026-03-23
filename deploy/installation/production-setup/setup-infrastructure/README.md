---
description: Setup infrastructure required for deploying DIGIT HCM
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/installation/production-setup/infrastructure-setup
---

# Setup Infrastructure

## Overview

DIGIT HCM can be deployed on a public cloud like AWS, Azure, GCP or a private cloud.

## Pre-reads

* Learn the basics of Kubernetes: [https://www.youtube.com/watch?v=PH-2FfFD2PU\&t=3s](https://www.youtube.com/watch?v=PH-2FfFD2PU\&t=3s)
* Learn the [basics of kubectl](https://www.tutorialspoint.com/kubernetes/kubernetes_kubectl_commands.htm) commands

{% hint style="info" %}
<mark style="color:orange;">**Note:**</mark> To deploy DIGIT HCM using GitHub Actions, refer to the document - [DIGIT Deployment Using GitHub Actions](../../install-using-github-actions-in-aws.md). With this installation approach, there's no need to manually create the infrastructure, as GitHub Actions will automatically handle the creation and deployment of DIGIT.
{% endhint %}

Choose your cloud and follow the instructions to set up a Kubernetes cluster before deploying.

{% content-ref url="aws/" %}
[aws](aws/)
{% endcontent-ref %}

{% content-ref url="azure/" %}
[azure](azure/)
{% endcontent-ref %}

{% content-ref url="google-cloud-platform-gcp/" %}
[google-cloud-platform-gcp](google-cloud-platform-gcp/)
{% endcontent-ref %}
