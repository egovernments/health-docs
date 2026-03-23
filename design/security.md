# Security

## Data Protection & Privacy Definitions

### 1. Data

Data is any information shared by citizens or received from existing databases to enable government service delivery and government operations. It could be name, address, mobile number, age, etc.

Under the Indian law, the current Digital Personal Data Act of 2023 defines data as:

Sec 2(h) - ‘Data’ means a representation of information, facts, concepts, opinions, or instructions in a manner suitable for communication, interpretation, or processing by human beings or by automated means.

It is similar to what is defined as ‘data’ in the Information Technology Act of 2000:&#x20;

[Data means](https://www.indiacode.nic.in/bitstream/123456789/13116/1/it_act_2000_updated.pdf) a representation of information, knowledge, facts, concepts or instructions which are being prepared or have been prepared in a formalized manner and are intended to be processed, is being processed or has been processed in a computer system or computer network, and may be in any form (including computer printouts magnetic or optical storage media, punched cards, punched tapes) or stored internally in the memory of the computer.

#### 1a) Personal Data or Personally Identifiable Information (PII)

For this document, PII and personal data are to mean the same.

Personal data is defined under the Digital Personal Data Act,2023 as:

Sec 2 (t) - “Personal data” means any data about an individual who is identifiable by or about such data;

To add, a breach of personal data is also defined in Section 2 (u) as -:

“Personal data breach” means any unauthorised processing of personal data or accidental disclosure, acquisition, sharing, use, alteration, destruction or loss of access to personal data, that compromises the confidentiality, integrity or availability of personal data;

[Another definition of personal data](https://www.meity.gov.in/writereaddata/files/GSR313E_10511\(1\)_0.pdf) is “any data that allows one to be recognised either directly or indirectly. It is defined as any information that relates to a natural person, which, either directly or indirectly, in combination with other information available or likely to be available with a body corporate, is capable of identifying such a person.”

Both the above definitions of personal data are to be read together until the government fixates on maintaining one.

**1b) Sensitive Personal Data (SPD)**

Sensitive Personal data of a person means “...such personal information which consists of information relating to:

* password;
* financial information such as Bank account, credit card, debit card or any other payment instrument details;
* physical, physiological and mental health conditions;
* sexual orientation;
* medical records and history;
* biometric information;
* any detail relating to the above clauses as provided to the body corporate for providing service;
* and any of the information received under the above clauses by the body corporate for processing, stored or processed under lawful contract or otherwise

Provided that, any information that is freely available or accessible in the public domain or furnished under the Right to Information Act, 2005 or any other law for the time being in force shall not be regarded as sensitive personal data or information\[...].”

### 2. Product Implementation Cycle

#### 2a) Product

For this document, ‘product’ refers to any software system that can be used by a government entity, or by a contractor performing any tasks on behalf of that government entity. The term ‘product’ refers to the software (code) itself, and NOT to any implementation of that code. Therefore, a product does not collect, store, process, use, or share data.

For example,[ DIGIT-HCM ](https://github.com/egovernments/health-campaign-services)is a product.

**2b) Product Implementation**

For this document, “product Implementation” refers to each instance of a product/software system that has been implemented.

* During the implementation of a product, the implementing agency may collect, store, process, use, and share such data as is necessary for implementing the product. This will normally be specified in the contract or agreement between the implementing agency and the administrative authority responsible for that implementation.

After the implementation of a product is complete, the implementing agency should cease to have access to data from the product implementation, except to such extent as may be agreed between the implementing agency and the administrative authority responsible for that implementation.

* In cases where the implementing agency performs the role of a support agency concerning any product implementation, the implementing agency may have access to data as specified for that role. The activity of product implementation involves roles having access to datasets flowing through the product.

For example, Salama (in Mozambique) is the product implementation – It is an implementation of the DIGIT-HCM product.

#### 2c) Programme

Any ongoing or to-be-executed delivery of government service or defined government operation is a programme.

* During the operation of a programme, the programme owner (and its staff and contractors) will collect, store, process, use, and share such data as is necessary for performing their tasks, and/or which they are required to do under prevailing law.

For example, a programme is one in which ULBs in Punjab use the MSeva product to collect revenues, deliver ULB services, and redress grievances.

**2d) Summary & Comparison of Product, Product Implementation, & Programme**

<table><thead><tr><th></th><th width="181">Product</th><th>Product Implementation</th><th>Programme</th></tr></thead><tbody><tr><td>Definition</td><td>Refers to a software system that can be used by government entities or contractors. The term ‘product’ refers to the software (code) itself, and NOT to any implementation of that code.</td><td>Refers to each instance of a product/software system that has been implemented.</td><td>Any delivery of govt services or other govt operations or reforms can be a programme. In the context of this document, a programme deploys and/or leverages a product implementation.</td></tr><tr><td>Does it process data?</td><td>No</td><td>Yes</td><td>Yes</td></tr><tr><td>Example</td><td>DIGIT</td><td>Salama</td><td>Provinces in Mozambique respectively.</td></tr></tbody></table>

#### 2e) Product Implementation Stages

We describe a product implementation as progressing across 7 stages:

<table><thead><tr><th width="114">Stage </th><th>Stage Name</th><th width="191">What happens at this stage</th><th>Who handles at this stage</th></tr></thead><tbody><tr><td>Stage 0</td><td>Programme set-up</td><td>Resources, budgets, procurement, and infrastructure are identified and an implementation partner is onboarded.</td><td>None</td></tr><tr><td>Stage 1</td><td>Programme kick-off</td><td>Implementation starts and data is collected from a few identified jurisdictions for testing.</td><td><p>Yes.</p><p>IA, Programme</p></td></tr><tr><td>Stage 2</td><td>Solution design</td><td>State-specific configurations are made with processes and workflows being designed. Policy decisions are made at this stage.</td><td><p>Yes.</p><p>IA, Programme</p></td></tr><tr><td>Stage 3</td><td>Customisations and configurations</td><td>Adoption and performance of the program are measured. UAT (Usee acceptance testing) is conducted here.</td><td><p>Yes.</p><p>IA, Programme</p></td></tr><tr><td>Stage 4</td><td>UAT and Go-live</td><td>The UAT testing is completed, feedback is received and final product deployment is carried out at all identified jurisdictions.</td><td><p>Yes.</p><p>IA, Programme</p></td></tr><tr><td>Stage 5</td><td>Statewide rollout</td><td>Phase-wise implementation of the product begins. Troubleshooting, support with errors, and critical bugs are fixed.</td><td><p>Yes.</p><p>IA, Programme, SA</p></td></tr><tr><td>Stage 6</td><td>Sustenance and ongoing improvement</td><td>Sustenance and ongoing Improvement - product adoption teams are set, adoption is tracked and awareness and reviews on adoption are conducted</td><td><p>Yes.</p><p>IA, Programmme, SA</p></td></tr></tbody></table>

## 3. Roles

#### 3a) Product Owner (PO)

For this document, a product owner is an entity that owns, governs, or controls the product's codebase. They are responsible for its architecture design, roadmap, and versions.

As a product is a code that has NOT been implemented, a product owner has no access to data.

When a product is implemented, becoming a product implementation, the product owner may have access to such data as is being collected, stored, processed, used, or shared by that product implementation as may be agreed upon by the product owner and the administrative authority responsible for that implementation.

In cases where a product owner performs the roles of an implementing agency or support agency concerning any product implementation, the product owner may have access to data as specified for those roles (see below).

For example, the eGovernments Foundation is a product owner.

**3b) Implementing Agency (IA)**

An agency that deploys and configures a product for the administrative authority or program owner (see below) is an implementing agency (IA). An IA may:

* set up the hardware necessary for the programme;
* customise, extend, configure, and install/set up the software (product) as per the needs of the programme owner;
* train staff or contractors of the program owner on how to use the product;
* Perform other such functions to ensure program readiness as may be agreed upon between the implementing agency and the program owner and/or administrative authority responsible for such product implementation.

During the implementation of a product, the implementing agency may collect, store, process, use, and share such data as is necessary for implementing the product. This will normally be specified in the contract or agreement between the implementing agency and the administrative authority responsible for that implementation.

After the implementation of a product is complete, the implementing agency should cease to have access to data from the product implementation, except to such extent as may be agreed between the implementing agency and the administrative authority responsible for that implementation.

In cases where the implementing agency performs the role of a support agency concerning any product implementation, the implementing agency may have access to data as specified for that role (see below).

For example, if a given state government signs a contract with “Company L” to implement the DIGIT-HCM product in that state, Company L is an IA.

#### 3c) Programme Owner (Prog)

For this document, a “programme owner” is the entity responsible for delivering specific public goods, services, or social welfare. A program owner is usually a government entity (though they may contract private entities to perform some or all of these tasks on their behalf).

In the context of a product implementation, the program owner is the primary client of the implementing agency, as they will use the product implementation to perform their tasks.

A programme owner (and its staff and contractors) will collect, store, process, use, and share such data as is necessary for performing their tasks, and/or which they are required to do under prevailing law.

A programme owner has primary responsibility for ensuring that all relevant legal provisions and good practices concerning data security, data protection, and privacy are followed in their programs.

A programme owner may perform the roles of implementing agency and/or support agency, or may contract those roles out to third-party implementing agencies and support agencie,s respectively. If they are performing these roles, they will have access to such data as is specified for these roles.

A programme owner is typically subordinate to the administrative authority in the official/administrative hierarchy. It is also possible that the administrative authority and program owner are the same entity.

For example, if a government has initiated a program to use the DIGIT-HCM product to reform Health Campaign Management, the respective department that is running the programme will be the programme owner.

**3d) Support Agency (SA)**

For this document, a “Support Agency” provides support in any functional aspect required by the program owner concerning that product implementation (for example, assistance in the maintenance of the product, technical or operational problem-solving, bug/error resolution).

A support agency would normally be engaged once the product has gone live, that is, during stages 5 and/or 6 of product implementation (see above).

A support agency will have access to such data as is necessary to perform their functions, and this shall normally be specified in the agreement/contract between the supporting agency and the programme owner/administrative authority responsible for that product implementation / the implementing agency responsible for that product implementation (in cases where the implementing agency sub-contracts support functions to the supporting agency).

In cases where a product owner, implementing agency, or program owner performs the role of a support agency, they may have access to such data as is specified for that role.

For example, suppose a given state government signs a contract with “Company L” to implement the DIGIT-HCM product in that state. In that case, and Company L sub-contracts support/maintenance/helpdesk activities to “Company M”, Company M is an IA.

**3e) Administrative Authority (AA)**

For this document, an administrative authority (AA) is a government entity that has the authority to enter into contracts/agreements with the product owner, implementing agency, and supporting agency.

Under prevailing law, an administrative authority has the power to permit other entities to access (collect, store, process, use, and/or share) data, including the PII of individuals within the territorial jurisdiction of that AA.

For this document, a product owner, implementing agency, or supporting agency cannot access data unless authorised to do so by the administrative authority. Such authorisation may be specified in an agreement/contract between the administrative authority and these entities. Such authorisation must be in keeping with prevailing laws and shall include such provisions and safeguards as are required under prevailing law.

An administrative authority may be a programme owner or a superior agency of a program owner in the administrative hierarchy.

For example, when a given state government decides to implement the DIGIT-HCM product in that state, the specific department of that state government which signs MOUs and/or contracts with eGov Foundation (as product owner) and with an IA to implement the DIGIT-HCM product is an AA.

#### 3f) Summary & Comparison Of Roles (PO, IA, Prog, SA)

|                | Product Owner (PO)                                                 | Implementing Agency (IA)                                          | Programme Owner (Prog)                                                                              | Support Agency (SA)                                                                                                               |
| -------------- | ------------------------------------------------------------------ | ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Definition     | The entity that owns, governs, or controls the product's codebase. | The entity that deploys and configures a product for the AA/Prog. | The entity that is responsible for the delivery of specific public goods, services, social welfare. | The entity that provides support in any technical/functional aspect required by the Prog, concerning that product implementation. |
| Access to Data | No, except to the extent agreed with Prog/AA.                      | Yes, during implementation only.                                  | Yes                                                                                                 | Yes, to the extent needed for support.                                                                                            |
| Example        | eGovernments Foundation                                            | Systems integrators (Example: PwC, Transerve)                     | NMCP or Polio department                                                                            | Any third party contracted for IT/programme support                                                                               |
