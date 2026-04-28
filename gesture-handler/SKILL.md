---
name: gesture-handler
description: Implement complex, native-feeling touch interactions using React Native Gesture Handler's modern API and Reanimated integration.
---

# Gesture Handler Expert

## Instructions

For robust gesture support, use `react-native-gesture-handler` (RNGH) version 2+ with the new `Gesture` object API.

1.  **Gesture Composition**: Use `Gesture.Race()`, `Gesture.Simultaneous()`, and `Gesture.Exclusive()` to manage how multiple gestures interact (e.g., panning while zooming).
2.  **State Management**: Use `onStart`, `onUpdate`, `onEnd`, and `onFinalize` callbacks to handle the lifecycle of a gesture.
3.  **Reanimated Integration**: Bind gestures directly to Shared Values. Use `'worklet';` within callbacks to ensure gestures are processed entirely on the UI thread for zero-latency response.
4.  **Hit Slop & Boundaries**: Use `.hitSlop()` to increase touch targets and `.activeCursor()` or boundaries to restrict movement within a specific area.
5.  **Root Wrap**: Ensure the entire application (or the gesture-heavy area) is wrapped in `GestureHandlerRootView` to enable gesture recognition on both iOS and Android.
6.  **Platform Consistency**: Test gestures on both platforms, as Android's touch system behaves differently from iOS's (e.g., scroll view interception).

## Example Prompts

- "Implement a pinch-to-zoom gesture for an Image component that updates its scale shared value."
- "Create a swipe-to-delete interaction for a list item with a resistance effect and an execution threshold."
- "Build a draggable bottom sheet that snaps to specific 'snap points' using PanGesture and Reanimated springs."

## Expected Output

- Declarative gesture definitions using the `Gesture` object.
- Integration code connecting `GestureDetector` with `Animated.View`.
- Clean separation of gesture logic and UI thread updates.

## Edge Cases & Common Mistakes

- **Forgetting `GestureHandlerRootView`**: This is the most common cause of gestures not firing at all, especially on Android.
- **Nested ScrollViews**: Native scroll views often "steal" touch events. Use `.simultaneousWithExternalGesture()` or `disallowInterruption` to manage conflicts.
- **Heavy JS Logic in Callbacks**: Performing heavy computations on the JS thread inside a gesture update will lead to "jank." Always move logic to worklets or the UI thread.
