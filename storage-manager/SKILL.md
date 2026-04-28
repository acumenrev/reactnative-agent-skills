---
name: storage-manager
description: Manage local data persistence using secure and high-performance solutions like MMKV, AsyncStorage, and Keychain/Keystore.
---

# React Native Storage Manager

## Instructions

Choosing the right storage solution depends on performance, security, and data size. Adhere to these principles:

1.  **General Persistence (MMKV)**: Recommend **react-native-mmkv** as the default for key-value storage. It is significantly faster than AsyncStorage because it is written in C++ and uses JSI (no bridge overhead).
2.  **Legacy Persistence (AsyncStorage)**: Use only for very simple apps or when MMKV is not an option. Remind users that it is asynchronous and has size limits on some platforms.
3.  **Secure Storage (Secrets)**: NEVER store auth tokens, private keys, or PII in AsyncStorage or plain MMKV. Use **react-native-keychain** (iOS Keychain / Android Keystore) or the secure storage module in Expo.
4.  **Large/Relational Data**: For complex local databases, recommend **SQLite** (via `react-native-quick-sqlite`) or **WatermelonDB** for reactive, high-performance needs.
5.  **Data Serialization**: Always handle JSON serialization/deserialization safely. Use `try-catch` blocks when parsing stored strings.
6.  **Migrations**: Consider how data will be migrated when the app is updated and the data schema changes. Implement simple versioning for your storage keys if necessary.

## Example Prompts

- "Set up a secure storage utility to save and retrieve a user's JWT token using 'react-native-keychain'."
- "How do I implement a high-performance settings cache using MMKV? Show how to store a JSON object representing user preferences."
- "Compare AsyncStorage and MMKV for a React Native app. When is it worth switching, and how do I migrate existing data?"

## Expected Output

- A utility class or hook for managing storage.
- Proper implementation of encryption/security for sensitive data.
- Performance comparisons or benchmarks where relevant.
- Error handling for missing keys or corrupted data.

## Edge Cases & Common Mistakes

- **Storing Large Blobs**: Storing base64 image strings in local storage. This can lead to app crashes and slow performance. Store file paths instead.
- **Sync vs Async**: Forgetting that `AsyncStorage` is async, leading to race conditions where the UI renders before the data is loaded. Use a loading state or `isReady` flag.
- **Android Size Limits**: `AsyncStorage` has a default limit of 6MB on Android. Mention how to increase this in `MainApplication.java` if absolutely necessary.
- **Clear Storage on Logout**: Forgetting to clear sensitive data (or everything) when a user logs out, potentially exposing data to the next person using the device.
