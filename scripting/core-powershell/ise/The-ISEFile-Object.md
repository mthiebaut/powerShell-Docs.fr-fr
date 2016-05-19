---
title: Objet ISEFile
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
---
# Objet ISEFile
  Un objet **ISEFile** représente un fichier dans l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShellÂ®. Il s’agit d’une instance de la classe Microsoft.PowerShell.Host.ISE.ISEFile. Cette rubrique répertorie les méthodes et propriétés membres de cet objet. **$psISE.CurrentFile** et les fichiers de la collection Files dans un onglet PowerShell sont tous des instances de la classe Microsoft.PowerShell.Host.ISE.ISEFile.

## Méthodes

###  <a name="save-override"></a> Save\( \[saveEncoding\] \)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Enregistre le fichier sur le disque.

 **\[saveEncoding\]** – [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) facultatif
 Paramètre facultatif d’encodage de caractères à utiliser pour le fichier enregistré. La valeur par défaut est **UTF8**.

 **Exceptions**
 -   **System.IO.IOException** : le fichier n’a pas pu être enregistré.

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

###  <a name="saveas"></a> SaveAs\(filename, \[saveEncoding\]\)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Enregistre le fichier avec le nom de fichier et l’encodage spécifiés.

 **filename** \- chaîne
 Nom à utiliser pour enregistrer le fichier.

 **\[saveEncoding\]** – [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) facultatif
 Paramètre facultatif d’encodage de caractères à utiliser pour le fichier enregistré. La valeur par défaut est **UTF8**.

 **Exceptions**
 -   **System.ArgumentNullException** : le paramètre **filename** est Null.

-   **System.ArgumentException** : le paramètre **filename** est vide.

-   **System.IO.IOException** : le fichier n’a pas pu être enregistré.

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## Propriétés

###  <a name="Displayname"></a> DisplayName
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Propriété en lecture seule qui obtient la chaîne contenant le nom complet de ce fichier. Le nom est affiché dans l’onglet **Fichier** en haut de l’éditeur. La présence d’un astérisque \(\*\) à la fin du nom indique que le fichier comporte des modifications qui n’ont pas encore été enregistrées.

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

###  <a name="Editor"></a> Editor
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Propriété en lecture seule qui obtient l’[objet editor](The-ISEEditor-Object.md) utilisé pour le fichier spécifié.

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

###  <a name="Encoding"></a> Encoding
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Propriété en lecture seule qui obtient l’encodage du fichier initial. Il s’agit d’un objet **System.Text.Encoding**.

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

###  <a name="FullPath"></a> FullPath
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Propriété en lecture seule qui obtient la chaîne spécifiant le chemin complet du fichier ouvert.

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

###  <a name="IsSaved"></a> IsSaved
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Propriété booléenne en lecture seule qui renvoie la valeur **$true** si le fichier a été enregistré depuis sa dernière modification.

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

###  <a name="IsUntitled"></a> IsUntitled
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures. 

 Propriété en lecture seule qui renvoie la valeur **$true** si le fichier n’a pas encore de titre.

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## Voir aussi
 [Objet ISEFileCollection](The-ISEFileCollection-Object.md) 
 [Modèle objet de script Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Référence de modèle objet Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


