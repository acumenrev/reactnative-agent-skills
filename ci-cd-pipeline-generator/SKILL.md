---
name: ci-cd-pipeline-generator
description: Automate the build, test, and deployment lifecycle of React Native apps using GitHub Actions and Fastlane.
---

# CI/CD Pipeline Generator

## Instructions

A robust CI/CD pipeline for React Native must handle both the JavaScript environment and the native iOS/Android build systems.

1.  **Pipeline Tooling**: Use GitHub Actions or GitLab CI as the orchestrator. Use `Fastlane` to handle the complexity of code signing, building, and uploading to stores.
2.  **Automated Testing**: Run unit tests (Jest) and linting (ESLint/Prettier) on every Pull Request. Implement E2E tests (Detox or Appium) for critical user flows.
3.  **Caching Strategy**: Cache `node_modules`, CocoaPods (`ios/Pods`), and Gradle files to drastically reduce build times.
4.  **Code Signing**:
    - **iOS**: Use `fastlane match` for centralized, encrypted certificate and profile management.
    - **Android**: Securely store your upload keystore in GitHub Secrets and inject it during the build process.
5.  **Environment Management**: Use secrets and environment variables to inject API keys and configuration during the build (e.g., `.env.production`).
6.  **Automated Releases**: Configure the pipeline to automatically deploy to TestFlight (iOS) and Google Play Console Internal Sharing (Android) when code is merged into the `develop` or `main` branch.

## Example Prompts

- "Create a GitHub Actions workflow that runs Jest tests and builds an Android APK on every push."
- "Set up a Fastlane 'lane' for iOS that handles version incrementing, building, and uploading to TestFlight."
- "Implement a full CI/CD pipeline that builds both iOS and Android apps, handles code signing, and notifies Slack on success."

## Expected Output

- GitHub Actions `.yml` configuration files.
- `Fastfile` and `Appfile` configurations for Fastlane.
- Scripts for handling versioning and environment injection.

## Edge Cases & Common Mistakes

- **Exposing Secrets**: Printing environment variables or secrets in the CI logs.
- **Flaky E2E Tests**: Relying on brittle Detox tests that fail randomly and block the pipeline.
- **Ignoring Native Versioning**: Updating the version in `package.json` but forgetting to sync it with `Info.plist` and `build.gradle`.
