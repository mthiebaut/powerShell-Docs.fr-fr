---
ms.date: 2017-08-09
keywords: "powershell, applet de commande, télécharger, installer, installation, programme d’installation, windows 10, windows 8.1, windows 8.0, windows 7"
title: Installation de Windows PowerShell
ms.openlocfilehash: 781bf50b6ac649e72bcdbb708555275fb7422d94
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2017
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="aa433-103">Installation de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa433-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="aa433-104">PowerShell est installé par défaut avec chaque copie de Windows, à compter de Windows 7 SP1 et de Windows Server 2008 R2 SP1.</span><span class="sxs-lookup"><span data-stu-id="aa433-104">PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="aa433-105">Les utilisateurs Linux, macOS et Windows qui souhaitent installer **PowerShell 6** (bêta) sur leurs ordinateurs doivent :</span><span class="sxs-lookup"><span data-stu-id="aa433-105">Linux, macOS, and Windows users that would like to install **PowerShell 6** (beta), in their machines, need to:</span></span>

1. <span data-ttu-id="aa433-106">Obtenir PowerShell pour leur système d’exploitation et leur version à partir de [GitHub](https://github.com/powershell/powershell#get-powershell)</span><span class="sxs-lookup"><span data-stu-id="aa433-106">Get PowerShell for the specific OS and version, from [GitHub](https://github.com/powershell/powershell#get-powershell)</span></span>
1. <span data-ttu-id="aa433-107">Suivre les instructions d'installation</span><span class="sxs-lookup"><span data-stu-id="aa433-107">Follow the installation instructions</span></span>
  - [<span data-ttu-id="aa433-108">Linux</span><span class="sxs-lookup"><span data-stu-id="aa433-108">Linux</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [<span data-ttu-id="aa433-109">macOS</span><span class="sxs-lookup"><span data-stu-id="aa433-109">macOS</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)
  - [<span data-ttu-id="aa433-110">Windows</span><span class="sxs-lookup"><span data-stu-id="aa433-110">Windows</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

<span data-ttu-id="aa433-111">PowerShell 6 est également disponible pour Docker. Consultez les instructions sur l’[installation de Docker](https://github.com/PowerShell/PowerShell/tree/master/docker).</span><span class="sxs-lookup"><span data-stu-id="aa433-111">PowerShell 6 is also available for Docker; see [Docker installation](https://github.com/PowerShell/PowerShell/tree/master/docker) instructions.</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="aa433-112">Recherche de PowerShell dans Windows 10, 8.1, 8.0 et 7</span><span class="sxs-lookup"><span data-stu-id="aa433-112">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="aa433-113">Il est parfois difficile de localiser la console ou l’environnement d'écriture de scripts intégré (ISE) de PowerShell dans Windows, car ils ne se trouvent pas au même emplacement d’une version de Windows à l’autre.</span><span class="sxs-lookup"><span data-stu-id="aa433-113">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="aa433-114">Les tableaux suivants devraient vous aider à trouver PowerShell dans votre version de Windows.</span><span class="sxs-lookup"><span data-stu-id="aa433-114">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="aa433-115">Toutes les versions listées ici sont les versions d’origine telles qu’elles ont été publiées, sans aucune mise à jour.</span><span class="sxs-lookup"><span data-stu-id="aa433-115">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="aa433-116">Pour la console</span><span class="sxs-lookup"><span data-stu-id="aa433-116">For Console</span></span>

<span data-ttu-id="aa433-117">Version</span><span class="sxs-lookup"><span data-stu-id="aa433-117">Version</span></span> | <span data-ttu-id="aa433-118">Emplacement</span><span class="sxs-lookup"><span data-stu-id="aa433-118">Location</span></span>
-- | --
<span data-ttu-id="aa433-119">Windows 10</span><span class="sxs-lookup"><span data-stu-id="aa433-119">Windows 10</span></span> | <span data-ttu-id="aa433-120">Cliquez sur l’icône Windows en bas à gauche et commencez à taper PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa433-120">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="aa433-121">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="aa433-121">Windows 8.1, 8.0</span></span> | <span data-ttu-id="aa433-122">Sur l’écran d’accueil, commencez à taper PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa433-122">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="aa433-123">Sur un poste de travail, cliquez sur l’icône Windows en bas à gauche et commencez à taper PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa433-123">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="aa433-124">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="aa433-124">Windows 7 SP1</span></span> | <span data-ttu-id="aa433-125">Cliquez sur l’icône Windows en bas à gauche et commencez à taper PowerShell dans la zone de recherche</span><span class="sxs-lookup"><span data-stu-id="aa433-125">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="aa433-126">Pour l’ISE</span><span class="sxs-lookup"><span data-stu-id="aa433-126">For ISE</span></span>

<span data-ttu-id="aa433-127">Version</span><span class="sxs-lookup"><span data-stu-id="aa433-127">Version</span></span> | <span data-ttu-id="aa433-128">Emplacement</span><span class="sxs-lookup"><span data-stu-id="aa433-128">Location</span></span>
-- | --
<span data-ttu-id="aa433-129">Windows 10</span><span class="sxs-lookup"><span data-stu-id="aa433-129">Windows 10</span></span> | <span data-ttu-id="aa433-130">Cliquez sur l’icône Windows en bas à gauche et commencez à taper ISE</span><span class="sxs-lookup"><span data-stu-id="aa433-130">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="aa433-131">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="aa433-131">Windows 8.1, 8.0</span></span> | <span data-ttu-id="aa433-132">Sur l’écran d’accueil, tapez **PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="aa433-132">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="aa433-133">Sur un poste de travail, cliquez sur l’icône Windows en bas à gauche et tapez **PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="aa433-133">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="aa433-134">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="aa433-134">Windows 7 SP1</span></span> | <span data-ttu-id="aa433-135">Cliquez sur l’icône Windows en bas à gauche et commencez à taper PowerShell dans la zone de recherche</span><span class="sxs-lookup"><span data-stu-id="aa433-135">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="aa433-136">Recherche de PowerShell dans les versions de Windows Server</span><span class="sxs-lookup"><span data-stu-id="aa433-136">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="aa433-137">À compter de Windows Server 2008 R2, le système d’exploitation Windows peut être installé sans l’interface graphique utilisateur (GUI).</span><span class="sxs-lookup"><span data-stu-id="aa433-137">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="aa433-138">Les éditions de Windows Server sans GUI sont appelées **Core**, tandis que les éditions avec GUI sont appelées **Desktop**.</span><span class="sxs-lookup"><span data-stu-id="aa433-138">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="aa433-139">Éditions Windows Server Core</span><span class="sxs-lookup"><span data-stu-id="aa433-139">Windows Server Core editions</span></span>

<span data-ttu-id="aa433-140">Dans toutes les éditions Core, quand vous vous connectez au serveur, vous obtenez une fenêtre d’invite de commandes Windows.</span><span class="sxs-lookup"><span data-stu-id="aa433-140">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="aa433-141">Tapez `powershell` et appuyez sur **Entrée** pour démarrer PowerShell dans la session d’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="aa433-141">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span> <span data-ttu-id="aa433-142">Tapez `exit` pour mettre fin à la session PowerShell et revenir à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="aa433-142">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="aa433-143">Éditions Windows Server Desktop</span><span class="sxs-lookup"><span data-stu-id="aa433-143">Windows Server Desktop editions</span></span>

<span data-ttu-id="aa433-144">Dans toutes les éditions Desktop, cliquez sur l’icône Windows en bas à gauche et commencez à taper PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa433-144">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="aa433-145">Vous obtenez à la fois les options de la console et de l’ISE.</span><span class="sxs-lookup"><span data-stu-id="aa433-145">You get both console and ISE options.</span></span>

<span data-ttu-id="aa433-146">La seule exception à cette règle est l’ISE dans Windows Server 2008 R2 SP1 ; dans cette édition, cliquez sur l’icône Windows en bas à gauche et tapez PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="aa433-146">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="aa433-147">Comment vérifier la version de PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa433-147">How to check the version of PowerShell</span></span>

<span data-ttu-id="aa433-148">Pour trouver la version de PowerShell que vous avez installée, démarrez une console PowerShell (ou l’ISE), puis tapez `$PSVersionTable` et appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="aa433-148">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="aa433-149">Mise à niveau des instances Windows PowerShell existantes</span><span class="sxs-lookup"><span data-stu-id="aa433-149">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="aa433-150">Le package d’installation de PowerShell se trouve dans un programme d’installation WMF.</span><span class="sxs-lookup"><span data-stu-id="aa433-150">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="aa433-151">La version du programme d’installation WMF correspond à la version de PowerShell ; il n’existe aucun programme d’installation autonome de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa433-151">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="aa433-152">Si vous devez mettre à jour votre version existante de PowerShell dans Windows, utilisez le tableau suivant pour trouver le programme d’installation de la version de PowerShell que vous souhaitez mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="aa433-152">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="aa433-153">Windows</span><span class="sxs-lookup"><span data-stu-id="aa433-153">Windows</span></span> | <span data-ttu-id="aa433-154">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="aa433-154">PS 3.0</span></span> | <span data-ttu-id="aa433-155">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="aa433-155">PS 4.0</span></span> | <span data-ttu-id="aa433-156">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="aa433-156">PS 5.0</span></span> | <span data-ttu-id="aa433-157">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="aa433-157">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="aa433-158">Windows 10 (voir Note1)</span><span class="sxs-lookup"><span data-stu-id="aa433-158">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="aa433-159">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="aa433-159">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="aa433-160">installé</span><span class="sxs-lookup"><span data-stu-id="aa433-160">installed</span></span>
<span data-ttu-id="aa433-161">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="aa433-161">Windows 8.1</span></span><br/><span data-ttu-id="aa433-162">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="aa433-162">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="aa433-163">installé</span><span class="sxs-lookup"><span data-stu-id="aa433-163">installed</span></span> | [<span data-ttu-id="aa433-164">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="aa433-164">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="aa433-165">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="aa433-165">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="aa433-166">Windows 8</span><span class="sxs-lookup"><span data-stu-id="aa433-166">Windows 8</span></span><br/><span data-ttu-id="aa433-167">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="aa433-167">Windows Server 2012</span></span> | <span data-ttu-id="aa433-168">installé</span><span class="sxs-lookup"><span data-stu-id="aa433-168">installed</span></span> | [<span data-ttu-id="aa433-169">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="aa433-169">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="aa433-170">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="aa433-170">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="aa433-171">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="aa433-171">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="aa433-172">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="aa433-172">Windows 7 SP1</span></span><br/><span data-ttu-id="aa433-173">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="aa433-173">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="aa433-174">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="aa433-174">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="aa433-175">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="aa433-175">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="aa433-176">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="aa433-176">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="aa433-177">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="aa433-177">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> <span data-ttu-id="aa433-178">**Note 1** :</span><span class="sxs-lookup"><span data-stu-id="aa433-178">**Note 1**:</span></span>
  >>
  >> <span data-ttu-id="aa433-179">Dans la version initiale de Windows 10, avec les mises à jour automatiques activées, PowerShell est mis à jour de la version 5.0 à la version 5.1.</span><span class="sxs-lookup"><span data-stu-id="aa433-179">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
  >>
  >> <span data-ttu-id="aa433-180">Si la version originale de Windows 10 n’est pas mise à jour par le biais de Windows Updates, la version de PowerShell est 5.0.</span><span class="sxs-lookup"><span data-stu-id="aa433-180">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="aa433-181">Pour Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa433-181">Need Azure PowerShell</span></span>

<span data-ttu-id="aa433-182">Si vous recherchez **Azure PowerShell**, vous pouvez commencer par [Vue d’ensemble d’Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span><span class="sxs-lookup"><span data-stu-id="aa433-182">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span></span>

<span data-ttu-id="aa433-183">Sinon, vous voudrez peut-être [Installer et configurer Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span><span class="sxs-lookup"><span data-stu-id="aa433-183">Otherwise, what you might need is [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="aa433-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa433-184">See Also</span></span>

- [<span data-ttu-id="aa433-185">Configuration nécessaire pour Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa433-185">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="aa433-186">Démarrage de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa433-186">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)
