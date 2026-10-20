<p align="center">
  <img src="Branding/Catter.png" width="160" height="160" alt="Catter logo">
</p>
<h1 align="center">Catter</h1>
<p align="center"><strong>Your phone. Your location.</strong></p>
<p align="center">An iPhone location simulator with guided Windows and macOS setup.</p>
<p align="center">
  <a href="https://github.com/diwasupadhyay/catter/releases">Official downloads</a> &middot;
  <a href="#getting-started">Getting started</a> &middot;
  <a href="docs/PRIVACY.md">Privacy</a>
</p>

## Downloads

**Coming soon.** Invitation access is being tested; no approved release is available yet. iPhone, Windows and macOS packages will appear on the [Releases page](https://github.com/diwasupadhyay/catter/releases).

This is Catter's official download and support repository. Development is maintained separately. There is nothing to compile here.

## Choose your location

Search for a place, pick a point on the map or enter coordinates. Confirm **Set location** to send it to your iPhone's developer service, or **Restore real location** to stop simulation.

The desktop installer guides you through Apple signing, installation, pairing and developer-image preparation. After preparation, the computer can be disconnected.

## Getting started

| Requirement | Details |
| --- | --- |
| iPhone | iOS 18+ deployment target; supported device/version combinations will be listed with each tested release. |
| Setup computer | Windows 11 with Apple Devices/iTunes drivers, or macOS 13+ with the matching Apple Silicon/Intel package. |
| Catter invitation | Required for upcoming builds. One iPhone per code; six days from first use in setup or the app. |
| Apple Account | Free-account installs require manual reinstallation every seven days. |
| Developer Mode | Enable it and approve the phone's Trust prompts when asked. |
| LocalDevVPN and Wi-Fi | Install LocalDevVPN separately and connect the phone to an active Wi-Fi network. Cellular-only developer connections are currently unresolved. |

1. Download the installer for your computer and the unsigned Catter IPA from the same official release.
2. Open the installer, sign in with Apple and select the IPA. Enter your Catter invitation when asked. Connect one unlocked iPhone by USB.
3. Follow the prompts. If Developer Mode requires a restart, keep the installed app, unlock the phone and select **Continue preparation**.
4. Connect LocalDevVPN and Wi-Fi on the phone. Open Catter, activate the same code in **Settings > Your access**, choose a place and confirm **Set location**.
5. Check the result in another app. Use **Restore real location** when finished and verify your actual position.

Apple requests a verification code when required. Install updates over the existing app with the same Apple Account to preserve pairing. There is no automatic renewal.

Windows users run `CatterInstaller.exe`. Mac users extract the matching archive and move **Catter Setup.app** to Applications. Python and Sideloadly are not required. Packages are not publisher-signed/notarized, so platform warnings may appear; do not disable system security globally.

macOS builds will be labelled as a preview until physical-device testing is confirmed.

## What to expect

- iOS may interrupt background work; a simulated location is not guaranteed to persist indefinitely while locked.
- Check results in other apps. A successful command does not verify what every app displays.
- Find My may show the correct position without an address label; Catter cannot force its address lookup or server refresh.

## Privacy and support

Upcoming Catter builds use an owner-operated invitation service, recording activation and last-check-in times without collecting locations or Apple credentials. Access is checked over the internet; Restore remains available after expiry. Apple sessions are held in memory and cleared on sign-out or normal closure. Private pairing credentials, signing material and cached preparation files remain locally for reuse. See [privacy details](docs/PRIVACY.md).

Report ordinary problems through [Issues](https://github.com/diwasupadhyay/catter/issues). Never attach passwords, verification codes, pairing files or signing keys. For security issues, follow [security reporting](docs/SECURITY.md).

Required third-party notices and applicable corresponding-source materials will accompany releases. This download repository does not replace dependency license obligations. Catter is independent and is not affiliated with Apple or LocalDevVPN.
