---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,applet de commande,psget
title: Update-Module
ms.openlocfilehash: 66535cd5b1f44e108c2bc47fa343c77c86bb21dc
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="update-module"></a>Update-Module

Télécharge et installe la version la plus récente des modules spécifiés à partir d’une galerie en ligne sur l’ordinateur local.

## <a name="description"></a>Description

L’applet de commande Update-Module installe une version plus récente d’un module Windows PowerShell qui a été installé à partir de la galerie en ligne en exécutant Install-Module sur l’ordinateur local.

Par défaut, la version la plus récente du module spécifié disponible dans la galerie en ligne est installée, sauf si vous spécifiez une version requise. Vous pouvez mettre à jour un module déjà installé, en spécifiant le nom du module ; Update-Module effectue des recherches dans $env:PSModulePath pour le module que vous souhaitez mettre à jour.

L’exécution d’Update-Module sans le paramètre Name met à jour tous les modules qui peuvent être mis à jour sur l’ordinateur local.

### <a name="notes"></a>Remarques

- Cette applet de commande s’exécute sur Windows PowerShell 3.0 ou versions ultérieures de Windows PowerShell, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.
- Si le module que vous spécifiez avec le paramètre Name n’a pas été installé à l’aide d’Install-Module, une erreur se produit. Vous pouvez uniquement exécuter Update-Module sur les modules que vous avez installés à partir de la galerie en ligne en exécutant Install-Module.
- Si Update-Module tente de mettre à jour les fichiers binaires qui sont en cours d’utilisation, Update-Module retourne une erreur qui identifie les processus du problème et demande à l’utilisateur de retenter Update-Module après l’arrêt des processus.
- Dans PowerShell 5.0 ou versions plus récentes, quand Update-Module met à jour un module, il ajoute la version la plus récente (ou spécifiée) du module afin que les versions plus anciennes et plus récentes figurent côte à côte dans le même répertoire. Il serait utile de le dire et d’afficher un exemple de la sortie de ces commandes.


## <a name="cmdlet-syntax"></a>Syntaxe de l’applet de commande
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Référence de l’aide en ligne de l’applet de commande

[Update-Module](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a>Exemples de commandes

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

### <a name="update-the-module-with-a-prerelease-version-requires--allowprerelease-flag"></a>Mettre à jour le module avec une préversion, nécessite l’indicateur -AllowPrerelease
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


### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>Mettez à jour le module TestDepWithNestedRequiredModules1 avec des dépendances.
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

