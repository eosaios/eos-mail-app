# EOS Mail

[English](./README.en.md) | [中文](./README.md)

A local-first desktop email client: mail arrives over IMAP and leaves over SMTP, and everything syncs to storage on your own computer — no cloud relay, no telemetry. Multiple accounts, one-click Gmail authorization, full offline search, and dual-layer sanitized HTML rendering, built with Tauri 2 + React.

> **This repository is the public portal for EOS Mail**, used for:
> - Installer downloads: see [Releases](https://github.com/eosaios/eos-mail-app/releases)
> - Bug reports and feature suggestions: please open [Issues](https://github.com/eosaios/eos-mail-app/issues)
> - Multi-platform builds (GitHub Actions)
>
> EOS Mail is closed-source commercial software. **The source code is not in this repository.**

## Download & Install

**Free during beta.** Pricing for the stable release will be announced closer to launch.

| Platform | Installer | Notes |
|---|---|---|
| Windows | `*-setup.exe` | NSIS installer, unsigned |
| macOS | `*.dmg` | universal (Intel + Apple Silicon), unsigned |
| Linux | `*.deb` / `*.AppImage` | both deb and AppImage |

- If Windows SmartScreen warns on first run, choose "More info → Run anyway"
- If macOS Gatekeeper blocks the first launch, run `xattr -cr "/Applications/EOS Mail.app"`
- Mail data lives in your user directory (a local SQLite database); upgrades never touch it, and uninstalling the app does not delete your mail
- Integrity checks: every Release ships a SHA256SUMS.txt

## Features

- **Multiple accounts**: standard IMAP / SMTP (SSL / STARTTLS) plus one-click Gmail OAuth2
- **Local-first**: full local indexing — read, search, and organize offline; incremental sync when you reconnect
- **Unified search**: full-text keyword search and attachment search (`has:pdf`, `file:invoice`)
- **Safe rendering**: HTML mail is sanitized on the Rust side and rendered inside a scriptless sandboxed iframe; remote images are blocked by default (anti read-receipt tracking) and unlocked per message on click
- **Anti-phishing**: display-name spoofing detection, link-text versus real-domain mismatch warnings, a suspicion score banner, and content-based attachment checks (double extensions / RTL override characters / executable confirmation)
- **Composing**: message composing, drafts, and a sent folder
- **Personalization**: light/dark themes, English and Chinese UI
- **100% local**: outside the mail servers you configure and the Google authorization page, the app makes no network requests — zero telemetry, zero crash reporting

## Privacy & Credentials

- Account passwords / app passwords / OAuth refresh tokens are stored **only in the OS keychain** (macOS Keychain / Windows Credential Manager / Linux Secret Service), never in the database or any plaintext file
- Message bodies and attachments exist only in the local database and attachment directory on your computer
- IMAP / SMTP connections are always TLS-encrypted; plaintext downgrade is not offered or accepted

## Feedback Guide

- 🐛 Bugs: include your OS version, EOS Mail version, mail provider, and reproduction steps (**never attach message bodies or passwords**)
- 💡 Feature requests: describe your use case, not just the solution
- 🔒 Privacy: the app makes no network requests beyond your mail servers and the authorization page — if you observe otherwise, please report it immediately

## License

© 2026 EOSAIOS. All rights reserved. This software may not be copied or redistributed without authorization.
