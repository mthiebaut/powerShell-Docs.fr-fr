---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ab82b239ddfdb4075d9440cd66343266b3c08eda
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="154a3-103">Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="154a3-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="154a3-104">Définissez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="154a3-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="154a3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="154a3-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="154a3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="154a3-106">Parameters</span></span>
----------

<span data-ttu-id="154a3-107">*ConfigurationData* \[in\] Les données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="154a3-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="154a3-108">*force* \[in\] **true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="154a3-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="154a3-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="154a3-109">Return value</span></span>
------------

<span data-ttu-id="154a3-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="154a3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="154a3-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="154a3-111">Remarks</span></span>

<span data-ttu-id="154a3-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="154a3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="154a3-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="154a3-113">Requirements</span></span>
------------
><span data-ttu-id="154a3-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="154a3-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="154a3-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="154a3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="154a3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="154a3-116">See also</span></span>


[<span data-ttu-id="154a3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="154a3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)