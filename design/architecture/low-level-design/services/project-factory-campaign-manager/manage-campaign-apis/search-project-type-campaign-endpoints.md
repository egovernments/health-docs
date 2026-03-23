# Search Project Type Campaign Endpoints

## Endpoint <a href="#endpoint-2" id="endpoint-2"></a>

**POST** `/project-type/search`

### Request Structure <a href="#request-structure-2" id="request-structure-2"></a>

**Body Parameters**

* **RequestInfo**: Object containing RequestInfo.
* **CampaignDetails**: Object containing the search criteria for campaigns.
* **tenantId**: Tenant identifier.
* **ids**: Array of campaign IDs to search for.
* **startDate**: The start date for the search.
* **endDate**: End date for the search.
* **projectType**: Type of the project.
* **campaignName**: Name of the campaign.
* **status**: Status of the campaign.
* **createdBy**: Creator of the campaign.
* **campaignNumber**: Number of the campaign.
* **campaignsIncludeDates**: Flag to include campaigns based on dates.
* **pagination**: Object containing pagination settings.
  * **limit**: Maximum number of results to return.
  * **offset**: Offset for paginated results.
  * **sortOrder**: Sort order for results (asc/desc).
  * **sortBy**: Field to sort results by.

### Response Structure <a href="#response-structure-2" id="response-structure-2"></a>

**Success Response**

* **ResponseInfo**: Object containing ResponseInfo details.
* **CampaignDetails**: Array containing details of matching campaigns.
* **totalCount**: Total number of matching campaigns.

## Flow <a href="#flow-2" id="flow-2"></a>

### **Client Initiates Request**

The client sends a searchCampaign request to the Project Factory Service.

### **Validate Request**

The Project Factory Service validates the request schema and search criteria.

### **Search Campaigns**

* The Project Factory Service constructs a search query based on the provided criteria.
* It checks if there are specific search fields like start date, end date, campaign name, etc.
* Depending on the `campaignsIncludeDates` flag, the service adjusts the search conditions accordingly.
  * If `campaignsIncludeDates` is **true**:
    * It shows only those campaigns whose start date is on or before the provided start date and whose end date is on or after the provided end date.
  * If `campaignsIncludeDates` is **false**:
    * It shows only those campaigns whose start date is on or after the provided start date and whose end date is on or before the provided end date.
* The service executes the constructed query to retrieve matching campaign details from the database.

### **Response**

The Project Factory Service sends the response back to the client.

* The response contains the matching campaign details along with the total count, if applicable.

## Flow Diagram <a href="#flow-diagram-2" id="flow-diagram-2"></a>

<figure><img src="https://docs.digit.org/~gitbook/image?url=https%3A%2F%2Flh7-us.googleusercontent.com%2F1FEAw78ZUkaFIWRF5TONniFAWk5iUvhPriukrrtZkr7qVwbhsEb8sEDVY1i1SVNxdfLtGN2XtXaxfKnyDBD5YHsuyMD0Yw4OHcRZk_h2k9lWdy5VLz4i-iH5i06-p9tC9kUQ9BTowbP79je03wvlki8&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=e7489a65&#x26;sv=2" alt=""><figcaption></figcaption></figure>
