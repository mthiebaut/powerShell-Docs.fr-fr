---
title: Objet ISEAddOnToolCollection
ms.date: 2016-05-11
keywords: powershell,applet de commande
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
translationtype: Human Translation
ms.sourcegitcommit: 3222a0ba54e87b214c5ebf64e587f920d531956a
ms.openlocfilehash: eb02179871cd6dc6ff6cc5ba16d2074a037dbfa1

---

# Objet ISEAddOnToolCollection
  L’objet **ISEAddOnToolCollection** est une collection d’objets **ISEAddOnTool**. L’objet **$psISE.CurrentPowerShellTab.VerticalAddOnTools** en est un exemple.

## Méthodes

### Add\( Name, ControlType, \[IsVisible\] \)
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures. 

 Ajoute un nouvel outil complémentaire à la collection. Elle retourne l’outil complémentaire qui vient d’être ajouté. Avant d’exécuter cette commande, vous devez installer l’outil complémentaire sur l’ordinateur local et charger l’assembly.

 **Name** : chaîne Spécifie le nom complet de l’outil complémentaire qui est ajouté à Windows PowerShell ISE.

 **ControlType** : type Spécifie le contrôle qui est ajouté.

 **\[IsVisible\]** : valeur booléenne facultative Si la valeur est **$true**, l’outil complémentaire est immédiatement visible dans le volet d’outils associé.

```
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)

```

### Remove\( Item \)
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures. 

 Supprime l’outil complémentaire spécifié de la collection.

 **Item** : Microsoft.PowerShell.Host.ISE.ISEAddOnTool Spécifie l’objet à supprimer de Windows PowerShell ISE.

```
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)

```

### SetSelectedPowerShellTab\( psTab \)
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures. 

 Sélectionne l’onglet PowerShell spécifié par le paramètre **psTab**.

 **psTab** : Microsoft.PowerShell.Host.ISE.PowerShellTab Onglet PowerShell à sélectionner.

```

      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"

```

### Remove\( psTab \)
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures. 

 Supprime l’onglet PowerShell spécifié par le paramètre **psTab**.

 **psTab** : Microsoft.PowerShell.Host.ISE.PowerShellTab Onglet PowerShell à supprimer.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## Voir aussi
 [Objet PowerShellTab](The-PowerShellTab-Object.md) 
 [Modèle objet de script Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Informations de référence sur le modèle objet Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Aug16_HO4-->


