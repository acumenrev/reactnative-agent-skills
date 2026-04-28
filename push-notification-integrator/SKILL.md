---
name: push-notification-integrator
description: Master cross-platform push notification integration using FCM, APNs, and powerful local notification tools.
---

# Push Notification Integrator

## Instructions

Push notifications require a combination of native configuration, cloud services, and frontend handling.

1.  **Unified Messaging Service**: Use Firebase Cloud Messaging (FCM) as the primary bridge for both iOS and Android to simplify the backend implementation.
2.  **Native Setup**: Rigorously follow the setup for `AppDelegate.mm` (iOS) and `AndroidManifest.xml` (Android). Ensure APNs certificates and FCM server keys are correctly configured.
3.  **Handling Notifications**: Implement handlers for three distinct states:
    - **Foreground**: Show a local notification (via `Notifee`) or a custom in-app banner.
    - **Background/Quit**: Handle the interaction when a user taps a notification to open the app.
    - **Initial Notification**: Use `getInitialNotification()` to handle deep links or specific navigation when the app is launched from a cold start.
4.  **Permissions**: Request permissions explicitly using `Messaging().requestPermission()`. Provide a clear rationale to the user before the system prompt appears to increase opt-in rates.
5.  **Token Management**: Store the FCM token on your backend. Implement logic to refresh the token when it changes.
6.  **Deep Linking**: Map notification data payloads (e.g., `screen: 'Details', id: '123'`) to your navigation system (e.g., React Navigation) to direct users to specific content.

## Example Prompts

- "Integrate @react-native-firebase/messaging for push notifications and set up the foreground message listener."
- "Configure Notifee to display rich local notifications with images and action buttons on Android."
- "Implement a deep-linking strategy that navigates to a specific 'Order Details' screen when a notification is tapped."

## Expected Output

- Native configuration changes (summarized or provided as snippets).
- TypeScript service for managing notification listeners and permissions.
- Integration with the app's navigation system for handling interaction events.

## Edge Cases & Common Mistakes

- **Silent Notifications on iOS**: Forgetting to enable 'Remote notifications' in Background Modes under XCode Capabilities.
- **Android Notification Channels**: On Android 8.0+, notifications *must* be assigned to a channel or they won't appear.
- **Handling Payload Consistency**: Ensure the data payload structure is consistent between iOS and Android to avoid crashes in the handler logic.
