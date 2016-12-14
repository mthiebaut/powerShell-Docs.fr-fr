---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,gallery
ms.date: 2016-10-14
contributor: manikb
title: psgallery_items_tab
ms.technology: powershell
ms.openlocfilehash: 32f28df7318472f34f79c61f19f33016cf73f517
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
<a name="items-tab"></a>Onglet Éléments
==========

L’onglet Éléments affiche tous les éléments disponibles dans PowerShell Gallery.

Pour afficher uniquement les modules dans PowerShell Gallery, cliquez sur Modules dans la liste déroulante de l’onglet Éléments.  De même, pour afficher uniquement les scripts dans PowerShell Gallery, cliquez sur Scripts dans la liste déroulante de l’onglet Éléments.  

Pour plus d’informations sur un élément particulier, cliquez sur l’élément.

Il existe plusieurs manières de trier les éléments :

##<a name="filter-by"></a>Filtrer par##
La section Filtrer par permet aux utilisateurs de filtrer les résultats selon :
* Type d’élément :
    * Modules
    * Scripts
* Catégorie :
    * Applet de commande
    * Ressource DSC
    * Fonction
    * Workflow

Remarque : Les filtres sont inclusifs.  
Exemple : Un élément qui contient à la fois des applets de commande et des fonctions s’affiche si l’applet de commande ou la fonction (ou les deux) sont cochées.  Si aucune n’est sélectionnée, l’élément n’apparaît pas.  
De même, si toutes les catégories sont sélectionnées, seuls les éléments contenant l’une de ces catégories s’affichent. **Les éléments qui n’appartiennent à aucune de ces catégories n’apparaissent pas.**

##<a name="sort-by"></a>Trier par## 
La liste déroulante Trier par permet aux utilisateurs de trier les résultats selon les critères :
* Popularité : la popularité est déterminée par le nombre de téléchargements.
* A à Z : noms des éléments par ordre alphabétique.
* Récent : les éléments apparaissent en fonction de leur date de publication.


##<a name="search-box"></a>Zone de recherche##
La zone de recherche permet aux utilisateurs de rechercher les éléments selon les mots clés.  
Pour plus d’informations, voir [Syntaxe de recherche](./psgallery_search_syntax.md).

