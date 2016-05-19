---
title: Autres objets de script utiles
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
---
# Autres objets de script utiles
  Les objets suivants fournissent des fonctionnalités de script supplémentaires dans Windows PowerShell ISE. Ils ne sont pas inclus dans la hiérarchie **$psISE**.

## Objets de script utiles

### $psUnsupportedConsoleApplications
 Il existe certaines restrictions sur la façon dont Windows PowerShell ISE interagit avec les applications de console. Une commande ou un script d’automatisation qui nécessite l’intervention de l’utilisateur peut ne pas fonctionner de la même façon qu’à partir de la console Windows PowerShell. Vous pouvez empêcher l’exécution de ces commandes ou scripts dans le volet Commande de Windows PowerShell ISE. L’objet **$psUnsupportedConsoleApplications** conserve la liste de ces commandes. Si vous essayez d’exécuter les commandes de cette liste, vous obtenez un message indiquant qu’elles ne sont pas prises en charge. Le script suivant ajoute une entrée à la liste.

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### $psLocalHelp
 Il s’agit d’un objet de dictionnaire qui gère un mappage sensible au contexte entre des rubriques d’aide et leurs liens correspondants dans le fichier d’aide HTML compilé local. Il est utilisé pour localiser l’aide locale d’une rubrique particulière. Vous pouvez ajouter ou supprimer des rubriques dans cette liste. L’exemple de code suivant illustre certaines paires clé-valeur contenues dans **$psLocalHelp**..

```
# See the local help map
$psLocalHelp |Format-List

```

### Sortie exemple

|||
|-|-|
|Clé : Add\-Computer|Valeur : WindowsPowerShellHelp.chm::\/html\/093f660c\-b8d5\-43cf\-aa0c\-54e5e54e76f9.htm|
|Clé : Add\-Content|Valeur : WindowsPowerShellHelp.chm::\/html\/0c836a1b\-f389\-4e9a\-9325\-0f415686d194.htm|

 Le script suivant ajoute une entrée à la liste.

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### $psOnlineHelp
 Il s’agit d’un objet de dictionnaire qui gère un mappage sensible au contexte entre des titres de rubriques d’aide et leurs URL externes correspondantes. Il est utilisé pour localiser l’aide d’une rubrique particulière sur le web. Vous pouvez ajouter ou supprimer des rubriques dans cette liste.

```
$psOnlineHelp |format-list

```

### Sortie exemple

|||
|-|-|
|Clé : Add\-Computer|Valeur : http:\/\/go.microsoft.com\/fwlink\/p\/?LinkID\=135194|
|Clé : Add\-Content|Valeur : http:\/\/go.microsoft.com\/fwlink\/p\/?LinkID\=113278|

 Le script suivant ajoute une entrée à la liste.

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## Voir aussi
 [Modèle objet de script Windows PowerShell ISE](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  


<!--HONumber=May16_HO2-->


