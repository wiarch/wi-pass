# WI Pass — Project Creation Brief

Build WI Pass, an original password and digital identity manager for the WI Arch ecosystem. Use Proton Pass as a functional reference, not as a source of code, branding, assets, or proprietary implementation.

## Product objective

Create a privacy-first password manager that lets users securely store, organize, autofill, synchronize, and share credentials and sensitive identity information across web, browser, desktop, and mobile clients.

## Required product areas

- Login/password records with title, username, password, URLs, notes, tags, custom fields, and history.
- Encrypted vaults and folders.
- Secure notes, payment cards, and personal identities.
- Password/passphrase generator and password-health analysis.
- TOTP authenticator.
- Passkey support with platform-appropriate WebAuthn/passkey APIs.
- Encrypted sync and offline access.
- Secure sharing of individual items and vaults, with expiration, revocation, and access control.
- Browser extension with carefully scoped autofill permissions and phishing-resistant domain matching.
- Desktop and mobile clients; native Android and iOS autofill integration.
- Import/export from common password managers.
- Future: hide-my-email aliases, breach monitoring, encrypted attachments, emergency access, CLI.

## Proposed technology direction

Use this as the recommended starting point, but validate compatibility and security before committing to implementation:

- React + TypeScript for web interfaces.
- TypeScript browser extension.
- Tauri desktop application.
- Capacitor mobile application with native Android/iOS autofill extensions and platform-specific secure storage.
- Laravel API for accounts, devices, encrypted synchronization, sharing coordination, and operational administration.
- A dedicated, versioned client-side cryptographic protocol shared across clients.

Do not create multiple crypto implementations casually. If cross-platform compatibility requires separate language bindings, define and test a single protocol with shared test vectors.

## Non-negotiable security requirements

1. Establish a threat model before building the vault or authentication flows.
2. Design end-to-end encryption and zero-knowledge storage from the beginning. The server must never receive plaintext vault contents or user-held decryption keys.
3. Use vetted cryptographic standards and maintained libraries. Never invent encryption, key exchange, password hashing, KDF, or sharing algorithms.
4. Define key hierarchy, key derivation, authenticated encryption, nonce generation, versioning, recovery, sharing, and device revocation in reviewed architecture decisions before coding them.
5. Encrypt sensitive fields and metadata, not only password values.
6. Keep secrets out of logs, telemetry, analytics, URLs, crash reports, and source control.
7. Design secure local persistence, clipboard handling, lock/unlock, memory exposure, backups, logout, and account deletion.
8. Enforce strict browser extension origin and frame validation to prevent phishing and credential exfiltration.
9. Follow the WI Arch security baseline. WI Zefer is a reference for encryption practices, not a drop-in vault cryptographic protocol.
10. Do not claim security properties as implemented until supported by code, tests, and independent review.

## First delivery

Do not attempt to build every feature at once. Start with:
- repository and architecture assessment;
- product requirements and threat model;
- architecture decision records for cryptography, key management, sync, recovery, and platforms;
- data model and API contracts that store only encrypted vault payloads;
- design system and clickable UI prototype using synthetic sample data only;
- implementation roadmap with acceptance criteria and security tests.

Then implement the secure vault MVP in small phases. Every phase must include tests and updated documentation.

## Deliverables

- Working source code with clear project structure.
- README with setup, architecture, feature status, and development instructions.
- CLAUDE.md and security documentation kept current.
- Threat model and architecture decision records.
- Environment example files containing placeholders only.
- CI for linting, type checking, tests, builds, dependency review, and security scanning.
- Issue/PR templates and contribution guidance.

Do not invent completed features, integrations, certifications, audits, or test results. Preserve existing repository content and never overwrite useful code without inspection.
