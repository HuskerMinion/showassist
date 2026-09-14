<p align="center">
  <img src="images/showassist-icon.png" alt="ShowAssist icon" width="128" height="128">
</p>

<h1 align="center">ShowAssist</h1>

<p align="center">Turn an unlocked Amazon Echo Show 5 into a local Home Assistant voice satellite and smart display.</p>

ShowAssist is a modified fork of the [View Assist Companion App (VACA)](https://github.com/msp1974/ViewAssistCompanionApp) by Mark Parker, maintained for running unlocked Amazon Echo Show 5 (2nd gen, 2021) devices as Home Assistant voice satellites. It uses the standard VACA Home Assistant integration, so wake words, Assist pipelines, media playback and dashboards work the same way.

## Requirements

- An Echo Show 5 (2nd gen) unlocked with amonet and running LineageOS 18.1 (v0.4 or newer).
- The View Assist Companion App integration for Home Assistant, installed from HACS, at the same version as the app (currently 0.13.3).

## Install

1. Download the latest `showassist-*-release.apk` from [Releases](https://github.com/HuskerMinion/showassist/releases).
2. Install it with `adb install -g showassist-<version>-release.apk` and set ShowAssist as the home app so it starts on boot.
3. In Home Assistant, add the View Assist Companion App integration using the IP address and port shown on the ShowAssist startup screen, then log in on the device.

If the official VACA app is installed, remove it first — both apps use the microphone and port 10800.

## Changes from upstream

- **Identity:** installs as `com.huskerminion.showassist` with the name "ShowAssist" and its own icon and startup screen, so it can't be overwritten by, or confused with, the official app. In-app updates check this repository's releases.
- **Music ducking:** the un-duck volume animation is cancelled when music is ducked again, so music no longer returns to full volume while the assistant is listening.
- **Voice pipeline:** a stale `pipeline-ended` event from a run Home Assistant just cancelled no longer ends the new run before it starts, which previously left the satellite stuck in "listening" and made every following wake word fail.
- **Release builds:** code shrinking (R8) is disabled, because it removed classes that native code and WorkManager load by name and crashed the app at startup.

Bug fixes are kept as separate commits.

## License

Licensed under the Apache License, Version 2.0, the same as upstream. See `LICENSE` and `NOTICE`.
