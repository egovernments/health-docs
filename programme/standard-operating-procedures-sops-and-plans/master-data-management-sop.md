# Master Data Management SOP

### Sources of master data&#x20;

1. Master data for Tete for the group 4 campaign. Note : Master data would be campaign specific as village boundaries and user lists will change from campaign to campaign.
2. Master data imported from DHIS2. This would be for other two provinces and be used for dashboard visualisation.

### &#x20;Types of Master Data&#x20;

| <p>Type of Master data</p><p>In DIGIT</p>                                                                                                                                                       | Frequency of Change/update                                                                                                                                        | Shared between           | Equivalent in DHIS2             | Typical Time taken to upload in the system |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ | ------------------------------- | ------------------------------------------ |
| Boundary hierarchy                                                                                                                                                                              | Fixed for a campaign                                                                                                                                              | CHAI program- eGov Impel | Available                       | <p><br></p>                                |
| <p>Boundary Data specs( Boundary names, total households, campaign dates for the boundary etc)</p><p>Note : No deletions after campaign begins. Updation is allowed in worst case scenario.</p> | Changeable. The village list may change right upto the campaign(i.e. Start of distribution)                                                                       | CHAI program- eGov Impel | Available                       | <p><br></p>                                |
| <p>System Users</p><p><br></p>                                                                                                                                                                  | <p>Local monitors-Changeable</p><p>Registrar-Changeable</p><p>Warehouse managers- Changeable</p><p>Supervisors( District and provincial and National)- Fixed </p> | CHAI program- eGov Impel | Available                       | <p><br></p>                                |
| Facility(warehouses-Community , District, provincial and national)                                                                                                                              | <p>Fixed for a campaign</p><p>(to be checked with CHAI)</p>                                                                                                       | CHAI program- eGov Impel | Available                       | <p><br></p>                                |
| Product( Type , variant, SKUs etc)                                                                                                                                                              | Fixed for a campaign                                                                                                                                              | CHAI program- eGov Impel | <p>Not available</p><p><br></p> | <p><br></p>                                |
| Complaints/ Type                                                                                                                                                                                | <p><br></p>                                                                                                                                                       | <p><br></p>              | <p><br></p>                     | <p><br></p>                                |
| Role - action mapping                                                                                                                                                                           | <p><br></p>                                                                                                                                                       | <p><br></p>              | <p><br></p>                     | <p><br></p>                                |
| Campaign setup                                                                                                                                                                                  | <p><br></p>                                                                                                                                                       | <p><br></p>              | <p><br></p>                     | <p><br></p>                                |
| Delivery procedure-1 bednet for 2 individuals to a maximum of 3 bednets per household                                                                                                           | Fixed for a campaign                                                                                                                                              | <p><br></p>              | <p><br></p>                     | <p><br></p>                                |
| <p>Registration procedure-</p><p>Do we want to limit the numbers of households in a household.</p>                                                                                              | Fixed for a campaign                                                                                                                                              | <p><br></p>              | <p><br></p>                     | <p><br></p>                                |

## Master Data Collection template

Click [here](master-data-management-sop.md#master-data-collection-template) to view the details.&#x20;

## Master Data review process and Upload process&#x20;

1\. Finalise the data gathering template

2\. Sharing templates to CHAI and having a run through

3\. Have an agreement with CHAI on the lead time for sharing the data

4\. CHAI to review the data internally before sharing it back with eGov. I am expecting these data to be in Portuguese.

5\. Store all the data in appropriate shared folders

6\. Abhishek or Naved to review the data shared and approve if all required values are present

7\. If there are mistakes, duplicates, missing fields etc. mark them and share it back with CHAI

8\. Once the approved data is ready, this has to be shared with the implementation engineers for loading to Dev

9\. Use the data load utility (if ready) or load manually.

10\. Verify the application using the new data

<figure><img src="../../.gitbook/assets/Screenshot 2023-05-16 at 6.17.45 PM.png" alt=""><figcaption></figcaption></figure>

### Master data upload process&#x20;

Handling DHIS2 master data updation:

1. How is master data updation handled in DHIS2 application?
2. How does CHAI get to know that a certain master data has been changed/updated and typically how much time will be available to update it in the HCM application.
3. Master data received from CHAI would be in Portuguese? It is understood that eGov won't be able to do any validation on accuracy of this.
4. Will helpdesk play any role in master data updation or communicating the changes to eGov.
5. When the Master Data update/change happens how do the devices get re-provisioned with the latest set of master data( in case of DHIS2). eGov-CHAI will need to draft a strategy around this.&#x20;
6. Can we arrive at default values for missing master data in agreement with CHAI.
