---
name: security-hardening
description: Implement industry-standard security measures to protect user data, secure API communication, and prevent app tampering.
---

# Security Hardening Expert

## Instructions

Securing a React Native app requires a multi-layered approach covering storage, networking, and the binary itself.

1.  **Secure Storage**: Never store sensitive data (tokens, PII) in `AsyncStorage`. Use `react-native-keychain` (iOS Keychain / Android Keystore) or `react-native-mmkv` with encryption enabled.
2.  **SSL Pinning**: Prevent Man-in-the-Middle (MITM) attacks by implementing SSL Pinning using `react-native-ssl-pinning` or native network interceptors (OkHttp/AFNetworking).
3.  **Environment Variables**: Use `react-native-config` or `react-native-dotenv` to manage API keys. Note that these are still discoverable; use a proxy or backend-for-frontend (BFF) for high-value secrets.
4.  **Code Obfuscation**: Enable ProGuard or R8 on Android to obfuscate Java/Kotlin code. For the JS bundle, consider using `Hermes` (which compiles to bytecode) to make reverse engineering more difficult.
5.  **Integrity Checks**: Use `react-native-device-info` or native modules to detect rooted (Android) or jailbroken (iOS) devices. Implement a "Security Policy" to block sensitive features on compromised devices.
6.  **Authentication Security**: Use OAuth2/OpenID Connect with PKCE for user authentication. Avoid storing passwords; use secure refresh token flows and biometric authentication (FaceID/TouchID).

## Example Prompts

- "Implement a secure token storage service using react-native-keychain with biometric fallback."
- "Configure SSL Pinning for all API requests to prevent traffic interception in a production app."
- "Set up a security utility that detects if the app is running in an emulator or on a rooted device."

## Expected Output

- Implementation of secure storage and networking protocols.
- Configuration for code obfuscation and binary protection.
- Best practices for managing secrets and sensitive user data.

## Edge Cases & Common Mistakes

- **Storing Secrets in Git**: Committing `.env` files or hardcoding API keys in the source code.
- **Over-Reliance on JS-level Checks**: Implementing security checks only in JavaScript, which can be easily bypassed. Always validate security on the backend.
- **Verbose Logging in Production**: Leaving `console.log` or native logs that expose sensitive data or API structures in production builds.
