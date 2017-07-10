---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_unlist_items
ms.openlocfilehash: 8fa09c77e144f14bf0fd3493dff7650897100715
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="unlisting-items" class="xliff"></a>
# Retrait d’éléments de la liste

**Pourquoi la suppression d’un élément de PowerShell Gallery n’est-elle pas proposée en option ?**

PowerShell Gallery ne gère pas la suppression définitive d’éléments par des utilisateurs. Cela permet à d’autres utilisateurs de s’attribuer des dépendances sur vos éléments sans se soucier d’arrêts possibles. Par exemple, si le module Pester dépend du module Azure et que le module Azure est supprimé de la galerie, l’utilisateur ne peut plus utiliser le module Pester.

Toutefois, au lieu de supprimer un élément, vous pouvez le retirer de la liste.

**À quoi sert le retrait d’un élément dans PowerShell Gallery ?**

Le retrait de la liste d’un élément comme un module ou un script dans PowerShell Gallery permet de supprimer cet élément de l’onglet Éléments.
De plus, les éléments retirés de la liste ne sont pas détectables à l’aide de la barre de recherche.
La seule façon de télécharger un élément non listé consiste à spécifier le nom et la version exacts de l’élément.
De ce fait, le retrait d’un élément de la liste n’interrompt pas les autres modules ou scripts qui en dépendent.

Pour retirer votre élément de la liste, visitez la page des détails de l’élément, puis sélectionnez « Supprimer l’élément ». Décochez la case « Répertorié », puis cliquez sur Enregistrer.

**Comment supprimer un élément ?**

Si vous êtes confronté à un scénario nécessitant la suppression d’un élément, contactez les administrateurs PowerShell Gallery.
Les scénarios de suppression valides sont les suivants :
- Problèmes de violation des droits d’auteur.
- Élément contenant un contenu potentiellement dangereux.
- Élément contenant des données sensibles.

Pour soumettre une demande de suppression d’élément aux administrateurs PowerShell Gallery, visitez la page des détails de votre élément, puis sélectionnez Contacter le support technique.  


