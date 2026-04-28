---
name: team-guideline-generator
description: Generates standardized coding guidelines and best practices tailored for React Native teams to ensure codebase consistency and high quality.
---

# React Native Team Guideline Generator

## Instructions

Your task is to create clear, actionable, and enforceable technical guidelines for a React Native development team. Good guidelines reduce PR review time, minimize "bike-shedding," and ensure that the app remains performant as it grows.

### Key Guideline Areas

#### 1. Component & Hook Standards
-   **Structure:** Mandatory functional components. Standardized prop naming (e.g., `on[Action]` for callbacks).
-   **Hooks:** Rules for when to extract logic into custom hooks (`useFeature`) to keep UI components lean.
-   **Performance:** Mandatory `useCallback` or `useMemo` for props passed to complex child components (e.g., `FlashList` items).

#### 2. Styling & Layout
-   **Theming:** Centralized theme object (tokens for colors, spacing, typography).
-   **Layout:** Preference for `Flexbox`. Guidelines on when to use absolute positioning vs. margins/padding.
-   **Responsiveness:** Use of `Dimensions` vs. `useWindowDimensions` vs. percentage-based layouts.

#### 3. Platform-Specific Code
-   **Strategy:** When to use `Platform.select` vs. `.ios.js`/`.android.js` files.
-   **Consistency:** Ensuring that if a feature exists on one platform, a graceful fallback or equivalent exists on the other.

#### 4. Testing & Quality Assurance
-   **Unit Tests:** Coverage requirements for utility functions and business logic hooks (Jest).
-   **Integration Tests:** Core user flows (React Native Testing Library).
-   **E2E Tests:** Critical paths (Detox or Maestro).

#### 5. Native Code Hygiene
-   **Linking:** Rules for adding new native dependencies (e.g., "Must check for Config Plugin before manual linking").
-   **Versions:** Standardized versions for Node, Ruby (CocoaPods), and Java/Gradle.

## Example Prompts
- "Create a `STYLEGUIDE.md` for a React Native team that prioritizes accessibility and performance."
- "Generate a pull request template for our mobile team that requires links to screenshots/videos and a performance impact summary."
- "Define a 'Feature-First' folder structure for a large-scale React Native application."

## Expected Output
A comprehensive "Team Playbook" including:
-   **Core Philosophy:** 3-5 guiding principles (e.g., "Performance is a feature").
-   **The Rules:** Categorized sections with code examples ("Bad" vs. "Good").
-   **PR Checklist:** 5-10 items that every developer must verify before submitting code.
-   **Tooling Recommendations:** ESLint/Prettier configs and VS Code extensions.

## Edge Cases & Common Mistakes
-   **The "Web Developer" Bias:** Creating rules that work for React on the Web but ignore the constraints of a mobile bridge or native threads.
-   **Over-Documentation:** Creating a 50-page document that no one reads. Keep it concise and searchable.
-   **No Enforcement:** Recommending guidelines without suggesting how to automate them (e.g., custom ESLint rules).
