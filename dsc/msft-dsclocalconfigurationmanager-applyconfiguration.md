---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 72fbedf30e5058d8003ed620400d6b443d50dff6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="27af2-103">Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="27af2-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="27af2-104">Utilise l’agent de configuration pour appliquer la configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="27af2-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="27af2-105">S’il n’existe aucune configuration en attente, cette méthode applique de nouveau la configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="27af2-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="27af2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27af2-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="27af2-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="27af2-107">Parameters</span></span>
----------

<span data-ttu-id="27af2-108">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="27af2-108">*force* \[in\]</span></span>  
<span data-ttu-id="27af2-109">Si la valeur est **true**, la configuration actuelle est de nouveau appliquée, même s’il existe une configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="27af2-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="27af2-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="27af2-110">Return value</span></span>
------------

<span data-ttu-id="27af2-111">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="27af2-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="27af2-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="27af2-112">Remarks</span></span>

<span data-ttu-id="27af2-113">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="27af2-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="27af2-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="27af2-114">Requirements</span></span>
------------
><span data-ttu-id="27af2-115">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="27af2-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="27af2-116">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="27af2-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="27af2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27af2-117">See also</span></span>


[<span data-ttu-id="27af2-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="27af2-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



