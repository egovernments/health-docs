---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/installation/install-using-github-actions-in-aws
---

# Install Using GitHub Actions in AWS

## **Prerequisites**

Before you begin, ensure you have the following:\
✅ GitHub account (to fork repositories and manage workflows)\
✅ AWS account (to deploy infrastructure)\
✅ AWS CLI installed (for authentication & deployment)\
✅ Kubectl installed (for managing Kubernetes)\
✅ Postman installed (for API testing)\
✅ Domain hosting provider (e.g., GoDaddy) for server domain configuration.

## Steps

{% stepper %}
{% step %}
### **Install AWS**

* Prepare AWS IAM User
* Create an IAM User in your AWS account.
* Generate ACCESS\_KEY and SECRET\_KEY for the IAM user.
* Assign administrator access to the IAM user.
* **Use the below command to set up the AWS profile locally:**

```
aws configure --profile {profilename}
```

* Fill in the key values at the respective prompts

```
 AWS_ACCESS_KEY_ID: <GENERATED_ACCESS_KEY>
 AWS_SECRET_ACCESS_KEY: <GENERATED_SECRET_KEY>
 AWS_DEFAULT_REGION: ap-south-1
 export AWS_PROFILE={profilename}
```

* Ensure the AWS Account has S3 Bucket access to the Filestore service.
{% endstep %}

{% step %}
### **Fork GitHub Repositories**

Fork the following repositories into your GitHub account:\
✅ [Health-campaign-devops](https://github.com/egovernments/health-campaign-devops)\
✅ [Configs](https://github.com/egovernments/health-campaign-config)
{% endstep %}

{% step %}
### Add AWS Keys to GitHub Repository

* Go to the forked health-campaign-devops repository and navigate to the repository settings.

<div align="left"><figure><img src="../../.gitbook/assets/image (214).png" alt="" width="375"><figcaption></figcaption></figure></div>

* Navigate to Secrets and Variables.

<div align="left"><figure><img src="../../.gitbook/assets/image (217).png" alt="" width="375"><figcaption></figcaption></figure></div>

* Add the following secrets under repository secrets:

```
AWS_ACCESS_KEY_ID: <GENERATED_ACCESS_KEY>
AWS_SECRET_ACCESS_KEY: <GENERATED_SECRET_KEY>
AWS_DEFAULT_REGION: ap-south-1
AWS_REGION: ap-south-1
```

<figure><img src="../../.gitbook/assets/image (219).png" alt=""><figcaption></figcaption></figure>

* Ensure AWS keys are added to the forked DevOps repository.
{% endstep %}

{% step %}
### Enable GitHub Actions

* Navigate to the **release-githubactions** branch in the forked DevOps repository.
*   **Enable GitHub Actions.**

    Click on **Actions,** then click on "**I understand my workflows, go ahead and enable them":**

<div><figure><img src="../../.gitbook/assets/Screenshot 2024-08-01 at 4.55.18 PM.png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2024-08-01 at 4.55.53 PM.png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Modify Configuration Files

{% hint style="info" %}
**Note:** Make these repository/branch changes before installation; making changes to the configuration repository link in the DevOps repository after installation without understanding what impact they may have will lead to failure in the application functionality.
{% endhint %}

* Navigate to egov-demo.yaml (**config-as-code/environments/egov-demo.yaml**).
* Under the **egov-persister:** change the **gitsync** link of the **health-campaign-config** repository to the forked config repository and the branch to **DEMO.**
* Under the **egov-indexer:** change the **gitsync** link of the **health-campaign-config** repository to the forked config repository and the branch to **DEMO.**

<figure><img src="../../.gitbook/assets/image (220).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (221).png" alt=""><figcaption></figcaption></figure>

* Under the **pdf-service**: change the **git-sync** link of the **health-campaign-config** repository to the forked config repository and the branch to **DEMO.**
{% endstep %}

{% step %}
### Configure Infrastructure-as-code

* Navigate to infra-as-code/terraform/sample-aws.
* Open input.yaml and enter details such as **domain\_name**, **cluster\_name**, **bucket\_name**, and **db\_name**.

<figure><img src="../../.gitbook/assets/Screenshot from 2025-02-13 11-52-20.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Configure HCM Version&#x20;

* Navigate to the file `deploy-as-code/deployer/digit_installer.go`
* Search for `health-demo` in the file and check for health-demo-vX.X
* Change the version to v1.7 -> `health-demo-v1.7`&#x20;

<figure><img src="../../.gitbook/assets/image (149).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Enable HCM Module

* Navigate to the file `deploy-as-code/deployer/digit_installer.go`&#x20;
* Search for `m_health` , and add this below this line `selectedMod = append(selectedMod, "m_pgr")`&#x20;

<figure><img src="../../.gitbook/assets/Screenshot from 2024-08-23 16-07-12.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Generate SSH Key Pair

* **Method A: Navigate to** [**this** website ](https://8gwifi.org/sshfunctions.jsp)to generate the SSH Key Pair. _(Note: This is not recommended for production setups, only for demo purposes.)_
* **Method B:** Use OpenSSL commands:&#x20;
  * `openssl genpkey -algorithm RSA -out private_key.pem`&#x20;
  * `ssh-keygen -y -f private_key.pem > ssh_public_key`
  * To view the key, run the commands or use any text editor to open the files
    * `vi private_key.pem`
    * `vi ssh_public_key`
* Once generated, navigate to config-as-code/environments
* Open egov-demo-secrets.yaml
* Search for `PRIVATE KEY` and replace  `-----BEGIN RSA PRIVATE KEY-----` to `-----BEGIN RSA PRIVATE KEY-----` with private\_key generated&#x20;

{% hint style="info" %}
**Note**: Make sure the private key is indented as given
{% endhint %}

* Add the public key to your GitHub account.
{% endstep %}

{% step %}
### Trigger Installation

🔹 Push all changes to GitHub.\
🔹 Navigate to GitHub Actions and check the workflow.\
🔹 Ensure the installation runs successfully.
{% endstep %}

{% step %}
### Configure Domain Name

* Connect to the Kubernetes cluster from your local machine using the command below:

```
aws eks update-kubeconfig --region ap-south-1 --name $CLUSTER_NAME
```

* Get the CNAME of the _nginx-ingress-controller_

```shell
kubectl get svc nginx-ingress-controller -n egov -o jsonpath='{.status.loadBalancer.ingress[0].hostname}'
```

*   The output of this will be something like this:&#x20;

    &#x20;[ae210873da6ff4c03bde2ad22e18fe04-233d3411.ap-south-1.elb.amazonaws.com](http://ae210873da6ff4c03bde2ad22e18fe04-233d3411.ap-south-1.elb.amazonaws.com/)<br>
* Add the displayed CNAME to your domain provider against your domain name. e.g. GoDaddy domain provider&#x20;
{% endstep %}

{% step %}
### Enable Filestore Service

* After connecting to the Kubernetes cluster, edit the deployment of the FileStore service using the following command:

```
export KUBE_EDITOR='code --wait'
kubectl edit deployment egov-filestore -n egov
```

* The deployment.yaml for Filestore Service  will open in VS Code, add the AWS key and secret key provided to you in the way shown below:

<div align="left"><figure><img src="../../.gitbook/assets/image (369).png" alt=""><figcaption></figcaption></figure></div>

Close the deployment.yaml file opened in your VS Code editor. The deployment is updated.
{% endstep %}
{% endstepper %}
