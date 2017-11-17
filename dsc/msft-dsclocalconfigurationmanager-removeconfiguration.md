---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="05e93-103">Méthode RemoveConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="05e93-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="05e93-104">Supprime les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="05e93-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="05e93-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05e93-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="05e93-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05e93-106">Parameters</span></span>
----------

<span data-ttu-id="05e93-107">*Stage* \[in\]</span><span class="sxs-lookup"><span data-stu-id="05e93-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="05e93-108">Spécifie le document de configuration à supprimer.</span><span class="sxs-lookup"><span data-stu-id="05e93-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="05e93-109">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="05e93-109">The following values are valid:</span></span>

|<span data-ttu-id="05e93-110">Value</span><span class="sxs-lookup"><span data-stu-id="05e93-110">Value</span></span> |<span data-ttu-id="05e93-111">Description</span><span class="sxs-lookup"><span data-stu-id="05e93-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="05e93-112">**1**</span><span class="sxs-lookup"><span data-stu-id="05e93-112">**1**</span></span> | <span data-ttu-id="05e93-113">Document de configuration **Current** (current.mof).</span><span class="sxs-lookup"><span data-stu-id="05e93-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="05e93-114">**2**</span><span class="sxs-lookup"><span data-stu-id="05e93-114">**2**</span></span> | <span data-ttu-id="05e93-115">Document de configuration **Pending** (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="05e93-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="05e93-116">**4**</span><span class="sxs-lookup"><span data-stu-id="05e93-116">**4**</span></span> | <span data-ttu-id="05e93-117">Document de configuration **Previous** (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="05e93-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="05e93-118">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="05e93-118">*Force* \[in\]</span></span>  
<span data-ttu-id="05e93-119">**true** pour forcer la suppression de la configuration.</span><span class="sxs-lookup"><span data-stu-id="05e93-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="05e93-120">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="05e93-120">Return value</span></span>
------------

<span data-ttu-id="05e93-121">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="05e93-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="05e93-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="05e93-122">Remarks</span></span>

<span data-ttu-id="05e93-123">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="05e93-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="05e93-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="05e93-124">Requirements</span></span>
------------
><span data-ttu-id="05e93-125">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="05e93-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="05e93-126">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="05e93-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="05e93-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05e93-127">See also</span></span>


[<span data-ttu-id="05e93-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="05e93-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



