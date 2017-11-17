---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressources DSC
ms.openlocfilehash: 62bf352b929d661e585e145e5aab0f44f13010a1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-resources"></a><span data-ttu-id="5451c-103">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="5451c-103">DSC Resources</span></span>

><span data-ttu-id="5451c-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5451c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5451c-105">Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="5451c-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="5451c-106">Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5451c-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="5451c-107">Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="5451c-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="5451c-108">Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.</span><span class="sxs-lookup"><span data-stu-id="5451c-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>  

<span data-ttu-id="5451c-109">Les rubriques suivantes décrivent les ressources DSC :</span><span class="sxs-lookup"><span data-stu-id="5451c-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="5451c-110">Ressources DSC intégrées</span><span class="sxs-lookup"><span data-stu-id="5451c-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="5451c-111">Créer des ressources DSC personnalisées</span><span class="sxs-lookup"><span data-stu-id="5451c-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="5451c-112">Ressources DSC intégrées pour Linux</span><span class="sxs-lookup"><span data-stu-id="5451c-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)

