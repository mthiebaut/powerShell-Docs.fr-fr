---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Méthode GetMetaConfiguration de la classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9ea9a-103">Méthode GetMetaConfiguration de la classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9ea9a-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9ea9a-104">Obtenez les paramètres du Gestionnaire de configuration local qui permettent de contrôler l’agent de configuration.</span><span class="sxs-lookup"><span data-stu-id="9ea9a-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="9ea9a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ea9a-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="9ea9a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9ea9a-106">Parameters</span></span>
----------

<span data-ttu-id="9ea9a-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="9ea9a-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="9ea9a-108">En retour, contient une instance incorporée de la classe **MSFT_DSCMetaConfiguration** qui définit les paramètres.</span><span class="sxs-lookup"><span data-stu-id="9ea9a-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="9ea9a-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9ea9a-109">Return value</span></span>
------------

<span data-ttu-id="9ea9a-110">Retourne zéro en cas de réussite ; sinon, retourne un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="9ea9a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ea9a-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="9ea9a-111">Remarks</span></span>

<span data-ttu-id="9ea9a-112">Il s’agit d’une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="9ea9a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ea9a-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9ea9a-113">Requirements</span></span>
------------
><span data-ttu-id="9ea9a-114">**MOF :** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9ea9a-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9ea9a-115">**Espace de noms** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9ea9a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9ea9a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ea9a-116">See also</span></span>


[<span data-ttu-id="9ea9a-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9ea9a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



