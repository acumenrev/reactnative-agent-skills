---
name: explainer-mode
description: Clearly articulates the technical reasoning, architectural decisions, and platform-specific nuances behind React Native implementations.
---

# Explainer Mode Expert

## Instructions

Explainer Mode is used to bridge the gap between complex technical implementation and developer understanding. It provides the "Why" behind the "How," making the codebase more accessible and ensuring that decisions are well-documented and defensible.

### 1. Decision Articulation
- **Architectural Justification:** Explain why a specific library or pattern was chosen (e.g., "Choosing React-Query for data fetching to simplify cache management and loading states").
- **Performance Reasoning:** Detail the performance implications of a specific change (e.g., "Using `FlatList` with `getItemLayout` to ensure O(1) scroll time for our large list").

### 2. Platform Nuance Clarification
- **Bridge vs. JSI:** Explain how specific native interactions work (e.g., "This module uses JSI for synchronous communication with the native layer, avoiding the overhead of the asynchronous bridge").
- **OS Discrepancies:** Clarify why certain code paths are needed for one platform but not the other (e.g., "Android requires specific permission handling in the Manifest that is handled automatically via plist on iOS").

### 3. Step-by-Step Walkthroughs
- **Workflow Explanation:** Break down complex execution paths into logical steps (e.g., explaining the 5 steps involved in setting up a new TurboModule).
- **Bug Root Cause Analysis:** Clearly explain why a bug occurred and how the proposed fix addresses the fundamental issue, not just the symptom.

### 4. Adaptive Depth
- **Context-Aware Explanations:** Adjust the level of detail based on the complexity of the task and the developer's expressed needs (e.g., a brief summary for a trivial fix vs. a deep dive for a major refactor).
- **Visual Description:** When describing UI or layout changes, use clear language to "paint a picture" of the structural changes in the component tree.

## Example Prompts

- "Explain why we are using a custom hook for this animation instead of the standard `useNativeDriver` within the component."
- "Provide a step-by-step explanation of how the new Deep Linking logic identifies and routes specific URLs within the app."
- "What are the technical trade-offs of the 'Optimistic Updates' pattern we implemented in the comments section?"

## Expected Output

- Clear, concise, and technically accurate explanations.
- Well-structured documentation that can be used in PR descriptions or project wikis.
- Increased developer confidence in the codebase through transparent decision-making.

## Edge Cases & Common Mistakes

- **Jargon Overload:** Using overly complex terminology without defining it, making the explanation harder to follow for junior developers.
- **Vague Reasoning:** Providing "because it's best practice" as a reason without explaining *why* it is best practice in the specific context of the project.
- **Inaccurate Claims:** Making technical claims about React Native's internal workings that are outdated or slightly incorrect (e.g., claiming the Bridge is used when a project has migrated to the New Architecture).
