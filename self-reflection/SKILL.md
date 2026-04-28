---
name: self-reflection
description: Critically analyzes and improves React Native code by identifying performance bottlenecks, architectural flaws, and platform-specific inconsistencies.
---

# Self-Reflection Expert

## Instructions

Self-reflection is the process of critically evaluating your own React Native implementations to ensure they meet the highest standards of performance, maintainability, and user experience. This skill involves finding subtle issues that might pass basic linting but fail in real-world mobile environments.

### 1. Performance Audit
- **Re-render Analysis:** Check for unnecessary re-renders in components using `React.memo`, `useMemo`, and `useCallback`. Identify if object/array literals are being passed as props.
- **List Optimization:** Audit `FlatList` or `SectionList` implementations for proper `keyExtractor`, `initialNumToRender`, and `windowSize`. Ensure `getItemLayout` is used where possible for large lists.
- **Bridge Congestion:** Reflect on the volume of data being sent over the bridge. Suggest moving heavy computations to the native layer or using JSI-based libraries.

### 2. Architectural Critique
- **State Management:** Evaluate if the chosen state management (Redux, Zustand, Context) is appropriate for the feature complexity. Check for "prop drilling" or bloated global state.
- **Logic Separation:** Ensure business logic is separated from UI components using hooks or services.
- **Dependency Health:** Identify redundant or heavy dependencies that could be replaced with lighter alternatives or native implementations.

### 3. Platform & UX Polish
- **Layout Consistency:** Verify that layouts work on small screens (iPhone SE) and large tablets (iPad/Android tablets). Check for hardcoded dimensions vs. `Flexbox` or `useWindowDimensions`.
- **Interaction Feedback:** Ensure all touchables have appropriate feedback (`Opacity`, `Highlight`) and hit slops for accessibility.
- **Edge-to-Edge:** Reflect on whether the UI respects `SafeAreaView` and handles system bars correctly on both iOS and Android.

## Example Prompts

- "Critique the implementation of this Home screen component. Look specifically for potential performance issues in the FlatList and unnecessary state updates."
- "Perform a self-reflection on our Redux architecture. Are we over-complicating the state for the current feature set? Suggest a simplified approach if applicable."
- "Audit this custom animation hook. Is it running on the UI thread? Check for potential frame drops on low-end Android devices."

## Expected Output

- A detailed report of identified issues categorized by severity (High, Medium, Low).
- Actionable suggestions for code improvement and optimization.
- Refined code snippets demonstrating the proposed fixes.

## Edge Cases & Common Mistakes

- **Ignoring the JS Thread:** Focusing only on native performance while neglecting JS-side bottlenecks like heavy JSON parsing or inefficient array transformations.
- **Over-Optimization:** Introducing complex memoization patterns where a simple component restructure would suffice, leading to harder-to-maintain code.
- **Simulator Bias:** Failing to reflect on how code will perform on actual hardware, particularly mid-range Android devices which are often the bottleneck in React Native apps.
