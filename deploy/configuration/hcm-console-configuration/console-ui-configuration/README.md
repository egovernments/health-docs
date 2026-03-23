---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-console-configuration/console-ui-configuration
---

# Console UI Configuration

## **Overview** <a href="#overview" id="overview"></a>

This page offers details of the DIGIT UI configuration required to enable it in any environment. Browse through the configuration details listed below:

* [Build configuration](./#build-configuration)
* [Helmchart configuration](./#helmchart-configuration)
* [Environment configuration](./#environment-configuration)
* [Global configuration](./#global-configuration)
* [AWS S3 Bucket configuration](./#aws-s3-bucket-configuration)

## **DevOps Configuration** <a href="#devops-configuration" id="devops-configuration"></a>

### **Build Configuration** <a href="#build-configuration" id="build-configuration"></a>

eGov recommends [CD/CI be set up](https://urban.digit.org/installation/jenkins-setup) before developing on top of DIGIT. This ensures that new modules can be developed and deployed in a streamlined way. DIGIT ships with CI as code as part of the DevOps repository. Run the [CI installer to set up DIGIT CD/CI](https://urban.digit.org/installation/jenkins-setup) before developing it on DIGIT.

**Step 1:** Add an entry in build-config.yaml file in the **master** branch of the forked repository. This will set up the job pipeline in Jenkins. Make sure to add the same config to the feature branch you are working on. Refer to [build-config.yaml](https://github.com/egovernments/DIGIT-Frontend/blob/4971c2d4f4b53428867366d8e5554242e0d7e9db/build/build-config.yml#L48).

Add the below content for digit-ui.

```
# Health Frontend Build pipelines
  - name: builds/Digit-Frontend/health/workbench-ui
    build:
      - work-dir: health/micro-ui/
        dockerfile: health/micro-ui/web/workbench/Dockerfile
        image-name: workbench-ui
```

**Step 2:** Go to the Jenkins build page, select "Job Builder" and click on "Build now". This will pull the config from build\_config.yaml and identify all modules that need to be built.

**Step 3**: Go to your Jenkins build page once the build is done. The service will appear under the repository path in which it has been added, that is, if the service is added under frontend, it will show up in the frontend section as below,

<figure><img src="https://core.digit.org/~gitbook/image?url=https%3A%2F%2F3868804918-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FegsIWleSdyH9rMLJ8ShI%252Fuploads%252Fgit-blob-a3b47ce6ab0837552b7a247c2e951e9254362b97%252FScreenshot%25202023-06-13%2520at%252012.10.44%2520PM.png%3Falt%3Dmedia&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=f6d7f930&#x26;sv=2" alt=""><figcaption><p>build ui docker image from jenkins</p></figcaption></figure>

**To learn more about the** [**build**](https://core.digit.org/guides/developer-guide/ui-developer-guide/build-and-deploy#build) **and** [**deployment**](https://core.digit.org/guides/developer-guide/ui-developer-guide/build-and-deploy#deploy) **process, visit:**

[Build & Deploy](https://core.digit.org/guides/developer-guide/ui-developer-guide/build-and-deploy)

### **Helmchart Configuration** <a href="#helmchart-configuration" id="helmchart-configuration"></a>

**Step 1:** Add an entry in the helm chart of the frontend directory in the **master** branch of the forked [DIGIT-DevOps](https://github.com/egovernments/DIGIT-DevOps/tree/unified-env-lts) repository.

**Step 2:** Deploy-as-code/helm/charts/frontend/digit-ui

[Reference Directory](https://github.com/egovernments/DIGIT-DevOps/blob/unified-env-lts/deploy-as-code/helm/charts/frontend/workbench-ui/values.yaml)

### **Environment Configuration** <a href="#environment-configuration" id="environment-configuration"></a>

**Step 1:** Locate the following `"deploy-as-code/helm/environments/unified-health-dev.yaml"`  in the DevOps repository of your organisation.

**Step 2:** Add the below code block within the environment YAML file used to deploy the Works platform -

```yaml

workbench-ui:
  custom-js-injection: |
    sub_filter.conf: "
      sub_filter  '<head>' '<head>
      <script src=https://egov-dev-assets.s3.ap-south-1.amazonaws.com/analytics/analytics.js type=text/javascript></script>      
      <script src={{INSERT_YOUR_AWS_BUCKET_NAME}}/globalConfigsWorkbenchDev.js type=text/javascript></script>
      ';"  
```

**Step 3:** Modify the development environment [sample file ](https://github.com/egovernments/DIGIT-DevOps/blob/888cd18925fea2793b9e02c8aae8aa718c168a37/deploy-as-code/helm/environments/unified-health-dev.yaml#L789C1-L795C12)as per requirements.

### **Global Configuration** <a href="#global-configuration" id="global-configuration"></a>

This section contains the configuration that applies globally to all UI modules. These need to be configured before the configuration of service-specific UI.

**Steps to create a globalconfig.js file:**

1. Create a config file (globalconfigs.js) with the below-mentioned config (refer to code below).
2. Configure all the images/logos required in the S3 and add links as footerBWLogoURL , footerLogoURL.
3. Mention the state tenant ID as stateTenantId.
4. If any User roles have to be made invalid, add as invalidEmployeeRoles.
5. Then push this global config file into your S3 bucket as globalconfigs.js
6. Mention the globalconfig file URL in your [`Environment config`](https://core.digit.org/guides/developer-guide/ui-developer-guide/ui-configuration-devops#environment-configuration)`.`

```javascript

 var globalConfigs = (function () {
  var stateTenantId = '<<INSERT_INSTANCE_TENANT_ID>>'
  var contextPath = 'workbench-ui';
  var configModuleName = 'commonMuktaUiConfig';
  var centralInstanceEnabled = false;
  var localeRegion = "IN";
  var localeDefault = "en";
  var mdmsContext = "egov-mdms-service";
  var footerBWLogoURL = '{{INSERT_YOUR_AWS_BUCKET_NAME}}/digit-footer-bw.png';
  var footerLogoURL = '{{INSERT_YOUR_AWS_BUCKET_NAME}}/digit-footer.png';
  var digitHomeURL = 'https://www.digit.org/';
  var hrmsContext = "health-hrms";
  var projectContext= "health-project";
  var invalidEmployeeRoles = ["CBO_ADMIN", "ORG_ADMIN", "ORG_STAFF", "SYSTEM"]
  var getConfig = function (key) {
    if (key === 'STATE_LEVEL_TENANT_ID') {
      return stateTenantId;
    }
    else if (key === 'ENABLE_SINGLEINSTANCE') {
      return centralInstanceEnabled;
    } else if (key === 'DIGIT_FOOTER_BW') {
      return footerBWLogoURL;
    } else if (key === 'DIGIT_FOOTER') {
      return footerLogoURL;
    } else if (key === 'DIGIT_HOME_URL') {
      return digitHomeURL;
   } else if (key === 'CONTEXT_PATH') {
      return contextPath;
    } else if (key === 'UICONFIG_MODULENAME') {
      return configModuleName;
    } else if (key === "LOCALE_REGION") {
      return localeRegion;
    } else if (key === "LOCALE_DEFAULT") {
      return localeDefault;
    } else if (key === "MDMS_CONTEXT_PATH") {
      return mdmsContext;
    } else if (key === "PROJECT_SERVICE_PATH") {
      return projectContext;
    } else if (key === "HRMS_CONTEXT_PATH") {
      return hrmsContext;
    } else if (key === "MDMS_V2_CONTEXT_PATH") {
      return mdmsContext;
    } else if (key === "MDMS_V1_CONTEXT_PATH") {
      return mdmsContext;
    } if (key === 'INVALIDROLES') {
      return invalidEmployeeRoles;
    }
  };
  return {
    getConfig
  };
}());

```

### AWS S3 Bucket Configuration <a href="#aws-s3-bucket-configuration" id="aws-s3-bucket-configuration"></a>

The S3 bucket has to be configured by the DevOps team to store all the assets being used in the application, like Logos, globalConfigs, etc.

**Steps to create a new AWS Bucket -**

1. Create a new AWS S3 Bucket
2. Update the Bucket Policy with the following content to make the bucket public

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::works-dev-asset/*"
        }
    ]
}
```

3. Update the Cross-Origin Resource Sharing (CORS) configuration with the below content:

```json
[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "GET",
            "PUT",
            "POST",
            "DELETE"
        ],
        "AllowedOrigins": [
            "*"
        ],
        "ExposeHeaders": [
            "x-amz-server-side-encryption",
            "x-amz-request-id",
            "x-amz-id-2"
        ],
        "MaxAgeSeconds": 3000
    }
]
```

4. To proxy the same bucket in any environment and make the necessary changes in the `environment.yaml` file located in the DevOps repository's `configmaps` under `egov-config` follow the steps below:

* Add the `s3-assets-bucket: "pg-egov-assets"`

```
 configmaps:
    egov-config:
      data:
        s3-assets-bucket: "(pg-egov-assets|egov-playground-assets|egov-uat-assets)"
```

5. After adding the proxy in the environment file, restart the `s3-proxy` build in the environment with config enabled.

<figure><img src="../../../../.gitbook/assets/image (150).png" alt=""><figcaption></figcaption></figure>
