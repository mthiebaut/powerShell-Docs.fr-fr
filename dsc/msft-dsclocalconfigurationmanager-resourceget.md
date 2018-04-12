---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode ResourceGet de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3fd7ae54eb3ae782156dc4619ee0b6905dfb1212
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cf630-103">Méthode ResourceGet de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cf630-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cf630-104">Appelle directement la méthode **Get** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="cf630-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="cf630-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf630-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="cf630-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf630-106">Parameters</span></span>
----------

<span data-ttu-id="cf630-107">*ResourceType* \[in\] Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="cf630-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="cf630-108">*ModuleName* \[in\] Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="cf630-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="cf630-109">*resourceProperty* \[in\] Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="cf630-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="cf630-110">Utilisez l’applet de commande [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="cf630-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="cf630-111">*configurations* \[out\] En retour, contient une instance incorporée des configurations.</span><span class="sxs-lookup"><span data-stu-id="cf630-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="cf630-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="cf630-112">Return value</span></span>
------------

<span data-ttu-id="cf630-113">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="cf630-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf630-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="cf630-114">Remarks</span></span>

<span data-ttu-id="cf630-115">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="cf630-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cf630-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cf630-116">Requirements</span></span>
------------
><span data-ttu-id="cf630-117">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cf630-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="cf630-118">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cf630-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="cf630-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf630-119">See also</span></span>


[<span data-ttu-id="cf630-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cf630-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)