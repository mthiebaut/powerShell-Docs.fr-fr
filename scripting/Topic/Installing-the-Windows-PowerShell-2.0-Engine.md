---
title: Installation du moteur Windows PowerShell 2.0
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
---
# Installation du moteur Windows PowerShell 2.0
Cette rubrique explique comment installer le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)].

[!INCLUDE[psversion3](../Token/psversion3_md.md)] est conçu pour offrir une compatibilité descendante avec [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Les applets de commande, fournisseurs, composants logiciels enfichables, modules et scripts écrits pour [!INCLUDE[psversion2](../Token/psversion2_md.md)] s’exécutent sans modification dans [!INCLUDE[psversion3](../Token/psversion3_md.md)] et [!INCLUDE[psversion4](../Token/psversion4_md.md)]. Toutefois, en raison d’une modification de la stratégie d’activation du runtime de Microsoft .NET Framework 4, les programmes hôtes de Windows PowerShell écrits pour [!INCLUDE[psversion2](../Token/psversion2_md.md)] et compilés avec Common Language Runtime (CLR) 2.0 ne peuvent pas s’exécuter sans modification dans les versions ultérieures de [!INCLUDE[wps_2](../Token/wps_2_md.md)], qui sont compilées avec CLR 4.0.

Pour assurer la compatibilité descendante avec les commandes et programmes hôtes qui sont affectés par ces modifications, les moteurs [!INCLUDE[psversion2](../Token/psversion2_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)]et [!INCLUDE[psversion4](../Token/psversion4_md.md)] sont conçus pour s’exécuter côte-à-côte. Par ailleurs, le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] dans [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] et [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]. Le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] est destiné à être utilisé uniquement quand un script ou un programme hôte existant ne peut pas s’exécuter parce qu’il n’est pas compatible avec [!INCLUDE[psversion3](../Token/psversion3_md.md)], [!INCLUDE[psversion4](../Token/psversion4_md.md)] ou Microsoft .NET Framework 4. Ces cas sont supposé être rares.

Le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] est une fonctionnalité facultative de [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] et [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)]. Dans les versions antérieures de Windows, lorsque vous installez [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], l’installation de [!INCLUDE[psversion3](../Token/psversion3_md.md)] remplace complètement l’installation de [!INCLUDE[psversion2](../Token/psversion2_md.md)] dans le répertoire d’installation de [!INCLUDE[wps_2](../Token/wps_2_md.md)]. Toutefois, moteur le [!INCLUDE[psversion2](../Token/psversion2_md.md)] est conservé.

Pour plus d’informations sur le démarrage du moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)], voir [Démarrage du moteur Windows PowerShell 2.0](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md).

## Sur [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] et [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]
Sur [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] et [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], la fonctionnalité du moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] est activée par défaut. Toutefois, pour l’utiliser, vous devez activer l’option pour Microsoft .NET Framework 3.5 dont il a besoin. Cette section explique également comment activer et désactiver la fonctionnalité du moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)].

#### Pour activer .NET Framework 3.5

1.  Dans l’écran **Démarrer**, tapez **Fonctionnalités Windows**.

2.  Dans la barre **Applications**, cliquez sur **Paramètres**, puis sur **Activer ou désactiver des fonctionnalités Windows**.

3.  Dans la zone **Fonctionnalités Windows**, cliquez sur **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)** pour sélectionner cette fonctionnalité.

    Lorsque vous sélectionnez **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)**, la zone indique que seule une partie de la fonctionnalité est activée. Toutefois, cela suffit pour le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)].

#### Pour activer et désactiver le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)]

1.  Dans l’écran **Démarrer**, tapez **Fonctionnalités Windows**.

2.  Dans la barre **Applications**, cliquez sur **Paramètres**, puis sur **Activer ou désactiver des fonctionnalités Windows**.

3.  Dans la zone **Fonctionnalités Windows** développez le nœud **[!INCLUDE[psversion2](../Token/psversion2_md.md)]**, puis cliquez sur la zone **Moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)]** pour l’activer ou la désactiver.

## Sur [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] et [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)]
Procédez comme suit pour ajouter le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] et les fonctionnalités Microsoft .NET Framework 3.5. Le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] nécessite au minimum Microsoft .NET Framework 2.0.50727. Cette condition est remplie par Microsoft .NET Framework 3.5.

#### Pour ajouter la fonctionnalité .NET Framework 3.5

1.  Dans le **Gestionnaire de serveur**, dans le menu **Gérer**, cliquez sur **Ajouter des rôles et fonctionnalités**.

    Ou bien, dans le **Gestionnaire de serveur**, cliquez sur **Tous les serveurs**, cliquez avec le bouton droit sur un nom de serveur, puis sélectionnez **Ajouter des rôles et fonctionnalités**.

2.  Dans la page **Type d’installation**, sélectionnez **Installation basée sur un rôle ou une fonctionnalité**.

3.  Dans la page **Fonctionnalités**, développez le nœud **Fonctionnalités .NET Framework 3.5**, puis sélectionnez **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)**.

    Les autres options sous ce nœud ne sont pas requises pour le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)].

#### Pour ajouter la fonctionnalité du moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)]

-   Dans le **Gestionnaire de serveur**, dans le menu **Gérer**, cliquez sur **Ajouter des rôles et fonctionnalités**.

    Ou bien, dans **Gestionnaire de serveur**, cliquez sur **Tous les serveurs**, cliquez avec le bouton droit sur un nom de serveur, puis sélectionnez **Ajouter des rôles et fonctionnalités**.

-   Dans la page **Type d’installation**, sélectionnez **Installation basée sur un rôle ou une fonctionnalité**.

-   Dans la page **Fonctionnalités**, développez le nœud **[!INCLUDE[mshshort](../Token/mshshort_md.md)] (installé)**, puis sélectionnez **Moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)]**.

Pour plus d’informations sur le démarrage du moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)], voir [Démarrage du moteur Windows PowerShell 2.0](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md).

## Sur les systèmes antérieurs
Le package [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) qui installe [!INCLUDE[psversion4](../Token/psversion4_md.md)] sur [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)], [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] et [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] inclut le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] est activé et prêt à l’usage, si nécessaire, sans autre installation, paramétrage ou configuration.

Le package [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] qui installe [!INCLUDE[psversion3](../Token/psversion3_md.md)] sur [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)], [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] et [!INCLUDE[lserver](../Token/lserver_md.md)] inclut le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] est activé et prêt à l’usage, si nécessaire, sans autre installation, paramétrage ou configuration.

## Voir aussi
[Configuration requise pour Windows PowerShell](../Topic/Windows-PowerShell-System-Requirements.md)
[Installation de Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[Démarrage de Windows PowerShell [ps]](assetId:///8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
[Démarrage du moteur Windows PowerShell 2.0](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)



<!--HONumber=Apr16_HO1-->


