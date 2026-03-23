# Update Campaign API Endpoints

## Endpoint <a href="#endpoint-1" id="endpoint-1"></a>

**POST** `/project-type/update`

### Request Structure <a href="#request-structure-1" id="request-structure-1"></a>

**Body Parameters**

* **RequestInfo**: Object containing RequestInfo.
* **CampaignDetails**: Object containing the details of the campaign to be updated.
* **id**: Unique identifier of the campaign.
* **tenantId**: Tenant identifier.
* **hierarchyType**: Type of hierarchy.
* **action**: Action type (`create` or `draft`).
* **boundaries**: Array of boundaries.
* **resources**: Array of resources.
* **projectType**: Type of the project.
* **deliveryRules**: Array of delivery rules.

### Response Structure <a href="#response-structure-1" id="response-structure-1"></a>

**Success Response**

* **ResponseInfo**: Object containing ResponseInfo.
* **CampaignDetails**: The updated campaign details.

## Flow <a href="#flow-1" id="flow-1"></a>

### **Receive Request**

The ProjectFactoryService receives an updateCampaign request from the Client.

### **Validate Request Schema**

The received request schema is validated to ensure it matches the expected format.

**Check Campaign Existence**

The system checks if the campaign specified in the request exists in the database.

**Conditional template generation call**

* If boundaries are different from the campaign in the database, call:
  * Facility template generate
  * User template generate
  * Target template generate
* If delivery conditions are different, call:
  * Target template generate

**Check Campaign Status**

If the campaign exists, the system checks its status in the database.

### **Handle Drafted Status**

**If the campaign status is 'drafted':**

1. **Validate Boundaries**: Validate the request for hierarchyType and boundaries.
2. **Validate Project Type**: It validates the request for the project type code from [MDMS](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/health/project-types.json).
3. **Enrich Campaign Details**: Enrich the campaign details and set the status to 'updating'.
4. **Update Campaign Details**: Update the campaign details in the database.
5. **Update Resource Data**: Update each resource data associated with the campaign through the `/project-factory/v1/data/_update` API.
6. **Enrich Boundaries**: Enrich the boundaries for the project update.
7. **Update Projects**: Update projects associated with each boundary.
8. **Persist Changes**: Persist the updated campaign details in the database.
9. **Send to Kafka Topic**: Send the updated CampaignDetails object to the Kafka topic for project mappings.
10. **Listen to Kafka**: Listen for updates from the Kafka topic to get the updated CampaignDetails object for project mappings.

### **Handle Campaign Status**

**If the campaign status is not 'created':**

1. Do project mapping through `/project-factory/v1/project-type/createCampaign` API.
2. Enrich the CampaignDetails and set the status to 'created'.
3. Update the CampaignDetail in the database.

### **Handle Project Mapping Error**

**If the campaign status is 'created':**

1. Throw an error indicating that the project is already mapped for this campaign.
2. Enrich the CampaignDetails and set the status to 'failed'.
3. Update the CampaignDetail in the database.

**Handle Non-Drafted Status**

If the campaign status is not 'drafted', the system throws an error indicating that only drafted campaigns can be updated.

**Send Response**

The ProjectFactoryService sends a response to the Client based on the outcome of the update operation.

## Flow Diagram <a href="#flow-diagram-1" id="flow-diagram-1"></a>

<figure><img src="https://docs.digit.org/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2FEGLQagtbWzQUFwPX8gui%2Fimage.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=4f6b14d3&#x26;sv=2" alt=""><figcaption></figcaption></figure>
