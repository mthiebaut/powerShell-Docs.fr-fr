---
title: Configuration requise pour Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
---
# Configuration requise pour Windows PowerShell
Cette rubrique répertorie la configuration requise pour [!INCLUDE[psversion3](../Token/psversion3_md.md)] et [!INCLUDE[psversion4](../Token/psversion4_md.md)], et pour des fonctionnalités spéciales, telles que [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)], des commandes CIM et des flux de travail.

[!INCLUDE[winblue_client_1](../Token/winblue_client_1_md.md)] et [!INCLUDE[winblue_server_1](../Token/winblue_server_1_md.md)] incluent tous les programmes requis. Cette rubrique est conçue pour les utilisateurs de versions antérieures de Windows.

## Systèmes d'exploitation requis
[!INCLUDE[psversion4](../Token/psversion4_md.md)] s’exécute sur les versions suivantes de Windows.

-   [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], installé par défaut

-   [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], installé par défaut

-   [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)] avec Service Pack 1, installer [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) pour exécuter [!INCLUDE[psversion4](../Token/psversion4_md.md)]

-   [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] avec Service Pack 1, installer [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) pour exécuter [!INCLUDE[psversion4](../Token/psversion4_md.md)]

[!INCLUDE[psversion3](../Token/psversion3_md.md)] s’exécute sur les versions suivantes de Windows.

-   [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], installé par défaut

-   [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], installé par défaut

-   [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)] avec Service Pack 1, installer [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) pour exécuter [!INCLUDE[psversion3](../Token/psversion3_md.md)]

-   [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] avec Service Pack 1, installer [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) pour exécuter [!INCLUDE[psversion3](../Token/psversion3_md.md)]

-   [!INCLUDE[lserver](../Token/lserver_md.md)] avec Service Pack 2, installer [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) pour exécuter [!INCLUDE[psversion3](../Token/psversion3_md.md)]

## Configuration requise pour Microsoft .NET Framework
[!INCLUDE[psversion4](../Token/psversion4_md.md)] requiert l’installation complète de Microsoft .NET Framework 4.5. [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] et [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] incluent Microsoft .NET Framework 4.5 par défaut.

[!INCLUDE[psversion3](../Token/psversion3_md.md)] requiert l’installation complète de Microsoft .NET Framework 4. [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] et [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] incluent Microsoft .NET Framework 4.5 par défaut, ce qui répond à cette exigence.

Pour installer Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), voir [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) sur le Centre de téléchargement Microsoft.

Pour effectuer l’installation complète de Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), voir [Microsoft .NET Framework 4 (programme d’installation web)](http://go.microsoft.com/fwlink/?LinkID=212931) sur le Centre de téléchargement Microsoft.

## WS-Management 3.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] et [!INCLUDE[psversion4](../Token/psversion4_md.md)] requièrent WS-Management 3.0, qui prend en charge le service WinRM et le protocole WSMan. Ce programme est inclus dans [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], Windows Management Framework 4.0 et [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)].

## WMI (Windows Management Instrumentation) 3.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] et [!INCLUDE[psversion4](../Token/psversion4_md.md)] requièrent WMI (Windows Management Instrumentation) 3.0. Ce programme est inclus dans [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], Windows Management Framework 4.0 et [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]. Si ce programme n’est pas installé sur l’ordinateur, les fonctionnalités qui requièrent WMI, telles que les commandes CIM, ne fonctionnent pas.

## Common Language Runtime (CLR) 4.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] et [!INCLUDE[psversion4](../Token/psversion4_md.md)] sont compilés avec Common Language Runtime (CLR) 4.0.

## Configuration requise de l’interface graphique utilisateur
[!INCLUDE[wps_2](../Token/wps_2_md.md)] est une application console qui ne requiert pas d’interface graphique utilisateur. Par conséquent, elle convient particulièrement pour des ordinateurs qui n’ont pas d’écran, de moniteur ou d’interface utilisateur, telles que les options d’installation Server Core de [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] ou [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)].

Toutefois, certains éléments, tels les suivants, requièrent une interface graphique utilisateur. Pour plus d’informations, consultez la rubrique d’aide de chaque élément.

-   [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]

-   Applets de commande

    1.  [Out-GridView](assetId:///70915a86-d753-464e-8349-cba02316154c)

    2.  [Show-Command](assetId:///65bba50b-91a8-49d5-80a2-a30fc684ba41)

    3.  [Show-ControlPanelItem](assetId:///0685d42c-37cc-498f-acf6-0ecfeb0cb162)

    4.  [Show-EventLog](assetId:///a3b0f5ad-0438-42c7-915b-d1b4793a431c)

-   Paramètres

    1.  Paramètre **ShowWindow** de l’applet de commande [Get-Help](assetId:///1f46eeb4-49d7-4bec-bb29-395d9b42f54a).

    2.  Paramètre **ShowSecurityDescriptorUi** des applets de commande [Register-PSSessionConfiguration](assetId:///e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) et [Set-PSSessionConfiguration](assetId:///b21fbad3-1759-4260-b206-dcb8431cd6ea).

## Configuration requise pour le moteur Windows PowerShell
[!INCLUDE[psversion4](../Token/psversion4_md.md)] est conçu pour offrir une compatibilité descendante avec [!INCLUDE[psversion3](../Token/psversion3_md.md)] et [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Les applets de commande, fournisseurs, composants logiciels enfichables, modules et scripts écrits pour [!INCLUDE[psversion2](../Token/psversion2_md.md)] et [!INCLUDE[psversion3](../Token/psversion3_md.md)] s’exécutent sans modification dans [!INCLUDE[psversion4](../Token/psversion4_md.md)].

Toutefois, en raison d’une modification de la stratégie d’activation du runtime de Microsoft .NET Framework 4, les programmes hôtes de [!INCLUDE[wps_2](../Token/wps_2_md.md)] écrits pour [!INCLUDE[psversion2](../Token/psversion2_md.md)] et compilés avec Common Language Runtime (CLR) 2.0 ne peuvent pas s’exécuter sans modification dans [!INCLUDE[psversion3](../Token/psversion3_md.md)] qui est compilé avec CLR 4.0.

Le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] nécessite au minimum Microsoft .NET Framework 2.0.50727. Cette condition est remplie par Microsoft .NET Framework 3.5 Service Pack 1. Cette condition n’est pas remplie par Microsoft .NET Framework 4 et versions ultérieures de Microsoft .NET Framework.

Pour plus d’informations sur l’ajout ou l’installation du moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)], et l’ajout ou l’installation des versions requises de Microsoft .NET Framework, voir [Installation du moteur Windows PowerShell 2.0](../Topic/Installing-the-Windows-PowerShell-2.0-Engine.md). Pour plus d’informations sur le démarrage du moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)], voir [Démarrage du moteur Windows PowerShell 2.0](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md).

## Environnement de préinstallation Windows
[!INCLUDE[psversion2](../Token/psversion2_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)]et [!INCLUDE[psversion4](../Token/psversion4_md.md)] s’exécutent dans l’environnement de préinstallation Windows (Windows PE). Toutefois, les applets de commande suivantes ne sont pas pris en charge.

-   [Applets de commande du service de transfert intelligent en arrière-plan (BITS)](http://go.microsoft.com/fwlink/?LinkId=257514)

-   [Get-EventLog](assetId:///b4985b11-82bf-487d-928d-becd96fc0419)

-   [Get-WinEvent[PSITPro5_Diagnostic]](assetId:///5fe94870-ed6b-4ce2-9500-93846cc65c95)

-   [Save-Help](assetId:///aed94f90-b73f-4e25-a25d-7c18d9f161fa)

-   [Update-Help](assetId:///93e1d870-ace6-432b-8778-8920291d7545)

En outre, le service **WinRm** n’est pas présent sur Windows PE.

## Voir aussi
[Prise en main de Windows PowerShell](../Topic/Getting-Started-with-Windows-PowerShell.md)
[Installation de Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[Démarrage de Windows PowerShell [ps]](assetId:///8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO1-->


