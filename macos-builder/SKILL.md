---
name: macos-builder
description: Automates macOS software building and development (Native, Tauri, Electron, React Native macOS) from Windows/Linux using GitHub Actions cloud runners.
---

# macos-builder Skill

## Overview
Whenever the user asks to build, compile, or package a macOS application (`.app`, `.dmg`, or `.pkg`) from a Windows or Linux machine, you MUST rely on a GitHub Actions CI/CD pipeline to route the build process to Apple `macos-latest` cloud servers.

Since macOS software requires Xcode tools and macOS operating systems to codesign and compile, Windows cannot do this natively. 

## Quick Start (GitHub Actions Workflow)

To set up a macOS builder, generate a GitHub actions workflow in the project repository (`.github/workflows/build-macos.yml`).

### 1. Tauri (Rust/Web) Mac Builder
If the project is a Tauri app, use the following action skeleton:
```yaml
name: Build macOS (Tauri)
on: [workflow_dispatch]
jobs:
  build-mac:
    runs-on: macos-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node
        uses: actions/setup-node@v3
      - name: Setup Rust
        uses: actions-rs/toolchain@v1
        with:
          toolchain: stable
      - run: npm install
      - run: npm run tauri build
      - uses: actions/upload-artifact@v3
        with:
          name: macos-app
          path: src-tauri/target/release/bundle/macos/
```

### 2. Electron Mac Builder
If the project is Electron:
```yaml
name: Build macOS (Electron)
on: [workflow_dispatch]
jobs:
  build-mac:
    runs-on: macos-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node
        uses: actions/setup-node@v3
      - run: npm install
      - run: npm run electron:build -- --mac
      - uses: actions/upload-artifact@v3
        with:
          name: macos-dmg
          path: dist/*.dmg
```

### 3. Downloading the Build
Instruct the user that once they commit and push the workflow to their repository, they can trigger the build from the GitHub Actions tab. Once complete, they can download the `.dmg` or `.app.tar.gz` artifact directly from the workflow run page on GitHub.

## Code Signing (Important)
macOS builds generated this way are **unsigned** by default. To properly sign the `.app` for distribution without the "App is damaged" gatekeeper warning on the user's end, you must inject Apple Developer Certificates (`MACOS_CERTIFICATE`, `MACOS_CERTIFICATE_PWD`) into the GitHub Actions secrets and run `security import` steps prior to the build.
