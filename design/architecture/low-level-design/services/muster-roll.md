---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/low-level-design/services/muster-roll
---

# Muster Roll

### Overview

The Muster Roll service aggregates attendance logs from the attendance service based on some rules and presents an attendance aggregate for a time period (week or month) per individual. This can then be used to compute payments or other semantics.

### Dependencies <a href="#pdf-page-kynhcdzgkzux6zad8mps-dependencies" id="pdf-page-kynhcdzgkzux6zad8mps-dependencies"></a>

* [DIGIT backbone services](https://core.digit.org/platform/core-services)
* [Idgen](https://core.digit.org/platform/core-services/id-generation-service)
* [Persister](https://core.digit.org/platform/core-services/persister-service)
* [Indexer](https://core.digit.org/platform/core-services/indexer-service)
* [Workflow](https://core.digit.org/platform/core-services/workflow-service)
* [User](https://core.digit.org/platform/core-services/user-services)
* [Attendance](../registries/attendance.md)

### Code <a href="#pdf-page-kynhcdzgkzux6zad8mps-code" id="pdf-page-kynhcdzgkzux6zad8mps-code"></a>

[Module code](https://github.com/egovernments/DIGIT-Works/tree/master/backend/muster-roll)

[Helm charts](https://github.com/egovernments/DIGIT-DevOps/tree/digit-works/deploy-as-code/helm/charts/digit-works/backend/muster-roll)

### API Specifications <a href="#pdf-page-kynhcdzgkzux6zad8mps-api-specifications" id="pdf-page-kynhcdzgkzux6zad8mps-api-specifications"></a>

**Base Path:** /health-muster-roll

#### API Contract Link <a href="#pdf-page-kynhcdzgkzux6zad8mps-api-contract-link" id="pdf-page-kynhcdzgkzux6zad8mps-api-contract-link"></a>

{% embed url="https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/DIGIT-Works/develop/backend/muster-roll-service/Muster-Roll-Service-1.0.0.yaml" %}

### Data Model <a href="#pdf-page-kynhcdzgkzux6zad8mps-data-model" id="pdf-page-kynhcdzgkzux6zad8mps-data-model"></a>

#### DB Schema Diagram <a href="#pdf-page-kynhcdzgkzux6zad8mps-db-schema-diagram" id="pdf-page-kynhcdzgkzux6zad8mps-db-schema-diagram"></a>

<figure><img src="../../../../.gitbook/assets/musterroll-db-diagram.png" alt=""><figcaption></figcaption></figure>

Web Sequence Diagrams

{% tabs %}
{% tab title="Create" %}
<figure><img src="../../../../.gitbook/assets/create_muster_roll_updated (1).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Update" %}
<figure><img src="../../../../.gitbook/assets/update_muster_roll_updated (1).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Search" %}
<figure><img src="../../../../.gitbook/assets/search_muster_rolls_updated.png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

#### Master Data

{% embed url="https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.8/MusterRoll.json" %}

{% embed url="https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.8/IdFormat.json" %}

{% embed url="https://github.com/egovernments/releasekit/blob/master/mdms/HCM/v1.8/workerRates.json" %}

### Related Topics

* [Muster Roll service configuration](../../../../deploy/configuration/hcm-service-configuration/muster-roll.md)
