---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande
ms.date: 2016-12-12
title: Objet PowerShellTabCollection
ms.technology: powershell
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: 38bac3445fd94022f03c0f336bd17f9033dfedc2
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-powershelltabcollection-object"></a>Objet PowerShellTabCollection
  L’objet collection **PowerShellTab** est une collection d’objets **PowerShellTab**. Chaque objet **PowerShellTab** fonctionne comme un environnement d’exécution distinct. Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.PowerShellTabs. L’objet **$psISE.PowerShellTabs** en est un exemple.

## <a name="methods"></a>Méthodes

### <a name="add"></a>Add\(\)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Ajoute un nouvel onglet PowerShell à la collection. Elle retourne l’onglet qui vient d’être ajouté.

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Supprime l’onglet spécifié par le paramètre **psTab**.

 **psTab**
 Onglet PowerShell à supprimer.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Sélectionne l’onglet PowerShell qui est spécifié par le paramètre **psTab** pour le définir comme onglet PowerShell actuellement actif.

 **psTab**
 Onglet PowerShell à sélectionner.

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a>Voir aussi
- [Objet PowerShellTab](The-PowerShellTab-Object.md) 
- [Modèle objet de script Windows PowerShell ISE](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Informations de référence sur le modèle objet Windows PowerShell ISE](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Hiérarchie du modèle objet ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  
