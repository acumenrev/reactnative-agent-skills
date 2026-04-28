---
name: constraint-handler
description: Rigorously enforces project-specific, platform-mandated, and architectural constraints to ensure React Native code remains compliant and functional.
---

# Constraint Handler Expert

## Instructions

The Constraint Handler ensures that every line of code produced adheres to the strict technical and business boundaries of a React Native project. It prioritizes constraints over "easy" solutions to ensure long-term project health and App Store/Play Store compliance.

### 1. Project-Level Constraints
- **Managed vs. Bare:** Enforce Expo-compatible solutions in Managed projects (no native code changes). In Bare projects, allow for `android/` and `ios/` modifications.
- **Dependency Restrictions:** Prevent the introduction of libraries that are forbidden (e.g., "Do not use `react-native-reanimated` v1") or redundant.
- **Node/React Native Versions:** Ensure all code and package additions are compatible with the specific versions defined in `package.json`.

### 2. Platform-Specific Constraints
- **iOS Compliance:** Enforce Apple's privacy guidelines (e.g., proper plist descriptions for permissions) and human interface guidelines.
- **Android Standards:** Ensure compatibility with required SDK levels and proper handling of Android-specific hardware back buttons or notification behaviors.
- **Hermes/JSC:** Validate that code and libraries work with the project's specific JS engine (e.g., avoiding features not supported in older JSC versions).

### 3. Architectural & Style Constraints
- **Pattern Enforcement:** Strictly follow established patterns like Atomic Design, Clean Architecture, or specific Redux/Zustand structures.
- **Type Safety:** Enforce strict TypeScript rules (no `any`, required interfaces) if the project is configured for it.
- **Accessibility (a11y):** Ensure all interactive elements have appropriate `accessibilityLabel`, `accessibilityRole`, and meet contrast requirements.

### 4. Continuous Validation
- **Pre-Commit Checks:** Simulate or run lint/type-checkers as a primary filter for all code changes.
- **Conflict Resolution:** When two constraints conflict (e.g., "High performance" vs. "Legacy device support"), present the trade-offs clearly.

## Example Prompts

- "Implement a new Image Picker feature, strictly adhering to the Expo Managed Workflow constraints. Do not use any library that requires manual linking."
- "Refactor this component to comply with our 'No Inline Styles' and 'Strict Accessibility' constraints."
- "Ensure all new API calls follow our 'Retry with Exponential Backoff' and 'Secure Token Storage' architectural constraints."

## Expected Output

- Code that is 100% compliant with all identified project and platform constraints.
- Clear documentation when a specific constraint forced a non-standard or more complex implementation.
- Successful verification through automated tools (Lint, TSC, Jest).

## Edge Cases & Common Mistakes

- **"Happy Path" Implementation:** Forgetting a platform-specific constraint (like iOS SafeArea) because the solution works on the developer's simulator.
- **Silent Failures:** Using a JS feature that works in the latest Chrome but breaks on the project's specific Android version or JS engine.
- **Constraint Neglect:** Prioritizing feature speed over a security or privacy constraint, leading to App Store rejection.
