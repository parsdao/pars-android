# Lux Messenger Android

> Private messaging on the Lux Network - A fork of [Session Android](https://github.com/session-foundation/session-android)

## Overview

Lux Messenger Android is a fork of Session Android, intended to connect to the Lux Network's SessionVM instead of the Oxen network. This app provides end-to-end encrypted messaging with post-quantum cryptographic protection.

## Current Status

**Integration Status: In Progress**

The Android app currently uses `libsession-util` for networking, which has hardcoded network endpoints. Full integration with the Lux SessionVM requires modifications to the underlying C++ library.

### What Works
- Building and running the app
- Core messaging functionality (against Session mainnet)

### What Needs Work
- Network configuration to connect to Lux SessionVM
- libsession-util modifications for custom network support
- Branding updates (Lux Messenger)

## Building

### Prerequisites

- Android Studio Arctic Fox or later
- Android SDK 21+
- JDK 11+

### Build Steps

1. Clone the repository:
```bash
git clone https://github.com/lux-tel/session-android
cd session-android
```

2. Open in Android Studio

3. Sync Gradle dependencies

4. Build and run

### Command Line Build

```bash
./gradlew assembleDebug
```

## Architecture

```
Session Android
├── app/                    # Main application module
├── libsession-util/        # JNI bindings to C++ library
├── libsignal/              # Signal protocol implementation
└── core-utils/             # Shared utilities

Network Layer
└── libsession-util (C++ via JNI)
    └── Hardcoded network endpoints
```

## Configuration for Lux Network

### Current Limitation

Similar to iOS, Android uses `libsession-util` for networking with hardcoded endpoints.

### Planned Approach

To enable Lux network connectivity:

1. **Modify libsession-util** (`lux-tel/libsession-util`)
   - Add environment-based configuration
   - Support custom seed node URLs
   - Support custom file server URLs

2. **Update Android JNI bindings**
   - Pass Lux network configuration to LibSession
   - Update UI branding

## Related Repositories

| Repository | Description |
|------------|-------------|
| [luxfi/session](https://github.com/luxfi/session) | Go SessionVM + API layer |
| [luxcpp/session](https://github.com/luxcpp/session) | C++ storage server |
| [lux-tel/libsession-util](https://github.com/lux-tel/libsession-util) | Native library (needs modification) |
| [lux-tel/session-desktop](https://github.com/lux-tel/session-desktop) | Desktop client (configured) |
| [lux-tel/session-ios](https://github.com/lux-tel/session-ios) | iOS client |

## Development

### Key Directories

| Directory | Description |
|-----------|-------------|
| `app/src/main/java/org/thoughtcrime/securesms/` | Main application code |
| `libsession-util/` | JNI bindings to C++ library |
| `libsession/` | Session-specific crypto/network |

### Building Debug APK

```bash
./gradlew assemblePlayDebug
```

### Running Tests

```bash
./gradlew test
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

GPL-3.0 - Same as upstream Session Android

## Upstream

This project is a fork of [Session Android](https://github.com/session-foundation/session-android) by the Session Technology Foundation.
