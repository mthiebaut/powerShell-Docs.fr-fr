---
title:  résolution des problèmes d’accès dans Accès Web Windows PowerShell
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
---

#  Résolution des problèmes d’accès dans Accès Web Windows PowerShell

Mise à jour : 24 juin 2013

S’applique à : Windows Server 2012 R2, Windows Server 2012

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

Le tableau suivant identifie certains problèmes courants que les utilisateurs peuvent rencontrer quand ils essaient de se connecter à un ordinateur distant à l’aide d’Accès Web Windows PowerShell et inclut des suggestions de résolution.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Problème</p></th>
<th><p>Cause possible et solution</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Échec de connexion</p></td>
<td><p>L’échec peut avoir les causes suivantes.</p>
<ul>
<li><p>Il n’existe aucune règle d’autorisation qui autorise l’utilisateur à accéder à l’ordinateur, ni configuration de session spécifique sur l’ordinateur distant. La sécurité d’Accès Web Windows PowerShell est restrictive ; les utilisateurs doivent recevoir un accès explicite aux ordinateurs distants à l’aide de règles d’autorisation. Pour plus d’informations sur la création de règles d’autorisation, consultez <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell</a> dans ce guide.</p></li>
<li><p>L’utilisateur n’est pas autorisé à accéder à l’ordinateur de destination. Cet accès est déterminé par des listes de contrôle d’accès. Pour plus d’informations, consultez « Connexion à Accès Web Windows PowerShell » dans <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Utiliser la console web Windows PowerShell</a> ou le <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">blog de l’équipe Windows PowerShell</a>.</p>
<ul>
<li><p>La gestion à distance Windows PowerShell n’est peut-être pas activée sur l’ordinateur de destination. Vérifiez qu’elle est activée sur l’ordinateur auquel l’utilisateur essaie de se connecter. Pour plus d’informations, consultez « Comment configurer votre ordinateur pour la communication à distance » dans <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> dans les rubriques d’aide conceptuelle de Windows PowerShell.</p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Quand des utilisateurs essaient de se connecter à Accès Web Windows PowerShell dans une fenêtre Internet Explorer, une page <strong>Erreur de serveur interne</strong> leur est présentée ou Internet Explorer cesse de répondre. Ce problème est propre à Internet Explorer.</p></td>
<td><p>Il peut survenir pour les utilisateurs qui se sont connectés avec un nom de domaine contenant des caractères chinois ou si un ou plusieurs caractères chinois font partie du nom du serveur de passerelle. Pour contourner ce problème, l’utilisateur doit <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">installer et exécuter Internet Explorer 10</a>, puis effectuer les étapes suivantes.</p>
<ol>
<li><p>Remplacez le paramètre Internet Explorer <strong>Mode de document</strong> par <strong>Normes Internet Explorer 10</strong>.</p>
<ol>
<li><p>Appuyez sur <strong>F12</strong> pour ouvrir la console Outils de développement.</p></li>
<li><p>Dans Internet Explorer 10, cliquez sur <strong>Mode navigateur</strong>, puis sélectionnez <strong>Internet Explorer 10</strong>.</p></li>
<li><p>Cliquez sur <strong>Mode de document</strong>, puis sur <strong>Normes Internet Explorer 10</strong>.</p></li>
<li><p>Appuyez de nouveau sur <strong>F12</strong> pour fermer la console Outils de développement.</p></li>
</ol></li>
<li><p>Désactivez la configuration automatique du proxy.</p>
<ol>
<li><p>Dans Internet Explorer 10, cliquez sur <strong>Outils</strong>, puis sur <strong>Options Internet</strong>.</p></li>
<li><p>Dans la boîte de dialogue <strong>Options Internet</strong>, sous l’onglet <strong>Connexions</strong>, cliquez sur <strong>Paramètres réseau</strong>.</p></li>
<li><p>Décochez la case <strong>Détecter automatiquement les paramètres de connexion</strong>. Cliquez sur <strong>OK</strong>, puis de nouveau sur <strong>OK</strong> pour fermer la boîte de dialogue <strong>Options Internet</strong>.</p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>Impossible de se connecter à un ordinateur de groupe de travail distant</p></td>
<td><p>Si l’ordinateur de destination est membre d’un groupe de travail, utilisez la syntaxe suivante pour fournir votre nom d’utilisateur et vous connecter à l’ordinateur : &lt;<em>nom_groupe_de_travail</em>&gt;\&lt;<em>nom_utilisateur</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>Impossible de trouver les outils de gestion de serveur Web (IIS) bien que le rôle ait été installé</p></td>
<td><p>Si vous avez installé Accès Web Windows PowerShell à l’aide de l’applet de commande <span class="code">Install-WindowsFeature</span>, les outils de gestion ne sont pas installés, sauf si le paramètre <span class="code">IncludeManagementTools</span> est ajouté à l’applet de commande. Pour obtenir un exemple, consultez « Pour installer Accès Web Windows PowerShell à l’aide des applets de commande Windows PowerShell » dans <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Installer et utiliser Accès Web Windows PowerShell</a>. Vous pouvez ajouter la console du Gestionnaire des services Internet et d’autres outils de gestion IIS dont vous avez besoin en sélectionnant les outils dans une session de l’Assistant Ajout de rôles et de fonctionnalités qui cible le serveur de passerelle. Vous pouvez ouvrir l’Assistant Ajout de rôles et de fonctionnalités à partir du Gestionnaire de serveur.</p></td>
</tr>
<tr class="odd">
<td><p>Le site web Accès Web Windows PowerShell n’est pas accessible.</p></td>
<td><p>Si la Configuration de sécurité renforcée est activée dans Internet Explorer (IE ESC), vous pouvez ajouter le site web Accès Web Windows PowerShell à la liste des sites de confiance ou désactiver IE ESC. Vous pouvez désactiver IE ESC dans la vignette <strong>Propriétés</strong> de la page <strong>Serveur local</strong> dans le Gestionnaire de serveur.</p></td>
</tr>
<tr class="even">
<td><p>Le message d’erreur suivant s’affiche lors de la tentative de connexion, quand le serveur de passerelle est à la fois l’ordinateur de destination et un groupe de travail : <strong>Un échec d’autorisation s’est produit. Vérifiez que vous êtes autorisé à vous connecter à l’ordinateur de destination.</strong></p></td>
<td><p>Quand le serveur de passerelle est également le serveur de destination, et qu’il se trouve dans un groupe de travail, spécifiez le nom d’utilisateur, le nom d’ordinateur et le nom du groupe d’utilisateurs comme indiqué dans le tableau suivant. N’utilisez pas de point (.) tout seul pour représenter le nom de l’ordinateur.</p>
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
<th><p>Scénario</p></th>
<th><p>Paramètre UserName</p></th>
<th><p>Paramètre UserGroup</p></th>
<th><p>Paramètre ComputerName</p></th>
<th><p>Paramètre ComputerGroup</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Serveur de passerelle dans un domaine</p></td>
<td><p><em>Nom_serveur</em>\<em>nom_utilisateur</em>, Localhost\<em>nom_utilisateur</em> ou .\<em>nom_utilisateur</em></p></td>
<td><p><em>Nom_serveur</em>\<em>groupe_utilisateurs</em>, Localhost\<em>groupe_utilisateurs</em> ou .\<em>groupe_utilisateurs</em></p></td>
<td><p>Nom complet du serveur de passerelle ou Localhost</p></td>
<td><p><em>Nom_serveur</em>\<em>groupe_ordinateurs</em>, Localhost\<em>groupe_ordinateurs</em> ou .\<em>groupe_ordinateurs</em></p></td>
</tr>
<tr class="even">
<td><p>Serveur de passerelle dans un groupe de travail</p></td>
<td><p><em>Nom_serveur</em>\<em>nom_utilisateur</em>, Localhost\<em>nom_utilisateur</em> ou .\<em>nom_utilisateur</em></p></td>
<td><p><em>Nom_serveur</em>\<em>groupe_utilisateurs</em>, Localhost\<em>groupe_utilisateurs</em> ou .\<em>groupe_utilisateurs</em></p></td>
<td><p>Nom du serveur</p></td>
<td><p><em>Nom_serveur</em>\<em>groupe_ordinateurs</em>, Localhost\<em>groupe_ordinateurs</em> ou .\<em>groupe_ordinateurs</em></p></td>
</tr>
</tbody>
</table>
</div>
<p>Connectez-vous à un serveur de passerelle en tant qu’ordinateur cible à l’aide d’informations d’identification formatées de l’une des manières suivantes.</p>
<ul>
<li><p><em>Nom_serveur</em>\<em>nom_utilisateur</em></p></li>
<li><p>Localhost\<em>nom_utilisateur</em></p></li>
<li><p>.\<em>nom_utilisateur</em></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Un identificateur de sécurité (SID) s’affiche dans une règle d’autorisation au lieu de la syntaxe <em>nom_utilisateur</em>/<em>nom_ordinateur</em> </p></td>
<td><p>Soit la règle n’est plus valide, soit la requête des services de domaine Active Directory a échoué. Une règle d’autorisation n’est généralement pas valide dans les scénarios où le serveur de passerelle était à un moment donné dans un groupe de travail, puis par la suite joint à un domaine.</p></td>
</tr>
<tr class="even">
<td><p>Impossible de se connecter à un ordinateur cible spécifié dans des règles d’autorisation sous forme d’adresse IPv6 avec un domaine.</p></td>
<td><p>Les règles d’autorisation ne prennent pas en charge une adresse IPv6 sous forme de nom de domaine. Pour spécifier un ordinateur de destination à l’aide d’une adresse IPv6, utilisez l’adresse IPv6 d’origine (qui contient des deux-points) dans la règle d’autorisation. Les adresses IPv6 de domaine et numériques (avec des signes deux-points) sont prises en charge en tant que nom d’ordinateur cible dans la page de connexion à Accès Web Windows PowerShell, mais pas dans les règles d’autorisation. Pour plus d’informations sur les adresses IPv6, consultez <a href="https://technet.microsoft.com/library/cc781672.aspx">Fonctionnement d’IPv6</a>.</p></td>
</tr>
</tbody>
</table>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Voir aussi</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Utiliser la console web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about\_Remote\_Requirements](https://technet.microsoft.com/library/dd315349.aspx)

<span>Afficher :</span> Hérité Protégé

<span class="stdr-votetitle">Cette page vous a-t-elle été utile ?</span>
Oui Non

Vous avez d’autres commentaires ?

<span class="stdr-count"><span class="stdr-charcnt">1500</span> caractères restants</span> Soumettre Ignorer

<span class="stdr-thankyou">Merci !</span> <span class="stdr-appreciate">Votre avis nous intéresse.</span>

[Gérer votre profil](https://social.technet.microsoft.com/profile)

|

<a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Commentaires sur le site</a> Commentaires sur le site

<a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a>

Faites-nous part de votre expérience...

La page s’est elle chargée rapidement ?

<span> Oui<span> </span></span> <span> Non<span> </span></span>

Êtes-vous satisfait de la conception de la page ?

<span> Oui<span> </span></span> <span> Non<span> </span></span>

Donnez-nous votre avis

-   [Bulletin d’informations](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [Contactez-nous](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [Déclaration de confidentialité](https://privacy.microsoft.com/privacystatement)
-   |
-   [Conditions d'utilisation](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [Marques](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

© 2016 Microsoft

© 2016 Microsoft

Les codes et les scripts développés par un tiers et en rapport à ce site doivent faire l’objet d’une licence fournie par le tiers, qui indique qu’il détient son code. Microsoft n’est pas partie prenante. Consultez les conditions d’utilisation CDN Ajax ASP.NET (http://www.asp.net/ajaxlibrary/CDN.ashx).
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />



<!--HONumber=May16_HO2-->


