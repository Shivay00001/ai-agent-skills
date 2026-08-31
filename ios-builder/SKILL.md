---
name: ios-builder
description: Automates iOS app building and development (native, Flutter, React Native) from any OS (Windows/Linux) using MobAI ios-builder via GitHub Actions.
---

# ios-builder Skill

## Overview
Whenever the user asks to build, compile, or develop an iOS app (especially from Windows/Linux/WSL) or asks to use MobAI ios-builder, you MUST use the `builder` CLI tool. It uses GitHub Actions for remote builds and MobAI for on-device development.

## Quick Start
Before running these commands, ensure the `builder` CLI is installed (via https://github.com/MobAI-App/ios-builder/releases for Windows or the install script for macOS/Linux).

### 1. Setup & Authentication
First, authenticate with GitHub:
```bash
builder auth github
```

Next, initialize the project in your project directory (supports Native iOS/Swift, React Native, Expo, Flutter, Cordova/Ionic):
```bash
builder init
```
*This detects the GitHub repo, creates the workflow files, and offers to commit, push, and trigger the first build.*

### 2. Building
To trigger a build and download the IPA to `./dist/`:
```bash
builder ios build
```

To build without code signing (if signing is configured):
```bash
builder ios build --unsigned
```

### 3. Development (Requires MobAI)
For Flutter hot reload with file watching:
```bash
builder dev flutter
```
*(Options: `--no-watch`, `--no-attach`, `--skip-install --bundle-id <id>`)*

For React Native hot reload:
```bash
builder dev rn
```
*(Options: `--metro-port <port>`)*

### 4. Code Signing
To set up code signing secrets:
```bash
builder signing setup
```

## Supported Frameworks
- Native iOS/Swift (`.` root)
- React Native (`ios/`)
- Expo ejected (`ios/`)
- Flutter (`ios/`)
- Cordova/Ionic (`platforms/ios/`)
