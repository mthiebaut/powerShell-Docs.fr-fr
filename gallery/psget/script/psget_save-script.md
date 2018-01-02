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
# <a name="save-script"></a><span data-ttu-id="8e6ee-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="8e6ee-103">Save-Script</span></span>

<span data-ttu-id="8e6ee-104">L’applet de commande Save-Script permet d’examiner le fichier de script en l’enregistrant à un emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="8e6ee-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="8e6ee-105">Description</span><span class="sxs-lookup"><span data-stu-id="8e6ee-105">Description</span></span>

<span data-ttu-id="8e6ee-106">L’applet de commande Save-Script enregistre le script spécifié.</span><span class="sxs-lookup"><span data-stu-id="8e6ee-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="8e6ee-107">Syntaxe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="8e6ee-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="8e6ee-108">Référence de l’aide en ligne de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="8e6ee-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="8e6ee-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="8e6ee-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="8e6ee-110">Exemples de commandes</span><span class="sxs-lookup"><span data-stu-id="8e6ee-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="8e6ee-111">Exemple 1 : Enregistrer un script à partir d’un référentiel</span><span class="sxs-lookup"><span data-stu-id="8e6ee-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="8e6ee-112">Cette commande enregistre la dernière version du script Fabrikam-ClientScript à partir du référentiel GalleryINT dans le dossier local C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="8e6ee-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="8e6ee-113">Exemple 2 : Enregistrer une version d’un script par envoi à partir de l’applet de commande Find-Script</span><span class="sxs-lookup"><span data-stu-id="8e6ee-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="8e6ee-114">La première commande recherche la version 1.5 de Fabrikam-ClientScript à partir du référentiel GalleryINT et l’enregistre dans le dossier C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="8e6ee-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="8e6ee-115">La deuxième commande valide les métadonnées du script enregistré.</span><span class="sxs-lookup"><span data-stu-id="8e6ee-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a><span data-ttu-id="8e6ee-116">Exemple 3 : Enregistrer une préversion d’un script à partir d’un référentiel</span><span class="sxs-lookup"><span data-stu-id="8e6ee-116">Example 3: Save a prerelease version of a script from a repository</span></span>
<span data-ttu-id="8e6ee-117">Cette commande enregistre la dernière version du script Fabrikam-ClientScript à partir du référentiel GalleryINT dans le dossier local C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="8e6ee-117">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```

