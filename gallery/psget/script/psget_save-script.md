---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 7b692d33e3f86a89505b8d37c0da4177f3dff2c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="save-script" class="xliff"></a>
# Save-Script

L’applet de commande Save-Script permet d’examiner le fichier de script en l’enregistrant à un emplacement spécifié.

<a id="description" class="xliff"></a>
## Description

L’applet de commande Save-Script enregistre le script spécifié.

<a id="cmdlet-syntax" class="xliff"></a>
## Syntaxe de l’applet de commande

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
<a id="cmdlet-online-help-reference" class="xliff"></a>
## Référence de l’aide en ligne de l’applet de commande

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

<a id="example-commands" class="xliff"></a>
## Exemples de commandes

<a id="example-1-save-a-script-from-a-repository" class="xliff"></a>
### Exemple 1 : Enregistrer un script à partir d’un référentiel
Cette commande enregistre la dernière version du script Fabrikam-ClientScript à partir du référentiel GalleryINT dans le dossier local C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

<a id="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet" class="xliff"></a>
### Exemple 2 : Enregistrer une version d’un script par envoi à partir de l’applet de commande Find-Script

La première commande recherche la version 1.5 de Fabrikam-ClientScript à partir du référentiel GalleryINT et l’enregistre dans le dossier C:\ScriptSharingDemo

La deuxième commande valide les métadonnées du script enregistré.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

