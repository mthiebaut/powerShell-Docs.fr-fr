---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: dadb6912af2e4450381958ed465799056da49946
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0cc07-103">Méthode StopConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0cc07-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0cc07-104">Arrête la modification de la configuration en cours.</span><span class="sxs-lookup"><span data-stu-id="0cc07-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="0cc07-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cc07-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="0cc07-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0cc07-106">Parameters</span></span>
----------

<span data-ttu-id="0cc07-107">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="0cc07-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="0cc07-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0cc07-108">Return value</span></span>
------------

<span data-ttu-id="0cc07-109">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0cc07-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0cc07-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="0cc07-110">Remarks</span></span>

<span data-ttu-id="0cc07-111">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="0cc07-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0cc07-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0cc07-112">Requirements</span></span>
------------
><span data-ttu-id="0cc07-113">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0cc07-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0cc07-114">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0cc07-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0cc07-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cc07-115">See also</span></span>


[<span data-ttu-id="0cc07-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0cc07-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)