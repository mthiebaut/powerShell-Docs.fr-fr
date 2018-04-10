---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: a565f2befddc32f5088fa3e158f58d2dd78d41b4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="74e57-102">Prise en charge du contrôle de version de modules côte à côte pour les ressources DSC</span><span class="sxs-lookup"><span data-stu-id="74e57-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="74e57-103">Les modules contenant des ressources DSC peuvent être installés côte à côte, et les configurations DSC peuvent utiliser une version spécifique de la ressource installée sur le système.</span><span class="sxs-lookup"><span data-stu-id="74e57-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="74e57-104">Pour plus d’informations, consultez [Utilisation de ressources avec plusieurs versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="74e57-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="74e57-105">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="74e57-105">Known issues</span></span>

<span data-ttu-id="74e57-106">Voici une liste des problèmes connus avec l’installation côte à côte dans cette version :</span><span class="sxs-lookup"><span data-stu-id="74e57-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="74e57-107">L’utilisation de deux versions différentes de la ressource DSC dans la même configuration n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="74e57-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>