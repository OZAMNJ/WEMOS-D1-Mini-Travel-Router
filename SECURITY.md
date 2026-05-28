# Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| v7.x    | ✅ Yes     |
| < v7.0  | ❌ No      |

## Reporting a Vulnerability

This project runs as a **network device** on your local network. Security issues are taken seriously.

**Please do NOT open a public GitHub issue for security vulnerabilities.**

### How to Report

1. Open a [GitHub Security Advisory](../../security/advisories/new) (private, only visible to maintainers).
2. Include:
   - A description of the vulnerability
   - Steps to reproduce
   - Potential impact
   - Suggested fix (if known)

### What to Expect

- **Acknowledgement** within 48 hours
- **Status update** within 7 days
- **Patch release** for confirmed critical issues within 14 days
- Credit in the release notes (if desired)

## Known Security Considerations

- **Credentials stored in plaintext** on LittleFS (`/config.txt`). Physical access to the device means full config access. Do not use the same password as other services.
- **HTTP only** — the dashboard at `192.168.4.1` is unencrypted. Only use it on your own local hotspot.
- **Default credentials** are `admin` / `admin`. **Change immediately** after first flash.
- **Open AP mode** is supported but strongly discouraged in public spaces.
