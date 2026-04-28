---
name: design-system-generator
description: Architect scalable, themeable, and type-safe design systems using design tokens and consistent component patterns.
---

# Design System Generator

## Instructions

A professional React Native design system should be built on Design Tokens and a robust theme provider.

1.  **Centralize Tokens**: Define all core values (colors, spacing, typography, shadows, border radii) in a single source of truth (e.g., `tokens.ts`).
2.  **TypeScript Theming**: Create a strict `Theme` interface. If using a library like `Restyle` (Shopify) or `Unistyles`, ensure the theme object is fully typed to provide autocomplete in components.
3.  **Component Scaffolding**: Build "atomic" components first (Button, Text, Box/Stack, Input). Use these as the building blocks for more complex molecules and organisms.
4.  **Dark Mode Support**: Structure the theme to support multiple color palettes (light/dark). Use a Context Provider or a reactive styling library to switch themes without re-mounting the app.
5.  **Responsive Patterns**: Use percentage-based widths, AspectRatios, or a scaling utility (like `mvs` for vertical scaling) to ensure the UI looks consistent across small phones and large tablets.
6.  **Standardized Props**: Use consistent naming conventions for style props (e.g., `variant`, `size`, `color`). Avoid passing raw style objects into base components; prefer predefined variants.

## Example Prompts

- "Define a comprehensive design token file with primary colors, a 4px-grid spacing system, and typography scales."
- "Create a type-safe ThemeProvider that supports switching between light and dark modes in a React Native app."
- "Build a polymorphic 'Button' component that supports 'primary', 'secondary', and 'ghost' variants based on design tokens."

## Expected Output

- A structured directory of design tokens and theme definitions.
- A collection of base components (Box, Text, Button) following the design system rules.
- Type definitions that enforce the use of theme values.

## Edge Cases & Common Mistakes

- **Hardcoding Values**: Never use magic numbers for colors or margins inside components. Everything must come from the theme.
- **Ignoring Platform Defaults**: Ensure typography scales account for system font differences (San Francisco on iOS, Roboto on Android).
- **Over-Complexity**: Don't build a massive system from day one. Start with core atoms and expand as the project grows to avoid unnecessary abstraction debt.
