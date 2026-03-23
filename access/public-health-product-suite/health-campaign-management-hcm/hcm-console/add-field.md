# Add Field

## Overview

The Add Field functionality allows administrators to extend and customise data capture screens by adding new fields as per campaign requirements. This enables flexible configuration of forms without code changes, allowing additional information to be captured from field users during campaign execution.

## Steps

### Step 1: Add a New Field

1. Navigate to the **Page Properties** panel for the selected screen.
2. Click **Add Field**.
3. Enter the required field details, such as:
   * Field Label
   * Field Type (e.g., text, number, dropdown, date)
   * Helper Text (optional guidance for field users)
4. Configure additional properties if required (e.g., mandatory, validation rules). Refer to the [field properties](add-field.md#field-properties) and [field types](add-field.md#field-types) table for details.

<figure><img src="../../../../.gitbook/assets/unknown (16).png" alt=""><figcaption></figcaption></figure>

### Step 2: Review the Field Configuration

1. Verify that the new field appears correctly on the screen.
2. Ensure the label and helper text are clear and aligned with campaign requirements.

<figure><img src="../../../../.gitbook/assets/image (460).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (461).png" alt=""><figcaption></figcaption></figure>

### Step 3: Save Changes

1. Review all configurations.
2. Click **Save Configuration** before exiting the module configuration screen.

Repeat the process for any additional fields or modules as required.

The newly added fields will now be available in the mobile application during campaign execution.

### Field Properties

<table><thead><tr><th width="148.45703125">Property</th><th width="379.3671875">Description</th><th>Applicable Fields</th></tr></thead><tbody><tr><td>Non Editable</td><td>Allows you to lock a field so users cannot modify its value. Useful for auto-filled or system-generated fields.</td><td>All field types</td></tr><tr><td>Label</td><td>Defines the display name of the field shown to users. This text can be updated according to the user.</td><td>All field types</td></tr><tr><td>Field Type</td><td>A dropdown that allows you to select the type of field. It contains all available field types and determines how the field will be displayed and what kind of input is allowed.</td><td>All field types</td></tr><tr><td>Required field</td><td>Marks a field as required. The form cannot be submitted if this field is left empty.</td><td>All field types</td></tr><tr><td>Default Value</td><td>Sets a pre-filled value that appears automatically when the form loads. </td><td>Text, Number, Date, Dropdown</td></tr><tr><td>Tool tip</td><td>Displays guidance or instructions to help users understand what to enter in the field.</td><td>All field types</td></tr><tr><td>Help Text</td><td>Displays guidance or instructions to help users understand what to enter in the field.</td><td>All field types</td></tr><tr><td>Dependent Field</td><td>Controls when a field is shown or hidden based on other field values.</td><td>All field types</td></tr><tr><td>Input Validation</td><td>Ensures the entered data follows specific rules (e.g., format, range, pattern).</td><td>Text, Number, Date, Phone, QR</td></tr><tr><td>Use Existing Data</td><td>Connects the field to a predefined list of values or master data for selection.</td><td>Dropdown, Checkbox, Radio, Search</td></tr></tbody></table>

### Field Types

<table><thead><tr><th width="176.609375">Field Type</th><th>Description</th></tr></thead><tbody><tr><td>Text</td><td>Used to capture free text input such as names, descriptions, or comments.</td></tr><tr><td>Number</td><td>Used to capture numeric values (integer or decimal).</td></tr><tr><td>Dropdown</td><td>Allows users to select one or more options from a list.</td></tr><tr><td>Checkbox</td><td>Allows users to select multiple options from a list.</td></tr><tr><td>Radio Button</td><td>Allows users to select only one option from a list.</td></tr><tr><td>Date Picker</td><td>Used to capture a date (e.g., Date of Birth, event date).</td></tr><tr><td>Numeric Counter</td><td>Allows users to increase or decrease a numeric value using + / – buttons.</td></tr><tr><td>Phone Number</td><td>Used to capture mobile or phone numbers with country code support.</td></tr><tr><td>QR Scanner</td><td>Allows scanning of QR codes (including GS1 QR codes).</td></tr><tr><td>Coordinates</td><td>Automatically captures latitude and longitude coordinates.</td></tr><tr><td>ID Populator</td><td>Displays auto-generated or system-calculated values (e.g., IDs, timestamps).</td></tr></tbody></table>
