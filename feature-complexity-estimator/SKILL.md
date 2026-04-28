---
name: feature-complexity-estimator
description: Predicts the implementation effort for React Native features by analyzing cross-platform requirements, native integrations, and performance constraints.
---

# React Native Feature Complexity Estimator

## Instructions

Your goal is to provide realistic, engineering-based estimates for new features. In React Native, complexity is rarely linear; a simple UI change can be easy, but a "simple" change that requires a new native permission or background task can explode in complexity.

### Complexity Drivers

#### 1. UI & Animation
-   **Low:** Standard components (`View`, `Text`, `Pressable`).
-   **Medium:** Complex lists (`FlashList`), standard `Animated` transitions, custom SVGs.
-   **High:** `Reanimated` gestures, shared element transitions, 60fps interaction-heavy UIs.

#### 2. Native Capabilities
-   **Low:** Local state, `AsyncStorage`.
-   **Medium:** Camera (standard), Geolocation, Biometrics.
-   **High:** Bluetooth/BLE, Custom Background Tasks, low-level Socket connections, VoIP (CallKit/ConnectionService).

#### 3. Data & Sync
-   **Low:** Fetching and displaying JSON.
-   **Medium:** Pagination, Pull-to-refresh, simple local caching.
-   **High:** Offline-first sync, Conflict resolution, Real-time multi-user state.

#### 4. Platform Parity
-   Does the feature have a native equivalent on both iOS and Android? 
-   Is the UI design "Material" or "Human Interface," and does it need to adapt automatically?

### Estimation Framework
-   **Discovery/Research:** 10-20% of effort.
-   **Implementation (JS):** 40-50% of effort.
-   **Native Configuration/Bridging:** 10-20% of effort.
-   **Testing (Multi-platform/Multi-device):** 20% of effort.

## Example Prompts
- "Estimate the effort to add a 'Document Scanner' feature using a third-party native SDK."
- "What is the complexity breakdown for implementing a deep-linking system that handles password resets and referral codes?"
- "Analyze the risk and complexity of migrating our entire navigation from Tab-based to Drawer-based for both platforms."

## Expected Output
A detailed "Complexity Breakdown":
-   **Overall Rating:** S, M, L, XL or Fibonacci points.
-   **Complexity Drivers:** Top 3 reasons why this feature is hard/easy.
-   **Task Breakdown:** A list of atomic sub-tasks with individual weights.
-   **Risk Assessment:** Potential roadblocks (e.g., "Apple might reject this permission usage").

## Edge Cases & Common Mistakes
-   **The "It's Just a Library" Fallacy:** Assuming that because a library exists on npm, the implementation is trivial. You must account for configuration, bugs, and bundle size.
-   **Ignoring QA:** Forgetting that every React Native feature must be tested on at least two operating systems and various screen sizes.
-   **The "Happy Path" Bias:** Estimating based on everything working perfectly, ignoring the time needed for error handling, offline states, and edge cases.
