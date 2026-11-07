# WI Pass

**WI Pass** is the password and digital identity manager for the WI Arch ecosystem. It is designed to help people securely store, organize, use, and share passwords and other sensitive information across their devices.

Inspired by the product experience of Proton Pass, WI Pass will develop its own implementation, identity, architecture, and security model.

> **Project status:** Product definition and architecture planning. This repository does not yet contain a working password manager. Do not store real credentials or sensitive information in it.

## Product vision

A privacy-first password manager built around end-to-end encryption and a zero-knowledge architecture: sensitive vault content is encrypted on the user's device before synchronization, and the server stores only the encrypted data required to sync devices.

## Planned capabilities

- Password and login manager with secure autofill.
- Encrypted vaults and folders for organizing credentials.
- Secure notes, payment cards, identities, and custom fields.
- Strong password and passphrase generator.
- Passkey storage and passkey-based authentication support.
- Built-in TOTP authenticator for two-factor codes.
- Cross-device synchronization and offline access.
- Secure sharing of individual items and vaults with revocation and expiry controls.
- Browser extensions and desktop/mobile clients.
- Import and export from common password managers.
- Password health checks for weak, reused, and compromised credentials.
- Hide-my-email aliases, subject to integration with a dedicated email-alias provider.
- Encrypted file attachments and emergency access, as later milestones.

## Security principles

1. End-to-end encryption for vault contents and sensitive metadata.
2. Zero-knowledge server design: the backend must not receive vault plaintext or user-held decryption keys.
3. Client-side encryption and decryption; encrypted synchronization payloads only.
4. Vetted cryptographic standards and libraries. No custom cryptography.
5. Explicit threat modeling, security review, and independent assessment before production.
6. Secure recovery and sharing designs that do not introduce hidden server-side decryption.
7. No secrets, real credentials, production tokens, or private keys in source control, logs, analytics, or crash reports.

The WI Arch security baseline is mandatory for this project. WI Zefer is a useful ecosystem reference for local encryption practices, but it is not a password-vault key-management protocol and must not be treated as a drop-in vault encryption engine.

## Proposed architecture

The recommended direction is a TypeScript-first client ecosystem with a Laravel API:

- **Web application:** React + TypeScript.
- **Browser extension:** TypeScript, with dedicated browser autofill and permission boundaries.
- **Desktop application:** Tauri, reusing the web client where safe.
- **Mobile application:** Capacitor with native platform integrations for Android Autofill Framework and iOS AutoFill Credential Provider. These integrations require native implementation and platform-specific review.
- **Backend:** Laravel API for accounts, device registration, encrypted sync, sharing coordination, subscriptions, and operational controls. The backend must never decrypt vault content.
- **Storage:** encrypted client-generated payloads and minimal operational metadata. Database choice and sync protocol must be finalized in architecture decisions.
- **Cryptography:** a reviewed, versioned client-side cryptographic protocol shared consistently across clients. Exact primitives, key hierarchy, KDF parameters, nonce handling, and recovery format require a dedicated ADR and security review before implementation.

This is a proposed direction, not a claim that these technologies or features are already implemented.

## Development milestones

1. **Foundation:** threat model, cryptographic architecture, account/device model, data model, security baseline adoption, and design system.
2. **Secure vault MVP:** client-side encryption, login entries, secure notes, password generator, local lock/unlock, and encrypted backup.
3. **Sync:** encrypted multi-device synchronization, conflict handling, offline behavior, and device revocation.
4. **Autofill:** browser extension first, followed by Android and iOS native autofill integrations.
5. **Identity tools:** cards, identities, custom fields, TOTP, passkeys, and import/export.
6. **Sharing and advanced protection:** secure item/vault sharing, password health, breach monitoring, aliases, file attachments, and emergency access.

Milestones must not be represented as completed until implemented and tested.

## Security and responsible development

See [SECURITY.md](./SECURITY.md), [CLAUDE.md](./CLAUDE.md), and [docs/](./docs/). Security-sensitive changes require a threat-model update, tests, and review. Do not claim "zero knowledge", "end-to-end encrypted", "audited", or "production ready" as implemented product properties until the implementation and evidence support those claims.

## License

To be determined after confirming the project's ownership, dependency licenses, and any third-party code. Do not copy Proton Pass branding, assets, source code, or proprietary materials.

---

Part of the **[WI Arch](https://github.com/wiarch)** ecosystem.
