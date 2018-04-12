---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Méthode GetConfigurationStatus de la classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: dde4ac003b346018561481e05ca7374475f9ff1d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3ee09-103">Méthode GetConfigurationStatus de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3ee09-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3ee09-104">Obtenez l’historique des états de la configuration.</span><span class="sxs-lookup"><span data-stu-id="3ee09-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="3ee09-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ee09-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="3ee09-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3ee09-106">Parameters</span></span>
----------

<span data-ttu-id="3ee09-107">*All* \[in\] **true** si cette méthode doit retourner des informations sur toutes les exécutions de configuration sur l’ordinateur, dont l’application de la configuration et la vérification de cohérence.</span><span class="sxs-lookup"><span data-stu-id="3ee09-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="3ee09-108">*configurationStatus* \[out\] En retour, contient une instance incorporée de la classe **MSFT_DSCConfigurationStatus** qui définit les paramètres.</span><span class="sxs-lookup"><span data-stu-id="3ee09-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="3ee09-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="3ee09-109">Return value</span></span>
------------

<span data-ttu-id="3ee09-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3ee09-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ee09-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="3ee09-111">Remarks</span></span>

<span data-ttu-id="3ee09-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="3ee09-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ee09-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3ee09-113">Requirements</span></span>
------------
><span data-ttu-id="3ee09-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3ee09-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="3ee09-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3ee09-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="3ee09-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ee09-116">See also</span></span>


[<span data-ttu-id="3ee09-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3ee09-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)