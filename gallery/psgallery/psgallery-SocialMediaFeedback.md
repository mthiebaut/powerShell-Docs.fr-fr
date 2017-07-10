---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: "Envoi de commentaires via des médias sociaux ou des commentaires"
ms.openlocfilehash: 775745e1c249014877073160eb3abd800574d54f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="providing-feedback-via-social-media-or-comments" class="xliff"></a>
# Envoi de commentaires via des médias sociaux ou des commentaires

Powershell Gallery prend en charge les deux approches pour les utilisateurs qui souhaitent fournir des commentaires publics sur un élément :

* Utiliser les liens sur le côté gauche pour « partager » un élément sur les réseaux sociaux Facebook, LinkedIn et Twitter ;
* utiliser la fonctionnalité Commenter pour publier des commentaires sur un élément et permettre aux auteurs de suivre les commentaires sur les éléments qu’ils publient.

<a id="social-media-feedback" class="xliff"></a>
## Commentaires sur les réseaux sociaux
Sur le côté gauche de la page pour chaque élément dans PowerShell Gallery, vous trouverez des liens pour Facebook, LinkedIn et Twitter.   
En cliquant sur ces liens, vous ouvrez le réseau social et pouvez rapidement partager un lien vers l’élément.

Les utilisateurs doivent se connecter au site qu'ils ont choisi afin de partager l’élément PowerShell Gallery.     

Les utilisateurs sont invités à procéder ainsi s’ils souhaitent recommander un élément à d’autres personnes. PowerShell Gallery vérifie chaque réseau social à la recherche de « partages » de l’élément et un affiche le nombre de fois que l’élément a été partagé sur chacun des réseaux sociaux.  
Étant donné que cela n'indique que le nombre de fois où un élément a été partagé, cela sera interprété comme si d’autres utilisateurs cliquaient sur « J’aime » pour l’élément.


<a id="comments" class="xliff"></a>
## Commentaires
PowerShell Gallery utilise le service LiveFyre pour permettre aux utilisateurs de commenter sur les éléments.
Les utilisateurs qui ont des recommandations ou des commentaires peuvent utiliser cette fonctionnalité pour fournir des commentaires qui sont visibles par toute personne qui consulte la page de l’élément.
Les propriétaires d’élément peuvent suivre ces commentaires et être avertis lorsqu’un utilisateur publie un commentaire. 

Le système de commentaires est basé sur LiveFyre, un service distinct qui n’est pas géré par Microsoft et nécessite une authentification séparée.  
La première fois que vous souhaitez laisser un commentaire ou suivez des commentaires sur l’un de vos éléments, vous devrez créer un compte LiveFyre.

Si vous avez créé un compte LiveFyre et vous êtes connecté, vous pouvez préparer un commentaire avec des retours sur l’élément. Cliquez alors sur « Publier le commentaire... » Le commentaire ne sera pas être visible immédiatement. Les commentaires pour les éléments de PowerShell Gallery sont modérés par des administrateurs, et toutes les publications sont vérifiées par ces derniers avant d’être publiées et visibles pour d’autres personnes.
Notre objectif avec la modération des commentaires est de vous assurer qu’ils sont en conformité avec les [conditions d’utilisation](https://www.powershellgallery.com/policies/Terms) de PowerShell Gallery.  

Les propriétaires d’éléments sont encouragés à suivre les commentaires qui sont publiés sur LiveFyre. Un compte LiveFyre est requis, et il est recommandé d’utiliser l’adresse de messagerie que vous utilisez pour la publication de votre élément dans LiveFyre. Pour suivre les commentaires, connectez-vous à LiveFyre et accédez à n’importe quel élément pour lequel vous êtes répertorié comme propriétaire. Sous la zone de commentaires en bas de chaque élément, vous pouvez voir un lien « + S’abonner ». Une fois que vous cliquez dessus, LiveFyre envoie un courrier électronique à l’adresse de messagerie inscrite chaque fois que de nouveaux commentaires sont écrits pour l’élément.

