# WI Pass Product Definition

## Positioning

WI Pass is WI Arch's password manager and digital identity protection product. Its functional benchmark is Proton Pass: a cross-platform product that combines password management, encrypted vaults, autofill, passkeys, secure notes, identity and payment records, TOTP, sharing, and privacy tools.

WI Pass must be an original product. The reference is for feature and user-experience analysis only.

## Users

- Individuals managing personal credentials and identities.
- Families or trusted groups sharing selected credentials.
- Professionals and small teams that need controlled sharing and device management.
- WI Arch users who want a consistent privacy-focused identity tool.

## Core domains

### Credential management
Login records, website/app associations, password generation, custom fields, tags, favorites, history, and import/export.

### Encrypted vaults
Multiple vaults, folders, secure notes, payment cards, identities, encrypted metadata, offline access, and encrypted backups.

### Authentication helpers
TOTP, passkeys, security recommendations, password reuse/strength analysis, and later breach monitoring.

### Autofill and platform access
Browser extension, web app, desktop client, Android Autofill Framework integration, and iOS AutoFill Credential Provider extension.

### Sharing and collaboration
Secure item sharing, vault sharing, invitations, expiration, revocation, and permission management. Sharing must not require server-side decryption.

### Identity privacy
Hide-my-email aliases require an email forwarding/alias service and must be treated as a separate integration, not simulated by simply generating email strings.

## Product principles

- Privacy by design and data minimization.
- End-to-end encryption for all sensitive vault content and metadata.
- No server-side plaintext access to vault contents.
- Clear security states and transparent user controls.
- Offline-first access with safe encrypted synchronization.
- Accessible, consistent, cross-platform user experience.
- Honest feature status and security claims.

## MVP boundary

The first usable release should focus on a secure local vault, login entries, secure notes, password generation, lock/unlock, encrypted export/backup, and a tested cryptographic protocol. Cloud sync and autofill follow only after the key-management design is reviewed.

## Non-goals for the first release

- Building an email provider or mail client.
- Replacing an identity provider or enterprise SSO platform.
- Acting as a payment processor.
- Claiming dark-web monitoring without a reliable breach-data provider and privacy review.
- Implementing cryptographic primitives from scratch.
