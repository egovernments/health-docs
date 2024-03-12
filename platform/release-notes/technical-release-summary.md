# Technical Release Summary

## Impacted Services

### Project:

* Implemented validation for updating the project start date and the end date. Implementing this ensures that any changes made to these critical campaigns adhere to the predefined criteria.
* Added the number of sessions field in additional details for the attendance registry, which enhances the system's ability to manage attendance tracking within projects. This field specifically denotes the frequency of attendance-taking sessions for a given project. Each session represents an instance where attendance is recorded, typically within a single day. For instance, if a project requires attendance twice daily (for example, morning and afternoon sessions), the number of sessions field would indicate ‘2’ to reflect this frequency. This information provides crucial context for understanding the attendance requirements and scheduling patterns within the project.

### Individual:

* Added the ability to search by user UUID (Universally Unique Identifier) for individual search. This addition expands the search capabilities within the DIGIT-HCM platform, providing users with a more versatile and efficient means of locating specific individuals. A UUID is a unique identifier assigned to each user within the system. This new feature allows users to quickly retrieve information about a particular individual by entering their UUID into the search functionality. By leveraging UUIDs, which ensure each user has a distinct identifier, the search process becomes highly precise and reliable, minimising the risk of ambiguity or confusion, particularly in large datasets.

### Referral Management:

**Health Facility Referral Feature Update**

**New Feature: HF Referral**

DIGIT-HCM now includes a Health Facility Referral (HF Referral) functionality that enhances the platform’s capability to efficiently manage referrals across health facilities. This addition is aimed at improving coordination and communication, ensuring a smoother referral process.

### Stock Registry:

Enhance the inventory flow with the sender ID and the receiver ID added. Including sender and receiver IDs offers flexibility in handling inventory transactions within the DIGIT-HCM platform. Transactions can involve movement between warehouses, from warehouse to staff, from staff to staff, or any combination thereof. This accommodates various scenarios, such as inter-departmental transfers, internal requisitions, or supplier deliveries.

1. Sender Identification: The sender ID specifies the entity initiating the inventory transaction. This could be a warehouse, indicating that inventory items are being dispatched from a specific storage location. Alternatively, it could represent an individual staff member responsible for authorising the transfer of inventory items.
2. Receiver Identification: The receiver ID denotes the entity or individual receiving the inventory items. Similar to the sender ID, this could represent either a warehouse where the items are being delivered or an individual staff member who is the designated recipient.

### Attendance:

Implemented offline-enabled functionality in the Attendance Module. Implementing this functionality in the attendance module significantly enhances the usability and reliability of the DIGIT-HCM platform, especially in environments where internet connectivity may be intermittent or unavailable.
