---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="89e78-103">Méthode GetConfigurationResultOutput de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="89e78-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="89e78-104">Obtient la sortie de l’agent de configuration associée à un travail spécifique.</span><span class="sxs-lookup"><span data-stu-id="89e78-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="89e78-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89e78-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="89e78-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89e78-106">Parameters</span></span>
----------

<span data-ttu-id="89e78-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="89e78-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="89e78-108">ID du travail pour lequel obtenir les données de sortie.</span><span class="sxs-lookup"><span data-stu-id="89e78-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="89e78-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="89e78-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="89e78-110">Spécifie que la sortie doit être une continuation à partir d’un signet précédent.</span><span class="sxs-lookup"><span data-stu-id="89e78-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="89e78-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="89e78-111">*output* \[out\]</span></span>  
<span data-ttu-id="89e78-112">Sortie pour le travail spécifié.</span><span class="sxs-lookup"><span data-stu-id="89e78-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="89e78-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="89e78-113">Return value</span></span>
------------

<span data-ttu-id="89e78-114">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="89e78-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="89e78-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="89e78-115">Remarks</span></span>

<span data-ttu-id="89e78-116">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="89e78-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="89e78-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="89e78-117">Requirements</span></span>
------------
><span data-ttu-id="89e78-118">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="89e78-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="89e78-119">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="89e78-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="89e78-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89e78-120">See also</span></span>


[<span data-ttu-id="89e78-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="89e78-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



