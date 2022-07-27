# Remove preinstalled apps or bloatwares apps from Windows 10 or Windows 11


##Remove All Apps : 
```
Get-AppxPackage -allusers | Remove-AppxPackage
```


##Restore All Apps : 
```
Get-AppxPackage -AllUsers| Foreach {Add-AppxPackage -DisableDevelopmentMode -Register “$($_.InstallLocation)\AppXManifest.xml”}
```

##Restore Specific Apps : 

###Microsoft.WindowsStore
```
Get-AppxPackage -allusers Microsoft.WindowsStore | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

###Microsoft.WindowsCalculator
```
Get-AppxPackage -allusers Microsoft.WindowsCalculator | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

###Microsoft.Windows.Photos
```
Get-AppxPackage -allusers Microsoft.Windows.Photos | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```



## Remove Node Modules folder from all folders
```
npx rimraf ./**/node_modules
```
