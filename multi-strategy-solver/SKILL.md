---
name: multi-strategy-solver
description: Generates and compares multiple technical strategies for React Native problems to identify the most efficient, maintainable, and platform-appropriate solution.
---

# Multi-Strategy Solver Expert

## Instructions

The Multi-Strategy Solver is used when a React Native problem has multiple potential solutions with different trade-offs. Instead of picking the first available option, it systematically explores and compares several approaches to find the optimal path.

### 1. Strategy Generation
- **Identify Approaches:** Generate at least 2-3 distinct ways to solve a problem (e.g., "Use a 3rd party library," "Build a custom Native Module," or "Implement it purely in JavaScript").
- **Platform-Aware Options:** Consider strategies that might differ by platform (e.g., using `CoreML` on iOS vs. `TensorFlow Lite` on Android).

### 2. Trade-off Analysis
- **Performance:** Compare the impact on frame rates, memory usage, and the React Native bridge.
- **Maintainability:** Evaluate the complexity of the code and the long-term support of external dependencies.
- **Development Speed:** Consider the time required to implement and test each strategy.
- **Binary Size:** For native solutions, account for the increase in the final `.ipa` or `.apk` size.

### 3. Selection Criteria
- **Weighting:** Apply project-specific weights to the trade-offs (e.g., "In this project, performance is more important than development speed").
- **Evidence-Based Choice:** Use documentation, benchmarks, or small proof-of-concept tests to justify the final selection.

### 4. Implementation Design
- **Hybrid Approaches:** Sometimes the best strategy is a combination of two (e.g., a JS-based UI with a native-backed data processor).
- **Fallback Planning:** Ensure the chosen strategy has a viable fallback if it fails to meet requirements during implementation.

## Example Prompts

- "We need to implement a complex image filter. Compare the following strategies: 1) `react-native-image-filter-kit`, 2) Custom Skia shaders via `react-native-skia`, and 3) Custom Native Modules for iOS/Android."
- "The app needs real-time data sync. Analyze the pros and cons of using Firebase Realtime Database vs. a custom GraphQL Subscription setup via Apollo."
- "We are seeing slow list performance. Compare optimizing our current FlatList with `memo` vs. migrating to `flash-list` by Shopify."

## Expected Output

- A structured comparison matrix or report of the generated strategies.
- A clear recommendation for the "Best Strategy" with a detailed justification.
- A high-level implementation plan for the chosen solution.

## Edge Cases & Common Mistakes

- **Bias Toward the Familiar:** Recommending a strategy just because it was used in a previous project, regardless of its fit for the current problem.
- **Ignoring Native Complexity:** Underestimating the effort required to maintain custom native code compared to a slightly less performant JS library.
- **Over-Engineering:** Choosing a "perfect" but overly complex strategy for a feature that doesn't require high performance or high scalability.
