---
description: HCM deployment guide
---

# Setup

## Prerequisites&#x20;

Access needed to the following:&#x20;

* Github&#x20;
* eGoV email Id&#x20;
* Jenkins: https://builds.digit.org

### Deployment Stages:

[Stage 1: Build](./#deployment-stage-1-build)

[Stage 2: Deploy](./#deployment-stage-2-deploy)

## Deployment Stage 1: Build

### Steps for building the image

* Click on ‘builds’.
* Visit [https://builds.digit.org/](https://builds.digit.org/) &#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.03.24 PM.png" alt=""><figcaption></figcaption></figure>

* Search for “health-campaign-services”.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.04.54 PM.png" alt=""><figcaption></figcaption></figure>

* Select the relevant service.
* All services which are created for the health campaign are in “Health-services”.
* If the service is not present, add it in the build files of the repo. The dev team should have added this already.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.05.55 PM.png" alt=""><figcaption></figcaption></figure>

* Select the service to build.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.07.14 PM.png" alt=""><figcaption></figcaption></figure>

* Click on “Build with Parameters”.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.08.00 PM.png" alt=""><figcaption></figcaption></figure>

* You will see a list of branches available for Github
* For QA, search ‘qa’.&#x20;
* Select “origin/qa”.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.09.22 PM.png" alt=""><figcaption></figcaption></figure>

* Click on ‘Build’.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.10.59 PM.png" alt=""><figcaption></figcaption></figure>

* This will trigger the build. The latest build will be on the top of the list.&#x20;
* Click on the top of the list to check for the build logs.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.11.56 PM.png" alt=""><figcaption></figcaption></figure>

* You will see multiple options.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.12.52 PM.png" alt=""><figcaption></figcaption></figure>

* Click on “Console Output”.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.14.14 PM.png" alt=""><figcaption></figcaption></figure>

* If the build is successful, you will see the following message: “Finished: SUCCESS”.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.15.23 PM.png" alt=""><figcaption></figcaption></figure>

* Scroll up to see the image name, which has been pushed: docker.io/egovio/household:qa-efb0e0ac09-20 pushed successfully!&#x20;
* Copy household:qa-efb0e0ac09-20.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.17.20 PM.png" alt=""><figcaption></figcaption></figure>

## Deployment Stage 2: Deploy

### Steps for deploying on QA

* Visit https://builds.digit.org/.&#x20;
* Click on deployments.
*

    <figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.22.04 PM.png" alt=""><figcaption></figcaption></figure>
* Select the environment where you want to deploy.&#x20;
* For QA, click on “deploy-to-health-qa”.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.22.49 PM.png" alt=""><figcaption></figcaption></figure>

* Click on “Build with Parameters”.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.24.39 PM.png" alt=""><figcaption></figcaption></figure>

* Click on ‘Build’.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.25.21 PM.png" alt=""><figcaption></figcaption></figure>

* Paste the image name from the build step and paste it in the text box.&#x20;
* Cluster Config: If there is a change at the infra level or it is the first deployment for the service on the infra, select this check box: default keep it unchecked.&#x20;
* Click on ‘Build’.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.27.26 PM.png" alt=""><figcaption></figcaption></figure>

* You will see the latest deployment in progress on the top of the deployment list.&#x20;
* Click on the top to see the deployment logs.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.27.55 PM.png" alt=""><figcaption></figcaption></figure>

* This will show the Git data.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.28.57 PM.png" alt=""><figcaption></figcaption></figure>

* Click on “Console Output”.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.29.27 PM.png" alt=""><figcaption></figcaption></figure>

* If the deployment is successful in the logs, you will see the following message: “Finished: SUCCESS”.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-16 at 2.30.22 PM.png" alt=""><figcaption></figcaption></figure>

* Check the status of Kubernetes to verify if the new pod is running or not.



[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
