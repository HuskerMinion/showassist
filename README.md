# ShowAssist

ShowAssist is a modified fork of the [View Assist Companion App (VACA)](https://github.com/msp1974/ViewAssistCompanionApp) by Mark Parker, maintained for running unlocked Amazon Echo Show 5 (2nd gen) devices as Home Assistant voice satellites. It works with the standard VACA Home Assistant integration.

## Changes from upstream

- Installs as `com.huskerminion.showassist` with the app name "ShowAssist", so it can't be overwritten by, or confused with, the official app. In-app updates check this repository's releases.
- Music ducking: the un-duck volume animation is cancelled when music is ducked again, so music no longer returns to full volume while the assistant is listening.
- Voice pipeline: a stale `pipeline-ended` event from a run Home Assistant just cancelled no longer ends the new run before it starts, which previously left the satellite stuck in "listening" and made every following wake word fail.

Bug fixes are kept as separate commits so they can be offered back upstream.

## License

Licensed under the Apache License, Version 2.0, the same as upstream. See `LICENSE` and `NOTICE`.

---

# View Assist Companion Android App

Readme coming soon.
