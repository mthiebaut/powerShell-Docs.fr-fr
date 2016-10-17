# Get-InstalledScript

Obtient les scripts installés sur un ordinateur.

## Description

L’applet de commande Get-InstalledScript obtient les scripts PowerShell installés sur un ordinateur.

Pour chaque script installé, Get-InstalledScript retourne un objet PSRepositoryItemInfo qui peut éventuellement être transmis à Uninstall-Script pour désinstaller les scripts installés.

- Get-InstalledScript peut filtrer les scripts installés selon le nom ou les paramètres de version.
- Get-InstalledScript permet de filtrer avec des paramètres de version : MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Ces paramètres sont mutuellement exclusifs, sauf MinmimumVersion et MaximumVersion.
  - Ces paramètres de version sont autorisés uniquement avec le nom de script unique sans les caractères génériques.
  - Si le paramètre RequiredVersion n’est pas spécifié, Get-InstalledScript retourne la dernière version du script installé qui est supérieure ou égale à la version minimale spécifiée ou la dernière version du script si aucune version minimale n’est spécifiée. 
  - Si le paramètre RequiredVersion est spécifié, Get-InstalledScript retourne uniquement la version du script installé qui correspond exactement à la version spécifiée.

## Syntaxe de l’applet de commande

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## Référence de l’aide en ligne de l’applet de commande

[Get-InstalledScript](http://go.microsoft.com/fwlink/?LinkId=619790)

## Exemples de commandes

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```

<!--HONumber=Aug16_HO3-->


