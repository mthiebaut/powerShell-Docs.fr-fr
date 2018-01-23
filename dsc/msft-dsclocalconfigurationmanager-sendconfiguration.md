---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 72c59b5aad293fa561146e5ad6822f27f40f321f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a0841-103">Méthode SendConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a0841-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a0841-104">Envoie le document de configuration au nœud géré et l’enregistre comme une modification en attente.</span><span class="sxs-lookup"><span data-stu-id="a0841-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="a0841-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0841-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="a0841-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0841-106">Parameters</span></span>
----------

<span data-ttu-id="a0841-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="a0841-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="a0841-108">Données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="a0841-108">The environment data for the configuration.</span></span>

<span data-ttu-id="a0841-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="a0841-109">*force* \[in\]</span></span>  
<span data-ttu-id="a0841-110">**true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="a0841-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="a0841-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a0841-111">Return value</span></span>
------------

<span data-ttu-id="a0841-112">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a0841-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0841-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="a0841-113">Remarks</span></span>

<span data-ttu-id="a0841-114">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="a0841-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a0841-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a0841-115">Requirements</span></span>
------------
><span data-ttu-id="a0841-116">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a0841-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a0841-117">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a0841-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a0841-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0841-118">See also</span></span>


[<span data-ttu-id="a0841-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a0841-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



