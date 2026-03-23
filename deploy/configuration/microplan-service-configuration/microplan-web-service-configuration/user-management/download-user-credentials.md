# Download User Credentials

## Overview

The **Download User Data** screen allows administrators to download user details and credentials generated through the **Bulk User Creation** process.

Files are available in `.xlsx` format and include login credentials for successfully created users.

## Steps

### Step 1: Access the Download User Data Screen

* Log in as **MICROPLAN\_ADMIN**.
* Navigate to **User Management**.
* Click on **Download User Data**.

You will see a list of uploaded and processed bulk user files related to the microplan.

<figure><img src="../../../../../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>

### Step 2: View Available Files

The system automatically:

* Fetches all uploaded files associated with the microplan.
* Filters files that:
  * Were created via bulk upload
  * Belongs to the microplan source

Each file entry displays:

* File name
* Status
* Download option (if eligible)

### Step 3: Check File Status

Before downloading, verify the file status.

#### Download Allowed:

* Status = **Completed**

#### Download Not Allowed:

* Status = **Invalid**

If a file status is **Invalid**, it means:

* The upload failed validation.
* Credentials were not generated.
* The file cannot be downloaded.

### Step 4: Download the File

To download credentials:

* Locate the file with the **Completed** status.
* Click the **Download** button next to the file.
* The system retrieves the processed file.
* The file downloads in `.xlsx` format.

Each file has its own dedicated download button.

### Step 4: Download the File

To download credentials:

* Locate the file with the **Completed** status.
* Click the **Download** button next to the file.
* The system retrieves the processed file. The `/project-factory/v1/data/_search` API returns all files uploaded for the microplan.
* The file downloads in `.xlsx` format.

When the download button is clicked, the system uses the file’s `processedFilestoreId` to download the file.

```
Digit.Utils.campaign.downloadExcelWithCustomName({ fileStoreId: item?.processedFilestoreId, customName: String(fileName) });
```

Each file has its own dedicated download button.
