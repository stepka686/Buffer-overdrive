# Android port notes

This is a first-pass Android-targeted port scaffold based on Input Buffer by Lyophi.

## Changes in this scaffold
- `mod.json` targets Android Geometry Dash 2.2081 and uses a new mod ID/name.
- CMake project name changed to `EarlyClickOverdrive`.
- Added a GitHub Actions workflow to attempt an Android64 build with Geode v5.11.2 and the bindings commit pinned by the upstream project's workflow.
- Upstream `LICENSE` is preserved (MIT).

## Important status
This is **not a verified working Android build yet**. The original project declares Windows as its only supported game platform. The gameplay hook signatures and Android touch-input behavior still need to be verified by a successful Android build and in-game testing.

## Build using GitHub Actions from an Android phone
1. Create a GitHub repository and upload the contents of this folder (not the containing folder).
2. Open the repository's **Actions** tab and enable Actions if prompted.
3. Run **Build Android mod**, or push a commit to trigger it.
4. Open the workflow run and download the `EarlyClickOverdrive-Android64` artifact.
5. Test it only after checking that the build completed successfully. Do not install a `.geode` artifact if the workflow failed.

If your device runs a 32-bit Geometry Dash build, change workflow target `Android64` to `Android32` and confirm the matching game/Geode architecture first.

## Upstream attribution
The input-buffering implementation is derived from the MIT-licensed Input Buffer project by Lyophi:
https://github.com/Lyoph/GMD-Buffer-Mod

The original LICENSE file is included and must remain with redistributed copies.
