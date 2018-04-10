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
# <a name="items-tab"></a>Onglet Éléments

L’onglet [Éléments](https://www.powershellgallery.com/items) affiche tous les éléments disponibles dans PowerShell Gallery.

Il existe plusieurs façons de filtrer, de trier les éléments et d’effectuer une recherche dans les éléments.
Pour plus d’informations sur un élément particulier, cliquez sur l’élément.

## <a name="filter-by"></a>Filtrer par

La liste déroulante sous « Filtrer par » permet aux utilisateurs de filtrer les résultats selon :
* Inclure la préversion
* Stable uniquement

Pour plus d’informations sur « Préversion » et « Stable », consultez [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Gestion des préversions ajoutée à PowerShellGet et à PowerShell Gallery) dans le blog de l’équipe PowerShell.

Les cases à cocher sous la liste déroulante permettent aux utilisateurs de filtrer les résultats par :
* Types d’éléments
  - Module
  - Script
* Catégories
  - Applet de commande
  - Ressource DSC
  - Fonction
  - Fonctionnalité de rôle
  - Workflow

Pour afficher uniquement les modules dans PowerShell Gallery, cochez Module dans Types d’éléments.
De même, pour afficher uniquement les scripts dans PowerShell Gallery, cochez Script dans Types d’éléments.

> [!NOTE]
> Les filtres sont inclusifs.
> Exemple : un élément qui contient à la fois des cmdlets et des fonctions s’affiche si la case Cmdlet ou la case Function (ou les deux) sont cochées.
> Si aucune n’est sélectionnée, l’élément n’apparaît pas.
> De même, si toutes les catégories sont sélectionnées, seuls les éléments contenant l’une de ces catégories s’affichent.
> **Les éléments qui n’appartiennent à aucune de ces catégories n’apparaissent pas.**

## <a name="sort-by"></a>Trier par

La liste déroulante Trier par permet aux utilisateurs de trier les résultats par :
* Popularité : la popularité est déterminée par le nombre de téléchargements
* A à Z : noms des éléments par ordre alphabétique
* Récent : les éléments apparaissent en fonction de leur date de publication

## <a name="search-box"></a>Zone de recherche

La zone de recherche permet aux utilisateurs de rechercher les éléments selon les mots clés.
Pour plus d’informations, consultez [Syntaxe de recherche dans la galerie](psgallery_search_syntax.md).