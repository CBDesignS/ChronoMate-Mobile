# ChronoMate permanent Android signing setup

ChronoMate v0.4.0 begins a new permanent signing line. Every future APK must use the **same private key** or Android will refuse to install it as an update.

> The first move from any v0.3.x debug APK to v0.4.0 will require one final uninstall. After v0.4.0 is installed, later correctly signed builds can update it in place and retain app data.

## 1. Create the permanent keystore once

Run this on your own Windows computer in PowerShell or Command Prompt. `keytool` is included with a Java JDK.

```text
keytool -genkeypair -v -keystore ChronoMate-release.jks -alias chronomate -keyalg RSA -keysize 4096 -validity 10000
```

You will be asked for:

- a keystore password
- your certificate details
- a key password

Use a strong password and keep it in a password manager. The alias may remain `chronomate`.

Do **not** create another keystore for later versions. This one file is the permanent identity of the app.

## 2. Make protected backups immediately

Keep at least two private copies of:

- `ChronoMate-release.jks`
- keystore password
- key alias (`chronomate`, unless changed)
- key password

Suggested storage:

1. One encrypted password-manager or encrypted cloud-vault copy.
2. One offline copy on a USB drive kept safely away from the main computer.

Never put the keystore or passwords in the public GitHub repository, a release ZIP, an APK attachment, email, or ordinary unencrypted cloud folder.

If this keystore or its passwords are lost, future APKs cannot update the installed app.

## 3. Convert the keystore to Base64 for GitHub

From PowerShell, in the folder containing the keystore:

```powershell
[Convert]::ToBase64String([IO.File]::ReadAllBytes("ChronoMate-release.jks")) | Set-Clipboard
```

This copies the Base64 text to the clipboard. It is still secret signing material; treat it like the keystore itself.

## 4. Add four GitHub Actions secrets

In the GitHub repository, open:

`Settings` → `Secrets and variables` → `Actions` → `New repository secret`

Create exactly these secrets:

| Secret name | Value |
|---|---|
| `CHRONOMATE_KEYSTORE_BASE64` | Paste the Base64 text copied in step 3 |
| `CHRONOMATE_STORE_PASSWORD` | Keystore password |
| `CHRONOMATE_KEY_ALIAS` | `chronomate` unless another alias was chosen |
| `CHRONOMATE_KEY_PASSWORD` | Key password |

GitHub masks these values in normal workflow logs. The workflow reconstructs the keystore only inside the temporary build runner and does not upload it.

## 5. Build v0.4.0

Push the v0.4.0 files to `main`, or run the workflow manually from the repository's **Actions** tab.

The workflow now runs:

```text
gradle --no-daemon assembleRelease
```

and produces:

```text
ChronoMate-v0.4.0.apk
```

## 6. First-install and future-update rule

For the transition to the permanent key:

1. Export a backup from v0.3.3.
2. Uninstall v0.3.3.
3. Install the signed v0.4.0 APK.
4. Import the desktop or mobile backup.
5. Keep v0.4.0 installed.

For every later release:

- keep the package name `uk.co.cbdesigns.chronomate`
- increase `versionCode`
- use the same GitHub signing secrets
- never replace the permanent keystore

Android should then offer an in-place update and preserve ChronoMate data.

## Optional: verify APK signatures locally

With Android build tools installed:

```text
apksigner verify --print-certs ChronoMate-v0.4.0.apk
```

Record the SHA-256 certificate fingerprint. Every later official APK should show the same fingerprint.
