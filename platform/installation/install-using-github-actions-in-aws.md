---
description: Installation Guide for DIGIT-HEALTH via GitHub Actions in AWS
---

# Install Using GitHub Actions in AWS

## Overview

This guide provides step-by-step instructions for installing DIGIT using GitHub Actions in an AWS environment.

## **Pre-requisites**

* Github account
* Kubectl installed in the system - [installation guide](https://kubernetes.io/docs/tasks/tools/)
* AWS account
* Install AWS CLI locally - [installation guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
* Postman - [installation guide](https://learning.postman.com/docs/getting-started/installation/installation-and-updates/)

## **Install**

* Prepare AWS IAM User
* Create an IAM User in your AWS account - [official document](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_users\_create.html)
* Generate ACCESS\_KEY and SECRET\_KEY for the IAM user - [AWS document](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_access-keys.html)
* Assign administrator access to the IAM user for necessary permissions.
* **Set up the AWS profile locally by running the following commands**
  * aws configure --profile {profilename}
  * fill in the key values as they are prompted&#x20;
    * AWS\_ACCESS\_KEY\_ID: \<GENERATED\_ACCESS\_KEY>
    * AWS\_SECRET\_ACCESS\_KEY: \<GENERATED\_SECRET\_KEY>
    * AWS\_DEFAULT\_REGION: ap-south-1
  * export AWS\_PROFILE={profilename}

## **Configure GitHub Repository**

* **Fork** the following Repositories with all the branches into your organisation account on GitHub - [official documentation](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo).
  * [Health-campaign-devops](https://github.com/egovernments/health-campaign-devops)
  * [Master data](https://github.com/egovernments/health-campaign-mdms)
  * [configs](https://github.com/egovernments/health-campaign-config)
* **Adding AWS key to the repository**&#x20;
  * Go to the forked health-campaign-devops repository
  * Navigate to the repository settings
  * Then to Secrets and Variables
  * Then click on actions options below secrets and variables
  * On the new page, choose the new Repository secret option in Repository secrets and add the following keys mentioned below
    * AWS\_ACCESS\_KEY\_ID: \<GENERATED\_ACCESS\_KEY>
    * AWS\_SECRET\_ACCESS\_KEY: \<GENERATED\_SECRET\_KEY>
    * AWS\_DEFAULT\_REGION: ap-south-1
    * AWS\_REGION: ap-south-1

### **Changes to be made in the repository**

* Navigate to the Kubernetes-1.27 branch in the forked DevOps Repository
* Enable GitHub Actions
  * click on **Actions** then click on **I understand my workflows, go ahead and enable them**

**How to Edit the Github Files**&#x20;

* The following steps can be done either directly in the browser or the local system if you are familiar with git usage
* Before following any of the steps switch to the  kubernetes-1.27 branch
* Steps to edit the git repository in the browser - [Git guide](https://docs.github.com/en/codespaces/the-githubdev-web-based-editor#opening-the-githubdev-editor)
* Steps to edit in the local system if you are familiar with Git basics
  * Git clone {forked DevOps repolink}
  * Follow the below steps and make changes
  * Then commit and push to the kubernetes-1.27 branch
* **NOTE:** Complete all changes at once then commit and push the code to remote to trigger the installation.

**Configure master and config data**

* **Note: -** make these repository/Branch changes before installation, changes to the repository after installation without working understanding will lead to failure in the application functionality.
* navigate to egov-demo.yaml (**config-as-code/environments/egov-demo.yaml**)
*   Under the **egov-mdms-service:** **initContainers:** change the **gitsync** repository link of master data to the master data repository you forked  and the branch to **DEMO** (The branch also can be changed based on your choice)&#x20;

    <div align="left" data-full-width="false">

    <figure><img src="../../.gitbook/assets/Screenshot 2024-04-03 at 11.29.48 AM.png" alt="" width="563"><figcaption></figcaption></figure>

    </div>
* Under the **egov-persister:** change the **gitsync** link of the **health-campaign-config** repository to the forked config repository and the branch to **DEMO**
*   Under the **egov-indexer:** change the gitsync link of the **health-campaign-config** repository to the forked config repository and the branch to **DEMO**&#x20;

    <div align="left">

    <figure><img src="../../.gitbook/assets/Screenshot 2024-04-03 at 11.30.33 AM.png" alt="" width="563"><figcaption></figcaption></figure>

    </div>

**Configure Infrastructure-as-Code**

* Navigate to infra-as-code/terraform/sample-aws.
* Open input.yaml and enter details such as domain\_name, cluster\_name, bucket\_name, and db\_name.

**Configure Application Secrets**

* Generate SSH key pair
* How to Generate SSH Key Pair - choose one of the following methods to generate an SSH key pair:&#x20;
  * **Method a:** Use an online website. (Note: This is not recommended for production setups, only for demo purposes): [https://8gwifi.org/sshfunctions.jsp](https://8gwifi.org/sshfunctions.jsp)&#x20;
  * **Method b:** Use OpenSSL commands:&#x20;
    * OpenSSL genpkey -algorithm RSA -out private\_key.pem&#x20;
    * openssl rsa -pubout -in private\_key.pem -out public\_key.pem
    * To view the key run the commands or use any text editor to open the files
      * vi private\_key.pem
      * vi public\_key.pem&#x20;
* Once generated Navigate to config-as-code/environments
* Open egov-demo-secrets.yaml
* Replace ssh\_private\_key (**note**: please make sure private key is intended as given)&#x20;
* Add the public\_key to your GitHub account - [Git guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

### **Finalise Installation**

* Once all details are entered, push these changes to the remote GitHub repository. Open the Actions tab in your GitHub account to view the workflow. You should see that the workflow has started, and the pipelines are completed successfully.

**Configuring the domain name**

* Once the deployment is done get the CNAME of the _nginx-ingress-controller_

```shell
kubectl get svc ingress-nginx-controller -n egov -o jsonpath='{.status.loadBalancer.ingress[0].hostname}'
```

*   The output of this will be something like this:&#x20;

    &#x20;[ae210873da6ff4c03bde2ad22e18fe04-233d3411.ap-south-1.elb.amazonaws.com](http://ae210873da6ff4c03bde2ad22e18fe04-233d3411.ap-south-1.elb.amazonaws.com/)\

* Add the displayed CNAME to your domain provider against your domain name.

### **Create Superuser**

* Connect to the Kubernetes cluster, from your local machine by using  the cmd
* aws eks update-kubeconfig --region ap-south-1 --name $CLUSTER\_NAME
* connect to user service by running th ebelow cmd
* kubectl port-forward svc/egov-user -n egov 8080:8080

Run the below curl in another window:

```json
curl --location 'http://localhost:8080/user/users/_createnovalidate'
--header 'Content-Type: application/json'
--data-raw '{ "requestInfo": { "apiId": "Rainmaker", "ver": ".01", "ts": null, "action": "_update", "did": "1", "key": "", "msgId": "20170310130900|en_IN", "authToken": "51e00caf-3218-4f15-ba70-a45f7d40abc1" }, "user": { "userName": "<>", "name": "Admin User", "gender": null, "mobileNumber": "9898989898", "type": "EMPLOYEE", "active": true, "password": "<>", "roles": [ { "name": "Super User", "code": "SUPERUSER", "tenantId": "mz" } ], "emailId": "xyz@gmail.com", "tenantId": "mz" } }'
```

Replace username, password and tenantId with proper values(keep tenantid as 'mz' if master data is unchanged).

## **DIGIT Infrastructure - Cleanup & Uninstallation**

As you wrap up your work with DIGIT, ensuring a smooth and error-free cleanup of the resources is crucial. The regular monitoring of the GitHub Actions workflow's output is essential during the destruction process. Watch out for any error messages or signs of issues. A successful job completion will be confirmed by a success message in the GitHub Actions window, indicating that the infrastructure has been effectively destroyed.&#x20;

When you're ready to remove DIGIT and clean up the resources it created, proceed with executing the terraform\_infra\_destruction job. This action is designed to dismantle all setup resources, clearing the environment neatly. We hope your experience with DIGIT was positive and that this guide makes the uninstallation process straightforward.

**Steps to run the Terraform Infrastructure Destruction job**

To initiate the destruction of a Terraform-managed infrastructure, follow these steps:

* Navigate to Actions.
* Click DIGIT-Install workflow.
* Select Run workflow.
* When prompted, type "destroy". This action starts the terraform\_infra\_destruction job.
* You can observe the progress of the destruction job in the actions window.
