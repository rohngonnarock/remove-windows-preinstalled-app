# Remove preinstalled apps or bloatwares apps from Windows 10 or Windows 11

## List All Preinstalled Apps :
```
Get-AppxPackage -allusers | findstr "^Name"
```

## Remove All Apps : 
```
Get-AppxPackage -allusers | Remove-AppxPackage
```


## Restore All Apps : 
```
Get-AppxPackage -AllUsers| Foreach {Add-AppxPackage -DisableDevelopmentMode -Register “$($_.InstallLocation)\AppXManifest.xml”}
```

## Restore Specific Apps : 

### Microsoft.WindowsStore
```
Get-AppxPackage -allusers Microsoft.WindowsStore | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

### Microsoft.WindowsCalculator
```
Get-AppxPackage -allusers Microsoft.WindowsCalculator | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

### Microsoft.Windows.Photos
```
Get-AppxPackage -allusers Microsoft.Windows.Photos | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```


### Common apps
```
# Microsoft Store (required for installs/updates)
Get-AppxPackage -allusers Microsoft.WindowsStore | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# App Installer (winget - VERY important)
Get-AppxPackage -allusers Microsoft.DesktopAppInstaller | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Windows Terminal (best CLI)
Get-AppxPackage -allusers Microsoft.WindowsTerminal | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Notepad
Get-AppxPackage -allusers Microsoft.WindowsNotepad | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Calculator
Get-AppxPackage -allusers Microsoft.WindowsCalculator | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Windows Subsystem for Linux (WSL)
Get-AppxPackage -allusers MicrosoftCorporationII.WindowsSubsystemForLinux | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Dev Home (optional but useful for dev environments)
Get-AppxPackage -allusers Microsoft.Windows.DevHome | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Photos (image viewer)
Get-AppxPackage -allusers Microsoft.Windows.Photos | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# HEIF (iPhone images)
Get-AppxPackage -allusers Microsoft.HEIFImageExtension | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# HEVC (important for modern videos)
Get-AppxPackage -allusers Microsoft.HEVCVideoExtension | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# RAW image support
Get-AppxPackage -allusers Microsoft.RawImageExtension | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# WebP support
Get-AppxPackage -allusers Microsoft.WebpImageExtension | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# AV1 / VP9 codecs
Get-AppxPackage -allusers Microsoft.AV1VideoExtension | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
Get-AppxPackage -allusers Microsoft.VP9VideoExtensions | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Intel Graphics (keep if Intel GPU)
Get-AppxPackage -allusers AppUp.IntelGraphicsExperience | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Thunderbolt (only if supported)
Get-AppxPackage -allusers AppUp.ThunderboltControlCenter | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Print dialog (safe system utility)
Get-AppxPackage -allusers Windows.PrintDialog | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Phone Link
Get-AppxPackage -allusers Microsoft.YourPhone | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Camera
Get-AppxPackage -allusers Microsoft.WindowsCamera | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# Sticky Notes
Get-AppxPackage -allusers Microsoft.MicrosoftStickyNotes | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# To Do
Get-AppxPackage -allusers Microsoft.Todos | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

winget install Microsoft.Notepad
winget install Microsoft.Paint
winget install WhatsApp.WhatsApp
winget install Git.Git
winget install Python.Python.3.12
winget install Docker.DockerDesktop
winget install Microsoft.VisualStudioCode
```



## Remove Node Modules folder from all folders
```
npx rimraf ./**/node_modules
```
