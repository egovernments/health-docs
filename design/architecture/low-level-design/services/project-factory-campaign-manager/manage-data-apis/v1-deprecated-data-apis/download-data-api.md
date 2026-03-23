# Download Data API

## Endpoint <a href="#endpoint-3" id="endpoint-3"></a>

* **Endpoint**: /data/\_download
* **Method**: POST

## **Request Structure** <a href="#request-structure-3" id="request-structure-3"></a>

* RequestInfo: Object containing request information.
* Type: (Optional) Type of the resource being downloaded.
* TenantId: Tenant identifier.
* HierarchyType: Type of hierarchy.
* Id: (Optional) ID of the resource being downloaded.
* Filters: (Optional) Additional filters for the download request.
* campaignId : campaignId

## **Response Structure** <a href="#response-structure-2" id="response-structure-2"></a>

* ResponseInfo: Object containing response information.
* ResourceDetails: Array containing the details object of the downloaded resource.

## **Flow** <a href="#flow-3" id="flow-3"></a>

1. **Client Request**: The client sends a POST request to download data.
2. **Request Validation**: Upon receiving the request, the server validates the request structure and parameters.
3. **Data Download Process**:
   * **Validation**: Validate the download request.
   * **Fetch Data**: Fetch existing data of the specified type from the data host service.
   * **Processing**: Process the retrieved data as necessary.
4. **Response Creation**: After processing the request, the server creates a response containing the details of the latest resource, ensuring that only one result is fetched.
5. **Response Dispatch**: The server sends the generated response back to the client.
6. **Error Handling**: If errors occur during the process, an error response is generated and sent.

#### Flow Diagram <a href="#flow-diagram-3" id="flow-diagram-3"></a>

<div align="left"><figure><img src="https://docs.digit.org/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2F7IuwolE1DKPXsWBcyy1G%2Fimage.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=ca63c01a&#x26;sv=2" alt=""><figcaption></figcaption></figure></div>

**Handling Empty or Missing Downloaded Responses**

If the downloaded response is empty or not searched with the provided ID, the system automatically starts regenerating a template of the same type. The generation process is triggered by the backend, not through the UI.
