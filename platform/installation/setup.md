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

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 9.45.01 AM.png" alt=""><figcaption></figcaption></figure>

* Run the following command:&#x20;

&#x20;     curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"

&#x20;     sudo installer -pkg AWSCLIV2.pkg -target /

* Verify if the installation is done -&#x20;

&#x20;     Which AWS

&#x20;     AWS – version

* Run the command: aws configure –profile=”health-eGov”
* A profile is required for multi-account setup.
* Make note of whatever profile name one has given.

<figure><img src="../../.gitbook/assets/Screenshot 2023-03-14 at 9.25.05 AM.png" alt=""><figcaption></figcaption></figure>

* Add the AWS key, which was created earlier.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.06.55 AM.png" alt=""><figcaption></figcaption></figure>

* Add the AWS secret key, which was created earlier.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.21.30 AM.png" alt=""><figcaption></figcaption></figure>

* Add the default region name as “ap-south-1”.&#x20;
* This is the Mumbai region of AWS for data centres. The infrastructure will be deployed here.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.25.10 AM.png" alt=""><figcaption></figcaption></figure>

* Add the output format as JSON.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.35.01 AM.png" alt=""><figcaption></figcaption></figure>

* Verify if you have successfully configured AWS.
* Run the command: aws ls s3 –profile=”health-eGov”
* If you get a list of bucket names, then the CLI is configured successfully

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.41.16 AM.png" alt=""><figcaption></figcaption></figure>

### Steps to Create AWS KMS Key for SOPS

* Search KMS on the top of the search bar.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.43.19 AM.png" alt=""><figcaption></figcaption></figure>

* Click on the “Create Key” on the top right.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.44.36 AM.png" alt=""><figcaption></figcaption></figure>

* Configure the key. We used the symmetric key and the encrypt and decrypt as usage. There are advanced options as well.&#x20;
* Click on ‘Next’.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.46.26 AM.png" alt=""><figcaption></figcaption></figure>

* Give an alias and description.&#x20;
* Click on ‘Next’.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.47.49 AM.png" alt=""><figcaption></figcaption></figure>

* Select the administrative permission. Ideally, it should be only env-based.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.53.59 AM.png" alt=""><figcaption></figcaption></figure>

* Select the key usage permission. Ideally, it should be only env-based.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.54.45 AM.png" alt=""><figcaption></figcaption></figure>

* Review the keys.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.56.52 AM.png" alt=""><figcaption></figcaption></figure>

* The key will be generated.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.58.04 AM (1).png" alt=""><figcaption></figcaption></figure>

* You can copy the Amazon Resource Name (ARN).

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-22 at 10.58.50 AM.png" alt=""><figcaption></figcaption></figure>

Encrypting and decrypting file with SOPS

❯ export SOPS\_KMS\_ARN=arn:aws:kms:ap-south-1:680148267093:key/4cc5ed9f-75c7-43ef-a6bb-b36c03c5b5e8

❯ export AWS\_PROFILE=health-eGov

❯ export AWS\_SDK\_LOAD\_CONFIG=1

❯sops -e -i health-dev-secrets.yaml

```
>sops -d -i health-dev-secrets.yaml
```



[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
