# Data Migration

Migration for new mandatory field (clientreferenceid) in Household\_Member table, This migration has to be done before the deployment the Household build.

```
ALTER TABLE HOUSEHOLD_MEMBER ADD COLUMN IF NOT EXISTS clientreferenceid character varying(256);

UPDATE HOUSEHOLD_MEMBER SET clientreferenceid = id;
```

Migration for null client Audit details Since previous versions did not have the information.

```
UPDATE HOUSEHOLD SET clientCreatedBy = createdBy,
                     clientCreatedTime = createdTime,
                     clientLastModifiedBy = clientLastModifiedBy,
                     clientLastModifiedTime = lastModifiedTime where clientcreatedby is null;

UPDATE HOUSEHOLD_MEMBER SET clientCreatedBy = createdBy,
                     clientCreatedTime = createdTime,
                     clientLastModifiedBy = clientLastModifiedBy,
                     clientLastModifiedTime = lastModifiedTime where clientcreatedby is null;

UPDATE INDIVIDUAL SET clientCreatedBy = createdBy,
                     clientCreatedTime = createdTime,
                     clientLastModifiedBy = clientLastModifiedBy,
                     clientLastModifiedTime = lastModifiedTime where clientcreatedby is null;

UPDATE PROJECT_BENEFICIARY SET clientCreatedBy = createdBy,
                     clientCreatedTime = createdTime,
                     clientLastModifiedBy = clientLastModifiedBy,
                     clientLastModifiedTime = lastModifiedTime where clientcreatedby is null;

UPDATE PROJECT_TASK SET clientCreatedBy = createdBy,
                     clientCreatedTime = createdTime,
                     clientLastModifiedBy = clientLastModifiedBy,
                     clientLastModifiedTime = lastModifiedTime where clientcreatedby is null;
```
