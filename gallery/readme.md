---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery, powershell, applet de commande, psgallery, psget
title: PowerShell Gallery
ms.openlocfilehash: 9fe341e4b297764321f3b3f07caca8ef4b8b40e0
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2017
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="ed2b6-103">PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="ed2b6-103">The PowerShell Gallery</span></span>

<span data-ttu-id="ed2b6-104">PowerShell Gallery est le référentiel central pour le contenu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed2b6-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="ed2b6-105">Les nouvelles commandes PowerShell ou les ressources DSC (configuration de l’état souhaité) sont disponibles dans la galerie.</span><span class="sxs-lookup"><span data-stu-id="ed2b6-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="ed2b6-106">Vue d’ensemble de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="ed2b6-106">PowerShellGet Overview</span></span>

<span data-ttu-id="ed2b6-107">Le module PowerShellGet contient des applets de commande permettant de détecter, d’installer, de mettre à jour et de publier les artefacts PowerShell tels que les modules, les ressources DSC, les fonctionnalités de rôle et les scripts à partir du référentiel [PowerShell Gallery](https://www.PowerShellGallery.com) et d’autres référentiels privés.</span><span class="sxs-lookup"><span data-stu-id="ed2b6-107">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="ed2b6-108">Prise en main de la galerie</span><span class="sxs-lookup"><span data-stu-id="ed2b6-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="ed2b6-109">L’installation d’éléments à partir de la galerie nécessite la dernière version du module PowerShellGet, qui est disponible dans Windows 10, dans Windows Management Framework (WMF) 5.0 ou dans le programme d’installation basé sur MSI (pour PowerShell 3 et 4).</span><span class="sxs-lookup"><span data-stu-id="ed2b6-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="ed2b6-110">[**Obtenir Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="ed2b6-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="ed2b6-111">[**Obtenir WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) ou</span><span class="sxs-lookup"><span data-stu-id="ed2b6-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="ed2b6-112">**Obtenir le programme d’installation de MSI**</span><span class="sxs-lookup"><span data-stu-id="ed2b6-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="ed2b6-113">Avec le module [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) le plus récent, vous pouvez effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ed2b6-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="ed2b6-114">Parcourir les éléments de la galerie avec [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) et [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span><span class="sxs-lookup"><span data-stu-id="ed2b6-114">Search through items in the Gallery with [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>
-   <span data-ttu-id="ed2b6-115">Enregistrer des éléments dans votre système à partir de la galerie avec [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) et [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span><span class="sxs-lookup"><span data-stu-id="ed2b6-115">Save items to your system from the Gallery with [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) and [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span></span>
-   <span data-ttu-id="ed2b6-116">Installer des éléments à partir de la galerie avec [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) et [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span><span class="sxs-lookup"><span data-stu-id="ed2b6-116">Install items from the Gallery with [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span></span>
-   <span data-ttu-id="ed2b6-117">Charger des éléments dans la galerie avec [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) et [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span><span class="sxs-lookup"><span data-stu-id="ed2b6-117">Upload items to the Gallery with [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) and [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span></span>
-   <span data-ttu-id="ed2b6-118">Ajouter votre propre référentiel personnalisé avec [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span><span class="sxs-lookup"><span data-stu-id="ed2b6-118">Add your own custom repository with [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span></span>

<span data-ttu-id="ed2b6-119">Pour plus d’informations sur l’utilisation des commandes PowerShellGet avec la galerie, consultez la page [Getting Started](psgallery/psgallery_gettingstarted.md).</span><span class="sxs-lookup"><span data-stu-id="ed2b6-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="ed2b6-120">Vous pouvez également exécuter *Update-Help-Module PowerShellGet* pour installer l’aide locale sur ces commandes.</span><span class="sxs-lookup"><span data-stu-id="ed2b6-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="ed2b6-121">Systèmes d’exploitation pris en charge</span><span class="sxs-lookup"><span data-stu-id="ed2b6-121">Supported Operating Systems</span></span>

<span data-ttu-id="ed2b6-122">Le module **PowerShellGet** nécessite **PowerShell 3.0 ou ultérieur**.</span><span class="sxs-lookup"><span data-stu-id="ed2b6-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="ed2b6-123">Par conséquent, **PowerShellGet** nécessite l’un des systèmes d’exploitation suivants :</span><span class="sxs-lookup"><span data-stu-id="ed2b6-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="ed2b6-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="ed2b6-124">Windows 10</span></span>
- <span data-ttu-id="ed2b6-125">Windows 8.1 Professionnel</span><span class="sxs-lookup"><span data-stu-id="ed2b6-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="ed2b6-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="ed2b6-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="ed2b6-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="ed2b6-127">Windows 7 SP1</span></span>
- <span data-ttu-id="ed2b6-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="ed2b6-128">Windows Server 2016</span></span>
- <span data-ttu-id="ed2b6-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ed2b6-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="ed2b6-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="ed2b6-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="ed2b6-131">**PowerShellGet** nécessite également .NET Framework 4.5 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="ed2b6-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="ed2b6-132">Vous pouvez installer .NET Framework 4.5 ou ultérieur à partir [d’ici](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="ed2b6-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="ed2b6-133">Vous avez une question ?</span><span class="sxs-lookup"><span data-stu-id="ed2b6-133">Got a question?</span></span> <span data-ttu-id="ed2b6-134">Vous avez des commentaires ?</span><span class="sxs-lookup"><span data-stu-id="ed2b6-134">Have feedback?</span></span>

<span data-ttu-id="ed2b6-135">Des informations supplémentaires relatives à PowerShell Gallery et PowerShellGet sont disponibles dans la page [Getting Started](psgallery/psgallery_gettingstarted.md).</span><span class="sxs-lookup"><span data-stu-id="ed2b6-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="ed2b6-136">Envoyez vos commentaires et signalez les problèmes à l’aide de [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="ed2b6-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>

