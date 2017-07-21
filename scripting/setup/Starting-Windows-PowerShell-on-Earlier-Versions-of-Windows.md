---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Démarrage de Windows PowerShell sur des versions antérieures de Windows"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: cb56fded1e67a4f4219d210dd95078314e855b1a
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="66c5a-103">Démarrage de Windows PowerShell sur des versions antérieures de Windows</span><span class="sxs-lookup"><span data-stu-id="66c5a-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="66c5a-104">Cette section explique comment démarrer Windows PowerShell et l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell sur Windows® 7, Windows Server® 2008 R2 et Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="66c5a-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="66c5a-105">Elle explique également comment activer la fonctionnalité facultative pour Windows PowerShell ISE dans Windows PowerShell 2.0 sur Windows Server® 2008 R2 et Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="66c5a-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="66c5a-106">Pour installer Windows PowerShell 4.0 sur des systèmes pris en charge, téléchargez et installez [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span><span class="sxs-lookup"><span data-stu-id="66c5a-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="66c5a-107">Pour plus d’informations, voir [Installation de Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="66c5a-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="66c5a-108">Pour installer Windows PowerShell 3.0 sur des systèmes pris en charge, téléchargez et installez [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="66c5a-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="66c5a-109">Pour plus d’informations, voir [Installation de Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="66c5a-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="66c5a-110">Comment démarrer Windows PowerShell sur des versions antérieures de Windows</span><span class="sxs-lookup"><span data-stu-id="66c5a-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="66c5a-111">Pour démarrer la version installée de Windows PowerShell 3.0 ou Windows PowerShell 4.0, le cas échéant, utilisez une des méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="66c5a-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="66c5a-112">À partir du menu Démarrer</span><span class="sxs-lookup"><span data-stu-id="66c5a-112">From the Start Menu</span></span>

-   <span data-ttu-id="66c5a-113">Cliquez sur **Démarrer**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="66c5a-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

-   <span data-ttu-id="66c5a-114">À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="66c5a-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="66c5a-115">À l’invite de commandes</span><span class="sxs-lookup"><span data-stu-id="66c5a-115">At the Command Prompt</span></span>

-   <span data-ttu-id="66c5a-116">Dans Cmd.exe, Windows PowerShell ou Windows PowerShell ISE, pour démarrer Windows PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="66c5a-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="66c5a-117">Vous pouvez également utiliser les paramètres du programme PowerShell.exe pour personnaliser la session.</span><span class="sxs-lookup"><span data-stu-id="66c5a-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="66c5a-118">Pour plus d’informations, voir [Aide sur la ligne de commande PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="66c5a-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="66c5a-119">Avec des privilèges d’administration (« Exécuter en tant qu’administrateur »)</span><span class="sxs-lookup"><span data-stu-id="66c5a-119">With Administrative privileges ("Run as administrator")</span></span>

1.  <span data-ttu-id="66c5a-120">Cliquez sur **Démarrer**, tapez **PowerShell**, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="66c5a-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="66c5a-121">Comment démarrer Windows PowerShell ISE sur des versions antérieures de Windows</span><span class="sxs-lookup"><span data-stu-id="66c5a-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="66c5a-122">Utilisez une des méthodes suivantes pour démarrer Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="66c5a-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="66c5a-123">À partir du menu Démarrer</span><span class="sxs-lookup"><span data-stu-id="66c5a-123">From the Start Menu</span></span>

-   <span data-ttu-id="66c5a-124">Cliquez sur **Démarrer**, tapez **ISE**, puis cliquez sur **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="66c5a-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

-   <span data-ttu-id="66c5a-125">À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="66c5a-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="66c5a-126">À l’invite de commandes</span><span class="sxs-lookup"><span data-stu-id="66c5a-126">At the Command Prompt</span></span>

-   <span data-ttu-id="66c5a-127">Dans Cmd.exe, Windows PowerShell ou Windows PowerShell ISE, pour démarrer Windows PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="66c5a-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="66c5a-128">ou</span><span class="sxs-lookup"><span data-stu-id="66c5a-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="66c5a-129">Avec des privilèges d’administration (« Exécuter en tant qu’administrateur »)</span><span class="sxs-lookup"><span data-stu-id="66c5a-129">With Administrative privileges ("Run as administrator")</span></span>

1.  <span data-ttu-id="66c5a-130">Cliquez sur **Démarrer**, tapez **ISE**, cliquez avec le bouton droit sur **Windows PowerShell ISE**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="66c5a-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="66c5a-131">Comment activer Windows PowerShell ISE sur des versions antérieures de Windows</span><span class="sxs-lookup"><span data-stu-id="66c5a-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="66c5a-132">Dans Windows PowerShell 4.0 et Windows PowerShell 3.0, Windows PowerShell ISE est activé par défaut sur toutes les versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="66c5a-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="66c5a-133">S’il n’est pas activé, Windows Management Framework 4.0 ou Windows Management Framework 3.0 l’active.</span><span class="sxs-lookup"><span data-stu-id="66c5a-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="66c5a-134">Dans Windows PowerShell 2.0, Windows PowerShell ISE est activé par défaut sur Windows 7.</span><span class="sxs-lookup"><span data-stu-id="66c5a-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="66c5a-135">Toutefois, sur Windows Server 2008 R2 et Windows Server 2008, c’est une fonctionnalité facultative.</span><span class="sxs-lookup"><span data-stu-id="66c5a-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="66c5a-136">Pour activer Windows PowerShell ISE dans Windows PowerShell 2.0 sur Windows Server 2008 R2 ou Windows Server 2008, utilisez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="66c5a-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="66c5a-137">Pour activer Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="66c5a-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1.  <span data-ttu-id="66c5a-138">Démarrez le Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="66c5a-138">Start Server Manager.</span></span>

2.  <span data-ttu-id="66c5a-139">Cliquez sur **Fonctionnalités**, puis sur **Ajouter des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="66c5a-139">Click **Features** and then click **Add Features**.</span></span>

3.  <span data-ttu-id="66c5a-140">Dans Sélectionner des fonctionnalités, cliquez sur Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="66c5a-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

