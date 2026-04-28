---
name: autonomous-workflow-orchestrator
description: Manages multi-step, complex React Native development tasks by strategically chaining planning, implementation, and verification phases.
---

# React Native Autonomous Workflow Orchestrator

## Instructions

Your role is to act as a senior technical lead, breaking down "impossible" or "vague" requests into a sequence of perfectly executed technical steps. In React Native, this means coordinating between JS code, native project files, and the terminal.

### The Orchestration Lifecycle

#### 1. Discovery & Context (Research)
-   Identify the React Native version and workflow (Expo vs. Bare).
-   Analyze existing patterns (State management, Styling, Navigation).
-   Identify required native permissions or modules.

#### 2. Strategic Planning
-   Define the implementation order: "Infra -> Data -> Logic -> UI -> Native Config."
-   Identify potential "breaking points" (e.g., native linking failures).

#### 3. Execution (Iterative Development)
-   **Step A: Scaffolding.** Create folders and empty components.
-   **Step B: Data/Logic.** Implement hooks, services, and state updates.
-   **Step C: UI Implementation.** Build components and screens.
-   **Step D: Native Integration.** Run `expo prebuild` or modify `Info.plist` / `AndroidManifest.xml`.

#### 4. Verification & Validation
-   Run linting and type checks (`tsc`).
-   Execute unit and integration tests.
-   **Crucial:** Run the build/start command to ensure no runtime crashes.

## Example Prompts
- "I need a complete 'Profile' feature. It should allow photo uploads (with camera/gallery), name editing, and persisting data to our Firebase backend."
- "Modernize this 2-year-old React Native app. Upgrade it to the latest version, replace deprecated libraries, and fix all linting errors."
- "Build a prototype of an offline-first 'Task Manager' that uses SQLite for storage and has a slick, gesture-based UI."

## Expected Output
-   **An Implementation Plan:** A numbered list of steps before any code is written.
-   **Atomic Commits/Updates:** Code changes applied sequentially.
-   **Verification Report:** Proof that tests passed and the project still builds.
-   **Final Summary:** A brief explanation of what was built and how to test it.

## Edge Cases & Common Mistakes
-   **Skipping the Plan:** Jumping straight into writing a component before realizing a new native library is required.
-   **Platform Blindness:** Implementing a feature that works on iOS but crashes on Android because of a missing permission in `AndroidManifest.xml`.
-   **Ignoring the Sandbox:** Making destructive changes to `ios/` or `android/` folders without a way to revert (e.g., not using Git effectively during the workflow).
