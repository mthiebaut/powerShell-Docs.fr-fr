---
title: "Nouveaux scénarios et fonctionnalités dans WMF 5.1 (préversion)"
ms.date: 2016-07-06
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: dcccf6880873c3f5c1b58fb1a8c546901b173879
ms.openlocfilehash: 9341b7fc3feea20cc2434065c3e512d1a8dd2b54

---

# Nouveaux scénarios et fonctionnalités dans WMF 5.1 (préversion) #

> Remarque : Ces informations sont préliminaires et susceptibles d’être modifiées.

## Éditions de PowerShell ##
À compter de la version 5.1, PowerShell est disponible dans différentes éditions qui indiquent la compatibilité de la plateforme et les différents ensembles de fonctionnalités.

- **Desktop Edition :** basée sur le .NET Framework, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions complètes de Windows telles que Server Core et Windows Desktop.
- **Core Edition :** basée sur .NET Core, elle fournit la compatibilité avec les scripts et les modules qui ciblent des versions de PowerShell exécutées sur des éditions réduites de Windows telles que Nano Server et Windows IoT.

**En savoir plus sur l’utilisation des éditions de PowerShell**
- [Déterminer la version en cours d’exécution de PowerShell]()
- [Déclarer la compatibilité d’un module avec des versions spécifiques de PowerShell]()
- [Filtrer les résultats de Get-Module par CompatiblePSEditions]()
- [Empêcher l’exécution des scripts, sauf en cas d’exécution sur une édition compatible de PowerShell]()

## Cache d’analyse de module ##
À compter de la version 5.1, PowerShell fournit le contrôle suivant sur le fichier utilisé pour mettre en cache les données relatives à un module, comme les commandes qu’il exporte.

Par défaut, ce cache est stocké dans le fichier `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Le cache est normalement lu au démarrage lors de la recherche d’une commande, et les données y sont écrites sur un thread d’arrière-plan après l’importation d’un module.

Pour modifier l’emplacement par défaut du cache, définissez la variable d’environnement PSModuleAnalysisCachePath avant de démarrer PowerShell. Les modifications apportées à cette variable d’environnement affectent uniquement les processus enfants.
La valeur doit nommer un chemin complet (y compris le nom de fichier) où PowerShell est autorisé à créer et à écrire des fichiers.
Pour désactiver le cache de fichiers, vous pouvez affecter à cette valeur un emplacement non valide, par exemple :

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

Cela définit un appareil non valide comme chemin. Si PowerShell ne peut pas écrire dans le chemin, aucune erreur n’est retournée mais vous pouvez observer la présence d’une erreur signalée par le biais d’un suivi d’erreur :

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Lors de l’écriture du cache, PowerShell recherche les modules qui n’existent plus pour éviter que le cache ne devienne volumineux inutilement.
Parfois, ces contrôles ne sont pas souhaitables, auquel cas vous pouvez les désactiver en définissant

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Cette variable d’environnement prend effet immédiatement dans le processus actif.

##Spécification de la version de module

Dans WMF 5.1, `using module` se comporte de la même façon que les autres constructions liées aux modules dans PowerShell. Auparavant, vous n’aviez aucun moyen de spécifier une version de module particulière. Si plusieurs versions étaient présentes, une erreur se produisait.


Dans WMF 5.1 :

* Vous pouvez utiliser `ModuleSpecification` [hashtable](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx). Cette table de hachage a le même format que `Get-Module -FullyQualifiedName`.

**Exemple :** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* S’il existe plusieurs versions du module, PowerShell utilise la **même logique de résolution** que `Import-Module` et ne retourne pas d’erreur (même comportement que `Import-Module` et `Import-DscResource`).

## Améliorations de la console PowerShell

Les modifications suivantes ont été apportées à Powershell.exe dans WMF 5.1 pour améliorer l’expérience de la console :

###Prise en charge de VT100

Ajout dans Windows 10 de la prise en charge des [séquences d’échappement VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
PowerShell ignore certaines séquences d’échappement de mise en forme VT100 lors du calcul des largeurs de tableaux.

Ajout dans PowerShell d’une nouvelle API que vous pouvez utiliser dans le code de mise en forme pour déterminer si VT100 est pris en charge. Par exemple :

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
Voici un [exemple](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) complet que vous pouvez utiliser pour mettre en surbrillance des correspondances à partir de Select-String.
Enregistrez l’exemple dans un fichier nommé `MatchInfo.format.ps1xml` puis, pour l’utiliser, dans votre profil ou ailleurs, exécutez `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Notez que les séquences d’échappement VT100 sont prises en charge uniquement à compter de la Mise à jour anniversaire Windows 10. Elles ne sont pas prises en charge sur les systèmes antérieurs.   

### Prise en charge du mode vi dans PSReadline

Ajout de la prise en charge du mode vi dans [PSReadline](https://github.com/lzybkr/PSReadLine). Pour utiliser le mode vi, exécutez `Set-PSReadline -EditMode vi`.

### Stdin redirigé avec entrée interactive 

Dans les versions antérieures, démarrer PowerShell avec `powershell -File -` était nécessaire quand stdin était redirigé et que vous souhaitiez entrer des commandes de manière interactive.

Avec WMF 5.1, cette option difficile à découvrir n’est plus nécessaire. Vous pouvez démarrer powershell sans option, par exemple `powershell`.

Notez qu’à l’heure actuelle PSReadline ne prend pas en charge stdin redirigé, et que l’expérience de modification de ligne de commande intégrée avec stdin redirigé est très limitée (par exemple, les touches de direction ne fonctionnent pas).  Une version ultérieure de PSReadline doit résoudre ce problème.   

##Améliorations du moteur PowerShell

Les améliorations suivantes du moteur principal PowerShell ont été implémentées dans WMF 5.1 :


## Performances ##

Les performances ont été améliorées dans certains domaines importants :

- Démarrage
- Le traitement « pipeline » vers les applets de commande ForEach-Object et Where-Object est environ 50 % plus rapide. 

Voici quelques exemples d’améliorations (les résultats peuvent varier en fonction de votre matériel) : 

| Scénario | Durée 5.0 (ms) | Durée 5.1 (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Première exécution PowerShell : `powershell -command "Unknown-Command"` | 30 000 | 13 000 |
| Création du cache d’analyse de commande : `powershell -command "Unknown-Command"` | 7000 | 520 |
| `1..1000000 | % { }` | 1400 | 750 |
  
> [!NOTE]  
> Une modification liée au démarrage peut affecter certains scénarios non pris en charge. PowerShell ne lit plus les fichiers `$pshome\*.ps1xml`. Ces fichiers ont été convertis en C# pour éviter une surcharge du processeur et des fichiers lors du traitement des fichiers XML. Les fichiers existent toujours pour prendre en charge V2 côte à côte. Ainsi, si vous modifiez le contenu des fichiers, cela n’affecte pas V5 mais uniquement V2. Notez que la modification du contenu de ces fichiers n’a jamais été un scénario pris en charge.

Une autre modification visible est la façon dont PowerShell met en cache les commandes exportées et d’autres informations pour les modules installés sur un système. Auparavant, ce cache était stocké dans le répertoire `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. Dans WMF 5.1, le cache est un fichier unique `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Pour plus de détails, consultez la page [analysis_cache.md]().



## Résolutions de bogues ##

Les bogues importants suivants ont été résolus :

### La détection automatique de module est honorée complètement `$env:PSModulePath` ###

La détection automatique de module (chargement automatique des modules sans Import-Module explicite lors de l’appel d’une commande) a été introduite dans WMF 3. Lors de l’introduction, PowerShell vérifiait la présence des commandes dans `$PSHome\Modules` avant d’utiliser `$env:PSModulePath`.

WMF 5.1 modifie ce comportement pour honorer `$env:PSModulePath` complètement. Ainsi, un module créé par l’utilisateur qui définit des commandes fournies par PowerShell (par exemple, `Get-ChildItem`) peut être chargé automatiquement et remplacer correctement la commande intégrée.

### La redirection de fichiers ne code plus en dur `-Encoding Unicode` ###

Dans toutes les versions précédentes de PowerShell, il était impossible de contrôler l’encodage de fichier utilisé par l’opérateur de redirection de fichier, par exemple `get-childitem > out.txt`, car PowerShell ajoutait `-Encoding Unicode`.

À compter de WMF 5.1, vous pouvez modifier l’encodage de fichier de la redirection en définissant `$PSDefaultParameterValues`, par exemple

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### Correction d’une régression dans l’accès aux membres de `System.Reflection.TypeInfo` ###

Une régression introduite dans WMF 5.0 interrompait l’accès aux membres de `System.Reflection.RuntimeType`, par exemple `[int].ImplementedInterfaces`.
Ce bogue a été résolu dans WMF 5.1.


### Résolution de certains problèmes liés aux objets COM ###

WMF 5.0 a introduit un nouveau binder COM pour appeler des méthodes sur des objets COM et accéder aux propriétés des objets COM.
Ce nouveau binder a amélioré les performances de manière significative, mais il a également introduit des bogues qui ont été résolus dans WMF 5.1.

#### Les conversions d’arguments n’étaient pas toujours effectuées correctement ####

Dans l’exemple suivant :

```
$obj = new-object -com wscript.shell
$obj.SendKeys([char]173)
```

La méthode SendKeys attend une chaîne, mais PowerShell n’a pas converti le caractère en chaîne, ce qui diffère la conversion en IDispatch::Invoke, qui utilise VariantChangeType pour effectuer la conversion. Dans cet exemple, cela provoque l’envoi des clés « 1 », « 7 » et « 3 » au lieu de la clé Volume.Mute attendue.

#### Les objets COM énumérables ne sont pas toujours gérés correctement ####

PowerShell énumère normalement la plupart des objets énumérables, mais une régression introduite dans WMF 5.0 empêchait l’énumération des objets COM qui implémentent IEnumerable.  Par exemple :

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

Dans l’exemple ci-dessus, WMF 5.0 écrivait incorrectement le Scripting.Dictionary dans le pipeline au lieu d’énumérer les paires clé/valeur.


### `[ordered]` n’était pas autorisé à l’intérieur des classes ###

WMF 5 a introduit des classes avec la validation des littéraux de type utilisée dans les classes.  `[ordered]` ressemble à un littéral de type, mais ce n’est pas un vrai type .Net.  WMF 5 signalait incorrectement une erreur sur `[ordered]` à l’intérieur d’une classe :

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### L’aide sur les rubriques de procédures avec plusieurs versions ne fonctionne pas ###

Avant WMF 5.1, si plusieurs versions d’un module étaient installées et que toutes partageaient une rubrique d’aide, par exemple about_PSReadline, `help about_PSReadline` retournait plusieurs rubriques sans aucun moyen évident d’afficher l’aide réelle.

WMF 5.1 résout ce problème en retournant l’aide de la version la plus récente de la rubrique.

Get-Help n’offre aucun moyen de spécifier la version pour laquelle vous souhaitez obtenir de l’aide. Pour contourner ce problème, accédez au répertoire de modules et affichez l’aide directement avec un outil tel que votre éditeur favori. 

## Améliorations de OneGet
WMF 5.1 comprend plusieurs correctifs et améliorations de l’utilisateur expérience par rapport à WMF 5.0. 

###Alias de version supprimé

**Scénario** : Si vous avez les versions 1.0 et 2.0 d’un package P1 installées sur votre système et que vous souhaitez désinstaller la version 1.0, vous devez exécuter « uninstall-package -name P1 -version 1.0 », et la version 1.0 devrait normalement être désinstallée après l’exécution de l’applet de commande. Toutefois, le résultat est que la version 2.0 est désinstallée. 
    
Cela se produit car le paramètre « -version » est un alias du paramètre « -minimumversion ». Quand OneGet recherche un package complet avec la version minimale 1.0, il retourne la dernière version. Ce comportement est attendu dans les cas normaux, car la recherche de la version la plus récente est généralement le résultat souhaité. Toutefois, il ne doit pas s’appliquer en cas d’utilisation d’uninstall-package.
    
**Solution** : Dans WMF 5.1, l’alias -version est supprimé entièrement dans OneGet et PowerShellGet. 

###Invites multiples pour le démarrage du fournisseur NuGet

**Scénario** : Quand vous exécutez Find-Module, Install-module ou d’autres applets de commande OneGet sur votre ordinateur pour la première fois, OneGet tente de démarrer le fournisseur NuGet. En effet, le fournisseur PowerShellGet utilise également le fournisseur NuGet pour télécharger les modules PowerShell. OneGet invite ensuite l’utilisateur à autoriser l’installation du fournisseur NuGet. Une fois que l’utilisateur a répondu « Oui » à la demande de démarrage, la version la plus récente du fournisseur NuGet est installée. 
    
Dans certains cas, quand une ancienne version du fournisseur NuGet est installée sur votre ordinateur, celle-ci est parfois chargée en premier dans la session PowerShell (il s’agit de la condition de concurrence dans OneGet). Toutefois, le fonctionnement de PowerShellGet nécessite la dernière version du fournisseur NuGet. Ainsi, PowerShellGet demande à OneGet de redémarrer le fournisseur NuGet. Cela entraîne l’affichage de plusieurs invites de démarrage du fournisseur NuGet.

**Solution** : Dans WMF 5.1, OneGet charge maintenant la dernière version du fournisseur NuGet pour éviter l’affichage de plusieurs invites de démarrage du fournisseur NuGet.

Vous pouvez également contourner ce problème en supprimant manuellement l’ancienne version du fournisseur NuGet (NuGet-Anycpu.exe), si elle existe, dans $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.


###Prise en charge de OneGet sur les ordinateurs avec un accès intranet uniquement

**Scénario** : Dans WMF 5.0, OneGet ne prenait pas en charge les ordinateurs ayant uniquement un accès intranet (et pas Internet).

**Solution** : Dans WMF 5.1, vous pouvez suivre ces étapes pour permettre aux ordinateurs intranet d’utiliser OneGet :

1. Téléchargez le fournisseur de NuGet à l’aide d’un autre ordinateur disposant d’une connexion Internet à l’aide de Install-PackageProvider NuGet.

2. Recherchez le fournisseur NuGet sous $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget  ou  $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget. 

3. Copiez les fichiers binaires vers un dossier ou un emplacement de partage réseau auquel l’ordinateur de l’intranet a accès, puis installez le fournisseur NuGet avec « Install-PackageProvider NuGet-Source <Path to folder> ».


###Améliorations de la journalisation des événements

Quand vous installez des packages, vous modifiez l’état de l’ordinateur. Dans WMF 5.1, OneGet enregistre désormais les événements dans le journal des événements Windows pour les activités d’installation, de désinstallation et d’enregistrement de package. Le canal d’événement est identique à celui de PowerShell, c’est-à-dire Microsoft-Windows-PowerShell, Operational.

###Prise en charge de l’authentification de base

Dans WMF 5.1, OneGet prend en charge la recherche et l’installation des packages à partir d’un dépôt qui nécessite l’authentification de base. Vous pouvez fournir vos informations d’identification aux applets de commande Find-Package et Install-Package. Par exemple :

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
###Prise en charge de OneGet derrière un proxy

Dans WMF 5.1, OneGet accepte désormais de nouveaux paramètres de proxy : -ProxyCredential et -Proxy. À l’aide de ces paramètres, vous pouvez spécifier l’URL de proxy et les informations d’identification aux applets de commande OneGet. Par défaut, les paramètres proxy du système sont utilisés. Par exemple :

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO1-->


