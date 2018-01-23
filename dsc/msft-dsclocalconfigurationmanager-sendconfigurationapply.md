---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode SendConfigurationApply de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 20f732d35860cccde4e507dc6916e27d0cf8c5f6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4afe4-103">Méthode SendConfigurationApply de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4afe4-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4afe4-104">Envoie le document de configuration au nœud géré et utilise l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="4afe4-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="4afe4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4afe4-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="4afe4-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4afe4-106">Parameters</span></span>
----------

<span data-ttu-id="4afe4-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4afe4-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="4afe4-108">Données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="4afe4-108">The environment data for the configuration.</span></span>

<span data-ttu-id="4afe4-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4afe4-109">*force* \[in\]</span></span>  
<span data-ttu-id="4afe4-110">**true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="4afe4-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="4afe4-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="4afe4-111">Return value</span></span>
------------

<span data-ttu-id="4afe4-112">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4afe4-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4afe4-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="4afe4-113">Remarks</span></span>

<span data-ttu-id="4afe4-114">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="4afe4-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4afe4-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4afe4-115">Requirements</span></span>
------------
><span data-ttu-id="4afe4-116">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4afe4-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4afe4-117">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4afe4-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4afe4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4afe4-118">See also</span></span>


[<span data-ttu-id="4afe4-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4afe4-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



