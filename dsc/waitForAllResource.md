---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WaitForAll
ms.openlocfilehash: dcc23ad4e6905bc277ad39348350d5425fc90ad7
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="8d790-103">Ressource DSC WaitForAll</span><span class="sxs-lookup"><span data-stu-id="8d790-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="8d790-104">S’applique à : Windows PowerShell 5.0 et ultérieur</span><span class="sxs-lookup"><span data-stu-id="8d790-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="8d790-105">La ressource de configuration d’état souhaité (DSC) **WaitForAll** peut être utilisée dans un bloc de nœud dans une [configuration DSC](configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="8d790-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="8d790-106">La ressource réussit si la ressource spécifiée par la propriété **ResourceName** est dans l’état souhaité sur tous les nœuds cible définis dans la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="8d790-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="8d790-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d790-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="8d790-108">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8d790-108">Properties</span></span>

|  <span data-ttu-id="8d790-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="8d790-109">Property</span></span>  |  <span data-ttu-id="8d790-110">Description</span><span class="sxs-lookup"><span data-stu-id="8d790-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="8d790-111">Nom_ressource</span><span class="sxs-lookup"><span data-stu-id="8d790-111">ResourceName</span></span>| <span data-ttu-id="8d790-112">Le nom de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="8d790-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="8d790-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="8d790-113">NodeName</span></span>| <span data-ttu-id="8d790-114">Les nœuds cible de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="8d790-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="8d790-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="8d790-115">RetryIntervalSec</span></span>| <span data-ttu-id="8d790-116">Le nombre de secondes avant la nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="8d790-116">The number of seconds before retrying.</span></span> <span data-ttu-id="8d790-117">Le minimum est 1.</span><span class="sxs-lookup"><span data-stu-id="8d790-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="8d790-118">RetryCount</span><span class="sxs-lookup"><span data-stu-id="8d790-118">RetryCount</span></span>| <span data-ttu-id="8d790-119">Le nombre maximum de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="8d790-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="8d790-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="8d790-120">ThrottleLimit</span></span>| <span data-ttu-id="8d790-121">Le nombre de machines à connecter simultanément.</span><span class="sxs-lookup"><span data-stu-id="8d790-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="8d790-122">La valeur par défaut est new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="8d790-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="8d790-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8d790-123">DependsOn</span></span> | <span data-ttu-id="8d790-124">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="8d790-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8d790-125">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8d790-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="8d790-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d790-126">Example</span></span>

<span data-ttu-id="8d790-127">Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="8d790-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

