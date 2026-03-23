---
description: >-
  A JSON-driven dynamic UI rendering framework that builds complete screens and
  workflows from configuration.
---

# DIGIT Flow Builder

## Overview

DIGIT Flow Builder is a powerful JSON-driven dynamic UI rendering framework that enables the creation of configurable forms and templates without code changes. It provides a declarative approach to building complex user interfaces with integrated state management, data binding, and action handling capabilities.

Link to the Pub Package:&#x20;

{% embed url="https://pub.dev/packages/digit_flow_builder" %}

## Features

* Render complete screens (forms or templates) from JSON flow configuration registered in FlowRegistry
* Two screen types — FORM (powered by digit\_forms\_engine) and TEMPLATE (custom layout with 26+ widgets)
* 12 built-in action types — create, update, search, navigate, scan QR, show toast, clear state, and more
* Conditional action execution — run actions only when formula conditions are met
* Template interpolation — dynamically resolve values in labels, properties, and actions using \{{key\}} syntax
* Bidirectional pagination with scroll listeners
* Transform form data to entities and reverse-transform entities back to form data for editing
* Accumulated search filters across multiple search interactions
* Custom widget registration — plug in your own widgets alongside built-in ones
* Screen capture protection on sensitive screens



**Screen Types**

<table><thead><tr><th width="153.87890625">Type</th><th width="399.484375">Description</th><th>Powered By</th></tr></thead><tbody><tr><td>FORM</td><td>Multi-page configurable forms with validation, visibility conditions, and summary</td><td>digit_forms_engine</td></tr><tr><td>TEMPLATE</td><td>Custom layouts with header, body, footer using 26+ built-in widgets</td><td>WidgetRegistry</td></tr></tbody></table>

**Supported Actions**

<table><thead><tr><th width="379.328125">Action</th><th width="362.8359375">Description</th></tr></thead><tbody><tr><td>CREATE_EVENT</td><td>Create new entities from form data</td></tr><tr><td>UPDATE_EVENT</td><td>Update existing entities with change detection</td></tr><tr><td>SEARCH_EVENT</td><td>Search entities with filters, pagination, and proximity</td></tr><tr><td>REFRESH_SEARCH</td><td>Re-execute previous search with new pagination</td></tr><tr><td>FETCH_TRANSFORMER_CONFIG</td><td>Map form data to entity models using transformer config</td></tr><tr><td>REVERSE_TRANSFORM</td><td>Map entities back to form data for pre-filling</td></tr><tr><td>NAVIGATION</td><td>Navigate to another page or flow (push, replace, pop)</td></tr><tr><td>BACK_NAVIGATION</td><td>Handle back button with custom logic</td></tr><tr><td>OPEN_SCANNER</td><td>Open QR/barcode scanner</td></tr><tr><td>CLEAR_STATE</td><td>Clear filters, widget data, or full state</td></tr><tr><td>CLOSE_POPUP</td><td>Close an action popup</td></tr></tbody></table>

**Built-in Widgets (for TEMPLATE screens)**

| Category   | Widgets                                                       |
| ---------- | ------------------------------------------------------------- |
| Layout     | Column, Row, Card, Expandable, Panel Card                     |
| Input      | Text Input, Dropdown, Radio, Switch, Search Bar, Filter       |
| Display    | Text, Tag, Icon, Info Card, Menu Card, Label Pair List, Table |
| List       | ListView (with scroll pagination)                             |
| Selection  | Selection Card                                                |
| Scanner    | QR Scanner, QR View                                           |
| Navigation | Button, Back Link, Action Popup                               |
| Search     | Proximity Search                                              |

#### **How It Works**

1. The host application registers flow configs into FlowRegistry
2. ScreenBuilder reads the config from the registry and checks the screen type
3. FORM screens are handed off to digit\_forms\_engine for rendering
4. TEMPLATE screens are rendered by LayoutRendererPage using WidgetRegistry
5. User interactions trigger actions defined in the config
6. ActionHandler executes the right action executor based on actionType
7. State is managed per screen instance via FlowCrudStateRegistry

#### **Sequence Diagram**

<figure><img src="../../../../.gitbook/assets/image (484).png" alt=""><figcaption></figcaption></figure>
