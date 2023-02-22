---
description: Developer machine setup
---

# Setup

## Required Softwares

* Terraform 0.14.10
* Helm ([https://helm.sh/docs/intro/install/](https://helm.sh/docs/intro/install/))
* Golang ([https://go.dev/doc/install](https://go.dev/doc/install))
* Kubectl (https://kubernetes.io/docs/tasks/tools/)
* AWS CLI (Steps setup)
* SOPs ([https://github.com/mozilla/sops](https://github.com/mozilla/sops))

Note: You need to be admin for configuration, MDMS and services for github keys. Else, you will get an error after deployment as MDMS is not able to pull data on the Kubernetes cluster.&#x20;

## Pre-Steps

### Setup AWS CLI

If you need to set up AWS CLI on the machine, the following commands assume that you are using a Macbook:

* Go to following site: [https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

<figure><img src="../.gitbook/assets/Screenshot 2023-02-22 at 9.45.01 AM.png" alt=""><figcaption></figcaption></figure>

* Run the following command:&#x20;

&#x20;     curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"

&#x20;     sudo installer -pkg AWSCLIV2.pkg -target /

* Verify if the installation is done -&#x20;

&#x20;     Which AWS

&#x20;     AWS – version

* Run the command: aws configure –profile=”health-eGov”
* A profile is required for multi-account setup.
* Make note of whatever profile name one has given.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-22 at 9.54.46 AM.png" alt=""><figcaption></figcaption></figure>

* Add the AWS key, which was created earlier.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-22 at 10.06.55 AM.png" alt=""><figcaption></figcaption></figure>

* Add the AWS secret key, which was created earlier.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-22 at 10.21.30 AM.png" alt=""><figcaption></figcaption></figure>

* Add the default region name as “ap-south-1”.&#x20;
* This is the Mumbai region of AWS for data centres. The infrastructure will be deployed here.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-22 at 10.25.10 AM.png" alt=""><figcaption></figcaption></figure>

* Add the output format as JSON.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-22 at 10.35.01 AM.png" alt=""><figcaption></figcaption></figure>

* Verify if you have successfully configured AWS.
* Run the command: aws ls s3 –profile=”health-eGov”
* If you get a list of bucket names, then the CLI is configured successfully

<figure><img src="../.gitbook/assets/Screenshot 2023-02-22 at 10.41.16 AM.png" alt=""><figcaption></figcaption></figure>



\








\




##

\


\










[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
