---
title: Objet ISEMenuItem
ms.date: 2016-05-11
keywords: powershell,applet de commande
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
translationtype: Human Translation
ms.sourcegitcommit: fe3d7885b7c031a24a737f58523c8018cfc36146
ms.openlocfilehash: 43477d0742612f331f74833a1d70e69692b5b8e7

---

# Objet ISEMenuItem
  Un objet **ISEMenuItem** est une instance de la classe Microsoft.PowerShell.Host.ISE.ISEMenuItem. Tous les objets du menu **Modules complémentaires** sont des instances de la classe **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.

## Propriétés

###  <a name="DisplayName"></a> DisplayName
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Propriété en lecture seule qui obtient le nom complet de l’élément de menu.

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

###  <a name="Action"></a> Action
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Propriété en lecture seule qui obtient le bloc de script. Elle appelle l’action qui est associée à l’élément de menu sur lequel vous cliquez.

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

###  <a name="Shortcut"></a> Shortcut
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Propriété en lecture seule qui obtient le raccourci clavier d’entrée Windows associé à l’élément de menu.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

###  <a name="Submenus"></a> Submenus
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Propriété en lecture seule qui obtient la [liste des sous-menus](The-ISEMenuItemCollection-Object.md) de l’élément de menu.

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## Exemple de script
 Pour mieux comprendre l’utilisation du menu Modules complémentaires et ses propriétés de script, consultez l’exemple de script suivant.

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## Voir aussi
 [Objet ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) 
 [Modèle objet de script Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Référence de modèle objet Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Oct16_HO1-->


