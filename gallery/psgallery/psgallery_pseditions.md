---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_pseditions
ms.openlocfilehash: 6634da5c2dadee9c0c6470b3d3e8883e6d02160f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="items-with-compatible-powershell-editions" class="xliff"></a>
# Éléments avec des éditions PowerShell compatibles
À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.

- **Desktop Edition :** basée sur le .NET Framework, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions complètes de Windows telles que Server Core et Windows Desktop.
- **Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.

<a id="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions" class="xliff"></a>
## PowerShell Gallery extrait des métadonnées d’éditions PS prises en charge et vous permet de filtrer les éléments compatibles pour des éditions PowerShell spécifiques

Si des éditions PS compatibles sont spécifiées pour un élément, elles sont répertoriées dans le cadre des « Éditions PowerShell » dans la page d’affichage de l’élément et également dans les résultats des éléments.
![Page d’affichage de l’élément avec des éditions PS](Images/ItemDisplayPageWithPSEditions.PNG)

<a id="search-for-items-in-the-gallery-ui-which-works-on-powershellcore" class="xliff"></a>
## Rechercher des éléments dans l’interface utilisateur PowerShell Gallery qui fonctionnent sur PowerShellCore
Utiliser Tags:"PSEdition_Desktop" et Tags:"PSEdition_Core" pour filtrer les éléments sur PowerShell Gallery.

<a id="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition" class="xliff"></a>
### Utiliser Tags:"PSEdition_Core" pour rechercher les éléments compatibles avec l’édition PowerShell Core.
![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Core](Images/SearchResultsWithPSEditions.PNG)

<a id="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition" class="xliff"></a>
### Utiliser Tags:"PSEdition_Desktop" pour rechercher les éléments compatibles avec l’édition PowerShell Desktop.
![Résultats de la recherche des éléments compatibles avec l’édition PowerShell Desktop](Images/SearchResultsWithPSEdition_Desktop.PNG)

<a id="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions" class="xliff"></a>
## Plus d’informations sur la création et la recherche des éléments avec des éditions PowerShell compatibles
<a id="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd" class="xliff"></a>
### [Modules avec des éditions PS](../psget/module/modulewithpseditionsupport.md)
<a id="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd" class="xliff"></a>
### [Scripts avec des éditions PS](../psget/script/scriptwithpseditionsupport.md)

