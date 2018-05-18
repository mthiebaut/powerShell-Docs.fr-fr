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
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="42bfb-103">Résolution des problèmes des applets de commande</span><span class="sxs-lookup"><span data-stu-id="42bfb-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="42bfb-104">Comment résoudre le problème « Avertissement : Échec du téléchargement du package 'nom_de_votre_package' » ?</span><span class="sxs-lookup"><span data-stu-id="42bfb-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="42bfb-105">L’échec d’Install-Module ou d’Update-Module sur certains ordinateurs est parfois signalé.</span><span class="sxs-lookup"><span data-stu-id="42bfb-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="42bfb-106">Selon nos recherches, cela est en rapport avec la connexion réseau.</span><span class="sxs-lookup"><span data-stu-id="42bfb-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="42bfb-107">Nous avons récemment mis à jour le fournisseur NuGet afin qu’il puisse télécharger des packages de façon fiable.</span><span class="sxs-lookup"><span data-stu-id="42bfb-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="42bfb-108">Vous pouvez suivre les instructions ci-dessous pour installer la build la plus récente du fournisseur NuGet, puis installer ou mettre à jour votre module.</span><span class="sxs-lookup"><span data-stu-id="42bfb-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="42bfb-109">Utilisons le module « Azure » à titre d’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="42bfb-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```