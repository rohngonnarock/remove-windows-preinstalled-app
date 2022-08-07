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
Get-AppxPackage -allusers Microsoft.WindowsStore | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
Get-AppxPackage -allusers Microsoft.Windows.Photos | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
Get-AppxPackage -allusers Microsoft.WindowsCalculator | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
Get-AppxPackage -allusers AppUp.ThunderboltControlCenter | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
Get-AppxPackage -allusers AppUp.IntelGraphicsExperience | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
Get-AppxPackage -allusers Microsoft.YourPhone | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
Get-AppxPackage -allusers Microsoft.WindowsCamera | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```



## Remove Node Modules folder from all folders
```
npx rimraf ./**/node_modules
```
