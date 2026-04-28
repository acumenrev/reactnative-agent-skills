---
name: debugging-assistant
description: Diagnose and resolve complex React Native issues, from JS crashes and Redbox errors to native build failures and performance bottlenecks.
---

# React Native Debugging Assistant

## Instructions

Debugging in React Native spans the JS, Bridge, and Native layers. Follow this systematic approach:

1.  **Error Classification**:
    - **Redbox/Logbox**: JS errors (undefined is not a function, component lifecycle errors).
    - **Yellowbox**: Warnings (Performance issues, deprecated APIs).
    - **Native Crashes**: Crash to home screen (NULL pointer exceptions in native modules, memory issues).
    - **Build Errors**: Gradle/Xcode failures (Dependency conflicts, linking issues).
2.  **JS Debugging Tools**:
    - **React DevTools**: Inspect the component tree, props, and state.
    - **Hermes Debugger**: Use Chrome or Flipper to debug JS execution on the Hermes engine.
    - **Console Logging**: Use `console.log` and `console.error` strategically. Mention `JSON.stringify(obj, null, 2)` for readable objects.
3.  **Network Debugging**: Use **Flipper Network Inspector** or **React Native Debugger** to see all API requests, headers, and responses.
4.  **Native Debugging**:
    - **Android**: Use `adb logcat` to see system-level logs and native crashes.
    - **iOS**: Use **Console.app** or the debug console in **Xcode** for native logs.
5.  **Build Issue Resolution**:
    - **Clean & Rebuild**: `watchman watch-del-all`, `rm -rf node_modules`, `cd ios && pod install`, `cd android && ./gradlew clean`.
    - **Dependency Conflicts**: Check `package.json` vs `Podfile.lock` or `build.gradle`.
6.  **Performance Profiling**: Use the **Perf Monitor** (in the dev menu) to see JS and UI thread FPS. Use the Profiler in React DevTools to find slow components.

## Example Prompts

- "My app is crashing on startup on Android after I added a new native library. How can I find the cause of the crash using adb logcat?"
- "I'm getting 'Invariant Violation: View config getter callback for component X must be a function'. What does this mean and how do I fix it?"
- "Help me debug a network request that works in Postman but fails in my React Native app with a 'Network Error'."

## Expected Output

- A clear explanation of the probable root cause.
- Step-by-step instructions to reproduce or fix the issue.
- Recommended tools (Flipper, Xcode, etc.) for deeper investigation.
- Shell commands for cleaning the build environment.

## Edge Cases & Common Mistakes

- **Assuming JS is the Cause**: Spending hours in JS code when the issue is a missing permission in `AndroidManifest.xml` or `Info.plist`.
- **Ignoring Warnings**: Allowing "Yellowbox" warnings to pile up, which can hide actual performance regressions or future-breaking changes.
- **Outdated Cache**: Forgetting to clear the Metro bundler cache (`npx react-native start --reset-cache`) after moving files or changing configuration.
- **Environmental Differences**: Debugging in the simulator and ignoring issues that only happen on physical devices (e.g., camera, sensors, or background execution).
