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
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="6bf03-103">Comment résoudre le problème « Avertissement : Échec du téléchargement du package 'nom_de_votre_package' » ?</span><span class="sxs-lookup"><span data-stu-id="6bf03-103">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>




<span data-ttu-id="6bf03-104">L’échec d’Install-Module ou d’Update-Module sur certains ordinateurs est parfois signalé.</span><span class="sxs-lookup"><span data-stu-id="6bf03-104">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="6bf03-105">Selon nos recherches, cela est en rapport avec la connexion réseau.</span><span class="sxs-lookup"><span data-stu-id="6bf03-105">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="6bf03-106">Nous avons récemment mis à jour le fournisseur NuGet afin qu’il puisse télécharger des packages de façon fiable.</span><span class="sxs-lookup"><span data-stu-id="6bf03-106">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="6bf03-107">Vous pouvez suivre les instructions ci-dessous pour installer la build la plus récente du fournisseur NuGet, puis installer ou mettre à jour votre module.</span><span class="sxs-lookup"><span data-stu-id="6bf03-107">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="6bf03-108">Utilisons le module « Azure » à titre d’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="6bf03-108">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

