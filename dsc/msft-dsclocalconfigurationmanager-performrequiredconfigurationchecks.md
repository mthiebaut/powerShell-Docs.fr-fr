---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode PerformRequiredConfigurationChecks de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 687c92f2dac5e8855731713e81390ac67615231e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="98282-103">Méthode PerformRequiredConfigurationChecks de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="98282-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="98282-104">Commence une vérification de cohérence à l’aide du Planificateur de tâches.</span><span class="sxs-lookup"><span data-stu-id="98282-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="98282-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98282-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="98282-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="98282-106">Parameters</span></span>
----------

<span data-ttu-id="98282-107">*Flags* \[in\]</span><span class="sxs-lookup"><span data-stu-id="98282-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="98282-108">Masque de bits qui spécifie le type de vérification de cohérence à exécuter.</span><span class="sxs-lookup"><span data-stu-id="98282-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="98282-109">Les valeurs suivantes sont valides et peuvent être combinées à l’aide d’une opération **OR** au niveau du bit :</span><span class="sxs-lookup"><span data-stu-id="98282-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="98282-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="98282-110">Value</span></span> |<span data-ttu-id="98282-111">Description</span><span class="sxs-lookup"><span data-stu-id="98282-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="98282-112">**1**</span><span class="sxs-lookup"><span data-stu-id="98282-112">**1**</span></span> | <span data-ttu-id="98282-113">Vérification de cohérence normale.</span><span class="sxs-lookup"><span data-stu-id="98282-113">A normal consistency check.</span></span> |
|<span data-ttu-id="98282-114">**2**</span><span class="sxs-lookup"><span data-stu-id="98282-114">**2**</span></span> | <span data-ttu-id="98282-115">Poursuite d’une vérification de cohérence après un redémarrage.</span><span class="sxs-lookup"><span data-stu-id="98282-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="98282-116">Cette valeur ne doit pas être combinée avec d’autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="98282-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="98282-117">**4**</span><span class="sxs-lookup"><span data-stu-id="98282-117">**4**</span></span> | <span data-ttu-id="98282-118">La configuration doit être extraite du serveur collecteur spécifié dans la métaconfiguration du nœud.</span><span class="sxs-lookup"><span data-stu-id="98282-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="98282-119">Cette valeur doit toujours être combinée avec **1** avec une valeur de **5**.</span><span class="sxs-lookup"><span data-stu-id="98282-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="98282-120">**8**</span><span class="sxs-lookup"><span data-stu-id="98282-120">**8**</span></span> | <span data-ttu-id="98282-121">Envoyez l’état au serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="98282-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="98282-122">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="98282-122">Return value</span></span>
------------

<span data-ttu-id="98282-123">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="98282-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="98282-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="98282-124">Remarks</span></span>

<span data-ttu-id="98282-125">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="98282-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="98282-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="98282-126">Requirements</span></span>
------------
><span data-ttu-id="98282-127">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="98282-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="98282-128">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="98282-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="98282-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98282-129">See also</span></span>


[<span data-ttu-id="98282-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="98282-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



