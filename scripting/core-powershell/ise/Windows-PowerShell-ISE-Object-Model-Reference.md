---
title: "Informations de référence sur le modèle objet Windows PowerShell ISE"
ms.date: 2016-05-11
keywords: powershell,applet de commande
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
translationtype: Human Translation
ms.sourcegitcommit: 16608d8b97ec816d77ec7b8ac2438a4d64b55fba
ms.openlocfilehash: c60a7adb5cce55392d5dc09c7ca357bfc4c73e15

---

# Informations de référence sur le modèle objet Windows PowerShell ISE
  
## Informations de référence sur le modèle objet
 Cette section fournit des informations de référence sur les classes sous-jacentes qui définissent les différents objets de l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell®. Pour afficher les objets organisés dans leur hiérarchie, consultez [Hiérarchie des modèles objet ISE](The-ISE-Object-Model-Hierarchy.md).

 [Objet ISEAddOnTool](The-ISEAddOnTool-Object.md)
 Exemples : $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.

 [Objet ISEAddOnTool](The-ISEAddOnTool-Object.md)
  [Objet ISEEditor](The-ISEEditor-Object.md)
 Exemples : $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.

 [Objet ISEFile](The-ISEFile-Object.md)
 Exemples : $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].

 [Objet ISEFileCollection](The-ISEFileCollection-Object.md)
 Exemples : $psISE.PowerShellTabs.Files.

 [Objet ISEMenuItem](The-ISEMenuItem-Object.md)
 Exemples : $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].

 [Objet ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md)
 Exemple : $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.

 [Objet ISEOptions](The-ISEOptions-Object.md)
 Exemples : $psISE.Options, $psISE.Options.DefaultOptions.

 [Objet ObjectModelRoot](The-ObjectModelRoot-Object.md)
 Exemple : L’objet $psISE racine.

 [Objet PowerShellTab](The-PowerShellTab-Object.md)
 Exemples : $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].

 [Objet PowerShellTabCollection](The-PowerShellTabCollection-Object.md)
 Exemple : $psISE.PowerShellTabs.

## Voir aussi
- [Modèle objet de script Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  



<!--HONumber=Oct16_HO1-->


