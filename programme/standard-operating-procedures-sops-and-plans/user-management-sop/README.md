# User Management SOP

## Overview

This document describes various users of the HCM system and lays out the processes to manage the access and provisioning related aspects. Broadly, the users can be categorised as permanent users of the HCM system who will be identified by their individual usernames and passwords, and the users who will be provisioned in the system for temporary durations and identified by the codes assigned (henceforth referred to as coded users). The user management module of the HCM platform will provide the interface to create and manage all types of users.&#x20;

## Types of users

| User type                                                                                | <p>Role mapping in DIGIT</p><p><br></p>                                              | What they will do                                                              | Organization       | Type of access              |
| ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------ | --------------------------- |
| Supervisor-National                                                                      | Dashboard user at the central level                                                  | Use the dashboard at national level, that is, all the provinces                | NMCP               | Web user                    |
| Supervisor-Provincial                                                                    | Dashboard user at the provincial level                                               | Use the dashboard at the provincial level, that is, their individual provinces | NMCP               | Web user                    |
| Supervisor-Provincial                                                                    | Dashboard user at the district level                                                 | Use the dashboard at the district level                                        | NMCP               | Web user                    |
| Supervisor-Local Monitors                                                                | Dashboard user at the village level                                                  | Supervisor to field teams                                                      | Temporary workers  | Mobile app                  |
| Registradors                                                                             | Registrar                                                                            | Part of distribution teams                                                     | Temporary workers  | Mobile app                  |
| <p>Warehouse users-National</p><p><br></p>                                               | Warehouse manager role but tagged with the national boundary                         | Keep stock of inventory for the facility they are managing                     | Temporary workers  | Mobile app                  |
| Warehouse- Provincial                                                                    | Warehouse manager role but tagged with the provincial boundary                       | <p><br></p>                                                                    | <p><br></p>        | <p><br></p>                 |
| Warehouse-District                                                                       | Warehouse manager role but tagged with the district-level boundary                   | <p><br></p>                                                                    | <p><br></p>        | <p><br></p>                 |
| Warehouse-Community                                                                      | Warehouse manager role but tagged with the community-level boundary                  | <p><br></p>                                                                    | <p><br></p>        | <p><br></p>                 |
| Logistics-They ship material between warehouse and teams, that is, the movement of stock | In terms of the actions they are performing, they are the same as warehouse managers | <p><br></p>                                                                    | <p><br></p>        | <p><br></p>                 |
| Helpdesk users (L1, L2)                                                                  | Access to the complaints inbox based on their level                                  | Take, resolve, reject or escalate technical queries from different users       | CHAI country team  | Web user                    |
| Temporary users provisioned for UAT with different role action mappings                  | <p><br></p>                                                                          | <p><br></p>                                                                    | NMCP               | Access based on their roles |
| Temporary users provisioned for trainings with different role action mappings            | <p><br></p>                                                                          | <p><br></p>                                                                    | NMCP               | Access based on their roles |

### Provisioning process for each user type

1. Supervisors at Central, Provincial and District levels

* Information is sent from NMCP to CHAI for provisioning via email.
* CHAI provisions the users and sends the list of created users back to NMCP.

2. Local monitors

* CHAI sends the list to eGov before the campaign for bulk provisioning.
* eGov will send the list to CHAI after provisioning with codes and defaulted passwords.
* During the campaign, CHAI helpdesk will provision the new LM (if any) using the DIGITs user management UI.
* These will be deactivated from the system once the campaign ends based on inputs from CHAI team.

Note : All the communication to be on emails.

3. Registrars

* CHAI sends the list to eGov before the campaign for bulk provisioning.
* eGov team will do the bulk provisioning using backend APIs.
* eGov will send the list of created users to CHAI after provisioning with codes and defaulted passwords.
* During the campaign, CHAI helpdesk will provision the new LM (if any) using the DIGITs user msanagement UI one by one.
* These will be deactivated from the system once the campaign ends based on inputs from CHAI team.

4. Warehouse users

* Information is sent from NMCP to CHAI for provisioning.&#x20;
* CHAI provisions the users and send the list of created users back to NMCP.

5. Helpdesk staff: With system admin functionality

* CHAI sends the list to eGov before the campaign for bulk provisioning.
* eGov will send the list to CHAI after provisioning with codes and defaulted passwords.

6. Temporarily provisioned users for UAT/Training

* CHAI will send the list of users to eGov a week before the UATs/training for provisioning into the system.
* eGov will send the list to CHAI after provisioning with user names and passwords.
* These will be deleted once the UAT/training is over.

### Password reset mechanism&#x20;

* For all kinds of users , the password reset would be managed by the system admin, who will be a part of the helpdesk.
* Users who have forgotten their passwords would reach out to the helpdesk on the designated helpline number and request for a new password.
* System admin would reset their passwords using a two-factor authentication. The email ID for retrieving the passwords would be the same for all users and would be managed by the system administrator.
* The system administrator would regenerate the password and communicate to the users over a phone call or in a Whatsapp group.

### Template for user creation&#x20;

This would be as per the [Master Data template](master-data-collection-template/).

### Recommendations around managing usernames

1. A username, once created during user creation, must not be changed.

&#x20;      \- Regarding the use of special characters: It is recommended that only commonly known special characters like period (.) be used in the username to make it easy to remember

&#x20;      \- Regarding use of the capital case: It is recommended to use either all lowercase or all uppercase characters to make it easy for users to remember and enter the login credentials (lowercase preferred).

&#x20;      \- It is recommended to keep passwords simple (and defaulted to a single value/string) so that mobile app users do not forget the password, and hence, do not face a barrier in using the app.

It has been assumed that user creation for temporary users who keep changing during the campaign would be taken care of by the helpdesk team.\
