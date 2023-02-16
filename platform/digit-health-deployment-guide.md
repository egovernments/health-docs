# DIGIT Health Deployment Guide

## Prerequisites&#x20;

Access needed to the following:&#x20;

* Github&#x20;
* eGoV email Id&#x20;
* Jenkins: https://builds.digit.org

## Deployment Stage 1: Build

### Steps for Building the image

* Click on ‘builds’.
* Visit [https://builds.digit.org/](https://builds.digit.org/) &#x20;

<figure><img src="../.gitbook/assets/Screenshot 2023-02-16 at 2.03.24 PM.png" alt=""><figcaption></figcaption></figure>

* Search for “health-campaign-services”.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-16 at 2.04.54 PM.png" alt=""><figcaption></figcaption></figure>

* Select the relevant service.
* All services which are created for the health campaign are in “Health-services”.
* If the service is not present, add it in the build files of the repo. The dev team should have added this already.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-16 at 2.05.55 PM.png" alt=""><figcaption></figcaption></figure>

* Select the service to build.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-16 at 2.07.14 PM.png" alt=""><figcaption></figcaption></figure>

* Click on “Build with Parameters”.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-16 at 2.08.00 PM.png" alt=""><figcaption></figcaption></figure>

* You will see a list of branches available for Github
* For QA, search ‘qa’.&#x20;
* Select “origin/qa”.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-16 at 2.09.22 PM.png" alt=""><figcaption></figcaption></figure>

* Click on ‘Build’.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-16 at 2.10.59 PM.png" alt=""><figcaption></figcaption></figure>

* This will trigger the build. The latest build will be on the top of the list.&#x20;
* Click on the top of the list to check for the build logs.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-16 at 2.11.56 PM.png" alt=""><figcaption></figcaption></figure>

* You will see multiple options.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-16 at 2.12.52 PM.png" alt=""><figcaption></figcaption></figure>

* Click on “Console Output”.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-16 at 2.14.14 PM.png" alt=""><figcaption></figcaption></figure>

* If the build is successful, you will see the following message: “Finished: SUCCESS”.

<figure><img src="../.gitbook/assets/Screenshot 2023-02-16 at 2.15.23 PM.png" alt=""><figcaption></figcaption></figure>











