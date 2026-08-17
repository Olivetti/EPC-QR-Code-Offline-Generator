# Changelog

All notable changes to this project are documented here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

Versions use CalVer: `YYYY.MM.DD.N`, where `N` counts the releases published on
that day. There is no build step — a release is the state of `main` at the tag,
packaged as a ZIP you can unpack and open. The release workflow refuses to
publish a tag unless `APP_VERSION` in `assets/app.js` and a section in this file
carry the same version.

## [Unreleased]

## [2026.08.17.1] - 2026-08-17

### Added
- Version indicator in the footer, linked to the releases page, so a downloaded
  offline copy can be matched against a release later on.
- Release workflow: pushing a `v*` tag publishes a GitHub release with a
  ready-to-use ZIP (`index.html`, `assets/`, README, LICENSE, this changelog).
- This changelog.
- Content-Security-Policy with `connect-src 'none'`. The browser now enforces
  the offline promise: the IBAN and amount you type cannot be sent anywhere,
  even if a script were injected.
- `.editorconfig` pinning UTF-8 and LF, so the encoding damage repaired below
  cannot happen again.
- `.gitignore` (Malte Hain).

### Changed
- QR rendering now uses `qrcode-generator`, which encodes umlauts and other
  non-ASCII characters correctly (Malte Hain).
- README credits the QR library actually in use.

### Fixed
- Error correction is pinned to level M, as EPC069-12 requires. When the payload
  grows, the QR version grows instead of the error correction dropping.
- PNG and JPEG export works again for SVG-rendered QR codes (Malte Hain).
- Repaired double-encoded language names in `assets/app.js` (`ÄŒeÅ¡tina` had
  replaced `Čeština` in eight entries) and stripped a stray BOM.
- Removed a call to a footer helper that no longer exists.
- Dropped duplicate function definitions that shadowed the live ones.

## [2025.09.05.1] - 2025-09-05

First tagged version: offline EPC/SEPA QR generator with live IBAN validation,
payload byte guard, PNG/SVG/JPG export, dark mode and optional locales. No
release notes were recorded at the time; the commit history holds the detail.

[Unreleased]: https://github.com/quasistatic-setup/EPC-QR-Code-Offline-Generator/compare/v2026.08.17.1...HEAD
[2026.08.17.1]: https://github.com/quasistatic-setup/EPC-QR-Code-Offline-Generator/compare/v2025.09.05.1...v2026.08.17.1
[2025.09.05.1]: https://github.com/quasistatic-setup/EPC-QR-Code-Offline-Generator/releases/tag/v2025.09.05.1
