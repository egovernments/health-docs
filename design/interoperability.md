---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/design/interoperability
---

# Interoperability

This document describes how DIGIT HCM  interoperates with other systems in a standardised and secure way:

**1. Https Protocols:**

* Utilises HTTP/HTTPS protocols, which are universally supported by web clients and servers.
* Adheres to RESTful principles, providing a consistent and standardised way for clients to interact with the platform.

**2. Data Format:**

* Offers JSON support for data exchange, ensuring compatibility with a wide range of programming languages and systems.
* Content Negotiation: Automatically handles content negotiation to serve responses in the JSON format requested by the client.

**3. API Documentation:**

* Provides comprehensive API documentation using Swagger/OpenAPI, making it easy for developers to understand and consume the APIs.

**4. Cross-Origin Resource Sharing:**

* Supports CORS, enabling secure cross-origin requests from web applications hosted on different domains.

**5. Authentication and Authorisation:**

* Implements OAuth2 and JWT for standardised and secure authentication and authorisation, allowing integration with various identity providers - this is currently under implementation.&#x20;

**6. Error Handling:**

* Provides standardised error responses with HTTP status codes and detailed messages, helping external systems handle errors reliably.
* Ensures uniform error handling across the platform, presenting predictable and understandable error responses to clients.

**7. API Versioning:**

* Supports API versioning to maintain backward compatibility, allowing external integrations to continue functioning while new features are added.

**8. Observability:**

* Uses Spring Boot Actuator to expose health checks and metrics endpoints, aiding external monitoring tools in observing platform health and performance.
* Compatible with popular monitoring tools like Prometheus and Grafana for comprehensive observability.
