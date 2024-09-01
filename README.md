# GitHub Build Actions for Flutter Apps

## Introduction

This repository offers pre-configured GitHub Actions designed to simplify the process of building Flutter apps for both
Android and iOS platforms. These actions streamline the build process, ensuring consistent and efficient deployments.

## Workflows

- `workflows/android-build.yml` : This workflow is specifically tailored for building Android apps. It includes steps
  such as:
    - Checking out the repository
    - Setting up the Flutter environment
    - Getting Flutter dependencies
    - Generating Localization files
    - Generating boilerplate code using `build_runner`
    - Building the Android APK
    - Uploading the Android APK to a Firebase App Distribution

- `workflows/ios-build.yml` : This workflow is focused on building iOS apps. It includes steps like:
    - Checking out the repository
    - Setting up the Flutter environment
    - Getting Flutter dependencies
    - Generating Localization files
    - Generating boilerplate code using `build_runner`
    - Setup Apple Certificate, Provisional Profile & Export Options in environment
    - Building the iOS IPA
    - Uploading the IPA to a Firebase App Distribution

## Prerequisites

- A GitHub account
- A Flutter project repository on GitHub
- Basic understanding of GitHub Actions and YAML syntax

## Usage

### 1. Clone the Repository:

```shell
git clone https://github.com/pintusingh28/flutter-gh-actions.git
```

### 2. Configure GitHub Actions Secrets:

This section outlines the necessary GitHub Actions secrets that need to be configured for the Flutter build workflows to
function correctly. These secrets provide the required credentials and configurations for interacting with various
platforms and services.

- `APPLE_DEVELOPMENT_CERTIFICATE`:
    - **Description**: Base64-encoded content of your Apple Development Certificate file.
    - **Purpose**: Used for signing iOS apps during the build process.

- `APPLE_CERTIFICATE_PASSWORD`:
    - **Description**: Password associated with your Apple Development Certificate file.
    - **Purpose**: Required for unlocking the certificate during the signing process.

- `APPLE_DEVELOPMENT_PROFILE`:
    - **Description**: Base64-encoded content of your Apple Development Provisioning Profile file.
    - **Purpose**: Defines the entitlements and capabilities allowed for your iOS app.

- `EXPORT_OPTIONS_PLIST`:
    - **Description**: Content of the `ExportOptions.plist` file used for configuring the export process of your iOS
      app.
    - **Purpose**: Specifies options like the team ID, provisioning profile name, and other export settings.

- `MACOS_KEYCHAIN_PASSWORD`:
    - **Description**: Password for the keychain that will be used on the macOS runner.
    - **Purpose**: Required for accessing and managing certificates and keys during the build process.

- `FIREBASE_ANDROID_APP_ID`:
    - **Description**: Your Android app's ID on Firebase.
    - **Purpose**: Used for identifying your Android app in Firebase for various services like analytics, notifications,
      and more.

- `FIREBASE_IOS_APP_ID`:
    - **Description**: Your iOS app's ID on Firebase.
    - **Purpose**: Used for identifying your iOS app in Firebase for various services like analytics, notifications, and
      more.

- `FIREBASE_CREDENTIAL_FILE_CONTENT`:
    - **Description**: Content of your Firebase service account JSON file.
    - **Purpose**: Provides authentication credentials for accessing Firebase services on behalf of your project.

#### Configuration:

To configure these secrets in your GitHub repository:

- Go to your repository's settings.
- Navigate to the "Secrets" section.
- Click "Add a new secret."
- Enter the secret name and its corresponding value.
- Repeat for each required secret.

**Note**: Ensure that you securely store these secrets and avoid sharing them publicly.

### 3. Add Actions to Your Project:

- Navigate to your Flutter project's repository on GitHub.
- Go to the Actions tab.
- Click on New workflow.
- Paste the contents of the [`android-build.yml`](workflows/android-build.yml) or
  [`ios-build.yml`](workflows/ios-build.yml) files from this repository into the workflow editor.
- Customize the files as needed (e.g., change paths, environment variables).
- For `ios-build.yml` replace [YOUR_APP_NAME] placeholder with your app name.
- Click Start commit.

## Customization

You can customize the workflow files to suit your specific needs, such as:

- **Environment Variables:** Set environment variables for secrets like API keys, certificates, or other sensitive
  information.
- **Build Targets:** Specify different build targets for different environments (e.g., debug, release).
- **Additional Steps:** Add additional steps to the workflow, such as running linters, code analysis tools, or deploying
  the app to a distribution platform.

## Additional Notes

- **Configuration**: Ensure that you have the necessary credentials and configurations set up for your target
  platforms (e.g., Google Play Console API key, App Store Connect credentials).
- **Customization**: Feel free to modify the workflows to suit your specific needs, such as adding additional steps or
  integrating with other tools.
- **Dependencies**: Make sure you have the required dependencies installed on your GitHub Actions runner, including
  Flutter and the necessary build tools.
- **Testing**: Thoroughly test your workflows to ensure they are working as expected before relying on them for
  production builds.

## Contributing

Contributions are welcome! If you have improvements or additional features to suggest, please feel free to open an issue
or submit a pull request.
