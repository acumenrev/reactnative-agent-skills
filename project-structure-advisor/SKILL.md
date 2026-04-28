---
name: project-structure-advisor
description: Design and implement scalable, feature-first project architectures that minimize coupling and maximize discoverability.
---

# React Native Project Structure Advisor

## Instructions

A well-organized project reduces cognitive load and scales with the team. Avoid the "folder-by-type" (e.g., `components/`, `screens/`, `hooks/`) trap for anything beyond a tiny prototype. Recommend a **Feature-Based Architecture**:

1.  **Top-Level Structure**:
    - `src/api/`: Global API client and shared services.
    - `src/components/`: Truly global, reusable UI atoms (Buttons, Inputs).
    - `src/features/`: The core of the app. Each feature folder (e.g., `auth`, `profile`, `feed`) contains its own `components/`, `hooks/`, `screens/`, `services/`, and `store/`.
    - `src/navigation/`: Navigator configurations and route types.
    - `src/theme/`: Design system tokens (colors, typography, spacing).
    - `src/utils/`: Pure helper functions.
2.  **Encapsulation**: Features should be as self-contained as possible. If a component is used only in the 'Auth' flow, it belongs in `src/features/auth/components/`.
3.  **Public API (Index Files)**: Use `index.ts` files in feature folders to export only what is needed by other parts of the app, acting as a "Public API" for that feature.
4.  **Absolute Imports**: Configure `tsconfig.json` or `babel-plugin-module-resolver` to use absolute paths (e.g., `@components/Button` instead of `../../../components/Button`).
5.  **Platform Specifics**: Keep `.ios.tsx` and `.android.tsx` files close to their common counterparts to make platform differences easy to manage.
6.  **Tests Placement**: Place unit tests (`__tests__`) inside the folder of the code they are testing, rather than a separate top-level `tests/` directory.

## Example Prompts

- "Propose a folder structure for a large social media app with features like 'Post Feed', 'Messaging', 'User Profiles', and 'Settings'."
- "How should I organize my 'Auth' feature? I have 3 screens, 2 custom hooks for API calls, and some local components like an 'AuthHeader'."
- "Refactor a flat 'src/screens' and 'src/components' structure into a modular, feature-based architecture."

## Expected Output

- A visual tree representation of the proposed folder structure.
- Explanations for why specific files are placed where they are.
- A guide on how to handle cross-feature dependencies (e.g., using a 'Shared' or 'Common' feature).
- Example `tsconfig.json` paths for absolute imports.

## Edge Cases & Common Mistakes

- **Circular Dependencies**: Features importing from each other in a loop. Solve by moving shared logic to a `common` or `shared` feature/layer.
- **Giant 'Shared' Folder**: Putting everything in `shared` because it's easier, eventually recreating the flat structure problem.
- **Deep Nesting**: Going more than 3-4 levels deep, making it hard to find files. Keep the hierarchy relatively flat within features.
- **Ignoring Native Folders**: Forgetting to manage `ios/` and `android/` directories properly in Git or during library installations.
