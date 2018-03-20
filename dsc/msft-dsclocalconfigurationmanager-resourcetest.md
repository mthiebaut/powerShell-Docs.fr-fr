---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 799b1cd91dfacf25c0e5e734ca96d20a776103f0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8ef01-103">Méthode ResourceTest de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8ef01-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8ef01-104">Appelle directement la méthode **Test** d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="8ef01-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="8ef01-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ef01-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="8ef01-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ef01-106">Parameters</span></span>
----------

<span data-ttu-id="8ef01-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="8ef01-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="8ef01-108">Nom de la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="8ef01-108">The name of the resource to call.</span></span>

<span data-ttu-id="8ef01-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="8ef01-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="8ef01-110">Nom du module qui contient la ressource à appeler.</span><span class="sxs-lookup"><span data-stu-id="8ef01-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="8ef01-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="8ef01-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="8ef01-112">Spécifie le nom de propriété de ressource et sa valeur dans une table de hachage comme clé et valeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="8ef01-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="8ef01-113">Utilisez l’applet de commande [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) pour découvrir les propriétés de ressources et leurs types.</span><span class="sxs-lookup"><span data-stu-id="8ef01-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="8ef01-114">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="8ef01-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="8ef01-115">En retour, cette propriété est définie avec la valeur **true** si le nœud cible est dans l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="8ef01-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="8ef01-116">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="8ef01-116">Return value</span></span>
------------

<span data-ttu-id="8ef01-117">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8ef01-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ef01-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="8ef01-118">Remarks</span></span>

<span data-ttu-id="8ef01-119">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="8ef01-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8ef01-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8ef01-120">Requirements</span></span>
------------
><span data-ttu-id="8ef01-121">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8ef01-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="8ef01-122">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8ef01-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="8ef01-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ef01-123">See also</span></span>


[<span data-ttu-id="8ef01-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8ef01-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



