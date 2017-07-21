---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_scriptanalyzer_rule_profile
ms.openlocfilehash: b178f198c9643fb39a6499d7e957cfd0d848c52d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a><span data-ttu-id="a11cd-103">Profil de règle ScriptAnalyzer pour la galerie</span><span class="sxs-lookup"><span data-stu-id="a11cd-103">ScriptAnazlyer Rule Profile for Gallery</span></span>
<span data-ttu-id="a11cd-104">Pour garantir la qualité des éléments publiés dans PowerShell Gallery, nous exécutons des règles [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) pour déterminer s’il existe des violations dans les scripts soumis.</span><span class="sxs-lookup"><span data-stu-id="a11cd-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="a11cd-105">Vous pouvez trouver la liste des règles que nous appliquons sur la [page GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1) de ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="a11cd-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="a11cd-106">Si vous avez des interrogations sur les règles que nous appliquons, contactez les administrateurs de PowerShell Gallery ou signalez un problème pour ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="a11cd-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="a11cd-107">Dans la version à venir, les résultats de ScriptAnalyzer seront affichés sur chaque page de chaque élément dans la galerie.</span><span class="sxs-lookup"><span data-stu-id="a11cd-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="a11cd-108">Nous encourageons les propriétaires d’éléments à vérifier leurs éléments pour s’assurer qu’il n’existe pas d’erreurs graves dans les éléments publiés.</span><span class="sxs-lookup"><span data-stu-id="a11cd-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>

