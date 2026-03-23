# Update Campaign Using Console

## Overview

This document describes the low-level web flow for updating an existing campaign using the Admin Console. The process involves coordinated interactions between the frontend (Admin Console) and backend services to ensure campaign data is correctly updated, validated, and finalised.

***

## Key Actors & Services

* **User**: Admin user interacting with the Admin Console to update campaigns.
* **CampaignManager (Admin Console)**: The web UI/controller handling orchestration of campaign updates.
* **ProjectFactory**: Backend service that manages campaign object lifecycle, including updates and validation.
* **BoundaryService**: Provides boundary hierarchy and relationship data for the campaign.
* **MDMSService**: Supplies master data (project types, hierarchies, templates).
* **FileStoreService**: Stores and retrieves campaign-related files.

***

## Sequence Flow&#x20;

#### Initiating Campaign Update

* **User**: Begins the update process by selecting an existing campaign from the "My Campaign" screen within the Admin Console.
* **CampaignManager**: Receives the request to update a specific campaign and retrieves the campaign object using its unique ID.

#### 2. Fetching Campaign Data

* **CampaignManager** sends a request to **ProjectFactory** to fetch the campaign object based on the provided campaign ID.
  * **ProjectFactory** responds with the campaign object containing the current campaign details.

#### 3. Fetching Boundary Information

* **CampaignManager** requests **BoundaryService** to fetch boundary hierarchy definitions based on the campaign's hierarchy type.
  * **BoundaryService** responds with the boundary hierarchy definition.
* **CampaignManager** requests **BoundaryService** to fetch boundary relationship data based on the hierarchy type.
  * **BoundaryService** responds with the boundary relationship data.

#### 4. User Data Input

* **User**: Updates the necessary fields, such as boundary delivery configuration and other campaign-specific details, using the Admin Console.
* **CampaignManager**: Sends the updated information to **ProjectFactory** to create or update the campaign object, storing it with an action status of "draft".

#### 5. Template Generation

* **ProjectFactory**: Automatically triggers the generation of templates for different resources, including:
  * Target templates
  * Facility templates
  * User templates

#### 6. Template Download and Storage

* **User**: Downloads the generated templates for each resource type via the Admin Console.
* **CampaignManager**: Sends a request to **FileStoreService** to store the downloaded files.
  * **FileStoreService** responds with a `filestoreid` that uniquely identifies the stored file.

#### 7. Data Validation

* **CampaignManager**: Sends the data and the `filestoreid` to **ProjectFactory** for validation.
  * **ProjectFactory** responds with a unique validation ID, as the validation process may take some time.
* **CampaignManager**: Periodically checks the validation status using the unique validation ID.

#### 8. Validation Outcome

* **ProjectFactory**:
  * If validation is successful:
    * Responds with a success message.
    * **CampaignManager**: Displays a success message to the user, indicating that they can proceed to the next step.
  * If validation fails:
    * Responds with an error message detailing the validation failure.
    * **CampaignManager**: Displays the error message to the user, prompting them to correct the errors and re-upload the files.

#### 9. Final Campaign Update

* **User**: Once all required data is filled in and validated, the user reviews the summary of the campaign data and clicks on the "Update Campaign" button.
* **CampaignManager**: Sends a request to **ProjectFactory** with the campaign update API, marking the action as "update".

#### 10. Campaign Update Outcome

* **ProjectFactory**:
  * If the update is successful:
    * Responds with a success message, indicating that the campaign update has started.
    * **CampaignManager**: Displays a success message to the user, confirming that the campaign has been updated successfully.
  * If the update fails:
    * Responds with an error message detailing the failure.
    * **CampaignManager**: Displays the error message to the user, prompting them to correct any issues and try again.

***

## Error Handling

* **Validation Failures**: If validation fails at any stage (e.g., during file validation or input data checks), the **CampaignManager** will notify the user of the specific issues. The user must resolve these issues and re-upload the necessary data to proceed.
* **Service Errors**: If any of the services (e.g., BoundaryService, ProjectFactory) encounter an error during processing, the **CampaignManager** will display an error message, detailing the problem and suggesting corrective actions.

***

## Sequence Diagram&#x20;

<figure><img src="../../../../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

***

## Conclusion

This document outlines the flow for updating an existing campaign using the Admin Console. The structured sequence ensures that any changes to the campaign are thoroughly validated and processed, minimising errors and ensuring the integrity of the campaign data. By following this flow, users can confidently update campaigns, knowing that all necessary steps are taken to verify and finalise their changes.
