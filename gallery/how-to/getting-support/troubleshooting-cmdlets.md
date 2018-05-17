---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,applet de commande,psget
title: Résolution des problèmes des applets de commande
ms.openlocfilehash: 6295a5b99aa19db933569638d84e490ad81eedc7
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="troubleshooting-cmdlets"></a>Résolution des problèmes des applets de commande

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Comment résoudre le problème « Avertissement : Échec du téléchargement du package 'nom_de_votre_package' » ?

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