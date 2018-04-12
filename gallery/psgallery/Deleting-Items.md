---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,applet de commande,psgallery
title: Suppression d’éléments
ms.openlocfilehash: f82d80a35f51227c4671bd2b15a7d1c16f0ba0a8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="deleting-items"></a>Suppression d’éléments

PowerShell Gallery ne prend pas en charge la suppression définitive d’éléments, car cela empêcherait toute personne qui en dépend de rester disponible.

Au lieu de cela, PowerShell Gallery prend en charge un moyen de retirer de la liste un élément. Cette opération peut être effectuée dans la page de gestion des éléments sur le site web.
Quand un élément est retiré de la liste, il ne s’affiche plus dans la recherche et dans les listes d’éléments, aussi bien dans PowerShell Gallery et lors de l’utilisation de commandes PowerShellGet.
Toutefois, il reste téléchargeable en spécifiant sa version exacte, ce qui permet aux scripts automatisés de continuer à fonctionner.

Si vous rencontrez une situation exceptionnelle où si vous pensez que l’un de vos éléments doit être supprimé, l’équipe PowerShell Gallery peut s’en charger manuellement.
Par exemple, la violation des droits d’auteur ou un contenu potentiellement dangereux peuvent constituer une raison valable de le supprimer.
Dans ce cas, vous devez soumettre une demande de support via [PowerShell Gallery] (http://www.PowerShellGallery.com)).