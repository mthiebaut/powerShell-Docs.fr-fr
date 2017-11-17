---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5c878-103">Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5c878-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5c878-104">Définissez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="5c878-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="5c878-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c878-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="5c878-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5c878-106">Parameters</span></span>
----------

<span data-ttu-id="5c878-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="5c878-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="5c878-108">Données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="5c878-108">The environment data for the configuration.</span></span>

<span data-ttu-id="5c878-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="5c878-109">*force* \[in\]</span></span>  
<span data-ttu-id="5c878-110">**true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="5c878-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="5c878-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="5c878-111">Return value</span></span>
------------

<span data-ttu-id="5c878-112">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5c878-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c878-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="5c878-113">Remarks</span></span>

<span data-ttu-id="5c878-114">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="5c878-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5c878-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5c878-115">Requirements</span></span>
------------
><span data-ttu-id="5c878-116">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5c878-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5c878-117">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5c878-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5c878-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c878-118">See also</span></span>


[<span data-ttu-id="5c878-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5c878-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



