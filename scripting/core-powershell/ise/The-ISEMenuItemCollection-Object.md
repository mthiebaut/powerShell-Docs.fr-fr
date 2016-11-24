---
title: Objet ISEMenuItemCollection
ms.date: 2016-05-11
keywords: powershell,applet de commande
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
translationtype: Human Translation
ms.sourcegitcommit: 6c666e2e23cb74818e37293410dafc9033057733
ms.openlocfilehash: 489c9492e8de213145b71a7963e180fe1a4ad5b6

---

# <a name="the-isemenuitemcollection-object"></a>Objet ISEMenuItemCollection
  Un objet **ISEMenuItemCollection** est une collection d’objets **ISEMenuItem**. Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Par exemple, l’objet **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** est utilisé pour personnaliser le menu **Module complémentaire** dans l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell®.

## <a name="method"></a>Méthode

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Ajoute un élément de menu à la collection.

 **DisplayName**
 Nom complet du menu à ajouter.

 **Action**
 Objet **System.Management.Automation.ScriptBlock** qui spécifie l’action associée à cet élément de menu.

 **Shortcut**
 Raccourci clavier associé à l’action.

 **Returns**
 Objet ISEMenuItem qui vient d’être ajouté.

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a>Clear\(\)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Supprime tous les sous-menus de l’élément de menu.

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a>Voir aussi
- [Objet ISEMenuItem](The-ISEMenuItem-Object.md) 
- [Modèle objet de script Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Informations de référence sur le modèle objet Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Nov16_HO4-->


