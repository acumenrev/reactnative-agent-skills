---
name: performance-optimizer
description: Identify and resolve performance bottlenecks in React Native apps, focusing on render cycles, list efficiency, and bridge traffic.
---

# React Native Performance Optimizer

## Instructions

Performance in React Native is about keeping the Main (UI) thread and the JS thread running smoothly. Focus on these core areas:

1.  **Render Optimization**:
    - Use `React.memo`, `useMemo`, and `useCallback` strategically to prevent unnecessary re-renders of expensive component trees.
    - Avoid passing anonymous functions or object literals as props to children in the render body.
2.  **FlatList & SectionList Tuning**: This is the #1 source of lag.
    - Use `getItemLayout` for fixed-height items.
    - Set `initialNumToRender`, `maxToRenderPerBatch`, and `windowSize`.
    - Ensure `keyExtractor` uses unique IDs, not indices.
    - Use `removeClippedSubviews={true}` (default on Android).
3.  **Bridge Traffic Reduction**: Minimize the data sent across the bridge. Avoid frequent, large JSON payloads. Use native modules or `TurboModules` for high-performance tasks.
4.  **Image Optimization**: Use `@shopify/flash-list` for ultra-high performance lists. Use `react-native-fast-image` for better caching and performance than the default `Image` component.
5.  **Animation Performance**: Always use `useNativeDriver: true` with the `Animated` API where possible. For complex animations, recommend **React Native Reanimated** for 60FPS performance on the UI thread.
6.  **Profiling Tools**: Recommend using **React DevTools Profiler** to find slow renders and **Hermes Debugger** (via Flipper or Chrome) to analyze JS execution.
7.  **JS Engine**: Ensure **Hermes** is enabled for both iOS and Android to benefit from pre-compiled bytecode and lower memory usage.

## Example Prompts

- "My FlatList is lagging when I scroll through 500 items with images. How can I optimize it for a smooth 60FPS experience?"
- "Analyze this component for unnecessary re-renders and suggest where to apply 'memo' or 'useCallback'."
- "Explain how to move a heavy calculation from the JS thread to avoid blocking the UI, and show a Reanimated example for a gesture-based swipe card."

## Expected Output

- Targeted code changes to improve performance.
- Explanation of the bottleneck (e.g., "JS thread starvation," "unnecessary reconciliation").
- Configuration settings for lists or images.
- Step-by-step profiling guide.

## Edge Cases & Common Mistakes

- **Premature Optimization**: Applying `memo` everywhere, which can actually slow down the app due to comparison overhead. Use the profiler first.
- **Inline Objects/Functions**: `style={{ marginTop: 10 }}` or `onPress={() => doSomething()}` creates a new reference on every render, breaking `memo`.
- **Heavy Initialization**: Doing massive data processing in `useEffect` on the first render. Use background tasks or optimize the data structure.
- **Console Logs in Production**: `console.log` is synchronous and can significantly slow down the app. Ensure they are stripped in production builds.
