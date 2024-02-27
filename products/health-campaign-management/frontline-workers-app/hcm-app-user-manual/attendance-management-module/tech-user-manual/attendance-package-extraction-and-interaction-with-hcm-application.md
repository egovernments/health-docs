---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Attendance Package Extraction and Interaction with HCM Application

## How the HCM App Interacts with the Attendance Package

Below is the BLOC diagram of the components that are there in the HCM App and attendance package, and how the interaction happens:\
\


<figure><img src="https://lh7-us.googleusercontent.com/fQZ8dmYqjDnHwCf5-YNUb_AUzE1JkYVF-FAXyM5SubKPh0ENk99pHHJposypB1Q6iOflD7I2lrN6U2ltI16N5u1ByOG0Q1vl6uMyFfIQW6c-1FdP7lDyX__BAICWtnUd_uZ5QJ1C9Gz_RNbAmWcO32g" alt=""><figcaption></figcaption></figure>

### New files or changes needed in the HCM App:

1. Add attendance package dependency in pubspec.
2. Create a bloc that extends the attendance listener class and creates the override methods.
3. Create model classes that import attendance models and add companion class.
4. Create repositories local and remote as per project requirements and structure.
5. Add typedef for repositories in untils/typedef.
6. Initialise repo in network manager, and create oplog.
7. Create SQL tables in case of offline.
8. Add navigation to manage the attendance page from the HCM app, and pass the required fields.
