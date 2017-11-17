---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode GetConfigurationStatus de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e02ed81a7b8436323bc68aaa2587a445e6a5adf9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fb886-103">Méthode GetConfigurationStatus de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fb886-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fb886-104">Obtenez l’historique des états de la configuration.</span><span class="sxs-lookup"><span data-stu-id="fb886-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="fb886-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb886-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="fb886-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fb886-106">Parameters</span></span>
----------

<span data-ttu-id="fb886-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="fb886-107">*All* \[in\]</span></span>  
<span data-ttu-id="fb886-108">**true** si cette méthode doit retourner des informations sur toutes les exécutions de configuration sur l’ordinateur, dont l’application de la configuration et la vérification de cohérence.</span><span class="sxs-lookup"><span data-stu-id="fb886-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="fb886-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="fb886-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="fb886-110">En retour, contient une instance incorporée de la classe **MSFT_DSCConfigurationStatus** qui définit les paramètres.</span><span class="sxs-lookup"><span data-stu-id="fb886-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="fb886-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="fb886-111">Return value</span></span>
------------

<span data-ttu-id="fb886-112">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="fb886-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fb886-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="fb886-113">Remarks</span></span>

<span data-ttu-id="fb886-114">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="fb886-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fb886-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fb886-115">Requirements</span></span>
------------
><span data-ttu-id="fb886-116">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fb886-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="fb886-117">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fb886-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="fb886-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb886-118">See also</span></span>


[<span data-ttu-id="fb886-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fb886-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



