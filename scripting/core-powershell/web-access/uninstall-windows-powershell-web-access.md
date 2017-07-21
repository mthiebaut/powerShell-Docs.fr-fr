---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Désinstaller Accès Web Windows PowerShell"
ms.openlocfilehash: 7231d5eadceda8e3b28d9a81c2b5dcbe43680ff2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
#  <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="cffd0-103">désinstaller Accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cffd0-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="cffd0-104">Mise à jour : 24 juin 2013</span><span class="sxs-lookup"><span data-stu-id="cffd0-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="cffd0-105">S’applique à : Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="cffd0-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="cffd0-106">Suivez les étapes de cette rubrique pour supprimer le site web et l’application Accès Web Windows PowerShell du serveur de passerelle qui exécute Windows Server 2012 R2 ou Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="cffd0-106">Follow steps in this topic to delete the Windows PowerShell Web Access website and application from the gateway server that is running either Windows Server 2012 R2 or Windows Server 2012.</span></span> <span data-ttu-id="cffd0-107">Avant de commencer, informez les utilisateurs de la console Web de la suppression du site Web.</span><span class="sxs-lookup"><span data-stu-id="cffd0-107">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

<span data-ttu-id="cffd0-108">Avant de désinstaller Accès Web Windows PowerShell du serveur de passerelle, exécutez l’applet de commande <span class="code">Uninstall-PswaWebApplication</span>pour supprimer le site web et les applications web Accès Web Windows PowerShell ou utilisez la procédure du Gestionnaire des services Internet, [Pour supprimer le site web et les applications web Accès Web Windows PowerShell à l’aide du Gestionnaire de services Internet](#BKMK_delsite).</span><span class="sxs-lookup"><span data-stu-id="cffd0-108">Before you uninstall Windows PowerShell Web Access from the gateway server, either run the <span class="code">Uninstall-PswaWebApplication</span> cmdlet to remove the website and Windows PowerShell Web Access web applications, or use the IIS Manager procedure, [To delete the Windows PowerShell Web Access website and web applications by using IIS Manager](#BKMK_delsite).</span></span>

<span data-ttu-id="cffd0-109">La désinstallation d’Accès Web Windows PowerShell ne désinstalle pas IIS ni d’autres fonctionnalités automatiquement installées, car Accès Web Windows PowerShell en a besoin pour s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="cffd0-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="cffd0-110">Le processus de désinstallation laisse les fonctionnalités installées dont dépendait Accès Web Windows PowerShell ; vous pouvez désinstaller ces fonctionnalités séparément si besoin.</span><span class="sxs-lookup"><span data-stu-id="cffd0-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

<span data-ttu-id="cffd0-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Désinstallation (rapide) recommandée</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="cffd0-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="cffd0-112">Les procédures de cette section vous permettent de désinstaller l’application web Accès Web Windows PowerShell et la fonctionnalité Accès Web Windows PowerShell à l’aide des applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cffd0-112">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using Windows PowerShell cmdlets.</span></span>

###

<span data-ttu-id="cffd0-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 1 : supprimer l’application web</span></a></span><span class="sxs-lookup"><span data-stu-id="cffd0-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="cffd0-114">Si vous avez défini un nom de site web personnalisé, ajoutez le paramètre <span class="code">WebsiteName</span> à votre commande et spécifiez le nom du site web.</span><span class="sxs-lookup"><span data-stu-id="cffd0-114">If you have specified your own, custom website name, add the <span class="code">WebsiteName</span> parameter to your command, and specify the website name.</span></span> <span data-ttu-id="cffd0-115">Si vous avez utilisé une application web personnalisée (et non l’application par défaut **pswa**), ajoutez le paramètre <span class="code">WebApplicationName</span> à votre commande et spécifiez le nom de l’application web.</span><span class="sxs-lookup"><span data-stu-id="cffd0-115">If you have used a custom web application (not the default application, **pswa**, add the <span class="code">WebApplicationName</span> parameter to your command, and specify the name of the web application.</span></span>

#### <a name="to-delete-the-website-and-web-applications-by-using-the-uninstall-pswawebapplication-cmdlet"></a><span data-ttu-id="cffd0-116">Pour supprimer le site Web et les applications Web à l’aide de l’applet de commande Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="cffd0-116">To delete the website and web applications by using the Uninstall-PswaWebApplication cmdlet</span></span>

1.  <span data-ttu-id="cffd0-117">Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cffd0-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="cffd0-118">Sur le Bureau Windows, cliquez avec le bouton droit sur **Windows PowerShell** dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="cffd0-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="cffd0-119">Dans l’écran d’**accueil** de Windows, cliquez sur **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="cffd0-120">Tapez **Uninstall-PswaWebApplication**, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-120">Type **Uninstall-PswaWebApplication**, and then press **Enter**.</span></span>

3.  <span data-ttu-id="cffd0-121">Si vous utilisez un certificat de test, ajoutez le paramètre <span class="code">DeleteTestCertificate</span> à l’applet de commande, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="cffd0-121">If you are using a test certificate, add the <span class="code">DeleteTestCertificate</span> parameter to the cmdlet, as shown in the following example.</span></span>

    [<span data-ttu-id="cffd0-122">Copy</span><span class="sxs-lookup"><span data-stu-id="cffd0-122">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "Copier dans le Presse-papiers.")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<span data-ttu-id="cffd0-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 2 : désinstaller Accès Web Windows PowerShell</span></a></span><span class="sxs-lookup"><span data-stu-id="cffd0-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="cffd0-124">Pour désinstaller Accès Web Windows PowerShell à l’aide des applets de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cffd0-124">To uninstall Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="cffd0-125">Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell avec des droits utilisateur élevés.</span><span class="sxs-lookup"><span data-stu-id="cffd0-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="cffd0-126">Si une session est déjà ouverte, passez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="cffd0-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="cffd0-127">Sur le Bureau Windows, cliquez avec le bouton droit dans la barre des tâches sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="cffd0-128">Dans l’écran d’**accueil** de Windows, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="cffd0-129">Tapez ce qui suit, puis appuyez sur **Entrée**, où *computer_name* représente le nom de l’ordinateur distant sur lequel vous souhaitez installer Accès Web Windows PowerShell, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="cffd0-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="cffd0-130">Le paramètre <span class="code">-Restart</span> redémarre automatiquement les serveurs de destination si la suppression l’exige.</span><span class="sxs-lookup"><span data-stu-id="cffd0-130">The <span class="code">-Restart</span> parameter automatically restarts destination servers if required by the removal.</span></span>

    [<span data-ttu-id="cffd0-131">Copy</span><span class="sxs-lookup"><span data-stu-id="cffd0-131">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "Copier dans le Presse-papiers.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="cffd0-132">Pour supprimer des rôles et fonctionnalités d’un disque dur virtuel hors connexion, ajoutez les paramètres <span class="code">-ComputerName</span> et <span class="code">-VHD</span>.</span><span class="sxs-lookup"><span data-stu-id="cffd0-132">To remove roles and features from an offline VHD, you must add both the <span class="code">-ComputerName</span> parameter and the <span class="code">-VHD</span> parameter.</span></span> <span data-ttu-id="cffd0-133">Le paramètre <span class="code">ComputerName</span> contient le nom du serveur sur lequel monter le disque dur virtuel, tandis que le paramètre <span class="code">VHD</span> contient le chemin du fichier VHD sur le serveur spécifié.</span><span class="sxs-lookup"><span data-stu-id="cffd0-133">The <span class="code">-ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">-VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="cffd0-134">Copy</span><span class="sxs-lookup"><span data-stu-id="cffd0-134">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "Copier dans le Presse-papiers.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

3.  <span data-ttu-id="cffd0-135">Une fois l’installation terminée, vérifiez que vous avez bien supprimé Accès Web Windows PowerShell. Pour cela, ouvrez la page **Tous les serveurs** dans le Gestionnaire de serveur, sélectionnez un serveur sur lequel vous avez installé la fonctionnalité, puis examinez la vignette **Rôles et fonctionnalités** dans la page du serveur sélectionné.</span><span class="sxs-lookup"><span data-stu-id="cffd0-135">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span> <span data-ttu-id="cffd0-136">Vous pouvez également exécuter l’applet de commande <span class="code">Get-WindowsFeature</span> qui cible le serveur sélectionné (Get-WindowsFeature -ComputerName &lt;*nom_ordinateur*&gt;) pour afficher la liste des rôles et fonctionnalités installés sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="cffd0-136">You can also run the <span class="code">Get-WindowsFeature</span> cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

<span data-ttu-id="cffd0-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Désinstallation personnalisée</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="cffd0-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="cffd0-138">Les procédures de cette section vous permettent de désinstaller l’application web Accès Web Windows PowerShell et la fonctionnalité Accès Web Windows PowerShell en utilisant l’Assistant Suppression de rôles et de fonctionnalités dans le Gestionnaire de serveur et la console du Gestionnaire des services Internet.</span><span class="sxs-lookup"><span data-stu-id="cffd0-138">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

###

<span data-ttu-id="cffd0-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 1 : supprimer l’application web</span></a></span><span class="sxs-lookup"><span data-stu-id="cffd0-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-delete-the-windows-powershell-web-access-website-and-web-applications-by-using-iis-manager"></a><span data-ttu-id="cffd0-140">Pour supprimer le site Web et les applications Web Accès Web Windows PowerShell à l’aide du Gestionnaire de services Internet</span><span class="sxs-lookup"><span data-stu-id="cffd0-140">To delete the Windows PowerShell Web Access website and web applications by using IIS Manager</span></span>

1.  <span data-ttu-id="cffd0-141">Ouvrez la console du Gestionnaire des services Internet en procédant de l’une des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="cffd0-141">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="cffd0-142">Si elle est déjà ouverte, passez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="cffd0-142">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="cffd0-143">Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows.</span><span class="sxs-lookup"><span data-stu-id="cffd0-143">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="cffd0-144">Dans le menu **Outils** du Gestionnaire de serveur, cliquez sur **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-144">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="cffd0-145">Sur l’écran d’**accueil** de Windows, tapez une partie du nom **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-145">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="cffd0-146">Cliquez sur le raccourci quand il s’affiche dans les résultats **Applications**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-146">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="cffd0-147">Dans le volet de l’arborescence du Gestionnaire des services Internet, sélectionnez le site web qui exécute l’application web Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cffd0-147">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

3.  <span data-ttu-id="cffd0-148">Dans le volet **Actions**, sous **Gérer le site web**, cliquez sur **Arrêter**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-148">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

4.  <span data-ttu-id="cffd0-149">Dans le volet de l’arborescence, cliquez avec le bouton droit sur l’application web dans le site web qui exécute l’application web Accès Web Windows PowerShell, puis cliquez sur **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-149">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

5.  <span data-ttu-id="cffd0-150">Dans le volet de l’arborescence, sélectionnez **Pools d’applications**, sélectionnez le dossier du pool d’applications Accès Web Windows PowerShell, cliquez sur **Arrêter** dans le volet **Actions**, puis cliquez sur **Supprimer** dans le volet de contenu.</span><span class="sxs-lookup"><span data-stu-id="cffd0-150">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

6.  <span data-ttu-id="cffd0-151">Fermez le Gestionnaire des services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="cffd0-151">Close IIS Manager.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="cffd0-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Remarque </span></span><span class="sxs-lookup"><span data-stu-id="cffd0-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="cffd0-153">Le certificat n’est pas supprimé durant la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="cffd0-153">The certificate is not deleted during uninstallation.</span></span> <span data-ttu-id="cffd0-154">Si vous avez créé un certificat auto-signé ou utilisé un certificat de test et que vous souhaitez le supprimer, supprimez le certificat dans le Gestionnaire des services Internet.</span><span class="sxs-lookup"><span data-stu-id="cffd0-154">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="cffd0-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 2 : désinstaller Accès Web Windows PowerShell</span></a></span><span class="sxs-lookup"><span data-stu-id="cffd0-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="cffd0-156">Pour désinstaller Accès Web Windows PowerShell à l’aide de l’Assistant Suppression de rôles et de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="cffd0-156">To uninstall Windows PowerShell Web Access by using the Remove Roles and Features Wizard</span></span>

1.  <span data-ttu-id="cffd0-157">Si le Gestionnaire de serveur est déjà ouvert, passez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="cffd0-157">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="cffd0-158">S’il n’est pas déjà ouvert, ouvrez-le en effectuant l’une des opérations suivantes.</span><span class="sxs-lookup"><span data-stu-id="cffd0-158">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="cffd0-159">Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows.</span><span class="sxs-lookup"><span data-stu-id="cffd0-159">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="cffd0-160">Dans l’écran d’**accueil** de Windows, cliquez sur **Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-160">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="cffd0-161">Dans le menu **Gérer**, cliquez sur **Supprimer des rôles et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-161">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

3.  <span data-ttu-id="cffd0-162">Dans la page **Sélectionner le serveur de destination**, sélectionnez le serveur ou le disque dur virtuel hors connexion sur lequel vous souhaitez supprimer la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="cffd0-162">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="cffd0-163">Pour sélectionner un disque dur virtuel hors connexion, choisissez d’abord le serveur sur lequel monter le disque dur virtuel, puis sélectionnez le fichier VHD.</span><span class="sxs-lookup"><span data-stu-id="cffd0-163">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="cffd0-164">Une fois que vous avez sélectionné le serveur de destination, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-164">After you have selected the destination server, click **Next**.</span></span>

4.  <span data-ttu-id="cffd0-165">Cliquez de nouveau sur **Suivant** pour passer à la page **Supprimer des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-165">Click **Next** again to skip to the **Remove features** page.</span></span>

5.  <span data-ttu-id="cffd0-166">Décochez la case **Accès Web Windows PowerShell**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-166">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

6.  <span data-ttu-id="cffd0-167">Dans la page **Confirmer les sélections pour la suppression**, cliquez sur **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="cffd0-167">On the **Confirm removal selections** page, click **Remove**.</span></span>

<span data-ttu-id="cffd0-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Voir aussi</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="cffd0-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="cffd0-169">[Installer et utiliser Accès Web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[Aide du Gestionnaire des services Internet 7.0](https://technet.microsoft.com/library/cc732664.aspx)</span><span class="sxs-lookup"><span data-stu-id="cffd0-169">[Install and Use Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)</span></span>

<span data-ttu-id="cffd0-170"><span>Afficher :</span> Hérité Protégé</span><span class="sxs-lookup"><span data-stu-id="cffd0-170"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="cffd0-171"><span class="stdr-votetitle">Cette page vous a-t-elle été utile ?</span></span><span class="sxs-lookup"><span data-stu-id="cffd0-171"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="cffd0-172">Oui Non</span><span class="sxs-lookup"><span data-stu-id="cffd0-172">Yes No</span></span>

<span data-ttu-id="cffd0-173">Vous avez d’autres commentaires ?</span><span class="sxs-lookup"><span data-stu-id="cffd0-173">Additional feedback?</span></span>

<span data-ttu-id="cffd0-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caractères restants</span> Soumettre Ignorer</span><span class="sxs-lookup"><span data-stu-id="cffd0-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="cffd0-175"><span class="stdr-thankyou">Merci !</span></span><span class="sxs-lookup"><span data-stu-id="cffd0-175"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="cffd0-176"><span class="stdr-appreciate">Votre avis nous intéresse.</span></span><span class="sxs-lookup"><span data-stu-id="cffd0-176"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="cffd0-177">Gérer votre profil</span><span class="sxs-lookup"><span data-stu-id="cffd0-177">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="cffd0-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span>Commentaires sur le site</a> Commentaires sur le site</span><span class="sxs-lookup"><span data-stu-id="cffd0-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="cffd0-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="cffd0-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="cffd0-180">Faites-nous part de votre expérience...</span><span class="sxs-lookup"><span data-stu-id="cffd0-180">Tell us about your experience...</span></span>

<span data-ttu-id="cffd0-181">La page s’est elle chargée rapidement ?</span><span class="sxs-lookup"><span data-stu-id="cffd0-181">Did the page load quickly?</span></span>

<span data-ttu-id="cffd0-182"><span> Oui<span> </span></span> <span> Non<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="cffd0-182"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="cffd0-183">Êtes-vous satisfait de la conception de la page ?</span><span class="sxs-lookup"><span data-stu-id="cffd0-183">Do you like the page design?</span></span>

<span data-ttu-id="cffd0-184"><span> Oui<span> </span></span> <span> Non<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="cffd0-184"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="cffd0-185">Donnez-nous votre avis</span><span class="sxs-lookup"><span data-stu-id="cffd0-185">Tell us more</span></span>

-   [<span data-ttu-id="cffd0-186">Bulletin d’informations</span><span class="sxs-lookup"><span data-stu-id="cffd0-186">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="cffd0-187">Contactez-nous</span><span class="sxs-lookup"><span data-stu-id="cffd0-187">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="cffd0-188">Déclaration de confidentialité</span><span class="sxs-lookup"><span data-stu-id="cffd0-188">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="cffd0-189">Conditions d'utilisation</span><span class="sxs-lookup"><span data-stu-id="cffd0-189">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="cffd0-190">Marques</span><span class="sxs-lookup"><span data-stu-id="cffd0-190">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="cffd0-191">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="cffd0-191">© 2016 Microsoft</span></span>

<span data-ttu-id="cffd0-192">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="cffd0-192">© 2016 Microsoft</span></span>

<span data-ttu-id="cffd0-193">Les codes et les scripts développés par un tiers et en rapport à ce site doivent faire l’objet d’une licence fournie par le tiers, qui indique qu’il détient son code. Microsoft n’est pas partie prenante.</span><span class="sxs-lookup"><span data-stu-id="cffd0-193">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="cffd0-194">Consultez les conditions d’utilisation CDN Ajax ASP.NET (http://www.asp.net/ajaxlibrary/CDN.ashx).</span><span class="sxs-lookup"><span data-stu-id="cffd0-194">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

