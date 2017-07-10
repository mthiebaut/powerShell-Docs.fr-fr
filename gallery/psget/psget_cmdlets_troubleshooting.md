---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: ccb39f44e8d11f1e2a912da0c4f18b700e836c91
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="how-to-resolve-warning-package-your-package-name-failed-to-download-issue" class="xliff"></a>
## Comment résoudre le problème « Avertissement : Échec du téléchargement du package 'nom_de_votre_package' » ?




L’échec d’Install-Module ou d’Update-Module sur certains ordinateurs est parfois signalé.
Selon nos recherches, cela est en rapport avec la connexion réseau.
Nous avons récemment mis à jour le fournisseur NuGet afin qu’il puisse télécharger des packages de façon fiable.
Vous pouvez suivre les instructions ci-dessous pour installer la build la plus récente du fournisseur NuGet, puis installer ou mettre à jour votre module.
Utilisons le module « Azure » à titre d’exemple ci-dessous.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

