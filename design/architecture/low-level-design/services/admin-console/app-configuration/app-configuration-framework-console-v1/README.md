# App Configuration Framework - Console v1

<figure><img src="../../../../../../../.gitbook/assets/component-flow(app config).png" alt=""><figcaption></figcaption></figure>

### 1. System Overview

The **App Configuration** module is a dynamic screen builder designed to configure **mobile application screens** without requiring code changes. It allows administrators to define, modify, and preview application screens using configuration stored in MDMS (Master Data Management System).

The system supports both **form-based screens** and **template-based screens**, enabling flexible UI composition. Changes made through the App Configuration UI are reflected in real time via a preview, and once saved, they are persisted back to MDMS and consumed by mobile applications.

#### Key Capabilities

* Dynamic screen creation using configuration (no hardcoded UI)
* Real-time preview of configured screens
* Deep MDMS integration (v1 and v2)
* Multi-language support through Localisation APIs
* Property-based field customisation via a drawer panel
* Extensible field types and UI components

This system serves as a low-code configuration layer, bridging the gap between business requirements and mobile UI rendering.

### 2. Technology Stack

The App Configuration system is built using the following technologies:

* **React** — UI rendering and component architecture
* **Redux Toolkit** — Centralised state management and predictable updates
* **MDMS v1 / v2** — Persistent storage for configuration schemas and master data
* **Localisation API** — Language translation and message management

Each layer is intentionally decoupled to ensure scalability, maintainability, and easy extension.

### 3. High-Level Architecture

At a high level, the system consists of three major layers:

1. **Configuration Layer (MDMS)**\
   Stores page schemas, field types, and drawer panel definitions.
2. **State Management Layer (Redux)**\
   Manages editable configuration, selected field state, localisation data, and caching.
3. **UI Layer (React Components)**\
   Renders configuration UI, preview screens, and property editors.

The architecture ensures that **MDMS remains the source of truth**, while Redux acts as an intermediate working state for editing and previewing.

***

### 4. Component Hierarchy

The App Configuration UI follows a clear and layered component hierarchy. Each component has a single responsibility and communicates through Redux.

```
AppConfigurationStore (Redux Provider)
└── FullConfigWrapper (Main Container)
    ├── AppConfiguration (Core UI Controller)
    │   ├── NewLayoutRenderer (Template Renderer)
    │   ├── AppPreview (Form Renderer)
    │   └── NewAppFieldScreenWrapper (Field List)
    ├── SidePanelApp (Property Drawer Container)
    │   └── NewDrawerFieldComposer (Field Property Editor)
    └── AddFieldPopUp (Add Field Modal)
```

#### Component Responsibilities

* **AppConfigurationStore**
  * Wraps the entire application with Redux Provider
  * Exposes global store access
* **FullConfigWrapper**
  * Entry point for configuration flow
  * Handles initialisation, API calls, and save actions
  * Coordinates data flow between MDMS, Redux, and UI
* **AppConfiguration**
  * Decides whether to render the Template view or the Form view
  * Acts as the UI orchestration layer
* **NewLayoutRenderer**
  * Renders template-based screens
  * Handles nested and recursive field structures
* **AppPreview**
  * Renders form-based screens
  * Used primarily for object/form configurations
* **SidePanelApp**
  * Hosts the right-side drawer
  * Controls the visibility of the property editor
* **NewDrawerFieldComposer**
  * Renders editable properties for the selected field
  * Applies debounced updates to Redux
* **NewAppFieldScreenWrapper**
  * Displays a list of fields/cards in the current screen
  * Handles field selection and ordering
*   **AddFieldPopUp**

    * Modal for adding new fields
    * Uses Field Type Master to generate default metadata



### 5. Redux State Architecture

Redux is the backbone of the App Configuration system. The state is structured to support **fast updates**, **easy rollback**, and **efficient field access**.

<figure><img src="../../../../../../../.gitbook/assets/redux-flow(app config).png" alt=""><figcaption></figcaption></figure>

#### Core State Concepts

* **remoteData**
  * Original MDMS response
  * Used as a base reference during save operations
* **currentData**
  * Editable working copy of the configuration
  * Drives UI rendering and preview
* **selectedField**
  * Currently selected field object
  * Used to populate the drawer panel
* **selectedFieldPath**
  * Optimised path reference for updates
  * Enables O(1) access during field updates
*   **localization**

    * Holds all fetched and modified translations
    * Synced during save



### 6. Configuration Types: Template vs Form

The system supports two configuration types:

#### Template Configuration

* Used for complex, nested, or layout-heavy screens
* Fields may be deeply nested
* Updates require **recursive traversal**
* Rendered via `NewLayoutRenderer`

#### Form (Object) Configuration

* Used for flat, form-like screens
* Fields stored in arrays
* Direct index-based updates
* Rendered via `AppPreview`

This distinction affects:

* Field update logic
* Hide/show operations
* Footer handling
* Save payload preparation

***

### 7. Core Design Principles

The App Configuration system follows these guiding principles:

* **Configuration over Code**
* **Single Source of Truth (MDMS)**
* **Predictable State Updates**
* **Separation of Concerns**
* **Extensibility for new field types and properties**

These principles ensure that the system remains scalable as new screens, field types, and features are added.

***

### 8. Data Sources and External APIs

The App Configuration system depends on multiple backend services to fetch configuration, metadata, and localisation data. Each API serves a specific purpose and is invoked at well-defined stages of the application lifecycle.

These APIs are **read-heavy during initialisation** and **write-heavy during save operations**.

<figure><img src="../../../../../../../.gitbook/assets/data-flow(app config).png" alt=""><figcaption></figcaption></figure>

***

#### 8.1 Page Configuration (MDMS v2)

The page configuration defines the **structure of a screen**, including its layout, fields, headers, and footers. This is the primary configuration that drives both preview and editing.

**API Details**

**Endpoint**

```
GET /mdms-v2/v2/_search
```

**Request Body**

```json
{
  "schemaCode": "HCM-ADMIN-CONSOLE.NewFormConfig",
  "filters": {
    "flow": "",
    "project": "",
    "page": ""
  }
}
```

**Response Structure (Simplified)**

* `type` – Determines rendering strategy (`template` or `object`)
* `heading` – Localisation key for screen heading
* `body[]` – Main content (cards, sections, fields)
* `footer[]` – Footer actions (buttons, links)

This response is treated as the **source configuration** and is stored in Redux for further processing.

***

#### 8.2 Field Type Master (MDMS v1)

Field Type Master defines **how a field should be rendered**, validated, and initialised. It acts as a registry of all supported field types in the system.

**API Details**

**Endpoint**

```
GET /egov-mdms-service/v1/_search
```

**Request Body**

```json
{
  "moduleName": "HCM-ADMIN-CONSOLE",
  "masterDetails": [
    { "name": "NewFieldType" }
  ]
}
```

**Response**

```json
fieldTypeMappingConfig[]
```

Each entry maps a `(type + format)` combination to:

* A UI component
* Default metadata
* Default properties
* Validation rules

This data is fetched **once per session** and cached in Redux.

***

#### 8.3 Drawer Panel Configuration

The drawer panel defines **which properties are editable** for a selected field and **how those properties should be rendered**.

* **Schema**: `HCM-ADMIN-CONSOLE.NewDrawerPanelConfig`
* **Purpose**: Drive the right-side property editor UI

The configuration determines:

* Which properties appear under which tab (Content / Validation)
* Which field types can see a property
* Conditional visibility logic (toggle-based, dependent fields)

This makes the property editor **fully configuration-driven**.

***

#### 8.4 Localisation APIs

Localization is deeply integrated into the App Configuration system. Labels, headings, descriptions, and button texts are all stored as localisation keys.

**Fetch Translations**

**Endpoint**

```
GET /localisation/messages/v1/_search
```

**Params**

```
tenantId
module = "hcm-{flow}-{campaignNumber}"
locale
```

**Response**

```json
{
  "messages": [
    {
      "code": "LOCALIZATION_CODE",
      "message": "Translated Text",
      "module": "module-name"
    }
  ]
}
```

***

**Upsert Translations**

**Endpoint**

```
POST /localisation/messages/v1/_upsert
```

**Request Body**

```json
{
  "tenantId": "",
  "messages": [
    {
      "code": "",
      "message": "",
      "locale": "",
      "module": ""
    }
  ]
}
```

This API is invoked **before saving the MDMS configuration**, ensuring that all localisation entries are available when the mobile app consumes the config.

***

### 9. Initialisation Flow

The initialisation flow is responsible for preparing the App Configuration UI with all required data. This flow is triggered when the configuration screen loads.

#### Entry Point

**File**

```
FullConfigWrapper.js (Lines 88–120)
```

***

#### 9.1 Step-by-Step Initialisation Sequence

**Step 1: Fetch Page Configuration**

* Triggered on component mount
* Calls MDMS v2 `_search`
* Response is split into two parts:
  * `responseData` → immutable reference for updates
  * `currentData` → editable working copy

Redux State Updated:

* `remoteData`
* `currentData`
* `pageType` (`template` or `object`)

***

**Step 2: Fetch Field Type Master (Async)**

* Initiated in parallel
* Populates the field type dropdown
* Required for:
  * Add Field flow
  * Component rendering
  * Metadata initialization

Redux State:

* `fieldTypeMaster.byName`
* `fieldTypeMaster.status`

***

**Step 3: Fetch Localisation Data (Async)**

* Initiated in parallel with the Field Type Master
* Stores all translations for the current flow and campaign
* Enables:
  * Label rendering
  * Live updates during editing

Redux State:

* `localization.data`
* `localization.status`

***

#### 9.2 Initialisation Timeline

```
Component Mount
      |
      ├── MDMS Page Config Fetch
      |
      ├── Field Type Master Fetch (Parallel)
      |
      └── Localisation Fetch (Parallel)
```

The UI becomes interactive only after **page configuration is available**, while field master and localisation load progressively.

### 10. Field Selection Flow

Field selection is the foundation of the App Configuration editor.\
Whenever a user clicks on a field in the preview or layout, the system identifies **which field was selected**, **where it exists in the config**, and **how the property panel should react**.

<figure><img src="../../../../../../../.gitbook/assets/field-selection-sequence(app config).png" alt=""><figcaption></figcaption></figure>

#### Entry Point

**File**

```
redux/remoteConfigSlice.js (Lines 50–96)
```

***

#### 10.1 What Happens When a Field Is Clicked?

When a user clicks a field:

1. The field object is captured
2. Its exact position in the configuration is calculated
3. The property drawer is opened

```js
onFieldClick(field, screen, card, cardIndex, fieldIndex) {
  dispatch(selectField({
    field,
    cardIndex,
    fieldIndex,
    isFooterField
  }));
}
```

***

#### 10.2 Redux State Updated

The following state is updated in one action:

* `selectedField`\
  → Direct reference to the selected field object
*   `selectedFieldPath`\
    → Path metadata used for fast updates

    ```js
    {
      cardIndex,
      fieldIndex,
      isFooterField
    }
    ```
* `isFieldSelected`\
  → Controls drawer panel visibility

This design allows **O(1) access** to the selected field during updates.

***

#### 10.3 Footer Field Handling

Footer fields behave differently from body fields.

| Case         | cardIndex |
| ------------ | --------- |
| Body Field   | `>= 0`    |
| Footer Field | `-1`      |

This special marker avoids conditional branching throughout the codebase.

***

### 11. Field Property Update Flow

Once a field is selected, any change made in the drawer panel must update:

* The configuration state
* The localization state (for text fields)

#### Entry Point

**File**

```
redux/remoteConfigSlice.js (Lines 110–229)
```

***

#### 11.1 Text Properties (Localization-Aware)

Text-based properties such as `label`, `description`, or `helpText` are **localization-driven**.

**Update Behavior**

* Input changes are **debounced by 800ms**
* Localization entries are updated first
* Field config is updated with the localization code

```js
onChange(value) {
  debounce(() => {
    dispatch(updateLocalizationEntry({ code, locale, message: value }));
    dispatch(updateSelectedField({ label: code }));
  }, 800);
}
```

This prevents excessive API calls while maintaining real-time preview.

***

#### 11.2 Non-Text Properties

Non-text properties (e.g. `mandatory`, `hidden`, `order`) update immediately.

```js
onChange(value) {
  dispatch(updateSelectedField({ mandatory: value }));
}
```

These updates directly mutate the working configuration state.

***

#### 11.3 Update Strategy by Screen Type

The update logic differs based on the screen rendering model.

**FORM (`object`) Screens**

* Fields are stored in flat arrays
* Updated using direct array index access
* Faster and simpler updates

**TEMPLATE Screens**

* Fields may be deeply nested
* Updated using recursive tree traversal

```js
updateFieldInTree(node, fieldName, updatedProps)
```

This recursive logic is implemented in:

```
remoteConfigSlice.js (Lines 175–209)
```

***

### 12. Add Field Flow

The Add Field flow allows users to introduce new fields dynamically into the screen configuration.

#### Entry Point

**Component**

```
AddFieldPopUp (inside FullConfigWrapper.js)
```

***

#### 12.1 Step-by-Step Flow

**Step 1: Open Add Field Modal**

```js
dispatch(handleShowAddFieldPopup({ currentCard, card }));
```

Redux State:

* `showAddFieldPopup = true`

***

**Step 2: User Fills Field Details**

* Field name
* Label (localized)
* Type and format

Localization entries are created **as the user types**.

```js
dispatch(updateLocalizationEntry({ code, locale, message }));
```

***

**Step 3: Create Field Configuration**

When the user clicks **Add**:

1. Metadata is fetched from Field Type Master
2. A new field object is constructed
3. Field is pushed into the current card

```js
const newFieldData = {
  type,
  format,
  label,
  jsonPath,
  metadata
};
```

Dispatch:

```js
dispatch(addField({ cardIndex, fieldData: newFieldData }));
```

***

#### 12.2 Auto-Generated Properties

Each newly added field automatically gets:

* `id`: `crypto.randomUUID()`
* `deleteFlag`: `true`
* `showLabel`: `false` (scanner / QR fields only)

This ensures consistency across all newly added fields.

***

### 13. Field Operations

#### 13.1 Hide / Show Field Logic

Field visibility is controlled differently for FORM and TEMPLATE screens.

**FORM**

* Direct lookup using `fieldName`

**TEMPLATE**

* Recursive tree search using:

```js
toggleByFieldName(fieldName)
```

This abstraction ensures consistent behavior regardless of nesting depth.

### 14. Save Flow Overview

The Save Flow is responsible for **persisting all user changes** made in the App Configuration UI.\
Saving is a **multi-step operation** that ensures:

* Configuration data is updated in MDMS
* Localization entries are synchronized
* The system remains consistent even if partial failures occur

The save operation is **explicit** and triggered only when the user clicks **Save / Update**.

***

### 15. Save Flow Entry Point

**File**

```
FullConfigWrapper.js
```

**Function**

```
handleUpdateMDMS()
```

This function orchestrates all persistence-related operations.

### 16. Step-by-Step Save Sequence

#### 16.1 Step 1: Upsert Localization Entries

Before updating MDMS, all localization changes must be saved.

**Why This Is Required**

* Page config references localization **codes**, not literal text
* The mobile app resolves labels at runtime
* Missing localization entries result in broken UI text

**Process**

1. Collect localization data from Redux
2. Remove empty or unchanged entries
3. Transform data into API format
4. Call localization upsert API

```js
transformLocalizationData(localization.data)
  .filter(entry => entry.message)
```

**API Call**

```
POST /localization/messages/v1/_upsert
```

***

#### 16.2 Step 2: Prepare MDMS Payload

Once localization is successfully upserted, the configuration is prepared for MDMS update.

**Payload Strategy**

* Preserve original MDMS metadata from `responseData`
* Replace only the `data` section with `currentData`

```js
{
  ...responseData,
  data: currentData
}
```

This ensures:

* Schema version remains intact
* Audit fields are preserved
* Partial overwrites are avoided

***

#### 17.3 Step 3: Update MDMS Configuration

**API Call**

```
POST /mdms-v2/v2/_update/HCM-ADMIN-CONSOLE.AppConfigCache
```

**Final Payload Structure**

```json
{
  "Mdms": {
    "schemaCode": "HCM-ADMIN-CONSOLE.NewFormConfig",
    "data": { /* updated currentData */ }
  }
}
```

***

#### 17.4 Step 4: Handle API Response

* **Success**
  * Show success toast
  * Navigate back to listing screen
* **Failure**
  * Show error toast
  * Retain unsaved changes in UI

This ensures **no accidental data loss**.

***

### 18. Transaction Safety & Consistency

The save flow intentionally follows this order:

1. Localization first
2. MDMS update second

#### Why This Order Matters

* MDMS config references localization keys
* If localization fails after MDMS update, UI breaks
* If MDMS fails, localization entries are harmless extras

This design favors **eventual consistency** without breaking runtime behavior.

***

### 19. Error Handling Strategy

#### API-Level Errors

* All API failures are caught and surfaced via toast messages
* Error messages displayed are backend-provided where available

#### UI-Level Errors

* Save button remains enabled after failure
* User can retry without losing state
* No partial reset of Redux state occurs

***

### 20. Payload Validation Before Save

Before sending data to MDMS:

* Empty cards are ignored
* Deleted fields (`deleteFlag = true`) are filtered
* Invalid configurations are prevented via UI validations

This reduces backend validation failures.

***

### 21. Versioning Behavior

* Each successful save increments the module or page version
* Versioning is controlled by MDMS
* App Configuration UI always edits the **latest version**

This prevents accidental overwrites.



### 22. File & Module Reference

This section acts as a **quick lookup** for developers to understand where each responsibility lives in the codebase.

***

#### 22.1 Core Screens

| File / Module                       | Responsibility                                               |
| ----------------------------------- | ------------------------------------------------------------ |
| `AppConfigurationParentRedesign.js` | Entry point, navigation between screens, fetches MDMS config |
| `ImpelWrapper.js`                   | Restructures config before render and before save            |
| `LocalizationWrapper.js`            | Localization handling and key resolution                     |
| `AppConfigurationWrapper.js`        | Orchestrates editor UI and data flow                         |



***

#### 22.2 Services & Helpers

| File                    | Responsibility                                       |
| ----------------------- | ---------------------------------------------------- |
| `service.js`            | Restructure, reverseRestructure, metadata extraction |
| `getMetadata.js`        | Resolves field metadata from masters                 |
| `reverseRestructure.js` | Converts UI state back to MDMS-compatible schema     |
| `utils.js`              | Shared helpers (deep clone, safe access, defaults)   |



***

#### 22.3 Rendering & Composition

| File                  | Responsibility                                    |
| --------------------- | ------------------------------------------------- |
| `ViewComposer.js`     | Dynamically renders fields based on type & format |
| `FieldComposer.js`    | Composes individual field rendering               |
| `TemplateComposer.js` | Renders TEMPLATE-based screens                    |
| `FooterComposer.js`   | Renders footer actions                            |

***

#### 22.4 Drawer & Property Panel

| File                         | Responsibility                    |
| ---------------------------- | --------------------------------- |
| `NewDrawerPanel.js`          | Right-side property drawer        |
| `NewDrawerFieldComposer.js`  | Renders property inputs           |
| `FieldPropertiesPanelConfig` | Defines editable properties       |
| `FieldTypeMappingConfig`     | Maps field types to UI components |

***

### Troubleshooting Guide

This section addresses the **most common issues** encountered during development and configuration.

***

#### Issue 1: Field Not Rendering

**Possible Causes**

* Field type not registered
* Missing FieldTypeMappingConfig entry
* Incorrect `type` or `format`

**Checklist**

* Verify entry in `HCM-ADMIN-CONSOLE.FieldTypeMappingConfig`
* Confirm component is registered in ComponentRegistry
* Check browser console for missing component logs

***

#### Issue 2: Field Renders but Not Editable

**Possible Causes**

* Drawer property not configured
* `visibilityEnabledFor` missing field type

**Fix**

* Update `FieldPropertiesPanelConfig`
* Ensure field type is included in visibility rules

***

#### Issue 3: Property Value Not Saving

**Possible Causes**

* Property not included in reverseRestructure
* Incorrect `bindTo` key

**Fix**

* Add mapping in `reverseRestructure`
* Confirm property exists in original MDMS schema

***

#### Issue 4: Localization Key Not Showing

**Possible Causes**

* Missing localization entry
* Incorrect key naming convention

**Fix**

* Validate localization key in i18n service
* Follow standardized naming pattern

***

#### Issue 5: Template Screen Breaking

**Possible Causes**

* Incorrect nesting
* Missing child array

**Fix**

* Ensure recursive structure is intact
* Validate with sample TEMPLATE config

***

### FAQs

***

#### Q1. Can this system support completely new screen types?

Yes.\
You can introduce new screen types by:

* Defining new screenType
* Implementing renderer
* Updating restructuring logic

However, FORM and TEMPLATE cover most use cases.

***

#### Q2. Why is restructuring required?

MDMS configs are not UI-friendly.\
Restructuring:

* Normalizes data
* Adds metadata
* Enables easy state updates

Reverse restructuring ensures backward compatibility.

***

#### Q3. Can we reuse field configs across modules?

Yes.\
Common patterns can be extracted into shared MDMS masters, but runtime reuse must be handled carefully to avoid mutation issues.

***

#### Q4. Is this system scalable?

Yes, because:

* Config-driven rendering
* No hardcoded screens
* Versioned MDMS storage
* Tenant isolation

***

### Best Practices

* Keep MDMS configs minimal
* Avoid deep nesting unless required
* Always version configs
* Test save + reload cycle
* Never bypass restructuring layer

***

### Final Summary

The App Configuration system is a **dynamic, metadata-driven UI framework** designed to eliminate hardcoded screens and enable rapid configuration at scale.

At its core, it:

* Reads structured configuration from MDMS
* Converts it into a UI-friendly format
* Allows controlled editing through a property-driven editor
* Persists changes safely back to MDMS

By separating:

* **Configuration**
* **Rendering**
* **Editing**
* **Persistence**

…the system achieves flexibility without sacrificing stability.

This documentation serves as a **complete reference** for:

* Onboarding new developers
* Extending functionality
* Debugging issues
* Maintaining long-term scalability

