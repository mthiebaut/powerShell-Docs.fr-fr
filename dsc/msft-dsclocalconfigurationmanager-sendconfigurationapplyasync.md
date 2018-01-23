---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode SendConfigurationApplyAsync de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="373ca-103">Méthode SendConfigurationApplyAsync de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="373ca-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="373ca-104">Envoie le document de configuration de façon asynchrone au nœud géré et utilise l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="373ca-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="373ca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="373ca-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="373ca-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="373ca-106">Parameters</span></span>
----------

<span data-ttu-id="373ca-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="373ca-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="373ca-108">Données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="373ca-108">The environment data for the configuration.</span></span>

<span data-ttu-id="373ca-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="373ca-109">*force* \[in\]</span></span>  
<span data-ttu-id="373ca-110">**true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="373ca-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="373ca-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="373ca-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="373ca-112">ID du travail pour lequel envoyer la configuration.</span><span class="sxs-lookup"><span data-stu-id="373ca-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="373ca-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="373ca-113">Return value</span></span>
------------

<span data-ttu-id="373ca-114">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="373ca-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="373ca-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="373ca-115">Remarks</span></span>

<span data-ttu-id="373ca-116">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="373ca-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="373ca-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="373ca-117">Requirements</span></span>
------------
><span data-ttu-id="373ca-118">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="373ca-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="373ca-119">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="373ca-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="373ca-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="373ca-120">See also</span></span>


[<span data-ttu-id="373ca-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="373ca-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



