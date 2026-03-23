# Target Data Upload API

**Base URL**: project-factory/v1/

**Endpoint: /data/\_create**

* **Method**: POST

## **Request Structure**

* **Body Parameters:**
  * RequestInfo: Object Containing RequestInfo
  * ResourceDetails: Details of a given Resource
    * type: Type of resource to create (e.g., boundarywithTarget)
    * tenantId: Tenant
    * fileStoreId: FileStoreId of Target Upload Sheet
    * action: Action to perform (e.g., validate for target upload)
    * hierarchyType: Name of Boundary Hierarchy
    * campaignId: CampaignId
    * additionalDetails: Additional details (optional)

## **Response Structure**

* **Success Response:**
  * ResponseInfo: Object Containing ResponseInfo
  * ResourceDetails: Details of the created resource

## **Flow**

1. **Client Initiates Request:**
   * The client sends a POST request to /data/\_create endpoint with action: validate.
2. **Validation of Request:**
   * **Resource Details Validation:**
     * Check if request.body.ResourceDetails exists and is not empty.
     * Throw a validation error if missing or empty with the message "ResourceDetails is missing or empty or null".
   * **Schema Validation:**
     * Validate request.body.ResourceDetails against createRequestSchema.
   * **Hierarchy Type Validation:**
     * Validate hierarchyType in request.body.ResourceDetails using validateHierarchyType function.
   * **Tenant ID Validation:**
     * Ensure that request.body.ResourceDetails.tenantId matches request.body.RequestInfo.userInfo.tenantId.
     * Throw a validation error if they do not match with the message "tenantId is not matching with userInfo".
3. **Different Tab Headers Validation:**
   * Validate whether headers are according to the template across all tabs of different districts.
4. **Target Sheet Validation:**
   * All validations will be on Sheets other than the ReadMe Sheet and Boundary Data Sheet.
   * **Immediate validations:**
     * **District Tabs Validation:**
       * Validate whether all district tabs are present in the Target Sheet uploaded.
     * **Empty Sheet Validation:**
       * Throw a validation error if any Target Sheet is empty.
     * **Root (District) level boundary validation:**
       * Throw a validation error if the root column (District) is empty in any row.
   * **Validations for each row:**
     * **Boundary Codes Validation:**
       * Check for missing or empty boundary codes in any row of any sheet.
       * Check for boundary code columns to be of type string.
       * Check for the presence of more than one boundary code in a given row of a given Target Sheet.
       * Check for duplicacy of the boundary code within the given Target Sheet.
     * **Boundary Targets Validation:**
       * Ensure that Target values are not missing and are positive numbers less than 1 Million.
