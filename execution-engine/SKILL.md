---
name: execution-engine
description: Orchestrates and executes complex React Native development tasks with sequential precision and consistency.
---

# Execution Engine Expert

## Instructions

The Execution Engine is responsible for the reliable, step-by-step implementation of React Native features, refactors, and bug fixes. It ensures that every action—from installing dependencies to modifying native code—is performed in the correct order to maintain project stability and build integrity.

### 1. Sequential Workflow Orchestration
- **Dependency First:** Always ensure required npm/yarn packages are installed before modifying code that imports them.
- **Native Linkage:** For non-Expo or prebuild projects, execute `npx pod-install` (iOS) after adding any library with native dependencies.
- **Incremental Implementation:** Break down large features into logical commits or steps (e.g., Type definitions -> API Layer -> Logic -> UI).

### 2. Environment-Aware Execution
- **Architecture Detection:** Determine if the project uses the New Architecture (TurboModules/Fabric) or the Bridge and execute tasks accordingly.
- **Build System Management:** Correctly navigate between `android/` (Gradle/Kotlin/Java) and `ios/` (CocoaPods/Swift/Obj-C) directories when native changes are required.

### 3. Verification and Validation
- **Linting & Typing:** Run `tsc` and `eslint` after code modifications to catch immediate regressions.
- **Build Checks:** For native changes, verify that the project still compiles using `npx react-native run-ios` or `run-android`.

### 4. Consistency Maintenance
- **Styling Standards:** Ensure all new components strictly follow the established styling pattern (e.g., StyleSheet.create, Tailwind/NativeWind, or Styled Components).
- **Naming Conventions:** Enforce consistency in component naming (PascalCase) and file naming (kebab-case or PascalCase).

## Example Prompts

- "Execute the implementation of the new Auth flow, starting with the Cognito SDK integration followed by the Redux state setup and finally the Login screen UI."
- "Sequentially refactor the navigation logic from React Navigation v5 to v6, ensuring all deep linking configurations are updated before changing the navigator components."
- "Implement a custom TurboModule for device-level encryption, following the official New Architecture execution path: spec definition, codegen, and native implementation."

## Expected Output

- A fully functional, verified implementation of the requested task.
- Clean, idiomatic React Native code that adheres to project-specific conventions.
- Successful verification through linting, type-checking, and build logs.

## Edge Cases & Common Mistakes

- **Skipping Pod Install:** Modifying `package.json` with native libraries but failing to run `pod install`, leading to "Module not found" or native crashes on iOS.
- **Stale Metro Cache:** Failing to restart the Metro bundler with `--reset-cache` after significant dependency changes or configuration updates.
- **Native/JS Mismatch:** Updating JS code that relies on a specific native module version without verifying the native project files (AppDelegate, MainApplication) are in sync.
