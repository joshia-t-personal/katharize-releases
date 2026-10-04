# Katharize

Katharize is a disk cleanup tool for Windows. It reads the whole drive, works out what each large folder is
(caches, build output, app data, games and so on), and shows what deleting it would cost you before you delete
anything.

This repository has the downloads only. Get the latest `Katharize.exe` from
[Releases](https://github.com/joshia-t-personal/katharize-releases/releases/latest).

## Running it

1. Download `Katharize.exe` and put it in any folder. It is the whole app: nothing to install, and no .NET
   runtime needed.
2. Double-click it.
3. **Windows asks for administrator permission once each time you start it.** Katharize needs it to read the
   drive's file table (the NTFS master file table), which is much faster than walking every folder. The window
   itself does not run as administrator.

The first start takes longer: Katharize scans the whole drive once. Later starts load the saved index and only
catch up on what changed.

### "Windows protected your PC"

The exe is not code-signed yet, so SmartScreen may warn about an unknown publisher. Click **More info**, then
**Run anyway**. You can check that your download matches the release by comparing its SHA-256 hash, listed in
the release notes, with:

```powershell
Get-FileHash .\Katharize.exe -Algorithm SHA256
```

## Requirements

- Windows 10 or 11, 64-bit (x64).
- An NTFS drive. Other formats (exFAT, FAT32) are listed but can't be read.

## Where it keeps its files

Everything Katharize saves is in `%LOCALAPPDATA%\Katharize`: the drive index, your Smart Folders sections, logs,
and a log of every cleanup run. To remove Katharize completely, delete the exe and that folder.
