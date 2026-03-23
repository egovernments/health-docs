# Create Campaign API Endpoints

## Endpoint <a href="#endpoint" id="endpoint"></a>

**POST** `/project-type/create`

## Request Structure <a href="#request-structure" id="request-structure"></a>

**Body Parameters**

* **RequestInfo**: Object containing RequestInfo.
* **CampaignDetails**: Object containing the details of the campaign to be created.
* **tenantId**: Tenant identifier.
* **hierarchyType**: Type of hierarchy.
* **action**: Action type (`create` or `draft`).
* **boundaries**: Array of boundaries.
* **resources**: Array of resources.
* **projectType**: Type of the project.
* **deliveryRules**: Array of delivery rules.
* **Additional request info**

## Response Structure <a href="#response-structure" id="response-structure"></a>

**Success Response**

* **ResponseInfo**: Object containing ResponseInfo.
* **CampaignDetails**: The created campaign details.

## Flow <a href="#flow" id="flow"></a>

### **Client Initiates Request**

The client initiates a createCampaign request to the Project Factory Service.

### **Validate Request**

**If the action is 'create':**

1. The Project Factory Service validates the request schema.
2. It also validates the uniqueness of the campaign name in the database.
3. If the campaign name exists, an error is thrown.

**If the action is 'draft':**

1. The Project Factory Service validates the request schema.
2. It also validates the uniqueness of the campaign name in the database.
3. If the campaign name exists, an error is thrown.

**Boundary and MDMS Validation**

For both 'create' and 'draft' actions:

1. The Project Factory Service validates the request for hierarchy type and boundaries with the Boundary Service.
2. It validates the request for the project type code from [MDMS](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-QA/data/mz/health/project-types.json).

### **Create Campaign**

**If the action is 'create':**

1. The Project Factory Service validates the request for data resources.
2. It enriches the CampaignDetails and sets the status to 'creating'.
3. The CampaignDetails are persisted in the database.
4. For each resource data, the Project Factory Service creates resources through the `/project-factory/v1/data/_create` API.
5. It enriches boundaries for project creation and creates projects for each boundary with the Health Project Service.
6. The enriched CampaignDetails are persisted in the database.
7. The CampaignDetails object is sent to a Kafka topic for project mappings.
8. If the campaign status is not "created", project mappings are performed through the `/project-factory/v1/project-type/createCampaign` API and the status is updated to 'created'.
9. If the campaign status is already 'created', an error is thrown, and the status is updated to 'failed'.

**If the action is 'draft':**

1. The CampaignDetails are enriched, and the status is set to 'drafted'.
2. The enriched CampaignDetails are persisted in the database.

**Response**

The Project Factory Service sends the response back to the client.

## Flow Diagram <a href="#flow-diagram" id="flow-diagram"></a>

<figure><img src="../../../../../../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>
