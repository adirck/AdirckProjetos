# Rocha DNS & Task Defender

Developed by **Alexandre Rocha**. Windows desktop application for local HOSTS and IPv4 DNS monitoring, backups, anomaly notices and manual review of scheduled tasks. Version 2.0.0, 2026-11-01.

**Distribution model:** public compiled binaries; private source code. The public ZIP intentionally contains no `.ps1` or `.cs` files. Implementation resources are embedded inside .NET executables. This reduces casual access to scripts but does not prevent reverse engineering. Do not publish the private source archive if you want the implementation to remain private.

## Install

1. Test in a disposable Windows 10/11 VM before deployment. Requires Windows PowerShell 5.1 and .NET Framework 4.8. These Windows components are used in-process; PowerShell 7 is not the runtime.
2. Uninstall the older **Soma Defender** first if present. Do not run both monitors together. Their logs and backups remain in the old profile folder.
3. Extract the complete public ZIP and run **Setup.exe** as administrator. Keep all distribution files together.
4. Choose **Português (Brasil), English (United States), Español or 日本語**. Labels, menus, editor and uninstaller use that language. Native Windows dialogs and underlying operating-system errors may follow the Windows language.
5. Read and accept the protection policy. Configure the notice title, message, optional support contact and QR attachment. Live preview updates while typing; **Preview window** opens the real notice without monitoring or repairs.
6. Save to complete installation. Cancelling the editor before saving cancels the installation before copying files or creating startup tasks. The optional developer donation window is shown after installation; donating is never required.

Installed folder: `%ProgramFiles%\RochaDefender`. Settings, the editor and the uninstaller are there. Start Menu shortcuts and Windows Installed Apps also provide access. The folder is restricted to administrator/System writes; standard users have read/execute permission. The app requests administrator elevation.

The task **RochaDefender-Monitor** starts the installed app immediately and at subsequent logins **of the administrator account that installed it**. It is not a Windows service and does not run before login or automatically for other users. If another administrator supplies elevation credentials, the task belongs to that account. Standard-user deployments require a separate service/session architecture; this version does not implement that.

## Icon and operation

The notification-area icon shows **A.R** and a colored indicator:

- Green: a completed monitoring cycle found no pending condition.
- Yellow: checking, paused, or not yet started. The tooltip distinguishes these states.
- Red: anomaly, remaining HOSTS evidence, unacknowledged notice or a failed operation.

Right-click for Open, Enable, Pause, Message editor, Developer tip jar and **Exit**, in the installed language. Double-click opens the window. Closing or minimizing hides the main window and keeps the app alive. **Exit** stops the monitor until it is reopened or the configured user logs in again. A manual launch starts paused: enable monitoring explicitly. Only the scheduled startup uses automatic mode.

## Protection policy

- Polls every 15 seconds plus processing/backup time. Transient changes between polls may be missed.
- IPv4 DNS must be exactly **8.8.8.8, 8.8.4.4** in that order. Different, empty or reordered settings cause backup, attempted repair and the single anomaly notice, even without any `hosts_old_*` file. Newly enumerated interfaces are checked too. A failure is logged and shown, never treated as successful repair.
- Covers IPv4 interfaces exposed by Windows, including Ethernet, Wi-Fi, VPN, virtual adapters and Bluetooth PAN. A Bluetooth radio without a network interface has no DNS settings. Disabled adapters are not enabled; disconnected/managed interfaces may reject changes.
- Does not change IPv6, browser secure DNS, proxies or corporate policy. Public DNS may break internal domain resolution.
- Initial HOSTS mappings are backed up and renamed `hosts_old_DDMMYYYY`, then a clean extensionless `hosts` is created. Legitimate entries are removed too. Later content changes, including comments, trigger the same operation against the saved SHA256 baseline. Name collisions receive a unique suffix.
- Any `hosts_old_*` in `%SystemRoot%\System32\drivers\etc` keeps the notice recurring every 60 seconds. Closing the notice does not clear that marker. IT should analyze and move all markers to evidence storage. Backup copies elsewhere do not trigger this rule.
- Missing HOSTS, permission errors or failed backups produce failures. An operation is blocked if its backup fails. This is not proof that every anomaly was caused by malware.
- Scheduled tasks are inventoried. Disabling requires an exact task identity, a matching known command fragment and confirmation. Tasks are not indiscriminately deleted; running processes are not terminated by this feature.

## Custom notice and QR attachments

Open **MessageEditor.exe** in the installed folder, use the Start Menu shortcut or the tray menu. Administrator permission is required. Customize title, body, contact and QR image, then save. Subsequent notices read the saved settings; an already open notice retains its current text until reopened.

Accepted attachments: **PDF, PNG, JPG/JPEG, BMP, GIF and TIFF**. PDFs use the **first page only**, rendered locally with the Windows PDF API. Animated/multipage images use the frame loaded by Windows imaging. The imported attachment is normalized to `notice-qr.png`; it is not generated from the contact field. Files up to 25 MB and decoded dimensions up to 10000 pixels are accepted. Password-protected/invalid PDFs or unsupported images may fail; check the preview. The software does not validate that the attachment contains a QR code or that its payment/link destination is trustworthy.

No built-in support phone or QR from the former store-specific version is included. Contact information is optional. No message or telemetry is automatically sent. QR links are opened only by the person scanning them.

## Developer tip jar

Shown after installation and available from the app/tray. Donation data is embedded in the product, separate from editable anomaly settings:

- Pix: `alexandre.dirck@gmail.com`
- Banco Santander (Brasil) S.A., branch `1071`, checking account `01011741-4`
- SWIFT/BIC: `BSCHBRSP`

Donations are voluntary. Confirm the recipient in your banking app. International transfers require complete beneficiary details and the appropriate correspondent-bank instructions for the currency; SWIFT alone is insufficient. No beneficiary address, IBAN or bank intermediary has been invented. Official reference, checked 2026-11-01: https://www.santander.com.br/cambio/transferencia-internacional/

The editor cannot change donation data. Like any client software, however, these resources cannot be guaranteed immutable against someone who modifies or reverse engineers the binary with administrative access.

## Uninstall and evidence

Run **Uninstall.exe** in the installed folder, use its localized Start Menu shortcut or Windows Installed Apps, and confirm the localized prompt. It removes its own startup task, installed app processes, known binaries, resources, shortcuts and registry entry. Unknown files are preserved for review. A temporary uninstall helper is scheduled for deletion on reboot.

**Preserved:** notice settings, the attached QR, logs/backups, `hosts_old_*`, current HOSTS and current DNS configuration. DNS is not automatically rolled back. The install folder may remain because personal settings are deliberately retained. Stop monitoring before restoring earlier network settings or they will be reapplied.

Logs and backups: `%LOCALAPPDATA%\RochaDefender` of the executing account. `audit.jsonl` records actions, timestamps and errors. Backups include HOSTS, ACLs, DNS per interface, TCP/IP values, task XML and hashes. They may contain internal data and are not tamper-proof. Frequent incidents can consume disk space; set an IT retention process.

## Security and limits

Compiled packaging is not encryption, anti-reverse-engineering or protection against a local administrator. No kernel driver, self-protection service or tamper-proof audit is included. The requested **Exit** menu deliberately allows monitoring to be stopped. This is a local repair utility, not a complete endpoint security product.

Release executables are currently **unsigned**. SHA256 checksums support integrity checking against a trusted copy but do not identify the publisher. Obtain an Authenticode certificate and sign verified releases before broad distribution. Do not put private keys, passwords, personal configuration, logs or incident evidence in a public repository.

## Private development

Keep source private. On Windows PowerShell 5.1:

```powershell
powershell.exe -NoProfile -STA -ExecutionPolicy RemoteSigned -File .\Test.ps1
powershell.exe -NoProfile -ExecutionPolicy RemoteSigned -File .\Build.ps1
```

`Build.ps1` embeds implementation scripts into executables using the framework compiler and an administrator manifest. `app\settings.example.json` is a neutral schema; actual `settings.json`, imported QR and logs are not public source assets.

Validated locally: complete four-language dictionaries, language picker, localized main windows and editor, actual preview button, save/attachment round-trip in temporary fixtures, QR PDF first-page import, tray state transitions/hide/reopen, and mocked HOSTS/DNS repairs including Bluetooth, new interfaces, marker recurrence, partial failures and backup gates. The installation, uninstallation, administrator repairs and startup after reboot still need VM acceptance testing. Japanese output renders correctly here; a native-language review remains advisable.

## VM acceptance checklist

1. Snapshot VM; record original HOSTS/DNS and ensure the selected policy is suitable.
2. Install in each language; verify cancellation and successful custom-message save, startup task, folder permissions, shortcuts and Installed Apps entry.
3. Attach a real QR as PDF and image; test live preview, full-window preview, changed text and reopening the editor.
4. Change HOSTS and DNS on multiple IPv4 adapters. Verify backup, repair, the single notice and red status. Close the notice, test recurrence with HOSTS markers and remove markers after IT review.
5. Test Pause/Enable/Exit, login restart under the configured account and failure on a restricted adapter.
6. Uninstall from the localized shortcut and Installed Apps; verify no startup task or app processes remain and evidence/settings are retained.

This project has not been assigned an open-source license. Public distribution is intended for compiled releases; keep the separate source archive private.
