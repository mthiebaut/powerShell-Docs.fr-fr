---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9fe41fa806a6abff1d36dadd0c041a5cf0e78caf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ae2ca-103">Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ae2ca-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ae2ca-104">Active le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="ae2ca-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="ae2ca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae2ca-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="ae2ca-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ae2ca-106">Parameters</span></span>
----------

<span data-ttu-id="ae2ca-107">*BreakAll* \[in\] Définit un point d’arrêt au niveau de chaque ligne dans le script de ressources.</span><span class="sxs-lookup"><span data-stu-id="ae2ca-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="ae2ca-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ae2ca-108">Return value</span></span>
------------

<span data-ttu-id="ae2ca-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ae2ca-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae2ca-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="ae2ca-110">Remarks</span></span>

<span data-ttu-id="ae2ca-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="ae2ca-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ae2ca-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ae2ca-112">Requirements</span></span>
------------
><span data-ttu-id="ae2ca-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ae2ca-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ae2ca-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ae2ca-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ae2ca-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae2ca-115">See also</span></span>


[<span data-ttu-id="ae2ca-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ae2ca-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)