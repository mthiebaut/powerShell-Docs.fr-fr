---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,applet de commande
title: "Démarrage de Windows PowerShell sur des versions antérieures de Windows"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: cb56fded1e67a4f4219d210dd95078314e855b1a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a>Démarrage de Windows PowerShell sur des versions antérieures de Windows
Cette section explique comment démarrer Windows PowerShell et l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell sur Windows® 7, Windows Server® 2008 R2 et Windows Server 2008. Elle explique également comment activer la fonctionnalité facultative pour Windows PowerShell ISE dans Windows PowerShell 2.0 sur Windows Server® 2008 R2 et Windows Server® 2008.

Pour installer Windows PowerShell 4.0 sur des systèmes pris en charge, téléchargez et installez [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Pour plus d’informations, voir [Installation de Windows PowerShell](Installing-Windows-PowerShell.md).

Pour installer Windows PowerShell 3.0 sur des systèmes pris en charge, téléchargez et installez [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Pour plus d’informations, voir [Installation de Windows PowerShell](Installing-Windows-PowerShell.md).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Comment démarrer Windows PowerShell sur des versions antérieures de Windows
Pour démarrer la version installée de Windows PowerShell 3.0 ou Windows PowerShell 4.0, le cas échéant, utilisez une des méthodes suivantes.

#### <a name="from-the-start-menu"></a>À partir du menu Démarrer

-   Cliquez sur **Démarrer**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell**.

-   À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>À l’invite de commandes

-   Dans Cmd.exe, Windows PowerShell ou Windows PowerShell ISE, pour démarrer Windows PowerShell, tapez :

    ```
    PowerShell
    ```

    Vous pouvez également utiliser les paramètres du programme PowerShell.exe pour personnaliser la session. Pour plus d’informations, voir [Aide sur la ligne de commande PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Avec des privilèges d’administration (« Exécuter en tant qu’administrateur »)

1.  Cliquez sur **Démarrer**, tapez **PowerShell**, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Comment démarrer Windows PowerShell ISE sur des versions antérieures de Windows
Utilisez une des méthodes suivantes pour démarrer Windows PowerShell ISE.

#### <a name="from-the-start-menu"></a>À partir du menu Démarrer

-   Cliquez sur **Démarrer**, tapez **ISE**, puis cliquez sur **Windows PowerShell ISE**.

-   À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>À l’invite de commandes

-   Dans Cmd.exe, Windows PowerShell ou Windows PowerShell ISE, pour démarrer Windows PowerShell, tapez :

    ```
    PowerShell_ISE
    ```

    ou

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Avec des privilèges d’administration (« Exécuter en tant qu’administrateur »)

1.  Cliquez sur **Démarrer**, tapez **ISE**, cliquez avec le bouton droit sur **Windows PowerShell ISE**, puis cliquez sur **Exécuter en tant qu’administrateur**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Comment activer Windows PowerShell ISE sur des versions antérieures de Windows
Dans Windows PowerShell 4.0 et Windows PowerShell 3.0, Windows PowerShell ISE est activé par défaut sur toutes les versions de Windows. S’il n’est pas activé, Windows Management Framework 4.0 ou Windows Management Framework 3.0 l’active.

Dans Windows PowerShell 2.0, Windows PowerShell ISE est activé par défaut sur Windows 7. Toutefois, sur Windows Server 2008 R2 et Windows Server 2008, c’est une fonctionnalité facultative.

Pour activer Windows PowerShell ISE dans Windows PowerShell 2.0 sur Windows Server 2008 R2 ou Windows Server 2008, utilisez la procédure suivante.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Pour activer Windows PowerShell Integrated Scripting Environment (ISE)

1.  Démarrez le Gestionnaire de serveur.

2.  Cliquez sur **Fonctionnalités**, puis sur **Ajouter des fonctionnalités**.

3.  Dans Sélectionner des fonctionnalités, cliquez sur Windows PowerShell Integrated Scripting Environment (ISE).

