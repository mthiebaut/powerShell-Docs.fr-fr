---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 8457189538ceb0181a8e65b57a9fc3e911cbcec4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="849f0-103">Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="849f0-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="849f0-104">Envoie le document de configuration au nœud géré et l’enregistre comme une modification en attente.</span><span class="sxs-lookup"><span data-stu-id="849f0-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="849f0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="849f0-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="849f0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="849f0-106">Parameters</span></span>
----------

<span data-ttu-id="849f0-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="849f0-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="849f0-108">Données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="849f0-108">The environment data for the configuration.</span></span>

<span data-ttu-id="849f0-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="849f0-109">*force* \[in\]</span></span>  
<span data-ttu-id="849f0-110">**true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="849f0-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="849f0-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="849f0-111">Return value</span></span>
------------

<span data-ttu-id="849f0-112">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="849f0-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="849f0-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="849f0-113">Remarks</span></span>

<span data-ttu-id="849f0-114">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="849f0-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="849f0-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="849f0-115">Requirements</span></span>
------------
><span data-ttu-id="849f0-116">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="849f0-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="849f0-117">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="849f0-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="849f0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="849f0-118">See also</span></span>


[<span data-ttu-id="849f0-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="849f0-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



