---
title: Configuration requise pour Windows PowerShell
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
translationtype: Human Translation
ms.sourcegitcommit: 1ae9150b226147c039acf0738690de4da8686a71
ms.openlocfilehash: e2e129c1c90ab7561861a7d9c71fb654569d5712

---

# Configuration requise pour Windows PowerShell
Cette rubrique répertorie la configuration requise pour Windows PowerShell 3.0 et Windows PowerShell 4.0, et pour des fonctionnalités spéciales telles que l’environnement d’écriture de scripts intégré de Windows PowerShell (ISE), les commandes CIM et les workflows.

Windows® 8.1 et Windows Server® 2012 R2 incluent tous les programmes obligatoires. Cette rubrique est conçue pour les utilisateurs de versions antérieures de Windows.

## Systèmes d'exploitation requis
Windows PowerShell 4.0 s’exécute sur les versions suivantes de Windows.

-   Windows 8.1, installé par défaut

-   Windows Server 2012 R2, installé par défaut

-   Windows® 7 avec Service Pack 1, installer [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) pour exécuter Windows PowerShell 4.0

-   Windows Server® 2008 R2 avec Service Pack 1, installer [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) pour exécuter Windows PowerShell 4.0

Windows PowerShell 3.0 s’exécute sur les versions suivantes de Windows.

-   Windows 8, installé par défaut

-   Windows Server 2012, installé par défaut

-   Windows® 7 avec Service Pack 1, installer [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) pour exécuter Windows PowerShell 3.0

-   Windows Server® 2008 R2 avec Service Pack 1, installer [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) pour exécuter Windows PowerShell 3.0

-   Windows Server® 2008 avec Service Pack 2, installer [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) pour exécuter Windows PowerShell 3.0

## Configuration requise pour Microsoft .NET Framework
Windows PowerShell 4.0 nécessite l’installation complète du Microsoft .NET Framework 4.5. Windows 8.1 et Windows Server 2012 R2 incluent le Microsoft .NET Framework 4.5 par défaut.

Windows PowerShell 3.0 nécessite l’installation complète du Microsoft .NET Framework 4. Windows 8 et Windows Server 2012 incluent le Microsoft .NET Framework 4.5 par défaut, ce qui répond à cette exigence.

Pour installer Microsoft .NET Framework 4.5 (dotNetFx45Fullsetup\_Full\_setup.exe), consultez [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) dans le Centre de téléchargement Microsoft.

Pour effectuer l’installation complète de Microsoft .NET Framework 4 (dotNetFx40Fullsetup\_Full\_setup.exe), consultez [Microsoft .NET Framework 4 (programme d’installation web)](http://go.microsoft.com/fwlink/?LinkID=212931) dans le Centre de téléchargement Microsoft.

## WS\-Management 3.0
Windows PowerShell 3.0 et Windows PowerShell 4.0 nécessitent WS\-Management 3.0, qui prend en charge le service WinRM et le protocole WSMan. Ce programme est inclus dans Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 et Windows Management Framework 3.0.

## WMI (Windows Management Instrumentation) 3.0
Windows PowerShell 3.0 et Windows PowerShell 4.0 nécessitent WMI (Windows Management Instrumentation) 3.0. Ce programme est inclus dans Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 et Windows Management Framework 3.0. Si ce programme n’est pas installé sur l’ordinateur, les fonctionnalités qui requièrent WMI, telles que les commandes CIM, ne fonctionnent pas.

## Common Language Runtime (CLR) 4.0
Windows PowerShell 3.0 et Windows PowerShell 4.0 sont compilés avec le Common Language Runtime (CLR) 4.0.

## Configuration requise de l’interface graphique utilisateur
Windows PowerShell est une application console qui ne nécessite pas d’interface graphique utilisateur. Elle est donc particulièrement adaptée aux ordinateurs qui n’ont pas d’écran, de moniteur ou d’interface utilisateur, notamment avec les options d’installation minimale de Windows Server 2012 R2 ou Windows Server 2012.

Toutefois, certains éléments, tels les suivants, requièrent une interface graphique utilisateur. Pour plus d’informations, consultez la rubrique d’aide de chaque élément.

-   Environnement d'écriture de scripts intégré de Windows PowerShell

-   Applets de commande

    1.  [Out-GridView](https://technet.microsoft.com/en-us/library/70915a86-d753-464e-8349-cba02316154c)

    2.  [Show-Command](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41)

    3.  [Show-ControlPanelItem](https://technet.microsoft.com/en-us/library/0685d42c-37cc-498f-acf6-0ecfeb0cb162)

    4.  [Show-EventLog](https://technet.microsoft.com/en-us/library/a3b0f5ad-0438-42c7-915b-d1b4793a431c)

-   Paramètres

    1.  Paramètre **ShowWindow** de l’applet de commande [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a).

    2.  Paramètre **ShowSecurityDescriptorUI** des applets de commande [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) et [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea).

## Configuration requise pour le moteur Windows PowerShell
Windows PowerShell 4.0 est conçu pour offrir une compatibilité descendante avec Windows PowerShell 3.0 et Windows PowerShell 2.0. Les applets de commande, fournisseurs, composants logiciels enfichables, modules et scripts écrits pour Windows PowerShell 2.0 et Windows PowerShell 3.0 s’exécutent sans modification dans Windows PowerShell 4.0.

Toutefois, en raison d’une modification de la stratégie d’activation du runtime dans le Microsoft .NET Framework 4, les programmes hôtes de Windows PowerShell écrits pour Windows PowerShell 2.0 et compilés avec le Common Language Runtime (CLR) 2.0 ne peuvent pas s’exécuter sans modification dans Windows PowerShell 3.0, qui est compilé avec le CLR 4.0.

Le moteur Windows PowerShell 2.0 nécessite au minimum le Microsoft .NET Framework 2.0.50727. Cette condition est remplie par Microsoft .NET Framework 3.5 Service Pack 1. Cette condition n’est pas remplie par Microsoft .NET Framework 4 et versions ultérieures de Microsoft .NET Framework.

Pour plus d’informations sur l’ajout ou l’installation du moteur Windows PowerShell 2.0, et l’ajout ou l’installation des versions requises du Microsoft .NET Framework, consultez [Installation du moteur Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md). Pour plus d’informations sur le démarrage du moteur Windows PowerShell 2.0, consultez [Démarrage du moteur Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## Environnement de préinstallation Windows
Windows PowerShell 2.0, Windows PowerShell 3.0 et Windows PowerShell 4.0 s’exécutent dans l’environnement de préinstallation Windows (Windows PE). Toutefois, les applets de commande suivantes ne sont pas pris en charge.

-   [Applets de commande du service de transfert intelligent en arrière-plan (BITS)](http://go.microsoft.com/fwlink/?LinkId=257514)

-   [Get-EventLog](https://technet.microsoft.com/en-us/library/b4985b11-82bf-487d-928d-becd96fc0419)

-   [Get-WinEvent](https://technet.microsoft.com/en-us/library/5fe94870-ed6b-4ce2-9500-93846cc65c95)

-   [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa)

-   [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545)

En outre, le service **WinRM** n’est pas présent sur Windows PE.

## Voir aussi
[Prise en main de Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)

[Installation de Windows PowerShell](Installing-Windows-PowerShell.md)

[Démarrage de Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)




<!--HONumber=Jun16_HO4-->


