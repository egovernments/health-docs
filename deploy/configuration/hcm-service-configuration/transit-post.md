---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/hcm-service-configuration/transit-post
---

# Transit Post

## Overview

The Transit Post Package is a Flutter-based module designed to manage transit post selections, including scanning resources and tracking delivery count. It integrates with Bloc for state management and supports reactive forms for user inputs.

## &#x20;Features

Transit Post Pages: The package includes several pages like 'transit\_post\_selection.dart', 'transit\_post\_record\_vaccination.dart', 'transit\_post\_acknowledgment.dart' and 'transit\_post\_wrapper.dart' to record resource delivery.

Transit Post Blocs: It provides various Blocs for state management.

Transit Post Repositories: The package provides abstract classes for data repositories, 'UserActionLocalRepository', 'UserActionRemoteRepository'.

## Getting Started

To use this package, add the following dependency to your 'pubspec.yaml' file:

```
dependencies:
    transit_post: ^any
```

## Usage

To navigate to any screens of the package:

First, add transit\_post\_router to your main app router

Navigate to the required screen using the code below:

```
context.router.push(TransitPostWrapperRoute())
```

Transit\_post package requires below data to be passed from the main app:

```
List<ProjectProductVariantModel>? _resources;
  List<String>? _transitPostType;
  String? _tenantId;
  String? _loggedInUserUuid;
  String? _projectId;
  BoundaryModel? _boundaryModel;
  int? _minAge;
  int? _maxAge;
```

## Configuration Details

**MDMS Schemas**

Action Test

```
{
                    "id": 2035,
                    "name": "Transit Post",
                    "url": "",
                    "displayName": "HOME_TRANSIT_POST_LABEL",
                    "orderNumber": 0,
                    "parentModule": "cards",
                    "enabled": true,
                    "serviceCode": "null",
                    "code": "null",
                    "path": ""
                }
```

* Roles

```
{
      "code": "TRANSIT_POST_VACCINATOR",
      "name": "Transit Post Vaccinator",
      "description": "Transit post vaccination provider"
    }
```

## Flow Diagram

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe2QSuKwhp8wATioruPB_Mbfo2c4zL98DpViyZGR_dZO-jW1bEMX5H9T0thL3WRY2BI9NEWE6St1XdPUS0wDSjWN_kOMgOpEw7hy-7qK0fF_cdl_ZTZ8LrQcER4sDBfQUZ61JBa7Q?key=1lf8D4un1prWEP84wwvW2w" alt=""><figcaption></figcaption></figure>
