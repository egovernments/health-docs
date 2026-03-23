# Transit Post

## Overview

The **Transit Post Package** is a Flutter module designed to streamline transit post operations, such as selecting posts, scanning resources, and tracking deliveries. Built for seamless integration in larger logistics and delivery systems, it leverages Bloc for robust state management and uses reactive forms for capturing user input efficiently. The module is structured for reusability, testability, and separation of concerns via repository patterns.

***

## Key Features

### User Interface (Pages)

The user interface is organised into modular pages, each responsible for a distinct step in the transit post workflow. These pages are designed to be simple, responsive, and directly integrated with Bloc state management for dynamic updates.

* **transit\_post\_selection.dart**\
  UI for displaying and selecting available transit posts. Initiates the delivery process and triggers navigation to the recording step.
* **transit\_post\_record\_vaccination.dart**\
  UI for resource scanning (QR/barcode) and entry of delivery details using reactive forms. Performs validation and provides real-time feedback.
* **transit\_post\_acknowledgment.dart**\
  Displays a summary and acknowledgement after a successful delivery submission.
* **transit\_post\_wrapper.dart**\
  Acts as the parent widget, managing navigation and Bloc provisioning for the entire flow.

### State Management (Bloc Pattern)

The application uses the Bloc pattern to ensure predictable state management, clear separation of concerns, and a responsive user interface throughout the transit post workflow. Each Bloc handles a specific stage of the process:

* **TransitPostSelectionBloc**
  * Manages loading and selection of transit posts.
  * **Events:** LoadPosts, SelectPost
  * **States:** Loading, Loaded, Selected, Error
* **TransitPostRecordVaccinationBloc**
  * Handles scanning, form input, and delivery validation.
  * **Events:** StartScan, SubmitDelivery, ValidateInput
  * **States:** Initial, Scanning, Validated, Delivered, Error
* **TransitPostAcknowledgmentBloc**
  * Controls the acknowledgement and confirmation stage.
  * **Events:** Acknowledge, Reset
  * **States:** Pending, Acknowledged
* **Bloc Integration**
  * Each page provides or consumes its relevant Bloc using `BlocProvider` or `BlocConsumer`.
  * UI reacts to state changes for navigation and updates.

### Data Layer (Repositories)

The application follows the Repository pattern to keep business logic independent from data storage and networking, making the system modular, testable, and easy to extend. Two key repository abstractions are defined:

* **UserActionLocalRepository (abstract)**
  * Handles local persistence (e.g., SQLite, Hive)
  * **Methods:** saveDelivery, getPendingDeliveries, markAsAcknowledged
* **UserActionRemoteRepository (abstract)**
  * Handles remote persistence (API integration)
  * **Methods:** submitDelivery, fetchTransitPosts, fetchDeliveryHistory

### Reactive Forms

The application uses the `reactive_forms` package to manage dynamic and validated data entry during the transit post flow. This approach ensures a structured way to capture delivery details while providing immediate feedback to users.

* **Dynamic Form Handling** – Forms can adapt to different input types such as resource details, quantities, or delivery metadata, enabling flexible data capture for various scenarios.
* **Built-in Validation** – Validation rules are applied directly within the form controls, ensuring data accuracy. Errors and invalid inputs are highlighted in real time, guiding the user to correct issues before submission.
* **Seamless UI Feedback** – The form state is reactive, meaning any change in input instantly reflects in the UI. This creates a smooth user experience with live validation messages and input tracking.

By combining dynamic fields, validation, and real-time feedback, Reactive Forms make the delivery recording process reliable, user-friendly, and less prone to data entry errors.

***

## Key Classes & Structure

* **UI Widgets:**
  * `TransitPostSelectionPage`
  * `TransitPostRecordVaccinationPage`
  * `TransitPostAcknowledgmentPage`
  * `TransitPostWrapper`
* **Bloc Classes:**
  * `TransitPostSelectionBloc`, `TransitPostSelectionEvent`, `TransitPostSelectionState`
  * `TransitPostRecordVaccinationBloc`, `TransitPostRecordVaccinationEvent`, `TransitPostRecordVaccinationState`
  * `TransitPostAcknowledgmentBloc`, `TransitPostAcknowledgmentEvent`, `TransitPostAcknowledgmentState`
* **Repositories (Abstract):**
  * `UserActionLocalRepository`
  * `UserActionRemoteRepository`

***

{% hint style="info" %}
**Note**:\
The modular design makes the Transit Post Package extensible for other resource types and business rules by adding new pages, events, or repository implementations.
{% endhint %}

## Sequence Diagram

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdYp563ddxf2xx8zAn4vk56fuMlf-4P7iNwZjcOl8kg4jLSRCziJehBvseGEU-lZ2HAQCVj5xFbqwGFHbUZ5tuPl_DkLBG-wotRWTsqlU6CDf_-7xwtRgVMxl9mG7B4ammRtJBQ?key=h6xj56uLHjrcNj0msKKRCQ" alt=""><figcaption></figcaption></figure>

