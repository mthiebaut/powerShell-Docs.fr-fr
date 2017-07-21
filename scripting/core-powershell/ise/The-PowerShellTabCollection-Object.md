---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Objet PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="0dffd-103">Objet PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="0dffd-103">The PowerShellTabCollection Object</span></span>
  <span data-ttu-id="0dffd-104">L’objet collection **PowerShellTab** est une collection d’objets **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="0dffd-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="0dffd-105">Chaque objet **PowerShellTab** fonctionne comme un environnement d’exécution distinct.</span><span class="sxs-lookup"><span data-stu-id="0dffd-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="0dffd-106">Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="0dffd-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="0dffd-107">L’objet **$psISE.PowerShellTabs** en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="0dffd-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="0dffd-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0dffd-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="0dffd-109">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="0dffd-109">Add\(\)</span></span>
  <span data-ttu-id="0dffd-110">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="0dffd-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0dffd-111">Ajoute un nouvel onglet PowerShell à la collection.</span><span class="sxs-lookup"><span data-stu-id="0dffd-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="0dffd-112">Elle retourne l’onglet qui vient d’être ajouté.</span><span class="sxs-lookup"><span data-stu-id="0dffd-112">It returns the newly added tab.</span></span>

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="0dffd-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="0dffd-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="0dffd-114">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="0dffd-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0dffd-115">Supprime l’onglet spécifié par le paramètre **psTab**.</span><span class="sxs-lookup"><span data-stu-id="0dffd-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

 <span data-ttu-id="0dffd-116">**psTab**
 Onglet PowerShell à supprimer.</span><span class="sxs-lookup"><span data-stu-id="0dffd-116">**psTab**
 The PowerShell tab to remove.</span></span>

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="0dffd-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="0dffd-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="0dffd-118">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="0dffd-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="0dffd-119">Sélectionne l’onglet PowerShell qui est spécifié par le paramètre **psTab** pour le définir comme onglet PowerShell actuellement actif.</span><span class="sxs-lookup"><span data-stu-id="0dffd-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

 <span data-ttu-id="0dffd-120">**psTab**
 Onglet PowerShell à sélectionner.</span><span class="sxs-lookup"><span data-stu-id="0dffd-120">**psTab**
 The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0dffd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0dffd-121">See Also</span></span>
- [<span data-ttu-id="0dffd-122">Objet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="0dffd-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="0dffd-123">Modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="0dffd-123">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="0dffd-124">Informations de référence sur le modèle objet Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="0dffd-124">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="0dffd-125">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="0dffd-125">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
