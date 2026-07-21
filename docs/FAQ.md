# ChronoMate 2026 Frequently Asked Questions

This document answers the most common questions about using ChronoMate 2026.

For detailed information, please refer to the User Guide and other documentation included with the project.

---

## What is ChronoMate?

ChronoMate is a lightweight, offline chronograph recording application designed specifically for air rifles.

It records chronograph sessions, calculates muzzle energy, stores rifle and pellet information, and generates professional printable reports.

---

## Does ChronoMate need to be installed?

No.

ChronoMate is completely portable.

Simply extract the release archive and open **ChronoMate.html** using a supported desktop browser.

No files are installed into Windows.

No registry entries are created.

---

## Does ChronoMate require an internet connection?

No.

ChronoMate runs entirely offline.

All calculations, reports and user data remain on your computer.

---

## Which browsers are supported?

ChronoMate has been tested using:

- Mozilla Firefox
- Microsoft Edge
- Brave Browser

Modern desktop browsers should work correctly.

---

## Does ChronoMate work on Android or iPhone?

Not currently.

Modern mobile operating systems restrict locally opened HTML applications from loading linked JavaScript, CSS and image files correctly.

ChronoMate is designed for desktop browsers.

---

## Where is my data stored?

ChronoMate stores user data locally within your browser.

This includes:

- Application settings
- Saved rifle profiles
- User pellets
- Session information (tester, chronograph and notes)

The built-in pellet database (.177, .22 and .25) forms part of the application itself.

---

## How do I update ChronoMate without losing my data?

Before updating:

1. Select **Export Data**.
2. Save your backup file.
3. Replace the application files with the new release.
4. Select **Import Data** to restore your data.

---

## Can I add my own pellets?

Yes.

ChronoMate supports user-created pellets which are stored separately from the built-in pellet database.

This ensures future application updates never overwrite your own pellet information.

---

## Can I edit the built-in pellet database?

The built-in pellet database is maintained as part of ChronoMate.

Users wishing to record additional pellets should use the User Pellet feature.

Future ChronoMate releases may expand the built-in database.

If you find a pellet that is not included in the built-in database, please let me know. The database will continue to grow through future ChronoMate updates.

---

## Can I save more than one rifle?

Yes.

ChronoMate supports multiple saved rifle profiles.

These are automatically included when creating a backup.

---

## Can I print or save reports?

Yes.

Reports are designed for landscape printing.

Most desktop browsers also allow reports to be saved directly as PDF files using the browser's Print function.

---

## Is a ChronoMate report an official certificate?

No.

ChronoMate reports are intended as personal chronograph records only.

They are not official certification documents and should not be treated as legal proof of compliance.

---

## Will ChronoMate continue to receive updates?

Yes.

Version 1.0.0 marks the completion of the original project scope.

Future releases will focus on:

- Built-in pellet database expansion.
- Bug fixes.
- Long-term maintenance.

New functionality will only be added where it clearly improves the recording, reporting or management of chronograph sessions while preserving ChronoMate's lightweight design philosophy.


---

Android Debug

if a user has task kill on exit enabled then ChronoMate will have problems with importing & exporting user Backup files.
the nature of a backup & import is to kill the current task to open the file picker, do the task then once complete restart ChronoMate,
this breaks ChronoMate by killing the current task it was busy doing so when the ChronoMate task is restated it has no idea what it was doing so will instantly fail.

Any android crashes and bugs should be filed with a debug log zip archive that was taken after the crash occured and will require steps that were taken to produce
the crash/bug on your device. WE only have access to a couple of Android devices so can not test on every item of Hardware in use.

---

## Where can I find more information?

The complete ChronoMate documentation is included with the project.

See:

- Installation Guide
- User Guide
- Backup & Restore Guide
- Changelog

---

## Documentation Pages

← [Backup & Restore](BACKUP.md)

↑ [Project README](../README.md)

→ [Changelog](CHANGELOG.md)

Doc Version 1.0.0
