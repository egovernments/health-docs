---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/access/public-health-product-suite/health-campaign-management-hcm/specifications/functional-specifications/boundary-hierarchy
---

# Boundary Hierarchy

## Overview

Boundary hierarchy defines how geographic administrative layers (like country → state → district → village) are represented and structured within the HCM system—essential for planning and managing campaign logistics, reporting, and stock distribution.

## Specifications

<table><thead><tr><th width="223">Name of the field</th><th width="195">Description</th><th width="132">Mandatory</th><th>Input</th><th width="136">Data type</th><th width="167">Minimum length</th><th width="162">Maximum length</th><th>Need data from program/state</th></tr></thead><tbody><tr><td>Serial number</td><td>The sequence number for the list.</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>Boundary hierarchy type</td><td>The meaningful name to define a group of boundaries defined to perform one function.</td><td>Mandatory</td><td>MDMS</td><td>String</td><td>2</td><td>256</td><td>Yes</td></tr><tr><td>Code</td><td>A code is used to identify a certain classification of the type of boundary hierarchy.</td><td>Mandatory</td><td>MDMS</td><td>String</td><td>2</td><td>64</td><td>Yes</td></tr><tr><td>Description</td><td></td><td>Mandatory</td><td>MDMS</td><td>String</td><td>2</td><td>256</td><td>Yes</td></tr></tbody></table>
