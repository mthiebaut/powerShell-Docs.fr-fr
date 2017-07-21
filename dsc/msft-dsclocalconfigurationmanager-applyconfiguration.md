---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="91047-103">Méthode ApplyConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="91047-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="91047-104">Utilise l’agent de configuration pour appliquer la configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="91047-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="91047-105">S’il n’existe aucune configuration en attente, cette méthode applique de nouveau la configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="91047-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="91047-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91047-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="91047-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="91047-107">Parameters</span></span>
----------

<span data-ttu-id="91047-108">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="91047-108">*force* \[in\]</span></span>  
<span data-ttu-id="91047-109">Si la valeur est **true**, la configuration actuelle est de nouveau appliquée, même s’il existe une configuration en attente.</span><span class="sxs-lookup"><span data-stu-id="91047-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="91047-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="91047-110">Return value</span></span>
------------

<span data-ttu-id="91047-111">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="91047-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="91047-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="91047-112">Remarks</span></span>

<span data-ttu-id="91047-113">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="91047-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="91047-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="91047-114">Requirements</span></span>
------------
><span data-ttu-id="91047-115">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="91047-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="91047-116">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="91047-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="91047-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91047-117">See also</span></span>


[<span data-ttu-id="91047-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="91047-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



