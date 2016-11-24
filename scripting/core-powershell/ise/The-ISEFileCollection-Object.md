---
title: Objet ISEFileCollection
ms.date: 2016-05-11
keywords: powershell,applet de commande
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
translationtype: Human Translation
ms.sourcegitcommit: 6c666e2e23cb74818e37293410dafc9033057733
ms.openlocfilehash: 86cb3485445fdb00c9b99a20694b9bf12a6e8f2c

---

# <a name="the-isefilecollection-object"></a>Objet ISEFileCollection
  L’objet **ISEFileCollection** est une collection d’objets **ISEFile**. La collection $psISE.CurrentPowerShellTab.Files en est un exemple.

## <a name="methods"></a>Méthodes

### <a name="add-fullpath-"></a>Add\( \[fullPath\] \)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Crée et retourne un nouveau fichier sans titre, et l’ajoute à la collection. La propriété **IsUntitled** du nouveau fichier est **$true**.

 **\[fullPath\]** : chaîne facultative. Chemin entièrement spécifié du fichier. Une exception est générée si vous incluez le paramètre **fullPath** et un chemin d’accès relatif, ou si vous utilisez un nom de fichier au lieu du chemin d’accès complet.

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### <a name="remove-file-force-"></a>Remove\( File, \[Force\] \)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Supprime un fichier spécifié dans l’onglet PowerShell actuel.

 **File** : chaîne. Fichier ISEFile que vous souhaitez supprimer de la collection. Si le fichier n’a pas été enregistré, cette méthode lève une exception. Utilisez le paramètre booléen **Force** pour forcer la suppression d’un fichier non enregistré.

 **\[Force\]** : valeur booléenne facultative. Si la valeur est **$true**, le fichier peut être supprimé même s’il n’a pas été enregistré depuis sa dernière utilisation. La valeur par défaut est **$false**.

```
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile \)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Sélectionne le fichier spécifié par le paramètre **selectedFile**.

 **selectedFile** : Microsoft.PowerShell.Host.ISE.ISEFile. Fichier ISEFile que vous souhaitez sélectionner.

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## <a name="see-also"></a>Voir aussi
- [Objet ISEFile](The-ISEFile-Object.md) 
- [Modèle objet de script Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Informations de référence sur le modèle objet Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Nov16_HO4-->


