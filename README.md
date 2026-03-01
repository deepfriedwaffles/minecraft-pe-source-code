# Minecraft Pocket Edition (v0.6.1) Source Code

This repository contains the original source code for **Minecraft: Pocket Edition v0.6.1**, supporting both Android and iOS platforms.
Right now you have to compile this yourself, but I'll supply a precompiled .ipa to put on you iPhone soon! (not everyone has Macs!)

> [!WARNING]
> The `main` branch is preserved for historical purposes and contains legacy 32-bit code (armv7) that is **not compatible** with modern 64-bit iOS devices or recent versions of Xcode. You could try to compile it with an old version of Xcode, but that's untested an I'm not sure if that works

## Modern iDevice Support (arm64)

To build and run the game, you have to use the `arm64-build` branch. This branch has been modernized to comply with the new C++ standards as they have changed since 2011. Also includes fixes for modern A-series chips to actually get the game running.

* **Architecture:** Migrated from `armv7` to `arm64`.
* **Legacy Patching:** Fixed header file extensions (e.g., `.height` back to `.h`) and resolved ambiguous function redefinitions.

---

## Cloning & Compiling Instructions

Follow these steps to get the game running on your own physical iOS device using Xcode. You will need a Mac. If you don't have a Mac, you could try using a macOS virtual machine. I'd reccomend using Ventura or newer.

### 1. Clone the arm64 Branch

Open your terminal and clone the repository, ensuring you switch to the `arm64-build` branch:

```bash
git clone https://github.com/deepfriedwaffles/minecraft-pe-source-code.git
cd minecraft-pe-source-code
git checkout arm64-build

```

### 2. Open in Xcode

Locate the project file in `handheld/project/iosproj/minecraftpe.xcodeproj` and open it.

### 3. Configure Code Signing

Before you can deploy to an iPhone, you must sign the app with your own Apple Developer account:

1. Select the **minecraftpe** project in the left sidebar.
2. Go to **Signing & Capabilities**.
3. Change the **Bundle Identifier** to something unique (e.g., `com.yourname.mcpe`).
4. Select your **Team** from the dropdown menu.

### 4. Build and Run

1. Connect your iPhone via USB or LAN.
2. Select your device from the run destination menu at the top of Xcode.
3. Press **Cmd + R** (or the Play button).
4. **Note:** If you encounter a "Developer Mode" or "Untrusted Developer" error on your phone, go to **Settings > General > VPN & Device Management** to trust your certificate.

---

## Known Issues

* **Display:** The game renders at a fixed 480x320 resolution and does not yet support the big iPhone displays.
* **UI:** The Options menu is absolutely broken.
* **Multiplayer:** Local/Online multiplayer is currently untested on `arm64` and may require further RakNet patching.

---
