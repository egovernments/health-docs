---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/community/faqs
---

# FAQs

## FAQs - General & Product-related&#x20;

Q1. When should we be expecting things like a geospatial feature on the HCM app?

> Answer: Geospatial data (longitude and latitude) is captured during registration and distribution activities through device tracking, and the same data can be viewed in map-based visualisation on the HCM dashboard.&#x20;

Q2. Does DIGIT accept open source contributions, and what does it take to build our own custom modules unique to our needs?

> Answer: Yes, DIGIT does have a community which contributes. There is a structured contribution process which should be followed for this. Anyone is free to use DIGIT services and build new modules as per their requirements.

Q3. Is the mobile app available on the Play Store or App Store?

> Answer: No, the HCM application is not available on the Play Store or Apple App Store.

Q4. Will eGov be providing post-training support to partners as they configure and customise DIGIT for campaigns?

> Answer: There is a 8-week support we offer after the training, during which queries can be addressed over a call. After this period, any queries can be shared in the[ discussion board](https://github.com/egovernments/Digit-Core/discussions/categories/public-health); this will be addressed timely manner.

Q5. What is limiting the availability of the iOS version of the DIGIT HCM App?

> Answer: For IOS, we need to launch the app in App Store / TestFlight. This requires a change in privacy and policy. As most of our partners use Android so we haven't implemented it.   Console has a preview which might help in visualisation of the app. on the web.

Q6. Are there plans to make the app available to the growing population of iOS users? Most especially in Nigeria?

> Answer: As of now, there is no immediate plan to make the DIGIT HCM available to iOS users. However, the eGov team continuously monitors the specific requirements from the end users, based on which launching the iOS version would be prioritised.

Q7. Once the data is downloaded, will it be available every time you log on, or do you need to re-download it every time you log in?

> Answer: Yes, data once downloaded on the phone will be there on the phone after you re-login; It will remain on the phone until the data is cleared explicitly.

Q8. Does the app allow multiple log-ons on different devices?

> Answer- We allow login using different devices, but the data created on each phone has to be synced up separately.

Q9. Is the name the only search field, or can it also be searched by ID or other fields?

> Answer: HCM product enables search based on name, status, beneficiary ID and proximity.

Q10. Is there a backend to access the data entered by the frontline workers?

> Answer- Yes, the data will be synced to the server. You can access it from the dashboard, reports or directly from the database.

Q11. What does the system use for a unique ID? Household name? GPS coordinate? Phone number? Campaign ID?

> Answer: All unique IDs generated in HCM is using the ID Generation service, which allows the SI partners to configure the format according to their needs.

Q12. It’d be nice if the search also returned similar names, not just results that match the entire word, because users can make spelling mistakes.

> Answer- Yes, but that might give a lot of data. We recommend using proximity search along with the name.

Q13. Can one create questionnaires by oneself?

> Answer- Yes, every implementation can have custom questionnaires as part of the checklist

Q14. Is there a default timeline for automated data synchronisation?

> Answer: Data is automatically synced at a scheduled frequency; by default, it will be every 5 minutes.

Q15. Can one search for a household member from the Beneficiary search page instead of searching for the head of household?

> Answer: Yes, we can search a beneficiary and head of household as part of the search.

Q16. Can the age be auto-calculated from DOB?

> Answer: Yes, age is auto-calculated from the date of birth.

Q17. What are the thresholds for GPS accuracy? What happens when the accuracy is low?

> Answer:&#x20;

Q18. Can you edit inputs in the preview page? I don't see a review button.

> Answer: In the top left corner, you will have a “Back” option. On a click of the back the user will be taken back to the previous page in edit mode, where they can change the data as required.

Q19. What does the system use for a unique ID?

> Answer: For the beneficiary, the unique ID will be a combination of the registrar ID, date of registration and a random number. Multiple options are there, and new ones can be configured. The current one used is only numbers and 12 digits in length.

Q20. I have seen instances where the GPS location fails. Does it happen with this app?

> Answer: There are rare cases where the device is not able to read the location. This can happen if they have denied the location permission. Also, we are working on UI to force the end user to allow all required permissions.

Q21. Can we set the minimum accuracy in the settings so that wrong data points are not recorded?

> Answer: Yes, we can set this. The default accuracy is set to 10 meters. We have set a pop-up so that the registrars or distributors stay on a screen for 5 seconds, so that their accuracy increases.

Q22. Speaking about GPS, can we configure Geo Fencing for individual campaigns, to ensure recorders don't leave the space?

> Answer: This feature is presently not available in HCM.

Q23. The members count on household registration. I suggest changing it to something like No. Of household members for easier understanding by the field users.

> Answer- You can change the Text to whatever is most suitable for you. This is a configuration element. We will show you how to change this in the upcoming sessions later.

Q24. Is it possible to send a picture/image of the situation you want to report, or is it just text? For ex. The quality of the road, or others.

> Answer- Yes, the complaints module used in local governance has the picture upload feature. We have not added it to the HCM for now as it was not required. But the feature exists in the platform.

Q25. Is there a particular DBMS used as the transactional database?

> Answer- Postgres is what we are using in HCM, but one can use other RDBMS and make necessary changes.

Q26. Can we import campaign data collected on other platforms into DIGIT to update the registries?

> Answer- We can write an adaptor and do this. Once we are FHIR compliant, it comes in handy.

Q27. Which data is stored in the Elastic and which is stored in the Postgres DB?

> Answer: All masters and transactions are stored in the Postgres database, whereas only the transactional data is stored in Elastic. The data available on Elastic would be an enriched version, which makes analysis easier.

Q28. Is there a slide that lists all these registries and services?

> Answer: You can refer to the [documentation](https://docs.digit.org/health/design/architecture/low-level-design)

Q29. Are other clouds supported, or is it strictly AWS-based?

> Answer- HCM is cloud agnostic. We have verified it on Azure and Google Cloud. The demo version is setup on AWS.

Q30. Is the data being sent to Elastic through Kafka?

> Answer- Yes, both to the database and Elastic, the data flows through Kafka.

Q31. What does PGR refer to?

> Answer- Public Grievance and Redressal, basically Complaints Management.

Q32. How do we access the chatbot?

> Answer: You can scan the QR Code in the DIGIT solution support page and get started.

Q33. What prediction model is it using in the Chatbot?

> Answer: The actual prediction (generation) model for chatbot responses is OpenAI's gpt-3.5-turbo. But we are in the process of upgrading to GPT-5.

Q34. Can we access the demo site to try our hands?

> Answer- Yes, [https://health-demo.digit.org/digit-ui/employee/user/login](https://health-demo.digit.org/digit-ui/employee/user/login). Credentials can be found [here](https://docs.google.com/spreadsheets/d/1TyqiwAJE3o7vXsmCuWmueG8cB1bGQ7JxUno1kERTAXo/edit?gid=0#gid=0).

Q35. What is the DB module on the app?

> Answer- This is the local mobile DB tool to see the data that is inserted into the mobile. This option will be enabled only in the developer mode. For a live/production app, this should be disabled

Q36. Does the DIGIT HCM app support a conditional checklist?

> Answer: Yes, a conditional checklist is supported in HCM.

Q37. Does the admin console also support bulk uploads for users and KPIs?

> Answer: Admin console does support bulk upload of users. However, it does not support the upload of KPIs.

## FAQ-Configuration & Support Activities (L1/L2)

Q1. Do we have access to the database, or do we have to request it?

> Answer: A SI Partners representative will have access to the database with the consent of the country and program.

Q2. How do we add a custom KPI?

> Answer: We are using Kibana for adding custom KPIs. Documentation can be found          [here](https://health.digit.org/deploy/configuration/dashboard-configurations/kibana-dashboard-integration), and more details can be found from the Chatbot.

Q3. Where do you add the transformations? Backend or on Elastic Search?

> Answer- All the transformed data will be stored in the ES itself

Q4. I am referring to the transformations. Let’s say we want to transform to take the date of birth and convert it to age. How do we do it?

> Answer- There is a transformation service where any logic can be written to transform data in the format required. Details can be obtained from the Chatbot.

Q5. How can I get the git link for this repository?

> Answer- Refer to the [documentation](https://docs.digit.org/health/release-notes/service-build-updates)&#x20;

Q6. Can you add multiple fields as a timestamp when creating a dataview?

> Answer- No, it can be just one timestamp

Q7. What does the following error imply? : Mapping conflict 6 fields are defined as several types (string, integer, etc) across the indices that match this pattern. You may still be able to use these conflict fields in parts of Kibana, but they will be unavailable for functions that require Kibana to know their type. Correcting this issue will require reindexing your data.&#x20;

Delete

Set as default

Edit.\
I am combining 2 indices

> Answer- If there is a common field across indexes in a data view that you are using for aggregation, and that field has different mapping types in those indexes—such as string, integer, or float—it will result in an error. You can check the mappings for the fields in that data view, and if necessary, reindex the data to change the mapping type accordingly.

Q8. Can different reports be from different timestamps?

> Answer: We can modify the reports to select the start and end times accordingly. If you want to use different start and end times for a particular report, these can be changed directly within the report itself. The reports are generally generated with a standard start and end date for consistency.

## FAQ- HCM Customisation&#x20;

Q1. How about the local install?

> Answer: Local installation of frontend and backend is available in the chatbot.

Q2. Can we go with the latest Flutter version?

> Answer- 3.22.2 is the version recommended

Q3. Can the background process be set to stop working when the application is idle for some time?

> Answer: Background service can't be stopped once it's started. We have a singleton reference for DB. If we stop the background service, the reference will also get closed, which breaks the application. We have decided not to stop because we can't predict when the end users will be creating a record.

Q4. I am getting this error: health-campaign-field-worker-app % flutter run Target file "lib/main.dart" not found when setting up the workspace. What could be the issue?

> Answer: The command should be run from inside apps/health\_campaign\_field\_worker\_app/ folder and not the main folder

Q5. Is there documentation for adding new fields?

> Answer: There is documentation, and the same can be obtained using the chatbot.

Q6. Considering changes are being added directly to the “registration delivery” module, doesn’t this mean conflicts can easily arise if updates or bug fixes from the official repository need to be merged in, in future?

> Answer- We can go with Custom screen creation and using a redirect route, or change the route to this new custom screen. That way, only screen-related changes need to be picked; other page changes can be picked by package update.

Q7. Is there an existing test suite that can be used to ensure regressions don’t find their way in when new fields/features are added to any of the modules?

> Answer- New fields are added only if a campaign needs any field over and above the list of fields not there in the HCM. The regression test suite can be found [here](https://docs.google.com/spreadsheets/d/17VYTkxvMgDVf8bRVyHOUAnYw-earf7YD3cqA11qGKew/edit?gid=0#gid=0).

Q8. How do we know the fields that are mandatory in the backend without looking at the code?

> Answer: We would need more information to give an exact answer; emulator issues would be specific to the system. Probably one can try downloading a new device from Android Device Manager and use that new one.

Q9. Do you recommend removing the mandatory fields from the backend?

> Answer- No, we do not recommend this. Fields are made mandatory for a definite reason; only the key fields which the registry needs are kept mandatory.

Q10. Suppose we want to add ID validation (integrating with our National Identity database) for verification checks. What is the best way to go about it? Are there existing modules/plugins for such a use case?

> Answer: Admin console can provide this for front-end validation, for backend, can add a custom validator for only that ID type

Q11. Is it safe to make API calls inside validators?

> Answer: Yes, it is safe as long as the API calls are authenticated.

Q12. What is the Postman collection for interacting with languages?

> Answer- [https://docs.google.com/presentation/d/1hMuqfJ6amIi4JmJZdZFDY6U\_Qz-bX22d0bVwYlxx-8o/edit?slide=id.g366097be971\_0\_14#slide=id.g366097be971\_0\_14](https://docs.google.com/presentation/d/1hMuqfJ6amIi4JmJZdZFDY6U_Qz-bX22d0bVwYlxx-8o/edit?slide=id.g366097be971_0_14#slide=id.g366097be971_0_14)

Q13. Does this translate all texts, including the KPIs?

> Answer: All the KPIs in the DSS dashboard would be translated to the selected language by default. However, the KPIs added in the custom tab, which is created from Kibana, need to be updated separately. (localisation needs to be updated for this to work.)

Q14. Which languages are available in HCM?

> Answer- By default, we have English, French and Portuguese available. The Kibana part will be English by default. The specific language Kibana dashboard will have to be configured separately.

Q15. Is there a reference to list the language value for all languages? e.g. English is "value": "en\_MZ"

> Answer- This is as per the standard. The first 2 characters will be the locale of that language, which is standard data available. The next 2 characters will be the country code. More details can be found in the Chatbot.

Q16. Can we just set the default localisation when doing the deployment?

> Answer- No, it is not an environment variable.

Q17. Suppose we have a use-case which requires us to use our local language on the mobile app (like Hausa language). Does this apply to that use case, or is there something different that we have to do? Will it affect the mobile app, or just the web interface? ha\_NG for Hausa

> Answer: We have the same configuration for both web and app for setting up the language. The procedure for setting up a language is the same for any. Any language localisation works if it meets the standard of i18n. Yes, we can able to set local language as ha\_NG and use.

Q18. Is there a maximum number of languages? Hypothetically, in multi-country use cases, more than 3 languages might be needed. Is that possible?

> Answer: There is no restriction on the number of languages that can be configured. Just that the mobile interface needs to be re-examined on the language selection page of the number is more than 3. Also, we need to verify for Arabic where the text starts from the right.

Q19. In the future, is there a plan to incorporate services like Google Translate to help with translation? Instead of manually adding the values yourself.

> Answer- We can do that, but Google Translate does not give the precise values for the context.

Q20. How do the roles affect what a user sees? Is there a description of the user roles and their permissions?&#x20;

> Answer: The options one sees in the mobile and web applications are based on the role attached to the user. Each role is mapped to a set of features and APIs. You can find the details [here](https://health.digit.org/access/public-health-product-suite/health-campaign-management-hcm/specifications/role-action-mapping).

Q21. Can we create users in bulk?

> Answer: Yes, bulk user creation is something that is done at the time of implementation. You can get the details from the Chatbot.

Q22. What if we have a list of users, and we want to update some information, like the name or the boundary code, for some users?

> Answer: You can edit the employee details using the Edit Employee option.

Q23. Can the usernames be generated by the administrators while doing the data load?

> Answer- You can generate a series of usernames using any online tool. It is not generated by the system.

Q24. What is the maximum users' data that has to be inputted per file?

> Answer: 30 user data in a single file.

Q25. Where can we get the possible values for the roles? Will that be through the UI?

> Answer: You can get the details of the roles in HCM and the features mapped [here](https://health.digit.org/access/public-health-product-suite/health-campaign-management-hcm/specifications/role-action-mapping).

Q26. How to handle a data load where we normally have thousands of users?

> Answer- You can create all 1000 in one file, and then the tool will split the content into 30 datasets per file. This takes care of the best performance.

Q27. How will the attendance screens be triggered?

> Answer: Attendance needs to be marked manually by the designated personnel.

Q28. Is there documentation for the required text case for each of the fields for user registration?

> Answer: You can find the test cases [here](https://health.digit.org/release-notes/complaints-test-cases/test-cases).

Q29. Is there a delete user option? Or do all users ever created remain on the system (whether active or deactivated)?

> Answer: There is no hard delete of any records in HCM, just that the record will be marked as inactive.

Q30. Is the attendance administered by an administrator for the users?

> Answer- Yes, there will be a designated administrator for a set of users for marking their attendance.

Q31. We have loops on our checklist that we have used in ODK.&#x20;

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeIS_7Yh6GCjhDn4ruQ3jHIKSW_V6RwltsXnbHC8y21Tw_goCDiUAXQpe5mIUeJUw5j5cQ5zPvkmIsrd31zo1980_4flyRmL0TPG9vrirRc1GKnFAaXeBXrR16HujixQvOLL0Th4A?key=HrNqJwLRPejn1wQ_5U_HkQ)![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcxuBviFswAN8BsUwRrq96WuXTUBz3V2SYX9v7V84JkVJNMx-yTubr7tsZmlB05aEjps3W6WN1_p86PP1S0sAXJg3EiZI-oJPKSvCAPfOjoKm8eNwvYSMFZENQ2VC3dklXnHALcdQ?key=HrNqJwLRPejn1wQ_5U_HkQ)

We want to allow them to add households. Can we currently add the households to the checklist?

> Answer: No, the household registry must be used for creating the households; the checklist module is for capturing data of supervision. Whatever changes are needed, they can modify the existing flow and make sure the necessary data is filled in the entities

## FAQ- Infrastructure Setup & Other DevOps Activities

Q1. What are the options available for on-prem hosting? Are you hosting a country's campaign data on-prem?

> Answer: At present, we are recommending OpenShift and Rancher as the two orchestration tools on which DIGIT can be deployed for an on-premise data centre. Refer to the [document](https://core.digit.org/guides/installation-guide/infrastructure-setup/sdc) for details.

Q2. How do we get access to the admin interface to be able to create our dashboards on Kibana?

> Answer: The System administrator who sets up the infrastructure should be able to give you access to Kibana.

Q3. Would the seed data step be required in the production setup as well?

> Answer- No. This is to set up HCM for demo ,or sa,y for vanilla development. For production, instead of seed data, actual data will have to be loaded.

Q4. What’s the minimum server requirements for setting up a demo instance of HCM?

> Answer-  Demo instance is provisioned using three r5ad.large nodes (2 vCPUs, 16 GiB RAM each) and a db.t3.medium database instance (2 vCPUs, 4 GiB RAM).

Q5. Do we also get an ArgoCD setup to automate our infrastructure changes?

> Answer- There is no ArgoCD configuration or pipeline provided out of the box, but the repository’s Helm charts are written to work with GitOps tools like ArgoCD if you decide to add it yourself.&#x20;

Q6. I noticed we are hardcoding the env. Why not use a secret manager like Hashicorp Vault?

> Answer: We do not keep production secrets in plain text. For this quick-start installatio,n we chose Mozilla SOPS instead of Vault, and we temporarily committed a few environment variables unencrypted to keep the “one-click” flow friction-free.

Q7. Have you incorporated the state locking already with Dynamo dB and S3?&#x20;

> Answer- Yes

Q8. Do you back up the volumes too?

> Answer- Yes, it is recommended to back up the volumes as well. Inside the cluster, you can invoke the EBS CSI driver’s VolumeSnapshot API, which creates the same point-in-time snapshot and lets you restore a new PVC from it just like any other Kubernetes object. We can also make use of Velero or AWS Data Life Cycle Manager to take these backups.

Q9. How do you manage the replication?

> Answer- In the dev environments, we use a single replica. In the production environments, we recommend using HPA for increasing the pod replicas based on resource utilisation. This could be derived from the load testing reports.

Q10. Why are we not using ArgoCD & GitHub Actions? Argocd is self-hosted, and it runs inside the cluster.

> Answer: We currently use GitHub Actions for builds, which is cost-free and stable for us and Jenkins for deployments. ArgoCD is self-hosted and adds operational overhead, so we’re reviewing it—along with other CD tools—for a phased rollout after a PoC.

Q11. How do we manage the amount of logs? I know that in production systems, logs take up a lot of space and drive costs up considerably.

> Answer:  We manage log volume by using Loki, which stores logs with minimal indexing to reduce storage needs and cost, and by setting retention policies to automatically purge old data. This keeps the system lightweight, cost-efficient, and easier to maintain in production.

Q12. Is there a reason DIGIT chose to use Grafana, Prometheus and Loki stack instead of using the ELK stack (Elastic, Logstash, & Kibana)? What are the benefits of using this stack instead of the ELK stack?

> Answer:  Prometheus + Loki (with Grafana) is lighter, cheaper, and more    Kubernetes-native than ELK. Prometheus handles metrics, Loki stores logs with minimal indexing (lower resource usage), and Grafana unifies both for easy correlation.
>
> ELK offers richer full-text search but is heavier, costlier, and more complex to run.

Q13. Does the monitoring start automatically with the one-click setup?

> Answer: No, monitoring tools have to be set up separately. One-click set-up is mainly aimed at helping a developer set up a demo or development environment.

Q14. Are there plans to also build HCM as a cloud platform?

> Answer: It is already a cloud platform.

Q15. Is DIGIT HCM SaaS or PaaS?

> Answer: It is PaaS; one can add customisation on top.

Q16. When setting up HCM and the emulator, it was discovered that the emulator does not have internet access. The app runs fine, but there is no internet for it to fetch data on a Mac M1. What could be the issue?

> Answer: This might be related to security/permissions on the device; one should check their firewall settings and ensure they are not using any proxy network connection.
