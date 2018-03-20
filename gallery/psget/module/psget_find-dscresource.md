---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-DscResource
ms.openlocfilehash: 6c5713f122d48e9c9d5e0aa45dc14047afc56102
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
---
# <a name="find-dscresource"></a><span data-ttu-id="38b78-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="38b78-103">Find-DscResource</span></span>

<span data-ttu-id="38b78-104">Recherche des ressources DSC dans des modules.</span><span class="sxs-lookup"><span data-stu-id="38b78-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="38b78-105">Description</span><span class="sxs-lookup"><span data-stu-id="38b78-105">Description</span></span>

<span data-ttu-id="38b78-106">L’applet de commande Find-DscResource recherche des ressources [DSC (Configuration de l’état souhaité)](https://msdn.microsoft.com/PowerShell/dsc/overview) contenues dans les modules qui correspondent aux critères spécifiés à partir des référentiels enregistrés.</span><span class="sxs-lookup"><span data-stu-id="38b78-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="38b78-107">Pour chaque module qu’elle détecte, Find-DscResource retourne un objet PSGetDscResourceInfo que vous pouvez rediriger vers Install-Module pour installer les modules contenant les ressources retournées par cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="38b78-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="38b78-108">DSC est une nouvelle plateforme de gestion de Windows PowerShell qui permet de déployer et gérer les données de configuration des services logiciels, et de gérer l’environnement dans lequel ces services s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="38b78-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="38b78-109">Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="38b78-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="38b78-110">Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="38b78-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="38b78-111">Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="38b78-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="38b78-112">Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.</span><span class="sxs-lookup"><span data-stu-id="38b78-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="38b78-113">Find-DscResource permet de filtrer avec des paramètres de version : MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="38b78-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="38b78-114">Ces paramètres sont mutuellement exclusifs.</span><span class="sxs-lookup"><span data-stu-id="38b78-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="38b78-115">Ces paramètres de version sont autorisés uniquement avec le nom de module unique sans les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="38b78-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="38b78-116">Si le paramètre RequiredVersion n’est pas spécifié, Find-DscResource retourne la dernière version du module qui est supérieure ou égale à la version minimale spécifiée ou la dernière version du module si aucune version minimale n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="38b78-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="38b78-117">Si le paramètre RequiredVersion est spécifié, Find-DscResource retourne uniquement la version du module qui correspond exactement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="38b78-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="38b78-118">Find-DscResource peut filtrer les métadonnées de modules avec le paramètre -Tag</span><span class="sxs-lookup"><span data-stu-id="38b78-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="38b78-119">Find-DscResource peut filtrer le langage de recherche propre au référentiel avec le paramètre -Filter.</span><span class="sxs-lookup"><span data-stu-id="38b78-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="38b78-120">Find-DscResource peut filtrer les modules à partir de l’ensemble ou de certains des référentiels enregistrés.</span><span class="sxs-lookup"><span data-stu-id="38b78-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="38b78-121">Syntaxe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="38b78-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="38b78-122">Référence de l’aide en ligne de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="38b78-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="38b78-123">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="38b78-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="38b78-124">Exemples de commandes</span><span class="sxs-lookup"><span data-stu-id="38b78-124">Example commands</span></span>
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

