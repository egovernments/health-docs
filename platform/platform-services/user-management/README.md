# User Management

The objective of User Management in DIGIT HRMS service is to provide a service that manages all the employees enrolled in the system. HRMS provides extensive APIs to create, update, and search employees with attributes like assignments, service history, jurisdiction, etc. HRMS can be treated as a sub-set of the egov-user service, Every employee created through HRMS will also be created as a user in egov-user.

### Pre-requisites <a href="#pre-requisites" id="pre-requisites"></a>

Before you proceed with the documentation, make sure the following pre-requisites are met:&#x20;

* _Java 8._
* Kafka server is up and running.
* egov-persister service is running and has Hrms service persister config path added in it.
* PSQL server is running and a database is created to store employee data.
* Dependency services should be up and running:
  * egov-user - [Source code](https://github.com/egovernments/Core-Platform/tree/health-digit-master/core-services/egov-user)
  * egov-notification-mail - [Source code](https://github.com/egovernments/DIGIT-Dev/tree/health-digit-master/core-services/egov-notification-mail)&#x20;
  * user-otp - [Source code](https://github.com/egovernments/DIGIT-Dev/tree/health-digit-master/core-services/user-otp)

### Key Functionalities <a href="#key-functionalities" id="key-functionalities"></a>

* This service provides a feature to create, update, and search the employee in the system.
* It provides a feature to add various roles to an employee under multiple jurisdictions.
* It provides a feature to deactivate and reactivate an employee.
* It records the employee details such as assignment details, jurisdiction details, and personal details.

**Setup Details**

The source code for an [User Management](https://github.com/egovernments/DIGIT-Dev/tree/health-digit-master/business-services/egov-hrms) (egov-hrms) is present in the digit-dev Git repo. The spring boot application needs the **Lombok\*** extension added to the IDE to load it. Once the application is up and running, the API requests can be posted to the URL and the IDs can be generated.&#x20;

**\***In the case of IntelliJ, the plugin can be installed directly. For eclipse, the Lombok jar location has to be added in the eclipse.ini file in this format javaagent:lombok.jar.

Following are the properties in the application.properties file in the HRMS service, which is configurable:

| **Property**                                      | **Value**                                        | **Remarks**                                                                                                                                            |
| ------------------------------------------------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <p>egov.hrms.employee.app.link</p><p> </p>        | https://health-dev.digit.org/employee/user/login | This is the link to the heath web app, which differs based on the environment.                                                                         |
| <p>egov.hrms.default.pagination.limit</p><p> </p> | 200                                              | This is the pagination limit on search results of employee search, it can be set to any numeric value without decimals.                                |
| <p>egov.hrms.default.pwd.length</p><p> </p>       | 10                                               | This is the length of password to be generated at the time of employee creation. However, please ensure this is in sync with the egov-user pwd policy. |
| egov.hrms.auto.generate.password                  | false                                            | Password can be set while creating the user. Use false when random password generation is not required.                                                |
| <p>open.search.enabled.roles</p><p> </p>          | <p>SUPERUSER,ADMIN</p><p> </p>                   | This is a list of role codes that are allowed to perform an open-search in hrms.                                                                       |
| kafka.topics.notification.sms                     | egov.core.notification.sms                       | Kafka Topic to push the sms request. Please ensure this is in sync with egov-notification-sms service.                                                 |
| <p>kafka.topics.save.service</p><p> </p>          | save-hrms-employee                               | Kafka topic to push the save request in hrms. Please ensure this in sync with the persister.                                                           |
| <p>kafka.topics.update.service</p><p> </p>        | update-hrms-employee                             | Kafka topic to push the update request in hrms. Please ensure this in sync with the persister.                                                         |
| <p>egov.idgen.ack.name</p><p> </p>                | <p>hrms.employeecode</p><p> </p>                 | Key to be configured in Idgen alongwith the ID format to generate employee code.                                                                       |
| egov.idgen.ack.format                             | <p>EMP-[city]-[SEQ_EG_HRMS_EMP_CODE]</p><p> </p> | Format to be configured in ID gen to generate employee code.                                                                                           |

### Configuration Details

* EmployeeDepartment.json&#x20;

```
{
  "tenantId": "default",
  "moduleName": "egov-hrms",
  "EmployeeDepartment": [
    {
      "code": "NMCP",
      "active": true
    },
    {
      "code": "TECH",
      "active": true
    },
    {
      "code": "WAREHOUSE",
      "active": true
    },
    {
      "code": "ADM",
      "active": true
    }
  ]
}
```

* Degree

```
{
  "tenantId": "default",
  "moduleName": "egov-hrms",
  "Degree": [
    {
      "code": "MATRICULATION",
      "active": true
    },
    {
      "code": "10+2/EQUIVALENTDIPLOMA",
      "active": true
    },
    {
      "code": "B.A/B.SC./B.COM/BBA",
      "active": true
    },
    {
      "code": "LLB/LLM",
      "active": true
    },
    {
      "code": "B.E/B.TECH.",
      "active": true
    },
    {
      "code": "M.A/M.COM./M.SC.",
      "active": true
    },
    {
      "code": "M.E/M.TECH.",
      "active": true
    },
    {
      "code": "MBA/PGDM",
      "active": true
    },
    {
      "code": "DOCTORATE",
      "active": true
    },
    {
      "code": "OTHER",
      "active": true
    }
  ]
}
```

* Employee Status

```
{
  "tenantId": "default",
  "moduleName": "egov-hrms",
  "EmployeeStatus": [
    {
      "code": "ACTIVE",
      "active": true
    },
    {
      "code": "INACTIVE",
      "active": true
    }
  ]
}
```

* Employee Type

```
{
  "tenantId": "default",
  "moduleName": "egov-hrms",
  "EmployeeType": [
    {
      "code": "PERMANENT",
      "active": true
    },
    {
      "code": "TEMPORARY",
      "active": true
    },
    {
      "code": "DAILYWAGES",
      "active": true
    },
    {
      "code": "CONTRACT",
      "active": true
    },
    {
      "code": "DEPUTATION",
      "active": true
    }
  ]
}
```

* Reason For Deactivation or Reactivation

```
{
  "tenantId": "default",
  "moduleName": "egov-hrms",
  "DeactivationReason": [
    {
      "code": "OTHERS",
      "active": true
    },
    {
      "code": "ORDERBYCOMMISSIONER",
      "active": true
    }
  ]
}
```

* Roles

```
{
  "tenantId": "default",
  "moduleName": "ACCESSCONTROL-ROLES",
  "roles": [
    {
      "code": "SYSTEM_ADMINISTRATOR",
      "name": "System Administrator",
      "description": "System Administrator"
    },
    {
      "code": "REGISTRAR",
      "name": "Registrar",
      "description": "Registrar"
    },
    {
      "code": "DISTRIBUTOR",
      "name": "Distributor",
      "description": "Distributor"
    },
    {
      "code": "SUPERUSER",
      "name": "Super User",
      "description": "Super User. Can change all master data and has access to all the system screens."
    },
    {
      "code": "NATIONAL_SUPERVISOR",
      "name": "National Supervisor",
      "description": "Supervisor who can view National health dashboard"
    },
    {
      "code": "PROVINCIAL_SUPERVISOR",
      "name": "Provincial Supervisor",
      "description": "Supervisor who can view Provincial health dashboard"
    },
    {
      "code": "DISTRICT_SUPERVISOR",
      "name": "District Supervisor",
      "description": "Supervisor who can view District health dashboard"
    },
    {
      "code": "FIELD_SUPERVISOR",
      "name": "Field Supervisor",
      "description": "Supervisor who can view Field health dashboard"
    },
    {
      "code": "SUPERVISOR",
      "name": "Supervisor",
      "description": "Supervisor"
    },
    {
      "code": "WAREHOUSE_MANAGER",
      "name": "Warehouse Manager",
      "description": "Warehouse manager"
    },
    {
      "code": "INTERNAL_MICROSERVICE_ROLE",
      "name": "Internal Microservice Role",
      "description": "Internal role for plain access"
    },
    {
      "code": "CITIZEN",
      "name": "Citizen",
      "description": "Citizen who can raise complaint"
    },
    {
      "code": "PGR-ADMIN",
      "name": "PGR Administrator",
      "description": "Admin role that has super access over the system"
    },
    {
      "code": "HRMS_ADMIN",
      "name": "HRMS Admin",
      "description": "HRMS Admin"
    },
    {
      "code": "HELPDESK_USER",
      "name": "HELPDESK USER",
      "description": "HELPDESK USER"
    },
    {
      "code": "L2_SUPPORT",
      "name": "L2 Support",
      "description": "L2 Support"
    },
    {
      "code": "CSR",
      "name": "CSR",
      "description": "CSR"
    }
  ]
}
```

* Boundary

{% embed url="https://github.com/egovernments/health-campaign-mdms/blob/DEV/data/default/egov-location/boundary-data.json" %}

### API Details

Refer to the Swagger API for YAML file details: [UserManagement.yaml](https://github.com/egovernments/DIGIT-Dev/blob/health-digit-master/business-services/Docs/hrms-v1.0.0.yaml)

#### persister configuration: <a href="#persister-configuration" id="persister-configuration"></a>

{% embed url="https://github.com/egovernments/health-campaign-config/blob/v1.1.0/egov-persister/hrms-employee-persister.yml" %}

**Postman collection**

[Click here](https://github.com/egovernments/DIGIT-Dev/blob/health-digit-master/business-services/Docs/Egov-HRMS.postman\_collection.json)
