---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WaitForAny
ms.openlocfilehash: 43922dbcccb6d06d7d9edfcf16ce4eb107e9d4e6
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="864f3-103">Ressource DSC WaitForAny</span><span class="sxs-lookup"><span data-stu-id="864f3-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="864f3-104">S’applique à : Windows PowerShell 5.1 et ultérieur</span><span class="sxs-lookup"><span data-stu-id="864f3-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="864f3-105">La ressource de configuration d’état souhaité (DSC) **WaitForSome** peut être utilisée dans un bloc de nœud dans une [configuration DSC](configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="864f3-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="864f3-106">La ressource réussit si la ressource spécifiée par la propriété **ResourceName** est dans l’état souhaité sur un des nœuds cible définis dans la propriété **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="864f3-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="864f3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="864f3-107">Syntax</span></span>

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="864f3-108">Propriétés</span><span class="sxs-lookup"><span data-stu-id="864f3-108">Properties</span></span>

|  <span data-ttu-id="864f3-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="864f3-109">Property</span></span>  |  <span data-ttu-id="864f3-110">Description</span><span class="sxs-lookup"><span data-stu-id="864f3-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="864f3-111">Nom_ressource</span><span class="sxs-lookup"><span data-stu-id="864f3-111">ResourceName</span></span>| <span data-ttu-id="864f3-112">Le nom de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="864f3-112">The resource name to depend on.</span></span> <span data-ttu-id="864f3-113">Si cette ressource appartient à une configuration différente, mettez en forme le nom comme ceci : « [__type_ressource__]__nom_ressource__::[__nom_configuration__]::[__nom_configuration__] »</span><span class="sxs-lookup"><span data-stu-id="864f3-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>| 
| <span data-ttu-id="864f3-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="864f3-114">NodeName</span></span>| <span data-ttu-id="864f3-115">Les nœuds cible de la ressource de la dépendance.</span><span class="sxs-lookup"><span data-stu-id="864f3-115">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="864f3-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="864f3-116">RetryIntervalSec</span></span>| <span data-ttu-id="864f3-117">Le nombre de secondes avant la nouvelle tentative.</span><span class="sxs-lookup"><span data-stu-id="864f3-117">The number of seconds before retrying.</span></span> <span data-ttu-id="864f3-118">Le minimum est 1.</span><span class="sxs-lookup"><span data-stu-id="864f3-118">Minimum is 1.</span></span>| 
| <span data-ttu-id="864f3-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="864f3-119">RetryCount</span></span>| <span data-ttu-id="864f3-120">Le nombre maximum de nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="864f3-120">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="864f3-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="864f3-121">ThrottleLimit</span></span>| <span data-ttu-id="864f3-122">Le nombre de machines à connecter simultanément.</span><span class="sxs-lookup"><span data-stu-id="864f3-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="864f3-123">La valeur par défaut est new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="864f3-123">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="864f3-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="864f3-124">DependsOn</span></span> | <span data-ttu-id="864f3-125">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="864f3-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="864f3-126">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="864f3-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="864f3-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="864f3-127">Example</span></span>

<span data-ttu-id="864f3-128">Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="864f3-128">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

