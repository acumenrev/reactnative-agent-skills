---
name: background-task-manager
description: Efficiently manage background execution, periodic syncs, and long-running tasks while adhering to iOS and Android system constraints.
---

# Background Task Manager

## Instructions

Running code in the background on mobile requires navigating strict OS limitations to prevent battery drain.

1.  **Select the Right Tool**:
    - Use `react-native-background-fetch` for periodic tasks (e.g., syncing data every 15 mins).
    - Use `react-native-background-actions` for long-running foreground tasks (e.g., music playback, active navigation).
    - Use `WorkManager` (Android) and `Background Tasks` (iOS) native modules for high-reliability background processing.
2.  **Respect OS Limits**: iOS strictly limits background execution time. Tasks should ideally complete within 30 seconds. On Android, use Foreground Services for any task visible to the user.
3.  **Headless JS**: Use `AppRegistry.registerHeadlessTask` on Android to run JavaScript tasks even when the app is closed. Note that this is Android-only; iOS requires a different approach via native background fetch.
4.  **Handle Network/Battery States**: Configure tasks to only run under specific conditions (e.g., connected to Wi-Fi, device charging) to avoid negatively impacting the user experience.
5.  **Task Termination**: Ensure tasks call their completion callbacks promptly. Failure to do so on iOS will result in the app being penalized or killed by the system.
6.  **State Management**: Avoid relying on global app state (Redux/Context) in background tasks, as the UI environment may not be fully initialized. Use persistent storage (MMKV, SQLite) for task data.

## Example Prompts

- "Configure a periodic background fetch task that syncs the local database with the server every hour."
- "Implement a background upload service that continues transferring large files even if the user leaves the app."
- "Set up a Headless JS task on Android to process incoming data from a broadcast receiver while the app is killed."

## Expected Output

- Setup code for background fetch or foreground service.
- Logic for task registration and execution.
- Handling of system events (low battery, network loss) during task execution.

## Edge Cases & Common Mistakes

- **Assuming Infinite Time**: Thinking background tasks can run as long as they want. They will be killed by the OS if they exceed time limits.
- **UI Interaction in Background**: Attempting to update the UI or show alerts directly from a background task (except for local notifications).
- **Ignoring "Low Power Mode"**: Systems will often disable all background activity when the device is in power-saving mode.
