# Master Data Management Service (MDMS) & Configuration Updates

### **MDMS**

| Feature                          | Service name | PR                                                                                                                                   |
| -------------------------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| Attendance Session Configuration | ​Attendance  | ​[attendance-sessions.json](https://github.com/egovernments/egov-mdms-data/blob/UNIFIED-DEV/data/mz/health/attendance-sessions.json) |

### **Config**

| Feature                             | Service name | PR                                                                                                                                                                                                                                                        |
| ----------------------------------- | ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Referral management and side-effect | referral     | ​[Persister](https://github.com/egovernments/health-campaign-config/blob/DEMO/egov-persister/referral-management-persister.yml) [Indexer](https://github.com/egovernments/health-campaign-config/blob/DEMO/egov-indexer/referral-management-indexer.yml)​ |
| Voucher-based registration          | project      | ​[Persister](https://github.com/egovernments/health-campaign-config/blob/DEMO/egov-persister/project-persister.yml)​                                                                                                                                      |
| Last-mile delivery with QR code     | stock        | ​[Persister](https://github.com/egovernments/health-campaign-config/blob/DEMO/egov-persister/stock-persister.yml)​                                                                                                                                        |

### **Devops**

| Feature                             | Service name         | PR                                                                                                                                                |
| ----------------------------------- | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Proximity-based search              | Household/Individual | -                                                                                                                                                 |
| Multi-round campaign                | ​                    | -                                                                                                                                                 |
| Referral management and side-effect | referral             | ​[Folder link](https://github.com/egovernments/health-campaign-devops/tree/master/deploy-as-code/helm/charts/health-services/referralmanagement)​ |
| Count in the household search       | Household            | -                                                                                                                                                 |
| Voucher-based registration          | Project              | -                                                                                                                                                 |
| Last-mile delivery with QR code     | ​                    | ​                                                                                                                                                 |
| Down sync API (v1.0)                | ​                    | -                                                                                                                                                 |
| Stock consumer group                | Stock                | ​[commit](https://github.com/egovernments/health-campaign-devops/commit/8f740dc95d695c7994194b49d39c057f0647c237)​                                |
