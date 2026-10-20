# Privacy and local storage

Catter 0.7 introduces an invitation-based access service. It does not collect location history or Apple credentials. This describes the new implementation, not the independent behavior of Apple, Cloudflare, LocalDevVPN or other apps. Earlier builds have no invitation service.

## Invitation access

The owner-operated Cloudflare service stores invitation labels, hashed invitation codes and device credentials, expiry/revocation state, activation times and last successful access-check times. Labels are supplied by the owner. The app sends its random device credential and licence ID over HTTPS; no hardware serial number or coordinates are sent to this service. A successful check is evidence of a device check-in, not a count of people actively using the app.

Installer invitation codes stay in process memory until sign-out or closure. The iPhone stores a random credential and licence ID in a non-migrating Keychain entry, which may survive app reinstallation under the same signing identity. Access checks require internet; expiry/revocation blocks new simulation commands, but not Restore.

The service stores an hourly salted IP-address hash for rate limiting for up to approximately three hours. Cloudflare independently processes network metadata. Invitation records remain until the owner deletes them from the database. Contact the owner for removal. Owner keys are held in dashboard tab memory, never browser local storage.

## Apple sign-in

The desktop backend authenticates with Apple. Passwords, verification codes, account tokens and pending challenges are held in memory. The UI clears password input after submission. Normal close/sign-out clears the account store; startup removes legacy disk sessions before reading account state.

Closing during signing/preparation is blocked until the operation finishes. Local logout does not revoke Apple's server-side sessions, remove Apple's device-list entries or guarantee a new verification-code challenge. Apple decides when a code is required.

Memory-only storage is not a promise of secure erasure from RAM, swap or crash dumps.

## Data retained locally

- **iPhone:** protected pairing records, cached developer images, background-monitoring preference and unresolved-simulation flag. No location-history file is recorded.
- **Windows:** signing keys/certificates, phone pairing backups and anisette provisioning state under `%LOCALAPPDATA%\CatterInstaller`. Existing installations may retain the legacy `GhostlyInstaller` directory. Files are protected using Windows account permissions.
- **macOS:** equivalent setup data under `~/Library/Application Support/CatterInstaller`, with an owner-only directory and restrictive file-creation permissions.
- **Runtime packages:** Windows extracts its bundled runtime under `%LOCALAPPDATA%\CatterSetup`; macOS bundles it inside the setup app. These packages are separate from account and phone secrets.

Do not upload private setup folders, pairing files, signing keys or account diagnostics. Restoring location does not delete preparation data. Deleting the iPhone app removes its local pairing; updating over it with the same signing identity preserves it.

## Network access

Apple sign-in/provisioning requests are made by the bundled signing engine. Apple Maps search and map tiles use Apple's services. Developer images and installer dependencies require downloads.

The anisette component also downloads provisioning libraries from a third-party HTTPS host. Its persisted device-provisioning state is separate from the Apple login session. Do not describe all installer traffic as Apple-only.

The signing engine's compatibility client metadata can appear as a generic Windows device in Apple account information, including when used on a Mac. It is not the connected iPhone's hardware identity.

## Security boundaries

The interface/backend communicate through inherited process pipes. IPA validation checks identity, paths, duplicates and unsafe archive entries; signing uses a private snapshot and checks its digest. Matching the expected bundle ID is not proof of publisher authenticity.

Certificate replacement requires review and explicit confirmation. Revocation may affect other sideloaded apps. Pairing backups are verified before transfer.

These controls have targeted regression tests. They are not an independent security audit or a guarantee that dependencies have no vulnerabilities. See [security reporting](SECURITY.md).
