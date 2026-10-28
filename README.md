# Early Click Buffer: OVERDRIVE

**An experimental input-buffering mod for Geometry Dash 2.2081 on Android.**

Early Click Buffer: OVERDRIVE is a port in progress based on [Input Buffer by Lyophi](https://github.com/Lyoph/GMD-Buffer-Mod). It remembers selected early inputs and can adjust very short taps, helping make difficult timings more consistent.

> [!WARNING]
> **Android support is still in progress.** The project has not yet been confirmed as a working, tested Android release. Builds and in-game behavior must be verified on the target device and Geometry Dash/Geode version before use.

## Features

- **Early-input buffering:** for supported modes, an early tap can be remembered and sent when the player reaches a landing or orb.
- **Short-tap handling:** in supported flying modes, very short presses can be adjusted according to the selected style.
- **Per-mode timing windows:** configure the buffer window separately for different game modes.
- **Wave timing styles:** choose between Min Hold, Min Gap, and Grid where available.
- **Dual-mode support:** experimental support for buffering the two icons independently in dual sections.
- **In-game settings and hotkeys:** adjust timing and inspect debug logs using the mod's settings.

The exact behavior depends on the active mode, timing window, and selected style. Buffering is input assistance; it does not guarantee that a click will be appropriate for every level or timing.

## Timing Windows

Timing windows are measured in game ticks:

| Value | Meaning |
| --- | --- |
| `-1` | Use the Main Buffer Window |
| `0` | Disable buffering for that mode |
| `1` or higher | Use the specified number of ticks |

At 240 ticks per second, one tick is approximately **4.17 ms**.

| Ticks | Approximate time |
| ---: | ---: |
| 2 | 8 ms |
| 4 | 17 ms |
| 8 | 33 ms |
| 16 | 67 ms |
| 32 | 133 ms |

Smaller windows generally feel stricter. Larger windows are more forgiving, but can trigger inputs earlier or later than intended.

## Wave Timing Styles

- **Min Hold** — extends a very short press to at least the configured window.
- **Min Gap** — enforces a minimum interval between a release and the next press; an early press may be delayed.
- **Grid** — aligns presses and releases to a fixed timing grid. This can add delay and may make some timings harder or impossible.

Change timing styles while paused when possible, especially during a wave section.

## Installation

There is **no confirmed stable Android release documented yet**.

When a successful Android build is available:

1. Confirm that your Geometry Dash version and device architecture match the build.
2. Download the `.geode` package from the repository's [Releases](../../releases) page or a verified build artifact.
3. Install it using the normal Geode mod installation process for your Android setup.
4. Restart Geometry Dash and check the Geode mod list for **Early Click Buffer: OVERDRIVE**.

Do not install an artifact from a failed or incomplete build. If you are testing a development build, expect bugs and back up your data first.

## Superb Input Precision Compatibility

Compatibility with [Superb Input Precision (SIP)](https://github.com/ch-zzzy/Superb-Input-Precision) is being investigated.

The current integration approach queues synthetic OVERDRIVE inputs so SIP can process their timing. A remaining concern is preventing an already scheduled synthetic input from being buffered again when SIP dispatches it through the game's input handler.

**Do not assume this interaction is fully resolved or tested yet.**

## Known Limitations

- Android compilation and in-game behavior still need to be verified on the intended device and Geode version.
- Dual-mode support is experimental.
- The timing window is assistance, not a guarantee that an input will land at the desired moment.
- Other input-manipulation mods may conflict or affect timing. When diagnosing issues, test with other input mods disabled first.
- Some level lists or competitions restrict input-assistance mods. Check the relevant rules before submitting a run.

## Building from Source

This project uses Geode and CMake. Install a compatible Geode SDK and toolchain for the target platform, then build using the project's configured workflow.

See [Android port notes](ANDROID_PORT_NOTES.md) and the GitHub Actions workflows for the current build setup.

A successful compile alone does not prove the mod works correctly in-game; test the generated package on the matching Android version and architecture.

## Credits and License

- **Original implementation:** [Input Buffer by Lyophi](https://github.com/Lyoph/GMD-Buffer-Mod).
- **Modding platform:** [Geode SDK](https://geode-sdk.org).
- **Subtick timing compatibility work:** [Superb Input Precision](https://github.com/ch-zzzy/Superb-Input-Precision).

This project retains the upstream **MIT License**. See [LICENSE](LICENSE) for the license text and applicable notices.
