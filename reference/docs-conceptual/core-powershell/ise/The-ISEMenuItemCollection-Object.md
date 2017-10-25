---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Objet ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7ce9132021d4d5e755503e0adb355beb388a625a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2017
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="d6ce5-103">Objet ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="d6ce5-103">The ISEMenuItemCollection Object</span></span>
  <span data-ttu-id="d6ce5-104">Un objet **ISEMenuItemCollection** est une collection d’objets **ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="d6ce5-105">Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="d6ce5-106">Par exemple, l’objet **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** est utilisé pour personnaliser le menu **Module complémentaire** dans l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="d6ce5-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="d6ce5-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="d6ce5-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="d6ce5-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>
  <span data-ttu-id="d6ce5-109">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="d6ce5-110">Ajoute un élément de menu à la collection.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-110">Adds a menu item to the collection.</span></span>

 <span data-ttu-id="d6ce5-111">**DisplayName** Nom complet du menu à ajouter.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-111">**DisplayName** The display name of the menu to be added.</span></span>

 <span data-ttu-id="d6ce5-112">**Action** Objet **System.Management.Automation.ScriptBlock** qui spécifie l’action associée à cet élément de menu.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

 <span data-ttu-id="d6ce5-113">**Shortcut** Raccourci clavier associé à l’action.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-113">**Shortcut** The keyboard shortcut for the action.</span></span>

 <span data-ttu-id="d6ce5-114">**Returns** Objet ISEMenuItem qui vient d’être ajouté.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a><span data-ttu-id="d6ce5-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="d6ce5-115">Clear\(\)</span></span>
  <span data-ttu-id="d6ce5-116">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="d6ce5-117">Supprime tous les sous-menus de l’élément de menu.</span><span class="sxs-lookup"><span data-stu-id="d6ce5-117">Removes all submenus from the menu item.</span></span>

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a><span data-ttu-id="d6ce5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6ce5-118">See Also</span></span>
- [<span data-ttu-id="d6ce5-119">Objet ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="d6ce5-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md) 
- [<span data-ttu-id="d6ce5-120">Modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d6ce5-120">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="d6ce5-121">Informations de référence sur le modèle objet Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d6ce5-121">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="d6ce5-122">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="d6ce5-122">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
