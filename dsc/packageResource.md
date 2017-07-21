---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource Package dans DSC
ms.openlocfilehash: f7bcbd387db422037614feee7c4a00d93b3cec4e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-package-resource"></a><span data-ttu-id="77dc3-103">Ressource Package dans DSC</span><span class="sxs-lookup"><span data-stu-id="77dc3-103">DSC Package Resource</span></span>

> <span data-ttu-id="77dc3-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="77dc3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="77dc3-105">La ressource **Package** dans DSC Windows PowerShell fournit un mécanisme permettant d’installer ou de désinstaller des packages, tels que les packages Windows Installer et setup.exe, sur un nœud cible.</span><span class="sxs-lookup"><span data-stu-id="77dc3-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="77dc3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77dc3-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="77dc3-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="77dc3-107">Properties</span></span>
|  <span data-ttu-id="77dc3-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="77dc3-108">Property</span></span>  |  <span data-ttu-id="77dc3-109">Description</span><span class="sxs-lookup"><span data-stu-id="77dc3-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="77dc3-110">Name</span><span class="sxs-lookup"><span data-stu-id="77dc3-110">Name</span></span>| <span data-ttu-id="77dc3-111">Indique le nom du package pour lequel vous souhaitez garantir un état spécifique.</span><span class="sxs-lookup"><span data-stu-id="77dc3-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="77dc3-112">Path</span><span class="sxs-lookup"><span data-stu-id="77dc3-112">Path</span></span>| <span data-ttu-id="77dc3-113">Indique le chemin où se trouve le package.</span><span class="sxs-lookup"><span data-stu-id="77dc3-113">Indicates the path where the package resides.</span></span>| 
| <span data-ttu-id="77dc3-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="77dc3-114">ProductId</span></span>| <span data-ttu-id="77dc3-115">Indique l’ID de produit qui identifie le package de manière unique.</span><span class="sxs-lookup"><span data-stu-id="77dc3-115">Indicates the product ID that uniquely identifies the package.</span></span>| 
| <span data-ttu-id="77dc3-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="77dc3-116">Arguments</span></span>| <span data-ttu-id="77dc3-117">Chaîne d’arguments transmise telle quelle au package.</span><span class="sxs-lookup"><span data-stu-id="77dc3-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>| 
| <span data-ttu-id="77dc3-118">Credential</span><span class="sxs-lookup"><span data-stu-id="77dc3-118">Credential</span></span>| <span data-ttu-id="77dc3-119">Informations d’identification permettant l’accès au package sur une source distante.</span><span class="sxs-lookup"><span data-stu-id="77dc3-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="77dc3-120">Cette propriété n’est pas utilisée pour installer le package.</span><span class="sxs-lookup"><span data-stu-id="77dc3-120">This property is not used to install the package.</span></span> <span data-ttu-id="77dc3-121">Le package est toujours installé sur le système local.</span><span class="sxs-lookup"><span data-stu-id="77dc3-121">The package is always installed on the local system.</span></span>| 
| <span data-ttu-id="77dc3-122">Ensure</span><span class="sxs-lookup"><span data-stu-id="77dc3-122">Ensure</span></span>| <span data-ttu-id="77dc3-123">Indique si le package est installé.</span><span class="sxs-lookup"><span data-stu-id="77dc3-123">Indicates if the package is installed.</span></span> <span data-ttu-id="77dc3-124">Définissez cette propriété sur « Absent » pour vous assurer que le package n’est pas installé (ou désinstallé, si le package n’est pas installé).</span><span class="sxs-lookup"><span data-stu-id="77dc3-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="77dc3-125">Définissez cette propriété sur « Present » (valeur par défaut) pour vous assurer que le package est installé.</span><span class="sxs-lookup"><span data-stu-id="77dc3-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>| 
| <span data-ttu-id="77dc3-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="77dc3-126">LogPath</span></span>| <span data-ttu-id="77dc3-127">Indique le chemin complet où vous souhaitez que le fournisseur enregistre un fichier journal pour installer ou désinstaller le package.</span><span class="sxs-lookup"><span data-stu-id="77dc3-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>| 
| <span data-ttu-id="77dc3-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="77dc3-128">DependsOn</span></span> | <span data-ttu-id="77dc3-129">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="77dc3-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="77dc3-130">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : DependsOn = "[ResourceType]ResourceName"</span><span class="sxs-lookup"><span data-stu-id="77dc3-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 
| <span data-ttu-id="77dc3-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="77dc3-131">ReturnCode</span></span>| <span data-ttu-id="77dc3-132">Indique le code de retour attendu.</span><span class="sxs-lookup"><span data-stu-id="77dc3-132">Indicates the expected return code.</span></span> <span data-ttu-id="77dc3-133">Si le code de retour réel ne correspond pas à la valeur attendue indiquée ici, la configuration retourne une erreur.</span><span class="sxs-lookup"><span data-stu-id="77dc3-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>| 

## <a name="example"></a><span data-ttu-id="77dc3-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="77dc3-134">Example</span></span>

<span data-ttu-id="77dc3-135">Cet exemple exécute le programme d’installation .msi qui se trouve dans le chemin spécifié et qui possède l’ID de produit spécifié.</span><span class="sxs-lookup"><span data-stu-id="77dc3-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    } 
}
```

