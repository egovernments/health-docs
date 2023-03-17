# Google Cloud

## Compute Engine API

For access to the Compute Engine API, it has to be enabled at the [Google APIs console](https://console.developers.google.com/apis/dashboard).

#### User Roles <a href="#user-roles" id="user-roles"></a>

The user for the _Google Service Account_ that has to be created has to have three roles:

* _Compute Admin: `roles/compute.admin`_
* _Service Account User: `roles/iam.serviceAccountUser`_
* _Viewer: `roles/viewer`_

f the [`gcloud`](https://cloud.google.com/sdk/install) CLI is installed, a service account can be created like follow:

```
# create new service account
gcloud iam service-accounts create k8c-cluster-provisioner

# get your service account id
gcloud iam service-accounts list
# get your project id
gcloud projects list

# create policy binding
gcloud projects add-iam-policy-binding YOUR_PROJECT_ID --member 'serviceAccount:YOUR_SERVICE_ACCOUNT_ID' --role='roles/compute.admin'
gcloud projects add-iam-policy-binding YOUR_PROJECT_ID --member 'serviceAccount:YOUR_SERVICE_ACCOUNT_ID' --role='roles/iam.serviceAccountUser' 
gcloud projects add-iam-policy-binding YOUR_PROJECT_ID --member 'serviceAccount:YOUR_SERVICE_ACCOUNT_ID' --role='roles/viewer'
```

#### Google Service Account <a href="#google-service-account" id="google-service-account"></a>

A _Google Service Account_ for the platform has to be created, see [Creating and managing service accounts](https://cloud.google.com/iam/docs/creating-managing-service-accounts). The result is a JSON file containing the fields

* `type`
* `project_id`
* `private_key_id`
* `private_key`
* `client_email`
* `client_id`
* `auth_uri`
* `token_uri`
* `auth_provider_x509_cert_url`
* `client_x509_cert_url`

The private key is BASE64 containing the newlines as non-escaped strings _"\n”_. So to avoid the resulting troubles the machine controller expects the whole service account encoded in BASE64.# create a new json key for your service accountgcloud iam service-accounts keys create --iam-account YOUR\_SERVICE\_ACCOUNT k8c-cluster-provisioner-sa-key.json# create base64 encoded secretbase64 -w 0 ./k8c-cluster-provisioner-sa-key.json

#### Passing the Google Service Account <a href="#passing-the-google-service-account" id="passing-the-google-service-account"></a>

The base64 encoded secret of the service account will be passed in the field `serviceAccount` of the `cloudProviderSpec` of the machine deployment. The encoded secret can be entered in the UI field `Service Account`​



[​![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)​](http://creativecommons.org/licenses/by/4.0/)All content on this page by [eGov Foundation](https://egov.org.in/) is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
