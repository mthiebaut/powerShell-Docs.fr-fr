---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_cmdlets_troubleshooting
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 740c72620e1a5a114716f924f859c57cad125614

---

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




<!--HONumber=Oct16_HO2-->


