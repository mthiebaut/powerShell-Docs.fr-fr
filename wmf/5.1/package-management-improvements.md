---
title: "Améliorations apportées à la gestion des packages dans WMF 5.1 (Preview)"
ms.date: 2016-07-15
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: jaimeo
contributor: jianyunt, quoctruong
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 0a5dcec1089bd07b968c61b18ca4e6d59d0afd3b
ms.openlocfilehash: 615bdf1a82dc5078ee2f37eec70a64e25b42bda2

---

# Améliorations apportées à la gestion des packages dans WMF 5.1 (Preview) #

## Améliorations apportées à PackageManagement ##
Voici les corrections apportées dans WMF 5.1 : 

### Alias de version

**Scénario** : Si vous avez installé les versions 1.0 et 2.0 d’un package P1 sur votre système et que vous souhaitez désinstaller la version 1.0, vous devez exécuter `Uninstall-Package -Name P1 -Version 1.0`, et la version 1.0 devrait normalement être désinstallée après l’exécution de l’applet de commande. Toutefois, le résultat est que la version 2.0 est désinstallée.  
    
Cela se produit, car le paramètre `-Version` est un alias du paramètre `-MinimumVersion`. Quand PackageManagement recherche un package qualifié avec la version minimale 1.0, il retourne la dernière version. Ce comportement est attendu dans les cas normaux, car la recherche de la version la plus récente est généralement le résultat souhaité. Toutefois, il ne devrait pas s’appliquer en cas d’utilisation de la commande `Uninstall-Package`.
    
**Solution** : L’alias de `-Version` a été entièrement supprimé dans PackageManagement (également appelé OneGet) et PowerShellGet. 

### Invites multiples pour le démarrage du fournisseur NuGet

**Scénario** : Quand vous exécutez `Find-Module`, `Install-Module` ou d’autres applets de commande PackageManagement sur votre ordinateur pour la première fois, PackageManagement tente de démarrer le fournisseur NuGet. En effet, le fournisseur PowerShellGet utilise également le fournisseur NuGet pour télécharger les modules PowerShell. PackageManagement invite ensuite l’utilisateur à autoriser l’installation du fournisseur NuGet. Une fois que l’utilisateur a répondu « Oui » à la demande de démarrage, la version la plus récente du fournisseur NuGet est installée. 
    
Dans certains cas, quand une ancienne version du fournisseur NuGet est installée sur votre ordinateur, celle-ci est parfois chargée en premier dans la session PowerShell (il s’agit de la condition de concurrence dans PackageManagement). Toutefois, le fonctionnement de PowerShellGet nécessite la dernière version du fournisseur NuGet. Ainsi, PowerShellGet demande à PackageManagement de redémarrer le fournisseur NuGet. Cela entraîne l’affichage de plusieurs invites de démarrage du fournisseur NuGet.

**Solution** : Dans WMF 5.1, PackageManagement charge la dernière version du fournisseur NuGet pour éviter l’affichage de plusieurs invites de démarrage du fournisseur NuGet.

Vous pouvez également contourner ce problème en supprimant manuellement l’ancienne version du fournisseur NuGet (NuGet-Anycpu.exe), si elle existe, dans $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.


### Prise en charge de PackageManagement sur les ordinateurs avec accès à l’intranet uniquement

**Scénario** : Pour le scénario d’entreprise, les utilisateurs travaillent dans un environnement où seul un accès à l’intranet est disponible. PackageManagement ne prenait pas en charge ce scénario dans WMF 5.0.

**Scénario** : Dans WMF 5.0, PackageManagement ne prenait pas en charge les ordinateurs ayant uniquement un accès à l’intranet (et non à Internet).

**Solution** : Dans WMF 5.1, procédez comme suit pour permettre aux ordinateurs connectés à l’intranet d’utiliser PackageManagement :

1. Téléchargez le fournisseur NuGet sur un autre ordinateur disposant d’une connexion Internet à l’aide de la commande `Install-PackageProvider -Name NuGet`.

2. Recherchez le fournisseur NuGet sous `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` ou `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. Copiez les fichiers binaires dans un dossier ou un emplacement de partage réseau auquel peut accéder l’ordinateur connecté à l’intranet, puis installez le fournisseur NuGet avec `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


### Améliorations de la journalisation des événements

Quand vous installez des packages, vous modifiez l’état de l’ordinateur. Dans WMF 5.1, PackageManagement consigne désormais des événements dans le journal des événements Windows pour les activités `Install-Package`, `Uninstall-Package` et `Save-Package`. Le journal des événements est le même que celui de PowerShell, autrement dit, `Microsoft-Windows-PowerShell, Operational`.

### Prise en charge de l’authentification de base

Dans WMF 5.1, PackageManagement prend en charge la recherche et l’installation de packages à partir d’un référentiel qui nécessite l’authentification de base. Vous pouvez fournir vos informations d’identification aux applets de commande `Find-Package` et `Install-Package`. Par exemple :

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
### Prise en charge de l’utilisation de PackageManagement derrière un proxy

Dans WMF 5.1, PackageManagement accepte désormais les nouveaux paramètres de proxy `-ProxyCredential` et `-Proxy`. À l’aide de ces paramètres, vous pouvez spécifier l’URL et les informations d’identification de proxy aux applets de commande PackageManagement. Par défaut, les paramètres proxy du système sont utilisés. Par exemple :

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```




<!--HONumber=Sep16_HO3-->

