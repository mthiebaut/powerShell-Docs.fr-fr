---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_get psrepository
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 3d0b67d012528a1ef59d8f5a1b16903d931426a3

---

# Get-PSRepository

Obtient les référentiels enregistrés sur un ordinateur.

## Description

L’applet de commande Get-PSRepository obtient les référentiels de modules PowerShell qui sont enregistrés pour l’utilisateur actuel sur un ordinateur.

Pour chaque référentiel enregistré, Get-PSRepository retourne un objet PSRepository qui peut éventuellement être transmis à Unregister-PSRepository pour annuler l’enregistrement d’un référentiel enregistré.

## Syntaxe de l’applet de commande
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## Référence de l’aide en ligne de l’applet de commande

[Get-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517127)

## Exemples de commandes

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```




<!--HONumber=Oct16_HO2-->


