---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_unregister psrepository
ms.technology: powershell
ms.openlocfilehash: c90710db47dbfdc58e1ca7f84c6d6fd8f04b5109
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="unregister-psrepository"></a>Unregister-PSRepository

Annule l’enregistrement d’un référentiel.

## <a name="description"></a>Description

L’applet de commande Unregister-PSRepository annule l’enregistrement d’un référentiel pour l’utilisateur actuel.
- L’annulation de l’enregistrement et un nouvel enregistrement du référentiel PSGallery sont autorisés pour des scénarios d’entreprise et déconnectés.
- Les utilisateurs peuvent réinscrire le dépôt PSGallery en exécutant simplement `Register-PSRepository -Default`
- Étant donné que PSGallery est le référentiel de publication par défaut dans les applets de commande Publish-Module et Publish-Script, une erreur est générée si PSGallery n’est pas disponible dans la liste des référentiels enregistrés.

## <a name="cmdlet-syntax"></a>Syntaxe de l’applet de commande

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Référence de l’aide en ligne de l’applet de commande

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a>Exemples de commandes

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a>L’annulation de l’enregistrement et un nouvel enregistrement du référentiel PSGallery sont autorisés pour des scénarios d’entreprise et déconnectés.
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```

