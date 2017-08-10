---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: utiliser la console web Windows PowerShell
ms.openlocfilehash: 48ed1646c00f909c4e950f197f51a30205060ef0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
#  <a name="use-the-web-based-windows-powershell-console"></a><span data-ttu-id="67a63-103">Utiliser la console web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="67a63-103">Use the Web-based Windows PowerShell Console</span></span>

<span data-ttu-id="67a63-104">Mise à jour : 24 juin 2013</span><span class="sxs-lookup"><span data-stu-id="67a63-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="67a63-105">S’applique à : Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="67a63-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="67a63-106">Accès Web Windows PowerShell® permet aux utilisateurs de Windows PowerShell® de se connecter à un site web sécurisé à l’aide du protocole SSL (Secure Sockets Layer) afin d’utiliser des sessions, des applets de commande et des scripts Windows PowerShell pour gérer un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="67a63-106">Windows PowerShell® Web Access lets Windows PowerShell® users sign in to a Secure Sockets Layer (SSL)-secured website to use Windows PowerShell sessions, cmdlets, and scripts to manage a remote computer.</span></span> <span data-ttu-id="67a63-107">La console Windows PowerShell s’exécutant dans un navigateur web, elle peut être ouverte à partir de différents périphériques clients tels que des téléphones portables, des tablettes, des bornes Internet publiques, des ordinateurs portables ou des ordinateurs partagés ou empruntés.</span><span class="sxs-lookup"><span data-stu-id="67a63-107">Because the Windows PowerShell console runs in a web browser, it can be opened from a variety of client devices, including cell phones, tablet computers, public computing kiosks, laptop computers, or shared or borrowed computers.</span></span> <span data-ttu-id="67a63-108">La console web Windows PowerShell a pour cible un ordinateur distant spécifié par les utilisateurs dans le cadre du processus de connexion.</span><span class="sxs-lookup"><span data-stu-id="67a63-108">The web-based Windows PowerShell console is targeted at a remote computer that is specified by users as part of the sign-in process.</span></span> <span data-ttu-id="67a63-109">Cette rubrique décrit comment se connecter et commencer à utiliser la console web Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67a63-109">This topic describes how to sign in to and start using the Windows PowerShell Web Access web-based console.</span></span>

<span data-ttu-id="67a63-110">Elle ne décrit pas comment utiliser Windows PowerShell ou exécuter des applets de commande ou des scripts.</span><span class="sxs-lookup"><span data-stu-id="67a63-110">This topic does not describe how to use Windows PowerShell or run cmdlets or scripts.</span></span> <span data-ttu-id="67a63-111">Pour plus d’informations sur la façon d’utiliser Windows PowerShell et pour accéder à des ressources de script, consultez la section Voir aussi à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="67a63-111">For information about how to use Windows PowerShell, and scripting resources, see the See Also section at the end of this topic.</span></span>

<span data-ttu-id="67a63-112">Dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="67a63-112">In this topic:</span></span>

-   [<span data-ttu-id="67a63-113">Navigateurs et périphériques clients pris en charge</span><span class="sxs-lookup"><span data-stu-id="67a63-113">Supported browsers and client devices</span></span>](#BKMK_browser)

-   [<span data-ttu-id="67a63-114">Connexion à l’accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="67a63-114">Signing in to Windows PowerShell Web Access</span></span>](#BKMK_sign)

-   [<span data-ttu-id="67a63-115">Déconnexion et dépassement de délais</span><span class="sxs-lookup"><span data-stu-id="67a63-115">Signing out and timing out</span></span>](#BKMK_timeout)

-   [<span data-ttu-id="67a63-116">Différences dans la console Windows PowerShell Web</span><span class="sxs-lookup"><span data-stu-id="67a63-116">Differences in the web-based Windows PowerShell console</span></span>](#BKMK_web)

<a href="" id="BKMK_browser"></a>
------------------------------------------------------------------------

<span data-ttu-id="67a63-117">Accès Web Windows PowerShell prend en charge les navigateurs suivants.</span><span class="sxs-lookup"><span data-stu-id="67a63-117">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="67a63-118">Bien que les navigateurs mobiles ne soient pas officiellement pris en charge, nombre d’entre eux sont susceptibles de pouvoir exécuter la console web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67a63-118">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="67a63-119">D’autres navigateurs acceptant les cookies, exécutant JavaScript et exécutant des sites Web HTTPS sont censés fonctionner, mais n’ont pas été testés officiellement.</span><span class="sxs-lookup"><span data-stu-id="67a63-119">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="67a63-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Navigateurs d’ordinateur de bureau pris en charge</span></a></span><span class="sxs-lookup"><span data-stu-id="67a63-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="67a63-121">Windows® Internet Explorer® pour Microsoft Windows® 8.0, 9.0, 10.0 et 11.0</span><span class="sxs-lookup"><span data-stu-id="67a63-121">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="67a63-122">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="67a63-122">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="67a63-123">Google Chrome™ 17.0.963.56m pour Windows</span><span class="sxs-lookup"><span data-stu-id="67a63-123">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="67a63-124">Apple Safari® 5.1.2 pour Windows</span><span class="sxs-lookup"><span data-stu-id="67a63-124">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="67a63-125">Apple Safari 5.1.2 pour Mac OS®</span><span class="sxs-lookup"><span data-stu-id="67a63-125">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="67a63-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Navigateurs ou appareils mobiles testés de façon minimale</span></a></span><span class="sxs-lookup"><span data-stu-id="67a63-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="67a63-127">Windows Phone 7 et 7.5</span><span class="sxs-lookup"><span data-stu-id="67a63-127">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="67a63-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="67a63-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="67a63-129">Apple Safari pour système d’exploitation iPhone 5.0.1</span><span class="sxs-lookup"><span data-stu-id="67a63-129">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="67a63-130">Apple Safari pour système d’exploitation iPad 2 5.0.1</span><span class="sxs-lookup"><span data-stu-id="67a63-130">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="67a63-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configuration requise des navigateurs</span></a></span><span class="sxs-lookup"><span data-stu-id="67a63-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="67a63-132">Pour utiliser la console web Accès Web Windows PowerShell, les navigateurs doivent :</span><span class="sxs-lookup"><span data-stu-id="67a63-132">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="67a63-133">autoriser les cookies à partir du site web de la passerelle Accès Web Windows PowerShell ;</span><span class="sxs-lookup"><span data-stu-id="67a63-133">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="67a63-134">être en mesure d’ouvrir et de lire des pages HTTPS ;</span><span class="sxs-lookup"><span data-stu-id="67a63-134">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="67a63-135">ouvrir et exécuter des sites Web qui utilisent JavaScript.</span><span class="sxs-lookup"><span data-stu-id="67a63-135">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_sign"></a>

<span data-ttu-id="67a63-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Connexion à l’accès Web Windows PowerShell</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="67a63-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing in to Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="67a63-137">Votre administrateur Accès Web Windows PowerShell doit vous fournir une URL qui est l’adresse du site web de la passerelle Accès Web Windows PowerShell de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="67a63-137">Your Windows PowerShell Web Access administrator should provide you with a URL that is the address of your organization’s Windows PowerShell Web Access gateway website.</span></span> <span data-ttu-id="67a63-138">Par défaut, l’adresse de ce site web est https://&lt;nom_serveur&gt;/pswa.</span><span class="sxs-lookup"><span data-stu-id="67a63-138">By default, this website address is https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="67a63-139">Avant de vous connecter à Accès Web Windows PowerShell, vérifiez que vous disposez du nom ou de l’adresse IP de l’ordinateur distant que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="67a63-139">Before you sign in to Windows PowerShell Web Access, be sure that you have the name or IP address of the remote computer that you want to manage.</span></span> <span data-ttu-id="67a63-140">Vous devez être un utilisateur autorisé sur l’ordinateur distant et celui-ci doit être configuré pour autoriser la gestion à distance.</span><span class="sxs-lookup"><span data-stu-id="67a63-140">You must be an authorized user on the remote computer, and it must be configured to allow remote management.</span></span> <span data-ttu-id="67a63-141">Pour plus d’informations sur la configuration de votre ordinateur pour autoriser la gestion à distance, consultez [Activer et utiliser des commandes distantes dans Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx).</span><span class="sxs-lookup"><span data-stu-id="67a63-141">For more information about configuring your computer to allow remote management, see [Enable and Use Remote Commands in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx).</span></span> <span data-ttu-id="67a63-142">Le moyen le plus simple de configurer votre ordinateur pour autoriser la gestion à distance consiste à exécuter l’applet de commande **Enable-PSRemoting -force** sur l’ordinateur, dans une session Windows PowerShell qui a été ouverte avec des droits d’utilisateur élevés (**Exécuter en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="67a63-142">The simplest method of configuring your computer to allow remote management is to run the **Enable-PSRemoting -force** cmdlet on the computer, in a Windows PowerShell session that has been opened with elevated user rights (**Run as Administrator**).</span></span>

### <a name="to-sign-in-to-windows-powershell-web-access"></a><span data-ttu-id="67a63-143">Pour se connecter à Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="67a63-143">To sign in to Windows PowerShell Web Access</span></span>

1.  <span data-ttu-id="67a63-144">Ouvrez le site web Accès Web Windows PowerShell dans une fenêtre ou un onglet de navigateur Internet.</span><span class="sxs-lookup"><span data-stu-id="67a63-144">Open the Windows PowerShell Web Access website in an Internet browser window or tab.</span></span>

2.  <span data-ttu-id="67a63-145">Dans la page de connexion à Accès Web Windows PowerShell, indiquez votre nom d’utilisateur réseau, votre mot de passe et le nom de l’ordinateur que vous souhaitez gérer (et sur lequel vous êtes un utilisateur autorisé).</span><span class="sxs-lookup"><span data-stu-id="67a63-145">On the Windows PowerShell Web Access sign-in page, provide your network user name, password, and the name of the computer that you want to manage (and on which you are an authorized user).</span></span> <span data-ttu-id="67a63-146">Si l’administrateur Accès Web Windows PowerShell vous a demandé d’utiliser un URI de site personnalisé ou de serveur proxy plutôt qu’un nom d’ordinateur, sélectionnez **URI de connexion** dans le champ **Type de connexion**, puis spécifiez l’URI.</span><span class="sxs-lookup"><span data-stu-id="67a63-146">If the Windows PowerShell Web Access administrator has instructed you to use a URI to a custom site or proxy server instead of a computer name, select **Connection URI** in the **Connection type** field, and then provide the URI.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="67a63-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Remarque </span></span><span class="sxs-lookup"><span data-stu-id="67a63-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><ul>
    <li><p><span data-ttu-id="67a63-148">Si l’ordinateur de destination est membre d’un groupe de travail, utilisez la syntaxe suivante pour fournir votre nom d’utilisateur et vous connecter à l’ordinateur : &lt;<em>nom_groupe_de_travail</em>&gt;\&lt;<em>nom_utilisateur</em>&gt;.</span><span class="sxs-lookup"><span data-stu-id="67a63-148">If the destination computer is in a workgroup, use the following syntax to provide your user name and sign in to the computer:&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    <li><p><span data-ttu-id="67a63-149">Si l’ordinateur de destination est le serveur passerelle, vous pouvez spécifier <strong>localhost</strong> dans le champ <strong>Nom de l’ordinateur</strong>.</span><span class="sxs-lookup"><span data-stu-id="67a63-149">If the destination computer is the gateway server, you can specify <strong>localhost</strong> in the <strong>Computer name</strong> field.</span></span></p></li>
    <li><p><span data-ttu-id="67a63-150">Si l’ordinateur de destination est le serveur passerelle et qu’il appartient à un groupe de travail, vous pouvez spécifier <strong>localhost</strong> dans le champ <strong>Nom de l’ordinateur</strong>, mais ne spécifiez pas localhost\&lt;<em>nom_utilisateur</em>&gt; dans le champ <strong>Nom d’utilisateur</strong>.</span><span class="sxs-lookup"><span data-stu-id="67a63-150">If the destination computer is the gateway server, and the gateway server is in a workgroup, you can use <strong>localhost</strong> in the <strong>Computer name</strong> field, but do not use localhost\&lt;<em>user_name</em>&gt; in the <strong>User name</strong> field.</span></span> <span data-ttu-id="67a63-151">Vous devez utiliser &lt;<em>nom_groupe_de_travail</em>&gt;\&lt;<em>nom_utilisateur</em>&gt;.</span><span class="sxs-lookup"><span data-stu-id="67a63-151">You must use &lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

3.  <span data-ttu-id="67a63-152">La section **Paramètres de connexion facultatifs** porte sur les exigences d’autorisation de l’ordinateur distant que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="67a63-152">The **Optional Connection Settings** section relates to the authorization requirements of the remote computer that you want to manage.</span></span> <span data-ttu-id="67a63-153">Pour plus d’informations sur les paramètres équivalents aux paramètres de connexion facultatifs, consultez l’[Aide de l’applet de commande Enter-PSSession](https://technet.microsoft.com/library/dd315384.aspx).</span><span class="sxs-lookup"><span data-stu-id="67a63-153">For more information about the parameters that are equivalent to optional connection settings, see the [Enter-PSSession cmdlet Help](https://technet.microsoft.com/library/dd315384.aspx).</span></span>

    <span data-ttu-id="67a63-154">En général, les informations d’identification que vous passez par le biais de la passerelle Accès Web Windows PowerShell sont identiques à celles reconnues par l’ordinateur distant que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="67a63-154">Typically, the credentials you use to pass through the Windows PowerShell Web Access gateway are the same that are recognized by the remote computer that you want to manage.</span></span> <span data-ttu-id="67a63-155">Toutefois, si vous souhaitez utiliser des informations d’identification différentes pour gérer l’ordinateur spécifié à l’étape 2, développez la section **Paramètres de connexion facultatifs** et spécifiez les autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="67a63-155">However, if you want to use different credentials to manage the remote computer that you specified in step 2, expand the **Optional Connection Settings** section, and provide the alternate credentials.</span></span> <span data-ttu-id="67a63-156">Sinon, passez à l’étape 6.</span><span class="sxs-lookup"><span data-stu-id="67a63-156">Otherwise, skip to step 6.</span></span>

4.  <span data-ttu-id="67a63-157">Si l’administrateur Accès Web Windows PowerShell a créé une configuration de session personnalisée pour les utilisateurs d’Accès Web Windows PowerShell, tapez le nom de cette configuration se session dans le champ **Nom de la configuration**.</span><span class="sxs-lookup"><span data-stu-id="67a63-157">If the Windows PowerShell Web Access administrator has created a custom session configuration for Windows PowerShell Web Access users, type the name of the session configuration name in the **Configuration name** field.</span></span> <span data-ttu-id="67a63-158">Pour plus d’informations sur les configurations de sessions, consultez [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) sur le site web de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="67a63-158">For more information about session configurations, see [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) on the Microsoft website.</span></span>

5.  <span data-ttu-id="67a63-159">Conservez le **Type d’authentification** **Par défaut**, sauf indication contraire de l’administrateur Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67a63-159">Keep the **Authentication type** set to **Default** unless you have been instructed to do otherwise by the Windows PowerShell Web Access administrator.</span></span>

6.  <span data-ttu-id="67a63-160">Cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="67a63-160">Click **Sign in**.</span></span>

<a href="" id="BKMK_timeout"></a>

<span data-ttu-id="67a63-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Déconnexion et dépassement de délais</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="67a63-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing out and timing out</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="67a63-162">Vous serez déconnecté de votre session web Windows PowerShell dans les cas suivants.</span><span class="sxs-lookup"><span data-stu-id="67a63-162">Any of the following signs you out of a web-based Windows PowerShell session.</span></span>

-   <span data-ttu-id="67a63-163">Clic sur le bouton **Se déconnecter** dans le coin inférieur droit de la console</span><span class="sxs-lookup"><span data-stu-id="67a63-163">Clicking **Sign out** in the lower right corner of the console.</span></span> <span data-ttu-id="67a63-164">(Windows Server 2012 uniquement).</span><span class="sxs-lookup"><span data-stu-id="67a63-164">(Windows Server 2012 only)</span></span>

-   <span data-ttu-id="67a63-165">Clic sur le bouton **Enregistrer** ou **Quitter** dans le coin inférieur droit de la console (Windows Server 2012 R2 uniquement).</span><span class="sxs-lookup"><span data-stu-id="67a63-165">Clicking **Save** or **Exit** in the lower right corner of the console (Windows Server 2012 R2 only).</span></span> <span data-ttu-id="67a63-166">Cliquez sur **Enregistrer** pour enregistrer et fermer votre session Accès Web Windows PowerShell ; vous pouvez vous reconnecter à la session ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="67a63-166">Clicking **Save** saves and closes your Windows PowerShell Web Access session; you can reconnect to the session later.</span></span> <span data-ttu-id="67a63-167">Quand vous vous reconnectez à Accès Web Windows PowerShell, une liste de vos sessions enregistrées s’affiche ; vous pouvez sélectionner et vous reconnecter à une session enregistrée ou démarrer une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="67a63-167">When you sign in to Windows PowerShell Web Access again, Windows PowerShell Web Access displays a list of your saved sessions; you can either select and reconnect to a saved session, or start a new session.</span></span> <span data-ttu-id="67a63-168">Le nombre maximal de sessions ouvertes autorisées à la fois enregistrées et actives par utilisateur, est configuré par l’administrateur de la passerelle.</span><span class="sxs-lookup"><span data-stu-id="67a63-168">The maximum number of open sessions that users are allowed, both saved and active, is configured by the gateway administrator.</span></span>

    <span data-ttu-id="67a63-169">Cliquez sur **Quitter** pour quitter la session Accès Web Windows PowerShell sans l’enregistrer.</span><span class="sxs-lookup"><span data-stu-id="67a63-169">Clicking **Exit** signs you out of the Windows PowerShell Web Access session without saving it.</span></span>

-   <span data-ttu-id="67a63-170">Tentative de connexion pour gérer un autre ordinateur distant dans la même session de navigateur ou sous un nouvel onglet de la même session de navigateur.</span><span class="sxs-lookup"><span data-stu-id="67a63-170">Attempting to sign in to manage a different remote computer in the same browser session, or in a new tab of the same browser session.</span></span> <span data-ttu-id="67a63-171">(Cela ne s’applique pas si le serveur de passerelle exécute Windows Server 2012 R2 ; l’exécution d’Accès Web Windows PowerShell sur Windows Server 2012 R2 autorise plusieurs sessions utilisateur sous de nouveaux onglets dans la même session de navigateur.) Pour plus d’informations sur la façon d’utiliser plusieurs sessions actives sur le même ordinateur, consultez « Connexion simultanée à plusieurs ordinateurs cibles » dans la section [Limitations de la console web](#BKMK_limits) de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="67a63-171">(This does not apply if the gateway server is running Windows Server 2012 R2; Windows PowerShell Web Access running on Windows Server 2012 R2 does allow multiple user sessions in new tabs in the same browser session.) For more information about how to use more than one active session on the same computer, see “Connecting to multiple target computers simultaneously” in the [Limitations of the web-based console](#BKMK_limits) section of this topic.</span></span>

-   <span data-ttu-id="67a63-172">20 minutes d’inactivité au cours de la session.</span><span class="sxs-lookup"><span data-stu-id="67a63-172">20 minutes of inactivity in the session.</span></span> <span data-ttu-id="67a63-173">L’administrateur de la passerelle peut personnaliser le délai d’inactivité. Pour plus d’informations, consultez [Gestion des sessions](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).</span><span class="sxs-lookup"><span data-stu-id="67a63-173">The gateway administrator can customize the inactivity time-out period; for more information, see [Session management](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).</span></span>

    -   <span data-ttu-id="67a63-174">Si vous êtes déconnecté d’une session de la console web en raison d’une erreur réseau ou d’autres défaillances ou arrêts non planifiés, et non parce que vous avez vous-même fermé la session, la session Accès Web Windows PowerShell continue de s’exécuter, connectée à l’ordinateur cible, jusqu’à ce que le délai d’expiration côté client soit écoulé.</span><span class="sxs-lookup"><span data-stu-id="67a63-174">If you are disconnected from a session in the web-based console because of a network error or other unplanned shutdown or failure, and not because you have closed the session yourself, the Windows PowerShell Web Access session continues to run, connected to the target computer, until the time-out period on the client side lapses.</span></span> <span data-ttu-id="67a63-175">Par défaut, ce délai est de 20 minutes et est configuré par l’administrateur de la passerelle.</span><span class="sxs-lookup"><span data-stu-id="67a63-175">By default, this time-out period is 20 minutes, and is configured by the gateway administrator.</span></span> <span data-ttu-id="67a63-176">La session est déconnectée après les 20 minutes définies par défaut, ou au terme du délai spécifié par l’administrateur de la passerelle, le délai le plus court étant appliqué.</span><span class="sxs-lookup"><span data-stu-id="67a63-176">The session is disconnected after either the default 20 minutes, or after the time-out period specified by the gateway administrator, whichever is shorter.</span></span>

        <span data-ttu-id="67a63-177">Si le serveur de passerelle exécute Windows Server 2012 R2, Accès Web Windows PowerShell permet aux utilisateurs de se reconnecter ultérieurement aux sessions enregistrées. Toutefois, vous ne pouvez pas accéder à ces sessions ou vous y reconnecter tant que le délai d’expiration spécifié par l’administrateur de la passerelle n’est pas écoulé.</span><span class="sxs-lookup"><span data-stu-id="67a63-177">If the gateway server is running Windows Server 2012 R2, Windows PowerShell Web Access lets users reconnect to saved sessions at a later time, but you cannot see or reconnect to saved sessions until after the time-out period specified by the gateway administrator has lapsed.</span></span>

-   <span data-ttu-id="67a63-178">Fermeture de la fenêtre ou de l’onglet de navigateur.</span><span class="sxs-lookup"><span data-stu-id="67a63-178">Closing the browser window or tab.</span></span>

-   <span data-ttu-id="67a63-179">Mise hors tension ou déconnexion du périphérique client sur lequel le navigateur s’exécute.</span><span class="sxs-lookup"><span data-stu-id="67a63-179">Turning off the client device on which the browser is running, or disconnecting it from the network.</span></span>

-   <span data-ttu-id="67a63-180">Exécution de la commande **Exit** dans la console web.</span><span class="sxs-lookup"><span data-stu-id="67a63-180">Running the **Exit** command in the web console.</span></span> <span data-ttu-id="67a63-181">Cette commande ne fonctionne pas si la configuration de session à laquelle vous êtes connecté est configurée pour prendre en charge le mode [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) ou si elle est dans une instance d’exécution restreinte.</span><span class="sxs-lookup"><span data-stu-id="67a63-181">This command does not work if the session configuration to which you are connected to is configured to support [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) mode, or is in a restricted runspace.</span></span>

<span data-ttu-id="67a63-182">Si vous souhaitez vous reconnecter, rouvrez la page web Accès Web Windows PowerShell et connectez-vous en effectuant les étapes de la section [Pour se connecter à Accès Web Windows PowerShell](#BKMK_signin) de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="67a63-182">If you want to sign in again, open the Windows PowerShell Web Access web page again, and sign in by following the steps in [To sign in to Windows PowerShell Web Access](#BKMK_signin) in this topic.</span></span>

<a href="" id="BKMK_web"></a>

<span data-ttu-id="67a63-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Différences dans la console Windows PowerShell Web</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="67a63-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Differences in the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="67a63-184">Une fois que vous vous êtes connecté à Accès Web Windows PowerShell, une console web Windows PowerShell s’ouvre dans la fenêtre ou l’onglet de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="67a63-184">After signing in to Windows PowerShell Web Access, a web-based Windows PowerShell console opens in your browser window or tab.</span></span> <span data-ttu-id="67a63-185">La console étant connectée à l’ordinateur distant que vous avez spécifié lors du processus de connexion, seuls les applets de commande ou scripts Windows PowerShell disponibles sur cet ordinateur distant peuvent être utilisés dans la console.</span><span class="sxs-lookup"><span data-stu-id="67a63-185">Because the console is connected to the remote computer that you specified during the sign-in process, only those Windows PowerShell cmdlets or scripts that are available on the remote computer can be used in the console.</span></span> <span data-ttu-id="67a63-186">Cette section décrit d’autres limitations des consoles Accès Web Windows PowerShell et les différences entre les consoles Accès Web Windows PowerShell et la console **PowerShell.exe** installée.</span><span class="sxs-lookup"><span data-stu-id="67a63-186">This section describes other limitations of Windows PowerShell Web Access consoles, and differences between Windows PowerShell Web Access consoles and the installed **PowerShell.exe** console.</span></span>

###

<span data-ttu-id="67a63-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Différences fonctionnelles avec PowerShell.exe</span></a></span><span class="sxs-lookup"><span data-stu-id="67a63-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Functional disparity with PowerShell.exe</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="67a63-188">La plupart des fonctionnalités hôtes de Windows PowerShell sont disponibles dans la console web Accès Web Windows PowerShell, mais certaines fonctionnalités ne sont pas accessibles.</span><span class="sxs-lookup"><span data-stu-id="67a63-188">The majority of Windows PowerShell host functionality is available in the Windows PowerShell Web Access web-based console, but there are some features that are not available.</span></span>

-   <span data-ttu-id="67a63-189"><span class="label">Affichage imbriqué de la progression.</span></span><span class="sxs-lookup"><span data-stu-id="67a63-189"><span class="label">Nested progress displays.</span></span></span>  <span data-ttu-id="67a63-190">Accès Web Windows PowerShell affiche une interface utilisateur graphique de progression pour les applets de commande qui indiquent la progression, mais seules les informations de progression de niveau supérieur sont affichées.</span><span class="sxs-lookup"><span data-stu-id="67a63-190">Windows PowerShell Web Access displays a progress GUI for cmdlets that report progress, but only top-level progress information is displayed.</span></span>

-   <span data-ttu-id="67a63-191"><span class="label">Modification de la couleur d’entrée.</span></span><span class="sxs-lookup"><span data-stu-id="67a63-191"><span class="label">Input color modification.</span></span></span>  <span data-ttu-id="67a63-192">La couleur d’entrée (premier plan et arrière-plan) ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="67a63-192">The input color (both foreground and background) cannot be changed.</span></span> <span data-ttu-id="67a63-193">Le style des messages de sortie, d’avertissement, de commentaires et d’erreur peut être modifié en exécutant un script.</span><span class="sxs-lookup"><span data-stu-id="67a63-193">The style of output, warning, verbose, and error messages can all be changed by running a script.</span></span>

-   <span data-ttu-id="67a63-194"><span class="label">PSHostRawUserInterface.</span></span><span class="sxs-lookup"><span data-stu-id="67a63-194"><span class="label">PSHostRawUserInterface.</span></span></span>  <span data-ttu-id="67a63-195">Accès Web Windows PowerShell est implémenté sur la gestion à distance Windows PowerShell et utilise une instance d’exécution distante.</span><span class="sxs-lookup"><span data-stu-id="67a63-195">Windows PowerShell Web Access is implemented over Windows PowerShell remote management, and uses a remote runspace.</span></span> <span data-ttu-id="67a63-196">Accès Web Windows PowerShell n’implémente pas certaines méthodes dans cette interface (par exemple les commandes qui écrivent dans la console Windows).</span><span class="sxs-lookup"><span data-stu-id="67a63-196">Windows PowerShell Web Access does not implement some methods in this interface; for example, any command that writes to the Windows console.</span></span> <span data-ttu-id="67a63-197">Les commandes telles que **PowerTab** ne fonctionnent pas dans Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67a63-197">Commands such as **PowerTab** do not work in Windows PowerShell Web Access.</span></span>

-   <span data-ttu-id="67a63-198"><span class="label">Touches de fonction.</span></span><span class="sxs-lookup"><span data-stu-id="67a63-198"><span class="label">Function keys.</span></span></span>  <span data-ttu-id="67a63-199">Accès Web Windows PowerShell ne prend pas en charge certaines touches de fonction, souvent car ces commandes sont réservées par le navigateur.</span><span class="sxs-lookup"><span data-stu-id="67a63-199">Windows PowerShell Web Access does not support some function keys, in many cases because the commands are reserved by the browser.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="67a63-200">Touche de fonction non prise en charge</span><span class="sxs-lookup"><span data-stu-id="67a63-200">Unsupported Function Key</span></span></p></th>
<th><p><span data-ttu-id="67a63-201">Action</span><span class="sxs-lookup"><span data-stu-id="67a63-201">Action</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="67a63-202">Ctrl+C</span><span class="sxs-lookup"><span data-stu-id="67a63-202">Ctrl+C</span></span></p></td>
<td><p><span data-ttu-id="67a63-203">Dans Accès Web Windows PowerShell, <strong>Ctrl+C</strong> est utilisé par le navigateur pour copier du contenu.</span><span class="sxs-lookup"><span data-stu-id="67a63-203">In Windows PowerShell Web Access, <strong>Ctrl+C</strong> is used by the browser to copy content.</span></span> <span data-ttu-id="67a63-204">La console propose un bouton <strong>Annuler</strong>, et les utilisateurs peuvent également utiliser <strong>Ctrl+Q</strong> pour annuler des commandes.</span><span class="sxs-lookup"><span data-stu-id="67a63-204">The console offers a <strong>Cancel</strong> button, and users can also use <strong>Ctrl+Q</strong> to cancel commands.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="67a63-205">Alt-Espace, e, l</span><span class="sxs-lookup"><span data-stu-id="67a63-205">Alt-space, e, l</span></span></p></td>
<td><p><span data-ttu-id="67a63-206">Parcourir la mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="67a63-206">Scroll through the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="67a63-207">Alt+Espace, e, f</span><span class="sxs-lookup"><span data-stu-id="67a63-207">Alt+Space, e, f</span></span></p></td>
<td><p><span data-ttu-id="67a63-208">Rechercher du texte dans la mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="67a63-208">Search for text in the screen buffer</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="67a63-209">Alt+Espace, e, k</span><span class="sxs-lookup"><span data-stu-id="67a63-209">Alt+Space, e, k</span></span></p></td>
<td><p><span data-ttu-id="67a63-210">Sélectionner du texte à copier à partir de la mémoire tampon d’écran</span><span class="sxs-lookup"><span data-stu-id="67a63-210">Select text to be copied from the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="67a63-211">Alt+Espace, e, p</span><span class="sxs-lookup"><span data-stu-id="67a63-211">Alt+Space, e, p</span></span></p></td>
<td><p><span data-ttu-id="67a63-212">Coller le contenu du Presse-papiers dans la console Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="67a63-212">Paste clipboard contents into the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="67a63-213">Alt+Espace, c</span><span class="sxs-lookup"><span data-stu-id="67a63-213">Alt+Space, c</span></span></p></td>
<td><p><span data-ttu-id="67a63-214">Fermer la console Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="67a63-214">Close the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="67a63-215">Ctrl+Pause</span><span class="sxs-lookup"><span data-stu-id="67a63-215">Ctrl+Break</span></span></p></td>
<td><p><span data-ttu-id="67a63-216">Forcer la fermeture de la fenêtre Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="67a63-216">Force the Windows PowerShell window to close</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="67a63-217">Ctrl+Origine</span><span class="sxs-lookup"><span data-stu-id="67a63-217">Ctrl+Home</span></span></p></td>
<td><p><span data-ttu-id="67a63-218">Supprimer à partir du début de la ligne de commande actuelle</span><span class="sxs-lookup"><span data-stu-id="67a63-218">Deletes from the beginning of the current command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="67a63-219">Ctrl+Fin</span><span class="sxs-lookup"><span data-stu-id="67a63-219">Ctrl+End</span></span></p></td>
<td><p><span data-ttu-id="67a63-220">Supprimer jusqu’à la fin de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="67a63-220">Deletes to end of the command line</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="67a63-221">F1</span><span class="sxs-lookup"><span data-stu-id="67a63-221">F1</span></span></p></td>
<td><p><span data-ttu-id="67a63-222">Déplacer le curseur d’un caractère vers la droite sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="67a63-222">Move cursor one character to the right on your command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="67a63-223">F2</span><span class="sxs-lookup"><span data-stu-id="67a63-223">F2</span></span></p></td>
<td><p><span data-ttu-id="67a63-224">Créer une commande en copiant la dernière commande jusqu’au caractère que vous tapez</span><span class="sxs-lookup"><span data-stu-id="67a63-224">Creates a new command by copying your last command up to the character that you type</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="67a63-225">F3</span><span class="sxs-lookup"><span data-stu-id="67a63-225">F3</span></span></p></td>
<td><p><span data-ttu-id="67a63-226">Terminer la ligne de commande avec le contenu de votre dernière ligne de commande</span><span class="sxs-lookup"><span data-stu-id="67a63-226">Complete the command line with content from your last command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="67a63-227">F4</span><span class="sxs-lookup"><span data-stu-id="67a63-227">F4</span></span></p></td>
<td><p><span data-ttu-id="67a63-228">Supprimer des caractères à la position du curseur</span><span class="sxs-lookup"><span data-stu-id="67a63-228">Deletes characters from cursor position</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="67a63-229">F5</span><span class="sxs-lookup"><span data-stu-id="67a63-229">F5</span></span></p></td>
<td><p><span data-ttu-id="67a63-230">Parcourir l’historique des commandes (des plus récentes au plus anciennes).</span><span class="sxs-lookup"><span data-stu-id="67a63-230">Scan backward through your command history.</span></span> <span data-ttu-id="67a63-231">Pour accéder aux commandes de l’historique dans Accès Web Windows PowerShell, cliquez sur les boutons de défilement <strong>Historique</strong> dans la console web.</span><span class="sxs-lookup"><span data-stu-id="67a63-231">To access commands in the command history in Windows PowerShell Web Access, click the <strong>History</strong> scroll buttons in the web-based console.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="67a63-232">F7</span><span class="sxs-lookup"><span data-stu-id="67a63-232">F7</span></span></p></td>
<td><p><span data-ttu-id="67a63-233">Sélectionner de manière interactive une commande dans votre historique de commandes</span><span class="sxs-lookup"><span data-stu-id="67a63-233">Interactively select a command from your command history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="67a63-234">F8</span><span class="sxs-lookup"><span data-stu-id="67a63-234">F8</span></span></p></td>
<td><p><span data-ttu-id="67a63-235">Parcourir l’historique en affichant les commandes qui correspondent au texte actif</span><span class="sxs-lookup"><span data-stu-id="67a63-235">Scan history displaying commands that match current text</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="67a63-236">F9</span><span class="sxs-lookup"><span data-stu-id="67a63-236">F9</span></span></p></td>
<td><p><span data-ttu-id="67a63-237">Exécuter une commande numérotée spécifique de l’historique</span><span class="sxs-lookup"><span data-stu-id="67a63-237">Run a specific numbered command from history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="67a63-238">Page précédente</span><span class="sxs-lookup"><span data-stu-id="67a63-238">Page Up</span></span></p></td>
<td><p><span data-ttu-id="67a63-239">Exécuter la première commande de l’historique</span><span class="sxs-lookup"><span data-stu-id="67a63-239">Run the first command in the history</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="67a63-240">Page suivante</span><span class="sxs-lookup"><span data-stu-id="67a63-240">Page Down</span></span></p></td>
<td><p><span data-ttu-id="67a63-241">Exécuter la dernière commande de l’historique</span><span class="sxs-lookup"><span data-stu-id="67a63-241">Run the last command in the history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="67a63-242">Alt+F7</span><span class="sxs-lookup"><span data-stu-id="67a63-242">Alt+F7</span></span></p></td>
<td><p><span data-ttu-id="67a63-243">Effacer la liste de l’historique de commandes</span><span class="sxs-lookup"><span data-stu-id="67a63-243">Clear the command history list</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="67a63-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitations de la console web</span></a></span><span class="sxs-lookup"><span data-stu-id="67a63-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitations of the web-based console</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="67a63-245"><span class="label">Double-saut.</span></span><span class="sxs-lookup"><span data-stu-id="67a63-245"><span class="label">Double-hop.</span></span></span>   <span data-ttu-id="67a63-246">Vous pouvez rencontrer la limitation relative au double-saut (connexion à un second ordinateur à partir de la première connexion) si vous tentez de créer ou de travailler sur une nouvelle session à l’aide d’Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67a63-246">You can encounter the double-hop (or connecting to a second computer from the first connection) limitation if you try to create or work on a new session by using Windows PowerShell Web Access.</span></span> <span data-ttu-id="67a63-247">Accès Web Windows PowerShell utilise une instance d’exécution à distance et, actuellement, **PowerShell.exe** ne prend pas en charge l’établissement d’une connexion à distance vers un second ordinateur à partir d’une instance d’exécution à distance.</span><span class="sxs-lookup"><span data-stu-id="67a63-247">Windows PowerShell Web Access uses a remote runspace, and currently, **PowerShell.exe** does not support establishing a remote connection to a second computer from a remote runspace.</span></span> <span data-ttu-id="67a63-248">Si vous essayez de vous connecter à un second ordinateur distant à partir d’une connexion existante, par exemple à l’aide de l’applet de commande **Enter-PSSession**, vous pouvez recevoir différents messages d’erreur, tels que « Impossible d’obtenir les ressources réseau ».</span><span class="sxs-lookup"><span data-stu-id="67a63-248">If you attempt to connect to a second remote computer from an existing connection by using the **Enter-PSSession** cmdlet, for example, you can get various errors, such as “Cannot get network resources.”</span></span>

    <span data-ttu-id="67a63-249">Pour éviter les erreurs de double-saut, votre administrateur doit configurer l’authentification CredSSP dans l’environnement réseau de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="67a63-249">To avoid double-hop errors, your administrator should configure CredSSP authentication in your organization’s network environment.</span></span> <span data-ttu-id="67a63-250">Pour plus d’informations sur la configuration de l’authentification CredSSP, consultez [CredSSP pour l’accès à distance de second saut](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) sur le site web de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="67a63-250">For more information about configuring CredSSP authentication, see [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) on the Microsoft website.</span></span> <span data-ttu-id="67a63-251">Vous pouvez également fournir des informations d’identification explicites quand vous voulez gérer un second ordinateur distant ; il est peu probable que des informations d’identification implicites autorisent le second saut.</span><span class="sxs-lookup"><span data-stu-id="67a63-251">You can also provide explicit credentials when you want to manage a second remote computer; implicit credentials are unlikely to allow the second hop.</span></span>

-   <span data-ttu-id="67a63-252">Accès Web Windows PowerShell utilise et présente les mêmes limitations qu’une session Windows PowerShell à distance.</span><span class="sxs-lookup"><span data-stu-id="67a63-252">Windows PowerShell Web Access uses and has the same limitations as a remote Windows PowerShell session.</span></span> <span data-ttu-id="67a63-253">Les commandes qui appellent directement des API de console Windows, telles que celles pour éditeurs basés sur console ou pour programmes de menu basé sur du texte, ne fonctionnent pas car les commandes ne lisent ni n’écrivent dans des canaux d’entrée, de sortie et d’erreur.</span><span class="sxs-lookup"><span data-stu-id="67a63-253">Commands that directly call Windows console APIs, such as those for console-based editors or text-based menu programs, do not work because the commands do not read or write to standard input, output, and error pipes.</span></span> <span data-ttu-id="67a63-254">Par conséquent, les commandes qui lancent un fichier exécutable, telles que **notepad.exe**, ou qui affichent une interface utilisateur graphique, telles que <span class="code">OpenGridView</span> ou <span class="code">ogv</span>, ne fonctionnent pas.</span><span class="sxs-lookup"><span data-stu-id="67a63-254">Therefore, commands that launch an executable file, such as **notepad.exe**, or display a GUI, such as <span class="code">OpenGridView</span> or <span class="code">ogv</span>, do not work.</span></span> <span data-ttu-id="67a63-255">Votre expérience est affectée par ce comportement ; pour vous, Accès Web Windows PowerShell semble ne pas répondre à votre commande.</span><span class="sxs-lookup"><span data-stu-id="67a63-255">Your experience is affected by this behavior; to you, it appears that Windows PowerShell Web Access is not responding to your command.</span></span>

-   <span data-ttu-id="67a63-256">La saisie semi-automatique par le biais de la touche Tab ne fonctionne pas dans une configuration de session avec une instance d’exécution restreinte ou en mode **NoLanguage**.</span><span class="sxs-lookup"><span data-stu-id="67a63-256">Tab completion does not work in a session configuration with a restricted runspace or one that is in **NoLanguage** mode.</span></span> <span data-ttu-id="67a63-257">Bien que les administrateurs puissent configurer une session pour prendre en charge la saisie semi-automatique via la touche TAB, cette pratique est déconseillée pour des raisons de sécurité car elle peut exposer les informations suivantes aux utilisateurs non autorisés :</span><span class="sxs-lookup"><span data-stu-id="67a63-257">Although administrators can configure a session to support tab completion, it is discouraged for security reasons, because it can expose the following information to unauthorized users.</span></span>

    -   <span data-ttu-id="67a63-258">chemins d’accès de système de fichiers internes ;</span><span class="sxs-lookup"><span data-stu-id="67a63-258">Internal file system paths</span></span>

    -   <span data-ttu-id="67a63-259">dossiers partagés sur les ordinateurs internes ;</span><span class="sxs-lookup"><span data-stu-id="67a63-259">Shared folders on internal computers</span></span>

    -   <span data-ttu-id="67a63-260">variables dans l’instance d’exécution ;</span><span class="sxs-lookup"><span data-stu-id="67a63-260">Variables in the runspace</span></span>

    -   <span data-ttu-id="67a63-261">types chargés ou espaces de noms du .NET Framework ;</span><span class="sxs-lookup"><span data-stu-id="67a63-261">Loaded types or.NET Framework namespaces</span></span>

    -   <span data-ttu-id="67a63-262">Variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="67a63-262">Environment variables</span></span>

-   <span data-ttu-id="67a63-263">Les utilisateurs connectés à une configuration de session **NoLanguage** ou à une instance d’exécution restreinte dans Accès Web Windows PowerShell ne peuvent pas exécuter la commande **Quitter** pour mettre fin à la session.</span><span class="sxs-lookup"><span data-stu-id="67a63-263">Users who are signed in to a **NoLanguage** session configuration or a restricted runspace in Windows PowerShell Web Access cannot run the **Exit** command to end the session.</span></span> <span data-ttu-id="67a63-264">Pour se déconnecter, les utilisateurs doivent cliquer sur **Se déconnecter** dans la page de console.</span><span class="sxs-lookup"><span data-stu-id="67a63-264">To sign out, users should click **Sign Out** on the console page.</span></span>

-   <span data-ttu-id="67a63-265"><span class="label">Connexion simultanée à plusieurs ordinateurs cibles.</span></span><span class="sxs-lookup"><span data-stu-id="67a63-265"><span class="label">Connecting to multiple target computers simultaneously.</span></span></span>   <span data-ttu-id="67a63-266">Si le serveur de passerelle exécute Windows Server 2012, Accès Web Windows PowerShell n’autorise qu’une seule connexion d’ordinateur distant par session de navigateur. Il n’autorise pas les utilisateurs à se connecter à plusieurs ordinateurs distants à l’aide d’onglets de navigateur distincts.</span><span class="sxs-lookup"><span data-stu-id="67a63-266">If the gateway server is running Windows Server 2012, Windows PowerShell Web Access allows only one remote computer connection per browser session; it does not allow users to sign in once, and connect to multiple remote computers by using separate browser tabs.</span></span> <span data-ttu-id="67a63-267">Quand vous ouvrez un nouvel onglet ou une nouvelle fenêtre de navigateur, Accès Web Windows PowerShell vous invite à mettre fin à votre session active et à démarrer une nouvelle session, afin que vous puissiez vous connecter au nouvel (ou au même) ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="67a63-267">When you open a new tab or new browser window, Windows PowerShell Web Access prompts you to disconnect your current session and start a new session, so that you can connect to the new (or the same) remote computer.</span></span> <span data-ttu-id="67a63-268">Si toutefois vous souhaitez ouvrir plusieurs sessions sur différents ordinateurs distants, une fonctionnalité d’Internet Explorer vous permet d’établir une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="67a63-268">If two or more separate sessions to different remote computers are desired, however, a feature in Internet Explorer lets you create a new session.</span></span> <span data-ttu-id="67a63-269">Pour démarrer une nouvelle session de navigateur dans Internet Explorer, appuyez sur **Alt**, ouvrez le menu **Fichier**, puis sélectionnez **Nouvelle session**.</span><span class="sxs-lookup"><span data-stu-id="67a63-269">To start a new browser session in Internet Explorer, press **ALT**, open the **File** menu, and then select **New Session**.</span></span> <span data-ttu-id="67a63-270">Ensuite, ouvrez le site web Accès Web Windows PowerShell dans la nouvelle session et connectez-vous pour accéder à un autre ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="67a63-270">Then, open the Windows PowerShell Web Access website in the new session, and sign in to access another remote computer.</span></span>

    <span data-ttu-id="67a63-271">Quand la passerelle Accès Web Windows PowerShell s’exécute sur Windows Server 2012 R2, les utilisateurs peuvent ouvrir plusieurs connexions à des ordinateurs distants dans différents onglets de navigateur.</span><span class="sxs-lookup"><span data-stu-id="67a63-271">When the Windows PowerShell Web Access gateway is running on Windows Server 2012 R2, users can open multiple connections to remote computers in different browser tabs.</span></span> <span data-ttu-id="67a63-272">Si vous souhaitez ouvrir plusieurs connexions à un ordinateur distant à l’aide de la console web Windows PowerShell, vérifiez auprès de votre administrateur de passerelle Accès Web Windows PowerShell que cette fonctionnalité est prise en charge par le serveur de passerelle.</span><span class="sxs-lookup"><span data-stu-id="67a63-272">If you want to open more than one connection to a remote computer by using the web-based Windows PowerShell console, check with your Windows PowerShell Web Access gateway administrator to see if this feature is supported by the gateway server.</span></span>

-   <span data-ttu-id="67a63-273"><span class="label">Sessions Windows PowerShell persistantes (reconnexion).</span></span><span class="sxs-lookup"><span data-stu-id="67a63-273"><span class="label">Persistent Windows PowerShell sessions (Reconnection).</span></span></span>   <span data-ttu-id="67a63-274">Une fois le délai d’expiration de la passerelle Accès Web Windows PowerShell atteint, la connexion à distance entre la passerelle et l’ordinateur cible est fermée.</span><span class="sxs-lookup"><span data-stu-id="67a63-274">After you time out of the Windows PowerShell Web Access gateway, the remote connection between the gateway and the target computer is closed.</span></span> <span data-ttu-id="67a63-275">Ceci arrête toutes les applets de commande et scripts en cours.</span><span class="sxs-lookup"><span data-stu-id="67a63-275">This stops any cmdlets or scripts that are currently in process.</span></span> <span data-ttu-id="67a63-276">Il est conseillé d’utiliser l’infrastructure **-Job** Windows PowerShell quand vous effectuez des tâches longues, de manière à pouvoir démarrer des travaux, vous déconnecter de l’ordinateur, vous reconnecter ultérieurement et conserver les travaux.</span><span class="sxs-lookup"><span data-stu-id="67a63-276">You are encouraged to use the Windows PowerShell **-Job** infrastructure when you are performing long-running tasks, so that you can start jobs, disconnect from the computer, reconnect later, and have jobs persist.</span></span> <span data-ttu-id="67a63-277">L’un des autres avantages offerts par les applets de commande **-Job** est la possibilité de les démarrer à l’aide d’Accès Web Windows PowerShell, de se déconnecter, puis de se reconnecter ultérieurement en exécutant Accès Web Windows PowerShell ou un autre hôte (tel que l’environnement d’écriture de scripts intégré de Windows PowerShell®).</span><span class="sxs-lookup"><span data-stu-id="67a63-277">Another benefit of using **-Job** cmdlets is that you can start them by using Windows PowerShell Web Access, sign out, and then reconnect later, either by running Windows PowerShell Web Access or another host (such as Windows PowerShell® Integrated Scripting Environment (ISE)).</span></span>

-   <span data-ttu-id="67a63-278"><span class="label">Redimensionnement de la console.</span></span><span class="sxs-lookup"><span data-stu-id="67a63-278"><span class="label">Console resizing.</span></span></span>   <span data-ttu-id="67a63-279">Vous pouvez redimensionner la fenêtre de console **PowerShell.exe** des trois manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="67a63-279">The **PowerShell.exe** console window can be resized in the following three ways.</span></span>

    -   <span data-ttu-id="67a63-280">en faisant glisser et en ajustant la taille de la fenêtre de console avec la souris ;</span><span class="sxs-lookup"><span data-stu-id="67a63-280">Drag and adjust the console window size with a mouse</span></span>

    -   <span data-ttu-id="67a63-281">en modifiant les propriétés de hauteur et de largeur à l’aide d’une interface utilisateur graphique destinée aux propriétés de la console ;</span><span class="sxs-lookup"><span data-stu-id="67a63-281">Change the height and width properties by using a GUI for console properties</span></span>

    -   <span data-ttu-id="67a63-282">en modifiant la hauteur et la largeur des fenêtres de console avec une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="67a63-282">Changing the height and width of console windows with a cmdlet</span></span>

        <span data-ttu-id="67a63-283">La fenêtre de console Accès Web Windows PowerShell peut être configurée comme suit à l’aide des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="67a63-283">The console window for Windows PowerShell Web Access can be configured by using the cmdlets as follows.</span></span> <span data-ttu-id="67a63-284">Dans l’exemple suivant, un utilisateur affecte la valeur **20** à la largeur de la console Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67a63-284">In the following example, a user changes the width of Windows PowerShell Web Access console to **20**.</span></span>

        [<span data-ttu-id="67a63-285">Copy</span><span class="sxs-lookup"><span data-stu-id="67a63-285">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_778d5e55-9195-4bd7-b313-d1fbca7876e4'); "Copier dans le Presse-papiers.")

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        <span data-ttu-id="67a63-286">Vous pouvez modifier la hauteur de la console d’une manière similaire.</span><span class="sxs-lookup"><span data-stu-id="67a63-286">You can change the height of the console in a similar manner.</span></span>

        <span data-ttu-id="67a63-287">D’autres exemples de personnalisation de l’affichage de la console sont disponibles sur le [blog de l’équipe Windows PowerShell](http://blogs.msdn.com/b/powershell/).</span><span class="sxs-lookup"><span data-stu-id="67a63-287">Additional examples for customizing the console view are available in the [Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/).</span></span>

<span data-ttu-id="67a63-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Voir aussi</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="67a63-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="67a63-289">[Référence pour les applets de commande Windows PowerShell](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell sur Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[Référentiel du Centre de scripts TechNet](http://gallery.technet.microsoft.com/scriptcenter)
[Centre de scripts - Blog « Hey, Scripting Guy! »](https://technet.microsoft.com/scriptcenter)
[Blog de l’équipe Windows PowerShell](http://blogs.msdn.com/b/powershell/)</span><span class="sxs-lookup"><span data-stu-id="67a63-289">[Windows PowerShell Cmdlet Reference](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell on Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet Script Center Repository](http://gallery.technet.microsoft.com/scriptcenter)
[Script Center - Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/)</span></span>

<span data-ttu-id="67a63-290"><span>Afficher :</span> Hérité Protégé</span><span class="sxs-lookup"><span data-stu-id="67a63-290"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="67a63-291"><span class="stdr-votetitle">Cette page vous a-t-elle été utile ?</span></span><span class="sxs-lookup"><span data-stu-id="67a63-291"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="67a63-292">Oui Non</span><span class="sxs-lookup"><span data-stu-id="67a63-292">Yes No</span></span>

<span data-ttu-id="67a63-293">Vous avez d’autres commentaires ?</span><span class="sxs-lookup"><span data-stu-id="67a63-293">Additional feedback?</span></span>

<span data-ttu-id="67a63-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caractères restants</span> Soumettre Ignorer</span><span class="sxs-lookup"><span data-stu-id="67a63-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="67a63-295"><span class="stdr-thankyou">Merci !</span></span><span class="sxs-lookup"><span data-stu-id="67a63-295"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="67a63-296"><span class="stdr-appreciate">Votre avis nous intéresse.</span></span><span class="sxs-lookup"><span data-stu-id="67a63-296"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="67a63-297">Gérer votre profil</span><span class="sxs-lookup"><span data-stu-id="67a63-297">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="67a63-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span>Commentaires sur le site</a> Commentaires sur le site</span><span class="sxs-lookup"><span data-stu-id="67a63-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="67a63-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="67a63-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="67a63-300">Faites-nous part de votre expérience...</span><span class="sxs-lookup"><span data-stu-id="67a63-300">Tell us about your experience...</span></span>

<span data-ttu-id="67a63-301">La page s’est elle chargée rapidement ?</span><span class="sxs-lookup"><span data-stu-id="67a63-301">Did the page load quickly?</span></span>

<span data-ttu-id="67a63-302"><span> Oui<span> </span></span> <span> Non<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="67a63-302"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="67a63-303">Êtes-vous satisfait de la conception de la page ?</span><span class="sxs-lookup"><span data-stu-id="67a63-303">Do you like the page design?</span></span>

<span data-ttu-id="67a63-304"><span> Oui<span> </span></span> <span> Non<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="67a63-304"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="67a63-305">Donnez-nous votre avis</span><span class="sxs-lookup"><span data-stu-id="67a63-305">Tell us more</span></span>

-   [<span data-ttu-id="67a63-306">Bulletin d’informations</span><span class="sxs-lookup"><span data-stu-id="67a63-306">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="67a63-307">Contactez-nous</span><span class="sxs-lookup"><span data-stu-id="67a63-307">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="67a63-308">Déclaration de confidentialité</span><span class="sxs-lookup"><span data-stu-id="67a63-308">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="67a63-309">Conditions d'utilisation</span><span class="sxs-lookup"><span data-stu-id="67a63-309">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="67a63-310">Marques</span><span class="sxs-lookup"><span data-stu-id="67a63-310">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="67a63-311">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="67a63-311">© 2016 Microsoft</span></span>

<span data-ttu-id="67a63-312">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="67a63-312">© 2016 Microsoft</span></span>

<span data-ttu-id="67a63-313">Les codes et les scripts développés par un tiers et en rapport à ce site doivent faire l’objet d’une licence fournie par le tiers, qui indique qu’il détient son code. Microsoft n’est pas partie prenante.</span><span class="sxs-lookup"><span data-stu-id="67a63-313">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="67a63-314">Consultez les conditions d’utilisation CDN Ajax ASP.NET (http://www.asp.net/ajaxlibrary/CDN.ashx).</span><span class="sxs-lookup"><span data-stu-id="67a63-314">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

