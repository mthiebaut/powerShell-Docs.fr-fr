---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: psget_moduledependencypopulation
ms.openlocfilehash: c4c9f203e9c526ff532c2388acb6334515d66934
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="7fcca-103">Logique pour la préparation des dépendances de module au cours de l’opération de publication</span><span class="sxs-lookup"><span data-stu-id="7fcca-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="7fcca-104">Les modules répertoriés dans le cadre de RequiredModules sont considérés comme des dépendances.</span><span class="sxs-lookup"><span data-stu-id="7fcca-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="7fcca-105">Les modules répertoriés dans le cadre de NestedModules, dont la base de modules n’est pas sous la base de modules spécifiée, sont considérés comme des dépendances.</span><span class="sxs-lookup"><span data-stu-id="7fcca-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="7fcca-106">Les dépendances ci-dessus doivent être disponibles dans le même référentiel cible, sinon l’opération de publication entraîne une erreur.</span><span class="sxs-lookup"><span data-stu-id="7fcca-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="7fcca-107">Par exemple, si 'SnippetPx' n’est pas disponible dans le référentiel, l’erreur ci-dessous est générée.</span><span class="sxs-lookup"><span data-stu-id="7fcca-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="7fcca-108">Certaines dépendances de module peuvent être gérées en externe, auquel cas elles doivent être ajoutées à l’entrée ExternalModuleDependencies dans la section PSData du manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="7fcca-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="7fcca-109">Partie inférieure du message d’erreur ci-dessus</span><span class="sxs-lookup"><span data-stu-id="7fcca-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="7fcca-110">*Pendant l’installation du module, la liste des dépendances préparée ci-dessus est utilisée pour installer les dépendances.*</span><span class="sxs-lookup"><span data-stu-id="7fcca-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="7fcca-111">*Vérifiez que les dépendances de votre module sont disponibles sous $env:PSModulePath sur votre système lors de l’opération de publication.*</span><span class="sxs-lookup"><span data-stu-id="7fcca-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>