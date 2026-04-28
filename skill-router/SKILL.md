---
name: skill-router
description: Intelligently routes incoming React Native development requests to the most appropriate specialized agent skills based on task requirements.
---

# React Native Skill Router

## Instructions

Your role is to act as the "Dispatcher." You analyze a user's request and determine which specialized React Native skills are needed to fulfill it. Efficient routing prevents wasted turns and ensures that the most relevant expertise is applied to each part of the problem.

### Routing Logic

#### 1. Analyze the Request
-   Is it about UI/UX? -> Route to `component-generator` or `animation-generator`.
-   Is it about Data/State? -> Route to `api-layer-generator` or `state-management-advisor`.
-   Is it about "Under the hood" issues? -> Route to `performance-optimizer` or `debugging-assistant`.
-   Is it about the Native layer? -> Route to `native-module-expert` (if available) or `architecture-critic`.
-   Is it a Meta-task? -> Route to `goal-decomposer` or `codebase-auditor`.

#### 2. Multi-Skill Chaining
-   Requests often require multiple skills. For example: "Add a login screen with Biometrics."
    -   `auth-flow-generator` (Logic/Flow)
    -   `screen-generator` (UI)
    -   `security-hardening` (Secure storage for tokens)

#### 3. Selection Strategy
-   Prioritize **Specific** over **General**. If a task is about a bug, use `debugging-assistant`, not just `codebase-auditor`.
-   Minimize the "Skill Set." Only route to skills that are strictly necessary to avoid context bloat.

## Example Prompts
- "We need to optimize the startup time of our Android app. It's taking 5 seconds to get to the first screen. Which skills are needed?"
- "I want to add an 'Offline Mode' to our existing GraphQL-based app. Plan the skill routing."
- "The design team sent a Figma link for a new 'Settings' screen. Route this request."

## Expected Output
A "Routing Table":
-   **Primary Skill:** The lead skill for the task.
-   **Secondary Skills:** Supporting skills for specific sub-tasks.
-   **Rationale:** A brief explanation of why these skills were chosen.
-   **Activation Order:** The sequence in which these skills should be utilized.

## Edge Cases & Common Mistakes
-   **Over-Routing:** Activating 10 skills for a task that only needs 2.
-   **Missing the 'Native' Component:** Routing a Bluetooth task only to `api-layer-generator` without considering that it needs a skill that understands native modules.
-   **Vague Routing:** Routing to a generic "implementation" skill when the user specifically asked for an "architecture review."
