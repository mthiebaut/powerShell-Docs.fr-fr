---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode ResourceGet de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 7d8b185c49778253dcb4e983ad948775c4cb0842
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="01de6-103">Méthode ResourceGet de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="01de6-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="01de6-104">Appelle directement la méthode **Get** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="01de6-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="01de6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01de6-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="01de6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="01de6-106">Parameters</span></span>
----------

<span data-ttu-id="01de6-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="01de6-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="01de6-108">Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="01de6-108">The name of the resource to call.</span></span>

<span data-ttu-id="01de6-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="01de6-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="01de6-110">Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="01de6-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="01de6-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="01de6-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="01de6-112">Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="01de6-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="01de6-113">Utilisez l’applet de commande [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="01de6-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="01de6-114">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="01de6-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="01de6-115">En retour, contient une instance incorporée des configurations.</span><span class="sxs-lookup"><span data-stu-id="01de6-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="01de6-116">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="01de6-116">Return value</span></span>
------------

<span data-ttu-id="01de6-117">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="01de6-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="01de6-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="01de6-118">Remarks</span></span>

<span data-ttu-id="01de6-119">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="01de6-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="01de6-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="01de6-120">Requirements</span></span>
------------
><span data-ttu-id="01de6-121">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="01de6-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="01de6-122">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="01de6-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="01de6-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01de6-123">See also</span></span>


[<span data-ttu-id="01de6-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="01de6-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



