---
name: screen-generator
description: Scaffold complete React Native screens with integrated state management, navigation, and feature-aligned layouts.
---

# React Native Screen Generator

## Instructions

Generate comprehensive screens that serve as the building blocks of a React Native application. Follow these best practices:

1.  **Feature-Based Architecture**: Organize screens within feature folders (e.g., `src/features/auth/screens/LoginScreen.tsx`). Avoid a flat `src/screens` directory for large projects.
2.  **Layout Patterns**: Use `SafeAreaView` or `useSafeAreaInsets` to ensure content is visible on all devices. Implement common layout patterns like `KeyboardAvoidingView` for forms.
3.  **State Management**: Use local state (`useState`, `useReducer`) for UI-specific logic. Integrate with global state (Redux, Zustand, Context) via custom hooks for business logic.
4.  **Navigation Integration**: Type the navigation and route props using React Navigation's `StackScreenProps` or similar. Access navigation via the `useNavigation` and `useRoute` hooks for better modularity.
5.  **Lifecycle Management**: Use `useEffect` for data fetching or subscriptions. Utilize `useFocusEffect` from React Navigation for logic that should trigger when the screen comes into focus.
6.  **Loading & Error States**: Every screen should handle its own loading, empty, and error states gracefully, often by composing reusable UI components.
7.  **Performance**: Optimize heavy screens by deferring non-essential renders or using `FlatList` for long lists instead of `ScrollView`.

## Example Prompts

- "Create a 'ProductDetails' screen that fetches data based on a 'productId' route param. Include an image gallery, description, and an 'Add to Cart' footer."
- "Generate a 'ProfileSettings' screen with a list of toggle options (Notifications, Privacy, etc.) and a 'Save Changes' button. Use local state to track changes."
- "Build a 'FeedScreen' that displays a paginated list of posts using FlatList. Implement pull-to-refresh and a loading spinner for the initial fetch."

## Expected Output

A professional-grade screen component including:
- TypeScript interfaces for navigation params and local state.
- Integration with navigation hooks.
- Layout using `SafeAreaView` and consistent spacing.
- Implementation of primary business logic (fetching, form handling).
- Optimized styles using `StyleSheet`.

## Edge Cases & Common Mistakes

- **Keyboard Overlap**: Forgetting to wrap forms in `KeyboardAvoidingView` or `KeyboardAwareScrollView`, leading to hidden inputs.
- **Stale Data**: Not refreshing data when navigating back to a screen. Use `useFocusEffect` or `onFocus` listeners to keep data fresh.
- **Deep Linking**: Screens should be designed to handle being opened via deep links, meaning all required data should be fetchable from the route parameters (e.g., an ID).
- **Heavy Renders**: Placing too much logic or too many complex components in a single screen, leading to slow transitions. Break down screens into smaller feature-level components.
