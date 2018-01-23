---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e5d10-103">Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e5d10-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e5d10-104">Supprime les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="e5d10-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="e5d10-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5d10-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="e5d10-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e5d10-106">Parameters</span></span>
----------

<span data-ttu-id="e5d10-107">*Stage* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e5d10-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="e5d10-108">Spécifie le document de configuration à supprimer.</span><span class="sxs-lookup"><span data-stu-id="e5d10-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="e5d10-109">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="e5d10-109">The following values are valid:</span></span>

|<span data-ttu-id="e5d10-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="e5d10-110">Value</span></span> |<span data-ttu-id="e5d10-111">Description</span><span class="sxs-lookup"><span data-stu-id="e5d10-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="e5d10-112">**1**</span><span class="sxs-lookup"><span data-stu-id="e5d10-112">**1**</span></span> | <span data-ttu-id="e5d10-113">Document de configuration **Current** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="e5d10-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="e5d10-114">**2**</span><span class="sxs-lookup"><span data-stu-id="e5d10-114">**2**</span></span> | <span data-ttu-id="e5d10-115">Document de configuration **Pending** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="e5d10-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="e5d10-116">**4**</span><span class="sxs-lookup"><span data-stu-id="e5d10-116">**4**</span></span> | <span data-ttu-id="e5d10-117">Document de configuration **Previous** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="e5d10-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="e5d10-118">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e5d10-118">*Force* \[in\]</span></span>  
<span data-ttu-id="e5d10-119">**true** pour forcer la suppression de la configuration.</span><span class="sxs-lookup"><span data-stu-id="e5d10-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="e5d10-120">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e5d10-120">Return value</span></span>
------------

<span data-ttu-id="e5d10-121">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e5d10-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5d10-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="e5d10-122">Remarks</span></span>

<span data-ttu-id="e5d10-123">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="e5d10-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5d10-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e5d10-124">Requirements</span></span>
------------
><span data-ttu-id="e5d10-125">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e5d10-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e5d10-126">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e5d10-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e5d10-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5d10-127">See also</span></span>


[<span data-ttu-id="e5d10-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e5d10-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



