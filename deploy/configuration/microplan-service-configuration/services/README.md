# Services

Microplanning is implemented as a small set of backend services. They own plan configuration, census inputs, and resource estimation outputs. Use this section to understand each service’s APIs, Kafka topics, and deployment knobs.

### Services in scope

* [Plan Service](plan-service.md): plan configuration and microplan lifecycle.
* [Resource Generator Service](resource-generator-service.md): parse uploads, run formulas, and orchestrate creation flows.
* [Census Service](census-service.md): store, validate, and approve population datasets.
