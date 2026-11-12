# Changelog

All notable changes to this fork of [BLEUnlock](https://github.com/ts1/BLEUnlock) are documented here.

## [Unreleased] — 2026-11-12

### Added

- **Platform SSO lock screen support** (optional, off by default): a new
  *Use Platform SSO Lock Screen* menu item lets BLEUnlock type the password into
  Apple's native Platform SSO lock-screen field. See
  [docs/macos-unlock.md](docs/macos-unlock.md). (upstream PR #195)
- Documentation for unlocking on recent macOS versions: permissions, lock-state
  detection, and diagnostic logs ([docs/macos-unlock.md](docs/macos-unlock.md)).
- Regression tests for lock-state detection, keyboard input, and unlock-target
  policy (`tools/test-macos27.zsh`), plus standalone tests for RSSI smoothing
  (`Tests/RSSIDecisionTests`).
- French localization. (upstream PR #172)
- Hebrew and Romanian translations. (upstream PR #146)
- Traditional Chinese README ([README_CHT.md](README_CHT.md)). (upstream PR #188)
- This changelog.

### Changed

- **Minimum macOS is now 12 (Monterey).** The deployment target was raised from
  10.13 because current Xcode no longer builds for older targets.
- Unlocking now uses the smoothed (moving-average) RSSI and needs at least 3
  samples, instead of a single raw reading. One strong spike (for example from a
  reflection or an advertising burst) can no longer unlock the Mac from far away.
  (refs upstream issue #153)
- Password input goes only to a verified, Apple-signed system process
  (`loginwindow`, or Platform SSO when enabled), not the global event stream.
  BLEUnlock waits for an observed unlock before reporting success and does not
  resubmit the password. (upstream PR #195)
- CI now runs on pull requests as well as pushes, and builds with a macOS 12
  deployment target and code signing disabled.
- Improved Norwegian translation. (upstream PR #170)
- Proofread Simplified Chinese translation. (upstream PR #143)

### Fixed

- Automatic unlock on macOS 27, where `CGSSessionScreenIsLocked` may be missing;
  lock state now also comes from the IORegistry `IOConsoleLocked` property.
  (upstream PR #195)
- Duplicate device names in the device scan list. (upstream PR #167)
- Variable reference in the Apple device-name parser. (upstream PR #185)

## [1.12.2] and earlier

See the [upstream releases](https://github.com/ts1/BLEUnlock/releases).
