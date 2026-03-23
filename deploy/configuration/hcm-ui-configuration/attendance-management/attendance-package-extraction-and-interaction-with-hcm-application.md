---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/iVdFjJNtaUlTFjgyyYVV/deploy/configuration/ui-configuration/attendance-management/attendance-package-extraction-and-interaction-with-hcm-application
---

# Attendance Package Extraction & Interaction with HCM Application

## Interaction With Attendance Package

Below is the diagram of the components that are in the DIGIT HCM app and attendance package, and how the interaction happens:

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-02-27 at 3.11.54 PM.png" alt=""><figcaption></figcaption></figure>

## New Files / Changes Required In HCM App

1. Add the attendance package dependency in pubspec.
2. Create a bloc that extends the attendance listener class and creates the override methods.
3. Create model classes that import attendance models and add a companion class.
4. Create local and remote repositories as per project requirements and structure.
5. Add a typedef for repositories in untils/typedef.
6. Initialise repo in network manager, and create oplog.
7. Create SQL tables in case of offline.
8. Add navigation to manage the attendance page from the HCM app, and pass the required fields.
