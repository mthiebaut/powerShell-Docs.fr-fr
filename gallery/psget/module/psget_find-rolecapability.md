---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-RoleCapability
ms.openlocfilehash: 89aacd604d54f6a5e9752790be65cc3bcc77c8e1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="find-rolecapability"></a><span data-ttu-id="73598-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="73598-103">Find-RoleCapability</span></span>

<span data-ttu-id="73598-104">Recherche les capacités de rôle dans des modules.</span><span class="sxs-lookup"><span data-stu-id="73598-104">Finds role capabilities in modules.</span></span>

## <a name="description"></a><span data-ttu-id="73598-105">Description</span><span class="sxs-lookup"><span data-stu-id="73598-105">Description</span></span>
<span data-ttu-id="73598-106">L’applet de commande Find-RoleCapability recherche les capacités de rôle PowerShell dans des modules.</span><span class="sxs-lookup"><span data-stu-id="73598-106">The Find-RoleCapability cmdlet finds PowerShell role capabilities in modules.</span></span> <span data-ttu-id="73598-107">Find-RoleCapability recherche des modules dans les référentiels enregistrés.</span><span class="sxs-lookup"><span data-stu-id="73598-107">Find-RoleCapability searches modules in registered repositories.</span></span>
<span data-ttu-id="73598-108">Pour chaque capacité de rôle qu’elle détecte, cette applet de commande retourne un objet PSGetRoleCapabilityInfo.</span><span class="sxs-lookup"><span data-stu-id="73598-108">For each role capability that this cmdlet finds, it returns a PSGetRoleCapabilityInfo object.</span></span> <span data-ttu-id="73598-109">Vous pouvez passer un objet PSGetRoleCapabilityInfo à l’applet de commande Install-Module pour installer le module qui contient la capacité de rôle.</span><span class="sxs-lookup"><span data-stu-id="73598-109">You can pass a PSGetRoleCapabilityInfo object to the Install-Module cmdlet to install the module that contains the role capability.</span></span>
<span data-ttu-id="73598-110">Les capacités de rôle PowerShell définissent, entre autres, les commandes et applications à la disposition d’un utilisateur au niveau d’un point de terminaison d’administration suffisante.</span><span class="sxs-lookup"><span data-stu-id="73598-110">PowerShell role capabilities define which commands, applications, and so on are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="73598-111">Les capacités de rôle sont définies par des fichiers portant une extension .psrc.</span><span class="sxs-lookup"><span data-stu-id="73598-111">Role capabilities are defined by files with a .psrc extension.</span></span>

- <span data-ttu-id="73598-112">Find-RoleCapability permet de filtrer avec des paramètres de version : MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="73598-112">Find-RoleCapability can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="73598-113">Ces paramètres sont mutuellement exclusifs.</span><span class="sxs-lookup"><span data-stu-id="73598-113">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="73598-114">Ces paramètres de version sont autorisés uniquement avec le nom de module unique sans les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="73598-114">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="73598-115">Si le paramètre RequiredVersion n’est pas spécifié, Find-RoleCapability retourne la dernière version du module qui est supérieure ou égale à la version minimale spécifiée ou la dernière version du module si aucune version minimale n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="73598-115">If the RequiredVersion parameter is not specified, Find-RoleCapability returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="73598-116">Si le paramètre RequiredVersion est spécifié, Find-RoleCapability retourne uniquement la version du module qui correspond exactement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="73598-116">If the RequiredVersion parameter is specified, Find-RoleCapability only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="73598-117">Find-RoleCapability peut filtrer les métadonnées de modules avec le paramètre -Tag</span><span class="sxs-lookup"><span data-stu-id="73598-117">Find-RoleCapability can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="73598-118">Find-RoleCapability peut filtrer le langage de recherche propre au référentiel avec le paramètre -Filter.</span><span class="sxs-lookup"><span data-stu-id="73598-118">Find-RoleCapability can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="73598-119">Find-RoleCapability peut filtrer les modules à partir de l’ensemble ou de certains des référentiels enregistrés.</span><span class="sxs-lookup"><span data-stu-id="73598-119">Find-RoleCapability can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="73598-120">Syntaxe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="73598-120">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="73598-121">Référence de l’aide en ligne de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="73598-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="73598-122">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="73598-122">Find-RoleCapability</span></span>](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a><span data-ttu-id="73598-123">Exemples de commandes</span><span class="sxs-lookup"><span data-stu-id="73598-123">Example commands</span></span>
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