# Architecture

DIGIT is India’s largest open-source platform for digital governance. The health services are built on top of DIGIT. It is built on OpenAPI (OAS 2.0) and provides API-based access to a variety of services, enabling governments to provide health campaign services with relevant new ones. It also facilitates integration with the existing system into the platform and runs seamlessly on any commercial/on-prem cloud infrastructure with scale and speed.

### Key Architecture Highlights <a href="#key-architecture-highlights" id="key-architecture-highlights"></a>

* Health DIGIT is a micro-services-based platform that is built to scale. Micro-services are small, autonomous, and developer-friendly services that work together.
* It facilitates decentralised control between teams so that its developers strive to produce useful tools that can then be used by others to solve the same problems.
* Micro-services have smart endpoints that process information and apply logic. They receive requests, process them, and generate a response accordingly.
* Parallelism in development: Micro-services architectures are mainly business-centric.
* A big software or system can be broken down into multiple small components or services. These components can be designed, developed, and deployed independently without compromising the integrity of the application.

<figure><img src="../.gitbook/assets/health-architecture-3.svg" alt=""><figcaption></figcaption></figure>

### Multi-layer Architecture

DIGIT Health follows a multi-layer or n-tiered distributed architecture pattern. As seen in the illustration above, there are different horizontal layers with some set of components such as Services, Registries and DIGIT Core Services. Every layer consists of a set of micro-services. Each layer of the layered architecture pattern has a specific role and responsibility within the application. The following are the advantages:

* Layered architecture increases flexibility, maintainability, and scalability.
* Multiple applications can reuse the components.
* Parallelism.
* Different components of the application can be independently deployed, maintained, and updated, on different time schedules.
* Layered architecture also makes it possible to configure different levels of security to different components.
* Layered architecture also helps users test the components independent of each other.

[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)_​_](http://creativecommons.org/licenses/by/4.0/)_All content on this page by_ [_eGov Foundation_](https://egov.org.in/) _is licensed under a_ [_Creative Commons Attribution 4.0 International License_](http://creativecommons.org/licenses/by/4.0/)_._
