---
name: auto-fix-loop
description: Iteratively refines React Native code by identifying, diagnosing, and fixing errors until stability and performance goals are achieved.
---

# Auto-Fix Loop Expert

## Instructions

The Auto-Fix Loop is a systematic approach to resolving complex bugs and performance issues in React Native. It moves beyond single-shot fixes, employing a repetitive cycle of execution, error capture, and refinement to ensure the final solution is robust and optimized.

### 1. Diagnostic Integration
- **Log Analysis:** Use Metro logs, Android Logcat, and iOS Xcode logs to identify the root cause of crashes or warnings.
- **Redbox/Yellowbox Capture:** Automatically parse React Native error boundaries and warnings to feed the fix loop.
- **Symbolication:** Ensure native stack traces are symbolicated to correctly identify the failing line in JavaScript or Native code.

### 2. Iterative Refinement Cycle
- **Step 1: Reproduce:** Confirm the issue using a test case or by running the app.
- **Step 2: Fix:** Apply a targeted fix based on the diagnostic data.
- **Step 3: Validate:** Run the build/test again. If it fails, capture the new error and repeat.
- **Step 4: Optimize:** Once the fix works, perform a final pass to ensure it doesn't introduce performance regressions or anti-patterns.

### 3. Build & Link Failure Resolution
- **Dependency Conflicts:** If a library installation fails, iteratively try alternative versions or resolution strategies (e.g., `npm-force-resolutions`).
- **Pod/Gradle Fixes:** Automatically handle common build errors like "Duplicate resource" or "Architectures mismatch" by applying standard project-level fixes.

### 4. Termination Logic
- **Diminishing Returns:** Recognize when a loop is oscillating between two states or when errors are becoming increasingly obscure, and stop to request manual intervention.
- **Success Criteria:** Define clear "done" states (e.g., zero TypeScript errors, successful build, test passing).

## Example Prompts

- "Run an auto-fix loop to resolve the current build failure on Android. Try common Gradle fixes and dependency alignments until it compiles."
- "There is a persistent 'Undefined is not an object' error in the UserProfile screen. Iteratively debug and fix the data-fetching logic until the screen loads reliably."
- "Improve the performance of the search results list. Run a refinement loop focusing on reducing re-renders and optimizing image loading."

## Expected Output

- A series of incremental code improvements leading to a final, stable solution.
- A log of the attempts made and why specific fixes were chosen or discarded.
- A verified, working build or feature that meets the performance/stability requirements.

## Edge Cases & Common Mistakes

- **Patching the Symptom:** Fixing a specific crash without addressing the underlying state management or data integrity issue, causing the loop to re-enter later.
- **Infinite Looping:** Failing to detect a circular dependency or an environment-specific error that cannot be fixed by code changes alone.
- **Ignoring Warnings:** Focus exclusively on "Redbox" errors while letting "Yellowbox" warnings accumulate, which often hide the root cause of future stability issues.
