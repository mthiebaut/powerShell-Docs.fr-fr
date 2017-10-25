---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a>Find-RoleCapability

Recherche les capacités de rôle dans des modules.

## <a name="description"></a>Description
L’applet de commande Find-RoleCapability recherche les capacités de rôle PowerShell dans des modules. Find-RoleCapability recherche des modules dans les référentiels enregistrés. Pour chaque capacité de rôle qu’elle détecte, cette applet de commande retourne un objet PSGetRoleCapabilityInfo. Vous pouvez passer un objet PSGetRoleCapabilityInfo à l’applet de commande Install-Module pour installer le module qui contient la capacité de rôle.
Les capacités de rôle PowerShell définissent, entre autres, les commandes et applications à la disposition d’un utilisateur au niveau d’un point de terminaison d’administration suffisante. Les capacités de rôle sont définies par des fichiers portant une extension .psrc.

- Find-RoleCapability permet de filtrer avec des paramètres de version : MinimumVersion, RequiredVersion, AllVersions.
  - Ces paramètres sont mutuellement exclusifs.
  - Ces paramètres de version sont autorisés uniquement avec le nom de module unique sans les caractères génériques.
  - Si le paramètre RequiredVersion n’est pas spécifié, Find-RoleCapability retourne la dernière version du module qui est supérieure ou égale à la version minimale spécifiée ou la dernière version du module si aucune version minimale n’est spécifiée.
  - Si le paramètre RequiredVersion est spécifié, Find-RoleCapability retourne uniquement la version du module qui correspond exactement à la version spécifiée.
- Find-RoleCapability peut filtrer les métadonnées de modules avec le paramètre -Tag
- Find-RoleCapability peut filtrer le langage de recherche propre au référentiel avec le paramètre -Filter.
- Find-RoleCapability peut filtrer les modules à partir de l’ensemble ou de certains des référentiels enregistrés.

## <a name="cmdlet-syntax"></a>Syntaxe de l’applet de commande
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Référence de l’aide en ligne de l’applet de commande

[Find-RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a>Exemples de commandes
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

