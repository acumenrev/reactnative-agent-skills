---
name: context-memory-manager
description: Efficiently maintains and utilizes project context, architectural decisions, and state history to ensure consistent React Native development across multiple turns.
---

# Context Memory Manager Expert

## Instructions

The Context Memory Manager is responsible for ensuring that the agent "remembers" the critical details of a React Native project. This avoids repetitive questions, prevents architectural contradictions, and ensures that new code seamlessly integrates with previous decisions.

### 1. Architectural State Tracking
- **Tech Stack Snapshot:** Maintain a record of the core stack (e.g., Expo vs. Bare, React Navigation version, State Management library, Styling solution).
- **Global Constraints:** Store persistent constraints like "Target iOS version >= 13.0" or "Always use Functional Components and Hooks."
- **Folder Structure:** Remember the established project structure (e.g., where hooks, components, and services live) to ensure new files are placed correctly.

### 2. Decision Logging
- **The "Why" Behind the "What":** Record the reasoning for specific choices (e.g., "Using Redux-Saga instead of Thunk because of complex side-effect requirements").
- **Avoid Regressions:** Maintain a list of "lessons learned" during the current session (e.g., "The latest version of library X crashes on Android, use version Y instead").

### 3. Contextual Retrieval
- **Relevant Snippet Loading:** Before starting a new task, retrieve relevant context from memory (e.g., existing API client configuration or navigation theme).
- **Contradiction Detection:** Proactively check if a new request or proposed fix contradicts a previous decision recorded in memory.

### 4. Memory Optimization
- **Pruning:** Remove outdated or irrelevant information from the immediate context to keep token usage efficient while retaining long-term project knowledge.
- **Hierarchical Memory:** Organize information by scope (Project-level, Module-level, Feature-level).

## Example Prompts

- "Initialize project memory by scanning the existing codebase. Identify the state management pattern, navigation setup, and styling conventions."
- "Before we implement the new Payment module, recall our previous decisions regarding secure storage and API error handling."
- "Verify if our proposed change to the theme provider contradicts the 'Dark Mode' implementation we finished in the last session."

## Expected Output

- A consistent and accurate "Source of Truth" for the project's current state.
- Faster execution times as common project details are retrieved from memory rather than re-discovered.
- Reduced errors caused by inconsistent architectural patterns or redundant implementations.

## Edge Cases & Common Mistakes

- **Memory Drift:** Failing to update the context memory when a manual or external change is made to the project, leading to "stale" information.
- **Over-Retention:** Storing too much low-level detail (e.g., every variable name) which clutters the context and obscures high-level architectural decisions.
- **Contradictory Instructions:** Carrying over memory from a *different* project into the current session, leading to inappropriate suggestions (e.g., suggesting Tailwind for a project using Styled Components).
