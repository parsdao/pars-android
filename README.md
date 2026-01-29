# Pars Messenger Android

[![License: GPL-3.0](https://img.shields.io/badge/License-GPL%203.0-blue.svg)](LICENSE)

> Private messaging for the Pars Network - Built on [pars.network](https://pars.network)

## Overview

Pars Messenger Android is a privacy-focused messaging app for the Pars Network, featuring end-to-end encryption with post-quantum cryptography. Messages are stored on decentralized storage nodes and routed through onion routing for maximum privacy.

## Current Status

**Integration Status: In Progress**

The Android app uses `libsession-util` for networking. Full Pars Network integration requires modifications to the underlying C++ library.

### What Works
- Building and running the app
- Core messaging functionality

### What Needs Work
- Network configuration for Pars SessionVM
- libsession-util modifications
- Pars branding updates

## Installation

### Option 1: Download APK (Easiest)

Download the latest APK from [Releases](https://github.com/parsdao/pars-android/releases):

| Variant | Description |
|---------|-------------|
| **play** | Google Play Store variant |
| **fdroid** | F-Droid variant (no proprietary dependencies) |
| **website** | Direct download variant |

**To install:** Enable "Install from unknown sources" in Android settings, then open the APK.

### Option 2: Build from Source

**Prerequisites:**
- Android Studio (latest)
- JDK 21
- Android SDK 21+

**Steps:**
```bash
git clone https://github.com/parsdao/pars-android
cd pars-android
./gradlew assemblePlayQa
```

APK will be in `app/build/outputs/apk/play/qa/`

### Option 3: F-Droid (Coming Soon)

We're working on F-Droid distribution. Track progress at [pars.network](https://pars.network).

## Architecture

```
Pars Messenger Android
├── app/                    # Main application module
├── libsession-util/        # JNI bindings to C++ library
├── libsignal/              # Signal protocol implementation
└── core-utils/             # Shared utilities

Network Layer
└── libsession-util (C++ via JNI)
    └── Network endpoints (needs configuration for Pars)
```

## Pars Ecosystem

| Repository | Description |
|------------|-------------|
| [parsdao/pars-android](https://github.com/parsdao/pars-android) | Android client (this repo) |
| [parsdao/pars-ios](https://github.com/parsdao/pars-ios) | iOS mobile client |
| [parsdao/pars-desktop](https://github.com/parsdao/pars-desktop) | Desktop client |
| [parsdao/pars-libsession](https://github.com/parsdao/pars-libsession) | Native crypto library |
| [parsdao/node](https://github.com/parsdao/node) | Pars blockchain node |

## Features

- End-to-end encryption (post-quantum)
- Decentralized message storage
- Onion routing for privacy
- Disappearing messages
- Group chats
- Voice messages
- Photo/file sharing

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

1. Fork this repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## Resources

- **Website:** [pars.network](https://pars.network)
- **Documentation:** [docs.pars.network](https://docs.pars.network)
- **PIPs:** [github.com/parsdao/pips](https://github.com/parsdao/pips)

## License

GPL-3.0 - See [LICENSE](LICENSE)

## Acknowledgments

- Fork of [Session Android](https://github.com/session-foundation/session-android)
- Built on [Lux Network](https://lux.network) technology
