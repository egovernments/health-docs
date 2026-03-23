---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/low-level-design/services/project-factory-campaign-manager/manage-resources
---

# Manage Resources

## **Overview** <a href="#overview" id="overview"></a>

This document outlines the various API flows and interactions for the Project Factory, focusing on resource data creation with retry logic, template generation, campaign update flows, and data search and download processes. The aim is to manage and automate various aspects of resource and campaign data efficiently using the Project Factory services.

## **Sequence Flow** <a href="#project-factory-resources-data-create-with-retry-logic" id="project-factory-resources-data-create-with-retry-logic"></a>

### **Project Factory Resources Data Create with Retry Logic** <a href="#project-factory-resources-data-create-with-retry-logic" id="project-factory-resources-data-create-with-retry-logic"></a>

**Description:** This flow describes how the Project Factory handles resource data creation with retry logic. It ensures data consistency and reliability by retrying operations if failures occur.

**Sequence of Operations**

1. **Client Request Initiation**:
   * The client sends a request to the Project Factory with `filestoreid` and `type`.
2. **MDMS Service Interaction**:
   * Project Factory retrieves the type schema from the MDMS Service.
   * MDMS Service returns the schema, which is then validated.
3. **Data Validation**:
   * The Project Factory validates the data against the MDMS schema.
   * If validation is successful, it informs the client that data processing has started.
   * If validation fails, an error message is returned, and the user must resubmit.
4. **File Handling**:
   * The Project Factory requests a file download from the FileStore Service.
   * Upon receiving the file, JSON data is created from the file of the desired type.
5. **Data Creation and Retry Logic**:
   * Data is validated according to the schema.
   * **Normal Create**:
     * Data is created in the respective service, and status is tracked.
     * A loop continues until retry attempts exceed the maximum retries, or no failed data remains.
   * **Bulk Create with Retry**:
     * Data is created in the respective service, and the status is checked.
     * A search is conducted using the `generateApi search`.
     * The loop continues under the same conditions as the normal create process.
6. **Database Update**:
   * The file is enriched with the created ID and sent back to the FileStore Service.
   * The updated file is received, and data is persisted in the database with a status of 'created' and the processed `filestoreid`.

### **Template Generate API Flow (forceUpdate = true)** <a href="#template-generate-api-flow-forceupdate-true" id="template-generate-api-flow-forceupdate-true"></a>

**Description:** This flow is triggered when a client sends a generate request with `forceUpdate = true`. It checks for existing data and creates a new row with the status `inProgress` if necessary.

**Sequence of Operations:**

1. **Client Request Initiation**:
   * The client sends a generate request with the specified type and `forceUpdate = true`.
2. **Validation and Data Check**:
   * The Project Factory validates the type against predefined types and `hierarchytype`.
   * A check is performed to see if previous data exists. If it does, the data is marked as expired.
3. **Database and Response**:
   * A new row is created with `null fileStoreId` and `status inProgress`.
   * The database is updated, and a successful response is sent back to the client.
4. **Data Fetch and Storage**:
   * The Project Factory fetches the template from the MDMS Service based on the type.
   * Data is consolidated and stored in the FileStore Service, which returns a `filestoreid`.
   * The database is updated with the new `filestoreid`.

### **Template Generate API During Update Campaign Flow (forceUpdate = true)** <a href="#template-generate-api-during-update-campaign-flow-forceupdate-true" id="template-generate-api-during-update-campaign-flow-forceupdate-true"></a>

**Description:** This flow is initiated when a generate request is sent due to a boundary change in an ongoing campaign.

**Sequence of Operations:**

1. **Boundary Change Trigger**:
   * The Project Factory sends a generate request with `campaignId`, type, and `forceUpdate = true`.
2. **Validation and Data Check**:
   * The type is validated against predefined types and `hierarchytype`.
   * Previous data is checked, and if found, marked as expired.
   * The campaign is searched in the database based on the provided `campaignId` and its parent campaign ID.
3. **Database and Response**:
   * A new row is created with `null fileStoreId` and `status inProgress`.
   * The database is updated, and a response is provided.
4. **File Update and Data Consolidation**:
   * The Project Factory fetches file details from the FileStore Service using the parent campaign object.
   * The sheet is updated, freezing all the data.
   * If new boundaries are added, boundary relation data is fetched.
   * Data is consolidated and stored in the FileStore, and the database is updated with the new `filestoreid`.

### **Project Factory Resources Data Search and Download** <a href="#project-factory-resources-data-search-and-download" id="project-factory-resources-data-search-and-download"></a>

**Description:** This flow allows the client to search and download resource data based on a provided ID and type.

**Sequence of Operations:**

1. **Client Request Initiation**:
   * The client sends a request with the `id` and `type`.
2. **Database Query**:
   * The Project Factory checks the created resource based on the provided ID.
   * The corresponding resource details row is fetched from the database.
3. **Response to Client**:
   * The Project Factory sends back the created resource response to the client.

## Sequence Diagrams <a href="#api-sequence-diagrams" id="api-sequence-diagrams"></a>

{% tabs %}
{% tab title="Data Create" %}
<figure><img src="../../../../../../.gitbook/assets/image (416).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Data Search" %}
<figure><img src="../../../../../../.gitbook/assets/image (418).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Generate With Force Update" %}
<figure><img src="../../../../../../.gitbook/assets/image (419).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Template Download" %}
<figure><img src="../../../../../../.gitbook/assets/image (420).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Generate API" %}
<figure><img src="../../../../../../.gitbook/assets/image (421).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

## **Conclusion** <a href="#conclusion" id="conclusion"></a>

The outlined API flows are crucial for handling resource data creation, management, and retrieval efficiently. They ensure data consistency, integrity, and seamless interaction between various services, making the Project Factory a robust system for managing campaign data. Implementing the retry logic, data validation, and template generation processes helps maintain a reliable and scalable architecture.
