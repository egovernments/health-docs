---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/low-level-design/registries/household
---

# Household

## Overview

The **Household Registry** is a core microservice in DIGIT’s registry framework, enabling the management of households and their members within the Health Campaign Management (HCM) context. It provides structured APIs for CRUD operations and search capabilities, both at the household level and for individual household members.

## API Spec

{% embed url="https://editor.swagger.io/?url=https://raw.githubusercontent.com/egovernments/health-campaign-services/master/docs/health-api-specs/contracts/registries/household.yml" %}

## Sequence Diagrams

{% tabs %}
{% tab title="Household" %}
<figure><img src="../../../../.gitbook/assets/create-Household.svg" alt=""><figcaption><p>Household Create</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/bulk_create-Household.svg" alt=""><figcaption><p>Household Bulk create</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/update-Household.svg" alt=""><figcaption><p>Household Update</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/bulk_update-Household.svg" alt=""><figcaption><p>Household bulk update</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/household_search.svg" alt=""><figcaption><p>Household Search</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/delete-Household.svg" alt=""><figcaption><p>Household Delete</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/bulk_delete-Household.svg" alt=""><figcaption><p>Household Bulk Delete</p></figcaption></figure>
{% endtab %}

{% tab title="Member" %}
<figure><img src="../../../../.gitbook/assets/household_member_create.svg" alt=""><figcaption><p>Household Member - Create</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/bulk_create-Household_Member.svg" alt=""><figcaption><p>Household Member Bulk Create</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/household_member_update.svg" alt=""><figcaption><p>Household Member - Update</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/bulk_update-Household_Member (1).svg" alt=""><figcaption><p>Household Member Bulk Update</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/household_member_search.svg" alt=""><figcaption><p>Household Member - Search</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/delete-Household_Member.svg" alt=""><figcaption><p>Household Member - Delete</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/bulk_delete-Household_Member (1).png" alt=""><figcaption><p>Household Member - Bulk Delete</p></figcaption></figure>
{% endtab %}
{% endtabs %}
