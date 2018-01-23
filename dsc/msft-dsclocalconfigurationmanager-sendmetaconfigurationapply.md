---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 350555220757b1939b1de34ab423e963635eb53c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2cb30-103">Méthode SendMetaConfigurationApply de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2cb30-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2cb30-104">Définissez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="2cb30-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="2cb30-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cb30-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="2cb30-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2cb30-106">Parameters</span></span>
----------

<span data-ttu-id="2cb30-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="2cb30-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="2cb30-108">Données d’environnement pour la configuration.</span><span class="sxs-lookup"><span data-stu-id="2cb30-108">The environment data for the configuration.</span></span>

<span data-ttu-id="2cb30-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="2cb30-109">*force* \[in\]</span></span>  
<span data-ttu-id="2cb30-110">**true** pour forcer l’arrêt de la configuration.</span><span class="sxs-lookup"><span data-stu-id="2cb30-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="2cb30-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="2cb30-111">Return value</span></span>
------------

<span data-ttu-id="2cb30-112">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2cb30-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2cb30-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="2cb30-113">Remarks</span></span>

<span data-ttu-id="2cb30-114">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="2cb30-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2cb30-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2cb30-115">Requirements</span></span>
------------
><span data-ttu-id="2cb30-116">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2cb30-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2cb30-117">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2cb30-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2cb30-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cb30-118">See also</span></span>


[<span data-ttu-id="2cb30-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2cb30-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



