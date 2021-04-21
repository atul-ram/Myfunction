	
# Installing Pre-requiresites
To run tests locally, Pester PowersHell module must be installed as Local Admin. 
Make sure the installation does not touch the network drive, otherwise it might slow down PowerShell as a whole:
```
### open powershell 7 with admin access
$CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
$UserPSModuleLocation = "$HOME\Documents\WindowsPowerShell\Modules"
mkdir $UserPSModuleLocation
[Environment]::SetEnvironmentVariable("PSModulePath", $UserPSModuleLocation + [System.IO.Path]::PathSeparator + $CurrentValue, "Machine")
Find-Module -Name 'Pester' -MinimumVersion 5.1.0  -Repository 'PSGallery' | Save-Module -Path $UserPSModuleLocation
Import-Module -FullyQualifiedName "$UserPSModuleLocation\Pester"
```
