---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-Command
ms.openlocfilehash: 26ddf4824816db245131a0fc95b7d2a88bef8f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="find-command"></a><span data-ttu-id="ee2a0-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="ee2a0-103">Find-Command</span></span>

<span data-ttu-id="ee2a0-104">Recherche des commandes PowerShell dans des modules.</span><span class="sxs-lookup"><span data-stu-id="ee2a0-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="ee2a0-105">Description</span><span class="sxs-lookup"><span data-stu-id="ee2a0-105">Description</span></span>
<span data-ttu-id="ee2a0-106">L’applet de commande Find-Command recherche des commandes PowerShell, telles que les applets de commande, alias, fonctions et workflows.</span><span class="sxs-lookup"><span data-stu-id="ee2a0-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="ee2a0-107">Find-Command recherche des modules dans les référentiels enregistrés.</span><span class="sxs-lookup"><span data-stu-id="ee2a0-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="ee2a0-108">Pour chaque commande qu’elle détecte, cette applet de commande retourne un objet PSGetCommandInfo.</span><span class="sxs-lookup"><span data-stu-id="ee2a0-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="ee2a0-109">Vous pouvez passer un objet PSGetCommandInfo à l’applet de commande Install-Module pour installer le module qui contient la commande.</span><span class="sxs-lookup"><span data-stu-id="ee2a0-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="ee2a0-110">Find-Command permet de filtrer avec des paramètres de version : MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="ee2a0-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="ee2a0-111">Ces paramètres sont mutuellement exclusifs.</span><span class="sxs-lookup"><span data-stu-id="ee2a0-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="ee2a0-112">Ces paramètres de version sont autorisés uniquement avec le nom de module unique sans les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="ee2a0-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="ee2a0-113">Si le paramètre RequiredVersion n’est pas spécifié, Find-Command retourne la dernière version du module qui est supérieure ou égale à la version minimale spécifiée ou la dernière version du module si aucune version minimale n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ee2a0-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="ee2a0-114">Si le paramètre RequiredVersion est spécifié, Find-Command retourne uniquement la version du module qui correspond exactement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ee2a0-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="ee2a0-115">Find-Command peut filtrer les métadonnées de modules avec le paramètre -Tag</span><span class="sxs-lookup"><span data-stu-id="ee2a0-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="ee2a0-116">Find-Command peut filtrer le langage de recherche propre au référentiel avec le paramètre -Filter.</span><span class="sxs-lookup"><span data-stu-id="ee2a0-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="ee2a0-117">Find-Command peut filtrer les modules à partir de l’ensemble ou de certains des référentiels enregistrés.</span><span class="sxs-lookup"><span data-stu-id="ee2a0-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="ee2a0-118">Syntaxe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="ee2a0-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="ee2a0-119">Référence de l’aide en ligne de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="ee2a0-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="ee2a0-120">Find-Command</span><span class="sxs-lookup"><span data-stu-id="ee2a0-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="ee2a0-121">Exemples de commandes</span><span class="sxs-lookup"><span data-stu-id="ee2a0-121">Example commands</span></span>
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