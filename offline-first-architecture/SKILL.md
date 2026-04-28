---
name: offline-first-architecture
description: Architect resilient, offline-ready applications that provide a seamless user experience regardless of network connectivity.
---

# Offline First Architecture

## Instructions

An offline-first approach ensures that the app remains functional and responsive even without an active internet connection.

1.  **Local Primary Storage**: Use a high-performance local database like `WatermelonDB` (for relational data), `Realm`, or `SQLite` as the primary source of truth for the UI.
2.  **Data Synchronization Strategy**: Use a sync engine to reconcile local changes with the remote server. Prioritize 'Pull' (get updates) then 'Push' (send local changes) patterns.
3.  **TanStack Query (Offline Mode)**: Utilize `react-query` with a persistent storage persister (e.g., `createSyncStoragePersister`) to cache API responses and handle automatic retries when the connection returns.
4.  **Conflict Resolution**: Implement strategies for data conflicts (e.g., Last Write Wins, Manual Merge, or Server Authority). Ensure the UI can handle 'Pending' states for unsynced data.
5.  **Connectivity Monitoring**: Use `@react-native-community/netinfo` to track connection status and trigger syncs or update the UI to show "Offline Mode" indicators.
6.  **Optimistic UI**: Implement optimistic updates for all user actions so the app feels instant. Roll back changes only if the server explicitly rejects the sync.

## Example Prompts

- "Design an offline-first data model using WatermelonDB for a task management app with sync capabilities."
- "Configure TanStack Query to persist its cache to MMKV and enable offline mutations with a request queue."
- "Implement a sync coordinator that handles background synchronization of local changes when the device comes back online."

## Expected Output

- Database schema and sync logic implementation.
- Integration of caching layers and persistence mechanisms.
- UI patterns for handling offline indicators and sync status.

## Edge Cases & Common Mistakes

- **Giant Initial Syncs**: Attempting to download the entire database on first launch. Use pagination and "Sync on Demand" for large datasets.
- **Ignoring Storage Limits**: Storing massive amounts of data or large images in the local DB without a cleanup/eviction policy.
- **Handling Binary Data**: Avoid storing large blobs/images directly in SQLite; store the file path and save the actual file to the filesystem.
