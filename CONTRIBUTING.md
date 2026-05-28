# Contributing to WEMOS D1 Mini Travel Router

Thank you for your interest in contributing! This project welcomes improvements, bug fixes, and feature suggestions.

> **Note:** The full Arduino source code (`router.ino`) is not yet publicly available in this repository. Currently, only the pre-compiled firmware binary (`router.bin`) is distributed. The source code will be released in a future update.

## How You Can Contribute Right Now

- **Report Bugs** — Open an issue using the Bug Report template. Include your hardware version, Arduino IDE version, and steps to reproduce.
- **Suggest Features** — Open an issue using the Feature Request template with a clear description of what you'd like to see.
- **Improve Documentation** — Found a typo or unclear step in the README? Feel free to open a PR directly against `README.md`.
- **Test the Firmware** — Flash `router.bin` on your D1 Mini and report your results (hardware version, speeds, bugs) in the Issues section.

## Arduino IDE Setup (for when source is released)

When the source code becomes available, you will need the following board settings:

- **Board:** LOLIN(WEMOS) D1 R2 & mini
- **CPU Frequency:** 160 MHz (Required for performance)
- **lwIP Variant:** v2 Higher Bandwidth (CRITICAL: NAT will fail without this)
- **Flash Size:** 4MB (FS: 1MB, OTA: ~1019KB) (Required for LittleFS saving)

## Reporting Bugs

Use the **Bug Report** issue template. Include:
- Your hardware version (D1 Mini v3, v4, etc.)
- Arduino IDE version and board package version
- Serial monitor output at startup
- Steps to reproduce

## Suggesting Features

Use the **Feature Request** issue template. Describe:
- The problem you are trying to solve
- Your proposed solution
- Any alternatives you considered

## Code of Conduct

This project follows the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md). By participating, you agree to uphold this standard.
