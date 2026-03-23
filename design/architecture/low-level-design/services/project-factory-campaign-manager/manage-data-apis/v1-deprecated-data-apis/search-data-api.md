# Search Data API

## Endpoint <a href="#endpoint-1" id="endpoint-1"></a>

* **Endpoint**: /data/\_search
* **Method**: POST

## **Request Structure** <a href="#request-structure-1" id="request-structure-1"></a>

* RequestInfo: Object containing request information.
* SearchCriteria: Object containing search criteria.
  * id: (Optional) ID of the resource.
  * tenantId: Tenant identifier.
  * type: (Optional) Type of the resource (boundary, facility, user, boundaryWithTarget).
  * status: (Optional) Status of the resource.

## **Response Structure** <a href="#response-body-structure" id="response-body-structure"></a>

* ResponseInfo: Object containing response information.
* ResourceDetails: Array containing the details object of the searched resource.

## **Flow** <a href="#flow-1" id="flow-1"></a>

1. **Client Request**: The client sends a POST request to /data/\_search.
2. **Request Content**: Includes RequestInfo and SearchCriteria.
3. **Validation**: The server validates request structure and content.
4. **Response Creation**: The server creates a response with info and resource details.
5. **Response Dispatch**: Sends response back to client.
6. **Error Handling**: If errors occur, generate an error response and send it.

## Flow Diagram <a href="#flow-diagram-1" id="flow-diagram-1"></a>

<div align="left"><figure><img src="https://docs.digit.org/~gitbook/image?url=https%3A%2F%2Flh7-us.googleusercontent.com%2FFN5NcaKqhPNzJ2CdNtUoaQvHZappry1C3DNViilP1e_-U4XNzxfZUWhNmaN6EupN7-BY6Yu0_H5XWuOcLLHw1YXTCfAmIC05l-a0HcMFKaMZxOWqFrsfDOOWoyrXbXnyTfsyzEIMLXBymXznHMRyCI8&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=d3a43b41&#x26;sv=2" alt=""><figcaption></figcaption></figure></div>
