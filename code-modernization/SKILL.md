---
name: code-modernization
description: Expert guidance on refactoring legacy React Native codebases into modern, performant, and maintainable patterns.
---

# React Native Code Modernization

## Instructions

As a Code Modernization expert, you guide developers in upgrading legacy codebases to the latest React Native standards.

1.  **Migration to Functional Components**: Systematically refactor Class Components to Functional Components using Hooks (`useState`, `useEffect`, `useMemo`, `useCallback`).
2.  **TypeScript Adoption**: Transition from JS/Flow to TypeScript. Focus on strong typing for component props, navigation parameters, and API responses.
3.  **Modern State Management**: Guide the move from legacy Redux (boilerplate-heavy) to Redux Toolkit, Zustand, or specialized libraries like TanStack Query for server state.
4.  **New Architecture Readiness**: Identify and refactor patterns that are incompatible with the New Architecture (Fabric/TurboModules), such as synchronous calls to native modules or deprecated `findNodeHandle` usage.
5.  **Performance Overhaul**: Replace outdated list components (e.g., `ListView`) with `FlashList` or optimized `FlatList`. Optimize re-renders using `React.memo` and stable references.
6.  **Navigation Modernization**: Update projects using deprecated navigation libraries or older versions of React Navigation to the latest major version, ensuring type-safe navigation.

## Example Prompts

- "Refactor this legacy Class Component into a Functional Component using Hooks and TypeScript."
- "We are on React Native 0.63. What are the most important steps to modernize our codebase for 0.74+ and the New Architecture?"
- "Convert this legacy Redux store implementation using `connect` and action constants into a modern Redux Toolkit slice with `createAsyncThunk`."

## Expected Output

- **Before vs. After Code**: Clear comparison showing the legacy pattern vs. the modernized implementation.
- **Refactoring Rationale**: Brief explanation of *why* the new pattern is better (e.g., "Reduced boilerplate," "Better type safety," "Improved performance").
- **Migration Plan**: Step-by-step instructions for large-scale changes to minimize regressions.
- **Unit Test Updates**: Guidance on how to adapt existing tests to the modernized code.

## Edge Cases & Common Mistakes

- **Lifecycle Mismanagement**: Incorrectly mapping `componentDidUpdate` or `componentWillUnmount` to `useEffect` hooks, leading to memory leaks or infinite loops.
- **Over-refactoring**: Changing too much at once without a solid test suite, making it difficult to debug regressions.
- **Ignoring Native Dependencies**: Modernizing the JS layer but forgetting that older native dependencies might break on newer React Native versions or architecture.
