---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode ResourceGet de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: df90cb6859413c94be992c8cbc30171e9bd3d6de
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ba1c2-103">Méthode ResourceGet de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ba1c2-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ba1c2-104">Appelle directement la méthode **Get** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="ba1c2-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="ba1c2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba1c2-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="ba1c2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ba1c2-106">Parameters</span></span>
----------

<span data-ttu-id="ba1c2-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ba1c2-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="ba1c2-108">Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="ba1c2-108">The name of the resource to call.</span></span>

<span data-ttu-id="ba1c2-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ba1c2-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="ba1c2-110">Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="ba1c2-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="ba1c2-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="ba1c2-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="ba1c2-112">Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="ba1c2-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="ba1c2-113">Utilisez l’applet de commande [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="ba1c2-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="ba1c2-114">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="ba1c2-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="ba1c2-115">En retour, contient une instance incorporée des configurations.</span><span class="sxs-lookup"><span data-stu-id="ba1c2-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="ba1c2-116">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ba1c2-116">Return value</span></span>
------------

<span data-ttu-id="ba1c2-117">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ba1c2-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba1c2-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="ba1c2-118">Remarks</span></span>

<span data-ttu-id="ba1c2-119">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="ba1c2-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba1c2-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ba1c2-120">Requirements</span></span>
------------
><span data-ttu-id="ba1c2-121">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ba1c2-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ba1c2-122">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba1c2-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ba1c2-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba1c2-123">See also</span></span>


[<span data-ttu-id="ba1c2-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ba1c2-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



