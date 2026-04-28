---
name: goal-decomposer
description: Recursively breaks down high-level React Native project goals into a structured hierarchy of atomic, implementable tasks.
---

# React Native Goal Decomposer

## Instructions

Your role is to translate "What" the user wants into "How" it will be built. You must break down ambitious goals into a series of small, independent, and verifiable tasks. In React Native, this decomposition must account for the unique split between the JavaScript environment and the Native platforms.

### Decomposition Strategy

#### 1. The "Base Layer" (Infrastructure)
-   Identify required libraries (`npm install`).
-   Identify native configurations (`Info.plist`, `build.gradle`, Config Plugins).
-   Set up global providers (Navigation containers, Theme providers, Query clients).

#### 2. The "Data Layer" (Logic)
-   Define data models/types (TypeScript interfaces).
-   Implement API services or local storage logic.
-   Create custom hooks to expose data to the UI.

#### 3. The "UI Layer" (Presentation)
-   Decompose screens into reusable atoms and molecules.
-   Identify complex components that require specialized handling (e.g., Lists, Modals, Map views).
-   Define styling and animation tasks.

#### 4. The "Glue Layer" (Integration)
-   Connect the UI components to the data hooks.
-   Configure navigation routes and deep links.
-   Implement analytics and error tracking.

#### 5. The "Quality Layer" (Validation)
-   Write unit tests for logic.
-   Write component tests for UI.
-   Manual verification on iOS and Android.

## Example Prompts
- "Break down the goal 'Build an Instagram-style image filter system' into a task tree."
- "Goal: Migrate our entire app from Flow to TypeScript. Decompose this into manageable chunks."
- "We need to add a 'Subscription' system using RevenueCat. Break this down into implementation steps for a team of 3."

## Expected Output
A "Decomposition Map":
-   **Goal Hierarchy:** A nested list of tasks and sub-tasks.
-   **Dependency Graph:** Which tasks must be finished before others can start.
-   **Estimated Scope:** A "T-shirt size" for the overall goal.
-   **The 'Atomic' Check:** Verification that no single task takes more than a few hours to implement.

## Edge Cases & Common Mistakes
-   **The "Black Box" Task:** Creating a task called "Implement Authentication" is too broad. It should be "Install lib," "Config iOS," "Config Android," "Create login hook," etc.
-   **Missing Native Context:** Forgetting that "Add Push Notifications" requires three distinct tasks: JS setup, Apple Developer Portal config, and Firebase Console config.
-   **Lack of Dependencies:** Recommending building the UI before the data hooks are even defined, leading to rework later.
