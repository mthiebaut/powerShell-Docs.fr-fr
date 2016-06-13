---
title:  Installation de Windows PowerShell
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
---

# Installation de Windows PowerShell
WindowsÂ® 8 et Windows ServerÂ® 2012 incluent Windows PowerShell 3.0 et tous ses composants requis. Le système inclut également le moteur Windows PowerShell 2.0 pour offrir la compatibilité descendante avec les programmes hôtes qui ne peuvent pas utiliser Windows PowerShell 3.0.

Cette rubrique explique comment installer Windows PowerShell 3.0 sur des systèmes antérieurs, puis comment installer et activer les fonctionnalités requises.

Cette rubrique contient les sections suivantes :

-   [Installation de Windows PowerShell sur Windows 8 et Windows Server 2012](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [Installation de Windows PowerShell sur Windows 7 et Windows Server 2008 R2](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [Installation de Windows PowerShell sur Windows Server 2008](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [Installation de Windows PowerShell sur Server Core](Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [Déploiement d’Accès Web Windows PowerShell](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [Installation du moteur Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Installation de Windows PowerShell sur Windows 8 et Windows Server 2012
Windows PowerShell 3.0 arrive installé, configuré et prêt à l’emploi. Windows PowerShell Integrated Scripting Environment (ISE) est installé et activé. Pour plus d’informations sur le démarrage de Windows PowerShell, consultez [Démarrage de Windows PowerShell sur Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) et [Démarrage de Windows PowerShell sur Windows Server 2012](https://technet.microsoft.com/en-us/library/4fc0110a-cc0c-42a4-bbb5-3cc89a0fc968).

## <a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Installation de Windows PowerShell sur Windows 7 et Windows Server 2008 R2
Ces instructions expliquent comment installer Windows PowerShell 3.0 sur des ordinateurs exécutant Windows 7 avec Service Pack 1 et Windows Server 2008 R2 avec Service Pack 1. Des instructions d’installation distinctes figurent ci-dessous pour les ordinateurs s’exécutant avec l’option d’installation Server Core de Windows Server 2008 R2.

#### Préparation à l’installation

-   Avant d’installer Windows Management Framework 3.0, désinstallez toute version antérieure de ce produit.

#### Pour installer Windows PowerShell 3.0

1.  Effectuez l’installation complète de Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    Ou bien, installez Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

2.  Installez Windows Management Framework 3.0 à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

Pour plus d’informations sur le démarrage de Windows PowerShell 3.0, consultez [Démarrage de Windows PowerShell sur des versions antérieures de Windows](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md).

## <a name="BKMK_InstallingOnServerCore"></a>Installation de Windows PowerShell sur Server Core
Ces instructions expliquent comment installer Windows PowerShell 3.0 sur des ordinateurs exécutant l’option d’installation Server Core de Windows Server 2008 R2 avec Service Pack 1.

Les premières étapes de la procédure utilisent des commandes de Gestion et maintenance des images de déploiement (DISM) pour installer Microsoft .NET Framework 2.0 pour Server Core et Windows PowerShell 2.0. Ces programmes sont des composants requis pour Windows Management Framework 3.0, qui est installé à une étape ultérieure.

#### Préparation à l’installation

-   Avant d’installer Windows Management Framework 3.0, désinstallez toute version antérieure de ce produit.

#### Pour installer Windows PowerShell 3.0

1.  Démarrez Cmd.exe.

2.  Exécutez l’une des commandes DISM suivantes. Ces commandes installent .NET Framework 2.0 et Windows PowerShell 2.0.

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  Effectuez l’installation complète de Microsoft .NET Framework 4.0 pour Server Core à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).

4.  Installez Windows Management Framework 3.0 à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## <a name="BKMK_InstallingOnWindowsServer2008LH"></a>Installation de Windows PowerShell sur Windows Server 2008
Ces instructions expliquent comment installer Windows PowerShell 3.0 sur des ordinateurs exécutant Windows Server 2008 avec Service Pack 2.

Sur les systèmes Windows Server 2008, Windows Management Framework (Windows PowerShell 2.0, article 968930 de la Base de connaissances) est un composant requis pour Windows Management Framework 3.0. La fonctionnalité « Protection étendue pour l’authentification » protège l’ordinateur contre les attaques de transfert d’authentification, et permet d’utiliser le paramètre **UseSSL** lors de la création de sessions à distance. Pour installer Windows PowerShell 3.0 et le moteur Windows PowerShell 2.0, utilisez la procédure suivante.

#### Préparation à l’installation

-   Avant d’installer Windows Management Framework 3.0, désinstallez toute version antérieure de ce produit.

#### Pour installer Windows PowerShell 3.0

1.  Installez Microsoft .NET Framework 3.5 Service Pack 1 à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).

2.  Installez Windows Management Framework (Windows PowerShell 2.0, article 968930 de la Base de connaissances) à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).

3.  Effectuez l’installation complète de Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).

    Ou bien, installez Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).

4.  Installez « Protection étendue pour l’authentification » (KB 968389) à partir de l’adresse [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).

5.  Installez Windows Management Framework 3.0 à partir du Centre de téléchargement Microsoft à l’adresse [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## Voir aussi
[Configuration système requise pour Windows PowerShell](Windows-PowerShell-System-Requirements.md)
[Démarrage de Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=May16_HO2-->


