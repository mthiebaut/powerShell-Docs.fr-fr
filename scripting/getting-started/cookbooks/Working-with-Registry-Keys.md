---
title: "Utilisation de clés de Registre"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: b979750580ea5c7171569f8982d6aeca883c33ab

---

# Utilisation de clés de Registre
Étant donné que les clés de Registre sont des éléments sur des lecteurs Windows PowerShell, leur utilisation est très similaire à l’utilisation de fichiers et dossiers. Une différence importante est que chaque élément sur un lecteur Windows PowerShell basé sur un Registre est un conteneur, tout comme un dossier sur un lecteur du système de fichiers. En revanche, les entrées de Registre et les valeurs qui leur sont associées sont des propriétés des éléments, pas des éléments distincts.

### Affichage de la liste de toutes les sous-clés d’une clé de Registre
Vous pouvez afficher tous les éléments figurant directement à l’intérieur d’une clé de Registre à l’aide de l’applet de commande **Get\-ChildItem**. Pour afficher les fichiers ou éléments système masqués, ajoutez le paramètre facultatif **Force**. Par exemple, cette commande affiche les éléments figurant directement dans le lecteur Windows PowerShell HKCU:, qui correspond à la ruche du Registre HKEY\_CURRENT\_USER :

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

Il s’agit des clés de niveau supérieur visibles sous HKEY\_CURRENT\_USER dans l’Éditeur du Registre (Regedit.exe).

Vous pouvez également définir ce chemin du Registre en spécifiant le nom du fournisseur de Registre, suivi de « **::** ». Le nom complet du fournisseur de Registre est **Microsoft.PowerShell.Core\\Registry**, mais il peut être abrégé en **Registry**. Toutes les commandes suivantes répertorient le contenu directement sous HKCU :

```
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Ces commandes répertorient uniquement les éléments contenus directement, de manière très similaire à la commande **DIR** de Cmd.exe ou à la commande **ls** dans un interpréteur de commande UNIX. Pour afficher les éléments contenus, vous devez spécifier le paramètre **Recurse**. Pour répertorier toutes les clés de Registre dans HKCU, utilisez la commande suivante (cette opération peut prendre beaucoup de temps) :

```
Get-ChildItem -Path hkcu:\ -Recurse
```

L’applet de commande **Get\-ChildItem** peut exécuter des fonctionnalités de filtrage complexes via ses paramètres **Path**, **Filter**, **Include** et **Exclude**, mais ces paramètres sont généralement basés uniquement sur le nom. Vous pouvez effectuer un filtrage complexe basé sur d’autres propriétés d’éléments à l’aide de l’applet de commande **Where\-Object**. La commande suivante recherche dans HKCU:\\Software toutes les clés qui n’ont pas plus d’une sous-clé et ont aussi exactement quatre valeurs :

```
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### Copie de clés
La copie s’effectue à l’aide de l’applet de commande **Copy\-Item**. La commande suivante copie HKLM:\\SOFTWARE\\Microsoft\\Window\\\CurrentVersion et toutes ses propriétés dans HKCU:\\, en créant une nouvelle clé nommée « CurrentVersion » :

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Si vous examinez cette nouvelle clé dans l’Éditeur du Registre ou en utilisant l’applet de commande **Get\-ChildItem**, vous remarquerez que vous n’avez pas de copies des sous-clés contenues dans le nouvel emplacement. Pour copier tout le contenu d’un conteneur, vous devez spécifier le paramètre **Recurse**. Pour rendre la commande de copie précédente récursive, vous devez utiliser la commande suivante :

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

Vous pouvez toujours utiliser d’autres outils déjà disponibles pour effectuer des copies du système de fichiers. Les outils d’édition du Registre (dont reg.exe, regini.exe et regedit.exe) et les objets COM qui prennent en charge l’édition du Registre (par exemple, WScript.Shell et la classe StdRegProv de WM) peuvent être utilisés à partir de Windows PowerShell.

### Création de clés
Créer des clés dans le Registre est plus simple que créer un élément dans un système de fichiers. Étant donné que toutes les clés de Registre sont des conteneurs, il est inutile spécifier le type d’élément. Vous devez simplement fournir un chemin d’accès explicite, par exemple :

```
New-Item -Path hkcu:\software\_DeleteMe
```

Pour spécifier une clé, vous pouvez également utiliser un chemin basé sur un fournisseur :

```
New-Item -Path Registry::HKCU\_DeleteMe
```

### Suppression de clés
La suppression d’éléments est essentiellement identique pour tous les fournisseurs. Les commandes suivantes suppriment des éléments en mode silencieux :

```
Remove-Item -Path hkcu:\Software\_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### Suppression de toutes les clés sous une clé spécifique
Vous pouvez supprimer des éléments contenus à l’aide de l’applet de commande **Remove\-Item**, mais vous devez confirmer la suppression si les éléments contiennent autre chose. Par exemple, si nous tentons de supprimer la sous-clé HKCU:\\CurrentVersion que nous avons créée, nous voyons ceci :

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Pour supprimer des éléments contenus sans invite de confirmation, spécifiez le paramètre **\-Recurse** :

```
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Si vous souhaitez supprimer tous les éléments figurant dans HKCU:\\CurrentVersion mais pas HKCU:\\CurrentVersion proprement dit, vous pouvez utiliser à la place :

```
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```




<!--HONumber=Jun16_HO4-->


