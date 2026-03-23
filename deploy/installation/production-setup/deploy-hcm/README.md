---
description: High-level overview of DIGIT HCM deployment
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/installation/production-setup/deploy-hcm
---

# Deploy HCM

## Basics

DIGIT is an open-source, customizable platform that lends itself to extensibility. New modules can be built on top of the platform to suit new use-cases, or existing modules can be modified or replaced. To enable this, in addition to deploying DIGIT, a CI/CD pipeline should be set up. CD/CI pipelines enable the end user to automate & simplify the build/deploy process.

DIGIT comes with configurable "CI as code", "Deploy as code", etc.. which can be utilized to set up the pipelines and deploy new modules. More on that in the steps below.

<mark style="color:orange;">**Note: Changing the DIGIT code has implications for upgrades. That is, you may not be able to upgrade to the latest version of DIGIT depending on the changes that have been made. New modules are generally not a problem for upgrades.**</mark>

## Pre-reads

* Find out more on Kubernetes manifests: [https://www.youtube.com/watch?v=ohSUtEfDefc](https://www.youtube.com/watch?v=ohSUtEfDefc)
* Learn how to manage env values, secrets of any service deployed in Kubernetes [https://www.youtube.com/watch?v=OW244LxB4oI](https://www.youtube.com/watch?v=OW244LxB4oI)
* Explore how to port forward to a pod running inside a k8s cluster and work locally [https://www.youtube.com/watch?v=TT3nd5n5Yus](https://www.youtube.com/watch?v=TT3nd5n5Yus)
* Find the SOPs to secure your keys/creds: [https://www.youtube.com/watch?v=DWzJ87KbwxA](https://www.youtube.com/watch?v=DWzJ87KbwxA)

