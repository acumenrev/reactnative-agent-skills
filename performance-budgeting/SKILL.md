---
name: performance-budgeting
description: Expert guidance on setting, monitoring, and enforcing performance budgets for React Native applications to ensure consistent UX.
---

# React Native Performance Budgeting

## Instructions

As a Performance Budgeting expert, you help teams set measurable goals and implement systems to stay within those limits.

1.  **Define Key Metrics**: Establish budgets for critical React Native metrics: TTI (Time to Interactive), FPS (Frames Per Second) during animations/scrolling, Bundle Size (JS), and App Startup Time.
2.  **Context-Specific Budgets**: Adjust budgets based on target devices (e.g., low-end Android devices need stricter budgets than the latest iPhone).
3.  **Bundle Size Management**: Set limits for the main JS bundle and individual feature chunks. Recommend tools like `react-native-bundle-visualizer`.
4.  **Runtime Budgets**: Establish limits for JS thread usage. For example, no single JS task should block the thread for more than 16ms to maintain 60 FPS.
5.  **Monitoring and Enforcement**: Integrate performance checks into CI/CD. Use tools like `Flashlight` (for Android) or custom profiling scripts to fail builds that exceed budgets.
6.  **Optimization Strategies**: Provide a toolkit of optimizations (e.g., Image compression, Lazy loading, Code splitting) to help teams stay under budget.

## Example Prompts

- "Help us set a performance budget for our new e-commerce app targeting mid-range Android devices in emerging markets."
- "Our JS bundle has grown to 5MB. How can we set a budget to prevent further growth and what are the first steps to reduce it?"
- "We are seeing frame drops on the home screen. Set a runtime budget for the JS thread and suggest how to monitor it in production."

## Expected Output

- **Performance Budget Table**: Clearly defined limits for Bundle Size, Startup Time, and Frame Rates.
- **Monitoring Plan**: Recommended tools and integration steps for the CI/CD pipeline.
- **Remediation Guide**: A checklist of actions to take when a budget is exceeded.
- **Baseline Report**: Comparison of current performance against the newly set budgets.

## Edge Cases & Common Mistakes

- **Unrealistic Targets**: Setting budgets that are impossible to achieve given the app's complexity or the team's resources.
- **Ignoring "Tail" Performance**: Focusing only on the average (p50) performance and ignoring the worst-case (p95/p99) scenarios that affect the most frustrated users.
- **One-and-Done Approach**: Setting a budget at the start of the project and never revisiting it as the app evolves.
