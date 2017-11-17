---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode GetMetaConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 4f209014e9fde5841a9bce743f5364e6677d1e41
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2230f-103">Méthode GetMetaConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2230f-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2230f-104">Obtenez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="2230f-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="2230f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2230f-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="2230f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2230f-106">Parameters</span></span>
----------

<span data-ttu-id="2230f-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="2230f-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="2230f-108">En retour, contient une instance incorporée de la classe **MSFT_DSCMetaConfiguration** qui définit les paramètres.</span><span class="sxs-lookup"><span data-stu-id="2230f-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="2230f-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="2230f-109">Return value</span></span>
------------

<span data-ttu-id="2230f-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2230f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2230f-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="2230f-111">Remarks</span></span>

<span data-ttu-id="2230f-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="2230f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2230f-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2230f-113">Requirements</span></span>
------------
><span data-ttu-id="2230f-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2230f-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2230f-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2230f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2230f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2230f-116">See also</span></span>


[<span data-ttu-id="2230f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2230f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



