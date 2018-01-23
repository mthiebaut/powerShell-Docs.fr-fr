---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressources DSC PackageManagementSource
ms.openlocfilehash: 1c904c70369a75802484c3c0520df63602760361
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="1895e-103">Ressources DSC PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="1895e-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="1895e-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1895e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1895e-105">La ressource **PackageManagementSource** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme permettant d’inscrire ou de désinscrire des sources de gestion des packages sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="1895e-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="1895e-106">**Les sources de gestion des packages inscrites de cette façon sont inscrites sous le contexte système et peuvent être utilisées par le compte système ou le moteur DSC.**</span><span class="sxs-lookup"><span data-stu-id="1895e-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="1895e-107">Cette ressource nécessite le module **PackageManagement** qui est disponible sur le site http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="1895e-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="1895e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1895e-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="1895e-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1895e-109">Properties</span></span>
|  <span data-ttu-id="1895e-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="1895e-110">Property</span></span>  |  <span data-ttu-id="1895e-111">Description</span><span class="sxs-lookup"><span data-stu-id="1895e-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="1895e-112">Name</span><span class="sxs-lookup"><span data-stu-id="1895e-112">Name</span></span>| <span data-ttu-id="1895e-113">Spécifie le nom de la source du package à inscrire ou à désinscrire sur votre système.</span><span class="sxs-lookup"><span data-stu-id="1895e-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>| 
| <span data-ttu-id="1895e-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="1895e-114">Ensure</span></span>| <span data-ttu-id="1895e-115">Détermine si la source du package doit être inscrite ou désinscrite.</span><span class="sxs-lookup"><span data-stu-id="1895e-115">Determines whether the package source is to be registered or unregistered.</span></span>| 
| <span data-ttu-id="1895e-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="1895e-116">InstallationPolicy</span></span>| <span data-ttu-id="1895e-117">Détermine si vous faites confiance à la source du package.</span><span class="sxs-lookup"><span data-stu-id="1895e-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="1895e-118">Valeurs disponibles : « Untrusted », « Trusted ».</span><span class="sxs-lookup"><span data-stu-id="1895e-118">One of: "Untrusted", "Trusted".</span></span>| 
| <span data-ttu-id="1895e-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="1895e-119">ProviderName</span></span>| <span data-ttu-id="1895e-120">Spécifie le nom du fournisseur OneGet par le biais duquel vous pouvez interagir avec la source du package.</span><span class="sxs-lookup"><span data-stu-id="1895e-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>| 
| <span data-ttu-id="1895e-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="1895e-121">SourceUri</span></span>| <span data-ttu-id="1895e-122">Spécifie l’URI de la source du package.</span><span class="sxs-lookup"><span data-stu-id="1895e-122">Specifies the URI of the package source.</span></span>| 
| <span data-ttu-id="1895e-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="1895e-123">SourceCredential</span></span>| <span data-ttu-id="1895e-124">Informations d’identification permettant l’accès au package sur une source distante.</span><span class="sxs-lookup"><span data-stu-id="1895e-124">Provides access to the package on a remote source.</span></span>| 

## <a name="example"></a><span data-ttu-id="1895e-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="1895e-125">Example</span></span>

<span data-ttu-id="1895e-126">Cet exemple inscrit la source du package http://nuget.org à l’aide de la ressource DSC **PackageManagementSource**.</span><span class="sxs-lookup"><span data-stu-id="1895e-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

