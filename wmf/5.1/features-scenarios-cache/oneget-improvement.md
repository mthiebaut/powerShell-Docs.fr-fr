---
title: "Améliorations apportées à PackageManagement (OneGet)"
contributor: jianyunt, quoctruong
translationtype: Human Translation
ms.sourcegitcommit: 3b5a3bb0ef9cf123c0cee4a36890ac61431c85ff
ms.openlocfilehash: bb1129e6aa20b64e94ddb6d7b7cf7b51b1df9ca3

---

>Remarque : fournir un titre descriptif proposé et une brève description

## Améliorations apportées à PackageManagement (OneGet) ##
Voici les corrections effectuées dans WMF 5.1 pour améliorer l’expérience utilisateur par rapport à WMF 5.0. 

1 **Alias de version**

**Scénario** : Supposez que les versions 1.0 et 2.0 d’un package P1 sont installées sur votre système. Vous souhaitez désinstaller la version 1.0. Vous exécutez donc « uninstall-package -name P1 -version 1.0 ». Vous vous attendez à ce que la version 1.0 soit désinstallée après l’exécution de l’applet de commande, mais c’est en fait la version 2.0 qui est désinstallée. 
    
Ce problème est dû au fait que le paramètre « -version » est un alias du paramètre « -minimumversion ». Quand OneGet recherche un package complet avec la version minimale 1.0, il retourne la dernière version. Ce comportement est attendu dans les cas normaux, car la recherche de la version la plus récente est dans la plupart des cas le résultat souhaité. Toutefois, il ne doit pas s’appliquer en cas d’utilisation d’uninstall-package.
    
**Solution** : l’alias -version est supprimé entièrement dans OneGet et PowerShellGet. 

2 **Invites multiples pour le démarrage du fournisseur NuGet**

**Scénario** : Quand vous exécutez Find-Module, Install-module ou d’autres applets de commande OneGet sur votre ordinateur pour la première fois, OneGet tente de démarrer le fournisseur NuGet. En effet, le fournisseur PowershellGet utilise également le fournisseur NuGet pour télécharger les modules PowerShell. OneGet invite ensuite l’utilisateur à autoriser l’installation du fournisseur NuGet. Une fois que l’utilisateur a répondu « Oui » à la demande de démarrage, la version la plus récente du fournisseur NuGet est installée. 
    
Dans certains cas, quand une ancienne version du fournisseur NuGet est installée sur votre ordinateur, celle-ci est parfois chargée en premier dans la session PowerShell (il s’agit de la condition de concurrence dans OneGet). Toutefois, le fonctionnement de PowerShellGet nécessite la dernière version du fournisseur Nuget. Ainsi, PowerShellGet demande à OneGet de redémarrer le fournisseur NuGet. C’est pourquoi plusieurs invites de démarrage du fournisseur NuGet s’affichent.

**Solution** : OneGet charge maintenant la dernière version du fournisseur NuGet pour éviter l’affichage de plusieurs invites de démarrage du fournisseur NuGet.

Vous pouvez également contourner ce problème en supprimant manuellement l’ancienne version du fournisseur NuGet (NuGet-Anycpu.exe), si elle existe, dans $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.


3 **Ordinateur avec Intranet uniquement**

**Scénario** : Pour le scénario d’entreprise, les utilisateurs travaillent dans un environnement où seul un accès à l’intranet est disponible. OneGet ne prenait pas en charge ce scénario dans WMF 5.0.

**Solution** :
- Vous pouvez télécharger le fournisseur NuGet sur un autre ordinateur disposant d’une connexion Internet à l’aide de la commande Install-PackageProvider -Name NuGet.

- Recherchez le fournisseur NuGet que vous venez d’installer sous $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget  ou  $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget. 

- Copiez les fichiers binaires vers un dossier ou un emplacement de partage réseau auquel votre ordinateur (celui qui n’a pas accès à Internet) a accès, puis installez le fournisseur NuGet avec « Install-PackageProvider NuGet -Source <Path to folder> ».


4 **Journal des événements**

Quand vous installez des packages, vous modifiez l’état de votre ordinateur. À des fins de diagnostic, OneGet enregistre désormais les événements dans le journal des événements Windows pour les activités d’installation, de désinstallation et d’enregistrement de package. Le canal d’événement est identique à celui de PowerShell, c’est-à-dire Microsoft-Windows-PowerShell, Operational.

5 **Prise en charge de l’authentification** OneGet prend maintenant en charge la recherche et l’installation des packages à partir d’un dépôt qui nécessite l’authentification de base. Vous pouvez fournir vos informations d’identification aux applets de commande Find-Package et Install-Package. Par exemple :
``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
6 **Utilisation de OneGet derrière un proxy**

OneGet accepte désormais les paramètres de proxy -ProxyCredential et -Proxy. À l’aide de ces paramètres, vous pouvez fournir l’URL de proxy et les informations d’identification de proxy aux applets de commande OneGet (par défaut, nous utilisons les paramètres proxy du système). Par exemple :
``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO3-->


