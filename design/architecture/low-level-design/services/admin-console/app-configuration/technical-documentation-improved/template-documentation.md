# Template documentation

### **Template Screens & App Configuration – Technical Design Documentation** <a href="#id-7tg5oljwneba" id="id-7tg5oljwneba"></a>

### **1. Introduction** <a href="#hrnzorcz5db" id="hrnzorcz5db"></a>

The **Template Screen** is a metadata-driven, dynamic UI architecture for managing project- or campaign-based workflows. Its purpose is to decouple UI structure from UI behavior, placing all layout, ordering, visibility, and localisation logic into a centrally managed MDMS (Master Data Management System).

Key benefits include:

* consistent, reusable component definitions<br>
* complete multi-language support<br>
* version-controlled, maintainable configurations<br>
* easier campaign rollouts without code redeployment<br>

At its core, the Template feature uses:

* **GenericTemplateScreen** as a dynamic renderer<br>
* **RegistrationComponentRegistry** as a component resolver<br>
* **TemplateRenderer** for advanced nested layouts / custom layouts<br>
* **MDMS configurations** for a single source of truth for app configurations<br>

### &#x20;<a href="#id-7n4xtdiwit3a" id="id-7n4xtdiwit3a"></a>

### &#x20;<a href="#y9ep86vk0qm6" id="y9ep86vk0qm6"></a>

### **2. Architecture Overview** <a href="#h1hu0fdcsbe4" id="h1hu0fdcsbe4"></a>

✅ **GenericTemplateScreen**

* Loads a page’s field configuration<br>
* Renders each field using the Registry<br>
* Supports a fixed button bar for Primary/Secondary actions<br>
* Delegates to a **TemplateRenderer** when a corresponding component is registered in the **RegistrationComponentRegistry** under the specified **templateName.**.

✅ **RegistrationComponentRegistry**

* Maps component jsonPath to a registered React component<br>

✅ **TemplateRenderer**

* Handles nested/grouped or repeated layouts with custom render logic

✅ **MDMS**

* Acts as the central, version-controlled data store for campaign and project configurations.<br>

### **3. App Configuration Feature** <a href="#gtyqadeg93ei" id="gtyqadeg93ei"></a>

The App Configuration feature supports implementation teams and administrators to:

* design dynamic forms<br>
* visually reorder or edit fields<br>
* add new pages and sections<br>
* manage labels and multi-language strings<br>
* preview final mobile app configurations before deployment<br>

#### **3.1 UI Flow** <a href="#id-9xgzla296dwy" id="id-9xgzla296dwy"></a>

The configuration UI includes:<br>

✅ **Drawer (Side Panel)**

* Provides field/component editing with:<br>
  * label<br>
  * tooltip<br>
  * validations<br>
  * hide/show<br>
  * localisation keys<br>

✅ **Supported Actions**<br>

* Reorder buttons in template screens via drag-and-drop<br>
* Set components as hidden or shown<br>
* Manage localisation for each component label and its properties<br>
* Save, submit, or update configurations

#### **3.2 Typical User Flow** <a href="#bigi5h9q0cf4" id="bigi5h9q0cf4"></a>

1. Administrator clicks **"Configure Mobile App"**<br>
2. Chooses one or more enabled modules<br>
3. App configuration screen loads based on MDMS<br>
4. User edits the form structure or template design using the drawer panel properties<br>
5. User submits the final configuration<br>
6. The new MDMS config is version-controlled and available to render immediately in the mobile application<br>

### **4. Data & State Layers**  <a href="#yoyhukh04hpr" id="yoyhukh04hpr"></a>

✅ **Parent Layer**

* Fetches and restructures the MDMS configuration on load<br>
* Normalizes data for easy preview<br>

✅ **Localisation Layer**

* Handles which fields are localisable<br>
* Provides live translation preview<br>

✅ **App Config Wrapper**

* Renders the live preview of the configured screen<br>
* Handles user edits through the side drawer<br>

### **5. Rendering Workflow in GenericTemplateScreen** <a href="#ogoec1g7twpm" id="ogoec1g7twpm"></a>

✅ Filters hidden fields\
✅ Splits Primary/Secondary buttons\
✅ Sorts button components by order\
✅ Delegates to TemplateRenderer if component with templateName exists\
✅ Otherwise loops through all fields and renders via the Registry\
✅ Buttons appear in a fixed-position footer

### **6. Extensibility Guide** <a href="#bqjnqfunkwwa" id="bqjnqfunkwwa"></a>

✅ **To add a new component:**

1. Implement a React component with<br>

| ({ field, t }) => { ... } |
| ------------------------- |

1. Register with the Registry<br>

| **registerComponent**("customComponent", CustomComponent); |
| ---------------------------------------------------------- |

1. Add to FormConfigTemplate with jsonPath and format<br>
2. If its label should be changeable in App Config, add its format to:<br>

* FieldPropertiesPanelConfig → visibilityEnabledFor<br>

1. Register its type in FieldTypeMappingConfig<br>
2. Validate on preview<br>

✅ **To add a nested TemplateRenderer:**

1. Write<br>

| ({ components, t }) => { ... } |
| ------------------------------ |

1. Register with getTemplateRenderer

| <p><strong>export</strong> <strong>const</strong> getTemplateRenderer = (templateName) => {</p><p><strong>switch</strong> (templateName) {<br><strong>case</strong> "AnotherTemplate":<br><strong>return</strong> anotherRenderer;<br>}<br>};</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

1. In MDMS Form Config, make sure templateName matches the page name
2. Validate end-to-end<br>

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

| **Helpers**                       | **Description**                                                               |
| --------------------------------- | ----------------------------------------------------------------------------- |
| **GenericTemplateScreen**         | Dynamic runtime renderer for a page                                           |
| **RegistrationComponentRegistry** | Maps jsonPath or format to React components                                   |
| **TemplateRenderer**              | Handles nested or grouped page layouts                                        |
| **FieldTypeMappingConfig**        | Maps type and metadata so the admin console can recognize the field/component |
| **FieldPropertiesPanelConfig**    | Controls what can be changed in the drawer editor                             |
| **DETAILS\_RENDERER\_CONFIG**     | Provides reusable field keys for DetailsCard and Table                        |
| **MDMS FormConfigTemplate**       | Describes page flow, fields/components, ordering, and navigation              |
|                                   |                                                                               |

### **10. Best Practices** <a href="#id-6rqrr63ike52" id="id-6rqrr63ike52"></a>

✅ Always assign **unique** jsonPath values\
✅ Keep field and entity codes consistent (entity.fieldKey)\
✅ Validate localisation keys across all supported languages\
✅ Prefer stateless, pure React components\
✅ Document new TemplateRenderers thoroughly\
✅ Always test edge cases in the preview environment before final submission

### **11. Conclusion** <a href="#id-1bct5sxtsp1b" id="id-1bct5sxtsp1b"></a>

This template feature provides a **metadata-first**, no-code-friendly strategy for dynamic app configuration. By leveraging:

* GenericTemplateScreen<br>
* RegistrationComponentRegistry<br>
* TemplateRenderer<br>
* FieldTypeMappingConfig<br>
* DETAILS\_RENDERER\_CONFIG<br>
