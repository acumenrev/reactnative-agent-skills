---
name: component-generator
description: Generate reusable, high-performance, and type-safe React Native components using modern functional patterns and TypeScript.
---

# React Native Component Generator

## Instructions

When generating React Native components, adhere to the following senior-level engineering standards:

1.  **Functional Components & Hooks**: Always use functional components with React Hooks. Avoid class components.
2.  **TypeScript First**: Define props using `interface` or `type`. Ensure all props are explicitly typed, including optional ones. Use `React.FC` or preferred function declaration patterns.
3.  **StyleSheet Separation**: Use `StyleSheet.create` for all styles. Place styles at the bottom of the file to keep the component logic clean. Avoid inline styles unless a property is truly dynamic (e.g., animated values or user-selected colors).
4.  **Semantic Components**: Prefer built-in React Native components (`View`, `Text`, `TouchableOpacity`, `Pressable`) over generic ones. Use `Pressable` for new components as it offers better interaction state handling.
5.  **Variants & Extensibility**: Build components to support variants (e.g., `primary`, `secondary`, `outline`). Allow passing of custom `style` props (usually `StyleProp<ViewStyle>`) to enable layout adjustments from parents.
6.  **Accessibility**: Include basic accessibility props like `accessible`, `accessibilityLabel`, `accessibilityRole`, and `accessibilityHint`.
7.  **Performance**: Use `React.memo` for components that render frequently or have expensive render logic. Use `useCallback` for event handlers passed to children.

## Example Prompts

- "Generate a reusable 'PrimaryButton' component that accepts a label, an onPress handler, and an optional loading state. Include styles for 'pressed' state using Pressable."
- "Create a 'UserCard' component that displays an avatar image, name, and bio. Use TypeScript for props and include a container style with a subtle shadow and rounded corners."
- "Build a 'CustomInput' component with a label, error message display, and support for all standard TextInput props using 'TextInputProps' from react-native."

## Expected Output

A single, self-contained TypeScript file (unless a multi-file structure is requested) containing:
- Necessary imports from `react`, `react-native`, and other libraries.
- A clearly defined `Props` interface.
- The functional component implementation with proper hook usage.
- A `StyleSheet` object containing all static styles.
- Export of the component (usually default export).

## Edge Cases & Common Mistakes

- **Shadows on Android vs iOS**: Shadows in RN are platform-specific. iOS uses `shadowColor`, `shadowOffset`, etc., while Android requires `elevation`. Always provide both or use a helper.
- **Z-Index Issues**: `zIndex` behavior can vary between platforms. Use `elevation` on Android alongside `zIndex` if needed.
- **Platform-Specific Styles**: Use `Platform.select` or `Platform.OS === 'ios'` for styles that need to differ (e.g., padding for status bars, font weights).
- **Not Handling 'Safe Area'**: When building layout components, remember that content might overlap with notches or home indicators. Use `SafeAreaView` or `useSafeAreaInsets` from `react-native-safe-area-context`.
