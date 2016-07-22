---
title: "Améliorations apportées à OneGet dans WMF 5.1 (préversion)"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 1d0bd545b52ef56045f2ec740b05c4e0fd93bb67

---

# Améliorations de OneGet
WMF 5.1 comprend plusieurs correctifs et améliorations de l’utilisateur expérience par rapport à WMF 5.0. 

##Alias de version supprimé

**Scénario** : Si vous avez les versions 1.0 et 2.0 d’un package P1 installées sur votre système et que vous souhaitez désinstaller la version 1.0, vous devez exécuter « uninstall-package -name P1 -version 1.0 », et la version 1.0 devrait normalement être désinstallée après l’exécution de l’applet de commande. Toutefois, le résultat est que la version 2.0 est désinstallée. 
    
Cela se produit car le paramètre « -version » est un alias du paramètre « -minimumversion ». Quand OneGet recherche un package complet avec la version minimale 1.0, il retourne la dernière version. Ce comportement est attendu dans les cas normaux, car la recherche de la version la plus récente est généralement le résultat souhaité. Toutefois, il ne doit pas s’appliquer en cas d’utilisation d’uninstall-package.
    
**Solution** : Dans WMF 5.1, l’alias -version est supprimé entièrement dans OneGet et PowerShellGet. 

##Invites multiples pour le démarrage du fournisseur NuGet

**Scénario** : Quand vous exécutez Find-Module, Install-module ou d’autres applets de commande OneGet sur votre ordinateur pour la première fois, OneGet tente de démarrer le fournisseur NuGet. En effet, le fournisseur PowerShellGet utilise également le fournisseur NuGet pour télécharger les modules PowerShell. OneGet invite ensuite l’utilisateur à autoriser l’installation du fournisseur NuGet. Une fois que l’utilisateur a répondu « Oui » à la demande de démarrage, la version la plus récente du fournisseur NuGet est installée. 
    
Dans certains cas, quand une ancienne version du fournisseur NuGet est installée sur votre ordinateur, celle-ci est parfois chargée en premier dans la session PowerShell (il s’agit de la condition de concurrence dans OneGet). Toutefois, le fonctionnement de PowerShellGet nécessite la dernière version du fournisseur NuGet. Ainsi, PowerShellGet demande à OneGet de redémarrer le fournisseur NuGet. Cela entraîne l’affichage de plusieurs invites de démarrage du fournisseur NuGet.

**Solution** : Dans WMF 5.1, OneGet charge maintenant la dernière version du fournisseur NuGet pour éviter l’affichage de plusieurs invites de démarrage du fournisseur NuGet.

Vous pouvez également contourner ce problème en supprimant manuellement l’ancienne version du fournisseur NuGet (NuGet-Anycpu.exe), si elle existe, dans $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.


##Prise en charge de OneGet sur les ordinateurs avec un accès intranet uniquement

**Scénario** : Dans WMF 5.0, OneGet ne prenait pas en charge les ordinateurs ayant uniquement un accès intranet (et pas Internet).

**Solution** : Dans WMF 5.1, vous pouvez suivre ces étapes pour permettre aux ordinateurs intranet d’utiliser OneGet :

1. Téléchargez le fournisseur de NuGet à l’aide d’un autre ordinateur disposant d’une connexion Internet à l’aide de Install-PackageProvider NuGet.

2. Recherchez le fournisseur NuGet sous $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget  ou  $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget. 

3. Copiez les fichiers binaires vers un dossier ou un emplacement de partage réseau auquel l’ordinateur de l’intranet a accès, puis installez le fournisseur NuGet avec « Install-PackageProvider NuGet-Source <Path to folder> ».


##Améliorations de la journalisation des événements

Quand vous installez des packages, vous modifiez l’état de l’ordinateur. Dans WMF 5.1, OneGet enregistre désormais les événements dans le journal des événements Windows pour les activités d’installation, de désinstallation et d’enregistrement de package. Le canal d’événement est identique à celui de PowerShell, c’est-à-dire Microsoft-Windows-PowerShell, Operational.

##Prise en charge de l’authentification de base

Dans WMF 5.1, OneGet prend en charge la recherche et l’installation des packages à partir d’un dépôt qui nécessite l’authentification de base. Vous pouvez fournir vos informations d’identification aux applets de commande Find-Package et Install-Package. Par exemple :

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
##Prise en charge de OneGet derrière un proxy

Dans WMF 5.1, OneGet accepte désormais de nouveaux paramètres de proxy : -ProxyCredential et -Proxy. À l’aide de ces paramètres, vous pouvez spécifier l’URL de proxy et les informations d’identification aux applets de commande OneGet. Par défaut, les paramètres proxy du système sont utilisés. Par exemple :

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO3-->


