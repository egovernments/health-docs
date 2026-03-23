# SOPs & Guidelines

## System SOP(s) for Programme Teams

1. Data upload [guidelines](/broken/pages/FgPR4ZeL3G2A7dpdXCNa) are to be followed and adhered to

&#x20;       a. Input formats supported:

&#x20;           \- Pre-defined Excel template

&#x20;           \- Geosjon (pre-defined schema)

&#x20;           \- Shapefile&#x20;

&#x20;      b. Configure data starting from admin 0

&#x20;      c. A naming convention needs to be followed for data upload (training to be provided)

&#x20;      d. 1 file per boundary to be uploaded

&#x20;           \- 1 file for all admin 0

&#x20;           \- 1 file for admin 1

## Guidelines

### Input File Validation

#### GeoJSON

* The GeoJSON file should meet the [RFC 7946 GeoJSON](https://datatracker.ietf.org/doc/html/rfc7946) specification
* The top-level element should be of type “FeatureCollection”
* All the Features within the FeatureCollection should have geometries of the same type (i.e. all should be points, or all should be MultiPolygons, and so on).
* The coordinates should be in the valid range of Latitude & Longitude. (Valid range for Latitude is -90 to +90; Valid range of Longitude is -180 to +180)
* If the third coordinate (i.e. the height value) is present, then it will be ignored.
* All the features should have properties with the same set of keys.
* In the Properties object, the values for fields that represent a Numeric Value should not be quoted with double quotes (i.e. population of 10,000 should be represented as “population”: 10000 and not “population”: “10,0000”

#### Shapefile

* A shapefile consists of multiple files with the same name and different extensions. Mandatory ones are  .shp, .shx & .dbf. You could also have .prj, .sbx & .sbn.
* The shapefile should be in the WGS 84 lat-long coordinate system. (i.e. EPSG:4326). If the .prj file is missing, then the data is assumed to be in the WGS 84 lat-long coordinate system.
* Data in any other coordinate system, even if indicated so in the .prj file, will not be considered valid.
* The coordinates should be in the valid range of Latitude & Longitude. (Valid range for Latitude is -90 to +90; Valid range for Longitude is -180 to +180).
* Field Names are limited to 10 Characters as per the Shapefile Specification.
* The Various fields in the attribute table should have the appropriate data types. (i.e. Numeric Values should be in fields of the type Short Integer, Long Integer, Float, or Double)
* The User should zip up all the files in Zip format and upload them into the system. At a minimum, the system needs .shp, .shx & .dbf files
* The total size of all files together should not exceed 2GB

#### Excel

* The Latitude & Longitude fields should have data in Degree Decimal and Degree Minute Seconds ( Value should be 12.3455 & not 12° 20' 43.7994")
* Any leading & trailing whitespace characters (Spaces, Tabs, Carriage Return, new line etc) will be stripped out from all fields
