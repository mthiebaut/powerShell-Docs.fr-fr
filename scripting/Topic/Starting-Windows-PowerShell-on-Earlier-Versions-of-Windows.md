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
Cette section explique comment démarrer [!INCLUDE[wps_2](../Token/wps_2_md.md)] et [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)] sur [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)], [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] et [!INCLUDE[lserver](../Token/lserver_md.md)]. Elle explique également comment activer la fonctionnalité facultative pour [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] dans [!INCLUDE[psversion2](../Token/psversion2_md.md)] sur [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] et [!INCLUDE[lserver](../Token/lserver_md.md)].

Pour installer [!INCLUDE[psversion4](../Token/psversion4_md.md)] sur des systèmes pris en charge, téléchargez et installez [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Pour plus d’informations, voir [Installation de Windows Server](../Topic/Installing-Windows-PowerShell.md).

Pour installer [!INCLUDE[psversion3](../Token/psversion3_md.md)] sur des systèmes pris en charge, téléchargez et installez [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Pour plus d’informations, voir [Installation de Windows Server](../Topic/Installing-Windows-PowerShell.md).

## Comment démarrer [!INCLUDE[mshshort](../Token/mshshort_md.md)] sur des versions antérieures de Windows
Pour démarrer la version installée de [!INCLUDE[psversion3](../Token/psversion3_md.md)] ou [!INCLUDE[psversion4](../Token/psversion4_md.md)], le cas échéant, utilisez une des méthodes suivantes.

#### À partir du menu Démarrer

-   Cliquez sur **Démarrer**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell**.

-   À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell**.

#### À l’invite de commandes

-   Dans Cmd.exe, [!INCLUDE[wps_2](../Token/wps_2_md.md)] ou [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE, pour démarrer [!INCLUDE[wps_2](../Token/wps_2_md.md)], tapez :

    ```
    PowerShell
    ```

    Vous pouvez également utiliser les paramètres du programme PowerShell.exe pour personnaliser la session. Pour plus d’informations, voir [Aide sur la ligne de commande PowerShell.exe](../Topic/PowerShell.exe-Command-Line-Help.md).

#### Avec des privilèges d’administration (« Exécuter en tant qu’administrateur »)

1.  Cliquez sur **Démarrer**, tapez **PowerShell**, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.

## Comment démarrer [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] sur des versions antérieures de Windows
Pour démarrer [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)], utilisez l’une des méthodes suivantes.

#### À partir du menu Démarrer

-   Cliquez sur **Démarrer**, tapez **ISE**, puis cliquez sur **Windows PowerShell ISE**.

-   À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell ISE**.

#### À l’invite de commandes

-   Dans Cmd.exe, [!INCLUDE[wps_2](../Token/wps_2_md.md)] ou [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE, pour démarrer [!INCLUDE[wps_2](../Token/wps_2_md.md)], tapez :

    ```
    PowerShell_ISE
    ```

    ou

    ```
    ISE
    ```

#### Avec des privilèges d’administration (« Exécuter en tant qu’administrateur »)

1.  Cliquez sur **Démarrer**, tapez **ISE**, cliquez avec le bouton droit sur **Windows PowerShell ISE**, puis cliquez sur **Exécuter en tant qu’administrateur**.

## Comment activer [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] sur des versions antérieures de Windows
Dans [!INCLUDE[psversion4](../Token/psversion4_md.md)] et [!INCLUDE[psversion3](../Token/psversion3_md.md)], [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] est activé par défaut sur toutes les versions de Windows. S’il n’est pas activé, Windows Management Framework 4.0 ou [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] l’active.

Dans [!INCLUDE[psversion2](../Token/psversion2_md.md)], [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] est activé par défaut sur [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)]. Toutefois, sur [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] et [!INCLUDE[lserver](../Token/lserver_md.md)], il s’agit d’une fonctionnalité facultative.

Pour activer [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] dans [!INCLUDE[psversion2](../Token/psversion2_md.md)] sur [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] ou [!INCLUDE[lserver](../Token/lserver_md.md)], procédez comme suit.

#### Pour activer [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]

1.  Démarrez le Gestionnaire de serveur.

2.  Cliquez sur **Fonctionnalités**, puis sur **Ajouter des fonctionnalités**.

3.  Dans Sélectionner des fonctionnalités, cliquez sur [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)].



<!--HONumber=Apr16_HO1-->


