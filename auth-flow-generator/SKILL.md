---
name: auth-flow-generator
description: Build secure and seamless authentication flows, including login, signup, social auth, and token management with navigation guards.
---

# React Native Auth Flow Generator

## Instructions

Authentication in React Native requires a combination of secure storage, global state, and navigation logic. Implement these patterns:

1.  **Navigation Guards**: Use a top-level conditional in your Navigation Container. If `userToken` is null, show the `AuthStack`; otherwise, show the `AppStack`. This prevents users from manually navigating to protected screens.
2.  **Secure Token Storage**: Use `react-native-keychain` or `expo-secure-store` to save JWTs. Never use AsyncStorage for tokens.
3.  **Automatic Login**: Check for a stored token in the root component's `useEffect` or a specialized `AuthContext`. Show a splash/loading screen while the check is in progress.
4.  **Token Refresh Logic**: Implement an Axios interceptor to handle `401 Unauthorized` responses by attempting to refresh the token. If the refresh fails, clear the state and redirect to Login.
5.  **Form Validation**: Use `react-hook-form` with `yup` or `zod` for performant and type-safe login/signup forms. Avoid excessive re-renders caused by controlled inputs in large forms.
6.  **Social Auth**: When implementing Google/Apple sign-in, use the respective native libraries and handle the callback on the JS side to exchange a native token for your backend JWT.
7.  **Logout**: Ensure the logout process is atomic: 1. Clear local secure storage. 2. Reset the global auth state. 3. (Optional) Clear the API cache (e.g., React Query `queryClient.clear()`).

## Example Prompts

- "Build a complete Login screen with email/password validation, a loading state, and integration with a 'useAuth' hook that saves the token to Keychain."
- "Create an Auth Navigator that switches between 'Login', 'Signup', and 'Home' based on a 'token' variable in a Zustand store."
- "Implement a 'forgot password' flow that includes an email input screen and an OTP (One-Time Password) verification screen with a countdown timer."

## Expected Output

- A set of Screen components (Login, Signup, etc.).
- An `AuthContext` or `useAuth` hook managing the auth state.
- Navigation logic with guards.
- Secure storage utility calls.

## Edge Cases & Common Mistakes

- **Keeping Password in State**: Accidentally logging or keeping the raw password in a global store or long-lived variable. Keep it local to the login form.
- **Unencrypted Storage**: Using `AsyncStorage` for JWTs, which is accessible on rooted/jailbroken devices.
- **Not Handling Background State**: Not checking if a token has expired when the app returns from the background.
- **Flash of Wrong Screen**: A brief flash of the Login screen before the app realizes a token exists. Use an `isLoading` state in your root navigator.
