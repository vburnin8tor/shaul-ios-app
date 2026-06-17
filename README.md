# ShaulIOSApp

A minimal iOS app built with SwiftUI.

## Requirements

- Xcode 16.0+
- iOS 16.0+ deployment target
- macOS 15 (Sequoia) for CI builds

## Building

### In Xcode

1. Open `ShaulIOSApp.xcodeproj`
2. Select a simulator or device target
3. Press Cmd+R to build and run

### From Command Line

```bash
xcodebuild -project ShaulIOSApp.xcodeproj \
  -scheme ShaulIOSApp \
  -destination 'generic/platform=iOS' \
  -configuration Debug \
  build
```

### CI Build (GitHub Actions)

The project includes a GitHub Actions workflow that builds on every push to `main`.
See `.github/workflows/build.yml`.

## Project Structure

```
ShaulIOSApp/
├── ShaulIOSApp/
│   ├── ShaulIOSAppApp.swift    # App entry point
│   ├── ContentView.swift        # Main view
│   └── Info.plist               # App configuration
├── ShaulIOSApp.xcodeproj/       # Xcode project
├── .github/workflows/build.yml  # CI workflow
├── .gitignore
└── README.md
```

## Bundle ID

`com.shaul.shauliosapp`

## Code Signing

For local development, set your Development Team in Xcode:
Project → Target → Signing & Capabilities → Team

For CI signing, configure the following GitHub Secrets:
- `APPLE_CERTIFICATE` — base64-encoded .p12 signing certificate
- `APPLE_CERTIFICATE_PASSWORD` — password for the .p12
- `APPLE_PROVISIONING_PROFILE` — base64-encoded .mobileprovision
- `APPLE_TEAM_ID` — Apple Developer Team ID

## Sideloading

Once built, the `.ipa` can be sideloaded using:
- [Sideloadly](https://sideloadly.io/) (recommended)
- [AltStore](https://altstore.io/)
- Xcode direct install

Free Apple Developer accounts require 7-day re-signing.
