---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/low-level-design/services/project-factory-campaign-manager/create-campaign
---

# Create Campaign

### Overview <a href="#overview" id="overview"></a>

This document outlines the flow for creating a campaign using various services in the system. The process involves interactions between multiple services, including the Project Factory, Project Service, Boundary Service, Facility Service, HRMS Service, MDMS Service, FileStore Service, and the database. This flow ensures that the required resources are validated and correctly set up before finalizing the campaign creation.

### Actors and Participants <a href="#actors-and-participants" id="actors-and-participants"></a>

* **Client**: The entity (user or system) initiating the campaign creation request.
* **CampaignManager (Project Factory)**: The main controller managing the campaign creation process.
* **ProjectService**: Manages project-related operations, including data creation and mapping.
* **BoundaryService**: Handles fetching of boundary relationships based on hierarchy types.
* **FacilityService**: Responsible for creating facility-related data.
* **HRMSService**: Manages the creation of employee data.
* **MDMSService**: Provides master data such as project types.
* **FileStoreService**: Manages the storage and retrieval of resource files.
* **Database**: Stores campaign-related data and status updates.

### Sequence Flow <a href="#sequence-flow" id="sequence-flow"></a>

1. **Initiate Campaign Creation**
   * The **Client** sends a request to the **CampaignManager** to create a campaign with all required and valid resources.
2. **Fetch Boundary Relationship**
   * The **CampaignManager** requests the **BoundaryService** to fetch the boundary relationship based on the hierarchy type.
   * The **BoundaryService** responds with the relevant boundary relationship data.
3. **Fetch Project Type Master**
   * The **CampaignManager** requests the **MDMSService** to fetch the project type master data.
   * The **MDMSService** responds with the project type master.
4. **Validate Resource Files**
   * The **CampaignManager** checks the **Database** to see if the input resource files have already been validated.
   * The **Database** responds with the validation status of the files.
5. **Validation Check**
   * The **CampaignManager** checks if all file templates and data are validated:
     * If validation is successful, the **CampaignManager** informs the **Client** that the campaign creation process has started, and the user needs to track the status using an ID.
     * If validation fails, the **CampaignManager** returns an error message, indicating which validation failed, and the user must resubmit the request.
6. **Resource File Retrieval**
   * The **CampaignManager** interacts with the **FileStoreService** to search for the resource based on the `filestoreid`.
   * The **FileStoreService** responds with the valid resource files.
7. **Process Resource Data**
   * The **CampaignManager** processes the retrieved sheets and identifies any resource data that needs to be created.
8. **Facility Data Creation**
   * The **CampaignManager** sends a request to the **FacilityService** to create facility data.
   * The **FacilityService** responds that the facilities have been created successfully.
9. **Employee Data Creation**
   * The **CampaignManager** sends a request to the **HRMSService** to create employee data.
   * The **HRMSService** responds that the employees have been created successfully.
10. **Project Data Creation**
    * The **CampaignManager** sends a request to the **ProjectService** to create project data with a parent-child relationship based on the project type and delivery configuration.
    * The **ProjectService** responds that the projects have been created successfully.
11. **Project-Facility Mapping Creation**
    * The **CampaignManager** sends a request to the **ProjectService** to create mappings between projects and facilities.
    * The **ProjectService** responds that the project-facility mappings have been created successfully.
12. **Project-Staff Mapping Creation**
    * The **CampaignManager** sends a request to the **ProjectService** to create mappings between projects and staff.
    * The **ProjectService** responds that the project-staff mappings have been created successfully.
13. **Update Campaign Creation Status**
    * The **CampaignManager** updates the **Database** with the status of the campaign creation process.

### Error Handling <a href="#error-handling" id="error-handling"></a>

* **Validation Failure**: If any validation step fails (e.g., invalid data in resource files), the **CampaignManager** sends an error message to the **Client**, indicating the failure. The user is required to fix the issues and resubmit the request.
* **Service Errors**: If any of the service interactions (e.g., BoundaryService, MDMSService) return an error, the **CampaignManager** stops the process and informs the **Client** of the failure, specifying the nature of the error.
* **Database Errors**: If the **Database** fails to update the campaign creation status, appropriate error handling and logging mechanisms should be triggered to handle the failure.

### **API Sequence Diagram** <a href="#api-sequence-diagram" id="api-sequence-diagram"></a>

Create Campaign API Flow

<figure><img src="https://docs.digit.org/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FTXGfwWeUzCL8CsU9R0tT%2Fblobs%2FG2Cm0AmZ7DkcbHtHd0nl%2FScreenshot%25202024-08-29%2520at%25204.36.05%2520PM.png&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=901868a1&#x26;sv=2" alt=""><figcaption></figcaption></figure>

### Conclusion <a href="#conclusion" id="conclusion"></a>

This document provides an overview of the campaign creation flow, detailing each step and interaction between different services and the database. The flow ensures proper validation and creation of necessary resources, while error handling mechanisms provide robustness to the process.
