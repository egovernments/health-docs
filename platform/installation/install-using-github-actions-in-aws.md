---
description: Installation Guide for DIGIT-HEALTH via GitHub Actions in AWS
---

# Install Using GitHub Actions in AWS

## Overview

This guide provides step-by-step instructions for installing DIGIT using GitHub Actions in an AWS environment.

## **Pre-requisites**

AWS account

Github account

## **Install**

* Prepare AWS IAM User
* Create an IAM User in your AWS account.
* Generate ACCESS\_KEY and SECRET\_KEY for the IAM user.
* Assign Administrator Access to the IAM user for necessary permissions.

### **Configure GitHub Repository**

* Fork the Repository into your organization account on GitHub.
* Navigate to the repository settings, then to Secrets and Variables, and add the following repository secrets:
* AWS\_ACCESS\_KEY\_ID: \<GENERATED\_ACCESS\_KEY>
* AWS\_SECRET\_ACCESS\_KEY: \<GENERATED\_SECRET\_KEY>
* AWS\_DEFAULT\_REGION: ap-south-1
* AWS\_REGION: ap-south-1

### **Changes to be made in the Repository**

* Navigate to the Kubernetes-1.27 branch.
* Enable GitHub Actions.
* Open the GitHub Actions workflow file.
* Specify the branch name you wish to enable GitHub Actions for.
* Configure Infrastructure-as-Code.
* Navigate to infra-as-code/terraform/sample-aws.
* Open input.yaml and enter details such as domain\_name, cluster\_name, bucket\_name, and db\_name.
* Configure Application Secrets.
* Navigate to config-as-code/environments.
* Open egov-demo-secrets.yaml.
* Enter db\_password and ssh\_private\_key. Add the public\_key to your GitHub account.
* Generate SSH Key Pair.
* Choose one of the following methods to generate an SSH key pair:&#x20;
  1. **Method a:** Use an online website. (Note: This is not recommended for production setups, only for demo purposes): [https://8gwifi.org/sshfunctions.jsp](https://8gwifi.org/sshfunctions.jsp)&#x20;
  2. **Method b:** Use OpenSSL commands: openssl genpkey -algorithm RSA -out private\_key.pem openssl rsa -pubout -in private\_key.pem -out public\_key.pem

### **Finalize Installation**

* Once all details are entered, push these changes to the remote GitHub repository. Open the Actions tab in your GitHub account to view the workflow. You should see that the workflow has started, and the pipelines are completed successfully.

### **Create Superuser**

* Connect to the Kubernetes cluster, from your local machine using (aws eks update-kubeconfig --region ap-south-1 --name $CLUSTER\_NAME) and run the below command
* kubectl port-forward svc/egov-user -n egov 8080:8080

Run the below curl in another window:

```
curl --location 'http://localhost:8080/user/users/_createnovalidate'
--header 'Content-Type: application/json'
--data-raw '{ "requestInfo": { "apiId": "Rainmaker", "ver": ".01", "ts": null, "action": "_update", "did": "1", "key": "", "msgId": "20170310130900|en_IN", "authToken": "51e00caf-3218-4f15-ba70-a45f7d40abc1" }, "user": { "userName": "<>", "name": "Admin User", "gender": null, "mobileNumber": "9898989898", "type": "EMPLOYEE", "active": true, "password": "<>", "roles": [ { "name": "Super User", "code": "SUPERUSER", "tenantId": "mz" } ], "emailId": "xyz@gmail.com", "tenantId": "mz" } }'
```

## **DIGIT Infrastructure - Cleanup & Uninstallation**

As you wrap up your work with DIGIT, ensuring a smooth and error-free cleanup of the resources is crucial. The regular monitoring of the GitHub Actions workflow's output is essential during the destruction process. Watch out for any error messages or signs of issues. A successful job completion will be confirmed by a success message in the GitHub Actions window, indicating that the infrastructure has been effectively destroyed.&#x20;

When you're ready to remove DIGIT and clean up the resources it created, proceed with executing the terraform\_infra\_destruction job. This action is designed to dismantle all set up resources, clearing the environment neatly. We hope your experience with DIGIT was positive and that this guide makes the uninstallation process straightforward.

**Steps to run the Terraform Infrastructure Destruction job**

To initiate the destruction of a Terraform-managed infrastructure, follow these steps:

* Navigate to Actions.
* Click DIGIT-Install workflow.
* Select Run workflow.
* When prompted, type "destroy". This action starts the terraform\_infra\_destruction job.
* You can observe the progress of the destruction job in the actions window.
