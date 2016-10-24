---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_install module
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 68e7ba36a723b0cb863ed890834855fa5f531240

---

# Install-Module

Installe les modules PowerShell à partir de référentiels en ligne sur l’ordinateur local.

## Description

L’applet de commande Install-Module télécharge un ou plusieurs modules à partir d’une galerie en ligne, les valide et les installe sur l’ordinateur local selon l’étendue d’installation spécifiée.

L’applet de commande Install-Module obtient un ou plusieurs modules qui répondent aux critères spécifiés à partir d’une galerie en ligne, vérifie que les résultats de la recherche sont des modules valides et copie les dossiers des modules à l’emplacement d’installation.

Quand aucune étendue n’est définie ou que la valeur du paramètre Scope est AllUsers, le module est installé dans %systemdrive%:\Program Files\WindowsPowerShell\Modules. Quand la valeur de Scope est CurrentUser, le module est installé dans $home\Documents\WindowsPowerShell\Modules.

Vous pouvez filtrer vos résultats selon les versions minimales et exactes des modules spécifiés.

- Prise en charge des versions côte à côte dans Windows PowerShell 5.0 ou version ultérieure
- Prise en charge de l’installation de dépendances de modules
- **Untrusted prompt :** (Invite pour les référentiels non approuvés) L’acceptation par l’utilisateur est obligatoire pour installer les modules à partir d’un référentiel non approuvé.
- -Force réinstalle le module installé
- RequiredVersion installe la version spécifiée côte à côte avec les versions existantes sur PowerShell versions 5.0 ou ultérieures.

### Étendue
Spécifie l’étendue d’installation du module. Les valeurs acceptables pour ce paramètre sont : AllUsers et CurrentUser.

L’étendue d’installation par défaut est AllUsers.

L’étendue AllUsers permet d’installer les modules à un emplacement qui est accessible à tous les utilisateurs de l’ordinateur, autrement dit $env:SystemDrive\Program Files\WindowsPowerShell\Modules.

L’étendue CurrentUser permet d’installer les modules uniquement dans $home\Documents\WindowsPowerShell\Modules, afin que le module ne soit disponible que pour l’utilisateur actuel.

## Remarques

Cette applet de commande s’exécute sur Windows PowerShell 3.0 ou versions ultérieures de Windows PowerShell, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.

Si un module installé ne peut pas être importé (autrement dit, s’il ne dispose pas d’un fichier .psm1, .psd1 ou .dll du même nom dans le dossier), l’installation échoue, sauf si vous ajoutez le paramètre Force à votre commande.

Si une version du module sur l’ordinateur correspond à la valeur spécifiée pour le paramètre Name et que vous n’avez pas ajouté le paramètre MinimumVersion ou RequiredVersion, Install-Module se poursuit de manière silencieuse sans installer ce module. Si les paramètres MinimumVersion ou RequiredVersion sont spécifiés et que le module existant ne correspond pas aux valeurs de ce paramètre, une erreur se produit. Pour être plus précis : si la version du module actuellement installé est inférieure à la valeur du paramètre MinimumVersion ou différente de la valeur du paramètre RequiredVersion, une erreur se produit. Si la version du module installé est supérieure à la valeur du paramètre MinimumVersion ou égale à la valeur du paramètre RequiredVersion, Install-Module se poursuit de manière silencieuse sans installer ce module.

Install-Module retourne une erreur s’il n’existe aucun module dans la galerie en ligne qui correspond au nom spécifié.

Pour installer plusieurs modules, spécifiez un tableau de noms de modules, séparés par des virgules. Vous ne pouvez pas ajouter MinimumVersion ou RequiredVersion si vous spécifiez plusieurs noms de modules.

Par défaut, les modules sont installés dans le dossier Program Files, afin d’éviter toute confusion quand vous installez les ressources DSC (Configuration de l’état souhaité) de Windows PowerShell. Vous pouvez diriger plusieurs objets PSGetItemInfo vers Install-Module ; il s’agit d’une autre façon de spécifier plusieurs modules à installer dans une seule commande.

Pour éviter d’exécuter des modules qui contiennent du code malveillant, les modules installés ne sont pas automatiquement importés par l’installation. Comme bonne pratique de sécurité, évaluez le code du module avant d’exécuter des applets de commande ou des fonctions dans un module pour la première fois.


## Syntaxe de l’applet de commande
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

## Référence de l’aide en ligne de l’applet de commande

[Install-Module](http://go.microsoft.com/fwlink/?LinkID=398573)

## Exemples de commandes

```powershell

# Install a module by name
Install-Module -Name MyDscModule

# Install multiple modules
Install-Module ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Module -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3

# Install the latest version of a module to $home\Documents\WindowsPowerShell\Modules.
Install-Module -Name ContosoServer -Scope CurrentUser

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -RequiredVersion 1.5

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -MinimumVersion 2.5

# Install multiple modules from multiple registered repositories
Install-Module ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a module with -WhatIf
Install-Module ContosoClient -WhatIf

# Install a module with -Confirm. A prompt will be displayed to confirm the installation.
Install-Module ContosoClient -WhatIf

# -Force option reinstalls the installed module
Install-Module ContosoClient -Force

# Install a module with dependencies
Install-Module -Name 
```

## Applet de commande Install-Module dans les opérations de pipeline

```powershell

# Find a module and install it
Find-Module -Name "MyDSC*" | Install-Module

# Find a module and install it to the CurrentUser scope
Find-Module -Name "MyDSC*" | Install-Module -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Module to install them.
# The second command uses Get-InstalledModule to verify the modules from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Module
Get-InstalledModule

# This command finds the resource named MyResource and passes it to the Install-Module cmdlet by using the pipeline operator. The Install-Module cmdlet installs the module for the resource. 
# If you pipe multiple resources to the Install-Module cmdlet from the same module, Install-Module attempts to install the module only once. 
Find-DscResource -Name "MyResource" | Install-Module
Get-InstalledModule

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Module
Get-InstalledModule

```

## Prise en charge des versions côte à côte sur PowerShell 5.0 ou version ultérieure

PowerShellGet assure la prise en charge des versions de modules côte à côte dans les applets de commande Install-Module, Update-Module et Publish-Module qui s’exécutent dans Windows PowerShell 5.0 ou versions ultérieures.

### Exemples Install-Module

```powershell
# Install a version of the module
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Install another version of the module in Side-by-Side with already installed version.
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Get all versions of an installed module
Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis... 
1.1.1      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...


```

## Installer un module avec ses dépendances

```powershell

# Find a module
Find-Module -Name TypePx -Repository PSGallery

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

# Find a module and its dependencies
Find-Module -Name TypePx -Repository PSGallery -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...

# Discover the dependencies list without adding -IncludeDependencies
$result = Find-Module -Name TypePx -Repository PSGallery
$result.Dependencies

Name                           Value
----                           -----
Name                           SnippetPx
CanonicalId                    powershellget:SnippetPx/#https://www.powershellgallery.com/api/v2/


# Now install the module along with its dependencies
Install-Module -Name TypePx -Repository PSGallery -Verbose

VERBOSE: Repository details, Name = 'PSGallery', Location = 'https://www.powershellgallery.com/api/v2/'; IsTrusted =
'False'; IsRegistered = 'True'.
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'PSGallery'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://www.powershellgallery.com/api/v2/' and PackageManagementProvider is
'NuGet'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'TypePx'.
VERBOSE: Performing the operation "Install-Module" on target "Version '2.0.1.20' of module 'TypePx'".

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
VERBOSE: The installation scope is specified to be 'AllUsers'.
VERBOSE: The specified module will be installed in 'C:\Program Files\WindowsPowerShell\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading module 'TypePx' with version '2.0.1.20' from the repository
'https://www.powershellgallery.com/api/v2/'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='SnippetPx'' for ''.
VERBOSE: InstallPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\SnippetPx\SnippetPx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'SnippetPx'.
VERBOSE: Hash for package 'SnippetPx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: InstallPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\TypePx\TypePx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'TypePx'.
VERBOSE: Hash for package 'TypePx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: Installing the dependency module 'SnippetPx' with version '1.0.5.18' for the module 'TypePx'.
VERBOSE: Module 'SnippetPx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18'.
VERBOSE: Module 'TypePx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\TypePx\2.0.1.20'.


# Get the installed modules
Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

```

## Scénarios d’erreur

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Module'
Install-Module ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Module'
Install-Module ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -MinimumVersion 2.0

```




<!--HONumber=Oct16_HO2-->


