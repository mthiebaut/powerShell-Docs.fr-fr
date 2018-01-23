---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource DSC PackageManagement
ms.openlocfilehash: 4cd7625af7ed0bb3fe971c826ac2075841cdfdc5
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="36b56-103">Ressource DSC PackageManagement</span><span class="sxs-lookup"><span data-stu-id="36b56-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="36b56-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="36b56-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="36b56-105">La ressource **PackageManagement** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’installer ou de désinstaller des packages de gestion des packages sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="36b56-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="36b56-106">Cette ressource nécessite le module **PackageManagement** qui est disponible sur http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="36b56-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="36b56-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36b56-107">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="36b56-108">Propriétés</span><span class="sxs-lookup"><span data-stu-id="36b56-108">Properties</span></span>
|  <span data-ttu-id="36b56-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="36b56-109">Property</span></span>  |  <span data-ttu-id="36b56-110">Description</span><span class="sxs-lookup"><span data-stu-id="36b56-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="36b56-111">Name</span><span class="sxs-lookup"><span data-stu-id="36b56-111">Name</span></span>| <span data-ttu-id="36b56-112">Spécifie le nom du package à installer ou à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="36b56-112">Specifies the name of the Package to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="36b56-113">Source</span><span class="sxs-lookup"><span data-stu-id="36b56-113">Source</span></span>| <span data-ttu-id="36b56-114">Spécifie le nom de la source du package où se trouve le package.</span><span class="sxs-lookup"><span data-stu-id="36b56-114">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="36b56-115">Il peut s’agir d’un URI ou d’une source inscrite avec une ressource DSC Register-PackageSource ou PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="36b56-115">This can either be a URI or a source registered with Register-PackageSource or PackageManagementSource DSC resource.</span></span> <span data-ttu-id="36b56-116">La ressource DSC MSFT_PackageManagementSource peut également inscrire une source de package.</span><span class="sxs-lookup"><span data-stu-id="36b56-116">The DSC resource MSFT_PackageManagementSource can also register a package source.</span></span>| 
| <span data-ttu-id="36b56-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="36b56-117">Ensure</span></span>| <span data-ttu-id="36b56-118">Détermine si le package doit être installé ou désinstallé.</span><span class="sxs-lookup"><span data-stu-id="36b56-118">Determines whether the package is to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="36b56-119">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="36b56-119">RequiredVersion</span></span>| <span data-ttu-id="36b56-120">Spécifie la version exacte du package à installer.</span><span class="sxs-lookup"><span data-stu-id="36b56-120">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="36b56-121">Si vous ne spécifiez pas ce paramètre, cette ressource DSC installe la version la plus récente du package parmi celles disponibles, sans toutefois dépasser la version maximale spécifiée par le paramètre MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="36b56-121">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="36b56-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="36b56-122">MinimumVersion</span></span>| <span data-ttu-id="36b56-123">Spécifie la version minimale autorisée du package à installer.</span><span class="sxs-lookup"><span data-stu-id="36b56-123">Specifies the minimum allowed version of the package that you want to install.</span></span> <span data-ttu-id="36b56-124">Si vous n’ajoutez pas ce paramètre, cette ressource DSC installe la version la plus élevée du package parmi celles disponibles, sans toutefois dépasser la version maximale spécifiée par le paramètre MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="36b56-124">If you do not add this parameter, this DSC resource intalls the highest available version of the package that also satisfies any maximum specified version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="36b56-125">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="36b56-125">MaximumVersion</span></span>| <span data-ttu-id="36b56-126">Spécifie la version maximale autorisée du package à installer.</span><span class="sxs-lookup"><span data-stu-id="36b56-126">Specifies the maximum allowed version of the package that you want to install.</span></span> <span data-ttu-id="36b56-127">Si vous ne spécifiez pas ce paramètre, cette ressource DSC installe la version la plus élevée du package parmi celles disponibles.</span><span class="sxs-lookup"><span data-stu-id="36b56-127">If you do not specify this parameter, this DSC resource installs the highest-numbered available version of the package.</span></span>| 
| <span data-ttu-id="36b56-128">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="36b56-128">SourceCredential</span></span> | <span data-ttu-id="36b56-129">Spécifie un compte d’utilisateur disposant des droits nécessaires pour installer un package pour une source ou un fournisseur de package spécifié.</span><span class="sxs-lookup"><span data-stu-id="36b56-129">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>| 
| <span data-ttu-id="36b56-130">ProviderName</span><span class="sxs-lookup"><span data-stu-id="36b56-130">ProviderName</span></span>| <span data-ttu-id="36b56-131">Spécifie un nom de fournisseur de package auquel vous souhaitez limiter votre recherche de package.</span><span class="sxs-lookup"><span data-stu-id="36b56-131">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="36b56-132">Pour obtenir les noms des fournisseurs de package, exécutez l’applet de commande Get-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="36b56-132">You can get package provider names by running the Get-PackageProvider cmdlet.</span></span>| 
| <span data-ttu-id="36b56-133">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="36b56-133">AdditionalParameters</span></span>| <span data-ttu-id="36b56-134">Paramètres spécifiques à un fournisseur passés sous forme d’une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="36b56-134">Provider specific parameters that are passed as an Hashtable.</span></span> <span data-ttu-id="36b56-135">Par exemple, pour le fournisseur NuGet, vous pouvez passer des paramètres supplémentaires tels que DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="36b56-135">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>| 

## <a name="additional-parameters"></a><span data-ttu-id="36b56-136">Paramètres supplémentaires</span><span class="sxs-lookup"><span data-stu-id="36b56-136">Additional Parameters</span></span>
<span data-ttu-id="36b56-137">Le tableau suivant répertorie les options de la propriété AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="36b56-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="36b56-138">Paramètre</span><span class="sxs-lookup"><span data-stu-id="36b56-138">Parameter</span></span>  | <span data-ttu-id="36b56-139">Description</span><span class="sxs-lookup"><span data-stu-id="36b56-139">Description</span></span>   | 
|---|---|
| <span data-ttu-id="36b56-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="36b56-140">DestinationPath</span></span>| <span data-ttu-id="36b56-141">Utilisé par les fournisseurs, notamment le fournisseur Nuget intégré.</span><span class="sxs-lookup"><span data-stu-id="36b56-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="36b56-142">Spécifie un emplacement de fichier où vous souhaitez installer le package.</span><span class="sxs-lookup"><span data-stu-id="36b56-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="36b56-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="36b56-143">InstallationPolicy</span></span>| <span data-ttu-id="36b56-144">Utilisé par les fournisseurs, notamment le fournisseur Nuget intégré.</span><span class="sxs-lookup"><span data-stu-id="36b56-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="36b56-145">Détermine si vous faites confiance à la source du package.</span><span class="sxs-lookup"><span data-stu-id="36b56-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="36b56-146">Valeurs disponibles : « Untrusted », « Trusted ».</span><span class="sxs-lookup"><span data-stu-id="36b56-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="36b56-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="36b56-147">Example</span></span>

<span data-ttu-id="36b56-148">Cet exemple installe le package NuGet **JQuery** et le module PowerShell **GistProvider** à l’aide de la ressource DSC **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="36b56-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="36b56-149">Cet exemple vérifie d’abord que les sources de package nécessaires sont disponibles, puis définit l’état attendu des packages **JQuery** et **GistProvider** (NuGet et PowerShell, respectivement).</span><span class="sxs-lookup"><span data-stu-id="36b56-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{    
    PackageManagementSource SourceRepository 
    { 
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
        InstallationPolicy ="Trusted" 
    } 
          
    PackageManagement NugetPackage 
    { 
        Ensure               = "Present"  
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1" 
        DependsOn            = "[PackageManagementSource]SourceRepository" 
    }
    
    PackageManagement PSModule 
    { 
        Ensure               = "Present"  
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery" 
    }
}
```

