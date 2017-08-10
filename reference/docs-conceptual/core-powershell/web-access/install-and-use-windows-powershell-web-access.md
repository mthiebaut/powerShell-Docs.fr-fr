---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "installer et utiliser Accès Web Windows PowerShell"
ms.openlocfilehash: a860f7c22829da46f0458ea729fa0afd1fe4fb6f
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
#  <a name="install-and-use-windows-powershell-web-access"></a><span data-ttu-id="f02be-103">Installer et utiliser Accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f02be-103">Install and Use Windows PowerShell Web Access</span></span>

<span data-ttu-id="f02be-104">Mise à jour : 5 novembre 2013</span><span class="sxs-lookup"><span data-stu-id="f02be-104">Updated: November 5, 2013</span></span>

<span data-ttu-id="f02be-105">S’applique à : Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="f02be-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="f02be-106">Accès Web Windows PowerShell®, fonctionnalité introduite initialement dans Windows Server® 2012, joue le rôle de passerelle Windows PowerShell, en fournissant une console web Windows PowerShell ciblée vers un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f02be-106">Windows PowerShell® Web Access, first introduced in Windows Server® 2012, acts as a Windows PowerShell gateway, providing a web-based Windows PowerShell console that is targeted at a remote computer.</span></span> <span data-ttu-id="f02be-107">Elle permet aux professionnels de l’informatique d’exécuter des commandes et des scripts Windows PowerShell à partir d’une console Windows PowerShell dans un navigateur web, sans nécessiter Windows PowerShell, ni de logiciel de gestion à distance ou d’installation d’un plug-in de navigateur sur le périphérique client.</span><span class="sxs-lookup"><span data-stu-id="f02be-107">It enables IT Pros to run Windows PowerShell commands and scripts from a Windows PowerShell console in a web browser, with no Windows PowerShell, remote management software, or browser plug-in installation necessary on the client device.</span></span> <span data-ttu-id="f02be-108">Tout ce qui est requis pour exécuter la console web Windows PowerShell est une passerelle Accès Web Windows PowerShell correctement configurée et un navigateur de périphérique client qui prend en charge JavaScript® et accepte les cookies.</span><span class="sxs-lookup"><span data-stu-id="f02be-108">All that is required to run the web-based Windows PowerShell console is a properly-configured Windows PowerShell Web Access gateway, and a client device browser that supports JavaScript® and accepts cookies.</span></span>

<span data-ttu-id="f02be-109">Un périphérique client est par exemple un ordinateur portable, un ordinateur personnel non professionnel, une tablette, une borne Web publique, un ordinateur sans système d’exploitation Windows ou encore un navigateur de téléphone portable.</span><span class="sxs-lookup"><span data-stu-id="f02be-109">Examples of client devices include laptops, non-work personal computers, borrowed computers, tablet computers, web kiosks, computers that are not running a Windows-based operating system, and cell phone browsers.</span></span> <span data-ttu-id="f02be-110">Les informaticiens peuvent effectuer des tâches de gestion stratégiques sur des serveurs Windows distants à partir de périphériques ayant accès à une connexion Internet et à un navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="f02be-110">IT Pros can perform critical management tasks on remote Windows-based servers from devices that have access to an Internet connection and a web browser.</span></span>

<span data-ttu-id="f02be-111">Après avoir installé et configuré correctement la passerelle, les utilisateurs peuvent accéder à une console Windows PowerShell à l’aide d’un navigateur web.</span><span class="sxs-lookup"><span data-stu-id="f02be-111">After successful gateway setup and configuration, users can access a Windows PowerShell console by using a web browser.</span></span> <span data-ttu-id="f02be-112">Quand les utilisateurs ouvrent le site web Accès Web Windows PowerShell sécurisé, ils peuvent exécuter une console web Windows PowerShell après une authentification réussie.</span><span class="sxs-lookup"><span data-stu-id="f02be-112">When users open the secured Windows PowerShell Web Access website, they can run a web-based Windows PowerShell console after successful authentication.</span></span>

<span data-ttu-id="f02be-113">L’installation et la configuration d’Accès Web Windows PowerShell forment un processus en trois étapes :</span><span class="sxs-lookup"><span data-stu-id="f02be-113">Windows PowerShell Web Access setup and configuration is a three-step process:</span></span>

1.  <span data-ttu-id="f02be-114">Installation d’Accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f02be-114">Installing Windows PowerShell Web Access</span></span>

2.  <span data-ttu-id="f02be-115">Configuration de la passerelle</span><span class="sxs-lookup"><span data-stu-id="f02be-115">Configuring the gateway</span></span>

3.  <span data-ttu-id="f02be-116">Configuration des règles d’autorisation qui permettent aux utilisateurs d’accéder à la console web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f02be-116">Configuring authorization rules that allow users access to the web-based Windows PowerShell console</span></span>

<span data-ttu-id="f02be-117">Avant d’installer et de configurer Accès Web Windows PowerShell, nous vous recommandons de lire ce guide dans son intégralité, qui inclut des instructions sur la façon d’installer, de sécuriser et de désinstaller cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="f02be-117">Before you install and configure Windows PowerShell Web Access, we recommend that you read this entire guide, which includes instructions about how to install, secure, and uninstall Windows PowerShell Web Access.</span></span> <span data-ttu-id="f02be-118">La rubrique [Utiliser la console web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) décrit comment les utilisateurs se connectent à la console web, et couvre les limitations et les différences entre la console Windows PowerShell basée sur le web et la console **powershell.exe**.</span><span class="sxs-lookup"><span data-stu-id="f02be-118">The [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) topic describes how users sign in to the web-based console, and covers limitations and differences between the web-based Windows PowerShell console and the **powershell.exe** console.</span></span> <span data-ttu-id="f02be-119">Les utilisateurs finaux de la console web doivent lire la rubrique [Utiliser la console web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), mais il n’est pas nécessaire pour eux de lire le reste de ce guide.</span><span class="sxs-lookup"><span data-stu-id="f02be-119">End users of the web-based console should read [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), but do not need to read the rest of this guide.</span></span>

<span data-ttu-id="f02be-120">La présente rubrique ne fournit pas d’instructions approfondies sur les opérations de serveur web (IIS), mais décrit uniquement les étapes requises pour configurer la passerelle Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-120">This topic does not provide in-depth Web Server (IIS) operations guidance; only those steps required to configure the Windows PowerShell Web Access gateway are described in this topic.</span></span> <span data-ttu-id="f02be-121">Pour plus d’informations sur la configuration et la sécurisation des sites web dans IIS, voir les ressources de documentation IIS dans la section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="f02be-121">For more information about configuring and securing websites in IIS, see the IIS documentation resources in the See Also section.</span></span>

<span data-ttu-id="f02be-122">Le diagramme suivant illustre le fonctionnement d’Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-122">The following diagram shows how Windows PowerShell Web Access works.</span></span>

<span><img src="https://i-technet.sec.s-msft.com/dynimg/IC564303.jpeg" title="Windows PowerShell Web Access diagram" alt="Windows PowerShell Web Access diagram" id="ee15fa8f-ce13-49e5-933d-514f6d60a2b1" /></span>

<span data-ttu-id="f02be-123">Dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="f02be-123">In this topic:</span></span>

-   [<span data-ttu-id="f02be-124">Configuration requise pour exécuter Accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f02be-124">Requirements for running Windows PowerShell Web Access</span></span>](#BKMK_reqs)

-   [<span data-ttu-id="f02be-125">Prise en charge de navigateurs et de périphériques clients</span><span class="sxs-lookup"><span data-stu-id="f02be-125">Browser and client device support</span></span>](#BKMK_browser)

-   [<span data-ttu-id="f02be-126">Déploiement (rapide) recommandé</span><span class="sxs-lookup"><span data-stu-id="f02be-126">Recommended (quick) deployment</span></span>](#BKMK_recm)

-   [<span data-ttu-id="f02be-127">Déploiement personnalisé</span><span class="sxs-lookup"><span data-stu-id="f02be-127">Custom deployment</span></span>](#BKMK_custom)

-   [<span data-ttu-id="f02be-128">Configurer un certificat authentique</span><span class="sxs-lookup"><span data-stu-id="f02be-128">Configure a genuine certificate</span></span>](#BKMK_configcert)

<a href="" id="BKMK_reqs"></a>

<span data-ttu-id="f02be-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configuration requise pour exécuter Accès Web Windows PowerShell</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f02be-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requirements for running Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f02be-130">Accès Web Windows PowerShell nécessite l’exécution, sur le serveur sur lequel la passerelle doit s’exécuter, d’un serveur web (IIS), de .NET Framework 4.5 et de Windows PowerShell 3.0 ou Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="f02be-130">Windows PowerShell Web Access requires Web Server (IIS), .NET Framework 4.5, and Windows PowerShell 3.0 or Windows PowerShell 4.0 to be running on the server on which you want to run the gateway.</span></span> <span data-ttu-id="f02be-131">Vous pouvez installer Accès Web Windows PowerShell sur un serveur qui exécute Windows Server 2012 R2 ou Windows Server 2012 en utilisant l’Assistant Ajout de rôles et de fonctionnalités dans le Gestionnaire de serveur ou des applets de commande de déploiement Windows PowerShell pour le Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="f02be-131">You can install Windows PowerShell Web Access on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either the Add Roles and Features Wizard in Server Manager, or Windows PowerShell deployment cmdlets for Server Manager.</span></span> <span data-ttu-id="f02be-132">Quand vous installez Accès Web Windows PowerShell à l’aide du Gestionnaire de serveur ou de ses applets de commande de déploiement, les rôles et fonctionnalités requis sont automatiquement ajoutés dans le cadre du processus d’installation.</span><span class="sxs-lookup"><span data-stu-id="f02be-132">When you install Windows PowerShell Web Access by using Server Manager or its deployment cmdlets, required roles and features are automatically added as part of the installation process.</span></span>

<span data-ttu-id="f02be-133">Accès Web Windows PowerShell permet aux utilisateurs distants d’accéder aux ordinateurs de votre organisation en utilisant Windows PowerShell dans un navigateur web.</span><span class="sxs-lookup"><span data-stu-id="f02be-133">Windows PowerShell Web Access allows remote users to access computers in your organization by using Windows PowerShell in a web browser.</span></span> <span data-ttu-id="f02be-134">Bien qu’Accès Web Windows PowerShell soit un outil de gestion pratique et puissant, l’accès web présente des risques de sécurité et doit être configuré de manière aussi sécurisée que possible.</span><span class="sxs-lookup"><span data-stu-id="f02be-134">Although Windows PowerShell Web Access is a convenient and powerful management tool, the web-based access poses security risks, and should be configured as securely as possible.</span></span> <span data-ttu-id="f02be-135">Nous recommandons aux administrateurs qui configurent la passerelle Accès Web Windows PowerShell d’utiliser les couches de sécurité disponibles, à la fois les règles d’autorisation basées sur des applets de commande incluses avec Accès Web Windows PowerShell et les couches de sécurité disponibles dans le serveur web (IIS) et les applications tierces.</span><span class="sxs-lookup"><span data-stu-id="f02be-135">We recommend that administrators who configure the Windows PowerShell Web Access gateway use available security layers, both the cmdlet-based authorization rules included with Windows PowerShell Web Access, and security layers that are available in Web Server (IIS) and third-party applications.</span></span> <span data-ttu-id="f02be-136">Cette documentation contient à la fois des exemples non sécurisés destinés uniquement aux environnements de test et des exemples recommandés pour des déploiements sécurisés.</span><span class="sxs-lookup"><span data-stu-id="f02be-136">This documentation includes both unsecure examples that are only recommended for test environments, as well as examples that are recommended for secure deployments.</span></span>

<a href="" id="BKMK_browser"></a>

<span data-ttu-id="f02be-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Prise en charge de navigateurs et de périphériques clients</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f02be-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser and client device support</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f02be-138">Accès Web Windows PowerShell prend en charge les navigateurs suivants.</span><span class="sxs-lookup"><span data-stu-id="f02be-138">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="f02be-139">Bien que les navigateurs mobiles ne soient pas officiellement pris en charge, nombre d’entre eux sont susceptibles de pouvoir exécuter la console web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-139">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="f02be-140">D’autres navigateurs acceptant les cookies, exécutant JavaScript et exécutant des sites Web HTTPS sont censés fonctionner, mais n’ont pas été testés officiellement.</span><span class="sxs-lookup"><span data-stu-id="f02be-140">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="f02be-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Navigateurs d’ordinateur de bureau pris en charge</span></a></span><span class="sxs-lookup"><span data-stu-id="f02be-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="f02be-142">Windows® Internet Explorer® pour Microsoft Windows® 8.0, 9.0, 10.0 et 11.0</span><span class="sxs-lookup"><span data-stu-id="f02be-142">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="f02be-143">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="f02be-143">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="f02be-144">Google Chrome™ 17.0.963.56m pour Windows</span><span class="sxs-lookup"><span data-stu-id="f02be-144">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="f02be-145">Apple Safari® 5.1.2 pour Windows</span><span class="sxs-lookup"><span data-stu-id="f02be-145">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="f02be-146">Apple Safari 5.1.2 pour Mac OS®</span><span class="sxs-lookup"><span data-stu-id="f02be-146">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="f02be-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Navigateurs ou appareils mobiles testés de façon minimale</span></a></span><span class="sxs-lookup"><span data-stu-id="f02be-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="f02be-148">Windows Phone 7 et 7.5</span><span class="sxs-lookup"><span data-stu-id="f02be-148">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="f02be-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="f02be-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="f02be-150">Apple Safari pour système d’exploitation iPhone 5.0.1</span><span class="sxs-lookup"><span data-stu-id="f02be-150">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="f02be-151">Apple Safari pour système d’exploitation iPad 2 5.0.1</span><span class="sxs-lookup"><span data-stu-id="f02be-151">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="f02be-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configuration requise des navigateurs</span></a></span><span class="sxs-lookup"><span data-stu-id="f02be-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f02be-153">Pour utiliser la console web Accès Web Windows PowerShell, les navigateurs doivent :</span><span class="sxs-lookup"><span data-stu-id="f02be-153">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="f02be-154">autoriser les cookies à partir du site web de la passerelle Accès Web Windows PowerShell ;</span><span class="sxs-lookup"><span data-stu-id="f02be-154">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="f02be-155">être en mesure d’ouvrir et de lire des pages HTTPS ;</span><span class="sxs-lookup"><span data-stu-id="f02be-155">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="f02be-156">ouvrir et exécuter des sites Web qui utilisent JavaScript.</span><span class="sxs-lookup"><span data-stu-id="f02be-156">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_recm"></a>

<span data-ttu-id="f02be-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Déploiement (rapide) recommandé</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f02be-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f02be-158">Vous pouvez installer la passerelle Accès Web Windows PowerShell sur un serveur qui exécute Windows Server 2012 R2 ou Windows Server 2012 en utilisant des applets de commande Windows PowerShell, ou l’Assistant Ajout de rôles et de fonctionnalités qui s’ouvre à partir du Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="f02be-158">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either Windows PowerShell cmdlets, or by using the Add Roles and Features Wizard that is opened from within Server Manager.</span></span> <span data-ttu-id="f02be-159">Pour une installation et une configuration rapides, utilisez les applets de commande Windows PowerShell, comme décrit dans cette section.</span><span class="sxs-lookup"><span data-stu-id="f02be-159">For quick installation and configuration, use Windows PowerShell cmdlets, as described in this section.</span></span>

-   [<span data-ttu-id="f02be-160">Étape 1 : installer Accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f02be-160">Step 1: Install Windows PowerShell Web Access</span></span>](#BKMK_step1)

-   [<span data-ttu-id="f02be-161">Étape 2 : configurer la passerelle</span><span class="sxs-lookup"><span data-stu-id="f02be-161">Step 2: Configure the gateway</span></span>](#BKMK_step2)

-   [<span data-ttu-id="f02be-162">Étape 3 : configurer une règle d’autorisation restrictive</span><span class="sxs-lookup"><span data-stu-id="f02be-162">Step 3: Configure a restrictive authorization rule</span></span>](#BKMK_step3)

<a href="" id="BKMK_step1"></a>
###

<span data-ttu-id="f02be-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 1 : installer Accès Web Windows PowerShell</span></a></span><span class="sxs-lookup"><span data-stu-id="f02be-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="f02be-164">Pour installer Accès Web Windows PowerShell à l’aide des applets de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f02be-164">To install Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="f02be-165">Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell avec des droits utilisateur élevés.</span><span class="sxs-lookup"><span data-stu-id="f02be-165">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="f02be-166">Sur le Bureau Windows, cliquez avec le bouton droit dans la barre des tâches sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="f02be-166">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="f02be-167">Dans l’écran d’**accueil** de Windows, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="f02be-167">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f02be-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Remarque </span></span><span class="sxs-lookup"><span data-stu-id="f02be-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f02be-169">Dans Windows PowerShell 3.0 et 4.0, il n’est pas nécessaire d’importer le module d’applet de commande du Gestionnaire de serveur dans la session Windows PowerShell avant d’exécuter des applets de commande qui font partie du module.</span><span class="sxs-lookup"><span data-stu-id="f02be-169">In Windows PowerShell 3.0 and 4.0, there is no need to import the Server Manager cmdlet module into the Windows PowerShell session before running cmdlets that are part of the module.</span></span> <span data-ttu-id="f02be-170">Un module est automatiquement importé la première fois que vous exécutez une applet de commande qui fait partie du module.</span><span class="sxs-lookup"><span data-stu-id="f02be-170">A module is automatically imported the first time you run a cmdlet that is part of the module.</span></span> <span data-ttu-id="f02be-171">En outre, les applets de commande Windows PowerShell ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="f02be-171">Also, Windows PowerShell cmdlets are not case-sensitive.</span></span></p></td>
    </tr>
    </tbody>
    </table>

2.  <span data-ttu-id="f02be-172">Tapez ce qui suit, puis appuyez sur **Entrée**, où *computer_name* représente le nom de l’ordinateur distant sur lequel vous souhaitez installer Accès Web Windows PowerShell, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="f02be-172">Type the following, and then press **Enter**, where *computer_name* represents a remote computer on which you want to install Windows PowerShell Web Access, if applicable.</span></span> <span data-ttu-id="f02be-173">Le paramètre <span class="code">Restart</span> redémarre automatiquement les serveurs de destination, si besoin.</span><span class="sxs-lookup"><span data-stu-id="f02be-173">The <span class="code">Restart</span> parameter automatically restarts destination servers if required.</span></span>

    [<span data-ttu-id="f02be-174">Copier</span><span class="sxs-lookup"><span data-stu-id="f02be-174">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_374a9c21-4f6e-471e-b957-bb190a594533'); "Copier dans le Presse-papiers.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f02be-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Remarque </span></span><span class="sxs-lookup"><span data-stu-id="f02be-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f02be-176">Installer Accès Web Windows PowerShell à l’aide d’applets de commande Windows PowerShell n’ajoute pas les outils de gestion de serveur web (IIS) par défaut.</span><span class="sxs-lookup"><span data-stu-id="f02be-176">Installing Windows PowerShell Web Access by using Windows PowerShell cmdlets does not add Web Server (IIS) management tools by default.</span></span> <span data-ttu-id="f02be-177">Si vous voulez installer les outils de gestion sur le même serveur que la passerelle Accès Web Windows PowerShell, ajoutez le paramètre <span class="code">IncludeManagementTools</span> à la commande d’installation (comme indiqué dans cette étape).</span><span class="sxs-lookup"><span data-stu-id="f02be-177">If you want to install the management tools on the same server as the Windows PowerShell Web Access gateway, add the <span class="code">IncludeManagementTools</span> parameter to the installation command (as provided in this step).</span></span> <span data-ttu-id="f02be-178">Si vous gérez le site web Accès Web Windows PowerShell à partir d’un ordinateur distant, installez le composant logiciel enfichable Gestionnaire des services Internet en installant les <a href="http://go.microsoft.com/fwlink/?LinkID=304145">outils d’administration de serveur distant pour Windows 8.1</a> ou les <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">outils d’administration pour serveur distant pour Windows 8</a> sur l’ordinateur à partir duquel vous voulez gérer la passerelle.</span><span class="sxs-lookup"><span data-stu-id="f02be-178">If you are managing the Windows PowerShell Web Access website from a remote computer, install the IIS Manager snap-in by installing <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Remote Server Administration Tools for Windows 8.1</a> or <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Remote Server Administration Tools for Windows 8</a> on the computer from which you want to manage the gateway.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="f02be-179">Pour installer des rôles et fonctionnalités sur un disque dur virtuel hors connexion, vous devez ajouter les paramètres <span class="code">ComputerName</span> et <span class="code">VHD</span>.</span><span class="sxs-lookup"><span data-stu-id="f02be-179">To install roles and features on an offline VHD, you must add both the <span class="code">ComputerName</span> parameter and the <span class="code">VHD</span> parameter.</span></span> <span data-ttu-id="f02be-180">Le paramètre <span class="code">ComputerName</span> contient le nom du serveur sur lequel monter le disque dur virtuel, tandis que le paramètre <span class="code">VHD</span> contient le chemin du fichier VHD sur le serveur spécifié.</span><span class="sxs-lookup"><span data-stu-id="f02be-180">The <span class="code">ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="f02be-181">Copier</span><span class="sxs-lookup"><span data-stu-id="f02be-181">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_d841d509-347e-49d0-bf54-8d1f306bece6'); "Copier dans le Presse-papiers.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart

3.  <span data-ttu-id="f02be-182">Quand l’installation est terminée, vérifiez qu’Accès Web Windows PowerShell a été installé sur les serveurs de destination en exécutant l’applet de commande **Get-WindowsFeature** sur un serveur de destination, dans une console Windows PowerShell ouverte avec des droits d’utilisateur élevés.</span><span class="sxs-lookup"><span data-stu-id="f02be-182">When installation is complete, verify that Windows PowerShell Web Access was installed on destination servers by running the **Get-WindowsFeature** cmdlet on a destination server, in a Windows PowerShell console that has been opened with elevated user rights.</span></span> <span data-ttu-id="f02be-183">Vous pouvez également vérifier qu’Accès Web Windows PowerShell a été installé dans la console Gestionnaire de serveur en sélectionnant un serveur de destination dans la page **Tous les serveurs**, puis en affichant la vignette **Rôles et fonctionnalités** du serveur sélectionné.</span><span class="sxs-lookup"><span data-stu-id="f02be-183">You can also verify that Windows PowerShell Web Access was installed in the Server Manager console, by selecting a destination server on the **All Servers** page, and then viewing the **Roles and Features** tile for the selected server.</span></span> <span data-ttu-id="f02be-184">Vous pouvez aussi afficher le fichier Lisez-moi associé à Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-184">You can also view the readme file for Windows PowerShell Web Access.</span></span>

4.  <span data-ttu-id="f02be-185">Une fois cette fonctionnalité installée, vous êtes invité à consulter le fichier Lisez-moi dans lequel se trouvent des instructions d’installation requises simples pour la passerelle.</span><span class="sxs-lookup"><span data-stu-id="f02be-185">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="f02be-186">Ces instructions d’installation sont également fournies dans la section suivante, [Étape 2 : Configurer la passerelle](#BKMK_step2).</span><span class="sxs-lookup"><span data-stu-id="f02be-186">These setup instructions are also in the following section, [Step 2: Configure the gateway](#BKMK_step2).</span></span> <span data-ttu-id="f02be-187">Le chemin du fichier Lisez-moi est <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span><span class="sxs-lookup"><span data-stu-id="f02be-187">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

<a href="" id="BKMK_step2"></a>
###

<span data-ttu-id="f02be-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 2 : configurer la passerelle</span></a></span><span class="sxs-lookup"><span data-stu-id="f02be-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f02be-189">L’applet de commande **Install-PswaWebApplication** constitue un moyen rapide de configurer l’Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-189">The **Install-PswaWebApplication** cmdlet is a quick way to get Windows PowerShell Web Access configured.</span></span> <span data-ttu-id="f02be-190">Bien que vous puissiez ajouter le paramètre <span class="code">UseTestCertificate</span> à l’applet de commande <span class="code">Install-PswaWebApplication</span> pour installer un certificat SSL auto-signé à des fins de test, cette pratique n’est pas sécurisée ; pour un environnement de production sécurisé, utilisez toujours un certificat SSL valide qui a été signé par une autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="f02be-190">Although you can add the <span class="code">UseTestCertificate</span> parameter to the <span class="code">Install-PswaWebApplication</span> cmdlet to install a self-signed SSL certificate for test purposes, this is not secure; for a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="f02be-191">Les administrateurs peuvent remplacer le certificat de test par le certificat signé de leur choix à l’aide de la console du Gestionnaire des services Internet.</span><span class="sxs-lookup"><span data-stu-id="f02be-191">Administrators can replace the test certificate with a signed certificate of their choice by using the IIS Manager console.</span></span>

<span data-ttu-id="f02be-192">Vous pouvez terminer la configuration de l’application web d’Accès Web Windows PowerShell en exécutant l’applet de commande <span class="code">Install-PswaWebApplication</span> ou les étapes de configuration basées sur l’interface graphique utilisateur dans le Gestionnaire des services Internet.</span><span class="sxs-lookup"><span data-stu-id="f02be-192">You can complete Windows PowerShell Web Access web application configuration either by running the <span class="code">Install-PswaWebApplication</span> cmdlet or by performing GUI-based configuration steps in IIS Manager.</span></span> <span data-ttu-id="f02be-193">Par défaut, l’applet de commande installe l’application web, **pswa** (et son pool d’applications, **pswa_pool**), dans le conteneur **Site Web par défaut**, comme indiqué dans le Gestionnaire des services Internet ; si vous le voulez, vous pouvez obliger l’applet de commande à modifier le conteneur de site par défaut de l’application web.</span><span class="sxs-lookup"><span data-stu-id="f02be-193">By default, the cmdlet installs the web application, **pswa** (and an application pool for it, **pswa_pool**), in the **Default Web Site** container, as shown in IIS Manager; if desired, you can instruct the cmdlet to change the default site container of the web application.</span></span> <span data-ttu-id="f02be-194">Le Gestionnaire des services Internet propose des options de configuration pour les applications Web, telles que la modification du numéro de port ou du certificat SSL (Secure Sockets Layer).</span><span class="sxs-lookup"><span data-stu-id="f02be-194">IIS Manager offers configuration options that are available for web applications, such as changing the port number or the Secure Sockets Layer (SSL) certificate.</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="f02be-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Remarque sur la sécurité </span></span><span class="sxs-lookup"><span data-stu-id="f02be-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f02be-196">Nous conseillons vivement aux administrateurs de configurer la passerelle de façon à utiliser un certificat valide signé par une autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="f02be-196">We strongly recommend that administrators configure the gateway to use a valid certificate that has been signed by a CA.</span></span></p></td>
</tr>
</tbody>
</table>

-   [<span data-ttu-id="f02be-197">Pour configurer la passerelle Accès Web Windows PowerShell avec un certificat de test à l’aide d’Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="f02be-197">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>](#BKMK_testcert)

-   [<span data-ttu-id="f02be-198">Pour configurer la passerelle Windows PowerShell Web Access avec un certificat authentique à l’aide de Install-PswaWebApplication et IIS Manager</span><span class="sxs-lookup"><span data-stu-id="f02be-198">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>](#BKMK_gencert)

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a><span data-ttu-id="f02be-199">Pour configurer la passerelle Accès Web Windows PowerShell avec un certificat de test à l’aide de Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="f02be-199">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>

1.  <span data-ttu-id="f02be-200">Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-200">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="f02be-201">Sur le Bureau Windows, cliquez avec le bouton droit sur **Windows PowerShell** dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="f02be-201">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="f02be-202">Dans l’écran d’**accueil** de Windows, cliquez sur **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f02be-202">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="f02be-203">Tapez ce qui suit, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="f02be-203">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="f02be-204">**Install-PswaWebApplication -UseTestCertificate**</span><span class="sxs-lookup"><span data-stu-id="f02be-204">**Install-PswaWebApplication -UseTestCertificate**</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f02be-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Remarque sur la sécurité </span></span><span class="sxs-lookup"><span data-stu-id="f02be-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f02be-206">Le paramètre <span class="code">UseTestCertificate</span> doit uniquement être utilisé dans un environnement de test privé.</span><span class="sxs-lookup"><span data-stu-id="f02be-206">The <span class="code">UseTestCertificate</span> parameter should only be used in a private test environment.</span></span> <span data-ttu-id="f02be-207">Pour un environnement de production sécurisé, nous vous recommandons d’utiliser un certificat valide signé par une autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="f02be-207">For a secure production environment, we recommend using a valid certificate that has been signed by a CA.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="f02be-208">L’exécution de l’applet de commande permet d’installer l’application web Accès Web Windows PowerShell au sein du conteneur de site web IIS par défaut.</span><span class="sxs-lookup"><span data-stu-id="f02be-208">Running the cmdlet installs the Windows PowerShell Web Access web application within the IIS Default Web Site container.</span></span> <span data-ttu-id="f02be-209">L’applet de commande crée l’infrastructure requise pour exécuter Accès Web Windows PowerShell sur le site web par défaut, https://&lt;server_name&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="f02be-209">The cmdlet creates the infrastructure required to run Windows PowerShell Web Access on the default website, https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="f02be-210">Pour installer l’application web dans un autre site web, indiquez son nom en ajoutant le paramètre <span class="code">WebSiteName</span>.</span><span class="sxs-lookup"><span data-stu-id="f02be-210">To install the web application in a different website, provide the website name by adding the <span class="code">WebSiteName</span> parameter.</span></span> <span data-ttu-id="f02be-211">Pour modifier le nom de l’application web (par défaut, il s’agit de <span class="code">pswa</span>), ajoutez le paramètre <span class="code">WebApplicationName</span>.</span><span class="sxs-lookup"><span data-stu-id="f02be-211">To change the name of the web application (the default is <span class="code">pswa</span>), add the <span class="code">WebApplicationName</span> parameter.</span></span>

    <span data-ttu-id="f02be-212">Les paramètres suivants peuvent être configurés en exécutant l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f02be-212">The following settings are configured by running the cmdlet.</span></span> <span data-ttu-id="f02be-213">Vous pouvez les modifier manuellement dans la console du Gestionnaire des services Internet, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="f02be-213">You can change these manually in the IIS Manager console, if desired.</span></span>

    -   <span data-ttu-id="f02be-214">Path: /pswa</span><span class="sxs-lookup"><span data-stu-id="f02be-214">Path: /pswa</span></span>

    -   <span data-ttu-id="f02be-215">ApplicationPool : pswa_pool</span><span class="sxs-lookup"><span data-stu-id="f02be-215">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="f02be-216">EnabledProtocols: http</span><span class="sxs-lookup"><span data-stu-id="f02be-216">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="f02be-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="f02be-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

    <span data-ttu-id="f02be-218"><span class="label">Exemple :</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span><span class="sxs-lookup"><span data-stu-id="f02be-218"><span class="label">Example:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span></span>

    <span data-ttu-id="f02be-219">Dans cet exemple, le site web obtenu pour Accès Web Windows PowerShell est https://&lt; *server_name*&gt;/myWebApp.</span><span class="sxs-lookup"><span data-stu-id="f02be-219">In this example, the resulting website for Windows PowerShell Web Access is https://&lt; *server_name*&gt;/myWebApp.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f02be-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Remarque </span></span><span class="sxs-lookup"><span data-stu-id="f02be-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f02be-221">Vous ne pouvez pas vous connecter tant que les utilisateurs ne se voient pas accorder l’accès au site Web en ajoutant des règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f02be-221">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="f02be-222">Pour plus d’informations, consultez <a href="#BKMK_step3">Étape 3 : Configurer une règle d’autorisation restrictive</a> et <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell</a>.</span><span class="sxs-lookup"><span data-stu-id="f02be-222">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a><span data-ttu-id="f02be-223">Pour configurer la passerelle Windows PowerShell Web Access avec un certificat authentique à l’aide de Install-PswaWebApplication et IIS Manager</span><span class="sxs-lookup"><span data-stu-id="f02be-223">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>

1.  <span data-ttu-id="f02be-224">Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-224">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="f02be-225">Sur le Bureau Windows, cliquez avec le bouton droit sur **Windows PowerShell** dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="f02be-225">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="f02be-226">Dans l’écran d’**accueil** de Windows, cliquez sur **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f02be-226">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="f02be-227">Tapez ce qui suit, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="f02be-227">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="f02be-228">**Install-PswaWebApplication**</span><span class="sxs-lookup"><span data-stu-id="f02be-228">**Install-PswaWebApplication**</span></span>

    <span data-ttu-id="f02be-229">Les paramètres de passerelle suivants peuvent être configurés en exécutant l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f02be-229">The following gateway settings are configured by running the cmdlet.</span></span> <span data-ttu-id="f02be-230">Vous pouvez les modifier manuellement dans la console du Gestionnaire des services Internet, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="f02be-230">You can change these manually in the IIS Manager console, if desired.</span></span> <span data-ttu-id="f02be-231">Vous pouvez également spécifier des valeurs pour les paramètres <span class="code">WebsiteName</span> et <span class="code">WebApplicationName</span> de l’applet de commande <span class="code">Install-PswaWebApplication</span>.</span><span class="sxs-lookup"><span data-stu-id="f02be-231">You can also specify values for the <span class="code">WebsiteName</span> and <span class="code">WebApplicationName</span> parameters of the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span>

    -   <span data-ttu-id="f02be-232">Path: /pswa</span><span class="sxs-lookup"><span data-stu-id="f02be-232">Path: /pswa</span></span>

    -   <span data-ttu-id="f02be-233">ApplicationPool : pswa_pool</span><span class="sxs-lookup"><span data-stu-id="f02be-233">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="f02be-234">EnabledProtocols: http</span><span class="sxs-lookup"><span data-stu-id="f02be-234">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="f02be-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="f02be-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

3.  <span data-ttu-id="f02be-236">Ouvrez la console du Gestionnaire des services Internet en procédant de l’une des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="f02be-236">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="f02be-237">Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows.</span><span class="sxs-lookup"><span data-stu-id="f02be-237">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="f02be-238">Dans le menu **Outils** du Gestionnaire de serveur, cliquez sur **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="f02be-238">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="f02be-239">Dans l’écran d’**accueil** de Windows, cliquez sur **Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="f02be-239">On the Windows **Start** screen, click **Server Manager**.</span></span>

4.  <span data-ttu-id="f02be-240">Dans le volet de l’arborescence du Gestionnaire des services Internet, développez le nœud du serveur sur lequel Accès Web Windows PowerShell est installé jusqu’à ce que le dossier **Sites** apparaisse.</span><span class="sxs-lookup"><span data-stu-id="f02be-240">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="f02be-241">Développez le dossier **Sites**.</span><span class="sxs-lookup"><span data-stu-id="f02be-241">Expand the **Sites** folder.</span></span>

5.  <span data-ttu-id="f02be-242">Sélectionnez le site web dans lequel vous avez installé l’application web d’Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-242">Select the website in which you have installed the Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="f02be-243">Dans le volet **Actions**, cliquez sur **Liaisons**.</span><span class="sxs-lookup"><span data-stu-id="f02be-243">In the **Actions** pane, click **Bindings**.</span></span>

6.  <span data-ttu-id="f02be-244">Dans la boîte de dialogue **Liaisons de site**, cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="f02be-244">In the **Site Binding** dialog box, click **Add**.</span></span>

7.  <span data-ttu-id="f02be-245">Dans la boîte de dialogue **Ajouter la liaison de site**, dans le champ **Type**, sélectionnez **https**.</span><span class="sxs-lookup"><span data-stu-id="f02be-245">In the **Add Site Binding** dialog box, in the **Type** field, select **https**.</span></span>

8.  <span data-ttu-id="f02be-246">Dans le champ **Certificat SSL**, sélectionnez votre certificat signé dans le menu déroulant.</span><span class="sxs-lookup"><span data-stu-id="f02be-246">In the **SSL certificate** field, select your signed certificate from the drop-down menu.</span></span> <span data-ttu-id="f02be-247">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f02be-247">Click **OK**.</span></span> <span data-ttu-id="f02be-248">Pour plus d’informations sur l’obtention d’un certificat, consultez [Pour configurer un certificat SSL dans le Gestionnaire des services Internet](#BKMK_cert) dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f02be-248">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

    <span data-ttu-id="f02be-249">L’application web d’Accès Web Windows PowerShell est à présent configurée pour utiliser votre certificat SSL signé.</span><span class="sxs-lookup"><span data-stu-id="f02be-249">The Windows PowerShell Web Access web application is now configured to use your signed SSL certificate.</span></span> <span data-ttu-id="f02be-250">Vous pouvez accéder à Accès Web Windows PowerShell en ouvrant https://&lt;server_name&gt;/pswa dans une fenêtre de navigateur.</span><span class="sxs-lookup"><span data-stu-id="f02be-250">You can access Windows PowerShell Web Access by opening https://&lt;server_name&gt;/pswa in a browser window.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f02be-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Remarque </span></span><span class="sxs-lookup"><span data-stu-id="f02be-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f02be-252">Vous ne pouvez pas vous connecter tant que les utilisateurs ne se voient pas accorder l’accès au site Web en ajoutant des règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f02be-252">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="f02be-253">Pour plus d’informations, consultez <a href="#BKMK_step3">Étape 3 : Configurer une règle d’autorisation restrictive</a> et <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell</a>.</span><span class="sxs-lookup"><span data-stu-id="f02be-253">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table><span data-ttu-id="f02be-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 3 : configurer une règle d’autorisation restrictive</span></a></span><span class="sxs-lookup"><span data-stu-id="f02be-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f02be-255">Une fois Accès Web Windows PowerShell installé et la passerelle configurée, les utilisateurs peuvent ouvrir la page de connexion dans un navigateur, mais ils ne peuvent pas se connecter tant que l’administrateur d’Accès Web Windows PowerShell ne leur a pas octroyé explicitement un accès.</span><span class="sxs-lookup"><span data-stu-id="f02be-255">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="f02be-256">Le contrôle d’accès d’Accès Web Windows PowerShell est géré à l’aide de l’ensemble d’applets de commande Windows PowerShell décrit dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f02be-256">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="f02be-257">Il n’existe aucune interface utilisateur graphique équivalente pour ajouter ou gérer les règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f02be-257">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="f02be-258">Pour plus d’informations sur les applets de commande Accès Web Windows PowerShell, consultez les rubriques de référence des applets de commande, [Applets de commande Accès Web Windows PowerShell](https://technet.microsoft.com/library/hh918342.aspx).</span><span class="sxs-lookup"><span data-stu-id="f02be-258">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="f02be-259">Pour plus de détails sur les règles d’autorisation et la sécurité d’Accès Web Windows PowerShell, consultez [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="f02be-259">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="f02be-260">Pour ajouter une règle d’autorisation restrictive</span><span class="sxs-lookup"><span data-stu-id="f02be-260">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="f02be-261">Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell avec des droits utilisateur élevés.</span><span class="sxs-lookup"><span data-stu-id="f02be-261">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="f02be-262">Sur le Bureau Windows, cliquez avec le bouton droit dans la barre des tâches sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="f02be-262">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="f02be-263">Dans l’écran d’**accueil** de Windows, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="f02be-263">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="f02be-264"><span class="label">Étape facultative pour restreindre l’accès utilisateur à l’aide de configurations de sessions :</span> vérifiez que les configurations de sessions que vous voulez utiliser dans vos règles existent déjà.</span><span class="sxs-lookup"><span data-stu-id="f02be-264"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="f02be-265">Si elles n’ont pas encore été créées, utilisez les instructions relatives à la création de configurations de sessions dans [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="f02be-265">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="f02be-266">Tapez ce qui suit, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="f02be-266">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="f02be-267">Copier</span><span class="sxs-lookup"><span data-stu-id="f02be-267">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_f9e7959b-75d0-4d63-8f8e-02334a8dd09d'); "Copier dans le Presse-papiers.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="f02be-268">Cette règle d’autorisation accorde à un utilisateur spécifique l’accès à un ordinateur sur le réseau auquel il a généralement accès, avec l’accès à une configuration de session spécifique ayant comme portée les besoins ordinaires de l’utilisateur en matière de script et d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f02be-268">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="f02be-269">Dans l’exemple suivant, un utilisateur nommé <span class="code">JSmith</span> dans le domaine <span class="code">Contoso</span> se voit accorder un accès pour gérer l’ordinateur <span class="code">Contoso_214</span> et utiliser une configuration de session nommée <span class="code">NewAdminsOnly</span>.</span><span class="sxs-lookup"><span data-stu-id="f02be-269">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="f02be-270">Copier</span><span class="sxs-lookup"><span data-stu-id="f02be-270">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ebd5bc5e-ec5d-4955-a86a-63843e480e37'); "Copier dans le Presse-papiers.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="f02be-271">Vérifiez que la règle a été créée en exécutant l’applet de commande **Get-PswaAuthorizationRule** ou **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;nom_ordinateur&gt;.</span><span class="sxs-lookup"><span data-stu-id="f02be-271">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="f02be-272">Par exemple, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span><span class="sxs-lookup"><span data-stu-id="f02be-272">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="f02be-273">Après avoir configuré une règle d’autorisation, les utilisateurs autorisés peuvent se connecter à la console web et commencer à utiliser Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-273">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_custom"></a>

<span data-ttu-id="f02be-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Déploiement personnalisé</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f02be-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f02be-275">Vous pouvez installer la passerelle Accès Web Windows PowerShell sur un serveur qui exécute Windows Server 2012 R2 ou Windows Server 2012 en utilisant l’Assistant Ajout de rôles et de fonctionnalités dans le Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="f02be-275">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using the Add Roles and Features Wizard in Server Manager.</span></span> <span data-ttu-id="f02be-276">Après avoir installé Accès Web Windows PowerShell, vous pouvez personnaliser la configuration de la passerelle dans le Gestionnaire des services Internet.</span><span class="sxs-lookup"><span data-stu-id="f02be-276">After Windows PowerShell Web Access is installed, you can customize the configuration of the gateway in IIS Manager.</span></span>

<a href="" id="BKMK_custom1"></a>
###

<span data-ttu-id="f02be-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 1 : installer Accès Web Windows PowerShell</span></a></span><span class="sxs-lookup"><span data-stu-id="f02be-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a><span data-ttu-id="f02be-278">Pour installer Accès Web Windows PowerShell à l’aide de l’Assistant Ajout de rôles et de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="f02be-278">To install Windows PowerShell Web Access by using the Add Roles and Features Wizard</span></span>

1.  <span data-ttu-id="f02be-279">Si le Gestionnaire de serveur est déjà ouvert, passez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="f02be-279">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="f02be-280">S’il n’est pas déjà ouvert, ouvrez-le en effectuant l’une des opérations suivantes.</span><span class="sxs-lookup"><span data-stu-id="f02be-280">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="f02be-281">Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows.</span><span class="sxs-lookup"><span data-stu-id="f02be-281">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="f02be-282">Dans l’écran d’**accueil** de Windows, cliquez sur **Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="f02be-282">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="f02be-283">Dans le menu **Gérer**, cliquez sur **Ajouter des rôles et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="f02be-283">On the **Manage** menu, click **Add Roles and Features**.</span></span>

3.  <span data-ttu-id="f02be-284">Dans la page **Sélectionner le type d’installation**, sélectionnez **Installation basée sur un rôle ou une fonctionnalité**.</span><span class="sxs-lookup"><span data-stu-id="f02be-284">On the **Select installation type** page, select **Role-based or feature-based installation**.</span></span> <span data-ttu-id="f02be-285">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="f02be-285">Click **Next**.</span></span>

4.  <span data-ttu-id="f02be-286">Dans la page **Sélectionner le serveur de destination**, sélectionnez un serveur dans le pool de serveurs ou sélectionnez un disque dur virtuel hors connexion.</span><span class="sxs-lookup"><span data-stu-id="f02be-286">On the **Select destination server** page, select a server from the server pool, or select an offline VHD.</span></span> <span data-ttu-id="f02be-287">Pour sélectionner un disque dur virtuel hors connexion en guise de serveur de destination, choisissez d’abord le serveur sur lequel monter le disque dur virtuel, puis sélectionnez le fichier VHD.</span><span class="sxs-lookup"><span data-stu-id="f02be-287">To select an offline VHD as your destination server, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="f02be-288">Pour plus d’informations sur l’ajout de serveurs à votre pool de serveurs, consultez l’Aide du Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="f02be-288">For information about how to add servers to your server pool, see the Server Manager Help.</span></span> <span data-ttu-id="f02be-289">Une fois que vous avez sélectionné le serveur de destination, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="f02be-289">After you have selected the destination server, click **Next**.</span></span>

5.  <span data-ttu-id="f02be-290">Dans la page **Sélectionner des fonctionnalités** de l’Assistant, développez **Windows PowerShell**, puis sélectionnez **Accès Web Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f02be-290">On the **Select features** page of the wizard, expand **Windows PowerShell**, and then select **Windows PowerShell Web Access**.</span></span>

6.  <span data-ttu-id="f02be-291">Notez que vous êtes invité à ajouter les fonctionnalités requises, telles que le .NET Framework 4.5 et les services de rôle du serveur Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="f02be-291">Note that you are prompted to add required features, such as .NET Framework 4.5, and role services of Web Server (IIS).</span></span> <span data-ttu-id="f02be-292">Ajoutez les fonctionnalités requises et continuez.</span><span class="sxs-lookup"><span data-stu-id="f02be-292">Add required features and continue.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f02be-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Remarque </span></span><span class="sxs-lookup"><span data-stu-id="f02be-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f02be-294">Installer Accès Web Windows PowerShell à l’aide de l’Assistant Ajout de rôles et de fonctionnalités installe également le serveur web (IIS), y compris le composant logiciel enfichable Gestionnaire des services Internet.</span><span class="sxs-lookup"><span data-stu-id="f02be-294">Installing Windows PowerShell Web Access by using the Add Roles and Features Wizard also installs Web Server (IIS), including the IIS Manager snap-in.</span></span> <span data-ttu-id="f02be-295">Le composant logiciel enfichable et d’autres outils de gestion des services Internet IIS sont installés par défaut si vous utilisez l’Assistant Ajout de rôles et de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="f02be-295">The snap-in and other IIS management tools are installed by default if you use Add Roles and Features Wizard.</span></span> <span data-ttu-id="f02be-296">Si vous installez Accès Web Windows PowerShell à l’aide d’applets de commande Windows PowerShell comme décrit dans la procédure suivante, les outils de gestion ne sont pas ajoutés par défaut.</span><span class="sxs-lookup"><span data-stu-id="f02be-296">If you install Windows PowerShell Web Access by using Windows PowerShell cmdlets as described in the following procedure, management tools are not added by default.</span></span></p></td>
    </tr>
    </tbody>
    </table>

7.  <span data-ttu-id="f02be-297">Dans la page **Confirmer les sélections d’installation**, si les fichiers de fonctionnalités d’Accès Web Windows PowerShell ne sont pas enregistrés sur le serveur de destination que vous avez sélectionné à l’étape 4, cliquez sur **Spécifier un autre chemin d’accès source**, puis indiquez le chemin des fichiers de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="f02be-297">On the **Confirm installation selections** page, if the feature files for Windows PowerShell Web Access are not stored on the destination server that you selected in step 4, click **Specify an alternate source path**, and provide the path to the feature files.</span></span> <span data-ttu-id="f02be-298">Sinon, cliquez sur **Installer**.</span><span class="sxs-lookup"><span data-stu-id="f02be-298">Otherwise, click **Install**.</span></span>

8.  <span data-ttu-id="f02be-299">Une fois que vous avez cliqué sur **Installer**, la page **Progression de l’installation** affiche la progression de l’installation, les résultats et des messages tels que des avertissements, échecs ou étapes de configuration de post-installation requises pour Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-299">After you click **Install**, the **Installation progress** page displays installation progress, results, and messages such as warnings, failures, or post-installation configuration steps that are required for Windows PowerShell Web Access.</span></span> <span data-ttu-id="f02be-300">Une fois cette fonctionnalité installée, vous êtes invité à consulter le fichier Lisez-moi dans lequel se trouvent des instructions d’installation requises simples pour la passerelle.</span><span class="sxs-lookup"><span data-stu-id="f02be-300">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="f02be-301">Ces instructions sont également incluses dans la présente rubrique.</span><span class="sxs-lookup"><span data-stu-id="f02be-301">These instructions are also included in this topic.</span></span> <span data-ttu-id="f02be-302">Le chemin du fichier Lisez-moi est <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span><span class="sxs-lookup"><span data-stu-id="f02be-302">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

###

<span data-ttu-id="f02be-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 2 : configurer la passerelle</span></a></span><span class="sxs-lookup"><span data-stu-id="f02be-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f02be-304">Les instructions données dans cette section concernent l’installation de l’application web d’Accès Web Windows PowerShell dans un sous-répertoire, et non dans le répertoire racine, de votre site web.</span><span class="sxs-lookup"><span data-stu-id="f02be-304">Instructions in this section are for installing the Windows PowerShell Web Access web application in a subdirectory—and not in the root directory—of your website.</span></span> <span data-ttu-id="f02be-305">Cette procédure est l’équivalent basé sur l’interface graphique utilisateur des actions effectuées par l’applet de commande <span class="code">Install-PswaWebApplication</span>.</span><span class="sxs-lookup"><span data-stu-id="f02be-305">This procedure is the GUI-based equivalent of the actions performed by the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span> <span data-ttu-id="f02be-306">Cette section inclut également des instructions sur la manière d’utiliser le Gestionnaire des services Internet pour configurer la passerelle Accès Web Windows PowerShell en tant que site web racine.</span><span class="sxs-lookup"><span data-stu-id="f02be-306">This section also includes instructions for how to use IIS Manager to configure the Windows PowerShell Web Access gateway as a root website.</span></span>

-   [<span data-ttu-id="f02be-307">Pour configurer la passerelle dans un site Web existant à l’aide du Gestionnaire des services Internet</span><span class="sxs-lookup"><span data-stu-id="f02be-307">To use IIS Manager to configure the gateway in an existing website</span></span>](#BKMK_configman)

-   [<span data-ttu-id="f02be-308">Pour configurer la passerelle comme site web racine avec un certificat de test à l’aide du Gestionnaire des services Internet</span><span class="sxs-lookup"><span data-stu-id="f02be-308">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>](#BKMK_configroot)

-   

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a><span data-ttu-id="f02be-309">Pour configurer la passerelle dans un site Web existant à l’aide du Gestionnaire des services Internet</span><span class="sxs-lookup"><span data-stu-id="f02be-309">To use IIS Manager to configure the gateway in an existing website</span></span>

1.  <span data-ttu-id="f02be-310">Ouvrez la console du Gestionnaire des services Internet en procédant de l’une des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="f02be-310">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="f02be-311">Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows.</span><span class="sxs-lookup"><span data-stu-id="f02be-311">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="f02be-312">Dans le menu **Outils** du Gestionnaire de serveur, cliquez sur **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="f02be-312">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="f02be-313">Sur l’écran d’**accueil** de Windows, tapez une partie du nom **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="f02be-313">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="f02be-314">Cliquez sur le raccourci quand il s’affiche dans les résultats **Applications**.</span><span class="sxs-lookup"><span data-stu-id="f02be-314">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="f02be-315">Créez un pool d’applications pour Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-315">Create a new application pool for Windows PowerShell Web Access.</span></span> <span data-ttu-id="f02be-316">Développez le nœud du serveur de passerelle dans l’arborescence du Gestionnaire des services Internet, sélectionnez **Pools d’applications**, puis cliquez sur **Ajouter un pool d’applications** dans le volet **Actions**.</span><span class="sxs-lookup"><span data-stu-id="f02be-316">Expand the node of the gateway server in the IIS Manager tree pane, select **Application Pools**, and click **Add Application Pool** in the **Actions** pane.</span></span>

3.  <span data-ttu-id="f02be-317">Ajoutez un nouveau pool d’applications portant le nom **pswa_pool** ou indiquez un autre nom.</span><span class="sxs-lookup"><span data-stu-id="f02be-317">Add a new application pool with the name **pswa_pool**, or provide another name.</span></span> <span data-ttu-id="f02be-318">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f02be-318">Click **OK**.</span></span>

4.  <span data-ttu-id="f02be-319">Dans le volet de l’arborescence du Gestionnaire des services Internet, développez le nœud du serveur sur lequel Accès Web Windows PowerShell est installé jusqu’à ce que le dossier **Sites** apparaisse.</span><span class="sxs-lookup"><span data-stu-id="f02be-319">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="f02be-320">Sélectionnez le dossier **Sites**.</span><span class="sxs-lookup"><span data-stu-id="f02be-320">Select the **Sites** folder.</span></span>

5.  <span data-ttu-id="f02be-321">Cliquez avec le bouton droit sur le site web (par exemple, **Site web par défaut**) auquel vous voulez ajouter le site web Accès Web Windows PowerShell, puis cliquez sur **Ajouter une application**.</span><span class="sxs-lookup"><span data-stu-id="f02be-321">Right-click the website (for example, **Default Web Site**) to which you would like to add the Windows PowerShell Web Access website, and then click **Add Application**.</span></span>

6.  <span data-ttu-id="f02be-322">Dans le champ **Alias**, tapez pswa ou indiquez un autre alias.</span><span class="sxs-lookup"><span data-stu-id="f02be-322">In the **Alias** field, type pswa, or provide another alias.</span></span> <span data-ttu-id="f02be-323">L’alias devient le nom du répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="f02be-323">The alias becomes the virtual directory name.</span></span> <span data-ttu-id="f02be-324">Par exemple, **pswa** dans l’URL suivante représente l’alias spécifié durant cette étape : https://&lt;server_name&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="f02be-324">For example, **pswa** in the following URL represents the alias specified in this step: https://&lt;server_name&gt;/pswa.</span></span>

7.  <span data-ttu-id="f02be-325">Dans le champ **Pool d’applications**, sélectionnez le pool d’applications que vous avez créé à l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="f02be-325">In the **Application pool** field, select the application pool that you created in step 3.</span></span>

8.  <span data-ttu-id="f02be-326">Dans le champ **Chemin d’accès physique**, naviguez jusqu’à l’emplacement de l’application.</span><span class="sxs-lookup"><span data-stu-id="f02be-326">In the **Physical path** field, browse for the location of the application.</span></span> <span data-ttu-id="f02be-327">Vous pouvez utiliser l’emplacement par défaut, %windir%/Web/PowerShellWebAccess/wwwroot.</span><span class="sxs-lookup"><span data-stu-id="f02be-327">You can use the default location, %windir%/Web/PowerShellWebAccess/wwwroot.</span></span> <span data-ttu-id="f02be-328">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f02be-328">Click **OK**.</span></span>

9.  <span data-ttu-id="f02be-329">Suivez les étapes de la procédure [Pour configurer un certificat SSL dans le Gestionnaire des services Internet](#BKMK_cert) dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f02be-329">Follow the steps in the procedure [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic.</span></span>

10. <span data-ttu-id="f02be-330"><span class="label">Étape de sécurité facultative :</span> Avec le site web sélectionné dans l’arborescence, double-cliquez sur **Paramètres SSL** dans le volet de contenu.</span><span class="sxs-lookup"><span data-stu-id="f02be-330"><span class="label">Optional security step:</span> With the website selected in the tree pane, double-click **SSL Settings** in the content pane.</span></span> <span data-ttu-id="f02be-331">Sélectionnez **Exiger SSL**, puis dans le volet **Actions**, cliquez sur **Appliquer**.</span><span class="sxs-lookup"><span data-stu-id="f02be-331">Select **Require SSL**, and then in the **Actions** pane, click **Apply**.</span></span> <span data-ttu-id="f02be-332">Dans le volet **Paramètres SSL**, vous pouvez éventuellement exiger que les utilisateurs qui se connectent au site web d’Accès Web Windows PowerShell possèdent des certificats clients.</span><span class="sxs-lookup"><span data-stu-id="f02be-332">Optionally, in the **SSL Settings** pane, you can require that users connecting to the Windows PowerShell Web Access website have client certificates.</span></span> <span data-ttu-id="f02be-333">Ceux-ci aident à vérifier l’identité d’un utilisateur de périphérique client.</span><span class="sxs-lookup"><span data-stu-id="f02be-333">Client certificates help to verify the identity of a client device user.</span></span> <span data-ttu-id="f02be-334">Pour plus d’informations sur la manière dont l’exigence de certificats clients permet de renforcer la sécurité d’Accès Web Windows PowerShell, consultez [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) dans ce guide.</span><span class="sxs-lookup"><span data-stu-id="f02be-334">For more information about how requiring client certificates can increase the security of Windows PowerShell Web Access, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) in this guide.</span></span>

11. <span data-ttu-id="f02be-335">Ouvrez une session de navigateur sur un périphérique client.</span><span class="sxs-lookup"><span data-stu-id="f02be-335">Open a browser session on a client device.</span></span> <span data-ttu-id="f02be-336">Pour plus d’informations sur les navigateurs et périphériques pris en charge, consultez [Prise en charge de navigateurs et de périphériques client](#BKMK_browser) dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f02be-336">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this topic.</span></span>

12. <span data-ttu-id="f02be-337">Ouvrez le nouveau site web Accès Web Windows PowerShell, https://&lt; *gateway_server_name*&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="f02be-337">Open the new Windows PowerShell Web Access website, https://&lt; *gateway_server_name*&gt;/pswa.</span></span>

    <span data-ttu-id="f02be-338">Le navigateur doit afficher la page de connexion de la console d’Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-338">The browser should display the Windows PowerShell Web Access console sign-in page.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f02be-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Remarque </span></span><span class="sxs-lookup"><span data-stu-id="f02be-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f02be-340">Vous ne pouvez pas vous connecter tant que les utilisateurs ne se voient pas accorder l’accès au site Web en ajoutant des règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f02be-340">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

13. <span data-ttu-id="f02be-341">Dans une session Windows PowerShell qui a été ouverte avec des droits d’utilisateur élevés (Exécuter en tant qu’administrateur), exécutez le script suivant dans lequel *application_pool_name* représente le nom du pool d’applications que vous avez créé à l’étape 3, afin de donner les droits d’accès au pool d’applications dans le fichier d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="f02be-341">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 3, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="f02be-342">Copier</span><span class="sxs-lookup"><span data-stu-id="f02be-342">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c1a80a93-8fcf-4beb-a025-5f81bfb8bdae'); "Copier dans le Presse-papiers.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="f02be-343">Pour afficher les droits d’accès existants sur le fichier d’autorisations, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f02be-343">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="f02be-344">Copier</span><span class="sxs-lookup"><span data-stu-id="f02be-344">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ac2179c2-9548-4a17-8663-267fdd105380'); "Copier dans le Presse-papiers.")

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a><span data-ttu-id="f02be-345">Pour configurer la passerelle comme site web racine avec un certificat de test à l’aide du Gestionnaire des services Internet</span><span class="sxs-lookup"><span data-stu-id="f02be-345">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>

1.  <span data-ttu-id="f02be-346">Ouvrez la console du Gestionnaire des services Internet en procédant de l’une des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="f02be-346">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="f02be-347">Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows.</span><span class="sxs-lookup"><span data-stu-id="f02be-347">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="f02be-348">Dans le menu **Outils** du Gestionnaire de serveur, cliquez sur **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="f02be-348">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="f02be-349">Sur l’écran d’**accueil** de Windows, tapez une partie du nom **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="f02be-349">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="f02be-350">Cliquez sur le raccourci quand il s’affiche dans les résultats **Applications**.</span><span class="sxs-lookup"><span data-stu-id="f02be-350">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="f02be-351">Dans le volet de l’arborescence du Gestionnaire des services Internet, développez le nœud du serveur sur lequel Accès Web Windows PowerShell est installé jusqu’à ce que le dossier **Sites** apparaisse.</span><span class="sxs-lookup"><span data-stu-id="f02be-351">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="f02be-352">Sélectionnez le dossier **Sites**.</span><span class="sxs-lookup"><span data-stu-id="f02be-352">Select the **Sites** folder.</span></span>

3.  <span data-ttu-id="f02be-353">Dans le volet **Actions**, cliquez sur **Ajouter un site Web**.</span><span class="sxs-lookup"><span data-stu-id="f02be-353">In the **Actions** pane, click **Add Website**.</span></span>

4.  <span data-ttu-id="f02be-354">Tapez le nom du site web, comme **Accès Web Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f02be-354">Type a name for the website, such as **Windows PowerShell Web Access**.</span></span>

5.  <span data-ttu-id="f02be-355">Un pool d’applications est créé automatiquement pour le nouveau site Web.</span><span class="sxs-lookup"><span data-stu-id="f02be-355">An application pool is automatically created for the new website.</span></span> <span data-ttu-id="f02be-356">Pour utiliser un autre pool d’applications, cliquez sur **Sélectionner** pour sélectionner un pool d’applications à associer au nouveau site web.</span><span class="sxs-lookup"><span data-stu-id="f02be-356">To use a different application pool, click **Select** to select an application pool to associate with the new website.</span></span> <span data-ttu-id="f02be-357">Sélectionnez l’autre pool d’applications dans la boîte de dialogue **Sélectionner un pool d’applications**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f02be-357">Select the alternate application pool in the **Select Application Pool** dialog box, and then click **OK**.</span></span>

6.  <span data-ttu-id="f02be-358">Dans la zone de texte **Chemin d’accès physique**, accédez à %*windir*%/Web/PowerShellWebAccess/wwwroot.</span><span class="sxs-lookup"><span data-stu-id="f02be-358">In the **Physical path** text box, navigate to %*windir*%/Web/PowerShellWebAccess/wwwroot.</span></span>

7.  <span data-ttu-id="f02be-359">Dans le champ **Type** de la zone **Liaison**, sélectionnez **https**.</span><span class="sxs-lookup"><span data-stu-id="f02be-359">In the **Type** field of the **Binding** area, select **https**.</span></span>

8.  <span data-ttu-id="f02be-360">Assignez au site Web un numéro de port qui n’est pas déjà utilisé par un autre site ou une autre application.</span><span class="sxs-lookup"><span data-stu-id="f02be-360">Assign a port number to the website that is not already in use by another site or application.</span></span> <span data-ttu-id="f02be-361">Pour localiser les ports ouverts, vous pouvez exécuter la commande **netstat** dans une fenêtre d’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="f02be-361">To locate open ports, you can run the **netstat** command in a Command Prompt window.</span></span> <span data-ttu-id="f02be-362">Le numéro de port par défaut est 443.</span><span class="sxs-lookup"><span data-stu-id="f02be-362">The default port number is 443.</span></span>

    <span data-ttu-id="f02be-363">Modifiez le port par défaut si un autre site Web utilise déjà le port 443 ou si vous avez d’autres raisons d’ordre sécuritaire.</span><span class="sxs-lookup"><span data-stu-id="f02be-363">Change the default port if another website is already using 443, or if you have other security reasons for changing the port number.</span></span> <span data-ttu-id="f02be-364">Si un autre site web qui s’exécute sur votre serveur de passerelle utilise votre port sélectionné, un avertissement s’affiche quand vous cliquez sur **OK** dans la boîte de dialogue **Ajouter un site Web**.</span><span class="sxs-lookup"><span data-stu-id="f02be-364">If another website that is running on your gateway server is using your selected port, a warning is displayed when you click **OK** in the **Add Website** dialog box.</span></span> <span data-ttu-id="f02be-365">Vous devez utiliser un port inutilisé pour exécuter Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-365">You must use an unused port to run Windows PowerShell Web Access.</span></span>

9.  <span data-ttu-id="f02be-366">Selon les besoins de votre organisation, spécifiez éventuellement un nom d’hôte qui a du sens pour votre organisation et ses utilisateurs, comme **www.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="f02be-366">Optionally, if needed for your organization, specify a host name that makes sense to your organization and users, such as **www.contoso.com**.</span></span> <span data-ttu-id="f02be-367">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f02be-367">Click **OK**.</span></span>

10. <span data-ttu-id="f02be-368">Pour un environnement de production plus sécurisé, nous vous recommandons vivement de fournir un certificat valide signé par une autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="f02be-368">For a more secure production environment, we strongly recommend providing a valid certificate that has been signed by a CA.</span></span> <span data-ttu-id="f02be-369">Vous devez fournir un certificat SSL, car les utilisateurs peuvent uniquement se connecter à Accès Web Windows PowerShell par le biais d’un site web HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f02be-369">You must provide an SSL certificate, because users can only connect to Windows PowerShell Web Access through an HTTPS website.</span></span> <span data-ttu-id="f02be-370">Pour plus d’informations sur l’obtention d’un certificat, consultez [Pour configurer un certificat SSL dans le Gestionnaire des services Internet](#BKMK_cert) dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f02be-370">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

11. <span data-ttu-id="f02be-371">Cliquez sur **OK** pour fermer la boîte de dialogue **Ajouter un site Web**.</span><span class="sxs-lookup"><span data-stu-id="f02be-371">Click **OK** to close the **Add Website** dialog box.</span></span>

12. <span data-ttu-id="f02be-372">Dans une session Windows PowerShell qui a été ouverte avec des droits d’utilisateur élevés (Exécuter en tant qu’administrateur), exécutez le script suivant dans lequel *application_pool_name* représente le nom du pool d’applications que vous avez créé à l’étape 4, afin de donner les droits d’accès au pool d’applications dans le fichier d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="f02be-372">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 4, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="f02be-373">Copier</span><span class="sxs-lookup"><span data-stu-id="f02be-373">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_35ae9944-ca44-4af7-9c96-616083b3e3db'); "Copier dans le Presse-papiers.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="f02be-374">Pour afficher les droits d’accès existants sur le fichier d’autorisations, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f02be-374">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="f02be-375">Copier</span><span class="sxs-lookup"><span data-stu-id="f02be-375">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0eb6d70a-2807-498b-b088-fa5233ed68d5'); "Copier dans le Presse-papiers.")

        c:\windows\system32\icacls.exe $authorizationFile

13. <span data-ttu-id="f02be-376">Avec le nouveau site web sélectionné dans le volet de l’arborescence du Gestionnaire des services Internet, cliquez sur **Démarrer** dans le volet **Actions** pour démarrer le site web.</span><span class="sxs-lookup"><span data-stu-id="f02be-376">With the new website selected in the IIS Manager tree pane, click **Start** in the **Actions** pane to start the website.</span></span>

14. <span data-ttu-id="f02be-377">Ouvrez une session de navigateur sur un périphérique client.</span><span class="sxs-lookup"><span data-stu-id="f02be-377">Open a browser session on a client device.</span></span> <span data-ttu-id="f02be-378">Pour plus d’informations sur les navigateurs et périphériques pris en charge, voir [Prise en charge de navigateurs et de périphériques client](#BKMK_browser) dans ce document.</span><span class="sxs-lookup"><span data-stu-id="f02be-378">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this document.</span></span>

15. <span data-ttu-id="f02be-379">Ouvrez le site web Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-379">Open the new Windows PowerShell Web Access website.</span></span>

    <span data-ttu-id="f02be-380">Étant donné que le site web racine pointe vers le dossier Accès Web Windows PowerShell, le navigateur doit afficher la page de connexion Accès Web Windows PowerShell quand vous ouvrez https://&lt;*gateway_server_name*&gt;.</span><span class="sxs-lookup"><span data-stu-id="f02be-380">Because the root website points to the Windows PowerShell Web Access folder, the browser should display the Windows PowerShell Web Access sign-in page when you open https://&lt; *gateway_server_name*&gt;.</span></span> <span data-ttu-id="f02be-381">Il n’est pas nécessaire d’ajouter **/pswa** à l’URL.</span><span class="sxs-lookup"><span data-stu-id="f02be-381">You should not need to add **/pswa** to the URL.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="f02be-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Remarque </span></span><span class="sxs-lookup"><span data-stu-id="f02be-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="f02be-383">Vous ne pouvez pas vous connecter tant que les utilisateurs ne se voient pas accorder l’accès au site Web en ajoutant des règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f02be-383">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="f02be-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 3 : configurer une règle d’autorisation restrictive</span></a></span><span class="sxs-lookup"><span data-stu-id="f02be-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f02be-385">Une fois Accès Web Windows PowerShell installé et la passerelle configurée, les utilisateurs peuvent ouvrir la page de connexion dans un navigateur, mais ils ne peuvent pas se connecter tant que l’administrateur d’Accès Web Windows PowerShell ne leur a pas octroyé explicitement un accès.</span><span class="sxs-lookup"><span data-stu-id="f02be-385">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="f02be-386">Le contrôle d’accès d’Accès Web Windows PowerShell est géré à l’aide de l’ensemble d’applets de commande Windows PowerShell décrit dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f02be-386">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="f02be-387">Il n’existe aucune interface utilisateur graphique équivalente pour ajouter ou gérer les règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f02be-387">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="f02be-388">Pour plus d’informations sur les applets de commande Accès Web Windows PowerShell, consultez les rubriques de référence des applets de commande, [Applets de commande Accès Web Windows PowerShell](https://technet.microsoft.com/library/hh918342.aspx).</span><span class="sxs-lookup"><span data-stu-id="f02be-388">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="f02be-389">Pour plus de détails sur les règles d’autorisation et la sécurité d’Accès Web Windows PowerShell, consultez [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="f02be-389">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="f02be-390">Pour ajouter une règle d’autorisation restrictive</span><span class="sxs-lookup"><span data-stu-id="f02be-390">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="f02be-391">Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell avec des droits utilisateur élevés.</span><span class="sxs-lookup"><span data-stu-id="f02be-391">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="f02be-392">Sur le Bureau Windows, cliquez avec le bouton droit dans la barre des tâches sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="f02be-392">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="f02be-393">Dans l’écran d’**accueil** de Windows, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="f02be-393">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="f02be-394"><span class="label">Étape facultative pour restreindre l’accès utilisateur à l’aide de configurations de sessions :</span> vérifiez que les configurations de sessions que vous voulez utiliser dans vos règles existent déjà.</span><span class="sxs-lookup"><span data-stu-id="f02be-394"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="f02be-395">Si elles n’ont pas encore été créées, utilisez les instructions relatives à la création de configurations de sessions dans [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="f02be-395">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="f02be-396">Tapez ce qui suit, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="f02be-396">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="f02be-397">Copier</span><span class="sxs-lookup"><span data-stu-id="f02be-397">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4df22c91-f56f-4bb5-91e7-99f9b365ed5d'); "Copier dans le Presse-papiers.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="f02be-398">Cette règle d’autorisation accorde à un utilisateur spécifique l’accès à un ordinateur sur le réseau auquel il a généralement accès, avec l’accès à une configuration de session spécifique ayant comme portée les besoins ordinaires de l’utilisateur en matière de script et d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f02be-398">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="f02be-399">Dans l’exemple suivant, un utilisateur nommé <span class="code">JSmith</span> dans le domaine <span class="code">Contoso</span> se voit accorder un accès pour gérer l’ordinateur <span class="code">Contoso_214</span> et utiliser une configuration de session nommée <span class="code">NewAdminsOnly</span>.</span><span class="sxs-lookup"><span data-stu-id="f02be-399">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="f02be-400">Copier</span><span class="sxs-lookup"><span data-stu-id="f02be-400">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_efc3999a-2905-453f-86cd-014b41658ffc'); "Copier dans le Presse-papiers.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="f02be-401">Vérifiez que la règle a été créée en exécutant l’applet de commande **Get-PswaAuthorizationRule** ou **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;nom_ordinateur&gt;.</span><span class="sxs-lookup"><span data-stu-id="f02be-401">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="f02be-402">Par exemple, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span><span class="sxs-lookup"><span data-stu-id="f02be-402">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="f02be-403">Après avoir configuré une règle d’autorisation, les utilisateurs autorisés peuvent se connecter à la console web et commencer à utiliser Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-403">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_configcert"></a>

<span data-ttu-id="f02be-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configurer un certificat authentique</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f02be-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configure a genuine certificate</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f02be-405">Pour un environnement de production sécurisé, utilisez toujours un certificat SSL valide signé par une autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="f02be-405">For a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="f02be-406">La procédure décrite dans cette section détaille comment obtenir et appliquer un certificat SSL valide à partir d’une autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="f02be-406">The procedure in this section describes how to obtain and apply a valid SSL certificate from a CA.</span></span>

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a><span data-ttu-id="f02be-407">Pour configurer un certificat SSL dans le Gestionnaire des services Internet</span><span class="sxs-lookup"><span data-stu-id="f02be-407">To configure an SSL certificate in IIS Manager</span></span>

1.  <span data-ttu-id="f02be-408">Dans le volet de l’arborescence du Gestionnaire des services Internet, sélectionnez le serveur sur lequel Accès Web Windows PowerShell est installé.</span><span class="sxs-lookup"><span data-stu-id="f02be-408">In the IIS Manager tree pane, select the server on which Windows PowerShell Web Access is installed.</span></span>

2.  <span data-ttu-id="f02be-409">Dans le volet de contenu, double-cliquez sur **Certificats de serveur**.</span><span class="sxs-lookup"><span data-stu-id="f02be-409">In the content pane, double click **Server Certificates**.</span></span>

3.  <span data-ttu-id="f02be-410">Dans le volet **Actions**, effectuez l’une des opérations suivantes.</span><span class="sxs-lookup"><span data-stu-id="f02be-410">In the **Actions** pane, do one of the following.</span></span> <span data-ttu-id="f02be-411">Pour plus d’informations sur la configuration des certificats de serveur dans IIS, consultez [Configuration des certificats de serveur dans IIS 7](https://technet.microsoft.com/library/cc732230.aspx).</span><span class="sxs-lookup"><span data-stu-id="f02be-411">For more information about configuring server certificates in IIS, see [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).</span></span>

    -   <span data-ttu-id="f02be-412">Cliquez sur **Importer** pour importer un certificat existant valide depuis un emplacement sur votre réseau.</span><span class="sxs-lookup"><span data-stu-id="f02be-412">Click **Import** to import an existing, valid certificate from a location on your network.</span></span>

    -   <span data-ttu-id="f02be-413">Cliquez sur **Créer une demande de certificat** pour demander un certificat auprès d’une autorité de certification comme VeriSign™, Thawte ou GeoTrust®.</span><span class="sxs-lookup"><span data-stu-id="f02be-413">Click **Create Certificate Request** to request a certificate from a CA such as VeriSign™, Thawte, or GeoTrust®.</span></span> <span data-ttu-id="f02be-414">Le nom courant du certificat doit correspondre à l’en-tête d’hôte dans la demande.</span><span class="sxs-lookup"><span data-stu-id="f02be-414">The certificate's common name must match the host header in the request.</span></span> <span data-ttu-id="f02be-415">Par exemple, si le navigateur client demande http://www.contoso.com/, le nom courant doit également être http://www.contoso.com/.</span><span class="sxs-lookup"><span data-stu-id="f02be-415">For example, if the client browser requests http://www.contoso.com/, then the common name must also be http://www.contoso.com/.</span></span> <span data-ttu-id="f02be-416">Il s’agit de l’option recommandée la plus sécurisée pour fournir un certificat à la passerelle Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f02be-416">This is the most secure and recommended option for providing the Windows PowerShell Web Access gateway with a certificate.</span></span>

    -   <span data-ttu-id="f02be-417">Cliquez sur **Créer un certificat auto-signé** pour créer un certificat que vous pouvez utiliser immédiatement, puis faire signer ultérieurement par une autorité de certification si besoin.</span><span class="sxs-lookup"><span data-stu-id="f02be-417">Click **Create a Self-Signed Certificate** to create a certificate that you can use immediately, and have signed later by a CA if desired.</span></span> <span data-ttu-id="f02be-418">Spécifiez un nom convivial pour le certificat auto-signé, comme **Accès Web Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f02be-418">Specify a friendly name for the self-signed certificate, such as **Windows PowerShell Web Access**.</span></span> <span data-ttu-id="f02be-419">Cette option est considérée comme non sécurisée et recommandée uniquement dans un environnement de test privé.</span><span class="sxs-lookup"><span data-stu-id="f02be-419">This option is not considered secure, and is recommended only for a private test environment.</span></span>

4.  <span data-ttu-id="f02be-420">Après avoir créé ou obtenu un certificat, sélectionnez le site web auquel il est appliqué (par exemple, le **Site Web par défaut**) dans le volet de l’arborescence du Gestionnaire des services Internet, puis cliquez sur **Liaisons** dans le volet **Actions**.</span><span class="sxs-lookup"><span data-stu-id="f02be-420">After creating or obtaining a certificate, select the website to which the certificate is applied (for example, **Default Web Site**) in the IIS Manager tree pane, and then click **Bindings** in the **Actions** pane.</span></span>

5.  <span data-ttu-id="f02be-421">Dans la boîte de dialogue **Ajouter la liaison de site**, ajoutez une liaison **https** pour le site, si aucune n’est déjà affichée.</span><span class="sxs-lookup"><span data-stu-id="f02be-421">In the **Add Site Binding** dialog box, add an **https** binding for the site, if one is not already displayed.</span></span> <span data-ttu-id="f02be-422">Si vous n’utilisez pas de certificat auto-signé, spécifiez le nom d’hôte de l’étape 3 de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="f02be-422">If you are not using a self-signed certificate, specify the host name from step 3 of this procedure.</span></span> <span data-ttu-id="f02be-423">Si vous utilisez un certificat auto-signé, vous pouvez ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="f02be-423">If you are using a self-signed certificate, this step is not required.</span></span>

6.  <span data-ttu-id="f02be-424">Sélectionnez le certificat que vous avez obtenu ou créé à l’étape 3 de cette procédure, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f02be-424">Select the certificate that you obtained or created in step 3 of this procedure, and then click **OK**.</span></span>

<a href="" id="BKMK_using"></a>

<span data-ttu-id="f02be-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Utilisation de la console Web Windows PowerShell</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f02be-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Using the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f02be-426">Une fois qu’Accès Web Windows PowerShell est installé et la configuration de la passerelle terminée comme décrit dans cette rubrique, la console web Windows PowerShell est prête à être utilisée.</span><span class="sxs-lookup"><span data-stu-id="f02be-426">After Windows PowerShell Web Access is installed and the gateway configuration is finished as described in this topic, the Windows PowerShell web-based console is ready to use.</span></span> <span data-ttu-id="f02be-427">Pour plus d’informations sur la prise en main de la console web, consultez [Utiliser la console web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span><span class="sxs-lookup"><span data-stu-id="f02be-427">For more information about getting started in the web-based console, see [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span></span>

<span data-ttu-id="f02be-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Voir aussi</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f02be-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f02be-429">[Documentation d’Internet Information Services (IIS) 7.0](https://technet.microsoft.com/library/cc753433.aspx)
[Aide du Gestionnaire des services Internet 7.0](https://technet.microsoft.com/library/cc732664.aspx)
[Configurer la sécurité du serveur Web (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[Ressources de déploiement de la sécurité IPsec](https://technet.microsoft.com/network/bb531150)</span><span class="sxs-lookup"><span data-stu-id="f02be-429">[Internet Information Services (IIS) 7.0 Documentation](https://technet.microsoft.com/library/cc753433.aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)
[Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec Deployment Resources](https://technet.microsoft.com/network/bb531150)</span></span>

<span data-ttu-id="f02be-430"><span>Afficher :</span> Hérité Protégé</span><span class="sxs-lookup"><span data-stu-id="f02be-430"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="f02be-431"><span class="stdr-votetitle">Cette page vous a-t-elle été utile ?</span></span><span class="sxs-lookup"><span data-stu-id="f02be-431"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="f02be-432">Oui Non</span><span class="sxs-lookup"><span data-stu-id="f02be-432">Yes No</span></span>

<span data-ttu-id="f02be-433">Vous avez d’autres commentaires ?</span><span class="sxs-lookup"><span data-stu-id="f02be-433">Additional feedback?</span></span>

<span data-ttu-id="f02be-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caractères restants</span> Soumettre Ignorer</span><span class="sxs-lookup"><span data-stu-id="f02be-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="f02be-435"><span class="stdr-thankyou">Merci !</span></span><span class="sxs-lookup"><span data-stu-id="f02be-435"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="f02be-436"><span class="stdr-appreciate">Votre avis nous intéresse.</span></span><span class="sxs-lookup"><span data-stu-id="f02be-436"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="f02be-437">Gérer votre profil</span><span class="sxs-lookup"><span data-stu-id="f02be-437">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="f02be-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span>Commentaires sur le site</a> Commentaires sur le site</span><span class="sxs-lookup"><span data-stu-id="f02be-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="f02be-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="f02be-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="f02be-440">Faites-nous part de votre expérience...</span><span class="sxs-lookup"><span data-stu-id="f02be-440">Tell us about your experience...</span></span>

<span data-ttu-id="f02be-441">La page s’est elle chargée rapidement ?</span><span class="sxs-lookup"><span data-stu-id="f02be-441">Did the page load quickly?</span></span>

<span data-ttu-id="f02be-442"><span> Oui<span> </span></span> <span> Non<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="f02be-442"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="f02be-443">Êtes-vous satisfait de la conception de la page ?</span><span class="sxs-lookup"><span data-stu-id="f02be-443">Do you like the page design?</span></span>

<span data-ttu-id="f02be-444"><span> Oui<span> </span></span> <span> Non<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="f02be-444"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="f02be-445">Donnez-nous votre avis</span><span class="sxs-lookup"><span data-stu-id="f02be-445">Tell us more</span></span>

-   [<span data-ttu-id="f02be-446">Bulletin d’informations</span><span class="sxs-lookup"><span data-stu-id="f02be-446">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="f02be-447">Contactez-nous</span><span class="sxs-lookup"><span data-stu-id="f02be-447">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="f02be-448">Déclaration de confidentialité</span><span class="sxs-lookup"><span data-stu-id="f02be-448">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="f02be-449">Conditions d'utilisation</span><span class="sxs-lookup"><span data-stu-id="f02be-449">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="f02be-450">Marques</span><span class="sxs-lookup"><span data-stu-id="f02be-450">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="f02be-451">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="f02be-451">© 2016 Microsoft</span></span>

<span data-ttu-id="f02be-452">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="f02be-452">© 2016 Microsoft</span></span>

<span data-ttu-id="f02be-453">Les codes et les scripts développés par un tiers et en rapport à ce site doivent faire l’objet d’une licence fournie par le tiers, qui indique qu’il détient son code. Microsoft n’est pas partie prenante.</span><span class="sxs-lookup"><span data-stu-id="f02be-453">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="f02be-454">Consultez les conditions d’utilisation CDN Ajax ASP.NET (http://www.asp.net/ajaxlibrary/CDN.ashx).</span><span class="sxs-lookup"><span data-stu-id="f02be-454">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

