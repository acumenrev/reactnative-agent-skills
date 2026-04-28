---
name: api-layer-generator
description: Architect a scalable and type-safe API abstraction layer using Axios or Fetch, featuring robust error handling and interceptors.
---

# React Native API Layer Generator

## Instructions

Build a clean, decoupled API layer that separates networking logic from UI components. Follow these senior-level patterns:

1.  **Layered Architecture**: Separate the layer into:
    - `api-client.ts`: Base configuration (BaseURL, timeouts).
    - `interceptors.ts`: Request/response modification (Auth tokens, error logging).
    - `services/`: Domain-specific API calls (e.g., `userService.ts`, `productService.ts`).
    - `hooks/`: React Query or SWR hooks for managing data fetching state in the UI.
2.  **Axios Interceptors**: Use interceptors to automatically inject Authorization headers (e.g., Bearer tokens) and handle global error codes like `401 Unauthorized` (for token refresh logic).
3.  **Strict Typing**: Every API call should have a defined Request and Response type. Use tools like `zod` or `io-ts` if runtime validation is required, but at minimum, provide full TypeScript coverage.
4.  **Centralized Error Handling**: Define a standard `AppError` type. Handle common network issues (timeout, offline) and server errors in one place to ensure consistent UI feedback.
5.  **Environment Variables**: Use `react-native-config` or `expo-constants` to manage different API endpoints for development, staging, and production. Never hardcode URLs.
6.  **Resource Cleanup**: Ensure that API requests can be aborted (using `AbortController` or Axios `CancelToken`) to prevent state updates on unmounted components.

## Example Prompts

- "Set up a centralized Axios client with a 10-second timeout and an interceptor that adds a JWT token from secure storage to every request."
- "Create a 'UserService' with methods for 'getProfile', 'updateProfile', and 'uploadAvatar'. Include TypeScript interfaces for all payloads and responses."
- "Generate a custom hook 'useFetchProducts' that uses an API service and handles loading, error, and data states using a standard reducer pattern or React Query."

## Expected Output

- An `api/` directory structure:
  - `client.ts`: The configured Axios/Fetch instance.
  - `types.ts`: Shared DTOs and Error types.
  - `services/`: Individual files for different API domains.
  - `hooks/`: (Optional) Custom hooks for data fetching.

## Edge Cases & Common Mistakes

- **Token Refresh Race Conditions**: When multiple requests fail with 401 simultaneously, ensure the refresh logic only runs once and queues subsequent requests.
- **Handling FormData**: File uploads in React Native require specific `FormData` handling (e.g., `{ uri, name, type }` objects for images).
- **Ignoring Offline State**: Not checking for network connectivity before attempting a request. Use `@react-native-community/netinfo` to handle offline gracefully.
- **Leaking Secrets**: Accidentally logging sensitive API responses or headers in production. Ensure logging is gated by `__DEV__`.
