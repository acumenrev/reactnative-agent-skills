---
name: navigation-generator
description: Design and implement robust, type-safe navigation structures using React Navigation, supporting nested stacks, tabs, and drawers.
---

# React Native Navigation Generator

## Instructions

Navigation is the backbone of the mobile experience. When generating navigation structures, prioritize UX and type safety:

1.  **React Navigation v6/v7**: Target the latest stable versions of React Navigation. Use the component-based configuration or the hook-based approach as appropriate.
2.  **Strict Type Safety**: Define a `RootStackParamList` and nested param lists. Export these types so they can be used throughout the app with `useNavigation<NavigationProp<RootStackParamList>>`.
3.  **Nested Navigators**: Properly structure nested navigators (e.g., an `AuthStack` and an `AppStack` within a `RootStack`). Avoid deeply nested structures that complicate state and deep linking.
4.  **Navigation Guards**: Implement authentication-based conditional rendering (e.g., `userToken ? <AppStack /> : <AuthStack />`) instead of manual navigation calls after login.
5.  **Header Customization**: Use `screenOptions` to maintain a consistent look. Implement custom header components when the standard ones are insufficient.
6.  **Dynamic Params**: Ensure params are used for data identifiers (IDs) rather than passing large objects, which can bloat the navigation state and break deep linking.
7.  **Platform Defaults**: Respect platform-specific navigation patterns (e.g., Bottom Tabs on iOS, Drawer or Tabs on Android) where it improves the user experience.

## Example Prompts

- "Set up a Root Navigator with a 'Loading' screen that branches into an 'AuthStack' (Login, Signup) and a 'MainTabNavigator' based on auth state."
- "Create a Bottom Tab Navigator with three tabs: 'Home', 'Search', and 'Profile'. Ensure each tab has its own nested Stack Navigator for internal navigation."
- "Generate a type-safe navigation configuration for a Stack Navigator with 'Home', 'Details', and 'Settings' screens. The 'Details' screen should require a 'itemId' string param."

## Expected Output

- A `navigation/` directory or file containing:
- `RootStackParamList` and related TypeScript types.
- Navigator components (Stack, Tab, Drawer).
- Navigation Container setup.
- Helper hooks for typed navigation access.

## Edge Cases & Common Mistakes

- **Memory Leaks**: Not cleaning up listeners or subscriptions when screens are unmounted. Navigation events (`focus`, `blur`) are often better than `useEffect` for screen-specific lifecycle.
- **Passing Large Objects**: Passing a full 'User' object as a navigation param. This breaks when the app is restored from a background state or via deep link. Pass only the `userId`.
- **Inconsistent Android Back Button**: Not handling the hardware back button correctly in complex nested navigators or modals.
- **Resetting State**: Forgetting to use `navigation.reset()` when switching between major app sections (e.g., Logout), leading to users being able to 'go back' to authenticated screens.
