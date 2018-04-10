---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,applet de commande,psgallery
title: psgallery_items_tab
ms.openlocfilehash: 5058253678a4f996b080e43820fee06b35b681f4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="items-tab"></a><span data-ttu-id="3f085-103">Onglet Éléments</span><span class="sxs-lookup"><span data-stu-id="3f085-103">Items Tab</span></span>

<span data-ttu-id="3f085-104">L’onglet [Éléments](https://www.powershellgallery.com/items) affiche tous les éléments disponibles dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="3f085-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="3f085-105">Il existe plusieurs façons de filtrer, de trier les éléments et d’effectuer une recherche dans les éléments.</span><span class="sxs-lookup"><span data-stu-id="3f085-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="3f085-106">Pour plus d’informations sur un élément particulier, cliquez sur l’élément.</span><span class="sxs-lookup"><span data-stu-id="3f085-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="3f085-107">Filtrer par</span><span class="sxs-lookup"><span data-stu-id="3f085-107">Filter By</span></span>

<span data-ttu-id="3f085-108">La liste déroulante sous « Filtrer par » permet aux utilisateurs de filtrer les résultats selon :</span><span class="sxs-lookup"><span data-stu-id="3f085-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
* <span data-ttu-id="3f085-109">Inclure la préversion</span><span class="sxs-lookup"><span data-stu-id="3f085-109">Include Prerelease</span></span>
* <span data-ttu-id="3f085-110">Stable uniquement</span><span class="sxs-lookup"><span data-stu-id="3f085-110">Stable Only</span></span>

<span data-ttu-id="3f085-111">Pour plus d’informations sur « Préversion » et « Stable », consultez [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Gestion des préversions ajoutée à PowerShellGet et à PowerShell Gallery) dans le blog de l’équipe PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f085-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="3f085-112">Les cases à cocher sous la liste déroulante permettent aux utilisateurs de filtrer les résultats par :</span><span class="sxs-lookup"><span data-stu-id="3f085-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
* <span data-ttu-id="3f085-113">Types d’éléments</span><span class="sxs-lookup"><span data-stu-id="3f085-113">Item Types</span></span>
  - <span data-ttu-id="3f085-114">Module</span><span class="sxs-lookup"><span data-stu-id="3f085-114">Module</span></span>
  - <span data-ttu-id="3f085-115">Script</span><span class="sxs-lookup"><span data-stu-id="3f085-115">Script</span></span>
* <span data-ttu-id="3f085-116">Catégories</span><span class="sxs-lookup"><span data-stu-id="3f085-116">Categories</span></span>
  - <span data-ttu-id="3f085-117">Applet de commande</span><span class="sxs-lookup"><span data-stu-id="3f085-117">Cmdlet</span></span>
  - <span data-ttu-id="3f085-118">Ressource DSC</span><span class="sxs-lookup"><span data-stu-id="3f085-118">DSC Resource</span></span>
  - <span data-ttu-id="3f085-119">Fonction</span><span class="sxs-lookup"><span data-stu-id="3f085-119">Function</span></span>
  - <span data-ttu-id="3f085-120">Fonctionnalité de rôle</span><span class="sxs-lookup"><span data-stu-id="3f085-120">Role Capability</span></span>
  - <span data-ttu-id="3f085-121">Workflow</span><span class="sxs-lookup"><span data-stu-id="3f085-121">Workflow</span></span>

<span data-ttu-id="3f085-122">Pour afficher uniquement les modules dans PowerShell Gallery, cochez Module dans Types d’éléments.</span><span class="sxs-lookup"><span data-stu-id="3f085-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="3f085-123">De même, pour afficher uniquement les scripts dans PowerShell Gallery, cochez Script dans Types d’éléments.</span><span class="sxs-lookup"><span data-stu-id="3f085-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="3f085-124">Les filtres sont inclusifs.</span><span class="sxs-lookup"><span data-stu-id="3f085-124">Filters are inclusive.</span></span>
> <span data-ttu-id="3f085-125">Exemple : un élément qui contient à la fois des cmdlets et des fonctions s’affiche si la case Cmdlet ou la case Function (ou les deux) sont cochées.</span><span class="sxs-lookup"><span data-stu-id="3f085-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="3f085-126">Si aucune n’est sélectionnée, l’élément n’apparaît pas.</span><span class="sxs-lookup"><span data-stu-id="3f085-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="3f085-127">De même, si toutes les catégories sont sélectionnées, seuls les éléments contenant l’une de ces catégories s’affichent.</span><span class="sxs-lookup"><span data-stu-id="3f085-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="3f085-128">**Les éléments qui n’appartiennent à aucune de ces catégories n’apparaissent pas.**</span><span class="sxs-lookup"><span data-stu-id="3f085-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="3f085-129">Trier par</span><span class="sxs-lookup"><span data-stu-id="3f085-129">Sort By</span></span>

<span data-ttu-id="3f085-130">La liste déroulante Trier par permet aux utilisateurs de trier les résultats par :</span><span class="sxs-lookup"><span data-stu-id="3f085-130">The Sort By drop-down allows users to sort the results by:</span></span>
* <span data-ttu-id="3f085-131">Popularité : la popularité est déterminée par le nombre de téléchargements</span><span class="sxs-lookup"><span data-stu-id="3f085-131">Popularity - Popularity is determined by Download Count</span></span>
* <span data-ttu-id="3f085-132">A à Z : noms des éléments par ordre alphabétique</span><span class="sxs-lookup"><span data-stu-id="3f085-132">A-Z - Alphabetically by item name</span></span>
* <span data-ttu-id="3f085-133">Récent : les éléments apparaissent en fonction de leur date de publication</span><span class="sxs-lookup"><span data-stu-id="3f085-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="3f085-134">Zone de recherche</span><span class="sxs-lookup"><span data-stu-id="3f085-134">Search Box</span></span>

<span data-ttu-id="3f085-135">La zone de recherche permet aux utilisateurs de rechercher les éléments selon les mots clés.</span><span class="sxs-lookup"><span data-stu-id="3f085-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="3f085-136">Pour plus d’informations, consultez [Syntaxe de recherche dans la galerie](psgallery_search_syntax.md).</span><span class="sxs-lookup"><span data-stu-id="3f085-136">For more information, see [Gallery Search Syntax](psgallery_search_syntax.md).</span></span>