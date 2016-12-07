---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_save script
ms.technology: powershell
ms.openlocfilehash: 58003350b991ca10b1d8bc65964bbfdd324334b5
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="save-script"></a>Save-Script

L’applet de commande Save-Script permet d’examiner le fichier de script en l’enregistrant à un emplacement spécifié.

## <a name="description"></a>Description

L’applet de commande Save-Script enregistre le script spécifié.

## <a name="cmdlet-syntax"></a>Syntaxe de l’applet de commande

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Référence de l’aide en ligne de l’applet de commande

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>Exemples de commandes

### <a name="example-1-save-a-script-from-a-repository"></a>Exemple 1 : Enregistrer un script à partir d’un référentiel
Cette commande enregistre la dernière version du script Fabrikam-ClientScript à partir du référentiel GalleryINT dans le dossier local C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>Exemple 2 : Enregistrer une version d’un script par envoi à partir de l’applet de commande Find-Script

La première commande recherche la version 1.5 de Fabrikam-ClientScript à partir du référentiel GalleryINT et l’enregistre dans le dossier C:\ScriptSharingDemo

La deuxième commande valide les métadonnées du script enregistré.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

