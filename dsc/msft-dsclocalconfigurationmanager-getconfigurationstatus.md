---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode GetConfigurationStatus de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9e8d2-103">Méthode GetConfigurationStatus de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9e8d2-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9e8d2-104">Obtenez l’historique des états de la configuration.</span><span class="sxs-lookup"><span data-stu-id="9e8d2-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="9e8d2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e8d2-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="9e8d2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9e8d2-106">Parameters</span></span>
----------

<span data-ttu-id="9e8d2-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9e8d2-107">*All* \[in\]</span></span>  
<span data-ttu-id="9e8d2-108">**true** si cette méthode doit retourner des informations sur toutes les exécutions de configuration sur l’ordinateur, dont l’application de la configuration et la vérification de cohérence.</span><span class="sxs-lookup"><span data-stu-id="9e8d2-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="9e8d2-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="9e8d2-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="9e8d2-110">En retour, contient une instance incorporée de la classe **MSFT_DSCConfigurationStatus** qui définit les paramètres.</span><span class="sxs-lookup"><span data-stu-id="9e8d2-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="9e8d2-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9e8d2-111">Return value</span></span>
------------

<span data-ttu-id="9e8d2-112">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="9e8d2-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e8d2-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="9e8d2-113">Remarks</span></span>

<span data-ttu-id="9e8d2-114">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="9e8d2-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e8d2-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9e8d2-115">Requirements</span></span>
------------
><span data-ttu-id="9e8d2-116">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9e8d2-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9e8d2-117">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9e8d2-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9e8d2-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e8d2-118">See also</span></span>


[<span data-ttu-id="9e8d2-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9e8d2-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



