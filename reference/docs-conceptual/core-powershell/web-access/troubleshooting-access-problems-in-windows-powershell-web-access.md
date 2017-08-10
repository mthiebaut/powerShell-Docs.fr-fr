---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "résolution des problèmes d’accès dans Accès Web Windows PowerShell"
ms.openlocfilehash: c10e19b177110ff62d44f28b6a523380b55b79e0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
#  <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="f0e7d-103">Résolution des problèmes d’accès dans Accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f0e7d-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="f0e7d-104">Mise à jour : 24 juin 2013</span><span class="sxs-lookup"><span data-stu-id="f0e7d-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="f0e7d-105">S’applique à : Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="f0e7d-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

<span data-ttu-id="f0e7d-106">Le tableau suivant identifie certains problèmes courants que les utilisateurs peuvent rencontrer quand ils essaient de se connecter à un ordinateur distant à l’aide d’Accès Web Windows PowerShell et inclut des suggestions de résolution.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-106">The following table identifies some common problems that users might experience when they are attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="f0e7d-107">Problème</span><span class="sxs-lookup"><span data-stu-id="f0e7d-107">Problem</span></span></p></th>
<th><p><span data-ttu-id="f0e7d-108">Cause possible et solution</span><span class="sxs-lookup"><span data-stu-id="f0e7d-108">Possible cause and solution</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f0e7d-109">Échec de connexion</span><span class="sxs-lookup"><span data-stu-id="f0e7d-109">Sign-in failure</span></span></p></td>
<td><p><span data-ttu-id="f0e7d-110">L’échec peut avoir les causes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-110">Failure could occur because of any of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="f0e7d-111">Il n’existe aucune règle d’autorisation qui autorise l’utilisateur à accéder à l’ordinateur, ni configuration de session spécifique sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-111">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span> <span data-ttu-id="f0e7d-112">La sécurité d’Accès Web Windows PowerShell est restrictive ; les utilisateurs doivent recevoir un accès explicite aux ordinateurs distants à l’aide de règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-112">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span> <span data-ttu-id="f0e7d-113">Pour plus d’informations sur la création de règles d’autorisation, consultez <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell</a> dans ce guide.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-113">For more information about creating authorization rules, see <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a> in this guide.</span></span></p></li>
<li><p><span data-ttu-id="f0e7d-114">L’utilisateur n’est pas autorisé à accéder à l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-114">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="f0e7d-115">Cet accès est déterminé par des listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-115">This is determined by access control lists (ACLs).</span></span> <span data-ttu-id="f0e7d-116">Pour plus d’informations, consultez « Connexion à Accès Web Windows PowerShell » dans <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Utiliser la console web Windows PowerShell</a> ou le <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">blog de l’équipe Windows PowerShell</a>.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-116">For more information, see “Signing in to Windows PowerShell Web Access” in <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Use the Web-based Windows PowerShell Console</a>, or the <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell Team Blog</a>.</span></span></p>
<ul>
<li><p><span data-ttu-id="f0e7d-117">La gestion à distance Windows PowerShell n’est peut-être pas activée sur l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-117">Windows PowerShell remote management might not be enabled on the destination computer.</span></span> <span data-ttu-id="f0e7d-118">Vérifiez qu’elle est activée sur l’ordinateur auquel l’utilisateur essaie de se connecter.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-118">Verify that it is enabled on the computer to which the user is trying to connect.</span></span> <span data-ttu-id="f0e7d-119">Pour plus d’informations, consultez « Comment configurer votre ordinateur pour la communication à distance » dans <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> dans les rubriques d’aide conceptuelle de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-119">For more information, see “How to Configure Your Computer for Remoting” in <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> in the Windows PowerShell About Help Topics.</span></span></p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f0e7d-120">Quand des utilisateurs essaient de se connecter à Accès Web Windows PowerShell dans une fenêtre Internet Explorer, une page <strong>Erreur de serveur interne</strong> leur est présentée ou Internet Explorer cesse de répondre.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-120">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an <strong>Internal Server Error</strong> page, or Internet Explorer stops responding.</span></span> <span data-ttu-id="f0e7d-121">Ce problème est propre à Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-121">This issue is specific to Internet Explorer.</span></span></p></td>
<td><p><span data-ttu-id="f0e7d-122">Il peut survenir pour les utilisateurs qui se sont connectés avec un nom de domaine contenant des caractères chinois ou si un ou plusieurs caractères chinois font partie du nom du serveur de passerelle.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span> <span data-ttu-id="f0e7d-123">Pour contourner ce problème, l’utilisateur doit <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">installer et exécuter Internet Explorer 10</a>, puis effectuer les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-123">To work around this issue, the user should <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">install and run Internet Explorer 10</a>, and then perform the following steps.</span></span></p>
<ol>
<li><p><span data-ttu-id="f0e7d-124">Remplacez le paramètre Internet Explorer <strong>Mode de document</strong> par <strong>Normes Internet Explorer 10</strong>.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-124">Change the Internet Explorer <strong>Document Mode</strong> setting to <strong>IE10 standards</strong>.</span></span></p>
<ol>
<li><p><span data-ttu-id="f0e7d-125">Appuyez sur <strong>F12</strong> pour ouvrir la console Outils de développement.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-125">Press <strong>F12</strong> to open the Developer Tools console.</span></span></p></li>
<li><p><span data-ttu-id="f0e7d-126">Dans Internet Explorer 10, cliquez sur <strong>Mode navigateur</strong>, puis sélectionnez <strong>Internet Explorer 10</strong>.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-126">In Internet Explorer 10, click <strong>Browser Mode</strong>, and then select <strong>Internet Explorer 10</strong>.</span></span></p></li>
<li><p><span data-ttu-id="f0e7d-127">Cliquez sur <strong>Mode de document</strong>, puis sur <strong>Normes Internet Explorer 10</strong>.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-127">Click <strong>Document Mode</strong>, and then click <strong>IE10 standards</strong>.</span></span></p></li>
<li><p><span data-ttu-id="f0e7d-128">Appuyez de nouveau sur <strong>F12</strong> pour fermer la console Outils de développement.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-128">Press <strong>F12</strong> again to close the Developer Tools console.</span></span></p></li>
</ol></li>
<li><p><span data-ttu-id="f0e7d-129">Désactivez la configuration automatique du proxy.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-129">Disable automatic proxy configuration.</span></span></p>
<ol>
<li><p><span data-ttu-id="f0e7d-130">Dans Internet Explorer 10, cliquez sur <strong>Outils</strong>, puis sur <strong>Options Internet</strong>.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-130">In Internet Explorer 10, click <strong>Tools</strong>, and then click <strong>Internet Options</strong>.</span></span></p></li>
<li><p><span data-ttu-id="f0e7d-131">Dans la boîte de dialogue <strong>Options Internet</strong>, sous l’onglet <strong>Connexions</strong>, cliquez sur <strong>Paramètres réseau</strong>.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-131">In the <strong>Internet Options</strong> dialog box, on the <strong>Connections</strong> tab, click <strong>LAN settings</strong>.</span></span></p></li>
<li><p><span data-ttu-id="f0e7d-132">Décochez la case <strong>Détecter automatiquement les paramètres de connexion</strong>.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-132">Clear the <strong>Automatically detect settings</strong> check box.</span></span> <span data-ttu-id="f0e7d-133">Cliquez sur <strong>OK</strong>, puis de nouveau sur <strong>OK</strong> pour fermer la boîte de dialogue <strong>Options Internet</strong>.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-133">Click <strong>OK</strong>, and then click <strong>OK</strong> again to close the <strong>Internet Options</strong> dialog box.</span></span></p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f0e7d-134">Impossible de se connecter à un ordinateur de groupe de travail distant</span><span class="sxs-lookup"><span data-stu-id="f0e7d-134">Cannot connect to a remote workgroup computer</span></span></p></td>
<td><p><span data-ttu-id="f0e7d-135">Si l’ordinateur de destination est membre d’un groupe de travail, utilisez la syntaxe suivante pour fournir votre nom d’utilisateur et vous connecter à l’ordinateur : &lt;<em>nom_groupe_de_travail</em>&gt;\&lt;<em>nom_utilisateur</em>&gt;</span><span class="sxs-lookup"><span data-stu-id="f0e7d-135">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f0e7d-136">Impossible de trouver les outils de gestion de serveur Web (IIS) bien que le rôle ait été installé</span><span class="sxs-lookup"><span data-stu-id="f0e7d-136">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span></p></td>
<td><p><span data-ttu-id="f0e7d-137">Si vous avez installé Accès Web Windows PowerShell à l’aide de l’applet de commande <span class="code">Install-WindowsFeature</span>, les outils de gestion ne sont pas installés, sauf si le paramètre <span class="code">IncludeManagementTools</span> est ajouté à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-137">If you installed Windows PowerShell Web Access by using the <span class="code">Install-WindowsFeature</span> cmdlet, management tools are not installed unless the <span class="code">IncludeManagementTools</span> parameter is added to the cmdlet.</span></span> <span data-ttu-id="f0e7d-138">Pour obtenir un exemple, consultez « Pour installer Accès Web Windows PowerShell à l’aide des applets de commande Windows PowerShell » dans <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Installer et utiliser Accès Web Windows PowerShell</a>.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-138">For an example, see “To install Windows PowerShell Web Access by using Windows PowerShell cmdlets” in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a>.</span></span> <span data-ttu-id="f0e7d-139">Vous pouvez ajouter la console du Gestionnaire des services Internet et d’autres outils de gestion IIS dont vous avez besoin en sélectionnant les outils dans une session de l’Assistant Ajout de rôles et de fonctionnalités qui cible le serveur de passerelle.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-139">You can add the IIS Manager console and other IIS management tools that you need by selecting the tools in an Add Roles and Features Wizard session that is targeted at the gateway server.</span></span> <span data-ttu-id="f0e7d-140">Vous pouvez ouvrir l’Assistant Ajout de rôles et de fonctionnalités à partir du Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-140">The Add Roles and Features Wizard is opened from within Server Manager.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f0e7d-141">Le site web Accès Web Windows PowerShell n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-141">The Windows PowerShell Web Access website is not accessible</span></span></p></td>
<td><p><span data-ttu-id="f0e7d-142">Si la Configuration de sécurité renforcée est activée dans Internet Explorer (IE ESC), vous pouvez ajouter le site web Accès Web Windows PowerShell à la liste des sites de confiance ou désactiver IE ESC.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-142">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites, or disable IE ESC.</span></span> <span data-ttu-id="f0e7d-143">Vous pouvez désactiver IE ESC dans la vignette <strong>Propriétés</strong> de la page <strong>Serveur local</strong> dans le Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-143">You can disable IE ESC in the <strong>Properties</strong> tile on the <strong>Local Server</strong> page in Server Manager.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f0e7d-144">Le message d’erreur suivant s’affiche lors de la tentative de connexion, quand le serveur de passerelle est à la fois l’ordinateur de destination et un groupe de travail : <strong>Un échec d’autorisation s’est produit. Vérifiez que vous êtes autorisé à vous connecter à l’ordinateur de destination.</strong></span><span class="sxs-lookup"><span data-stu-id="f0e7d-144">The following error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup: <strong>An authorization failure occurred. Verify that you are authorized to connect to the destination computer.</strong></span></span></p></td>
<td><p><span data-ttu-id="f0e7d-145">Quand le serveur de passerelle est également le serveur de destination, et qu’il se trouve dans un groupe de travail, spécifiez le nom d’utilisateur, le nom d’ordinateur et le nom du groupe d’utilisateurs comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-145">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name as shown in the following table.</span></span> <span data-ttu-id="f0e7d-146">N’utilisez pas de point (.) tout seul pour représenter le nom de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-146">Do not use a dot (.) by itself to represent the computer name.</span></span></p>
<div>
<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="f0e7d-147">Scénario</span><span class="sxs-lookup"><span data-stu-id="f0e7d-147">Scenario</span></span></p></th>
<th><p><span data-ttu-id="f0e7d-148">Paramètre UserName</span><span class="sxs-lookup"><span data-stu-id="f0e7d-148">UserName Parameter</span></span></p></th>
<th><p><span data-ttu-id="f0e7d-149">Paramètre UserGroup</span><span class="sxs-lookup"><span data-stu-id="f0e7d-149">UserGroup Parameter</span></span></p></th>
<th><p><span data-ttu-id="f0e7d-150">Paramètre ComputerName</span><span class="sxs-lookup"><span data-stu-id="f0e7d-150">ComputerName Parameter</span></span></p></th>
<th><p><span data-ttu-id="f0e7d-151">Paramètre ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="f0e7d-151">ComputerGroup Parameter</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f0e7d-152">Serveur de passerelle dans un domaine</span><span class="sxs-lookup"><span data-stu-id="f0e7d-152">Gateway server is in a domain</span></span></p></td>
<td><p><span data-ttu-id="f0e7d-153"><em>Nom_serveur</em>\<em>nom_utilisateur</em>, Localhost\<em>nom_utilisateur</em> ou .\<em>nom_utilisateur</em></span><span class="sxs-lookup"><span data-stu-id="f0e7d-153"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="f0e7d-154"><em>Nom_serveur</em>\<em>groupe_utilisateurs</em>, Localhost\<em>groupe_utilisateurs</em> ou .\<em>groupe_utilisateurs</em></span><span class="sxs-lookup"><span data-stu-id="f0e7d-154"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em>, or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="f0e7d-155">Nom complet du serveur de passerelle ou Localhost</span><span class="sxs-lookup"><span data-stu-id="f0e7d-155">Fully qualified name of gateway server, or Localhost</span></span></p></td>
<td><p><span data-ttu-id="f0e7d-156"><em>Nom_serveur</em>\<em>groupe_ordinateurs</em>, Localhost\<em>groupe_ordinateurs</em> ou .\<em>groupe_ordinateurs</em></span><span class="sxs-lookup"><span data-stu-id="f0e7d-156"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em>, or .\<em>computer_group</em></span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f0e7d-157">Serveur de passerelle dans un groupe de travail</span><span class="sxs-lookup"><span data-stu-id="f0e7d-157">Gateway server is in a workgroup</span></span></p></td>
<td><p><span data-ttu-id="f0e7d-158"><em>Nom_serveur</em>\<em>nom_utilisateur</em>, Localhost\<em>nom_utilisateur</em> ou .\<em>nom_utilisateur</em></span><span class="sxs-lookup"><span data-stu-id="f0e7d-158"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="f0e7d-159"><em>Nom_serveur</em>\<em>groupe_utilisateurs</em>, Localhost\<em>groupe_utilisateurs</em> ou .\<em>groupe_utilisateurs</em></span><span class="sxs-lookup"><span data-stu-id="f0e7d-159"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="f0e7d-160">Nom du serveur</span><span class="sxs-lookup"><span data-stu-id="f0e7d-160">Server name</span></span></p></td>
<td><p><span data-ttu-id="f0e7d-161"><em>Nom_serveur</em>\<em>groupe_ordinateurs</em>, Localhost\<em>groupe_ordinateurs</em> ou .\<em>groupe_ordinateurs</em></span><span class="sxs-lookup"><span data-stu-id="f0e7d-161"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> or .\<em>computer_group</em></span></span></p></td>
</tr>
</tbody>
</table>
</div>
<p><span data-ttu-id="f0e7d-162">Connectez-vous à un serveur de passerelle en tant qu’ordinateur cible à l’aide d’informations d’identification formatées de l’une des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-162">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="f0e7d-163"><em>Nom_serveur</em>\<em>nom_utilisateur</em></span><span class="sxs-lookup"><span data-stu-id="f0e7d-163"><em>Server_name</em>\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="f0e7d-164">Localhost\<em>nom_utilisateur</em></span><span class="sxs-lookup"><span data-stu-id="f0e7d-164">Localhost\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="f0e7d-165">.\<em>nom_utilisateur</em></span><span class="sxs-lookup"><span data-stu-id="f0e7d-165">.\<em>user_name</em></span></span></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f0e7d-166">Un identificateur de sécurité (SID) s’affiche dans une règle d’autorisation au lieu de la syntaxe <em>nom_utilisateur</em>/<em>nom_ordinateur</em> </span><span class="sxs-lookup"><span data-stu-id="f0e7d-166">A security identifier (SID) is displayed in an authorization rule instead of the syntax <em>user_name</em>/<em>computer_name</em> </span></span></p></td>
<td><p><span data-ttu-id="f0e7d-167">Soit la règle n’est plus valide, soit la requête des services de domaine Active Directory a échoué.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-167">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="f0e7d-168">Une règle d’autorisation n’est généralement pas valide dans les scénarios où le serveur de passerelle était à un moment donné dans un groupe de travail, puis par la suite joint à un domaine.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-168">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f0e7d-169">Impossible de se connecter à un ordinateur cible spécifié dans des règles d’autorisation sous forme d’adresse IPv6 avec un domaine.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-169">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span></p></td>
<td><p><span data-ttu-id="f0e7d-170">Les règles d’autorisation ne prennent pas en charge une adresse IPv6 sous forme de nom de domaine.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-170">Authorization rules do not support an IPv6 address in form of a domain name.</span></span> <span data-ttu-id="f0e7d-171">Pour spécifier un ordinateur de destination à l’aide d’une adresse IPv6, utilisez l’adresse IPv6 d’origine (qui contient des deux-points) dans la règle d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-171">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="f0e7d-172">Les adresses IPv6 de domaine et numériques (avec des signes deux-points) sont prises en charge en tant que nom d’ordinateur cible dans la page de connexion à Accès Web Windows PowerShell, mais pas dans les règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-172">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span> <span data-ttu-id="f0e7d-173">Pour plus d’informations sur les adresses IPv6, consultez <a href="https://technet.microsoft.com/library/cc781672.aspx">Fonctionnement d’IPv6</a>.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-173">For more information about IPv6 addresses, see <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a>.</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="f0e7d-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Voir aussi</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="f0e7d-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="f0e7d-175">[Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Utiliser la console web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span><span class="sxs-lookup"><span data-stu-id="f0e7d-175">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span></span>

<span data-ttu-id="f0e7d-176"><span>Afficher :</span> Hérité Protégé</span><span class="sxs-lookup"><span data-stu-id="f0e7d-176"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="f0e7d-177"><span class="stdr-votetitle">Cette page vous a-t-elle été utile ?</span></span><span class="sxs-lookup"><span data-stu-id="f0e7d-177"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="f0e7d-178">Oui Non</span><span class="sxs-lookup"><span data-stu-id="f0e7d-178">Yes No</span></span>

<span data-ttu-id="f0e7d-179">Vous avez d’autres commentaires ?</span><span class="sxs-lookup"><span data-stu-id="f0e7d-179">Additional feedback?</span></span>

<span data-ttu-id="f0e7d-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span> caractères restants</span> Soumettre Ignorer</span><span class="sxs-lookup"><span data-stu-id="f0e7d-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="f0e7d-181"><span class="stdr-thankyou">Merci !</span></span><span class="sxs-lookup"><span data-stu-id="f0e7d-181"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="f0e7d-182"><span class="stdr-appreciate">Votre avis nous intéresse.</span></span><span class="sxs-lookup"><span data-stu-id="f0e7d-182"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="f0e7d-183">Gérer votre profil</span><span class="sxs-lookup"><span data-stu-id="f0e7d-183">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="f0e7d-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span>Commentaires sur le site</a> Commentaires sur le site</span><span class="sxs-lookup"><span data-stu-id="f0e7d-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="f0e7d-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="f0e7d-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="f0e7d-186">Faites-nous part de votre expérience...</span><span class="sxs-lookup"><span data-stu-id="f0e7d-186">Tell us about your experience...</span></span>

<span data-ttu-id="f0e7d-187">La page s’est elle chargée rapidement ?</span><span class="sxs-lookup"><span data-stu-id="f0e7d-187">Did the page load quickly?</span></span>

<span data-ttu-id="f0e7d-188"><span> Oui<span> </span></span> <span> Non<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="f0e7d-188"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="f0e7d-189">Êtes-vous satisfait de la conception de la page ?</span><span class="sxs-lookup"><span data-stu-id="f0e7d-189">Do you like the page design?</span></span>

<span data-ttu-id="f0e7d-190"><span> Oui<span> </span></span> <span> Non<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="f0e7d-190"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="f0e7d-191">Donnez-nous votre avis</span><span class="sxs-lookup"><span data-stu-id="f0e7d-191">Tell us more</span></span>

-   [<span data-ttu-id="f0e7d-192">Bulletin d’informations</span><span class="sxs-lookup"><span data-stu-id="f0e7d-192">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="f0e7d-193">Contactez-nous</span><span class="sxs-lookup"><span data-stu-id="f0e7d-193">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="f0e7d-194">Déclaration de confidentialité</span><span class="sxs-lookup"><span data-stu-id="f0e7d-194">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="f0e7d-195">Conditions d'utilisation</span><span class="sxs-lookup"><span data-stu-id="f0e7d-195">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="f0e7d-196">Marques</span><span class="sxs-lookup"><span data-stu-id="f0e7d-196">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="f0e7d-197">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="f0e7d-197">© 2016 Microsoft</span></span>

<span data-ttu-id="f0e7d-198">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="f0e7d-198">© 2016 Microsoft</span></span>

<span data-ttu-id="f0e7d-199">Les codes et les scripts développés par un tiers et en rapport à ce site doivent faire l’objet d’une licence fournie par le tiers, qui indique qu’il détient son code. Microsoft n’est pas partie prenante.</span><span class="sxs-lookup"><span data-stu-id="f0e7d-199">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="f0e7d-200">Consultez les conditions d’utilisation CDN Ajax ASP.NET (http://www.asp.net/ajaxlibrary/CDN.ashx).</span><span class="sxs-lookup"><span data-stu-id="f0e7d-200">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

