---
title: Démarrage de Windows PowerShell sur des versions antérieures de Windows
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
---
# Démarrage de Windows PowerShell sur des versions antérieures de Windows
Cette section explique comment démarrer Windows PowerShell et Windows PowerShell Integrated Scripting Environment (ISE) sur WindowsÂ® 7, Windows ServerÂ® 2008 R2 et Windows Server 2008. Elle explique également comment activer la fonctionnalité facultative pour Windows PowerShell ISE dans Windows PowerShell 2.0 sur Windows ServerÂ® 2008 R2 et Windows Server 2008.

Pour installer Windows PowerShell 4.0 sur des systèmes pris en charge, téléchargez et installez [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Pour plus d’informations, consultez [Installation de Windows Server](Installing-Windows-PowerShell.md)..

Pour installer Windows PowerShell 3.0 sur des systèmes pris en charge, téléchargez et installez [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Pour plus d’informations, consultez [Installation de Windows Server](Installing-Windows-PowerShell.md)..

## Comment démarrer Windows PowerShell sur des versions antérieures de Windows
Pour démarrer la version installée de Windows PowerShell 3.0 ou Windows PowerShell 4.0, le cas échéant, utilisez une des méthodes suivantes.

#### À partir du menu Démarrer

-   Cliquez sur **Démarrer**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell**..

-   À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell**..

#### À l’invite de commandes

-   Dans Cmd.exe, Windows PowerShell ou Windows PowerShell ISE, pour démarrer Windows PowerShell, tapez :

    ```
    PowerShell
    ```

    Vous pouvez également utiliser les paramètres du programme PowerShell.exe pour personnaliser la session. Pour plus d’informations, consultez [Aide sur la ligne de commande PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md)..

#### Avec des privilèges d’administration (« Exécuter en tant qu’administrateur »)

1.  Cliquez sur **Démarrer**, tapez **PowerShell**, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**..

## Comment démarrer Windows PowerShell ISE sur des versions antérieures de Windows
Utilisez une des méthodes suivantes pour démarrer Windows PowerShell ISE.

#### À partir du menu Démarrer

-   Cliquez sur **Démarrer**, tapez **ISE**, puis cliquez sur **Windows PowerShell ISE**..

-   À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell ISE**..

#### À l’invite de commandes

-   Dans Cmd.exe, Windows PowerShell ou Windows PowerShell ISE, pour démarrer Windows PowerShell, tapez :

    ```
    PowerShell_ISE
    ```

    ou

    ```
    ISE
    ```

#### Avec des privilèges d’administration (« Exécuter en tant qu’administrateur »)

1.  Cliquez sur **Démarrer**, tapez **ISE**, cliquez avec le bouton droit sur **Windows PowerShell ISE**, puis cliquez sur **Exécuter en tant qu’administrateur**..

## Comment activer Windows PowerShell ISE sur des versions antérieures de Windows
Dans Windows PowerShell 4.0 et Windows PowerShell 3.0, Windows PowerShell ISE est activé par défaut sur toutes les versions de Windows. S’il n’est pas activé, Windows Management Framework 4.0 ou Windows Management Framework 3.0 l’active.

Dans Windows PowerShell 2.0, Windows PowerShell ISE est activé par défaut sur Windows PowerShell 7. Toutefois, sur Windows Server 2008 R2 et Windows Server 2008, c’est une fonctionnalité facultative.

Pour activer Windows PowerShell ISE dans Windows PowerShell 2.0 sur Windows Server 2008 R2 ou Windows Server 2008, utilisez la procédure suivante.

#### Pour activer Windows PowerShell Integrated Scripting Environment (ISE)

1.  Démarrez le Gestionnaire de serveur.

2.  Cliquez sur **Fonctionnalités**, puis sur **Ajouter des fonctionnalités**..

3.  Dans Sélectionner des fonctionnalités, cliquez sur Windows PowerShell Integrated Scripting Environment (ISE).



<!--HONumber=May16_HO2-->


