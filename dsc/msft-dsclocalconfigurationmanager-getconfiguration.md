---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode GetConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 60f4b49575dbb28ce74af0500e6982ec5d2e7a66
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b2766-103">Méthode GetConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b2766-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b2766-104">Envoie le document de configuration au nœud géré et utilise la méthode **Get** de l’agent de configuration pour appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="b2766-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="b2766-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2766-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="b2766-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2766-106">Parameters</span></span>
----------

<span data-ttu-id="b2766-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b2766-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="b2766-108">Spécifie les données de configuration à envoyer.</span><span class="sxs-lookup"><span data-stu-id="b2766-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="b2766-109">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="b2766-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="b2766-110">En retour, contient une instance incorporée des configurations.</span><span class="sxs-lookup"><span data-stu-id="b2766-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="b2766-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b2766-111">Return value</span></span>
------------

<span data-ttu-id="b2766-112">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b2766-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2766-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="b2766-113">Remarks</span></span>

<span data-ttu-id="b2766-114">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="b2766-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b2766-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b2766-115">Requirements</span></span>
------------
><span data-ttu-id="b2766-116">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b2766-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b2766-117">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2766-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b2766-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2766-118">See also</span></span>


[<span data-ttu-id="b2766-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b2766-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



