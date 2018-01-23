---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WaitForSome
ms.openlocfilehash: cbe16c543f0eeb62dbe1fb439af2f9147f1bc210
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="f3579-103">Ressource DSC WaitForSome</span><span class="sxs-lookup"><span data-stu-id="f3579-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="f3579-104">S’applique à : Windows PowerShell 5.0 et ultérieur</span><span class="sxs-lookup"><span data-stu-id="f3579-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="f3579-105">La ressource de configuration d’état souhaité (DSC) **WaitForAny** peut être utilisée dans un bloc de nœud dans une [configuration DSC](configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="f3579-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="f3579-106">La ressource réussit si la ressource spécifiée dans la propriété **ResourceName** est dans l’état souhaité sur un nombre minimal de nœuds (spécifié par **NodeCount**) défini par la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="f3579-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="f3579-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3579-107">Syntax</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a><span data-ttu-id="f3579-108">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f3579-108">Properties</span></span>

|  <span data-ttu-id="f3579-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="f3579-109">Property</span></span>  |  <span data-ttu-id="f3579-110">Description</span><span class="sxs-lookup"><span data-stu-id="f3579-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="f3579-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="f3579-111">NodeCount</span></span>| <span data-ttu-id="f3579-112">Le nombre minimal de nœuds qui doivent être dans l’état souhaité pour que cette ressource réussisse.</span><span class="sxs-lookup"><span data-stu-id="f3579-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="f3579-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="f3579-113">NodeName</span></span>| <span data-ttu-id="f3579-114">Les nœuds cible de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="f3579-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="f3579-115">Nom_ressource</span><span class="sxs-lookup"><span data-stu-id="f3579-115">ResourceName</span></span>| <span data-ttu-id="f3579-116">Le nom de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="f3579-116">The resource name to depend on.</span></span>| 
| <span data-ttu-id="f3579-117">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="f3579-117">RetryIntervalSec</span></span>| <span data-ttu-id="f3579-118">Le nombre de secondes avant la nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="f3579-118">The number of seconds before retrying.</span></span> <span data-ttu-id="f3579-119">Le minimum est 1.</span><span class="sxs-lookup"><span data-stu-id="f3579-119">Minimum is 1.</span></span>| 
| <span data-ttu-id="f3579-120">RetryCount</span><span class="sxs-lookup"><span data-stu-id="f3579-120">RetryCount</span></span>| <span data-ttu-id="f3579-121">Le nombre maximum de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="f3579-121">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="f3579-122">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="f3579-122">ThrottleLimit</span></span>| <span data-ttu-id="f3579-123">Le nombre de machines à connecter simultanément.</span><span class="sxs-lookup"><span data-stu-id="f3579-123">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="f3579-124">La valeur par défaut est new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="f3579-124">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="f3579-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f3579-125">DependsOn</span></span> | <span data-ttu-id="f3579-126">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="f3579-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f3579-127">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f3579-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="f3579-128">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f3579-128">PsDscRunAsCredential</span></span> | <span data-ttu-id="f3579-129">Voir [Exécution de DSC avec les informations d’identification de l’utilisateur](https://docs.microsoft.com/en-us/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="f3579-129">See [Using DSC with User Credentials](https://docs.microsoft.com/en-us/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="f3579-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3579-130">Example</span></span>

<span data-ttu-id="f3579-131">Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="f3579-131">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

