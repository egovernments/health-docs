# Update Campaign

## Overview <a href="#overview" id="overview"></a>

This document outlines the flow for updating an existing campaign using various services in the system. The process involves interactions between multiple services, including the Project Factory, Project Service, Boundary Service, Facility Service, HRMS Service, MDMS Service, FileStore Service, and the database. The update flow ensures that the required resources are validated and updated correctly before finalising the campaign update.

## Actors & Participants <a href="#actors-and-participants" id="actors-and-participants"></a>

* **Client**: The entity (user or system) initiating the campaign update request.
* **CampaignManager (Project Factory)**: The main controller managing the campaign update process.
* **ProjectService**: Manages project-related operations, including data creation and mapping updates.
* **BoundaryService**: Handles fetching of boundary relationships based on hierarchy types.
* **FacilityService**: Responsible for creating and updating facility-related data.
* **HRMSService**: Manages the creation and updating of employee data.
* **MDMSService**: Provides master data such as project types.
* **FileStoreService**: Manages the storage and retrieval of resource files.
* **Database**: Stores campaign-related data and status updates.

## Sequence Flow <a href="#sequence-flow" id="sequence-flow"></a>

1. **Initiate Campaign Update**
   * The **Client** sends an update request to the **CampaignManager** with all required and valid resources.
2. **Fetch Boundary Relationship**
   * The **CampaignManager** requests the **BoundaryService** to fetch the boundary relationship based on the hierarchy type.
   * The **BoundaryService** responds with the relevant boundary relationship data.
3. **Fetch Project Type Master**
   * The **CampaignManager** requests the **MDMSService** to fetch the project type master data.
   * The **MDMSService** responds with the project type master.
4. **Validate Resource Files**
   * The **CampaignManager** queries the **Database** to check if the input resource files have already been validated.
   * The **Database** responds with the validation status of the files.
5. **Fetch Parent Campaign Object**
   * The **CampaignManager** queries the **Database** to fetch the parent campaign object based on the `parentCampaignId`.
   * The **Database** responds with the parent campaign object.
6. **Validation Check**
   * The **CampaignManager** checks if all file templates and data are validated:
     * If validation is successful, the **CampaignManager** informs the **Client** that the campaign update process has started, and the user needs to track the status using an ID.
     * If validation fails, the **CampaignManager** returns an error message, indicating which validation failed, and the user must resubmit the request.
7. **Deactivate Parent Campaign**
   * The **CampaignManager** updates the **Database** to mark the parent campaign object as inactive.
8. **Retrieve Resource Files**
   * The **CampaignManager** interacts with the **FileStoreService** to search for the resource based on the `filestoreid`.
   * The **FileStoreService** responds with the valid resource files.
9. **Process Resource Data**
   * The **CampaignManager** processes the retrieved sheets to identify any resource data that needs to be created.
10. **Facility Data Creation**
    * The **CampaignManager** sends a request to the **FacilityService** to create facility data.
    * The **FacilityService** responds that the facilities have been created successfully.
11. **Employee Data Creation**
    * The **CampaignManager** sends a request to the **HRMSService** to create employee data.
    * The **HRMSService** responds that the employees have been created successfully.
12. **Search for Parent Project**
    * The **CampaignManager** sends a request to the **ProjectService** to search for the previous or parent project.
    * The **ProjectService** responds with the project object.
13. **Create New Projects for Added Boundaries**
    * The **CampaignManager** copies the project content from the parent project while creating new projects for newly added boundaries.
    * The **CampaignManager** sends a request to the **ProjectService** to create project data for newly added boundary data and map it according to its parent.
    * The **ProjectService** responds that the projects have been created successfully.
14. **Update Facility Data**
    * The **CampaignManager** identifies what exact data needs to be updated for facilities.
    * The **CampaignManager** sends a request to the **ProjectService** to create project-facility mapping if any new facilities are added.
    * The **ProjectService** responds that the project-facility mapping has been created successfully.
    * The **CampaignManager** sends a request to the **ProjectService** to search for the previous project-facility mapping.
    * The **ProjectService** responds with the project-facility mapping data.
    * The **CampaignManager** sends a request to the **ProjectService** to update the project-facility mapping.
    * The **ProjectService** responds that the project-facility mapping has been updated successfully.
15. **Update Staff Data**
    * The **CampaignManager** identifies what exact data needs to be updated for staff.
    * The **CampaignManager** sends a request to the **ProjectService** to create project-staff mapping if any new staff are added.
    * The **ProjectService** responds that the project-staff mapping has been created successfully.
    * The **CampaignManager** sends a request to the **ProjectService** to search for the previous project-staff mapping.
    * The **ProjectService** responds with the project-staff mapping data.
    * The **CampaignManager** sends a request to the **ProjectService** to update the project-staff mapping.
    * The **ProjectService** responds that the project-staff mapping has been updated successfully.
16. **Update Campaign Status**
    * The **CampaignManager** updates the **Database** with the campaign update status.

## Error Handling <a href="#error-handling" id="error-handling"></a>

* **Validation Failure**: If any validation step fails (e.g., invalid data in resource files or missing required resources), the **CampaignManager** sends an error message to the **Client**, indicating the failure. The user is required to fix the issues and resubmit the request.
* **Service Errors**: If any of the service interactions (e.g., BoundaryService, MDMSService, ProjectService) return an error, the **CampaignManager** stops the process and informs the **Client** of the failure, specifying the nature of the error.
* **Database Errors**: If the **Database** fails to update the campaign update status or mark the parent campaign as inactive, appropriate error handling and logging mechanisms should be triggered to handle the failure.

## **Sequence Diagram** <a href="#api-sequence-diagram" id="api-sequence-diagram"></a>

Update Campaign Flow

<figure><img src="https://docs.digit.org/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2FiuOLXL2nzcWxBvoHLNEz%2FScreenshot%25202024-08-30%2520at%25202.09.24%2520PM.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=418416fb&#x26;sv=2" alt=""><figcaption></figcaption></figure>

## Conclusion <a href="#conclusion" id="conclusion"></a>

This document provides a comprehensive overview of the update campaign flow, detailing each step and interaction between different services and the database. The flow ensures proper validation and updating of necessary resources, while error handling mechanisms provide robustness to the process.
