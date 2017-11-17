---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fce20-103">Méthode RollBack de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fce20-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fce20-104">Restaure la configuration à une version précédente.</span><span class="sxs-lookup"><span data-stu-id="fce20-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="fce20-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fce20-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="fce20-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fce20-106">Parameters</span></span>
----------

<span data-ttu-id="fce20-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="fce20-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="fce20-108">Spécifie la configuration demandée.</span><span class="sxs-lookup"><span data-stu-id="fce20-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="fce20-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="fce20-109">Return value</span></span>
------------

<span data-ttu-id="fce20-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="fce20-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fce20-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="fce20-111">Remarks</span></span>

<span data-ttu-id="fce20-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="fce20-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fce20-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fce20-113">Requirements</span></span>
------------
><span data-ttu-id="fce20-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fce20-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="fce20-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fce20-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="fce20-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fce20-116">See also</span></span>


[<span data-ttu-id="fce20-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fce20-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



