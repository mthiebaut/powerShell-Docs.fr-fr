---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-Script
ms.openlocfilehash: df62a9934d8013d37bd0083c03f90fa7fa05ac0c
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="find-script"></a>Find-Script

Recherche les fichiers de script PowerShell à partir d’une galerie en ligne qui correspondent aux critères spécifiés.

## <a name="description"></a>Description

Find-Script détecte les fichiers de script à partir des référentiels enregistrés qui correspondent aux critères spécifiés.
Pour chaque script trouvé, Find-Script retourne un objet PSRepositoryItemInfo qui peut éventuellement être transmis à Install-Script pour installer les scripts.
L’applet de commande Find-Script permet de découvrir les fichiers de script avec différents critères de recherche tels que nom, balise, filtre, nom de commande, plage de versions, version exacte, toutes les versions, y compris ses dépendances et à partir de dépôts spécifiques ou de tous les dépôts inscrits.

- Find-Script peut filtrer le contenu de script avec les paramètres -Command et -Includes.
- Find-Script permet de filtrer avec des paramètres de version : MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Ces paramètres sont mutuellement exclusifs, sauf MinmimumVersion et MaximumVersion.
  - Ces paramètres de version sont autorisés uniquement avec le nom de script unique sans les caractères génériques.
  - Si le paramètre RequiredVersion n’est pas spécifié, Find-Script retourne la dernière version du script qui est supérieure ou égale à la version minimale spécifiée ou la dernière version du script si aucune version minimale n’est spécifiée. 
  - Si le paramètre RequiredVersion est spécifié, Find-Script retourne uniquement la version du script qui correspond exactement à la version spécifiée.
- Find-Script peut filtrer les métadonnées de scripts avec le paramètre -Tag.
- Find-Script peut filtrer le langage de recherche propre au référentiel avec le paramètre -Filter.
- Find-Script peut filtrer les scripts à partir de l’ensemble ou de certains des référentiels enregistrés.

**REMARQUE :** Un référentiel PSRepository enregistré doit avoir une valeur ScriptSourceLocation valide. Vous pouvez utiliser l’applet de commande Set-PSRepository pour définir la valeur ScriptSourceLocation.

## <a name="cmdlet-syntax"></a>Syntaxe de l’applet de commande

```powershell
Get-Command -Name Find-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Référence de l’aide en ligne de l’applet de commande

[Find-Script](http://go.microsoft.com/fwlink/?LinkId=619785)

## <a name="example-commands"></a>Exemples de commandes

```powershell
# Find a script from the registered repository with ScriptSourceLocation
Find-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Find-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Find-Script -Name *Azure*

# Find all versions of a script
Find-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion. 
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Find-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Find-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Find-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Find a script with exact version
Find-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script with a specific pre-release version
Find-Script -Name Connect-O365 -RequiredVersion 1.3.2-alpha -AllowPrerelease

# Find a script from the specified repository
Find-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Find-Script

# Find available scripts from few registered repositories
Find-Script -Repository PSGallery, PrivatePSGallery

# Find a script along with its dependent modules and scripts
Find-Script -Name Connect-AzureVM -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...
1.4.0      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management
1.1.2      Azure.Storage                       PSGallery            Microsoft Azure PowerShell - Storage service cmd...
1.0.8      AzureRM.profile                     PSGallery            Microsoft Azure PowerShell - Profile credential ...

# Find all scripts with workflows
Find-Script -Includes Workflow

# Find all scripts with functions
Find-Script -Includes Function

# Find scripts with specific commands
Find-Script -Command Log-Message
Find-Script -Command Log-Message, Show-Tree -Includes Function
Find-Script -Command Connect-AzureVM -Includes Workflow

# Find scripts with -Filter based search. -Filter searches in description and names
Find-Script -Filter Windows
Find-Script -Filter Azure

# Find all scripts with tags O365 or Nano
Find-Script -Tag O365, Nano

# Properties of Find-Script returned object
Find-Script Show-Tree | Format-List * -Force
Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              :
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
AdditionalMetadata         : {versionDownloadCount, ItemType, copyright, PackageManagementProvider...}


# Includes property on PSRepositoryItemInfo object
$t = Find-Script -Includes Workflow -Repository INT -Name Fabrikam-ClientScript
$t.Includes

Name                           Value
----                           -----
Function                       {Test-FunctionFromScript_Fabrikam-ClientScript}
RoleCapability                 {}
Command                        {Test-FunctionFromScript_Fabrikam-ClientScript, Test-WorkflowFromScript_Fabrikam-Clie...
DscResource                    {}
Workflow                       {Test-WorkflowFromScript_Fabrikam-ClientScript}
Cmdlet                         {}


```

