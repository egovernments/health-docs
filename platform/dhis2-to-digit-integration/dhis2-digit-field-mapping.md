# DHIS2-DIGIT Field Mapping

## Master Data

The following data is needed for DIGIT ecosystem

### Boundary Hierarchy

Boundary and Boundary Hierarchy is part of one time setup. All the fields cannot be fetched from the DHIS2 directly. Some manual intervention is needed.

| DIGIT Field             | DHIS2 Source              | Comments                                                                                                                                                                                                                                                                                                                          |
| ----------------------- | ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Code                    | <p><br></p>               | DHIS2 has numerical short codes. DIGIT expects alphabets. We can directly use the Level codes - 1,2,3,4,5,6 as described by DHIS2                                                                                                                                                                                                 |
| Boundary Hierarchy Type | Organizational Unit Level | <p><a href="https://dev.ccumoz.com/api/organisationUnitLevels?fields=id,displayName,level">https://dev.ccumoz.com/api/organisationUnitLevels?fields=id,displayName,level</a></p><p><br></p><p><a href="https://dev.ccumoz.com/api/organisationUnits/wqmPoqfG93D">https://dev.ccumoz.com/api/organisationUnits/wqmPoqfG93D</a></p> |
| Description             | OrgUnit.Name              | [https://dev.ccumoz.com/api/organisationUnits/wqmPoqfG93D](https://dev.ccumoz.com/api/organisationUnits/wqmPoqfG93D)                                                                                                                                                                                                              |

### Projects/Boundaries

Clubbing projects and boundaries because both of these can be populated from same set of master data.  These are directly correlated to Organisational Units. Targets to be fetched from forms. The forms of interest are “RTIs Metas Macroplano” and “RTIs Metas Microplano”. They are available at village level only.  Projects and relevant targets can be fetched from the following boundary information.

| DIGIT Field                       | DHIS2 Source                                      | Comments    |
| --------------------------------- | ------------------------------------------------- | ----------- |
| Boundary Code                     | OrgUnit.code                                      | <p><br></p> |
| Boundary Name                     | OrgUnit.name                                      | <p><br></p> |
| Parent Boundary Code              | OrgUnit.parent.code                               | <p><br></p> |
| Boundary Type                     | OrgUnitLevel.name                                 | <p><br></p> |
| Hierarchy Type Code               | OrgUnitLevel                                      | <p><br></p> |
| Campaign Start Date               | <p><br></p>                                       | <p><br></p> |
| Campaign End Date                 | <p><br></p>                                       | <p><br></p> |
| Total Households                  | RTIs Metas Macroplano.Agregado familiar           | <p><br></p> |
| Targetted Households              | RTIs Metas Microplano.Agregados do Microplano     | <p><br></p> |
| Total Individuals                 | RTIs Metas Macroplano.População                   | <p><br></p> |
| Targeted Individuals              | <p>RTIs Metas Microplano.População</p><p><br></p> | <p><br></p> |
| Bednets estimated to be delivered | RTIs Metas Macroplano.Redes mosquiteiras          | <p><br></p> |

### Users

| DIGIT Field            | DHIS2 Source                  | Comments                                                                                                                                      |
| ---------------------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Username               | User.userCredentials.username | Can be kept same as DHIS2 username                                                                                                            |
| Password               | <p><br></p>                   | We will need to auto generate this, if user access needs to be provided.                                                                      |
| Name                   | User.name                     | <p><br></p>                                                                                                                                   |
| Mobile No              | Not available                 | DHIS2 does not capture demographic and user information.                                                                                      |
| Gender                 | Not Available                 | DHIS2 does not capture demographic and user information.                                                                                      |
| Date of Birth          | Not Available                 | DHIS2 does not capture demographic and user information.                                                                                      |
| Email                  | Not Available                 | DHIS2 does not capture demographic and user information.                                                                                      |
| Correspondence Address | Not Available                 | DHIS2 does not capture demographic and user information.                                                                                      |
| Role                   | User.userRole                 | Multiple role assignments are possible. Role Maps need to be created between DIGIT and DHIS2 and appropriately assigned                       |
| Employment Type        | Not Available                 | DHIS2 does not capture demographic and user information.                                                                                      |
| Date of Appointment    | Not Available                 | DHIS2 does not capture demographic and user information.                                                                                      |
| Department\*           | Not Available                 | DHIS2 does not capture demographic and user information.                                                                                      |
| Designation            | Not Available                 | DHIS2 does not capture demographic and user information.                                                                                      |
| Project                | User.organisationalUnit       | A user can be associated with multiple Organisational Units. We will need to map OU to Projects and appropriately map the project to the user |

### Product

Product and Product variant are one time config

ration for a campaign. Unable to find equivalent in DHIS2. Will need to double check.

For Mozambique, the following are being tracked on DHIS2 at a team level.

* Red Sticker
* Green Sticker
* Bednet

At the district and community warehouses only bed nets are being tracked.

### Shapefile

OrgUnits have shapes (geometry) associated with them. Granularity is available only till district level. If we have to generate the shapefile dynamically, it will be tedious. Would be better to check with the CHAI team about how they are downloading the shapefiles from DHIS2 and replicate.&#x20;

### Facility

Unable to find on DHIS2. Will need to check with Mrunal and CHAI team.

## Transactional Data

Types of Data

There are two types of transactional data that we need to ingest into DIGIT from DHIS2.

* Beneficiary - In the case of Moz it is Household data.
* Service Delivery - In the case of Moz, this is the bed net being distributed.
* Inventory management
* Supervisor checklist - Forms are available in DHIS2, need to understand DIGIT models before this mapping can be done.

### DHIS2 Forms

The following forms contain transactional data in DHIS2

| DHIS2 Form                                                      | Translation                                               | Comments                                                                                                                                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ficha de entrega de material - Monitor (Entrega e Devolução)    | <p>Material delivery form for monitor. </p><p><br></p>    | Not sure about where this can be used. This contains details for all materials used as part of campaigns. Red stickers, Green stickers, bednets etc.                         |
| Ficha de entrega de material - Provincial (Entrega e Devolução) | Material delivery form - Provincial (Delivery and Return) | Need to understand use case                                                                                                                                                  |
| Ficha de entrega de material - Logistico (Entrega e Devolução)  | Material delivery form - Logistics (Delivery and Return)  | Need to understand use case                                                                                                                                                  |
| Ficha de Registo dos Agregados Familiares                       | Household registration form                               | This is the form of interest. This contains the service delivery information.                                                                                                |
| Gestão De Stock - Começo de cada dia                            | Stock management - Start of every day                     | This is stock management to each distribution team. How many Red and Green stickers, bed nets etc are being given to each team at the beginning of the day. Not of interest. |
| Gestão De Stock - No final de cada dia                          | Stock management - End of each day                        | This is stock management to each distribution team. How many Red and Green stickers, bednets etc are returned by the team at the end of each day. Not of interest.           |
| AD (Armazém distrital) - Entradas                               | District Warehouse - Entry                                | <p><br></p>                                                                                                                                                                  |
| AD (Armazém distrital) - Saidas                                 | District Warehouse - Exit                                 | <p><br></p>                                                                                                                                                                  |
| AD (Armazém distrital)- Contagem física                         | District Warehouse - Physical Count                       | <p><br></p>                                                                                                                                                                  |
| AC (Armazem Comunitarial) - Entradas                            | Community Warehouse - Entry                               | <p><br></p>                                                                                                                                                                  |
| AC (Armazem Comunitarial) - Saidas                              | Community Warehouse - Exit                                | <p><br></p>                                                                                                                                                                  |
| AC (Armazem Comunitarial) - Contagem física                     | Community Warehouse - Physical count                      | <p><br></p>                                                                                                                                                                  |

### Beneficiary

This data is extracted from the form called “Ficha de Registo dos Agregados Familiares”. The only Beneficiary field available is the Head of household’s name and memberCount of the household. The rest of the required fields will be empty.

| DIGIT Field                | DHIS2 Source                                                                                               | Comments                                                                                                                                 |
| -------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| projectId                  | OrgUnit                                                                                                    | This is an acquired field from DIGIT<>DHIS2 master data mapping. It will be associated with the relevant OU at the village level         |
| tenantId                   | <p><br></p>                                                                                                | <p><br></p>                                                                                                                              |
| clientReferenceId          | FormEntry.ID                                                                                               | This is to store the DHIS2 internal unique identifier of this beneficiary record from the form. This will be the ID of the form instance |
| memberCount                | Número de membros do agregado familiar que vivem na mesma casa (incluindo o(a) chefe do agregado familiar) | <p><br></p>                                                                                                                              |
| address.tenantId           | <p><br></p>                                                                                                | <p><br></p>                                                                                                                              |
| address.doorNo             | NA                                                                                                         | <p><br></p>                                                                                                                              |
| address.latitude           | FormEntry.latitude                                                                                         | <p><br></p>                                                                                                                              |
| address.longitude          | FormEntry.longitude                                                                                        | <p><br></p>                                                                                                                              |
| address.locationAccuracy   | NA                                                                                                         | <p><br></p>                                                                                                                              |
| address.type               | HOUSEHOLD                                                                                                  | <p><br></p>                                                                                                                              |
| address.addressLine1       | NA                                                                                                         | <p><br></p>                                                                                                                              |
| address.addressLine2       | NA                                                                                                         | <p><br></p>                                                                                                                              |
| address.landmark           | NA                                                                                                         | <p><br></p>                                                                                                                              |
| address.city               | OrgUnit?                                                                                                   | Can we populate from OrgUnit or can we ignore this                                                                                       |
| address.pincode            | NA                                                                                                         | <p><br></p>                                                                                                                              |
| address.buildingName       | NA                                                                                                         | <p><br></p>                                                                                                                              |
| address.street             | NA                                                                                                         | <p><br></p>                                                                                                                              |
| address.locality.code      | OrgUnit.code                                                                                               | <p><br></p>                                                                                                                              |
| address.locality.label     | OrgUnit.name                                                                                               | <p><br></p>                                                                                                                              |
| address.locality.latitude  | NA                                                                                                         | <p><br></p>                                                                                                                              |
| address.locality.longitude | NA                                                                                                         | <p><br></p>                                                                                                                              |

### Service Delivery

This data is extracted from the form called “Ficha de Registo dos Agregados Familiares”.

| DIGIT Field                | DHIS2 Source                               | Comments                                                                                                                                                                      |
| -------------------------- | ------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| projectId                  | OrgUnit                                    | This is an acquired field from DIGIT<>DHIS2 master data mapping. It will be associated with the relevant OU at the village level                                              |
| tenantId                   | <p><br></p>                                | <p><br></p>                                                                                                                                                                   |
| clientReferenceId          | FormEntry.ID                               | This is to store the DHIS2 internal unique identifier of this beneficiary record from the form. This will be the ID of the form instance                                      |
| projectBeneficiaryId       | DIGIT BeneficiaryID                        | After the beneficiary is created, we will need to fetch that ID and populate this field                                                                                       |
| resources.tenantId         | <p><br></p>                                | <p><br></p>                                                                                                                                                                   |
| resources.productVariantId | <p><br></p>                                | This is the product variant being distributed. Will be part of MDMS. We were told that if we configure at project level in MDMS, it will be auto populated.                   |
| resources.quantity         | FormEntry.Número de redes distribuídas     | <p><br></p>                                                                                                                                                                   |
| resources.isDelivered      | <p><br></p>                                | This will always be true, because entry is created in DHIS2 after service delivery                                                                                            |
| resources.deliveryComment  | FormEntry.Observações                      | <p><br></p>                                                                                                                                                                   |
| plannedStartDate           | <p><br></p>                                | <p><br></p>                                                                                                                                                                   |
| plannedEndDate             | <p><br></p>                                | <p><br></p>                                                                                                                                                                   |
| actualStartDate            | <p><br></p>                                | <p><br></p>                                                                                                                                                                   |
| actualEndDate              | <p><br></p>                                | <p><br></p>                                                                                                                                                                   |
| createdBy                  | FormEntry.Selecione equipe de distribuição | This is the name of the DHIS2 user who created this record. We will be importing these users as part of master data import, the equivalent DIGIT userID to be populated here. |
| createdDate                | <p><br></p>                                | <p><br></p>                                                                                                                                                                   |
| address.tenantId           | <p><br></p>                                | <p><br></p>                                                                                                                                                                   |
| address.doorNo             | NA                                         | <p><br></p>                                                                                                                                                                   |
| address.latitude           | FormEntry.latitude                         | <p><br></p>                                                                                                                                                                   |
| address.longitude          | FormEntry.longitude                        | <p><br></p>                                                                                                                                                                   |
| address.locationAccuracy   | NA                                         | <p><br></p>                                                                                                                                                                   |
| address.type               | HOUSEHOLD                                  | <p><br></p>                                                                                                                                                                   |
| address.addressLine1       | NA                                         | <p><br></p>                                                                                                                                                                   |
| address.addressLine2       | NA                                         | <p><br></p>                                                                                                                                                                   |
| address.landmark           | NA                                         | <p><br></p>                                                                                                                                                                   |
| address.city               | OrgUnit?                                   | <p><br></p>                                                                                                                                                                   |
| address.pincode            | NA                                         | <p><br></p>                                                                                                                                                                   |
| address.buildingName       | NA                                         | <p><br></p>                                                                                                                                                                   |
| address.street             | NA                                         | <p><br></p>                                                                                                                                                                   |
| address.locality.code      | OrgUnit.code                               | <p><br></p>                                                                                                                                                                   |
| address.locality.label     | OrgUnit.name                               | <p><br></p>                                                                                                                                                                   |
| address.locality.latitude  | NA                                         | <p><br></p>                                                                                                                                                                   |
| address.locality.longitude | NA                                         | <p><br></p>                                                                                                                                                                   |

### Inventory Management

At the start of the campaign we will need to ingest data from the physical count form. Entry and Exits are tracked through the entry and exit form mentioned above. We will need to do this for District and Community warehouses. The fields remain the same only the forms are changing. Which means the appropriate IDs will also change. The following are the forms:

| AD (Armazém distrital) - Entradas           | District Warehouse - Entry           |
| ------------------------------------------- | ------------------------------------ |
| AD (Armazém distrital) - Saidas             | District Warehouse - Exit            |
| AD (Armazém distrital)- Contagem física     | District Warehouse - Physical Count  |
| AC (Armazem Comunitarial) - Entradas        | Community Warehouse - Entry          |
| AC (Armazem Comunitarial) - Saidas          | Community Warehouse - Exit           |
| AC (Armazem Comunitarial) - Contagem física | Community Warehouse - Physical count |

| DIGIT Field          | DHIS2 Source              | Comments                                                                                                                                                                           |
| -------------------- | ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| clientReferenceId    | FormInstance.ID           | This is will be unique identity of the FormEntryInstance                                                                                                                           |
| tenantId             | <p><br></p>               | <p><br></p>                                                                                                                                                                        |
| facilityId           | Armazém distrital         | This will be the district warehouse or community warehouse ID. We will need to fetch and do a mapping. This facility will be mapped to the project so we need only the facilityId. |
| productVariantId     | <p><br></p>               | This is a DIGIT field, created as part of master data creation                                                                                                                     |
| quantity             | Nr. da guia de remessa \* | <p><br></p>                                                                                                                                                                        |
| referenceId          | <p><br></p>               | Unsure of what this is                                                                                                                                                             |
| referenceType        | Entrada ou Devolucao      | Entry or Exit                                                                                                                                                                      |
| transactionReason    | Entrada ou Devolucao      | <p><br></p><p>Return</p>                                                                                                                                                           |
| transactingPartyId   | <p><br></p>               | User ID of the transacting party                                                                                                                                                   |
| transactingPartyType | WAREHOUSE                 | <p><br></p>                                                                                                                                                                        |

### Supervisor Checklist

The spec of the survey service is being worked on at the product side. Once the design is completed, this section will be addressed.

## DHIS2 Service Delivery form&#x20;

On DHIS2 there is a single form that captures Bednet distribution as well as household registration (Both the required transactional data fields). This form is called “Ficha de Registo dos Agregados Familiares”. We will have to convert this single form data into two DIGIT payloads - Beneficiary and Benefit (or Service Delivery or Task).

All data is collected at a village level only in DHIS2. This form has the following fields.

| DHIS2 Field Name                                                                                           | DIGIT Field                                                                                                                                                    | Comments                                                                                                                                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Org Unit                                                                                                   | <p>Beneficiary.projectId, Beneficiary.address[].locality,</p><p>Benefit.projectId,</p><p>Benefit.address[].locality</p>                                        | This corresponds to the Village in which the Bed Nets are distributed. Each Org Unit has a different unique identifier. This mapping needs to be maintained in configuration.                                                                  |
| Latitude                                                                                                   | <p>Beneficiary.address[].latitude,</p><p>Beneficiary.address[].locality.latitude</p><p>Benefit.address[].locality.latitude, Benefit.address[].latitude</p>     | <p><br></p>                                                                                                                                                                                                                                    |
| Longitude                                                                                                  | <p>Beneficiary.address[].longitude,</p><p>Beneficiary.address[].locality.longitude</p><p>Benefit.address[].locality.longitude, Benefit.address[].longitude</p> | <p><br></p>                                                                                                                                                                                                                                    |
| Equipe de distribuição                                                                                     | Beneficiary.userId, Benefit.createdBy                                                                                                                          | This is the user who does the distribution. Typically this is the user who distributes the Bednets.                                                                                                                                            |
| Data hoje                                                                                                  | Beneficiary.dateOfRegistration, Benefit.plannedStartDate, Benefit.plannedEndDate, Benefit.actualStartDate, Benefit.actualEndDate, Benefit.createdDate          | Date when the form was filled/service was delivered.                                                                                                                                                                                           |
| Nome do(a) chefe do agregado familiar                                                                      | Beneficiary.name.givenName                                                                                                                                     | DHIS2 captures the full name of the head of the household. There is no way to syntactically split it into Given Name, Surname and otherNames as needed for the DIGIT ecosystem. So the assumption is that only the givenName will be populated |
| Selecione equipe de distribuição                                                                           | Beneficiary.userId, Benefit.createdBy                                                                                                                          | <p><br></p>                                                                                                                                                                                                                                    |
| Número de membros do agregado familiar que vivem na mesma casa (incluindo o(a) chefe do agregado familiar) | Beneficiary.memberCount                                                                                                                                        | <p><br></p>                                                                                                                                                                                                                                    |
| Número de redes por atribuir                                                                               | <p><br></p>                                                                                                                                                    | No equivalent in DIGIT payload for service delivery. This is a calculated field on the UI. No persistence. The aggregate for a village will be persisted at the equivalent project level.                                                      |
| Número de redes distribuídas                                                                               | Benefit.resources\[].quantity                                                                                                                                  | <p><br></p>                                                                                                                                                                                                                                    |
| Observações                                                                                                | Benefit.deliveryComment                                                                                                                                        | <p><br></p>                                                                                                                                                                                                                                    |
| Verifique se seus números estão corretos antes de finalizar este formulário                                | <p><br></p>                                                                                                                                                    | This field is to let the distributor validate the information present in the form.                                                                                                                                                             |

### DHIS2 Warehouse Inventory Tracking forms

| DHIS2 Field Name                                 | Translation                                          | DIGIT Field Mapping | Comments    |
| ------------------------------------------------ | ---------------------------------------------------- | ------------------- | ----------- |
| Entrada ou Devolucao                             | Incoming or Outgoing                                 | <p><br></p>         | <p><br></p> |
| Armazém distrital                                | District warehouse                                   | <p><br></p>         | <p><br></p> |
| Identificação do fiel armazém (nome completo)    | Identification of the faithful warehouse (full name) | <p><br></p>         | <p><br></p> |
| Proveniência                                     | Provenance                                           | <p><br></p>         | <p><br></p> |
| Especficar                                       | Specify                                              | <p><br></p>         | <p><br></p> |
| Nr. da guia de remessa                           | Delivery note number                                 | <p><br></p>         | <p><br></p> |
| Nr. matrícula ou tipo de transporte              | Registration no. or type of transport                | <p><br></p>         | <p><br></p> |
| Quantidade de redes indicadas na guia de remessa | Quantity of nets indicated on delivery note          | <p><br></p>         | <p><br></p> |
| Quantidade de redes recebidas                    | Quantity of nets received                            | <p><br></p>         | <p><br></p> |
| Comentário                                       | Comment                                              | <p><br></p>         | <p><br></p> |

