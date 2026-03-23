---
description: >-
  This package provides a way to register a household and individual members and
  deliver the resources to the registered households.
---

# Registration & Delivery Package

To learn more about Registration and Delivery, [click here.](https://health.digit.org/hcm-product-suite/health-products/frontline-workers-app/user-manual)\
\
Link to the pub package:

{% embed url="https://pub.dev/packages/registration_delivery" %}

## Role

* DISTRIBUTOR

## **Features**

* Register new households and individuals.
* Search existing households and individuals.
* Update details for existing households and individuals.
* Record service delivery of healthcare interventions to households and individuals for a single round campaign.
* Auto-calculation of resources to be delivered to a household or individuals based on the configured rule.

## Getting Started

To use this package, add the following dependency to your pubspec.yaml file:

```
dependencies:
  registration_delivery: ^latest
  digit_scanner: ^latest
```

## Integrating with the HCM Application:&#x20;

1. To integrate this package with the HCM Application, run the main function located in `health-campaign-field-worker-app/tools/registration_delivery_imports.dart.`&#x20;
   * This will automatically add the necessary imports, mapper initializers, route config, setting initial data, and repository initialization to the required files.
2. Make sure you are on the path `apps/health_campaign_field_worker_app` and run the command:

```dart
dart run build_runner build --delete-conflicting-outputs
```

This adds a package route to the `main router.gr.dart`&#x20;

3. Install the application and you should have Registration and Delivery integrated into your base app.

By following these steps, you can successfully integrate and use the registration and delivery module within your application.

{% hint style="info" %}
The below step is required as per your use case
{% endhint %}

During boundary selection, if you need to downsync registration-delivery-related data, include the below code in the `project_beneficiaries_downsync` file:

```dart
final LocalRepository<HouseholdModel, HouseholdSearchModel>
  householdLocalRepository;
final LocalRepository<HouseholdMemberModel, HouseholdMemberSearchModel>
  householdMemberLocalRepository;
final LocalRepository<ProjectBeneficiaryModel, ProjectBeneficiarySearchModel>
  projectBeneficiaryLocalRepository;
final LocalRepository<TaskModel, TaskSearchModel> taskLocalRepository;
final LocalRepository<SideEffectModel, SideEffectSearchModel>
  sideEffectLocalRepository;
final LocalRepository<ReferralModel, ReferralSearchModel>
  referralLocalRepository;
```

Next, find this method in the same file `networkManager.writeToEntityDb` and the below repositories:&#x20;

```dart
householdLocalRepository,
householdMemberLocalRepository,
projectBeneficiaryLocalRepository,
taskLocalRepository,
sideEffectLocalRepository,
referralLocalRepository,
```

With the above changes, you will enable the down sync of registration and delivery data.

#### **Registries -Update**

When the user down sync's the data by passing project id and boundary code. Server will send responses which are created under that selected boundary.&#x20;

#### **Response Entities**

* Household&#x20;
* Individual
* House Member

#### **Now what ?**

**Case 1:** Need to update the Entities related to project specific data.

**Case 2:** Create Project specific data - (Beneficiary - Mandatory. Task and other relative entities)&#x20;

#### **Introducing Filters**

* Registered
* Un registered
* Closed&#x20;

#### **Combination of filters by search.**&#x20;

* **Proximity enabled**&#x20;
* **Search by name**

To get the search response we create a query build which is as shown below. It's an example for an individual based project.&#x20;

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe592zsfxXugkuiq81n7bV9ClbDm05ffjJaZ6q6XXG-eU0DS3EDX1uiiTfSY5LvGaJjj8FdZJGrwkwLJifdx66UCouLqlxhr0eql8LL17ms1WO1vzGHHZ1_rGJynfw7d8u_-9J3tMw_vXVTUtTUHYSw3-65?key=9Nh1qYotTAKkaU2_CLeYjA" alt=""><figcaption></figcaption></figure>

**Sequence diagram :**\
\
<br>

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdtIOsYMODvdR98edviAMDKS8QdRXNkSCUP2zbt7-iGRhoDgGelt4V6mhjBv3USFOhRkgtVF7_7ltgzaIP0SYo7FC-eI0erhBgW2NE0l4yijXZKi9dscZHF6C_ce57Ggw6Q8nQJvlMmqIQv5sdTEghG4EQ3?key=9Nh1qYotTAKkaU2_CLeYjA" alt=""><figcaption></figcaption></figure>



#### Fields Incorporated in Registration Flow.

1. GPS accuracy - Household Location screen
2. No. of Pregnant Women and No. of Childs- Member screen - Both these field values persist in Additional fields Object of HH Member entity&#x20;
3. Added a new screen to capture the structure of household structure

The structure data will be fetched from MDMS and rendered in card format and the selected value will be stored in Additional Details Object in Household Entity.

#### Closed House Data Capture.&#x20;

It’s been built as a new module (pub package)- [**closed\_household**](../closed-household-package.md) and It will be a dependency of registration and delivery package.

### Unsuccessful delivery &#x20;

For HH based flow we have introduced a flow to capture the reason for unsuccessful delivery&#x20;

**Sequence diagram**&#x20;

&#x20;&#x20;

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe4VOziJYqh74W6SmrVx0gPoqjlaWAHMp3iM35iMr_xNSRWYnLJGp5OXcudYmk3wyqQjuggRT0uy27WGVQ4clLjzIrkO5kWx1yNdyP3Jt-jAAbalNqqlvmv2tK-LTSuzuWqsFuwdETRFXRE_Dorvp0ww7jk?key=9Nh1qYotTAKkaU2_CLeYjA" alt=""><figcaption></figcaption></figure>



<br>
