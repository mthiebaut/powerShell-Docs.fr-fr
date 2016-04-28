---
title: Démarrage du moteur Windows PowerShell 2.0
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
---
# Démarrage du moteur Windows PowerShell 2.0
Cette section explique comment démarrer le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] sur [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] et [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], qui incluent le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)], et sur d’autres systèmes sur lesquels [!INCLUDE[psversion2](../Token/psversion2_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] et [!INCLUDE[psversion4](../Token/psversion4_md.md)] sont installés.

[!INCLUDE[psversion4](../Token/psversion4_md.md)] et [!INCLUDE[psversion3](../Token/psversion3_md.md)] sont conçus pour offrir une compatibilité descendante avec [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Les applets de commande, fournisseurs, composants logiciels enfichables, modules et scripts écrits pour [!INCLUDE[psversion2](../Token/psversion2_md.md)] s’exécutent sans modification dans [!INCLUDE[psversion4](../Token/psversion4_md.md)] et [!INCLUDE[psversion3](../Token/psversion3_md.md)]. Toutefois, en raison d’une modification de la stratégie d’activation du runtime de Microsoft .NET Framework 4, les programmes hôtes de [!INCLUDE[wps_2](../Token/wps_2_md.md)] écrits pour [!INCLUDE[psversion2](../Token/psversion2_md.md)] et compilés avec Common Language Runtime (CLR) 2.0 ne peuvent pas s’exécuter sans modification dans [!INCLUDE[psversion3](../Token/psversion3_md.md)] ou [!INCLUDE[psversion4](../Token/psversion4_md.md)], qui sont compilés avec CLR 4.0. Le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] est destiné à être utilisé uniquement quand un script ou un programme hôte existant ne peut pas s’exécuter parce qu’il n’est pas compatible avec [!INCLUDE[psversion4](../Token/psversion4_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] ou Microsoft .NET Framework 4. Ces cas sont supposé être rares.

De nombreux programmes qui nécessitent le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] le démarrent automatiquement. Ces instructions sont fournies pour les rares cas où vous devez démarrer le moteur manuellement.

## Installation et activation des programmes requis
Avant de démarrer le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)], activez le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] et Microsoft .NET Framework 3.5 avec Service Pack 1. Pour obtenir des instructions, voir [Installation de Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

Les systèmes sur lesquels [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) ou [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] sont installés disposent de tous les composants requis. Aucune autre configuration n’est nécessaire. Pour plus d’informations sur l’installation de [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) ou de [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], voir [Installation de Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

## Comment démarrer le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)]
Lorsque vous démarrez [!INCLUDE[mshshort](../Token/mshshort_md.md)], la version la plus récente démarre par défaut. Pour démarrer [!INCLUDE[mshshort](../Token/mshshort_md.md)] avec le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)], utilisez le paramètre Version de PowerShell.exe. Vous pouvez exécuter la commande à tout invite de commandes, y compris de Windows PowerShell et de Cmd.exe.

```
PowerShell.exe -Version 2
```

## Comment démarrer une session à distance avec le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)]
Pour exécuter le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] dans une session à distance, créez une configuration de session (également appelée « point de terminaison ») sur l’ordinateur distant qui charge le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)]. La configuration de session est enregistrée sur l’ordinateur distant et utilisable par tout utilisateur autorisé à créer des sessions utilisant le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)].

Il s’agit d’une tâche avancée généralement effectuée par un administrateur système.

La procédure suivante utilise le paramètre **PSVersion** de l’applet de commande [Register-PSSessionConfiguration](assetId:///e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) pour créer une configuration de session qui utilise le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)]. Vous pouvez également utiliser le paramètre **PowerShellVersion** de l’applet de comment [New-PSSessionConfigurationFile](assetId:///5f3e3633-6e90-479c-aea9-ba45a1954866) pour créer un fichier de configuration de session pour une session qui charge le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)], et pouvez utiliser le paramètre **PSVersion** de l’applet de commande [Set-PSSessionConfiguration](assetId:///b21fbad3-1759-4260-b206-dcb8431cd6ea) pour modifier une configuration de session afin d’utiliser le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)].

Pour plus d’informations sur les fichiers de configuration de session, voir [about_Session_Configuration_Files](assetId:///c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Pour plus d’informations sur les configurations de session, y compris l’installation et la sécurité, voir [about_Session_Configurations [v4]](assetId:///a2fbe12a-350c-4d04-be50-24102824e3ab).

#### Pour démarrer une session à distance [!INCLUDE[psversion2](../Token/psversion2_md.md)]

1.  Pour créer une configuration de session qui requiert le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)], utilisez le paramètre **PSVersion** de l’applet de commande [Register-PSSessionConfiguration](assetId:///e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) avec la valeur « 2.0 ». Exécutez cette commande sur l’ordinateur « côté serveur » ou en fin de réception de la connexion.

    L’exemple de commande suivant crée la configuration de session PS2 sur l’ordinateur Server01. Pour exécuter cette commande, démarrez [!INCLUDE[psversion4](../Token/psversion4_md.md)] ou [!INCLUDE[psversion3](../Token/psversion3_md.md)] avec l’option **Exécuter en tant qu’administrateur »**.

    ```
    Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
    ```

2.  Pour créer une session sur l’ordinateur Server01 qui utilise la configuration de session PS2, utilisez le paramètre **ConfigurationName** d’applets de commande qui créent une session à distance, telle l’applet de commande [New-PSSession](assetId:///76f6628c-054c-4eda-ba7a-a6f28daaa26f).

    Quand une session utilisant la configuration de session démarre, le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)] est automatiquement chargé dans la session.

    La commande suivante démarre une session sur l’ordinateur Server01 qui utilise la configuration de session PS2. La commande enregistre la session dans la variable $s.

    ```
    $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
    ```

## Comment démarrer un travail en arrière-plan avec le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)]
Pour démarrer un travail en arrière-plan avec le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)], utilisez le paramètre **PSVersion** de l’applet de commande [Start-Job](assetId:///2bc04935-0deb-4ec0-b856-d7290cca6442).

La commande suivante démarre un travail en arrière-plan avec le moteur [!INCLUDE[psversion2](../Token/psversion2_md.md)].

```
Start-Job {Get-Process} -PSVersion 2.0
```

Pour plus d’informations sur les travaux en arrière-plan, voir [about_Jobs [v4]](assetId:///7362512a-8a4e-4575-b2ea-a740e5c4f002).



<!--HONumber=Apr16_HO1-->


