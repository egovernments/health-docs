---
description: >-
  The attendance management package is a comprehensive solution for managing
  attendance.
---

# Attendance Management Package

To learn more about Attendance Management, [click here.](https://health.digit.org/hcm-product-suite/health-products/frontline-workers-app/user-manual/common-functions/attendance-management)

Link to the Pub Package:&#x20;

{% embed url="https://pub.dev/packages/attendance_management" %}

## Role

* SUPERVISOR

## **Features**

* Attendance Pages: The package includes several pages like mark\_attendance.dart, manage\_attendance.dart, and session\_select.dart that provides the user interface for managing attendance.

## Getting Started

To use this package, add the following dependency to your pubspec.yaml file:

```
dependencies:
  attendance_management: ^latest
```

## Integrating with the HCM Application:&#x20;

1. To integrate this package with the HCM application, run the main function located in `health-campaign-field-worker-app/tools/attendance_management_imports.dart.`&#x20;
   * This will automatically add the necessary imports, mapper initializers, route config, setting initial data, and repository initialization to the required files.
2. Now make sure you are on the path `apps/health_campaign_field_worker_app` and run the command:

```dart
dart run build_runner build --delete-conflicting-outputs
```

This adds a package route to the `main router.gr.dart`&#x20;

3. Navigate to the project bloc since we need to fetch registers and attendee data after login:

```dart
final RemoteRepository<AttendanceRegisterModel, AttendanceRegisterSearchModel>
  attendanceRemoteRepository;
final LocalRepository<AttendanceRegisterModel, AttendanceRegisterSearchModel>
  attendanceLocalRepository;
final LocalRepository<AttendanceLogModel, AttendanceLogSearchModel>
  attendanceLogLocalRepository;
final RemoteRepository<AttendanceLogModel, AttendanceLogSearchModel>
  attendanceLogRemoteRepository;
```

4. Next, navigate to the line where the project staff search is written, and add the below code in the try-catch where we check the role and fetch attendance data:

```dart
if (context.loggedInUserRoles
            .where(
              (role) => role.code == RolesType.districtSupervisor.toValue(),
            )
            .toList()
            .isNotEmpty) {
          final individual = await individualRemoteRepository.search(
            IndividualSearchModel(
              userUuid: [projectStaff.userId.toString()],
            ),
          );
          final attendanceRegisters = await attendanceRemoteRepository.search(
            AttendanceRegisterSearchModel(
              staffId: individual.first.id,
              referenceId: projectStaff.projectId,
            ),
          );
          await attendanceLocalRepository.bulkCreate(attendanceRegisters);

          for (final register in attendanceRegisters) {
            if (register.attendees != null &&
                (register.attendees ?? []).isNotEmpty) {
              try {
                final individuals = await individualRemoteRepository.search(
                  IndividualSearchModel(
                    id: register.attendees!
                        .map((e) => e.individualId!)
                        .toList(),
                  ),
                );
                await individualLocalRepository.bulkCreate(individuals);
                final logs = await attendanceLogRemoteRepository.search(
                  AttendanceLogSearchModel(
                    registerId: register.id,
                  ),
                );
                await attendanceLogLocalRepository.bulkCreate(logs);
              } catch (_) {
                emit(state.copyWith(
                  loading: false,
                  syncError: ProjectSyncErrorType.project,
                ));

                return;
              }
            }
          }
        }
```

5. Make sure you are on the path `apps/health_campaign_field_worker_app` and run the command:

```dart
dart run build_runner build --delete-conflicting-outputs
```

This adds a package route to the `main router.gr.dart`&#x20;

By following these steps, you'll successfully integrate and can use attendance module within your application.

## Sequence Diagram

<br>

<figure><img src="../../../../.gitbook/assets/attendance_sequence (2).png" alt=""><figcaption></figcaption></figure>
