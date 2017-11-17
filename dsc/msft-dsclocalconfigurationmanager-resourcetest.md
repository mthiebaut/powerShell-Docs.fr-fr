---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 73d7d543505a3768a0660084345d3858e055514f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="425f3-103">Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="425f3-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="425f3-104">Appelle directement la méthode **Test** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="425f3-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="425f3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="425f3-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="425f3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="425f3-106">Parameters</span></span>
----------

<span data-ttu-id="425f3-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="425f3-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="425f3-108">Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="425f3-108">The name of the resource to call.</span></span>

<span data-ttu-id="425f3-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="425f3-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="425f3-110">Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="425f3-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="425f3-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="425f3-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="425f3-112">Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="425f3-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="425f3-113">Utilisez l’applet de commande [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="425f3-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="425f3-114">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="425f3-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="425f3-115">En retour, cette propriété est définie avec la valeur **true** si le nœud cible est dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="425f3-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="425f3-116">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="425f3-116">Return value</span></span>
------------

<span data-ttu-id="425f3-117">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="425f3-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="425f3-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="425f3-118">Remarks</span></span>

<span data-ttu-id="425f3-119">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="425f3-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="425f3-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="425f3-120">Requirements</span></span>
------------
><span data-ttu-id="425f3-121">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="425f3-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="425f3-122">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="425f3-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="425f3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="425f3-123">See also</span></span>


[<span data-ttu-id="425f3-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="425f3-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



