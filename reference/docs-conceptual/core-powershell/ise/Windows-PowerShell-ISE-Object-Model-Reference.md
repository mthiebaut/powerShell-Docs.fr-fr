---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Informations de référence sur le modèle objet Windows PowerShell ISE"
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 624ddca3895ba3e24bf52a27babdb07e8714baae
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="windows-powershell-ise-object-model-reference"></a>Informations de référence sur le modèle objet Windows PowerShell ISE
  
## <a name="object-model-reference"></a>Informations de référence sur le modèle objet
 Cette section fournit des informations de référence sur les classes sous-jacentes qui définissent les différents objets de l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell®. Pour afficher les objets organisés dans leur hiérarchie, consultez [Hiérarchie des modèles objet ISE](The-ISE-Object-Model-Hierarchy.md).

 [Objet ISEAddOnTool](The-ISEAddOnTool-Object.md) Exemples : $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.

 [Objet ISEAddOnTool](The-ISEAddOnTool-Object.md) [Objet ISEEditor](The-ISEEditor-Object.md) Exemples : $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.

 [Objet ISEFile](The-ISEFile-Object.md) Exemples : $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].

 [Objet ISEFileCollection](The-ISEFileCollection-Object.md) Exemples : $psISE.PowerShellTabs.Files.

 [Objet ISEMenuItem](The-ISEMenuItem-Object.md) Exemples : $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].

 [Objet ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) Exemple : $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.

 [Objet ISEOptions](The-ISEOptions-Object.md) Exemples : $psISE.Options, $psISE.Options.DefaultOptions.

 [Objet ObjectModelRoot](The-ObjectModelRoot-Object.md) Exemple : L’objet $psISE racine.

 [Objet PowerShellTab](The-PowerShellTab-Object.md) Exemples : $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].

 [Objet PowerShellTabCollection](The-PowerShellTabCollection-Object.md) Exemple : $psISE.PowerShellTabs.

## <a name="see-also"></a>Voir aussi
- [Modèle objet de script Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
