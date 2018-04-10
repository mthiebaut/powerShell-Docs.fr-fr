---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Publish-Module
ms.openlocfilehash: 8b73be2814678ce143cc5b53e2b8103b3297eb6a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="publish-module"></a><span data-ttu-id="26d24-103">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="26d24-103">Publish-Module</span></span>

<span data-ttu-id="26d24-104">Publie un module spécifié à partir de l’ordinateur local sur une galerie en ligne.</span><span class="sxs-lookup"><span data-stu-id="26d24-104">Publishes a specified module from the local computer to an online gallery.</span></span>

## <a name="description"></a><span data-ttu-id="26d24-105">Description</span><span class="sxs-lookup"><span data-stu-id="26d24-105">Description</span></span>

<span data-ttu-id="26d24-106">L’applet de commande **Publish-Module** publie un module sur une galerie NuGet en ligne, à l’aide d’une clé API stockée dans le cadre du profil d’un utilisateur dans la galerie.</span><span class="sxs-lookup"><span data-stu-id="26d24-106">The **Publish-Module** cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="26d24-107">Vous pouvez indiquer le module à publier par son nom ou par le chemin d’accès au dossier le contenant.</span><span class="sxs-lookup"><span data-stu-id="26d24-107">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="26d24-108">Quand vous spécifiez un module par son nom, **Publish-Module** publie le premier module trouvé en exécutant `Get-Module -ListAvailable <Name>`.</span><span class="sxs-lookup"><span data-stu-id="26d24-108">When you specify a module by name, **Publish-Module** publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="26d24-109">Si vous spécifiez une version minimale d’un module à publier, **Publish-Module** publie le premier module avec une version qui est supérieure ou égale à la version minimale que vous avez spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26d24-109">If you specify a minimum version of a module to publish, **Publish-Module** publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="26d24-110">La publication d’un module nécessite des métadonnées affichées dans la page de la galerie pour le module.</span><span class="sxs-lookup"><span data-stu-id="26d24-110">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="26d24-111">Les métadonnées requises incluent le nom du module, la version, la description et l’auteur.</span><span class="sxs-lookup"><span data-stu-id="26d24-111">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="26d24-112">Bien que la plupart des métadonnées proviennent du manifeste du module, certaines métadonnées doivent être spécifiées dans les paramètres **Publish-Module**, comme *Tag, ReleaseNote, IconUri, ProjectUri,* et *LicenseUri*, car ces paramètres correspondent aux champs dans une galerie NuGet.</span><span class="sxs-lookup"><span data-stu-id="26d24-112">Although most metadata is taken from the module manifest, some metadata must be specified in **Publish-Module** parameters, such as *Tag, ReleaseNote, IconUri, ProjectUri,* and *LicenseUri*, because these parameters match fields in a NuGet-based gallery.</span></span>

<span data-ttu-id="26d24-113">Le paramètre RequiredVersion vous permet de spécifier la version exacte d’un module à publier.</span><span class="sxs-lookup"><span data-stu-id="26d24-113">The RequiredVersion parameter allows you to specify the exact version of a module to be published.</span></span>
<span data-ttu-id="26d24-114">Le paramètre Path prend également en charge le chemin de base de module avec le dossier de version.</span><span class="sxs-lookup"><span data-stu-id="26d24-114">The Path parameter also supports the module base path with the version folder.</span></span>
<span data-ttu-id="26d24-115">Le paramètre de commutateur Force de l’applet de commande Publish-Module démarre NuGet.exe sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="26d24-115">The Force switch parameter on Publish-Module cmdlet bootstraps the NuGet.exe without prompting.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="26d24-116">Syntaxe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="26d24-116">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Publish-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="26d24-117">Référence de l’aide en ligne de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="26d24-117">Cmdlet online help reference</span></span>

[<span data-ttu-id="26d24-118">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="26d24-118">Publish-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398575)

## <a name="example-commands"></a><span data-ttu-id="26d24-119">Exemples de commandes</span><span class="sxs-lookup"><span data-stu-id="26d24-119">Example commands</span></span>

```powershell
ContosoServer module with different versions to be published.
PS C:\\windows\\system32> Get-Module -Name ContosoServer -ListAvailable
Directory: C:\\Program Files\\WindowsPowerShell\\Modules
ModuleType Version Name ExportedCommands
---------- ------- ---- ----------------
Manifest 2.8 ContosoServer Get-ContosoServer
Manifest 2.0 ContosoServer Get-ContosoServer
Manifest 1.5 ContosoServer Get-ContosoServer
Manifest 1.0 ContosoServer Get-ContosoServer
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.0 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.5 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Path "C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0" -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
_------ ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
2.0 ContosoServer LocalRepo ContosoServer module
```

## <a name="publishing-a-module-with-dependencies"></a><span data-ttu-id="26d24-120">Publication d’un module avec des dépendances</span><span class="sxs-lookup"><span data-stu-id="26d24-120">Publishing a module with dependencies</span></span>

### <a name="create-a-module-with-dependencies-and-version-range-specified-in-requiredmodules-property-of-its-module-manifest"></a><span data-ttu-id="26d24-121">Créez un module avec des dépendances et une plage de versions spécifiées dans la propriété RequiredModules de son manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="26d24-121">Create a module with dependencies and version range specified in RequiredModules property of its module manifest.</span></span>

<span data-ttu-id="26d24-122">**Remarque :**</span><span class="sxs-lookup"><span data-stu-id="26d24-122">**Note:**</span></span>
  - <span data-ttu-id="26d24-123">\* est pris en charge uniquement dans MaximumVersion et doit également figurer à la fin de la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="26d24-123">\* is supported only in MaximumVersion and also it should be at the end of version string.</span></span>
  - <span data-ttu-id="26d24-124">\* est remplacé par 999999999 dans l’objet de version.</span><span class="sxs-lookup"><span data-stu-id="26d24-124">\* is replaced with 999999999 in the version object.</span></span>

```powershell
PS C:\windows\system32> $requiredModules = @( @{ModuleName = 'RequiredModule1'; ModuleVersion = '0.1'; MaximumVersion = '1.9'; }, @{ModuleName = 'RequiredModule2'; MaximumVersion = '1.*'; })

PS C:\windows\system32> cd C:\MyModules\ModuleWithDependencies

PS C:\MyModules\ModuleWithDependencies> New-ModuleManifest -Path .\ModuleWithDependencies.psd1 -ModuleVersion 1.0 -RequiredModules $requiredModules -Description 'ModuleWithDependencies demo module'
```

### <a name="publish-modulewithdependencies-module-with-dependencies-to-the-repository"></a><span data-ttu-id="26d24-125">Publiez un module ModuleWithDependencies avec des dépendances sur le référentiel.</span><span class="sxs-lookup"><span data-stu-id="26d24-125">Publish ModuleWithDependencies module with dependencies to the repository.</span></span>

```powershell
PS C:\MyModules\ModuleWithDependencies> Publish-Module -Path C:\MyModules\ModuleWithDependencies -Repository LocalRepo
```

### <a name="find-modulewithdependencies-module-with-its-dependencies-by-specifying--includedependencies"></a><span data-ttu-id="26d24-126">Recherchez le module ModuleWithDependencies avec ses dépendances en spécifiant -IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="26d24-126">Find ModuleWithDependencies module with its dependencies by specifying -IncludeDependencies</span></span>

```powershell
PS C:\MyModules\ModuleWithDependencies> Find-Module -Name ModuleWithDependencies -Repository LocalRepo -IncludeDependencies

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

### <a name="install-the-modulewithdependencies-module-with-dependencies"></a><span data-ttu-id="26d24-127">Installez le module ModuleWithDependencies avec les dépendances.</span><span class="sxs-lookup"><span data-stu-id="26d24-127">Install the ModuleWithDependencies module with dependencies.</span></span>
<span data-ttu-id="26d24-128">Notez que les plages de versions sont respectées lors de l’installation des dépendances.</span><span class="sxs-lookup"><span data-stu-id="26d24-128">Note that version ranges are honored during the dependency installation.</span></span>

```powershell
PS C:\windows\system32> Get-InstalledModule
PS C:\windows\system32>
PS C:\windows\system32> Install-Module -Name ModuleWithDependencies -Repository LocalRepo
PS C:\windows\system32>
PS C:\windows\system32> Get-InstalledModule

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

### <a name="contents-of-modulewithdependencies2-module-manifest-file"></a><span data-ttu-id="26d24-129">Contenu du fichier manifeste de module ModuleWithDependencies2</span><span class="sxs-lookup"><span data-stu-id="26d24-129">Contents of ModuleWithDependencies2 module manifest file</span></span>

```powershell
@{
# Version number of this module.
ModuleVersion = '2.0'
# ID used to uniquely identify this module
GUID = '0eae34da-99dd-4608-8d28-c614fe7b0841'
# Author of this module
Author = 'manikb'
# Company or vendor of this module
CompanyName = 'Unknown'
# Copyright statement for this module
Copyright = '(c) 2015 manikb. All rights reserved.'
# Description of the functionality provided by this module
Description = 'ModuleWithDependencies2 module'
# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @('RequiredModule1',
@{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'RequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'RequiredModule4'; ModuleVersion = '1.1'; MaximumVersion = '2.0'; },
@{ModuleName = 'RequiredModule5'; MaximumVersion = '1.5'; })
# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @('NestedRequiredModule1',
@{ModuleName = 'NestedRequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'NestedRequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'NestedRequiredModule4'; ModuleVersion = '0.7'; MaximumVersion = '2.4'; },
@{ModuleName = 'NestedRequiredModule5'; MaximumVersion = '1.6'; },'ModuleWithDependencies2.psm1')
# Functions to export from this module
FunctionsToExport = '\*'
# Cmdlets to export from this module
CmdletsToExport = '\*'
# Variables to export from this module
VariablesToExport = '\*'
# Aliases to export from this module
AliasesToExport = '\*'
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
      # Tags applied to this module. These help with module discovery in online galleries.
      Tags = 'Tag1', 'Tag2', 'Tag-ModuleWithDependencies2-2.0'
      # A URL to the license for this module.
      LicenseUri = 'http://modulewithdependencies2.com/license'
      # A URL to the main website for this project.
      ProjectUri = 'http://modulewithdependencies2.com/'
      # A URL to an icon representing this module.
      IconUri = 'http://modulewithdependencies2.com/icon'
      # ReleaseNotes of this module
      ReleaseNotes = 'ModuleWithDependencies2 release notes'
    } # End of PSData hashtable
} # End of PrivateData hashtable
}
```


### <a name="external-dependencies"></a><span data-ttu-id="26d24-130">Dépendances externes</span><span class="sxs-lookup"><span data-stu-id="26d24-130">External dependencies</span></span>
<span data-ttu-id="26d24-131">Certaines dépendances de module peuvent être gérées en externe, auquel cas elles doivent être ajoutées à l’entrée ExternalModuleDependencies dans la section PSData du manifeste du module.</span><span class="sxs-lookup"><span data-stu-id="26d24-131">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>

<span data-ttu-id="26d24-132">Si 'SnippetPx' n’est pas disponible dans le référentiel, l’erreur ci-dessous est générée.</span><span class="sxs-lookup"><span data-stu-id="26d24-132">If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
```powershell
Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
```