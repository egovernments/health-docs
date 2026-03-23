---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/access/public-health-product-suite/health-campaign-management-hcm/microplanning/product-requirements-document/sops-and-guidelines
---

# SOPs & Guidelines

### 1. Purpose

This document defines the **Standard Operating Procedures (SOPs)** and **data upload guidelines** to be followed by Programme Teams while preparing and uploading data for the Microplanning module. Adherence to these SOPs ensures data consistency, accuracy, and successful ingestion into the system.

***

### 2. Scope

This SOP applies to all Programme Team members responsible for preparing, validating, and uploading boundary and geographic data required for microplanning activities.

***

### 3. Roles and Responsibilities

* **Programme Teams**: Prepare data files as per prescribed formats and guidelines.
* **System Administrators**: Provide training on naming conventions and oversee data readiness.
* **Implementation Support Teams**: Assist with validation errors and troubleshooting, if required.

***

### 4. Supported Input Formats

The Microplanning module supports the following input formats:

* Pre-defined **Excel template**
* **GeoJSON** files (pre-defined schema)
* **Shapefile** (zipped)

Only the supported formats listed above will be accepted by the system.

***

### 5. Data Upload SOP

#### 5.1 Boundary-wise Data Configuration

* Data must be configured starting from **Admin Level 0**.
* Uploads must follow a **one-file-per-boundary** rule:
  * One file for all Admin 0 boundaries
  * One file for each Admin 1 boundary

#### 5.2 Naming Convention

* A standard naming convention must be followed for all uploaded files.
* Training on naming conventions will be provided by the system administrators.
* Files not adhering to the agreed naming convention may be rejected.

***

### 6. Input File Validation Guidelines

#### 6.1 GeoJSON Validation Rules

All GeoJSON files must comply with the following rules:

* Must conform to **RFC 7946 GeoJSON specification**
* The top-level element must be of type **FeatureCollection**
* All features must have geometries of the **same type** (e.g., all Points or all MultiPolygons)
* Coordinates must be within valid ranges:
  * Latitude: -90 to +90
  * Longitude: -180 to +180
* Any third coordinate (height value), if present, will be ignored
* All features must contain **properties with the same set of keys**
* Numeric values must not be quoted in the properties object
  * Example: `"population": 10000` (valid)
  * Example: `"population": "10,000"` (invalid)

***

#### 6.2 Shapefile Validation Rules

Shapefile uploads must meet the following requirements:

* A valid shapefile must include, at a minimum:
  * `.shp`, `.shx`, and `.dbf` files
* Optional supporting files may include:
  * `.prj`, `.sbx`, `.sbn`
* All files must be compressed and uploaded in **ZIP format**
* Coordinate reference system must be **WGS 84 (EPSG:4326)**
  * If `.prj` is missing, WGS 84 is assumed
  * Any other coordinate system is not supported
* Coordinates must be within valid ranges:
  * Latitude: -90 to +90
  * Longitude: -180 to +180
* Field names must not exceed **10 characters**, as per shapefile specifications
* Attribute fields must use appropriate data types:
  * Numeric values must be stored as Integer, Float, or Double fields
* Total size of all zipped files must not exceed **2 GB**

***

#### 6.3 Excel Validation Rules

When using the Excel upload template, ensure the following:

* Latitude and Longitude values must be in:
  * Degree Decimal (e.g., `12.3455`), or
  * Degree Minute Seconds (DMS) format without symbols
* Symbol-based formats are not supported
  * Example: `12° 20' 43.7994"` (invalid)
* All leading and trailing whitespace characters will be automatically stripped, including:
  * Spaces
  * Tabs
  * Carriage returns
  * New lines

***

### 7. Compliance and Enforcement

* All uploaded data is subject to system validation checks.
* Files failing validation will be rejected and must be corrected before re-upload.
* Repeated non-compliance may delay microplan setup and campaign timelines.

***

### 8. Versioning and Updates

This SOP is applicable for **Microplanning Module v0.1**. Any updates or changes to supported formats or validation rules will be communicated separately and reflected in updated versions of this document.

***

### 9. Support

For questions or support related to data preparation or upload issues, Programme Teams should contact the designated system administrator or implementation support team.
