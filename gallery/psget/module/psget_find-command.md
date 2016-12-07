---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_find command
ms.technology: powershell
ms.openlocfilehash: 99091130ea89023495e5e3aacafb292f67f2db30
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="find-command"></a>Find-Command

Recherche des commandes PowerShell dans des modules.

## <a name="description"></a>Description
L’applet de commande Find-Command recherche des commandes PowerShell, telles que les applets de commande, alias, fonctions et workflows. Find-Command recherche des modules dans les référentiels enregistrés.
Pour chaque commande qu’elle détecte, cette applet de commande retourne un objet PSGetCommandInfo. Vous pouvez passer un objet PSGetCommandInfo à l’applet de commande Install-Module pour installer le module qui contient la commande.

- Find-Command permet de filtrer avec des paramètres de version : MinimumVersion, RequiredVersion, AllVersions.
  - Ces paramètres sont mutuellement exclusifs.
  - Ces paramètres de version sont autorisés uniquement avec le nom de module unique sans les caractères génériques.
  - Si le paramètre RequiredVersion n’est pas spécifié, Find-Command retourne la dernière version du module qui est supérieure ou égale à la version minimale spécifiée ou la dernière version du module si aucune version minimale n’est spécifiée.
  - Si le paramètre RequiredVersion est spécifié, Find-Command retourne uniquement la version du module qui correspond exactement à la version spécifiée.
- Find-Command peut filtrer les métadonnées de modules avec le paramètre -Tag
- Find-Command peut filtrer le langage de recherche propre au référentiel avec le paramètre -Filter.
- Find-Command peut filtrer les modules à partir de l’ensemble ou de certains des référentiels enregistrés.

## <a name="cmdlet-syntax"></a>Syntaxe de l’applet de commande
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Référence de l’aide en ligne de l’applet de commande

[Find-Command](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a>Exemples de commandes
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

