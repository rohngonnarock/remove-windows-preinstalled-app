# Remove Preinstalled Apps from Windows 10/11

A comprehensive guide for managing Windows preinstalled apps and bloatware. This repository contains PowerShell commands to list, remove, and restore Windows Store applications.

## ⚠️ Important Warnings

- **Run PowerShell as Administrator** before executing any commands
- **"Remove All Apps" is destructive** - use with caution and prefer selective removal instead
- **Back up your system** before bulk removing apps
- Some apps may be required for system functionality

## Table of Contents

- [Quick Commands](#quick-commands)
- [Detailed Restore Options](#detailed-restore-options)
- [Recommended App Restoration](#recommended-app-restoration)
- [Additional Setup](#additional-setup)

---

## Quick Commands

### List All Preinstalled Apps
View all currently installed Store apps:
```powershell
Get-AppxPackage -allusers | findstr "^Name"
```

### Remove All Apps (⚠️ Use with Caution)
Remove all preinstalled Store apps at once:
```powershell
Get-AppxPackage -allusers | Remove-AppxPackage
```

### Restore All Apps
Restore all previously installed Store apps:
```powershell
Get-AppxPackage -AllUsers | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

---

## Recommended App Restoration

### Essential System Apps
These apps are highly recommended for most users:

```powershell
# Microsoft Store (required for installs/updates)
Get-AppxPackage -allusers Microsoft.WindowsStore | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# App Installer (winget - essential for package management)
Get-AppxPackage -allusers Microsoft.DesktopAppInstaller | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Windows Terminal (modern command line)
Get-AppxPackage -allusers Microsoft.WindowsTerminal | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Notepad (basic text editor)
Get-AppxPackage -allusers Microsoft.WindowsNotepad | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Calculator (system calculator)
Get-AppxPackage -allusers Microsoft.WindowsCalculator | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Windows Subsystem for Linux (required if using WSL)
Get-AppxPackage -allusers MicrosoftCorporationII.WindowsSubsystemForLinux | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

### Developer-Friendly Apps
Useful for development environments:

```powershell
# Dev Home (helpful for developer environments)
Get-AppxPackage -allusers Microsoft.Windows.DevHome | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Camera (system camera access)
Get-AppxPackage -allusers Microsoft.WindowsCamera | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

### Media & Codec Support
Important for handling various file formats:

```powershell
# Photos (image viewer)
Get-AppxPackage -allusers Microsoft.Windows.Photos | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# HEIF (iPhone and modern image format support)
Get-AppxPackage -allusers Microsoft.HEIFImageExtension | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# HEVC (modern video codec - recommended)
Get-AppxPackage -allusers Microsoft.HEVCVideoExtension | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# RAW Image Support (for photographers)
Get-AppxPackage -allusers Microsoft.RawImageExtension | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# WebP Image Support
Get-AppxPackage -allusers Microsoft.WebpImageExtension | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# AV1 / VP9 Codecs (modern video compression)
Get-AppxPackage -allusers Microsoft.AV1VideoExtension | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
Get-AppxPackage -allusers Microsoft.VP9VideoExtensions | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

### Hardware & System Support
Keep these only if applicable to your hardware:

```powershell
# Intel Graphics (keep if using Intel GPU)
Get-AppxPackage -allusers AppUp.IntelGraphicsExperience | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Thunderbolt (only if your device supports Thunderbolt)
Get-AppxPackage -allusers AppUp.ThunderboltControlCenter | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Print Dialog (safe system utility)
Get-AppxPackage -allusers Windows.PrintDialog | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

### Productivity & Communication
Optional but useful applications:

```powershell
# Phone Link (connect to your phone)
Get-AppxPackage -allusers Microsoft.YourPhone | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Sticky Notes (simple note-taking)
Get-AppxPackage -allusers Microsoft.MicrosoftStickyNotes | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# To Do (task management)
Get-AppxPackage -allusers Microsoft.Todos | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

---

## Additional Setup

### Useful Applications via winget

Install popular third-party applications:

```powershell
winget install --id 9PCFS5B6T72H -e --source msstore
winget install --id 9NKSQGP7F2NH -e --source msstore
winget install Docker.DockerDesktop
winget install Microsoft.VisualStudioCode
winget install Inkscape.Inkscape
winget install Google.Chrome
winget install 7zip.7zip
winget install VideoLAN.VLC
winget install Google.GoogleDrive
winget install Microsoft.PowerShell
winget install qBittorrent.qBittorrent
winget install NordSecurity.NordVPN
winget install Anthropic.Claude
winget install Adobe.Acrobat.Reader.64-bit
```

### Git Configuration

Set up Git with your credentials:

```powershell
git config --global user.email "rohngonnarock@gmail.com"
git config --global user.name "Rahul Prajapati"
```

### Node.js Utilities

Remove node_modules folders from all subdirectories:

```powershell
npx rimraf ./**/node_modules
```

---

## Notes

- Always run PowerShell commands as **Administrator**
- Test commands on a non-critical system first
- Some system functionality depends on certain apps—be selective with removals
- You can restore apps individually without restoring all of them
