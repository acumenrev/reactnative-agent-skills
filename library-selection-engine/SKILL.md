---
name: library-selection-engine
description: Systematically evaluates and selects the best third-party libraries for React Native projects based on technical health, compatibility, and community standards.
---

# React Native Library Selection Engine

## Instructions

Your task is to identify and validate the most suitable third-party libraries for a React Native project. Unlike web development, React Native library selection must account for native code dependencies, platform-specific bugs, and compatibility with the React Native "Bridge" or "New Architecture."

### Evaluation Criteria
1.  **Technical Health:** Last commit date, frequency of releases, number of active contributors, and ratio of open/closed issues.
2.  **Platform Compatibility:** Does it support iOS, Android, and potentially Web/Windows? Does it require specific native versions (e.g., iOS 13+)?
3.  **Expo Support:** Is it compatible with Expo Go? If not, does it provide an Expo Config Plugin for use with Development Builds (Prebuild)?
4.  **Architecture Alignment:** Does it support the New Architecture (TurboModules/Fabric)? Does it rely on deprecated APIs?
5.  **Footprint:** Impact on bundle size (JS) and binary size (Native). Use tools like `bundle-phobia` for JS.
6.  **Dependency Hell:** Does it have peer dependencies that conflict with the current project's versions of `react` or `react-native`?

### Selection Process
-   **Step 1: Discovery:** Search GitHub, npm, and community curated lists (like `react-native-directory`).
-   **Step 2: Filtering:** Eliminate unmaintained or low-quality candidates.
-   **Step 3: Comparison:** Compare the top 2-3 candidates against the project-specific requirements.
-   **Step 4: Verification:** Check for known "gotchas" in the library's issue tracker (e.g., "Doesn't work on Android 14").

## Example Prompts
- "I need a library for SQLite persistence. It must support the New Architecture and have an Expo Config Plugin. What's the best choice?"
- "Find a lightweight alternative to `moment.js` that works flawlessly with React Native's Intl polyfills."
- "What is the industry standard for handling deep links in a large-scale React Native app using React Navigation?"

## Expected Output
A structured recommendation including:
-   **The Winner:** The primary recommended library with a direct link to documentation.
-   **Rationale:** 3-5 bullet points explaining why this library was chosen over others.
-   **Installation Guide:** Exact commands and any mandatory native configuration (e.g., `pod install`, `AndroidManifest.xml` changes).
-   **Alternatives:** 1-2 "Honorable Mentions" for specific edge cases.

## Edge Cases & Common Mistakes
-   **The "Abandonware" Trap:** Recommending a library with 10k stars that hasn't been updated in 2 years and fails on current React Native versions.
-   **Ignoring Native Linking:** Failing to mention that a library requires `npx expo prebuild` or manual native linking in older RN versions.
-   **Peer Dependency Conflicts:** Recommending a library that requires `react-native@^0.72` when the user is on `0.74`.
