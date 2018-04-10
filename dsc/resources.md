---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressources DSC
ms.openlocfilehash: e393c8fe2e1ba8d68ba9aa1b656d1e5ebfad30e8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="da5c2-103">Ressources DSC</span><span class="sxs-lookup"><span data-stu-id="da5c2-103">DSC Resources</span></span>

><span data-ttu-id="da5c2-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="da5c2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="da5c2-105">Les ressources de configuration de l’état souhaité (DSC) fournissent les éléments de base d’une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="da5c2-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="da5c2-106">Une ressource expose les propriétés qui peuvent être configurées (schéma) et contient les fonctions de script PowerShell que le gestionnaire de configuration local appelle pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="da5c2-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="da5c2-107">Une ressource peut modéliser un élément générique comme un fichier ou spécifique comme un paramètre de serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="da5c2-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="da5c2-108">Les groupes de ce type de ressources sont combinés dans un module DSC qui organise tous les fichiers nécessaires dans une structure portable incluant les métadonnées permettant d’identifier la façon dont sont utilisées les ressources.</span><span class="sxs-lookup"><span data-stu-id="da5c2-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="da5c2-109">Les rubriques suivantes décrivent les ressources DSC :</span><span class="sxs-lookup"><span data-stu-id="da5c2-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="da5c2-110">Ressources DSC intégrées</span><span class="sxs-lookup"><span data-stu-id="da5c2-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="da5c2-111">Créer des ressources DSC personnalisées</span><span class="sxs-lookup"><span data-stu-id="da5c2-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="da5c2-112">Ressources DSC intégrées pour Linux</span><span class="sxs-lookup"><span data-stu-id="da5c2-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)