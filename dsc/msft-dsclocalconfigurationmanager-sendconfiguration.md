---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 07ae48dd456e68be4ad0b09127ba9801359fd101
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="79cc0-103">Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="79cc0-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="79cc0-104">Envoie le document de configuration au nœud géré et l’enregistre comme une modification en attente.</span><span class="sxs-lookup"><span data-stu-id="79cc0-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="79cc0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79cc0-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="79cc0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79cc0-106">Parameters</span></span>
----------

<span data-ttu-id="79cc0-107">*ConfigurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="79cc0-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="79cc0-108">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="79cc0-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="79cc0-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="79cc0-109">Return value</span></span>
------------

<span data-ttu-id="79cc0-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="79cc0-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="79cc0-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="79cc0-111">Remarks</span></span>

<span data-ttu-id="79cc0-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="79cc0-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="79cc0-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="79cc0-113">Requirements</span></span>
------------
><span data-ttu-id="79cc0-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="79cc0-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="79cc0-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="79cc0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="79cc0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79cc0-116">See also</span></span>


[<span data-ttu-id="79cc0-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="79cc0-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)