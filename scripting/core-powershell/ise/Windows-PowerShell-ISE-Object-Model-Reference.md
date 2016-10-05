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
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 9bfb74ba438dd27fc2799263fc12a20edd2bb8cb

---

# Informations de référence sur le modèle objet Windows PowerShell ISE
  
## Informations de référence sur le modèle objet
 Cette section fournit des informations de référence sur les classes sous-jacentes qui définissent les différents objets de l’environnement d’écriture de scripts intégré de Windows PowerShell® (ISE). Pour afficher les objets organisés dans leur hiérarchie, consultez [Hiérarchie des modèles objet ISE](The-ISE-Object-Model-Hierarchy.md).

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
 [Modèle objet de script Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  



<!--HONumber=Aug16_HO3-->


