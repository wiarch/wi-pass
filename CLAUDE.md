# WI Pass — Agent Instructions

## Product context

WI Pass is the planned password and digital identity manager for WI Arch. Its product reference is Proton Pass, but the implementation, branding, architecture, and code must be original.

The repository is currently in product-definition/planning stage. Never imply that planned capabilities already exist.

## Mandatory security rules

- Follow the WI Arch security baseline in the WI Zefer documentation: authentication, authorization, session security, secrets, encryption, input validation, API protection, supply-chain controls, CI/CD, logging, incident response, and backups.
- Treat WI Pass as a high-impact security product. Every change involving cryptography, authentication, recovery, sharing, autofill, browser permissions, device trust, or synchronization requires an explicit threat-model update.
- Never implement custom cryptographic algorithms or invent protocol formats casually. Use vetted standards and maintained libraries; document algorithm agility and versioning.
- Never send plaintext vault content, passwords, TOTP seeds, private keys, recovery secrets, or decrypted metadata to the backend, telemetry, analytics, logs, or crash reporting.
- Never store plaintext credentials in local storage, browser sync storage, SQLite, IndexedDB, caches, logs, or temporary files. Persistent client storage must follow the approved encryption design.
- Do not place secrets in URLs, query strings, command-line arguments, source code, test fixtures, screenshots, or issue reports.
- Do not weaken TLS verification or disable certificate validation to make integrations work.
- Enforce least privilege and strict origin/extension permissions. Autofill must defend against phishing, lookalike domains, frame confusion, and credential exfiltration.
- Design secure logout, lock, clipboard clearing, session expiry, device revocation, backup, recovery, and account deletion behavior.
- Do not claim end-to-end encryption, zero-knowledge, passkey support, secure sharing, or independent audit until implemented and verified.

## Architecture guardrails

- Proposed direction: React/TypeScript clients, browser extension, Tauri desktop, Capacitor mobile with native autofill integrations, and a Laravel API.
- The backend is an untrusted storage/synchronization and coordination service for vault content. It must not possess user vault decryption keys.
- Keep the cryptographic protocol versioned and consistent across clients. Do not create separate incompatible crypto implementations without an approved design.
- WI Zefer is an ecosystem encryption reference, not a ready-made password-vault key-management protocol. Do not couple WI Pass security to its file format.
- Separate product domain logic, cryptographic boundaries, persistence, synchronization, and platform autofill adapters.
- Document architecture decisions in ADRs before introducing key formats, KDF parameters, sharing protocols, recovery flows, or cryptographic dependencies.

## Engineering workflow

1. Inspect the existing repository before editing. Preserve useful files and history.
2. Read README.md, docs/, SECURITY.md, and relevant architecture decisions.
3. Identify whether a requested feature is implemented, partially implemented, planned, or unsupported.
4. Prefer small, reviewable changes with tests.
5. Add tests for malformed encrypted payloads, tampering, replay, concurrency, offline behavior, device revocation, and authorization where applicable.
6. Run the relevant lint, typecheck, test, and build commands. Report exactly what ran and its result.
7. Never commit real secrets, real user vault data, production credentials, or unredacted security artifacts.
8. Update documentation and threat models alongside security-sensitive code.

## Quality bar

Production readiness requires a documented threat model, independent security review, secure recovery design, cross-platform cryptographic test vectors, dependency review, automated security gates, backup/restore testing, and a tested incident-response process. A passing unit-test suite alone is not a security audit.
