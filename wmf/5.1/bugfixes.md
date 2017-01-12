---
title: "Résolutions de bogues dans WMF 5.1"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 09316fef0594697a60a1bd4acabf39588f75edc2
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
# <a name="bug-fixes-in-wmf-51"></a>Résolutions de bogues dans WMF 5.1#

## <a name="bug-fixes"></a>Résolutions de bogues ##

Les bogues importants suivants sont résolus dans WMF 5.1 :

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>La détection automatique de module respecte entièrement `$env:PSModulePath` ###

La détection automatique de module (chargement automatique des modules sans Import-Module explicite lors de l’appel d’une commande) a été introduite dans WMF 3. Lors de l’introduction, PowerShell vérifiait la présence des commandes dans `$PSHome\Modules` avant d’utiliser `$env:PSModulePath`.

WMF 5.1 modifie ce comportement pour honorer `$env:PSModulePath` complètement. Ainsi, un module créé par l’utilisateur qui définit des commandes fournies par PowerShell (par exemple, `Get-ChildItem`) peut être chargé automatiquement et remplacer correctement la commande intégrée.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>La redirection de fichiers ne code plus en dur `-Encoding Unicode` ###

Dans toutes les versions précédentes de PowerShell, il était impossible de contrôler l’encodage de fichier utilisé par l’opérateur de redirection de fichier, par exemple `Get-ChildItem > out.txt`, car PowerShell ajoutait `-Encoding Unicode`.

À compter de WMF 5.1, vous pouvez modifier l’encodage de fichier de la redirection en définissant `$PSDefaultParameterValues` :

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Correction d’une régression dans l’accès aux membres de `System.Reflection.TypeInfo` ###

Une régression introduite dans WMF 5.0 interrompait l’accès aux membres de `System.Reflection.RuntimeType`, par exemple `[int].ImplementedInterfaces`.
Ce bogue a été résolu dans WMF 5.1.


### <a name="fixed-some-issues-with-com-objects"></a>Résolution de certains problèmes liés aux objets COM ###

WMF 5.0 a introduit un nouveau binder COM pour appeler des méthodes sur des objets COM et accéder aux propriétés des objets COM. Ce nouveau binder a amélioré les performances de manière significative, mais il a également introduit des bogues qui ont été résolus dans WMF 5.1.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Les conversions d’arguments n’étaient pas toujours effectuées correctement ####

Dans l’exemple suivant :

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

La méthode SendKeys attend une chaîne, mais PowerShell n’a pas converti le caractère en chaîne, ce qui diffère la conversion en IDispatch::Invoke, qui utilise VariantChangeType pour effectuer la conversion. Dans cet exemple, cela provoque l’envoi des clés « 1 », « 7 » et « 3 » au lieu de la clé Volume.Mute attendue.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Les objets COM énumérables ne sont pas toujours gérés correctement ####

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

Cette modification résout également le [problème 1752224 sur Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224).

### <a name="ordered-was-not-allowed-inside-classes"></a>`[ordered]` n’était pas autorisé à l’intérieur des classes ###

WMF 5.0 a introduit des classes avec la validation des littéraux de type utilisée dans les classes.  
`[ordered]` ressemble à un littéral de type, mais n’est pas un vrai type .NET. WMF 5.0 signalait de façon erronée une erreur sur `[ordered]` à l’intérieur d’une classe :

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>L’aide sur les rubriques de procédures avec plusieurs versions ne fonctionne pas ###

Avant WMF 5.1, si plusieurs versions d’un module étaient installées et que toutes partageaient une rubrique d’aide, par exemple about_PSReadline, `help about_PSReadline` retournait plusieurs rubriques sans aucun moyen évident d’afficher l’aide réelle.

WMF 5.1 résout ce problème en retournant l’aide de la version la plus récente de la rubrique.

`Get-Help` n’offre aucun moyen de spécifier la version pour laquelle vous souhaitez obtenir de l’aide. Pour contourner ce problème, accédez au répertoire de modules et affichez l’aide directement avec un outil tel que votre éditeur favori. 
