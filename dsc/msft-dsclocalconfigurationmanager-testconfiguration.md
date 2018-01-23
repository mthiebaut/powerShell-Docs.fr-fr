---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode TestConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 04f0f3146473dc71f492086449d9dce5467c55db
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6ce2d-103">Méthode TestConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6ce2d-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6ce2d-104">Envoie le document de configuration au nœud géré et vérifie la configuration actuelle par rapport au document.</span><span class="sxs-lookup"><span data-stu-id="6ce2d-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="6ce2d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ce2d-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="6ce2d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6ce2d-106">Parameters</span></span>
----------

<span data-ttu-id="6ce2d-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="6ce2d-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="6ce2d-108">Données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="6ce2d-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="6ce2d-109">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="6ce2d-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="6ce2d-110">En retour, indique si le nœud géré est dans l’état spécifié par le document de configuration.</span><span class="sxs-lookup"><span data-stu-id="6ce2d-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="6ce2d-111">*ResourcesInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="6ce2d-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="6ce2d-112">En retour, contient une instance incorporée de la classe **MSFT_ResourceInDesiredState** qui spécifie les ressources qui sont dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="6ce2d-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="6ce2d-113">*ResourcesNotInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="6ce2d-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="6ce2d-114">En retour, contient une instance incorporée de la classe **MSFT_ResourceNotInDesiredState** qui spécifie les ressources qui ne sont pas dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="6ce2d-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="6ce2d-115">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="6ce2d-115">Return value</span></span>
------------

<span data-ttu-id="6ce2d-116">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6ce2d-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ce2d-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="6ce2d-117">Remarks</span></span>

<span data-ttu-id="6ce2d-118">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="6ce2d-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6ce2d-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6ce2d-119">Requirements</span></span>
------------
><span data-ttu-id="6ce2d-120">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6ce2d-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="6ce2d-121">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6ce2d-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="6ce2d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ce2d-122">See also</span></span>


[<span data-ttu-id="6ce2d-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6ce2d-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



