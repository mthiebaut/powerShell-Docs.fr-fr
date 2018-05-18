---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery, powershell, applet de commande, psgallery, psget
title: PowerShell Gallery
ms.openlocfilehash: cffb2f0182ffe9072f9fbbc7f4cdfcf28de276db
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="d4b2c-103">PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="d4b2c-103">The PowerShell Gallery</span></span>

<span data-ttu-id="d4b2c-104">PowerShell Gallery est le référentiel central pour le contenu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="d4b2c-105">Vous pouvez y trouver des modules PowerShell utiles contenant les commandes PowerShell et les ressources DSC (Configuration de l’état souhaité).</span><span class="sxs-lookup"><span data-stu-id="d4b2c-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="d4b2c-106">Vous pouvez également trouver des scripts PowerShell, certains d’entre eux peuvent contenir des workflows PowerShell qui présentent une série de tâches et donnent le séquencement de ces tâches.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="d4b2c-107">Certains de ces éléments sont créés par Microsoft et d’autres sont créés par la communauté PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="d4b2c-108">Vue d’ensemble de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d4b2c-108">PowerShellGet Overview</span></span>

<span data-ttu-id="d4b2c-109">Le module PowerShellGet contient des applets de commande permettant de détecter, d’installer, de mettre à jour et de publier les artefacts PowerShell tels que les modules, les ressources DSC, les fonctionnalités de rôle et les scripts à partir du référentiel [PowerShell Gallery](https://www.PowerShellGallery.com) et d’autres référentiels privés.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="d4b2c-110">Prise en main de la galerie</span><span class="sxs-lookup"><span data-stu-id="d4b2c-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="d4b2c-111">L’installation d’éléments de la galerie nécessite la dernière version du module PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="d4b2c-112">Pour des instructions complètes, consultez [Installation de PowerShellGet](installing-psget.md).</span><span class="sxs-lookup"><span data-stu-id="d4b2c-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="d4b2c-113">Pour plus d’informations sur l’utilisation des commandes PowerShellGet avec la galerie, consultez la page [Getting Started](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="d4b2c-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="d4b2c-114">Vous pouvez également exécuter *Update-Help-Module PowerShellGet* pour installer l’aide locale sur ces commandes.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="d4b2c-115">Systèmes d’exploitation pris en charge</span><span class="sxs-lookup"><span data-stu-id="d4b2c-115">Supported Operating Systems</span></span>

<span data-ttu-id="d4b2c-116">Le module **PowerShellGet** nécessite **PowerShell 3.0 ou ultérieur**.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="d4b2c-117">Par conséquent, **PowerShellGet** nécessite l’un des systèmes d’exploitation suivants :</span><span class="sxs-lookup"><span data-stu-id="d4b2c-117">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="d4b2c-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="d4b2c-118">Windows 10</span></span>
- <span data-ttu-id="d4b2c-119">Windows 8.1 Professionnel</span><span class="sxs-lookup"><span data-stu-id="d4b2c-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="d4b2c-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="d4b2c-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="d4b2c-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d4b2c-121">Windows 7 SP1</span></span>
- <span data-ttu-id="d4b2c-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="d4b2c-122">Windows Server 2016</span></span>
- <span data-ttu-id="d4b2c-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d4b2c-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="d4b2c-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d4b2c-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="d4b2c-125">**PowerShellGet** nécessite également .NET Framework 4.5 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="d4b2c-126">Vous pouvez installer .NET Framework 4.5 ou ultérieur à partir [d’ici](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="d4b2c-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="d4b2c-127">Vous avez une question ?</span><span class="sxs-lookup"><span data-stu-id="d4b2c-127">Got a question?</span></span> <span data-ttu-id="d4b2c-128">Vous avez des commentaires ?</span><span class="sxs-lookup"><span data-stu-id="d4b2c-128">Have feedback?</span></span>

<span data-ttu-id="d4b2c-129">Des informations supplémentaires relatives à PowerShell Gallery et PowerShellGet sont disponibles dans la page [Getting Started](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="d4b2c-129">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="d4b2c-130">Envoyez vos commentaires et signalez les problèmes à l’aide de [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="d4b2c-130">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>