---
name: migration-planner
description: Outlines safe and efficient migration paths for React Native projects, ensuring minimal downtime and no regressions during major version or library transitions.
---

# React Native Migration Planner

## Instructions

Your role is to orchestrate complex transitions in a React Native codebase. Migrations in mobile apps are high-stakes because of the "installed base" — you cannot easily force users to update, and a broken update can brick the app for thousands of users.

### Migration Strategies

#### 1. Version Upgrades (e.g., RN 0.72 to 0.75)
-   Use the `React Native Upgrade Helper` as a baseline.
-   Identify breaking changes in native code (`AppDelegate`, `MainApplication`, `build.gradle`).
-   Plan for "Dependency Synchronicity" — ensuring all third-party libs support the target version.

#### 2. Architectural Shifts (e.g., Expo Managed to Bare, Bridge to New Arch)
-   **Bridging the Gap:** Use `npx expo prebuild` to see what native changes are required.
-   **Component Migration:** Identify which components need to be rewritten for Fabric or TurboModules.

#### 3. Library Swaps (e.g., Redux to Zustand, React Navigation to Expo Router)
-   **Incremental Adoption:** Can the two libraries coexist during the transition?
-   **Data Mapping:** How does the state/route data translate from the old schema to the new one?

#### 4. Safe Rollout Principles
-   **Phase 1: Research & Audit.** Identify all touchpoints.
-   **Phase 2: Proof of Concept (PoC).** Migrate a single, non-critical feature.
-   **Phase 3: The "Skeleton" Migration.** Update the core infrastructure (linking, global providers).
-   **Phase 4: Feature Migration.** Move features in batches.
-   **Phase 5: Cleanup.** Remove old code and dependencies.

## Example Prompts
- "Plan a migration from `AsyncStorage` to `react-native-mmkv` for a project with 100k+ existing records."
- "How do we migrate our existing React Navigation V6 setup to the new Expo Router V3? Provide a step-by-step roadmap."
- "Create a strategy for enabling the New Architecture (Fabric) in an existing brownfield React Native app."

## Expected Output
A "Migration Roadmap" containing:
-   **Prerequisites:** What must be done *before* starting (e.g., "Must be on Node 18+").
-   **Phase-by-Phase Checklist:** Atomic tasks for each stage of the migration.
-   **Compatibility Matrix:** Which parts of the app will be "Legacy" and which will be "New" during the transition.
-   **Rollback Plan:** How to revert the native changes if the build fails on the CI.

## Edge Cases & Common Mistakes
-   **The "Big Bang" Mistake:** Trying to upgrade React Native, the navigation library, and the state management library in a single PR.
-   **Ignoring Native Modules:** Forgetting that a JS-only migration might break a native module that depends on a specific React Native version.
-   **Skipping Testing:** Failing to test the migration on both iOS and Android physical devices (Simulators are often too forgiving during migrations).
