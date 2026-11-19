# EOS Mail

[English](./README.en.md) | [中文](./README.md)

A local-first desktop email client built with Tauri 2, Rust and React. Read and search synced mail on your computer; sending, receiving, fetching content not yet downloaded, and optional AI, account and update services require network access.

> **This repository is the public portal for EOS Mail**, providing downloads, issue reporting and multi-platform builds.
> EOS Mail is closed-source commercial software. **The source code is not in this repository.**
> See the [product page](https://eosaios.com/en/products/mail/) and version-specific release notes for available features and downloads.

## Download & Install

[Latest stable release and file checksums](https://github.com/eosaios/eos-mail-app/releases/latest)

| Platform | Current stable download |
|---|---|
| macOS · Apple Silicon | [Official download](https://eosaios.com/download/eos-mail/darwin-arm64) |
| Windows · x64 | [Download `.exe`](https://eosaios.com/download/eos-mail/windows-amd64) |
| Linux · x64 | [Download `.deb`](https://eosaios.com/download/eos-mail/linux-amd64) |

The Windows website installer lacks an Authenticode signature. SmartScreen may report an unknown publisher.

Check the download source, OS and architecture, and follow the normal installation process. If the OS displays a security warning, report the warning and version rather than disabling security checks or removing quarantine attributes. Back up important mail, attachments and exports before updating or uninstalling. Uninstalling is not the same as deleting all local copies or data held by your mail provider.

## Mail Accounts & Features

- **Multiple accounts**: connect mailboxes that support IMAP / SMTP, using provider-supported authentication and TLS-encrypted connections.
- **Manual Gmail setup**: use a Google App Password to receive mail over IMAP and send it over SMTP. Enable Google 2-Step Verification, then [create an App Password](https://myaccount.google.com/apppasswords). Do not enter your main Google password. Availability depends on account eligibility and organization policies. See [Google's guidance](https://support.google.com/accounts/answer/185833).
- **Offline use**: read and search downloaded mail. New mail sync, sending and content not yet downloaded still require a connection.
- **Search**: search synced messages by keywords and attachment conditions; this does not mean every attachment's contents are full-text indexed.
- **Safe rendering**: sanitized HTML mail in a scriptless sandbox, with remote images blocked by default.
- **Anti-phishing**: warnings for sender impersonation, mismatched link domains and suspicious attachments.
- **Writing & interface**: composing, drafts and sent-mail management, light/dark themes, and English/Chinese UI.

## Pro & Network Access

EOS Mail offers Pro subscriptions. The website currently lists US$5.99 monthly and US$49.99 annually. See the [product page](https://eosaios.com/en/products/mail/) for current entitlements, applicable versions and checkout pricing.

Local-first does not mean fully offline or connected only to mail servers. Account sign-in, entitlement checks, updates and enabled AI / semantic indexing services may access the network. AI or semantic indexing may send relevant mail content and context to configured services; local and cloud models have different data paths. Review your configuration and the [privacy policy](https://eosaios.com/en/privacy) before enabling them. Manual Gmail setup does not grant permission for every form of cloud AI processing.

## Privacy & Credentials

- Credentials use local credential storage. The current macOS version uses an encrypted local-file backend, not exclusively the OS keychain. OS user permissions protect the key and ciphertext; this does not defend against malicious processes running as the same user.
- Credential encryption does not mean the entire mail database is encrypted. Synced messages and attachment copies are stored locally. When using an EOS-hosted mailbox, EOS Mail Center also stores messages on its servers as the mail provider.
- Removing a local account, deleting mail at the provider, clearing attachments or backups, and cancelling a subscription are separate operations.
- See the [privacy policy](https://eosaios.com/en/privacy) for data flows, third-party processing and deletion details.

## Feedback

Open an [Issue](https://github.com/eosaios/eos-mail-app/issues) with your OS, EOS Mail version, mail provider, error message and reproduction steps. Redact private information. **Never submit passwords, App Passwords, tokens or message bodies.** Please also report behavior inconsistent with the privacy information above.

## License

© 2026 EOSAIOS. All rights reserved. This software may not be copied or redistributed without authorization.
