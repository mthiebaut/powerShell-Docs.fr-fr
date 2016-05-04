---
title: Comment créer un onglet PowerShell dans Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
---
# Comment créer un onglet PowerShell dans Windows PowerShell ISE
Les onglets dans [!INCLUDE[ise_1](../Token/ise_1_md.md)] permettent de créer et d’utiliser simultanément plusieurs environnements d’exécution au sein de la même application. Chaque onglet PowerShell correspond à un environnement d’exécution ou à une session distincts.

> [!NOTE]
> Les variables, fonctions et alias que vous créez sous un onglet ne s’appliquent pas à un autre. Il s’agit de sessions Windows PowerShell différentes.

Pour ouvrir ou fermer un onglet dans [!INCLUDE[wps_2](../Token/wps_2_md.md)], procédez comme suit. Pour renommer un onglet, définissez la propriété [DisplayName](assetId:///a9b58556-951b-4f48-b3ae-b351b7564360#Displayname) sur l’objet de script Onglet [!INCLUDE[wps_2](../Token/wps_2_md.md)].

## Pour créer et utiliser un onglet PowerShell
Dans le menu **Fichier**, cliquez sur **Nouvel onglet PowerShell**. Le nouvel onglet PowerShell s’ouvre toujours comme la fenêtre active. Les onglets PowerShell sont numérotés de façon incrémentielle dans l’ordre de leur ouverture. Chaque onglet est associé à sa propre fenêtre de console Windows PowerShell. Vous pouvez avoir jusqu’à 32 onglets PowerShell avec leur propre session ouverte simultanément (ce nombre est limité à 8 sur [!INCLUDE[ise_2](../Token/ise_2_md.md)]2.0.)

Notez qu’un clic sur l’icône **Nouveau** ou **Ouvrir** dans la barre d’outils ne crée pas d’onglet avec une session distincte.  Au lieu de cela, ces boutons ouvrent un fichier de script nouveau ou existant sur l’onglet actif avec une session. Vous pouvez avoir plusieurs fichiers script ouverts avec chaque onglet et session. Les onglets de script pour une session s’affichent sous les onglets de la session uniquement lorsque la session associée est active.

Pour activer un onglet PowerShell, cliquez dessus. Pour opérer une sélection parmi tous les onglets PowerShell ouverts, dans le menu **Affichage**, cliquez sur l’onglet PowerShell que vous souhaitez utiliser.

## Pour créer et utiliser un onglet PowerShell à distance
Dans le menu **Fichier**, cliquez sur **Nouvel onglet PowerShell à distance** pour établir une session sur un ordinateur distant. Une boîte de dialogue s’affiche et vous invite à entrer les détails requis pour établir la connexion à distance. L’onglet à distance fonctionne exactement comme un onglet PowerShell local, mais les commandes et les scripts sont exécutés sur l’ordinateur distant.

## Pour fermer un onglet PowerShell
Pour fermer un onglet, vous pouvez utiliser l’une des techniques suivantes :

-   Cliquez sur l’onglet que vous souhaitez fermer.

-   Dans le menu **Fichier**, cliquez sur **Fermer l’onglet PowerShell** ou sur le bouton Fermer (**X**) d’un onglet actif pour fermer celui-ci.

Si des fichiers non enregistrés sont ouverts dans l’onglet PowerShell que vous fermez, vous êtes invité à les enregistrer ou les ignorer. Pour plus d’informations sur l’enregistrement d’un script, voir [Comment enregistrer un script](assetId:///162f594d-efd3-4234-9960-45e56e6eadc8).

## Voir aussi
[Utilisation de Windows PowerShell ISE](../Topic/Using-the-Windows-PowerShell-ISE.md)
[Comment utiliser le volet Console dans Windows PowerShell ISE](../Topic/How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO1-->


