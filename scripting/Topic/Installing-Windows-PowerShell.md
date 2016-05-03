---
title: Installation de Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
---
# Installation de Windows PowerShell
[!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] et [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)] incluent [!INCLUDE[psversion3](../Token/psversion3_md.md)] et tous ses composants requis. Le système inclut également le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] pour offrir la compatibilité descendante avec les programmes hôtes qui ne peuvent pas utiliser [!INCLUDE[psversion3](../Token/psversion3_md.md)].

Cette rubrique explique comment installer [!INCLUDE[psversion3](../Token/psversion3_md.md)] sur des systèmes antérieurs, ainsi qu’installer et activer les fonctionnalités requises.

Cette rubrique contient les sections suivantes :

-   [Installation de Windows PowerShell sur Windows 8 et Windows Server 2012](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [Installation de Windows PowerShell sur Windows 7 et Windows Server 2008 R2](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [Installation de Windows PowerShell sur Windows Server 2008](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [Installation de Windows PowerShell sur Server Core](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [Déploiement d’Accès Web Windows PowerShell](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [Installation du moteur Windows PowerShell 2.0](../Topic/Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Installation de Windows PowerShell sur Windows 8 et Windows Server 2012
[!INCLUDE[psversion3](../Token/psversion3_md.md)] arrive installé, configuré et prêt à l’emploi. [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)] est installé et activé. Pour plus d’informations sur le démarrage de [!INCLUDE[mshshort](../Token/mshshort_md.md)], voir [Démarrage de Windows PowerShell sur Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) et [Démarrage de Windows PowerShell sur Windows Server 2012](https://technet.microsoft.com/en-us/library/4fc0110a-cc0c-42a4-bbb5-3cc89a0fc968).

## <a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Installation de Windows PowerShell sur Windows 7 et Windows Server 2008 R2
Ces instructions expliquent comment installer [!INCLUDE[psversion3](../Token/psversion3_md.md)] sur des ordinateurs exécutant [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)] avec Service Pack 1 et [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] avec Service Pack 1. Des instructions d’installation distinctes figurent ci-dessous pour les ordinateurs s’exécutant avec l’option d’installation Server Core de [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)].

#### Préparation à l’installation

-   Avant d’installer [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], désinstallez toute version antérieure de Windows Management Framework 3.0.

#### Pour installer [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  Effectuez l’installation complète de Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    Ou bien, installez Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

2.  Installez [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

Pour plus d’informations sur le démarrage de [!INCLUDE[psversion3](../Token/psversion3_md.md)], voir [Démarrage de Windows PowerShell sur des versions antérieures de Windows](../Topic/Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md).

## <a name="BKMK_InstallingOnServerCore"></a>Installation de Windows PowerShell sur Server Core
Ces instructions expliquent comment installer [!INCLUDE[psversion3](../Token/psversion3_md.md)] sur des ordinateurs exécutant l’option d’installation Server Core de [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] avec Service Pack 1.

Les premières étapes de la procédure utilisent des commandes de Gestion et maintenance des images de déploiement (DISM) pour installer Microsoft [!INCLUDE[dnprdnlong](../Token/dnprdnlong_md.md)] pour Server Core et [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Ces programmes sont des composants requis pour [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] qui est installé dans une étape ultérieure.

#### Préparation à l’installation

-   Avant d’installer [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], désinstallez toute version antérieure de Windows Management Framework 3.0.

#### Pour installer [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  Démarrez Cmd.exe.

2.  Exécutez l’une des commandes DISM suivantes. Ces commandes installent [!INCLUDE[dnprdnlong](../Token/dnprdnlong_md.md)] et [!INCLUDE[psversion2](../Token/psversion2_md.md)].

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  Effectuez l’installation complète de Microsoft [!INCLUDE[netfx40_short](../Token/netfx40_short_md.md)] pour Server Core à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).

4.  Installez [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## <a name="BKMK_InstallingOnWindowsServer2008LH"></a>Installation de Windows PowerShell sur Windows Server 2008
Ces instructions expliquent comment installer [!INCLUDE[psversion3](../Token/psversion3_md.md)] sur des ordinateurs exécutant [!INCLUDE[lserver](../Token/lserver_md.md)] avec Service Pack 2.

Sur des systèmes [!INCLUDE[lserver](../Token/lserver_md.md)], Windows Management Framework ([!INCLUDE[psversion2](../Token/psversion2_md.md)], KB 968930) est un composant requis pour [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]. La fonctionnalité « Protection étendue pour l’authentification » protège l’ordinateur contre les attaques de transfert d’authentification, et permet d’utiliser le paramètre **UseSSL** lors de la création de sessions à distance. Pour installer [!INCLUDE[psversion3](../Token/psversion3_md.md)] et le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)], procédez comme suit.

#### Préparation à l’installation

-   Avant d’installer [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], désinstallez toute version antérieure de Windows Management Framework 3.0.

#### Pour installer [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  Installez Microsoft .NET Framework 3.5 Service Pack 1 à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).

2.  Installez Windows Management Framework ([!INCLUDE[psversion2](../Token/psversion2_md.md)], KB 968930) à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).

3.  Effectuez l’installation complète de Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    Ou bien, installez Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

4.  Installez « Protection étendue pour l’authentification » (KB 968389) à partir de l’adresse [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).

5.  Installez [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## Voir aussi
[Configuration requise pour Windows PowerShell](../Topic/Windows-PowerShell-System-Requirements.md)
[Démarrage de Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO2-->


