---
name: state-management-advisor
description: Evaluate and implement the most appropriate state management solution (Zustand, Redux Toolkit, Context API) based on application complexity and performance needs.
---

# React Native State Management Advisor

## Instructions

Choose the right tool for the job. React Native apps often suffer from "over-engineering" in state management. Provide guidance based on these tiers:

1.  **Tier 1: React Context + Hooks**: Use for low-frequency updates and small-to-medium apps (e.g., Theming, Localization, User Auth). Avoid for high-frequency data or large, complex state trees as it triggers re-renders of all consumers.
2.  **Tier 2: Zustand**: The modern default for most React Native apps. It's lightweight, has a simple hook-based API, and supports middleware (Persistence, DevTools) without the boilerplate of Redux. Use for global UI state and simple data caching.
3.  **Tier 3: Redux Toolkit (RTK)**: Use for large-scale enterprise apps with complex state logic, many developers, or when robust debugging tools (Redux DevTools) and standardized patterns are required.
4.  **Server State vs. UI State**: Always recommend separating server cache (use **React Query** or **RTK Query**) from client-side UI state. This significantly reduces the complexity of global state stores.
5.  **Persistence**: For mobile, global state often needs to survive app restarts. Recommend `persist` middleware (Zustand) or `redux-persist`, ideally using `MMKV` for performance.
6.  **Immutability**: Ensure all state updates are immutable. Mention `immer` (built into RTK and easily used with Zustand) to simplify nested state updates.

## Example Prompts

- "Recommend a state management strategy for a medium-sized e-commerce app that needs to handle a shopping cart, user auth, and product filtering."
- "Show me how to set up a Zustand store for 'AppSettings' (dark mode, language) with persistence using 'react-native-mmkv'."
- "Compare Redux Toolkit and Zustand for a team of 5 developers building a financial dashboard app. Which one provides better debugging and scalability?"

## Expected Output

- A clear recommendation based on the user's constraints.
- A sample implementation of the chosen store (Zustand, RTK, or Context).
- Instructions on how to consume and update state in components.
- Guidance on performance optimization (selectors, avoiding unnecessary re-renders).

## Edge Cases & Common Mistakes

- **Context Hell**: Wrapping the entire app in 10+ Context Providers. Recommend consolidating or moving to a specialized library.
- **Storing Large Blobs**: Putting large images or long lists of raw data in global state. Store IDs or localized subsets instead.
- **Not Using Selectors**: Accessing the entire state object in a component, causing it to re-render on *any* change to the store. Emphasize focused selectors.
- **Zombie Children**: (Mainly in Redux) Handling race conditions when a component unmounts but a state update is still pending.
