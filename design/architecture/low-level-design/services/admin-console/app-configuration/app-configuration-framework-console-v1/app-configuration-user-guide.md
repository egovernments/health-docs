# App Configuration User Guide

## Introduction

This document serves as a **basic user guide for configuring the App Configuration feature**.

The App Configuration system enables **dynamic screen rendering** through configuration, allowing application behavior and UI structure to be controlled without changing application code. Screens, modules, fields, and supporting UI elements are all driven by predefined configuration schemas.

To function correctly, the App Configuration feature relies on a **well-defined set of configurations**. These configurations act as the contract between the configuration data and the UI rendering layer. Any new screen, module, field type, or UI extension must follow this structure to ensure it is correctly interpreted and rendered by the application.

MDMS Configurations to be set up:-

1.  HCM-ADMIN-CONSOLE.NewBaseAppConfig &#x20;

    Hold template config of screens and flows for specific module and project type
2.  HCM-ADMIN-CONSOLE.FieldTypeMappingConfig

    List of types of field and their fieldType used to render on the screen and its meta data like type and format&#x20;
3.  HCM-ADMIN-CONSOLE.FieldPropertiesPanelConfig

    List of meta properties to be configured for each types of field.&#x20;

### How to add new module in App Configuration

To add new module in add configuration. You need to add config in **HCM-ADMIN-CONSOLE.NewBaseAppConfig**

**EXAMPLE**

```
{
   "name": "REGISTRATION", // name of the module 
   "order": 1, // order of flow 
   "active": true, // if true then appear on the app config screen
   "project": "MR-DN", // type of project for which module definition is there 
   "version": 1, // version of the module, it will be updated whenever configured from App configuration 
   "disabled": false, // is disabled it will be not selectable
   "initialPage": "searchBeneficiary" // deciding the first page of the flow
   "flows": [
   {
   "screenType": "TEMPLATE",
   ...
   },
   {
   "screenType": "FORM",
   ...
   }
   ]
}
```

**Screen Type can be Template or Form.**&#x20;

Template Screen type is defined for those screen where data capturing part is not happening and is used for navigation and it has its own defined layout like Inbox, Search Screen

Form Screen type is defined for those where data capturing is happening and has basic layout like Create Screen

**Template Screen Example**

```
{
  "name": "REGISTRATION",
  // Unique identifier for the module.
  // Used to group all related flows and screens under one module.

  "order": 1,
  // Defines the order in which this module appears in the App Configuration UI.

  "active": true,
  // If true, the module is visible in the App Configuration screen.

  "project": "MR-DN",
  // Project or application identifier for which this module is applicable.

  "version": 1,
  // Version of the module.
  // Automatically updated when changes are made via App Configuration.

  "disabled": false,
  // If true, the module will be visible but cannot be selected.

  "initialPage": "searchBeneficiary",
  // Defines the first screen that loads when the module flow starts.

  "flows": [
    // List of flows or screens belonging to this module.
    // For TEMPLATE screens, each flow generally maps to a single screen.

    {
      "name": "searchBeneficiary",
      // Unique name of the screen or flow.

      "order": 1,
      // Order of this screen within the module.

      "heading": "REGISTRATION_SEARCH_BENEFICIARY_HEADING",
      // Localization key for the screen heading.

      "screenType": "TEMPLATE",
      // Determines how the screen is rendered.
      // TEMPLATE screens are layout-driven and support header, body, and footer sections.

      "description": "REGISTRATION_SEARCH_BENEFICIARY_DESC",
      // Localization key for the screen description text.

      "header": [
        // Header section of the TEMPLATE screen.
        // Typically used for navigation controls such as Back buttons.

        {
          "label": "BACK",
          // Text shown for the header action.

          "format": "backLink",
          // Determines the UI component to be rendered.

          "onAction": [
            {
              "actionType": "BACK_NAVIGATION",
              // Built-in navigation action to go to the previous screen.

              "properties": {}
            }
          ]
        }
      ],

      "body": [
        // Main content section of the TEMPLATE screen.
        // All primary interactive fields are configured here.

        {
          "type": "template",
          // Defines the category of the field.
          // TEMPLATE fields rely on predefined UI layouts.

          "label": "PROXIMITY_SEARCH_REGISTRATION",
          // Localization key for the field label.

          "format": "proximitySearch",
          // Determines which UI component is rendered.
          // Mapped internally via field type configuration.

          "fieldName": "proximitySearch",
          // Unique identifier for the field.
          // Used to store and reference field values.

          "onAction": [
            {
              "actionType": "field.value==true ? SEARCH_EVENT : CLEAR_STATE",
              // Conditional action based on field value.

              "properties": {
                "data": [
                  {
                    "key": "",
                    "value": 5,
                    "operation": "within"
                  }
                ],
                "name": "address",
                "type": "field.value==true ? SEARCH_EVENT : CLEAR_STATE"
              }
            }
          ],

          "validations": [
            // Validation rules applied to this field.

            {
              "key": "proximityRadius",
              "value": 5,
              "errorMessage": "PROXIMITY_RADIUS_ERROR_MESSAGE"
            }
          ]
        }
      ],

      "footer": [
        // Footer section of the TEMPLATE screen.
        // Typically used for primary actions such as Submit or Next.

        {
          "type": "template",
          // Defines the field category.

          "label": "REGISTER_BENEFICIARY",
          // Localization key for the button label.

          "format": "button",
          // Determines the UI element to render.

          "fieldName": "registerBeneficiary",
          // Unique identifier for the footer action.

          "mandatory": true,
          // Indicates that the action is mandatory to proceed.

          "onAction": [
            {
              "actionType": "NAVIGATION",
              // Action that triggers screen navigation.

              "properties": {
                "data": [
                  {
                    "key": "nameOfIndividual",
                    "value": "{{searchBar.value}}"
                  }
                ],
                "name": "HOUSEHOLD",
                "type": "FORM"
              }
            }
          ],

          "properties": {
            // UI-specific properties for rendering the button.

            "size": "large",
            "type": "primary",
            "mainAxisSize": "max",
            "mainAxisAlignment": "center"
          }
        }
      ],

      "wrapperConfig": {
        // Static meta configuration required by the application.
        // These values are not configurable via App Configuration UI.
      }
    }
  ]
}

```

**Form Screen Example**

```
{
  "name": "REGISTRATION", 
  // Unique identifier for the module.
  // This value is used internally to map the module across configs and UI.

  "order": 1, 
  // Determines the sequence in which this module appears in the App Configuration UI.

  "active": true, 
  // Controls visibility of the module in the App Configuration screen.
  // If false, the module will not be shown.

  "project": "MR-DN", 
  // Specifies the project or domain to which this module belongs.
  // Used to scope configurations for different applications.

  "version": 1, 
  // Version of the module configuration.
  // This value is incremented automatically whenever the module is updated via App Configuration.

  "disabled": false, 
  // If true, the module is visible but not selectable in the UI.

  "initialPage": "searchBeneficiary", 
  // Defines the first page that will be loaded when this module flow starts.

  "flows": [ 
    // A module can contain multiple flows.
    // Each flow represents a logical user journey within the module.

    {
      "name": "ADD_MEMBER", 
      // Unique identifier for the flow.

      "order": 4, 
      // Determines the order of this flow within the module.

      "pages": [
        // List of screens/pages that belong to this flow.

        {
          "page": "beneficiaryDetails", 
          // Unique key identifying the page.

          "type": "object", 
          // Defines the data structure type for the page.
          // Typically used to group related fields.

          "label": "APPONE_REGISTRATION_BENEFICIARYDETAILS_SCREEN_HEADING_addmember", 
          // Localization key for the page heading.

          "order": 4, 
          // Determines the order of this page within the flow.

          "screenType": "FORM", 
          // Defines how the page should be rendered in the UI.
          // Example: FORM, REVIEW, SUMMARY, etc.

          "properties": [
            // List of fields rendered on this page.

            {
              "type": "string", 
              // Field type.
              // Used by the UI renderer to decide which component to render.

              "format": "text", 
              // Further refines the field type.
              // Example: text, number, email, date, etc.

              "fieldName": "nameOfIndividual", 
              // Key used for storing and retrieving field data.

              "label": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_nameOfIndividual_addmember", 
              // Localization key for the field label.

              "order": 1, 
              // Determines the position of the field on the page.

              "value": "", 
              // Default value of the field.

              "mandatory": true, 
              // Marks the field as mandatory.

              "hidden": false, 
              // If true, the field will not be visible in the UI.

              "readOnly": false, 
              // If true, the field will be displayed in read-only mode.

              "deleteFlag": false, 
              // Used to soft-delete the field from configuration without removing it.

              "systemDate": false, 
              // If true, the field value is auto-populated by the system date.

              "isMultiSelect": false, 
              // Applicable for dropdown or selection-based fields.

              "innerLabel": "", 
              // Optional secondary label shown inside the field.

              "tooltip": "", 
              // Short tooltip text displayed on hover.

              "helpText": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_nameOfIndividual_helpText_addmember", 
              // Localization key for additional help text shown to the user.

              "infoText": "", 
              // Informational text shown below or alongside the field.

              "errorMessage": "", 
              // Default error message placeholder.

              "validations": [
                // List of validation rules applied to the field.

                {
                  "type": "required", 
                  // Validation rule type.

                  "value": true, 
                  // Validation rule value.

                  "message": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_nameOfIndividual_mandatory_message_addmember"
                  // Localization key for validation error message.
                },
                {
                  "type": "minLength",
                  "value": "2",
                  "message": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_nameOfIndividual_min_message_addmember"
                },
                {
                  "type": "maxLength",
                  "value": "200",
                  "message": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_nameOfIndividual_max_message_addmember"
                }
              ]
            }
          ],

          "actionLabel": "APPONE_REGISTRATION_BENEFICIARYDETAILS_ACTION_BUTTON_LABEL_addmember", 
          // Localization key for the primary action button on the page.

          "description": "APPONE_REGISTRATION_BENEFICIARYDETAILS_SCREEN_DESCRIPTION_addmember"
          // Localization key for the page description or helper text.
        }
      ],

      "version": 1, 
      // Version of the flow configuration.

      "disabled": false 
      // If true, the entire flow is disabled and cannot be selected.
    }
  ]
}

```

### How to Add a New Field Type

Field Types define **how a field configuration is translated into a UI component**.\
Every field rendered in the App Configuration UI is resolved using the **Field Type Mapping Configuration**.

The system reads the field’s `type` and `format` from the screen configuration and uses the **FieldTypeMappingConfig** to determine:

* Which UI component should be rendered
* How the field should behave
* What metadata it supports

All field type mappings are defined in: _**HCM-ADMIN-CONSOLE.FieldTypeMappingConfig**_

#### Field Type Resolution Flow

1. A screen configuration defines a field using `type` and `format`
2. The App Configuration engine looks up a matching entry in `FieldTypeMappingConfig`
3. The mapped `fieldType` determines which UI component is rendered
4. Metadata is passed to the component for rendering and validation

#### Basic Field Type Configuration Structure

Each field type mapping must define:

| Key         | Description                                                |
| ----------- | ---------------------------------------------------------- |
| `type`      | Logical field type used in screen configuration            |
| `order`     | Rendering priority when multiple mappings exist            |
| `metadata`  | Criteria used to match the field configuration             |
| `fieldType` | <p></p><p>UI component identifier used by the renderer</p> |

```
{
  "type": "text",
  // Logical field type referenced in screen configuration

  "order": 1,
  // Determines priority when resolving field types

  "metadata": {
    "type": "string",
    // Data type of the field value

    "format": "text"
    // Format used to distinguish input variations
  },

  "fieldType": "textInput"
  // UI component key used by the renderer
}
```

#### Adding a Custom Component Field Type

For advanced use cases, custom UI components can be introduced as field types.

1. Use `component` as the `fieldType`, and specify the component name as the key:

```
{
  "type": "custom",
  "order": 10,
  "metadata": {
    "type": "component",
    "format": "customComponent"
  },
  "fieldType": "component"
}

```

2. Create a React component whose name matches the `component` value
3. Register the custom component in the component registry.

#### Common Issues and Troubleshooting

| Issue                    | Cause                                         |
| ------------------------ | --------------------------------------------- |
| Field not rendering      | Missing or incorrect FieldTypeMappingConfig   |
| Blank screen             | Component not registered in ComponentRegistry |
| Wrong component rendered | Conflicting `type` + `format` mappings        |
| Validation not working   | Metadata mismatch                             |

### How to Add Drawer Panel Properties

Drawer Panels are used to **configure field-level properties** from the App Configuration UI.\
These properties appear when a user selects a field and opens the **properties drawer**.

All drawer panel configurations are managed through a **single centralized configuration**:

HCM-ADMIN-CONSOLE.FieldPropertiesPanelConfig

This configuration defines:

* What properties are editable for a field
* On which **tab** (Content / Validation) the property appears
* Which **field types** the property applies to
* How the property behaves in the UI (toggle, input, conditional fields, etc.)

#### Important Design Principle

There is **only one object** that holds **all drawer property configurations**.

To add a new property:

* You **must edit this existing object**
* Add the property definition inside either:
  * `content` array → for UI/content-related properties
  * `validation` array → for validation-related properties

The array you choose determines **which tab** the property appears under in the drawer panel. If you want to introduce new tab you can do that.

#### Drawer Property Resolution Flow

1. User selects a field in App Configuration
2. Drawer panel opens
3. System reads `FieldPropertiesPanelConfig`
4. Properties are filtered based on:
   * Active tab (Content / Validation)
   * Field type (`visibilityEnabledFor`)
5. Matching properties are rendered dynamically in the drawer

#### Basic Drawer Property Configuration Structure

Each drawer property configuration supports the following keys:

| Key                    | Description                                                    |
| ---------------------- | -------------------------------------------------------------- |
| `id`                   | Unique identifier for the property                             |
| `label`                | Display label shown in the drawer                              |
| `order`                | Position of the property within the tab                        |
| `bindTo`               | Field configuration key this property updates                  |
| `fieldType`            | UI control type rendered in the drawer                         |
| `defaultValue`         | Default value assigned when property is enabled                |
| `conditionalField`     | Field(s) shown conditionally                                   |
| `showFieldOnToggle`    | Controls conditional rendering                                 |
| `visibilityEnabledFor` | <p></p><p>Field types for which this property is available</p> |

#### Example: Adding a Help Text Property

To allow configuration of **help text** for supported field types, add the following entry to the **`content` array** of `FieldPropertiesPanelConfig`:

```
{
  "id": "helpText",
  // Unique identifier for the drawer property

  "label": "helpText",
  // Display label shown in the drawer panel

  "order": 3,
  // Position of this property in the Content tab

  "bindTo": "helpText",
  // Field configuration key this property updates

  "fieldType": "toggle",
  // UI control rendered in the drawer (toggle, input, dropdown, etc.)

  "defaultValue": "",
  // Default value applied when the property is enabled

  "conditionalField": [
    {
      "type": "textArea",
      // Field rendered when toggle is enabled

      "bindTo": "helpText"
      // Binds user input to the same field config key
    }
  ],

  "showFieldOnToggle": true,
  // Displays conditionalField only when toggle is enabled

  "visibilityEnabledFor": [
    "text",
    "checkbox",
    "radio",
    "numeric",
    "Image",
    "date",
    "dropdown",
    "number",
    "mobileNumber"
  ]
  // List of field types for which this drawer property is visible
}


```

#### How This Reflects in the UI

* Property appears under the **Content** tab in the drawer
* A toggle labeled **Help Text** is shown
* When enabled, a textarea input appears
* The entered value is stored in the field’s `helpText` key
* Property is only visible for supported field types

#### Adding Validation Properties

To add validation-related properties:

* Place the configuration inside the `validation` array instead of `content`
* Bind to validation-specific keys (e.g., `mandatory`, `minLength`, `pattern`)
* Use `visibilityEnabledFor` to restrict applicability

#### Dependent Fields (Display Logic)

The display logic property allows adding conditional display logic to\
form fields. When enabled, you configure an expression that determines whether\
this field is visible based on other fields' values.

**Where it's stored in config:** field.visibilityCondition.expression

**How it works:**

1. In the Validation tab, toggle ON the display logic property
2. A condition builder UI appears
3. You select a field from the current page, a comparison operator, and a value
4. The expression is stored as a string like "fieldName == 'someValue'"

**Supported field types for dependency:** checkbox, numeric, date, dob, select, dropdown, idPopulator, mobileNumber, number, textarea, text, latLng, radio, administrativeArea, searchableDropdown

Example config result:&#x20;

`{ "type": "string", "format": "text", "fieldName": "referralReason", "label": "REFERRAL_REASON", "visibilityCondition": { "expression": "referralRequired == true" } }`

#### Best Practices

* Keep `id` and `bindTo` values consistent
* Use `visibilityEnabledFor` to avoid invalid configurations
* Prefer toggles for optional properties
* Avoid duplicating `bindTo` keys across properties
* Maintain logical `order` values for usability

#### Common Issues and Troubleshooting

| Issue                         | Cause                                                |
| ----------------------------- | ---------------------------------------------------- |
| Property not visible          | Field type not included in `visibilityEnabledFor`    |
| Value not saved               | Incorrect `bindTo` key                               |
| Conditional field not showing | `showFieldOnToggle` missing or false                 |
| Property in wrong tab         | Added to incorrect array (`content` vs `validation`) |

### Summary

The App Configuration system is designed to **dynamically drive application UI and behavior through configuration**, enabling scalable and extensible screen management without code changes.

This guide covered the **core building blocks required to extend App Configuration safely and correctly**, including:

* **Module Configuration**\
  How to define new modules, control flow order, enable or disable visibility, and configure entry points for dynamic screens.
* **Screen and Flow Configuration**\
  How FORM and TEMPLATE screens are structured, how header, body, and footer sections are configured, and how navigation and actions are handled.
* **Field Type Configuration**\
  How fields are rendered using `FieldTypeMappingConfig`, how `type` and `format` map to UI components, and how to introduce custom components through `ComponentRegistry`.
* **Drawer Panel Properties Configuration**\
  How field-level properties are managed centrally through `FieldPropertiesPanelConfig`, how properties are grouped under Content and Validation tabs, and how visibility and conditional rendering are controlled per field type.

Together, these configurations form a **contract between configuration data and the UI rendering engine**. Any new capability—whether a field, validation, screen, or UI extension—must follow these patterns to ensure consistency, maintainability, and predictable behavior.

By adhering to the rules and best practices outlined in this guide, developers and configurators can:

* Extend the application confidently
* Avoid breaking existing screens
* Maintain backward compatibility
* Keep configuration scalable and easy to manage

This document should be used as the **primary reference** when introducing or modifying App Configuration features.
