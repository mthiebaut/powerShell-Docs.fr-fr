---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,applet de commande,psgallery
title: psgalleryint_status
ms.openlocfilehash: 4f7d300bb07fcbdb100c2fb029f8f66ab260fe7a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a>État de PowerShell Gallery
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>27/03/2017 - RÉSOLU : Impossible de voir les pages individuelles de module et de script

__Résumé de l’impact__ : Les liens directs vers les pages individuelles de module et de script sur https://www.powershellgallery.com ont été rompus. Le problème a été signalé dans toutes les régions. Aucun impact sur les applets de commande PowerShellGet. Par exemple, Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continuent à fonctionner.

__Cause première__ : Les ingénieurs ont identifié la cause. Il s’agit d’un problème d’affichage des boutons des médias sociaux (comme Facebook) sur la page.

__Résolution__ : Les ingénieurs ont résolu le problème en désactivant les informations de compte Facebook.

__Étapes suivantes__ : Nous avons ouvert un problème de suivi interne pour corriger notre utilisation de l’API Facebook.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>15/12/2016 - Impossible d’envoyer des e-mails sur le site web PowerShell Gallery

__Résumé de l’impact__ : Entre le 13/12/2016 et le 15/12/2016, les messages envoyés par le biais de Contacter les propriétaires, Gérer les propriétaires, Contacter le support technique ou Signaler un abus n’ont pas été reçus par les administrateurs de PowerShell Gallery.
__Cause racine__ : Les ingénieurs ont identifié la cause comme étant un problème d’authentification avec le serveur SMTP.
__Résolution__ : Les ingénieurs ont pu résoudre le problème d’authentification et restaurer la connexion au serveur SMTP.
__Étapes suivantes__ : Si vous avez utilisé les liens Contacter les propriétaires, Gérer les propriétaires, Contacter le support technique ou Signaler un abus pour envoyer un e-mail à cgadmin@microsoft.com pendant ce laps de temps et que nous n’avons pas répondu, veuillez réessayer. Veuillez nous excuser pour ce désagrément.


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>10/08/2016 - Résolu : Impossible d’envoyer des e-mails à cgadmin@microsoft.com
__Résumé de l’impact__ : Entre le 05/08/2016 et le 10/08/2016, les clients n’ont pas pu envoyer d’e-mails à cgadmin@microsoft.com ni utiliser la fonctionnalité Nous contacter.
__Cause racine__ : Les ingénieurs ont identifié une modification de la configuration du compte e-mail.
__Résolution__ : Les ingénieurs ont travaillé à la résolution du problème de configuration.
__Étapes suivantes__ : Si vous avez utilisé le lien Nous contacter ou envoyé un e-mail à cgadmin@microsoft.com pendant cette période et que nous n’avons pas répondu, réessayez. Nous vous remercions de votre patience.