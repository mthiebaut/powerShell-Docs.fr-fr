---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,gallery
ms.date: 2016-10-14
contributor: manikb
title: "Suppression d’éléments"
ms.technology: powershell
ms.openlocfilehash: 0bc8261992802c75463c454dd990dccdbfb2eb12
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="deleting-items"></a>Suppression d’éléments

PowerShell Gallery ne prend pas en charge la suppression définitive d’éléments, car cela empêcherait toute personne qui en dépend de rester disponible.

Au lieu de cela, PowerShell Gallery prend en charge un moyen de retirer de la liste un élément. Cette opération peut être effectuée dans la page de gestion des éléments sur le site web. Quand un élément est retiré de la liste, il ne s’affiche plus dans la recherche et dans les listes d’éléments, aussi bien dans PowerShell Gallery et lors de l’utilisation de commandes PowerShellGet. Toutefois, il reste téléchargeable en spécifiant sa version exacte, ce qui permet aux scripts automatisés de continuer à fonctionner.

Si vous rencontrez une situation exceptionnelle où si vous pensez que l’un de vos éléments doit être supprimé, l’équipe PowerShell Gallery peut s’en charger manuellement. Par exemple, la violation des droits d’auteur ou un contenu potentiellement dangereux peuvent constituer une raison valable de le supprimer. Dans ce cas, vous devez soumettre une demande de support via [PowerShell Gallery] (http://www.PowerShellGallery.com).

