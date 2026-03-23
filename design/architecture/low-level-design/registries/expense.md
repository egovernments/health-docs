# Expense

## Overview <a href="#overview" id="overview"></a>

The Expense service allows users to capture the details for expense bills and payments.

## API Specifications <a href="#api-specifications" id="api-specifications"></a>

**Base path**: `/health-expense/bill/`

#### API Contract Link <a href="#api-contract-link" id="api-contract-link"></a>

The API specification is available [here](https://github.com/egovernments/DIGIT-Specs/blob/c7e5b6efefbfb351fd123788a7f762673223952d/Domain%20Services/Health/Expense-v1.1.0.yml). To view it in the Swagger editor, click below.

[![Logo](https://editor.swagger.io/dist/favicon-32x32.png)Swagger Editor](https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/DIGIT-Specs/c7e5b6efefbfb351fd123788a7f762673223952d/Domain%20Services/Health/Expense-v1.1.0.yml)

## Data Model <a href="#data-model" id="data-model"></a>

#### DB Schema Diagram <a href="#db-schema-diagram" id="db-schema-diagram"></a>

<figure><img src="../../../../.gitbook/assets/Expense (1).png" alt=""><figcaption></figcaption></figure>

## Web Sequence Diagrams <a href="#web-sequence-diagrams" id="web-sequence-diagrams"></a>

{% tabs %}
{% tab title="Create" %}
<figure><img src="../../../../.gitbook/assets/ExpenseSequenceDiagramCreate.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Update" %}
<figure><img src="../../../../.gitbook/assets/ExpenseSequenceDiagramUpdate.png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Search" %}
<figure><img src="../../../../.gitbook/assets/ExpenseSequenceDiagramSearch.png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

#### Persister <a href="#persister" id="persister"></a>

Persister configuration: [Expense persister](https://github.com/egovernments/configs/blob/HCM-v1.8/health/egov-persister/expense-bill-payment-persister.yml)

### Related Topics <a href="#related-topics" id="related-topics"></a>

* [Functional specifications - Expense](https://works.digit.org/specifications/functional-specifications/expenditure-billing)
* [Expense service configuration](../../../../deploy/configuration/hcm-service-configuration/expense-service.md)
