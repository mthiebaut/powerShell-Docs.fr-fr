---
title: Objet ISEFileCollection
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
---
# Objet ISEFileCollection
  L’objet **ISEFileCollection** est une collection d’objets **ISEFile**. La collection $psISE.CurrentPowerShellTab.Files en est un exemple.

## Méthodes

### Add\( \[fullPath\] \)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Crée et retourne un nouveau fichier sans titre, et l’ajoute à la collection. La propriété **IsUntitled** du nouveau fichier est **$true**.

 **\[fullPath\]** : chaîne facultative
 Chemin d’accès complet du fichier. Une exception est générée si vous incluez le paramètre **fullPath** et un chemin d’accès relatif, ou si vous utilisez un nom de fichier au lieu du chemin d’accès complet.

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### Remove\( File, \[Force\] \)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Supprime un fichier spécifié dans l’onglet PowerShell actuel.

 **File** : chaîne
 Fichier ISEFile que vous souhaitez supprimer de la collection. Si le fichier n’a pas été enregistré, cette méthode lève une exception. Utilisez le paramètre booléen **Force** pour forcer la suppression d’un fichier non enregistré.

 **\[Force\]** : valeur booléenne facultative
 Si la valeur est **$true**, le fichier peut être supprimé même s’il n’a pas été enregistré depuis sa dernière utilisation. La valeur par défaut est **$false**.

```
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### SetSelectedFile\ (selectedFile \)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Sélectionne le fichier spécifié par le paramètre **selectedFile**.

 **selectedFile** : Microsoft.PowerShell.Host.ISE.ISEFile
 Fichier ISEFile que vous souhaitez sélectionner.

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## Voir aussi
 [Objet ISEFile](The-ISEFile-Object.md) 
 [Modèle objet de script Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Référence de modèle objet Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


