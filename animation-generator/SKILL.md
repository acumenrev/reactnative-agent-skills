---
name: animation-generator
description: Expertly craft high-performance, fluid animations using React Native Reanimated and modern declarative patterns.
---

# Animation Generator

## Instructions

When implementing animations in React Native, prioritize performance by offloading work to the UI thread. Use `react-native-reanimated` (version 3+) as the primary library.

1.  **Use Shared Values**: Always use `useSharedValue` for state that needs to be animated. Avoid using React `useState` for animation frames.
2.  **Declarative Animation Hooks**: Utilize `useAnimatedStyle` to map shared values to view properties. Wrap animated components with `Animated.View`, `Animated.Text`, etc.
3.  **UI Thread Execution**: Ensure heavy computations and style updates happen on the UI thread. Use worklets (`'worklet';`) when custom logic is needed inside animation callbacks.
4.  **Layout Animations**: Use Reanimated's built-in `Layout`, `Entering`, and `Exiting` animations for seamless layout transitions without manual interpolation.
5.  **Interpolation**: Use `interpolate()` for mapping values (e.g., scroll position to opacity) instead of manual math to ensure clarity and performance.
6.  **Springs and Timing**: Default to `withSpring` for natural, physics-based interactions. Use `withTiming` for predictable, duration-based transitions (e.g., fades).

## Example Prompts

- "Create a spring-based scale animation for a button when it is pressed using Reanimated."
- "Implement a staggered entrance animation for a list of cards where each card fades in and slides up."
- "Build a smooth, circular progress loader that uses a shared value to animate the stroke dash offset."

## Expected Output

- Modular, performant animation code using `react-native-reanimated`.
- Proper TypeScript typing for shared values and animated styles.
- Components wrapped in `Animated.*` and utilizing `useAnimatedStyle`.

## Edge Cases & Common Mistakes

- **Animating Non-GPU Properties**: Avoid animating properties like `width`, `height`, or `flex` as they trigger layout passes on the shadow thread. Stick to `transform` and `opacity`.
- **Bridge Congestion**: Do not pass shared values back to the JS thread frequently (e.g., via `runOnJS`) unless absolutely necessary for business logic.
- **Missing `useAnimatedStyle` dependency array**: Reanimated handles dependencies automatically in most cases, but ensure any external variables used inside are stable or properly accounted for.
