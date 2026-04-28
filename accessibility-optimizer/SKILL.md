---
name: accessibility-optimizer
description: Ensure your React Native application is inclusive and usable for everyone by implementing WCAG-compliant accessibility features.
---

# Accessibility Optimizer

## Instructions

Accessibility is a core requirement, not an optional feature. Follow these React Native best practices:

1.  **Use Descriptive Labels**: Provide `accessibilityLabel` for all interactive elements (buttons, links, icons). Ensure the label describes the *action* or *content*, not just the component name.
2.  **Assign Proper Roles**: Use `accessibilityRole` (e.g., 'button', 'header', 'link', 'none') to help screen readers understand the purpose of a component.
3.  **Manage Focus**: Use `accessibilityState` to communicate states like `selected`, `disabled`, or `busy`. For complex flows, use `findNodeHandle` or accessibility refs to move focus programmatically after an action (e.g., opening a modal).
4.  **Group Elements**: Use `importantForAccessibility="yes"` (Android) and `accessible={true}` (iOS) to group related children into a single focusable element, preventing the screen reader from reading disjointed text fragments.
5.  **Dynamic Type Support**: Allow text to scale according to system settings. Use `allowFontScaling={true}` (default) and avoid hardcoding `height` on containers; use `minHeight` or padding instead.
6.  **Color Contrast**: Ensure a contrast ratio of at least 4.5:1 for normal text and 3:1 for large text. Use tools to verify your theme's accessibility.

## Example Prompts

- "Audit this custom 'Tab' component for accessibility and add the necessary roles and states."
- "Implement a screen reader-friendly error message that is automatically announced when a form validation fails."
- "Optimize a complex data table to be navigable using VoiceOver and TalkBack, grouping related cell information."

## Expected Output

- Components updated with `accessibilityLabel`, `accessibilityRole`, and `accessibilityState`.
- Implementation of `AccessibilityInfo` for custom announcements or focus management.
- Recommendations for color contrast and font scaling improvements.

## Edge Cases & Common Mistakes

- **Redundant Labels**: Avoid including the role in the label (e.g., "Submit Button"). The screen reader will already announce it as a button.
- **Hidden Interaction Targets**: Ensure icon-only buttons have a descriptive label (e.g., a "X" icon should have `accessibilityLabel="Close"`).
- **Ignoring High Contrast Mode**: Test your app with inverted colors and high contrast settings to ensure visibility.
