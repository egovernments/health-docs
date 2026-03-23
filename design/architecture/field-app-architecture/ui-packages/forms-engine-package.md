# Forms Engine Package

## Overview

This document describes the forms\_engine Flutter package. It dynamically renders multi-page forms based on a JSON configuration and is built on top of the digit\_ui\_components package.

***

## Installation

```
dependencies:
  forms_engine:
    git:
      url: https://github.com/egovernments/health-campaign-field-worker-app.git
      path: packages/forms_engine
      ref: delivery_flow
```

Run:

```
flutter pub get
```

***

## Configuration Example

Below is a realistic JSON config that forms\_engine consumes:

```
{
  "name": "DELIVERYFLOW",
  "order": 2,
  "pages": [
      {
      "page": "DeliveryDetails",
      "type": "object",
      "label": "APPONE_REGISTRATION_DELIVERYDETAILS_SCREEN_HEADING",
      "order": 1,
      "navigateTo": { "name": "household-acknowledgement", "type": "template" },
      "properties": [
        {
          "type": "integer",
          "format": "date",
          "fieldName": "dateOfRegistration",
          "label": "APPONE_REGISTRATION_DELIVERYDETAILS_label_dateOfDelivery",
          "systemDate": true,
          "order": 1,
          "includeInForm": true,
          "includeInSummary": true
        },
        {
          "type": "dynamic",
          "format": "custom",
          "fieldName": "resourceCard",
          "label": "APPONE_REGISTRATION_DELIVERYDETAILS_label_resource",
          "enums": [ { "code": "SP1", "name": "SP1" }, { "code": "SP2", "name": "SP2" }, { "code": "AQ1", "name": "AQ1" }, { "code": "AQ2", "name": "AQ2" } ],
          "validations": [{ "type": "required", "value": true, "message": "..._mandatory_message" }],
          "order": 2,
          "includeInForm": true,
          "includeInSummary": true
        },
        {
          "type": "string",
          "format": "dropdown",
          "fieldName": "deliveryComment",
          "schemaCode": "HCM.DELIVERY_COMMENT_OPTIONS_POPULATOR",
          "label": "APPONE_REGISTRATION_BENEFICIARYDETAILS_label_deliveryComments",
          "order": 3,
          "includeInForm": true,
          "includeInSummary": true
        },
        {
          "type": "string",
          "format": "scanner",
          "fieldName": "scanner",
          "label": "APPONE_REGISTRATION_DELIVERYDETAILS_label_scanner",
          "order": 4,
          "includeInForm": true,
          "includeInSummary": true
        }
      ],
      "actionLabel": "APPONE_REGISTRATION_DELIVERYDETAILS_ACTION_BUTTON_LABEL_1",
      "description": "APPONE_REGISTRATION_DELIVERYDETAILS_SCREEN_DESCRIPTION"
    }  ],
  "project": "CMP-2025-07-09-009012",
  "version": 2,
  "disabled": false,
  "isSelected": true
}
```

***

## Schema & Key Concepts

* Root fields:
  * name / order: identifies the flow.
  * pages (array): each element drives one screen.
  * project, version, disabled, isSelected: meta information.
* Page object:
  * page (string): unique key.
  * type: object
  * label, order, description.
  * navigateTo: next flow or template.
  * properties (array): each defines one UI widget / Form component.
* Property fields:
  * type: “object”, “integer”, “string”,” dynamic”, etc.
  * format: how it renders ( date, dropdown, radio, checkbox,scanner, etc.).
  * fieldName: internal form key.
  * label, order, value.
  * enums: for radio button type form component
  * validations: array of rules (required, custom messages).
  * includeInForm / includeInSummary: Hides fields in form or summary pages..
  * systemDate: if true, auto-populates current date.
  * readOnly, hidden, etc.

***

## Usage

Load the form:

```
context.read<FormsBloc>().add(FormsEvent.load(schemas: schemas));
```

Example:&#x20;

```
final arrayJunctionDataSchemaData = arrayJunctionBoxSchemaEntry?['data'];
final arrayJunctionSchemas = jsonEncode(arrayJunctionDataSchemaData);
context.read<FormsBloc>().add(FormsEvent.load(schemas: [arrayJunctionSchemas]));
```

Clear the form:

```
context.read<FormsBloc>().add(
  const FormsEvent.clearForm(schemaKey: 'AssetForm'));
```

Load submitted form Data:

```
BlocListener<FormsBloc, FormsState>(
listener: (context, formState) {
  if (formState is FormsSubmittedState) {
    DigitLoaders.overlayLoader(context: context);

    final formData = formState.formData;
    if (formData.isEmpty) return;
```

* Builds an internal FormGroup for all properties across pages.
* Renders pages in ascending order.
* Shows the action button with actionLabel (fallback to "Submit").
* After the final page, if a summary.enabled, renders summary before calling onSubmit.

***

## Extension Points

1. Custom Property Types: register new format handlers in FieldBuilder.
2. Conditional Flows: wrap and mutate config before passing to the widget.
3. Theming & Styling: leverages digit\_ui\_components theme—override via ThemeData.
4. Validation: uses reactive\_forms under the hood—add global validators or messages.

***

For more details, explore the code in the[ packages/forms\_engine](https://github.com/egovernments/health-campaign-field-worker-app/tree/delivery_flow/packages/forms_engine) directory.
