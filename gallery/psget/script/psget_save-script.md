---
ms.date: 2017-10-17
contributor: keithb
ms.topic: reference
keywords: gallery,powershell,applet de commande,psget
title: Save-Script
ms.openlocfilehash: b54e8ba074b7cadd52df781c9021332ccc90f9fd
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
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

### <a name="example-1-save-a-script-from-a-repository"></a>Exemple 1 : Enregistrer un script à partir d’un référentiel
Cette commande enregistre la dernière version du script Fabrikam-ClientScript à partir du référentiel GalleryINT dans le dossier local C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>Exemple 2 : Enregistrer une version d’un script par envoi à partir de l’applet de commande Find-Script

La première commande recherche la version 1.5 de Fabrikam-ClientScript à partir du référentiel GalleryINT et l’enregistre dans le dossier C:\ScriptSharingDemo

La deuxième commande valide les métadonnées du script enregistré.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a>Exemple 3 : Enregistrer une préversion d’un script à partir d’un référentiel
Cette commande enregistre la dernière version du script Fabrikam-ClientScript à partir du référentiel GalleryINT dans le dossier local C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```

