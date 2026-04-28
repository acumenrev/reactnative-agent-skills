---
name: tool-integration-loop
description: Simulates and utilizes a comprehensive suite of development tools to verify, test, and build React Native applications during the development process.
---

# Tool Integration Loop Expert

## Instructions

The Tool Integration Loop replicates the real-world workflow of a senior React Native developer. It ensures that code is not just written, but also validated against the actual build systems and runtime environments of mobile platforms.

### 1. Build System Interaction
- **Metro Bundler Simulation:** Predict how changes will affect the Metro dependency graph and identify potential resolution errors before they occur.
- **Native Build Triggers:** Simulate or initiate native build commands (e.g., `./gradlew assembleDebug` or `xcodebuild`) to verify native modifications.
- **Config Management:** Correctly modify and verify `app.json`, `package.json`, `Info.plist`, and `AndroidManifest.xml` using appropriate tooling.

### 2. Automated Verification
- **Test Execution:** Integrate with `Jest` for unit/integration tests and `Detox` or `Maestro` for E2E verification.
- **Static Analysis:** Utilize `ESLint`, `Prettier`, and `TypeScript` (tsc) to ensure code quality and adherence to standards.
- **Security Scanning:** Simulate the use of tools like `npm audit` or specialized React Native security scanners to find vulnerable dependencies.

### 3. Debugging & Profiling
- **Performance Profiling:** Simulate the use of the React DevTools and Flipper to identify performance bottlenecks.
- **Memory Leak Detection:** Incorporate logic to check for common memory leak patterns in `useEffect` and event listeners.
- **Network Inspection:** Verify API interactions as if using a network inspector (e.g., Charles or Flipper's Network plugin).

### 4. Continuous Feedback Integration
- **Failure Analysis:** When a tool reports an error (e.g., a failing test or build), automatically parse the output and feed it back into the development loop for correction.
- **Standardization:** Ensure all tools are used with the specific configurations defined in the project's root directory.

## Example Prompts

- "Run a full verification loop on the new Authentication module: check types, run unit tests, and verify the iOS build compiles."
- "The CI pipeline is failing on the 'Lint' step. Integrate with ESLint to find and automatically fix all formatting and logic warnings."
- "Simulate a performance profile of the new scrollable header. Identify any frames being dropped and suggest a tool-verified fix."

## Expected Output

- Code that has been verified through multiple automated "checks."
- Detailed reports from simulated or actual tool executions.
- A "Green" state indicating that the build, tests, and linting all pass.

## Edge Cases & Common Mistakes

- **Tool Misconfiguration:** Running a tool with default settings instead of the project-specific configuration (e.g., ignoring `.eslintrc.js`).
- **Ignoring Tool Warnings:** Treating warnings from tools as optional, which often leads to subtle bugs in production environments.
- **Environment Discrepancy:** Assuming a tool's output in a local environment will be identical to the CI/CD environment without verifying the environment variables and versions.
