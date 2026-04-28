# React Native Agent Skills — Optimized for Gemini CLI

[![React Native](https://img.shields.io/badge/React%20Native-0.7x-61DAFB?logo=react&logoColor=white)](https://reactnative.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Gemini CLI](https://img.shields.io/badge/Gemini%20CLI-compatible-blue.svg)](https://github.com/google/gemini-cli)

A collection of 48 agent skills for modern React Native development, optimized specifically for **Gemini CLI**. These skills cover everything from basic component generation to complex architectural orchestration and autonomous workflows.

## Install

To use these skills with Gemini CLI, you can install them from this local directory.

### Install All Skills

Install every skill in the collection to your user-level skill store:

```bash
for d in */; do
  if [ -f "$d/SKILL.md" ]; then
    gemini skills install "$d" --scope user
  fi
done
```

### Install Specific Skills

Install individual skills as needed:

```bash
gemini skills install ./component-generator --scope workspace
gemini skills install ./performance-optimizer --scope user
```

### Reload Skills

After installation, reload your session to enable the new skills:

```
/skills reload
```

## Global Context

This repository includes a `GEMINI.md` file. When you work with Gemini CLI in this directory, the agent automatically reads this file to understand the project's architecture, communication style, and React Native-specific documentation rules.

## Skills Catalog

### UI & UX Generation
- **component-generator**: Reusable, type-safe functional components with StyleSheet separation.
- **screen-generator**: Feature-based screen scaffolding and navigation integration.
- **animation-generator**: High-performance animations using Reanimated 3.
- **gesture-handler**: Complex touch interactions with RNGH 2.
- **design-system-generator**: Scalable, type-safe design systems and tokens.
- **accessibility-optimizer**: WCAG-compliant strategies for inclusive design.

### Foundation & Architecture
- **navigation-generator**: Type-safe navigation with React Navigation.
- **api-layer-generator**: Scalable API layers with Axios and strict typing.
- **state-management-advisor**: Guidance on Zustand, Redux Toolkit, and Context API.
- **project-structure-advisor**: Feature-first architecture and absolute imports.
- **storage-manager**: High-performance storage with MMKV and secure storage.
- **offline-first-architecture**: Strategies for local-first storage and synchronization.
- **monorepo-architect**: Scaling with Nx/Turborepo and managing native code.

### Performance & Security
- **performance-optimizer**: Render optimization, FlatList tuning, and bridge traffic reduction.
- **performance-budgeting**: Setting and enforcing measurable metrics like TTI and FPS.
- **security-hardening**: Multi-layered security for storage, networking, and obfuscation.
- **codebase-auditor**: Holistic health checks of JS and Native codebases.

### Automation & Workflow
- **autonomous-workflow-orchestrator**: Chaining research, planning, and implementation.
- **goal-decomposer**: Breaking high-level requirements into atomic sub-tasks.
- **skill-router**: Dispatching requests to relevant specialized skills.
- **execution-engine**: Sequential task orchestration and build management.
- **auto-fix-loop**: Iterative diagnostics and build failure resolution.
- **tool-integration-loop**: Build system interaction and automated verification.

### Strategic Planning
- **decision-engine**: Framework for high-stakes architectural choices (e.g., Expo vs. Bare).
- **tradeoff-analyzer**: Objective comparisons of architectural choices.
- **library-selection-engine**: Evaluating third-party libraries for health and compatibility.
- **scalability-planner**: Long-term roadmaps for feature and team growth.
- **migration-planner**: Strategies for version upgrades and architectural shifts.
- **feature-complexity-estimator**: Effort prediction based on mobile-specific drivers.

### Quality & Mentorship
- **code-review-expert**: Rigorous feedback patterns for performance and security.
- **architecture-critic**: Evaluation of modularity and separation of concerns.
- **antipattern-detector**: Identifying and fixing performance-killing practices.
- **team-guideline-generator**: Standardizing coding practices and workflows.
- **explainer-mode**: Decision articulation and platform nuance clarification.
- **self-reflection**: Performance audits and architectural critiques.

## License

MIT License.
