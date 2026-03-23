---
title: The Template Screen is a me...
---

```
The Template Screen is a metadata-driven, dynamic UI architecture for managing
project- or campaign-based workflows. Its purpose is to decouple UI structure
from UI behavior, placing all layout, ordering, visibility, and localisation
logic into a centrally managed MDMS (Master Data Management System).

Key benefits include:
- Consistent, reusable component definitions
- Complete multi-language support with live preview
- Version-controlled, maintainable configurations
- Easier campaign rollouts without code redeployment
- Visual drag-and-drop editing through the Admin Console

At its core, the system uses:
- NewLayoutRenderer as the dynamic template renderer (renders components inside
  a mobile bezel preview)
- ComponentRegistryService as a component resolver (maps format to React components,
  defined in Module.js)
- NewDrawerFieldComposer as the right-side property editor panel with Content and
  Validation tabs
- MDMS configurations as a single source of truth for all field configs, field type
  mappings, and property panel definitions
```
