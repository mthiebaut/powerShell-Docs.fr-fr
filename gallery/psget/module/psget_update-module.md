---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Update-Module
ms.openlocfilehash: 89b0111eda4421606843f108dca90519b2c9379e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="update-module"></a><span data-ttu-id="303e3-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="303e3-103">Update-Module</span></span>

<span data-ttu-id="303e3-104">Télécharge et installe la version la plus récente des modules spécifiés à partir d’une galerie en ligne sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="303e3-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="303e3-105">Description</span><span class="sxs-lookup"><span data-stu-id="303e3-105">Description</span></span>

<span data-ttu-id="303e3-106">L’applet de commande Update-Module installe une version plus récente d’un module Windows PowerShell qui a été installé à partir de la galerie en ligne en exécutant Install-Module sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="303e3-106">The Update-Module cmdlet installs a newer version of a Windows PowerShell module that was installed from the online gallery by running Install-Module on the local computer.</span></span>

<span data-ttu-id="303e3-107">Par défaut, la version la plus récente du module spécifié disponible dans la galerie en ligne est installée, sauf si vous spécifiez une version requise.</span><span class="sxs-lookup"><span data-stu-id="303e3-107">By default, the newest version of the specified module available in online gallery is installed, unless you specify a required version.</span></span> <span data-ttu-id="303e3-108">Vous pouvez mettre à jour un module déjà installé, en spécifiant le nom du module ; Update-Module effectue des recherches dans $env:PSModulePath pour le module que vous souhaitez mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="303e3-108">You can update an existing, installed module by specifying the name of the module; Update-Module searches $env:PSModulePath for the module that you want to update.</span></span>

<span data-ttu-id="303e3-109">L’exécution d’Update-Module sans le paramètre Name met à jour tous les modules qui peuvent être mis à jour sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="303e3-109">Running Update-Module without the Name parameter updates all modules that can be updated on the local computer.</span></span>

### <a name="notes"></a><span data-ttu-id="303e3-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="303e3-110">Notes</span></span>

- <span data-ttu-id="303e3-111">Cette applet de commande s’exécute sur Windows PowerShell 3.0 ou versions ultérieures de Windows PowerShell, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="303e3-111">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>
- <span data-ttu-id="303e3-112">Si le module que vous spécifiez avec le paramètre Name n’a pas été installé à l’aide d’Install-Module, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="303e3-112">If the module that you specify with the Name parameter was not installed by using Install-Module, an error occurs.</span></span> <span data-ttu-id="303e3-113">Vous pouvez uniquement exécuter Update-Module sur les modules que vous avez installés à partir de la galerie en ligne en exécutant Install-Module.</span><span class="sxs-lookup"><span data-stu-id="303e3-113">You can only run Update-Module on modules that you installed from the online gallery by running Install-Module.</span></span>
- <span data-ttu-id="303e3-114">Si Update-Module tente de mettre à jour les fichiers binaires qui sont en cours d’utilisation, Update-Module retourne une erreur qui identifie les processus du problème et demande à l’utilisateur de retenter Update-Module après l’arrêt des processus.</span><span class="sxs-lookup"><span data-stu-id="303e3-114">If Update-Module attempts to update binaries that are in use, Update-Module returns an error that identifies the problem processes, and informs the user to retry Update-Module after stopping the processes.</span></span>
- <span data-ttu-id="303e3-115">Dans PowerShell 5.0 ou versions plus récentes, quand Update-Module met à jour un module, il ajoute la version la plus récente (ou spécifiée) du module afin que les versions plus anciennes et plus récentes figurent côte à côte dans le même répertoire.</span><span class="sxs-lookup"><span data-stu-id="303e3-115">On PowerShell 5.0 or newer versions, when Update-Module updates a module, it adds the latest (or specified) version of the module, so the older and newer versions are now side-by-side in the same directory.</span></span> <span data-ttu-id="303e3-116">Il serait utile de le dire et d’afficher un exemple de la sortie de ces commandes.</span><span class="sxs-lookup"><span data-stu-id="303e3-116">It would be useful to say so and to show an example of the output from these commands.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="303e3-117">Syntaxe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="303e3-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="303e3-118">Référence de l’aide en ligne de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="303e3-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="303e3-119">Update-Module</span><span class="sxs-lookup"><span data-stu-id="303e3-119">Update-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a><span data-ttu-id="303e3-120">Exemples de commandes</span><span class="sxs-lookup"><span data-stu-id="303e3-120">Example commands</span></span>

```powershell
PS C:\windows\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\windows\system32> Update-Module -Name ContosoServer
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```

### <a name="update-the-module-with-a-prerelease-version-requires--allowprerelease-flag"></a><span data-ttu-id="303e3-121">Mettre à jour le module avec une préversion, nécessite l’indicateur -AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="303e3-121">Update the module with a prerelease version, requires -AllowPrerelease flag</span></span>
```powershell
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module

PS C:\windows\system32> Find-Module ContosoServer -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
3.0.0-alpha    ConstosoServer                      MSPSGallery          The PowerShell Contoso Server deployment tools...

PS C:\windows\system32> Update-Module -Name ContosoServer -AllowPrerelease
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
3.0.0-alpha ContosoServer MSPSGallery ContosoServer module

```


### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a><span data-ttu-id="303e3-122">Mettez à jour le module TestDepWithNestedRequiredModules1 avec des dépendances.</span><span class="sxs-lookup"><span data-stu-id="303e3-122">Update the TestDepWithNestedRequiredModules1 module with dependencies.</span></span>
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module



```