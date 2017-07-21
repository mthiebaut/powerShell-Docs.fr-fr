---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="83dcd-103">Méthode EnableDebugConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="83dcd-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="83dcd-104">Active le débogage des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="83dcd-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="83dcd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83dcd-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="83dcd-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="83dcd-106">Parameters</span></span>
----------

<span data-ttu-id="83dcd-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="83dcd-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="83dcd-108">Définit un point d’arrêt au niveau de chaque ligne dans le script de ressources.</span><span class="sxs-lookup"><span data-stu-id="83dcd-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="83dcd-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="83dcd-109">Return value</span></span>
------------

<span data-ttu-id="83dcd-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="83dcd-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="83dcd-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="83dcd-111">Remarks</span></span>

<span data-ttu-id="83dcd-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="83dcd-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="83dcd-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="83dcd-113">Requirements</span></span>
------------
><span data-ttu-id="83dcd-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="83dcd-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="83dcd-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="83dcd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="83dcd-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83dcd-116">See also</span></span>


[<span data-ttu-id="83dcd-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="83dcd-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



