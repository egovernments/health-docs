---
hidden: true
---

# Technical Documentation (Improved)

1\. Overview

The App Configuration feature enables internal users—primarily system administrators and implementation teams—to design and manage dynamic forms for campaign- or project-based flows. This feature provides a visual UI for creating, updating, reordering, and removing form fields and sections. All configurations are structured, version-controlled, and tightly integrated with both localisation and the Master Data Management System (MDMS)

2\. UI Flow

The user interface is organized into several interactive layers to streamline the configuration process:

3\. Data & State Flow

4\. Core Logic and State Management

The feature uses React’s context and reducer patterns for robust state management:

[#id-6.-formconfigtemplate](../../../../../../../deploy/configuration/hcm-console-configuration/#id-6.-formconfigtemplate "mention")

```json
{
// Unique identifier for the configuration flow (e.g., registration, onboarding)
"name": "REGISTRATIONFLOW",
// Order in which this configuration appears among multiple flows
"order": 1,
// Array of page objects. Each object defines a screen or step in the flow.
"pages": [
{
// Unique name/identifier for the page/screen
"page": "SearchBeneficiary",
// Type of the page, often "template" for reusable layouts
"type": "template",
// Localisation key for the page heading, used for multi-language support
"label": "APPONE_REGISTRATION_SEARCHBENEFICIARY_SCREEN_HEADING",
// Numeric order of the page within the flow
"order": 1,
// Object specifying the next screen to navigate to after this page
"navigateTo": {
// Name of the target page/screen
"name": "overview",
// Type of the target page/screen
"type": "template"
},
// Array of field/property objects that define the UI components on this page
"properties": [
{
// Type of UI component or field (e.g., "template", "text", "dropdown")
"type": "template",
// Localisation key for the field label
"label": "APPONE_REGISTRATION_SEARCHBENEFICIARY_BY_PROXIMITY",
// Numeric order of the field within the page
"order": 1,
// Default value for the field; data type varies by field type
"value": true,
// UI rendering hint (e.g., "searchByProximity", "searchBar", "filter")
"format": "searchByProximity",
// If true, the field is hidden from the UI
"hidden": false,
// Tooltip text (usually localised) shown on hover for guidance
"tooltip": "",
// Help text (localised) displayed near the field for user assistance
"helpText": "",
// Additional informational text (localised) related to the field
"infoText": "",
// If true, the field is not editable by the user
"readOnly": false,
// Internal identifier for the field, used in data binding and logic
"fieldName": "searchByProximity",
// If true, marks the field for deletion (soft delete)
"deleteFlag": false,
// Placeholder or label shown inside the field (e.g., input placeholder)
"innerLabel": "",
// If true, the field auto-populates with the system date
"systemDate": false,
// Array of validation rule objects (e.g., required, pattern checks)
"validations": [],
// Error message (localised) to display if validation fails
"errorMessage": "",
// If true, field is included in the form submission payload
"includeInForm": true,
// If true, field allows multiple selections (dropdowns, checkboxes)
"isMultiSelect": false,
// If true, field is shown in the summary or review screen
"includeInSummary": true
},
],
// (Optional) Localisation key for the action button label on this page
"actionLabel": "",
// Localisation key for the page description, used for help or guidance text
"description": "APPONE_REGISTRATION_SEARCHBENEFICIARY_SCREEN_DESCRIPTION"
}
],
// Identifier for the project or campaign this configuration is associated with
"project": "CMP-2025-06-26-003927",
// Boolean flag indicating if a summary section is present or required for this flow
"summary": true,
// Integer representing the version of this configuration (supports version control)
"version": 2,
// Boolean flag; if true, this configuration is disabled and not available for selection/use
"disabled": false,
// Boolean flag; if true, this configuration is currently active or selected for editing/display
"isSelected": true
}
```

2\. FieldTypeMappingConfig

2\. FieldPropertiesPanelConfig<br>

4\. AppScreenLocalisationConfig

Suppose To introduce a new field type _say:”text” field type_ in the app configuration, you have follow these steps to make it functional for app config:

Create a Field Type mapping config for text. Add combination of type and format to be identified for app and field type to be identified for web and attributeToRename to identified for web to pass field properties when adding config.

To be identified for web to show all field properties related to text field. _For eg. You want to show tooltip properties for text in content Tab, then you add tooltip and their type say toggle, then you add conditional field which show when you turn on the toggle. And you add your field in visibilityEnabledFor, this is responsible to show properties to show for field_

3.Adding all field-properties in localisable: This is identified by web to check which all field console has to be make localisable. If you add it then system will generate unique localisation code and gets save in config. If not then it will directly save the text as it is.

_Say you want to make label, tooltip to be localisable so you need to add tooltip in localisabe properties for text field._

4\. Now you’re good and app config is configure for the new type i.e -> text
