---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/architecture/low-level-design/services/admin-console/app-configuration/technical-documentation-improved/template-documentation
---

# Template documentation

### **Template Screens & App Configuration – Technical Design Documentation** <a href="#id-7tg5oljwneba" id="id-7tg5oljwneba"></a>

### **1. Introduction** <a href="#hrnzorcz5db" id="hrnzorcz5db"></a>

The **Template Screen** is a metadata-driven, dynamic UI architecture for managing\
project- or campaign-based workflows. Its purpose is to decouple UI structure\
from UI behavior, placing all layout, ordering, visibility, and localisation\
logic into a centrally managed **MDMS** (Master Data Management System)

Key benefits include:

* Consistent, reusable component definitions
* Complete multi-language support with live preview
* Version-controlled, maintainable configurations
* Easier campaign rollouts without code redeployment



At its core, the system uses:

* **Layout Renderer** as the dynamic template renderer (renders components inside a mobile bezel preview)
* **ComponentRegistryService** as a component resolver (maps format to React components, defined in Module.js)
* **DrawerFieldComposer** as the right-side property editor panel with Content and Validation tabs
* **MDMS configurations** as a single source of truth for all field configs, field type mappings, and property panel definitions



### **2. Architecture Overview** <a href="#h1hu0fdcsbe4" id="h1hu0fdcsbe4"></a>

**2.1 Rendering Pipeline**

**MDMS Config** (flows/pages/fields)\
|\
v\
**NewCampaignCreate/transformMdmsConfig.js** -- Initial Transform (MDMS -> App Config flat format)\
Converts validations\[] to flat keys, enums to\
dropDownOptions, onAction to conditionalNavigateTo, etc.

|\
v\
**AppConfigurationWrapper.js** -- Loads page config, dispatches to Redux\
|\
v\
**remoteConfigSlice**.initializeConfig() -- Stores currentData in Redux\
|\
v\
**NewLayoutRenderer.js** -- Renders template page preview\
\
For each field in body\[0].fields:\
1\. Filter hidden fields\
2\. Sort by order\
3\. Call renderTemplateComponent(field, ...)\
\
&#x20;**templateRendererHelpers.js**

1\. getComponentName(field.format, fieldTypeMasterData) -> e.g., "ButtonTemplate"

2\. ComponentRegistryService.getComponent("ButtonTemplate") -> React component

3\. Render \<Component field={field} t={t} ... />

4\. If no component found -> fallback placeholder\
|\
**Footer** rendered in sticky bottom section\
**actionPopup** fields render PopUp overlay

**2.2 Mandatory Fields in Config**

Every component MUST have these three fields for the renderer to work:

| Field         | Required | Description                                                        |
| ------------- | -------- | ------------------------------------------------------------------ |
| **type**      | YES      | "string", "integer", "boolean", "template", or "object"            |
| **format**    | YES      | Component format identifier (e.g., "panelCard", "button", "table") |
| **fieldName** | YES      | Unique identifier for the field within the page                    |

**2.3 Page Types**

| pageType   | screenType | Layout          | Field Access                                          |
| ---------- | ---------- | --------------- | ----------------------------------------------------- |
| "object"   | "FORM"     | Multi-card form | body\[cardIndex].fields\[fieldIndex]                  |
| "template" | "TEMPLATE" | Template layout | Recursive tree search by fieldName in body\[0].fields |

### **3. App Configuration Feature** <a href="#gtyqadeg93ei" id="gtyqadeg93ei"></a>

The App Configuration feature supports implementation teams and administrators to:

* design dynamic forms<br>
* visually reorder or edit fields<br>
* add new pages and sections - (Only at the base config, not through Console in current version.)<br>
* manage labels and multi-language strings<br>
* preview final mobile app configurations before deployment<br>

#### **3.1 UI Flow** <a href="#id-9xgzla296dwy" id="id-9xgzla296dwy"></a>

The configuration UI includes:<br>

1. Administrator clicks "Configure Mobile App"
2. Chooses one or more enabled modules
3. App configuration screen loads based on MDMS
4. User edits the form structure or template design using the drawer panel properties
5. User submits the final configuration
6. The new MDMS config is version-controlled and available to render immediately in the mobile application

#### 3.2 Typical User Flow

* Set components as hidden or shown
* Manage localisation for each component label and its properties
* Save, submit, or update configurations

#### Supported Actions:

* label
* tooltip
* validations
* hide/show
* localisation keys<br>

### **4. Data & State Layers**  <a href="#yoyhukh04hpr" id="yoyhukh04hpr"></a>

✅ **Parent Layer**

* Fetches and restructures the MDMS configuration on load<br>
* Normalizes data for easy preview<br>

✅ **Localisation Layer**

* Handles which fields are localisable<br>
* Provides live translation preview<br>

✅ **App Config Wrapper**

* Renders the live preview of the configured screen<br>
* Handles user edits through the side drawer

✅**Redux State Management**

* **remoteConfigSlice**: Config state (currentData, selectedField, selectedFieldPath, pageType)
* **fieldMasterSlice**: Field type master data
* **fieldPanelPropertiesSlice**: Panel configuration
* **localizationSlice**: Multi-language management

<br>

### **5. Data Transformation Pipeline** <a href="#ogoec1g7twpm" id="ogoec1g7twpm"></a>

#### 5.1 Initial Transform: NewCampaignCreate/transformMdmsConfig.js

When a campaign config is first loaded from MDMS, this transformer converts it to the flat App Config format used by the editor:

**For TEMPLATE screens:**

* Copies body, footer, header, heading, description directly
* Transforms nested validations\[] arrays back to flat field properties
* Extracts primaryActionLabel / secondaryActionLabel from panelCard actions

**For FORM screens:**

* Converts properties\[] (the runtime format) back to fields\[]
* Maps enums -> dropDownOptions and sets isMdms flag based on schemaCode presence
* Flattens grouped validations: validations: \[{type: "min", value: 5}] -> range: {min: 5}
* Extracts conditionalNavigateTo from flow-level onAction for the last page

#### 5.2 Final Transform: NewAppConfiguration/transformers/mdmsToAppConfig.js

When saving back, this transformer converts the editor format back to the runtime MDMS format:

**For TEMPLATE fields:**

| Format            | Transformation Applied                                                                                                 |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------- |
| panelCard         | Copies primaryActionLabel/secondaryActionLabel back into nested action objects                                         |
| searchBar         | Builds validations: \[{type: "minSearchChars", value: N}] from flat minSearchChars                                     |
| scanner/qrScanner | Builds validations\[] from flat scanLimit, isGS1, pattern, pattern.message                                             |
| Dropdown types    | If isMdms === true -> keeps schemaCode, clears enums \| if false -> copies dropDownOptions to enums, clears schemaCode |



**For FORM fields:**

* Builds validations\[] array from flat properties: required, pattern, min, max, minLength, maxLength, isGS1, scanLimit, minSearchChars
* Groups related validations: range.min / range.max -> validations: \[{type: "min"}, {type: "max"}]
* Retains non-configurable validations (e.g., notEqualTo, custom) as-is from original validations\[]
* Maps dropDownOptions -> enums or schemaCode based on isMdms flag

#### 6. Template components what can be modified

Each template component is registered in Module.js and rendered by NewLayoutRenderer.\
Below is every template component, what config properties it reads, and which\
properties can be modified through the Admin Console drawer panel.

**6.1 PanelCard (format: "panelCard")**

**Component:** PanelCardTemplate.js | Registered as: PanelCard

**What it renders:** A full-width status panel (success/error) with heading, description, and primary/secondary action buttons.

**Config properties:**

| Property                      | Type              | Modifiable in Drawer                        |
| ----------------------------- | ----------------- | ------------------------------------------- |
| label / heading               | locale code       | YES - via panelTitle property               |
| description                   | locale code       | YES - via panelDescription property         |
| properties.type               | "success"/"error" | Read from FieldTypeMappingConfig            |
| primaryAction                 | object            | YES - click button in preview to edit label |
| primaryAction.label           | locale code       | YES                                         |
| primaryAction.properties.type | string            | NO (always forced to "primary")             |
| primaryAction.onAction        | array             | NO (base config only)                       |
| secondaryAction               | object            | YES - click to edit label                   |
| secondaryAction.label         | locale code       | YES                                         |
| primaryActionLabel            | locale code       | Auto-managed (save transform)               |
| secondaryActionLabel          | locale code       | Auto-managed (save transform)               |

Example config:&#x20;

`{ "type": "template", "format": "panelCard", "fieldName": "successCard", "label": "DELIVERY_SUCCESS_HEADING", "description": "DELIVERY_SUCCESS_DESC", "properties": { "type": "success" }, "primaryAction": { "type": "template", "format": "button", "fieldName": "viewBtn", "label": "VIEW_DETAILS", "properties": { "type": "primary" }, "onAction": [{ "actionType": "NAVIGATION", "properties": { "name": "overview", "type": "TEMPLATE" } }] }, "secondaryAction": { "type": "template", "format": "button", "fieldName": "goBack", "label": "GO_BACK", "properties": { "type": "secondary" } } }`

**6.2 Button (format: "button")**

**Component:** ButtonTemplate.js | Registered as: ButtonTemplate

**What it renders:** A styled button with label and optional icon.

**Config properties:**

| Property                               | Type                             | Modifiable in Drawer             |
| -------------------------------------- | -------------------------------- | -------------------------------- |
| label                                  | locale code                      | YES                              |
| properties.type / properties.variation | "primary"/"secondary"/"tertiary" | Read from FieldTypeMappingConfig |
| properties.icon                        | icon name                        | Read from FieldTypeMappingConfig |
| onAction                               | array                            | NO (base config only)            |
| hidden                                 | boolean                          | YES - toggle hide/show           |

**6.3 Card (format: "card")**

**Component:** CardTemplate.js | Registered as: CardTemplate Editable: false (non-editable container - clicking does not open drawer)

**What it renders:** A container card that renders nested children components recursively.

| Property            | Type                  | Modifiable in Drawer               |
| ------------------- | --------------------- | ---------------------------------- |
| properties.cardType | "primary"/"secondary" | NO (editable: false)               |
| children            | array                 | Children ARE individually editable |
| hidden              | boolean               | YES - toggle hide/show             |

_<mark style="color:red;background-color:$warning;">**Note:**</mark> <mark style="color:red;">While the Card itself is not editable, each child component inside it is clickable and editable through the drawer.</mark>_

**6.4 Table (format: "table")**

**Component:** TableTemplate.js | Registered as: TableTemplate

**What it renders:** A data table with configurable column headers and visibility toggles.

| Property                  | Type          | Modifiable in Drawer                              |
| ------------------------- | ------------- | ------------------------------------------------- |
| data.columns              | array         | YES - via "table" property in drawer              |
| data.columns\[].header    | locale code   | YES - localization input per column               |
| data.columns\[].isActive  | boolean       | YES - toggle per column (cannot hide last column) |
| data.columns\[].cellValue | string/obj    | NO (base config only)                             |
| data.rows                 | template expr | NO (base config only)                             |

**Drawer behavior:** The "table" fieldType in NewDrawerFieldComposer renders a list of columns with:

* A toggle per column to show/hide it (isActive)
* A localization input per column for the header text
* Prevents hiding the last visible column

Example config:&#x20;

`{ "type": "template", "format": "table", "fieldName": "deliveryTable", "data": { "rows": "{{contextData.0.targetCycle.0.deliveries}}", "columns": [ { "header": "DOSE", "isActive": true, "cellValue": "DOSE {{item.id}}" }, { "header": "STATUS", "isActive": true, "cellValue": { "@default": "PENDING", "@condition": [...] } }, { "header": "COMPLETED_ON", "isActive": true, "cellValue": "{{fn:getDate(item.id)}}" } ] } }`

**6.5 LabelFieldPair / LabelPairList (format: "labelPairList")**

**Component:** LabelFieldPairTemplate.js | Registered as: LabelFieldPair

**What it renders:** A vertical list of label-value pairs (like a details card showing key-value information).

| Property      | Type          | Modifiable in Drawer                         |
| ------------- | ------------- | -------------------------------------------- |
| data          | array         | YES - via "labelPairList" property in drawer |
| data\[].key   | locale code   | YES - localization input per pair            |
| data\[].value | template expr | NO (base config only)                        |

**Drawer behavior:** The "labelPairList" fieldType renders a multi-select picker from MDMS labelPairConfig categories. Each selected pair gets a localization input for its key label. The data array is the source - you select which pairs to display and set their localized labels. Values are template expressions resolved at runtime from context data.

Example config:&#x20;

`{ "type": "template", "format": "labelPairList", "fieldName": "memberDetails", "data": [ { "key": "NAME_OF_INDIVIDUAL", "value": "{{contextData.0.name}}" }, { "key": "AGE", "value": "{{fn:formatDate(contextData.0.dob, 'age')}}" }, { "key": "GENDER", "value": "{{contextData.0.gender}}" } ] }`

**6.6 InfoCard (format: "infoCard")**

**Component:** InfoCardTemplate.js | Registered as: InfoCard

**What it renders:** An alert/info card with label and description text.

| Property                | Type                               | Modifiable in Drawer               |
| ----------------------- | ---------------------------------- | ---------------------------------- |
| label                   | locale code                        | YES - via label property           |
| description             | locale code                        | YES - via infoDescription property |
| properties.infoCardType | "info"/"success"/"error"/"warning" | Read from FieldTypeMappingConfig   |

**6.7 Tag (format: "tag")**

**Component:** TagTemplate.js | Registered as: Tag

**What it renders:** A small tag/badge component.

| Property           | Type                                     | Modifiable in Drawer             |
| ------------------ | ---------------------------------------- | -------------------------------- |
| fieldName          | string                                   | Editable only on creation        |
| properties.tagType | "success"/"error"/"warning"/"monochrome" | Read from FieldTypeMappingConfig |

**6.8 MenuCard (format: "menu\_card")**

**Component:** MenuCardTemplate.js | Registered as: MenuCardTemplate

**What it renders:** A clickable menu card with icon, heading, and description.

| Property               | Type        | Modifiable in Drawer                   |
| ---------------------- | ----------- | -------------------------------------- |
| heading                | locale code | YES - via menuCardTitle property       |
| description            | locale code | YES - via menuCardDescription property |
| icon / properties.icon | string      | NO (base config only)                  |
| onAction               | array       | NO (base config only)                  |
| disabled               | boolean     | NO (base config only)                  |

**6.9 Switch / Toggle (format: "switch")**

**Component:** SwitchTemplate.js | Registered as: Toggle

**What it renders:** A toggle switch with a label.

| Property | Type        | Modifiable in Drawer     |
| -------- | ----------- | ------------------------ |
| label    | locale code | YES - via label property |
| value    | boolean     | NO (runtime state)       |

Also used for: proximitySearch, searchByProximity, searchByID formats (all render the same Toggle component).

**6.10 SearchBar (format: "searchBar")**

**Component:** SearchBar.js | Registered as: SearchBar

**What it renders:** A search input field.

| Property       | Type        | Modifiable in Drawer                           |
| -------------- | ----------- | ---------------------------------------------- |
| label          | locale code | YES - via label property                       |
| minSearchChars | number      | YES - via minSearchChars property (default: 2) |

Transform behavior: On save, minSearchChars is converted to:&#x20;

`validations: [{type: "minSearchChars", value: N, message: "..."}]`&#x20;

On load, the validations array is flattened back to field.minSearchChars.

**6.11 Scanner / QR Scanner (format: "scanner" or "qrScanner")**

**Component:** Scanner.js (QRScanner) | Registered as: QRScanner

**What it renders:** A button with QR code scanner icon.

| Property          | Type        | Modifiable in Drawer                                      |
| ----------------- | ----------- | --------------------------------------------------------- |
| label             | locale code | YES - via label property                                  |
| scanLimit         | number      | YES - toggle + number input                               |
| scanLimit.message | locale code | YES - text input                                          |
| isGS1             | boolean     | YES - toggle (mutually exclusive with pattern)            |
| pattern           | string      | YES - toggle + text input (mutually exclusive with isGS1) |
| pattern.message   | locale code | YES - text input                                          |

Transform behavior: On save, all these flat properties are bundled into validations\[]:&#x20;

`"validations": [ { "type": "scanLimit", "value": 3, "message": "SCAN_LIMIT_ERROR" }, { "type": "isGS1", "value": true }, { "type": "pattern", "value": "^[A-Z0-9]+$", "message": "PATTERN_ERROR" } ]`

<mark style="color:$success;">**Mutual exclusivity:**</mark> _<mark style="color:$warning;">**isGS1**</mark> and <mark style="color:$warning;">**pattern**</mark> cannot both be enabled. Enabling one disables the other in the drawer._

**6.12 QR View (format: "qr\_view")**

**Component:** QRView.js | Registered as: QRView What it renders: A QR code display icon (visual placeholder). No editable properties.

**6.13 Filter (format: "filter")**

**Component:** Filter.js | Registered as: Filter

**What it renders:** A filter icon with label and active filter count badge.

| Property        | Type        | Modifiable in Drawer             |
| --------------- | ----------- | -------------------------------- |
| label           | locale code | YES - via label property         |
| dropDownOptions | array       | YES - via filter toggle property |
| value           | array       | NO (runtime state)               |

**Drawer behavior:** The "filter" toggle in Content tab has dual conditional children:

* When ON (condition: true): Shows MDMS schema selector from predefined options
* When OFF (condition: false): Shows static options editor

**6.14 DropdownTemplate (format: "dropdownTemplate")**

**Component:** DropdownTemplate.js | Registered as: DropdownTemplate

What it renders: A dropdown/select field that supports both MDMS data and static options.

| Property              | Type        | Modifiable in Drawer                      |
| --------------------- | ----------- | ----------------------------------------- |
| label                 | locale code | YES - via label property                  |
| isMdms                | boolean     | YES - toggle                              |
| schemaCode            | string      | YES - dropdown when isMdms=true           |
| dropDownOptions/enums | array       | YES - options editor when isMdms=false    |
| helpText              | locale code | YES - toggle + textarea                   |
| tooltip               | locale code | YES - toggle + text input                 |
| prefixText            | string      | NO (not in visibilityEnabledFor)          |
| required              | boolean     | NO (not applicable for template dropdown) |
| readOnly              | boolean     | Rendered but not typically editable       |

Also used for dynamic components: **facilityFromWhich**, **facilityToWhich**, **productdetail**, **evaluationFacility** - these all use DropdownTemplate but with metadata.type: "dynamic".

**6.15 TextTemplate (format: "textTemplate")**

**Component:** TextTemplate.js | Registered as: TextTemplate What it renders: A simple text display showing fieldName : \*\*\*\*\*\*\*\* (masked value).

| Property  | Type   | Modifiable in Drawer |
| --------- | ------ | -------------------- |
| fieldName | string | Set on creation      |

**6.16 Row (format: "row" or "Row")**

**Component:** RowTemplate.js | Registered as: Row Editable: false (non-editable container)

**What it renders:** A horizontal flex container for child components.

| Property                      | Type    | Modifiable in Drawer               |
| ----------------------------- | ------- | ---------------------------------- |
| children                      | array   | Children are individually editable |
| properties.gap                | string  | NO (default: "8px")                |
| properties.mainAxisAlignment  | string  | NO                                 |
| properties.crossAxisAlignment | string  | NO                                 |
| properties.wrap               | boolean | NO                                 |

**6.17 Column (format: "column" or "Column")**

**Component:** ColumnTemplate.js | Registered as: Column Editable: false (non-editable container)

**What it renders:** A vertical flex container for child components.

| Property                      | Type   | Modifiable in Drawer               |
| ----------------------------- | ------ | ---------------------------------- |
| children                      | array  | Children are individually editable |
| properties.gap                | string | NO (default: "8px")                |
| properties.mainAxisAlignment  | string | NO                                 |
| properties.crossAxisAlignment | string | NO                                 |



**6.18 Expandable (format: "expandable")**

**Component:** ExpandableTemplate.js | Registered as: ExpandableTemplate Editable: false (non-editable container)

**What it renders:** A collapsible section with expand/collapse button and nested children.

| Property       | Type        | Modifiable in Drawer                   |
| -------------- | ----------- | -------------------------------------- |
| expandLabel    | locale code | NO (default: "VIEW\_MORE")             |
| collapseLabel  | locale code | NO (default: "HIDE")                   |
| children       | array       | Children are individually editable     |
| visible        | expression  | NO (e.g., "\{{fn:length(data)\}} > 0") |
| properties.gap | string      | NO                                     |

**6.19 ListView (format: "listView")**

**Component:** ListViewTemplate.js | Registered as: ListView Editable: false (non-editable container)

**What it renders:** A list that renders a single child template (preview shows one item).

| Property       | Type   | Modifiable in Drawer           |
| -------------- | ------ | ------------------------------ |
| child          | object | Child is individually editable |
| properties.gap | string | NO (default: "8px")            |

**6.20 ActionPopup (format: "actionPopup")**

**Component:** Uses Button for the trigger | Registered as: Button

**What it renders:** A button that opens a popup overlay with its own body fields and footer actions.

| Property                             | Type        | Modifiable in Drawer                |
| ------------------------------------ | ----------- | ----------------------------------- |
| label                                | locale code | YES                                 |
| properties.popupConfig.title         | locale code | YES - via popupTitle property       |
| properties.popupConfig.type          | string      | NO                                  |
| properties.popupConfig.body          | array       | Each field is individually editable |
| properties.popupConfig.footerActions | array       | Button labels are editable          |
| properties.popupConfig.titleIcon     | string      | NO                                  |

**Drawer behavior:** When you click an actionPopup field, the popup preview automatically opens. The popupTitle text property appears in the Content tab. Popup body fields and footer actions are editable by clicking them inside the popup preview.

**6.21 Other Template Components**

**TextInput** (format: "textInput") Component: TextInputTemplate.js | Registered as: TextInputTemplate Editable: false (preview only)

**RadioList** (format: "radioList") Component: RadioListTemplate.js | Registered as: RadioListTemplate Editable: false (preview only)

**Icon** (format: "icon") Component: IconTemplate.js | Registered as: IconTemplate Editable: false (preview only)

**SelectionCard** (format: "selectionCard") Component: SelectionCard | Registered as: SelectionCard Modifiable properties depend on usage context.





### &#x20; <a href="#bqjnqfunkwwa" id="bqjnqfunkwwa"></a>

### **7. MDMS Configurations** <a href="#id-3y4hpefqq57l" id="id-3y4hpefqq57l"></a>

### **7.1 FormConfig Example** <a href="#yyi786i7go6d" id="yyi786i7go6d"></a>

| <p>{<br>"name": "REGISTRATIONFLOW",<br>"order": 1,<br>"pages": [<br>{<br>"page": "SearchBeneficiary",<br>"type": "template",<br>"label": "APPONE_REGISTRATION_BENEFICIARY_SEARCH_SCREEN_HEADING",<br>"order": 1,<br>"navigateTo": { "name": "overview", "type": "template" },<br>"properties": [<br>{<br>"type": "template",<br>"format": "filter",<br>"jsonPath": "filter",<br>"order": 1<br>},<br>{<br>"type": "template",<br>"format": "searchByProximity",<br>"jsonPath": "searchByProximity",<br>"order": 2<br>},<br>{<br>"type": "template",<br>"format": "PrimaryButton",<br>"jsonPath": "PrimaryButton",<br>"order": 3<br>},<br>{<br>"type": "template",<br>"format": "searchBar",<br>"jsonPath": "searchBar",<br>"order": 4<br>},<br>{<br>"type": "template",<br>"format": "SecondaryButton",<br>"jsonPath": "SecondaryButton",<br>"order": 5<br>}<br>]<br>}<br>]<br>}</p> |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### **7.2 FieldTypeMappingConfig** <a href="#ij6lbx47ppwx" id="ij6lbx47ppwx"></a>

| <p>{<br>"type": "searchByProximity",<br>"metadata": { "type": "template", "format": "searchByProximity" },<br>"fieldType": "searchByProximity"<br>}</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- |

These components are defined with the template type, which means they cannot be added as standalone fields or components in other screens.

### **7.3 FieldPropertiesPanelConfig** <a href="#id-9bt3koumyj1j" id="id-9bt3koumyj1j"></a>

| <p>{<br>"tab": "content",<br>"label": "label",<br>"bindTo": "label",<br>"fieldType": "text",<br>"visibilityEnabledFor": [<br>"filter", "searchByProximity", "DetailsCard", "Table",<br>"PrimaryButton", "SecondaryButton"<br>]<br>}</p> |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Adding your component’s type to the visibilityEnabledFor property ensures that the label localisation field is available in the drawer panel, allowing users to dynamically translate and edit component labels in supported languages.

### **7.4 DETAILS\_RENDERER\_CONFIG** <a href="#a669na6d3yzj" id="a669na6d3yzj"></a>

| <p>{<br>"entity": "Task",<br>"displayFields": [<br>{ "fieldKey": "doseIndex", "jsonPath": "Task.additionalFields" },<br>{ "fieldKey": "status", "jsonPath": "Task.status" },<br>{ "fieldKey": "createdTime", "jsonPath": "Task.auditDetails.createdTime" }<br>]<br>}</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

This structure powers the nested options in the AppConfig drawer for **DetailsCard** and **Table** so users can dynamically select which fields to render, and override their labels.

### **8. Custom Components: DetailsCard/Table with Enums** <a href="#id-6v5d1th0hpa" id="id-6v5d1th0hpa"></a>

For **DetailsCard** or **Table**, the FormConfig uses an enums array:

| <p>{<br>"type": "template",<br>"format": "Table",<br>"jsonPath": "Table",<br>"order": 2,<br>"enums": [<br>{<br>"code": "Task.deliveryNo",<br>"name": "deliveryNo",<br>"jsonPath": "Task.additionalFields"<br>},<br>{<br>"code": "Task.status",<br>"name": "status",<br>"jsonPath": "Task.status"<br>}<br>]<br>}</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

These enums are dynamically sourced from the HCM-ADMIN-CONSOLE.DETAILS\_RENDERER\_CONFIG schema, enabling campaign users to flexibly select fields, assign localised labels, and even modify Table component column names

### **9. Summary** <a href="#b6m9r8vfaj1f" id="b6m9r8vfaj1f"></a>

<table data-header-hidden><thead><tr><th width="374"></th><th></th></tr></thead><tbody><tr><td><strong>Helpers</strong></td><td><strong>Description</strong></td></tr><tr><td><strong>FieldTypeMappingConfig</strong></td><td>Maps type and metadata so the admin console can recognize the field/component</td></tr><tr><td><strong>FieldPropertiesPanelConfig</strong></td><td>Controls what can be changed in the drawer editor</td></tr><tr><td><strong>LabelFieldPairConfig</strong></td><td>Provides reusable field keys for Label Pair Summary Card</td></tr><tr><td><strong>MDMS FormConfigTemplate</strong></td><td>Describes page flow, fields/components, ordering, and navigation - Base config</td></tr><tr><td></td><td></td></tr></tbody></table>

### **10. Best Practices** <a href="#id-6rqrr63ike52" id="id-6rqrr63ike52"></a>

* Always assign **unique fieldName** values within a page
* Use localization codes for all user-facing text (label, description, helpText, tooltip, error messages)
* Keep **type**, **format**, and **fieldName** as the minimum required properties on every field
* Keep field and entity codes consistent&#x20;
* Validate **localisation** keys across all supported languages
* Use the preview (mobile bezel) to verify layout before submitting
* Prefer stateless, pure React components
* For template components, remember that editable: false means the container itself cannot be selected in the drawer - only its children can
* **Navigation logic** is only editable where it already exists in the base config - you cannot add it to arbitrary pages
* **DEFAULT** and **custom** type navigation conditions are preserved and never shown in the editor
* When adding new properties, always handle both the load transform (flat -> editor) and save transform (editor -> MDMS)
* Document new template components thoroughly
* Always test edge cases in the preview environment before final submission

### 11. Extensibilty Guide

#### 11.1 Adding a New Template Component

**Step 1: Create the component in NewAppConfiguration/components/:**

```
// MyNewTemplate.js
const MyNewTemplate = ({ field, t, fieldTypeMasterData, selectedField, onFieldClick, isFieldSelected, data }) => {
  return (
    <div>
      <h3>{t(field.label)}</h3>
      <p>{t(field.description)}</p>
    </div>
  );
};
export default MyNewTemplate;
```

**Step 2: Register in Module.js:**

```
import MyNewTemplate from "./pages/employee/NewAppConfiguration/components/MyNewTemplate";
// In componentsToRegister:
componentsToRegister.MyNewTemplate = MyNewTemplate;
```

**Step 3: Add to FieldTypeMappingConfig (MDMS or dummyFieldTypeConfig.json):**

```
{
  "type": "myNew",
  "order": 28,
  "category": "advanced",
  "editable": true,
  "metadata": { "type": "template", "format": "myNew" },
  "component": "MyNewTemplate",
  "fieldType": "myNew",
  "properties": [
    { "code": "myProp", "options": ["optionA", "optionB"] }
  ]
}
```

**Step 4: Add editable properties to FieldPropertiesPanelConfig:**

```
{
  "id": "myLabel",
  "label": "myLabel",
  "order": 30,
  "bindTo": "label",
  "fieldType": "text",
  "visibilityEnabledFor": ["myNew"]
}
```

**Step 5: Use in config:**

```
{ "type": "template", "format": "myNew", "fieldName": "myField", "label": "MY_LABEL" }
```

#### 11.2 Adding a New Editable Property

1. Add to FieldPropertiesPanelConfig (content or validation tab) with appropriate bindTo, fieldType, and visibilityEnabledFor
2. If using a new fieldType not handled by NewDrawerFieldComposer, add a case in the RenderField switch
3. Add validation in AppConfigurationWrapper.checkAllFieldsValidation() if needed
4. Add transformation logic in both transformMdmsConfig.js (load) and mdmsToAppConfig.js (save) if the property needs special handling

#### 11.3 Adding a New Form Field Type

1. Add entry to FieldTypeMappingConfig with category: "basic" or advanced and appropriate metadata
2. Add the type to visibilityEnabledFor arrays of applicable properties in FieldPropertiesPanelConfig
3. The field will automatically render via the FieldV1 fallback if no custom component is registered

####

#### 12. Component Quick Reference

**Template Components (Editable):**

```

  Format          | Component             | Key Modifiable Properties
  ----------------|-----------------------|-------------------------------------------
  panelCard       | PanelCardTemplate     | label (heading), description, action labels
  button          | ButtonTemplate        | label
  table           | TableTemplate         | Column headers (localization), column visibility
  labelPairList   | LabelFieldPairTemplate| Field pair selection, pair labels
  infoCard        | InfoCardTemplate      | label, description
  menu_card       | MenuCardTemplate      | heading, description
  switch          | SwitchTemplate        | label
  searchBar       | SearchBar             | label, minSearchChars
  scanner/qrScanner| QRScanner            | label, scanLimit, isGS1, pattern
  filter          | Filter                | label, filter options (MDMS or static)
  dropdownTemplate| DropdownTemplate      | label, isMdms, schemaCode, dropDownOptions
  actionPopup     | Button (trigger)      | label, popup title, body/footer fields
  qr_view         | QRView                | (none)
  selectionCard   | SelectionCard         | (depends on usage)
```

**Template Components (Non-Editable Containers):**

```

  Format          | Component             | What's Inside
  ----------------|-----------------------|-------------------------------------------
  card            | CardTemplate          | children[] - each child IS editable
  row / Row       | RowTemplate           | children[] - horizontal layout
  column / Column | ColumnTemplate        | children[] - vertical layout
  expandable      | ExpandableTemplate    | children[] - collapsible section
  listView        | ListViewTemplate      | child - single item template
  textInput       | TextInputTemplate     | Preview only
  radioList       | RadioListTemplate     | Preview only
  icon            | IconTemplate          | Preview only
  textTemplate    | TextTemplate          | Preview only
```

**Dynamic Components (Advanced, MDMS-driven):**

```
 Format              | Component        | Description
  --------------------|------------------|-----------------------------------
  facilityFromWhich   | DropdownTemplate | Facility origin selector
  facilityToWhich     | DropdownTemplate | Facility destination selector
  productdetail       | DropdownTemplate | Product selector
  evaluationFacility  | DropdownTemplate | Evaluation facility selector
  resourceCard        | SelectionCard    | Resource selection
  select              | SelectionCard    | Generic selection component
```

<br>
