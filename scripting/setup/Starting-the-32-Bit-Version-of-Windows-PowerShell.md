---
title: "Démarrage de la version 32 bits de Windows PowerShell"
ms.date: 2016-05-11
keywords: powershell,applet de commande
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: e6e9d951b2dd10637bbf2c6afda774cd9ba32a8d
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a>Démarrage de la Version 32 bits de Windows PowerShell
Quand vous installez Windows PowerShell sur un ordinateur 64 bits, **Windows PowerShell (x86)**, version 32 bits de Windows PowerShell, est installé en plus de la version 64 bits. Quand vous exécutez Windows PowerShell, la version 64 bits s’exécute par défaut.

Toutefois, il se peut que vous deviez occasionnellement exécuter **Windows PowerShell (x86)**, par exemple, lorsque vous utilisez un module nécessitant la version 32 bits ou lorsque vous vous connectez à distance à un ordinateur 32 bits.

Pour démarrer une version 32 bits de Windows PowerShell, procédez de l’une des manières suivantes.

#### <a name="in-windows-server-2012-r2"></a>Dans Windows Server® 2012 R2

-   Dans l’écran **Démarrer**, tapez **Windows PowerShell (x86)**. Cliquez sur la vignette **Windows PowerShell x86**.

-   Dans **Server Manager**, dans le menu **Outils**, sélectionnez **Windows PowerShell (x86)**.

-   Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Recherche**, tapez **PowerShell x86**, puis cliquez sur **Windows PowerShell (x86)**.

-   Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>Dans Windows Server® 2012

-   Dans l’écran **Démarrer**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell (x86)**.

-   Dans **Server Manager**, dans le menu **Outils**, sélectionnez **Windows PowerShell (x86)**.

-   Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **recherche**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell (x86)**.

-   Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>Dans Windows® 8.1

-   Dans l’écran **Démarrer**, tapez **Windows PowerShell (x86)**. Cliquez sur la vignette **Windows PowerShell x86**.

-   Si vous exécutez les [Outils d’Administration de serveur distant](http://go.microsoft.com/fwlink/?LinkID=304145) pour Windows 8.1, vous pouvez également ouvrir Windows PowerShell x86 à partir du menu **Outils du Gestionnaire de serveur**. Sélectionnez **Windows PowerShell (x86)**.

-   Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Recherche**, tapez **PowerShell x86**, puis cliquez sur **Windows PowerShell (x86)**.
   
-   Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>Dans Windows® 8

-   Dans l’écran **Démarrer**, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Paramètres**, **Vignettes**, puis positionnez le curseur **Afficher les outils d’administration** sur Oui. Ensuite, tapez **PowerShell** puis cliquez sur **Windows PowerShell (x86)**.

-   Si vous exécutez les [Outils d’Administration de serveur distant](http://www.microsoft.com/download/details.aspx?id=28972) pour Windows 8, vous pouvez également ouvrir Windows PowerShell x86 à partir du menu **Outils du Gestionnaire de serveur**. Sélectionnez **Windows PowerShell (x86)**.

-   Dans l’écran **Démarrer** ou sur le Bureau, tapez **PowerShell (x86)**, puis cliquez sur **Windows PowerShell (x86)**.

-   Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
