---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WaitForSome
ms.openlocfilehash: 5d67a9111f6358240590b651e627ffb96abc0896
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="78465-103">Ressource DSC WaitForSome</span><span class="sxs-lookup"><span data-stu-id="78465-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="78465-104">S’applique à : Windows PowerShell 5.0 et ultérieur</span><span class="sxs-lookup"><span data-stu-id="78465-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="78465-105">La ressource de configuration d’état souhaité (DSC) **WaitForAny** peut être utilisée dans un bloc de nœud dans une [configuration DSC](configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="78465-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="78465-106">La ressource réussit si la ressource spécifiée dans la propriété **ResourceName** est dans l’état souhaité sur un nombre minimal de nœuds (spécifié par **NodeCount**) défini par la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="78465-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="78465-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78465-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    NodeCount = [Uint32]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="78465-108">Propriétés</span><span class="sxs-lookup"><span data-stu-id="78465-108">Properties</span></span>

|  <span data-ttu-id="78465-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="78465-109">Property</span></span>  |  <span data-ttu-id="78465-110">Description</span><span class="sxs-lookup"><span data-stu-id="78465-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="78465-111">Nom_ressource</span><span class="sxs-lookup"><span data-stu-id="78465-111">ResourceName</span></span>| <span data-ttu-id="78465-112">Le nom de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="78465-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="78465-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="78465-113">NodeName</span></span>| <span data-ttu-id="78465-114">Les nœuds cible de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="78465-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="78465-115">NodeCount</span><span class="sxs-lookup"><span data-stu-id="78465-115">NodeCount</span></span>| <span data-ttu-id="78465-116">Le nombre minimal de nœuds qui doivent être dans l’état souhaité pour que cette ressource réussisse.</span><span class="sxs-lookup"><span data-stu-id="78465-116">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="78465-117">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="78465-117">RetryIntervalSec</span></span>| <span data-ttu-id="78465-118">Le nombre de secondes avant la nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="78465-118">The number of seconds before retrying.</span></span> <span data-ttu-id="78465-119">Le minimum est 1.</span><span class="sxs-lookup"><span data-stu-id="78465-119">Minimum is 1.</span></span>| 
| <span data-ttu-id="78465-120">RetryCount</span><span class="sxs-lookup"><span data-stu-id="78465-120">RetryCount</span></span>| <span data-ttu-id="78465-121">Le nombre maximum de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="78465-121">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="78465-122">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="78465-122">ThrottleLimit</span></span>| <span data-ttu-id="78465-123">Le nombre de machines à connecter simultanément.</span><span class="sxs-lookup"><span data-stu-id="78465-123">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="78465-124">La valeur par défaut est new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="78465-124">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="78465-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="78465-125">DependsOn</span></span> | <span data-ttu-id="78465-126">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="78465-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="78465-127">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="78465-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="78465-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="78465-128">Example</span></span>

<span data-ttu-id="78465-129">Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="78465-129">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

