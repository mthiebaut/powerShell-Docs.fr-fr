---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: f68847ba8292a277e464025c1baa17a5aa2752f5
ms.sourcegitcommit: 4ab9a86e47b6effe8fe22ebeb81e8fadff41d31c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2017
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="8fd97-102">Prise en charge des versions côte à côte sur PowerShell 5.0 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="8fd97-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="8fd97-103">Les applets de commande Install-module, Update-Module et Publish-Module qui s’exécutent dans Windows PowerShell 5.0 ou version ultérieure offrent désormais une prise en charge des versions de modules côte à côte (SxS).</span><span class="sxs-lookup"><span data-stu-id="8fd97-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="8fd97-104">Nous avons aussi ajouté un paramètre -RequiredVersion à l’applet de commande Publish-Module pour spécifier la version à publier.</span><span class="sxs-lookup"><span data-stu-id="8fd97-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="8fd97-105">Le paramètre Path prend désormais en charge le chemin de base de module avec le dossier de version.</span><span class="sxs-lookup"><span data-stu-id="8fd97-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="8fd97-106">**Exemples Install-Module :**</span><span class="sxs-lookup"><span data-stu-id="8fd97-106">**Install-Module examples:**</span></span>
```powershell
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Get-InstalledModule -Name PSScriptAnalyzer -AllVersions

Version    Name                                Type       Repository           Description            
-------    ----                                ----       ----------           -----------            
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis... 
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```

