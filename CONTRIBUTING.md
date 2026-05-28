# Contributing to WEMOS D1 Mini Travel Router

Thank you for your interest in contributing! This project welcomes improvements, bug fixes, and feature suggestions.

## Getting Started

1. **Fork** the repository and clone it locally.
2. Make sure you have the correct Arduino IDE setup:
   - Board: **LOLIN(WEMOS) D1 R2 & mini**
   - lwIP Variant: **v2 Higher Bandwidth**
   - Flash Size: **4MB (FS: 1MB, OTA: ~1019KB)**
3. Open `src/router.ino` in the Arduino IDE.

## How to Contribute

### Reporting Bugs
Use the **Bug Report** issue template. Include:
- Your hardware version (D1 Mini v3, v4, etc.)
- Arduino IDE version and board package version
- Serial monitor output at startup
- Steps to reproduce

### Suggesting Features
Use the **Feature Request** issue template. Explain the use case clearly.

### Submitting Code

1. Create a branch: `git checkout -b feature/your-feature-name`
2. Make your changes in `src/router.ino`
3. Test on real hardware before submitting
4. Commit with a clear message: `git commit -m "feat: add WPA3 support"`
5. Open a Pull Request against `main` using the PR template

## Commit Message Format

Use conventional commits:
- `feat:` — new feature
- `fix:` — bug fix
- `docs:` — documentation only
- `refactor:` — code restructure without behavior change
- `chore:` — maintenance tasks

## Code Style

- Follow the existing indentation (2 spaces)
- Keep comments concise and in English
- Avoid adding new libraries unless strictly necessary (flash space is limited on ESP8266)
- All persistent config changes must go through `saveConfig()` / `loadConfig()`

## Security

If you find a **security vulnerability** (e.g. authentication bypass, config injection), please do **not** open a public issue. See [SECURITY.md](SECURITY.md) for responsible disclosure.

## License

By contributing, you agree your code will be licensed under the [MIT License](LICENSE).
