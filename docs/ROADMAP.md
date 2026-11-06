# WI Pass Roadmap

This roadmap describes intended work, not completed functionality.

## Phase 0 — Product and security foundation
- [ ] Confirm requirements, supported platforms, and release boundaries.
- [ ] Threat model covering endpoint compromise, malicious browser pages, server compromise, account takeover, sync attacks, sharing abuse, backups, and recovery.
- [ ] ADR: vault key hierarchy and client-side encryption protocol.
- [ ] ADR: authentication, account recovery, and device enrollment.
- [ ] ADR: encrypted sync, conflict resolution, and revocation.
- [ ] ADR: sharing and recipient key exchange.
- [ ] Security baseline adoption and CI security gates.
- [ ] UI design system and synthetic-data prototype.

## Phase 1 — Secure local vault MVP
- [ ] Secure lock/unlock flow.
- [ ] Encrypted local vault storage.
- [ ] Login and secure-note item types.
- [ ] Password/passphrase generator.
- [ ] Encrypted export and verified restore.
- [ ] Cross-client cryptographic test vectors.
- [ ] Security-focused tests for tampering, malformed payloads, and data leakage.

## Phase 2 — Accounts and encrypted synchronization
- [ ] Account and device registration.
- [ ] Encrypted payload synchronization.
- [ ] Offline queue and conflict handling.
- [ ] Device list, session control, and device revocation.
- [ ] Server-side verification that stored payloads are opaque ciphertext.

## Phase 3 — Autofill and platform clients
- [ ] Browser extension with origin verification.
- [ ] Web vault application.
- [ ] Desktop application.
- [ ] Android Autofill Framework integration.
- [ ] iOS AutoFill Credential Provider extension.
- [ ] Permission and phishing-resistance testing.

## Phase 4 — Identity and authentication tools
- [ ] Payment cards and personal identities.
- [ ] TOTP authenticator.
- [ ] Passkey integration.
- [ ] Password health and reuse checks.
- [ ] Import/export from supported password managers.

## Phase 5 — Sharing and advanced privacy
- [ ] Secure single-item sharing.
- [ ] Shared vaults and role-based access.
- [ ] Expiring links and revocation.
- [ ] Email alias provider integration.
- [ ] Breach monitoring integration.
- [ ] Encrypted attachments and emergency access.

## Release gate

No production release until the threat model, cryptographic design, recovery flows, cross-platform test vectors, dependency review, incident response, and independent security assessment have been completed.
