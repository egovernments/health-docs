---
description: DIGIT Infrastructure - Cleanup & Uninstallation
---

# Server Cleanup

## **Overview**

{% hint style="info" %}
As you wrap up your work with DIGIT, ensuring a smooth and error-free cleanup of the resources is crucial. The regular monitoring of the GitHub Actions workflow's output is essential during the destruction process. Watch out for any error messages or signs of issues. A successful job completion will be confirmed by a success message in the GitHub Actions window, indicating that the infrastructure has been effectively destroyed.&#x20;
{% endhint %}

When you are ready to remove DIGIT and clean up the resources it created, proceed with executing the terraform\_infra\_destruction job. This action is designed to dismantle all set-up resources, clearing the environment neatly. We hope your experience with DIGIT was positive and that this guide makes the uninstallation process straightforward.

## &#x20;Steps&#x20;

{% stepper %}
{% step %}
### Create seed data dump

* Check the available pods under the playground namespace

```
kubectl get pods -n playground
```

* This will return a list of running pods within the **playground** namespace. You should see an output similar to this:

```
NAME                               READY   STATUS    RESTARTS   AGE
playground-6c7f7b4c7b-rswb4       1/1     Running   0          15m
some-other-pod-name               1/1     Running   0          20m
```

* To further verify that this is the correct pod, you can describe the pod details using:&#x20;

```
kubectl describe pod playground-6c7f7b4c7b-rswb4 -n playground
```

This will give you details about the containers running inside the pod, logs, events, and other metadata.

* Once you've identified the correct pod, you need to access it via an interactive shell session:

```
kubectl exec -it playground-6c7f7b4c7b-rswb4 -n playground -- /bin/sh
```

* or (if Bash is available in the container)

```
kubectl exec -it playground-6c7f7b4c7b-rswb4 -n playground -- /bin/bash
```

* Once inside the pod, replace`{PLAYGROUND_POD_NAME}` ,  `{DATABASE_HOST}`,  {`DATABASE_USERNAME}`,  {`DB_NAME}` in the command given below, run it to generate the **seed data dump**:

```
pg_dump --data-only -h {DATABASE_HOST} -p 5432 -U {DATABASE_USERNAME} -d {DB_NAME} -f seed_data_dump_1_7.sql \
    --table=product_variant \
    --table=product \
    --table=boundary \
    --table=boundary_hierarchy \
    --table=boundary_relationship \
    --table=eg_mdms_data \
    --table=eg_mdms_schema_definition
```

This will create a file named **`seed_data_dump_1_7.sql`** inside the pod’s filesystem.

* Once the dump is completed, exit the pod shell by running:

```
exit
```

* Now that the dump file is available inside the pod, copy it to your local system using:

```
kubectl cp playground/{PLAYGROUND_POD_NAME}:seed_data_dump_1_7.sql /home/seed_data_dump_v1.7.sql
```
{% endstep %}

{% step %}
## Destroy the Server

To initiate the destruction of a Terraform-managed infrastructure, follow these steps:

* Navigate to Actions.
* Click DIGIT-Install workflow.
* Select Run workflow.
* When prompted, type 'destroy'. This action starts the terraform\_infra\_destruction job.
* You can observe the progress of the destruction job in the actions window.
{% endstep %}
{% endstepper %}
