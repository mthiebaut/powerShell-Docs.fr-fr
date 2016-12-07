---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_find dscresource
ms.technology: powershell
ms.openlocfilehash: afd13e1dd791794d62be4601477bcc77448586c5
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="find-dscresource"></a>Find-DscResource

Recherche des ressources DSC dans des modules.

## <a name="description"></a>Description

L’applet de commande Find-DscResource recherche des ressources [DSC (Configuration de l’état souhaité)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) contenues dans les modules qui correspondent aux critères spécifiés à partir des référentiels enregistrés.
Pour chaque module qu’elle détecte, Find-DscResource retourne un objet PSGetDscResourceInfo que vous pouvez rediriger vers Install-Module pour installer les modules contenant les ressources retournées par cette applet de commande.

DSC est une nouvelle plateforme de gestion de Windows PowerShell qui permet de déployer et gérer les données de configuration des services logiciels, et de gérer l’environnement dans lequel ces services s’exécutent.

Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC. Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.

Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS. Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.

- Find-DscResource permet de filtrer avec des paramètres de version : MinimumVersion, RequiredVersion, AllVersions.
  - Ces paramètres sont mutuellement exclusifs.
  - Ces paramètres de version sont autorisés uniquement avec le nom de module unique sans les caractères génériques.
  - Si le paramètre RequiredVersion n’est pas spécifié, Find-DscResource retourne la dernière version du module qui est supérieure ou égale à la version minimale spécifiée ou la dernière version du module si aucune version minimale n’est spécifiée.
  - Si le paramètre RequiredVersion est spécifié, Find-DscResource retourne uniquement la version du module qui correspond exactement à la version spécifiée.
- Find-DscResource peut filtrer les métadonnées de modules avec le paramètre -Tag
- Find-DscResource peut filtrer le langage de recherche propre au référentiel avec le paramètre -Filter.
- Find-DscResource peut filtrer les modules à partir de l’ensemble ou de certains des référentiels enregistrés.

## <a name="cmdlet-syntax"></a>Syntaxe de l’applet de commande
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Référence de l’aide en ligne de l’applet de commande

[Find-DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a>Exemples de commandes
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

