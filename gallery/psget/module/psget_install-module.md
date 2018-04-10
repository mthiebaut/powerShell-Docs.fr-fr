---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Install-Module
ms.openlocfilehash: 960e3a85a0f915dd9da00f6456550a335c619cea
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="install-module"></a><span data-ttu-id="11925-103">Install-Module</span><span class="sxs-lookup"><span data-stu-id="11925-103">Install-Module</span></span>

<span data-ttu-id="11925-104">Installe les modules PowerShell à partir de référentiels en ligne sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="11925-104">Installs the PowerShell modules from online repositories to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="11925-105">Description</span><span class="sxs-lookup"><span data-stu-id="11925-105">Description</span></span>

<span data-ttu-id="11925-106">L’applet de commande Install-Module télécharge un ou plusieurs modules à partir d’une galerie en ligne, les valide et les installe sur l’ordinateur local selon l’étendue d’installation spécifiée.</span><span class="sxs-lookup"><span data-stu-id="11925-106">Install-Module cmdlet downloads one or more modules from an online gallery, validates and installs them on the local computer to the specified installation scope.</span></span>

<span data-ttu-id="11925-107">L’applet de commande Install-Module obtient un ou plusieurs modules qui répondent aux critères spécifiés à partir d’une galerie en ligne, vérifie que les résultats de la recherche sont des modules valides et copie les dossiers des modules à l’emplacement d’installation.</span><span class="sxs-lookup"><span data-stu-id="11925-107">The Install-Module cmdlet gets one or more modules that meet specified criteria from an online gallery, verifies that search results are valid modules, and copies module folders to the installation location.</span></span>

<span data-ttu-id="11925-108">Quand aucune étendue n’est définie ou que la valeur du paramètre Scope est AllUsers, le module est installé dans %systemdrive%:\Program Files\WindowsPowerShell\Modules.</span><span class="sxs-lookup"><span data-stu-id="11925-108">When no scope is defined, or when the value of the Scope parameter is AllUsers, the module is installed to %systemdrive%:\Program Files\WindowsPowerShell\Modules.</span></span> <span data-ttu-id="11925-109">Quand la valeur de Scope est CurrentUser, le module est installé dans $home\Documents\WindowsPowerShell\Modules.</span><span class="sxs-lookup"><span data-stu-id="11925-109">When the value of Scope is CurrentUser, the module is installed to $home\Documents\WindowsPowerShell\Modules.</span></span>

<span data-ttu-id="11925-110">Vous pouvez filtrer vos résultats selon les versions minimales et exactes des modules spécifiés.</span><span class="sxs-lookup"><span data-stu-id="11925-110">You can filter your results based on minimum and exact versions of specified modules.</span></span>

- <span data-ttu-id="11925-111">Prise en charge des versions côte à côte dans Windows PowerShell 5.0 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="11925-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
- <span data-ttu-id="11925-112">Prise en charge de l’installation de dépendances de modules</span><span class="sxs-lookup"><span data-stu-id="11925-112">Module dependency installation support</span></span>
- <span data-ttu-id="11925-113">**Untrusted prompt :** (Invite pour les référentiels non approuvés) L’acceptation par l’utilisateur est obligatoire pour installer les modules à partir d’un référentiel non approuvé.</span><span class="sxs-lookup"><span data-stu-id="11925-113">**Untrusted prompt:**User acceptance is required for installing the modules from an untrusted repository.</span></span>
- <span data-ttu-id="11925-114">-Force réinstalle le module installé</span><span class="sxs-lookup"><span data-stu-id="11925-114">-Force reinstalls the installed module</span></span>
- <span data-ttu-id="11925-115">RequiredVersion installe la version spécifiée côte à côte avec les versions existantes sur PowerShell versions 5.0 ou ultérieures.</span><span class="sxs-lookup"><span data-stu-id="11925-115">RequiredVersion installs the specified version in SxS with existing versions on PowerShell version 5.0 or newer.</span></span>

### <a name="scope"></a><span data-ttu-id="11925-116">Étendue</span><span class="sxs-lookup"><span data-stu-id="11925-116">Scope</span></span>
<span data-ttu-id="11925-117">Spécifie l’étendue d’installation du module.</span><span class="sxs-lookup"><span data-stu-id="11925-117">Specifies the installation scope of the module.</span></span> <span data-ttu-id="11925-118">Les valeurs acceptables pour ce paramètre sont : AllUsers et CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="11925-118">The acceptable values for this parameter are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="11925-119">L’étendue d’installation par défaut est AllUsers.</span><span class="sxs-lookup"><span data-stu-id="11925-119">The default installation scope is AllUsers.</span></span>

<span data-ttu-id="11925-120">L’étendue AllUsers permet d’installer les modules à un emplacement qui est accessible à tous les utilisateurs de l’ordinateur, autrement dit $env:SystemDrive\Program Files\WindowsPowerShell\Modules.</span><span class="sxs-lookup"><span data-stu-id="11925-120">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, "$env:SystemDrive\Program Files\WindowsPowerShell\Modules".</span></span>

<span data-ttu-id="11925-121">L’étendue CurrentUser permet d’installer les modules uniquement dans $home\Documents\WindowsPowerShell\Modules, afin que le module ne soit disponible que pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="11925-121">The CurrentUser scope lets modules be installed only to "$home\Documents\WindowsPowerShell\Modules", so that the module is available only to the current user.</span></span>

## <a name="notes"></a><span data-ttu-id="11925-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="11925-122">Notes</span></span>

<span data-ttu-id="11925-123">Cette applet de commande s’exécute sur Windows PowerShell 3.0 ou versions ultérieures de Windows PowerShell, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="11925-123">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="11925-124">Si un module installé ne peut pas être importé (autrement dit, s’il ne dispose pas d’un fichier .psm1, .psd1 ou .dll du même nom dans le dossier), l’installation échoue, sauf si vous ajoutez le paramètre Force à votre commande.</span><span class="sxs-lookup"><span data-stu-id="11925-124">If an installed module cannot be imported (that is, if it does not have a .psm1, .psd1, or .dll of the same name within the folder), installation fails unless you add the Force parameter to your command.</span></span>

<span data-ttu-id="11925-125">Si une version du module sur l’ordinateur correspond à la valeur spécifiée pour le paramètre Name et que vous n’avez pas ajouté le paramètre MinimumVersion ou RequiredVersion, Install-Module se poursuit de manière silencieuse sans installer ce module.</span><span class="sxs-lookup"><span data-stu-id="11925-125">If a version of the module on the computer matches the value specified for the Name parameter, and you have not added the MinimumVersion or RequiredVersion parameter, Install-Module silently continues without installing that module.</span></span> <span data-ttu-id="11925-126">Si les paramètres MinimumVersion ou RequiredVersion sont spécifiés et que le module existant ne correspond pas aux valeurs de ce paramètre, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="11925-126">If the MinimumVersion or RequiredVersion parameters are specified, and the existing module does not match the values in that parameter, then an error occurs.</span></span> <span data-ttu-id="11925-127">Pour être plus précis : si la version du module actuellement installé est inférieure à la valeur du paramètre MinimumVersion ou différente de la valeur du paramètre RequiredVersion, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="11925-127">To be more specific: if the version of the currently-installed module is either lower than the value of the MinimumVersion parameter, or not equal to the value of the RequiredVersion parameter, an error occurs.</span></span> <span data-ttu-id="11925-128">Si la version du module installé est supérieure à la valeur du paramètre MinimumVersion ou égale à la valeur du paramètre RequiredVersion, Install-Module se poursuit de manière silencieuse sans installer ce module.</span><span class="sxs-lookup"><span data-stu-id="11925-128">If the version of the installed module is greater than the value of the MinimumVersion parameter, or equal to the value of the RequiredVersion parameter, Install-Module silently continues without installing that module.</span></span>

<span data-ttu-id="11925-129">Install-Module retourne une erreur s’il n’existe aucun module dans la galerie en ligne qui correspond au nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="11925-129">Install-Module returns an error if no module exists in the online gallery that matches the specified name.</span></span>

<span data-ttu-id="11925-130">Pour installer plusieurs modules, spécifiez un tableau de noms de modules, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="11925-130">To install multiple modules, specify an array of the module names, separated by commas.</span></span> <span data-ttu-id="11925-131">Vous ne pouvez pas ajouter MinimumVersion ou RequiredVersion si vous spécifiez plusieurs noms de modules.</span><span class="sxs-lookup"><span data-stu-id="11925-131">You cannot add MinimumVersion or RequiredVersion if you specify multiple module names.</span></span>

<span data-ttu-id="11925-132">Par défaut, les modules sont installés dans le dossier Program Files, afin d’éviter toute confusion quand vous installez les ressources DSC (Configuration de l’état souhaité) de Windows PowerShell. Vous pouvez diriger plusieurs objets PSGetItemInfo vers Install-Module ; il s’agit d’une autre façon de spécifier plusieurs modules à installer dans une seule commande.</span><span class="sxs-lookup"><span data-stu-id="11925-132">By default, modules are installed to the Program Files folder, to prevent confusion when you are installing Windows PowerShell Desired State Configuration (DSC) resources.You can pipe multiple PSGetItemInfo objects to Install-Module; this is another way of specifying multiple modules to install in a single command.</span></span>

<span data-ttu-id="11925-133">Pour éviter d’exécuter des modules qui contiennent du code malveillant, les modules installés ne sont pas automatiquement importés par l’installation.</span><span class="sxs-lookup"><span data-stu-id="11925-133">To help prevent running modules that contain malicious code, installed modules are not automatically imported by installation.</span></span> <span data-ttu-id="11925-134">Comme bonne pratique de sécurité, évaluez le code du module avant d’exécuter des applets de commande ou des fonctions dans un module pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="11925-134">As a security best practice, evaluate module code before running any cmdlets or functions in a module for the first time.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="11925-135">Syntaxe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="11925-135">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="11925-136">Référence de l’aide en ligne de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="11925-136">Cmdlet online help reference</span></span>

[<span data-ttu-id="11925-137">Install-Module</span><span class="sxs-lookup"><span data-stu-id="11925-137">Install-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398573)

## <a name="example-commands"></a><span data-ttu-id="11925-138">Exemples de commandes</span><span class="sxs-lookup"><span data-stu-id="11925-138">Example commands</span></span>

```powershell

# Install a module by name
Install-Module -Name MyDscModule

# Install multiple modules
Install-Module ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Module -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3

# Install a specific prerelease version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3-alpha -AllowPrerelease

# Install the latest version of a module by name, including prelrelease versions if one exists
Install-Module -Name ContosoServer -AllowPrerelease

# Install the latest version of a module to $home\Documents\WindowsPowerShell\Modules.
Install-Module -Name ContosoServer -Scope CurrentUser

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -RequiredVersion 1.5

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -MinimumVersion 2.5

# Install multiple modules from multiple registered repositories
Install-Module ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a module with -WhatIf
Install-Module ContosoClient -WhatIf

# Install a module with -Confirm. A prompt will be displayed to confirm the installation.
Install-Module ContosoClient -WhatIf

# -Force option reinstalls the installed module
Install-Module ContosoClient -Force

# Install a module with dependencies
Install-Module -Name
```

## <a name="install-module-cmdlet-in-pipeline-operations"></a><span data-ttu-id="11925-139">Applet de commande Install-Module dans les opérations de pipeline</span><span class="sxs-lookup"><span data-stu-id="11925-139">Install-Module cmdlet in pipeline operations</span></span>

```powershell

# Find a module and install it
Find-Module -Name "MyDSC*" | Install-Module

# Find a module and install it to the CurrentUser scope
Find-Module -Name "MyDSC*" | Install-Module -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Module to install them.
# The second command uses Get-InstalledModule to verify the modules from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Module
Get-InstalledModule

# This command finds the resource named MyResource and passes it to the Install-Module cmdlet by using the pipeline operator. The Install-Module cmdlet installs the module for the resource.
# If you pipe multiple resources to the Install-Module cmdlet from the same module, Install-Module attempts to install the module only once.
Find-DscResource -Name "MyResource" | Install-Module
Get-InstalledModule

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Module
Get-InstalledModule

```

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="11925-140">Prise en charge des versions côte à côte sur PowerShell 5.0 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="11925-140">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="11925-141">PowerShellGet assure la prise en charge des versions de modules côte à côte dans les applets de commande Install-Module, Update-Module et Publish-Module qui s’exécutent dans Windows PowerShell 5.0 ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="11925-141">PowerShellGet supports the side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>

### <a name="install-module-examples"></a><span data-ttu-id="11925-142">Exemples Install-Module</span><span class="sxs-lookup"><span data-stu-id="11925-142">Install-Module examples</span></span>

```powershell
# Install a version of the module
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Install another version of the module in Side-by-Side with already installed version.
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Get all versions of an installed module
Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...


```

## <a name="install-module-with-its-dependencies"></a><span data-ttu-id="11925-143">Installer un module avec ses dépendances</span><span class="sxs-lookup"><span data-stu-id="11925-143">Install module with its dependencies</span></span>

```powershell

# Find a module
Find-Module -Name TypePx -Repository PSGallery

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

# Find a module and its dependencies
Find-Module -Name TypePx -Repository PSGallery -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...

# Discover the dependencies list without adding -IncludeDependencies
$result = Find-Module -Name TypePx -Repository PSGallery
$result.Dependencies

Name                           Value
----                           -----
Name                           SnippetPx
CanonicalId                    powershellget:SnippetPx/#https://www.powershellgallery.com/api/v2/


# Now install the module along with its dependencies
Install-Module -Name TypePx -Repository PSGallery -Verbose

VERBOSE: Repository details, Name = 'PSGallery', Location = 'https://www.powershellgallery.com/api/v2/'; IsTrusted =
'False'; IsRegistered = 'True'.
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'PSGallery'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://www.powershellgallery.com/api/v2/' and PackageManagementProvider is
'NuGet'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'TypePx'.
VERBOSE: Performing the operation "Install-Module" on target "Version '2.0.1.20' of module 'TypePx'".

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
VERBOSE: The installation scope is specified to be 'AllUsers'.
VERBOSE: The specified module will be installed in 'C:\Program Files\WindowsPowerShell\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading module 'TypePx' with version '2.0.1.20' from the repository
'https://www.powershellgallery.com/api/v2/'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='SnippetPx'' for ''.
VERBOSE: InstallPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\SnippetPx\SnippetPx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'SnippetPx'.
VERBOSE: Hash for package 'SnippetPx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: InstallPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\TypePx\TypePx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'TypePx'.
VERBOSE: Hash for package 'TypePx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: Installing the dependency module 'SnippetPx' with version '1.0.5.18' for the module 'TypePx'.
VERBOSE: Module 'SnippetPx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18'.
VERBOSE: Module 'TypePx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\TypePx\2.0.1.20'.


# Get the installed modules
Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

```

## <a name="error-scenarios"></a><span data-ttu-id="11925-144">Scénarios d’erreur</span><span class="sxs-lookup"><span data-stu-id="11925-144">Error scenarios</span></span>

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Module'
Install-Module ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Module'
Install-Module ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -MinimumVersion 2.0

```