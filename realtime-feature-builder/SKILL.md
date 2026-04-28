---
name: realtime-feature-builder
description: Build low-latency, resilient real-time features like chat and live updates using WebSockets or Firebase.
---

# Realtime Feature Builder

## Instructions

Implementing real-time functionality requires careful handling of connectivity and state sync in mobile environments.

1.  **Choose the Right Backend**: Use WebSockets (via `Socket.io` or raw WS) for custom high-frequency updates, or Firebase (Firestore/Realtime Database) for seamless data syncing and offline persistence.
2.  **Connection Lifecycle**: Monitor the app's state (Active/Background). Disconnect or throttle updates when the app is in the background to save battery and data, and reconnect gracefully on resume.
3.  **Optimistic UI Updates**: Immediately update the local state when a user performs an action (e.g., sending a chat message) and then reconcile with the server response to ensure the UI feels instant.
4.  **Handle Reconnection**: Implement exponential backoff for reconnection attempts. Use a 'Connectivity' banner to inform users when the app is offline.
5.  **Message Queueing**: If an action occurs while offline, queue it locally and sync it once the connection is restored.
6.  **Security**: Ensure real-time streams are authenticated. Use JWT or Firebase Auth tokens to secure WebSocket channels and database rules.

## Example Prompts

- "Set up a Socket.io client in a React Native app with robust reconnection logic and state management."
- "Implement a real-time chat screen using Firestore with paginated 'infinite scroll' for message history."
- "Create a live stock-ticker feature that throttles updates when the component is not focused to optimize performance."

## Expected Output

- Clean integration code for WebSocket or Firebase listeners.
- Hooks for managing real-time data and connection status.
- UI components that handle loading, error, and optimistic states.

## Edge Cases & Common Mistakes

- **Memory Leaks**: Forgetting to unsubscribe from listeners in `useEffect` cleanup. Always close connections/listeners.
- **Race Conditions**: Handle scenarios where an older update arrives after a newer one. Use timestamps or versioning for data reconciliation.
- **Battery Drain**: Keeping a WebSocket open indefinitely in the background can lead to the OS killing the app. Use Push Notifications for background events instead.
