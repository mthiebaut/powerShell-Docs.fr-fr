---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode SendConfigurationApplyAsync de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e680bfd1c5b39d364c90cf5ef6b43d0a568af23a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="49488-103">Méthode SendConfigurationApplyAsync de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="49488-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="49488-104">Envoie le document de configuration de façon asynchrone au nœud géré et utilise l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="49488-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="49488-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49488-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="49488-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49488-106">Parameters</span></span>
----------

<span data-ttu-id="49488-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="49488-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="49488-108">Données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="49488-108">The environment data for the configuration.</span></span>

<span data-ttu-id="49488-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="49488-109">*force* \[in\]</span></span>  
<span data-ttu-id="49488-110">**true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="49488-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="49488-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="49488-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="49488-112">ID du travail pour lequel envoyer la configuration.</span><span class="sxs-lookup"><span data-stu-id="49488-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="49488-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="49488-113">Return value</span></span>
------------

<span data-ttu-id="49488-114">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="49488-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="49488-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="49488-115">Remarks</span></span>

<span data-ttu-id="49488-116">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="49488-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="49488-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="49488-117">Requirements</span></span>
------------
><span data-ttu-id="49488-118">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="49488-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="49488-119">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="49488-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="49488-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49488-120">See also</span></span>


[<span data-ttu-id="49488-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="49488-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



