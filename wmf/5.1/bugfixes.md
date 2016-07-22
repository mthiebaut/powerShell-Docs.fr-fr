---
title: "Résolutions de bogues dans WMF 5.1 (préversion)"
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
ms.openlocfilehash: 90d57af0c8b90e709769525455ae39557b9c7176

---

# Résolutions de bogues dans WMF 5.1 (préversion)#

## Résolutions de bogues ##

Les bogues importants suivants sont résolus dans WMF 5.1 :

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

Cette modification résout également les [problèmes 1752224 sur Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

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



<!--HONumber=Jul16_HO3-->


