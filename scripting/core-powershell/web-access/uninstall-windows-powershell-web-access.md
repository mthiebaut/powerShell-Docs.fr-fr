#  désinstaller Accès Web Windows PowerShell

Mise à jour : 24 juin 2013

S’applique à : Windows Server 2012 R2, Windows Server 2012

Suivez les étapes de cette rubrique pour supprimer le site web et l’application Accès Web Windows PowerShell du serveur de passerelle qui exécute Windows Server 2012 R2 ou Windows Server 2012. Avant de commencer, informez les utilisateurs de la console Web de la suppression du site Web.

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

Avant de désinstaller Accès Web Windows PowerShell du serveur de passerelle, exécutez l’applet de commande <span class="code">Uninstall-PswaWebApplication</span>pour supprimer le site web et les applications web Accès Web Windows PowerShell ou utilisez la procédure du Gestionnaire des services Internet, [Pour supprimer le site web et les applications web Accès Web Windows PowerShell à l’aide du Gestionnaire de services Internet](#BKMK_delsite)..

La désinstallation d’Accès Web Windows PowerShell ne désinstalle pas IIS ni d’autres fonctionnalités automatiquement installées, car Accès Web Windows PowerShell en a besoin pour s’exécuter. Le processus de désinstallation laisse les fonctionnalités installées dont dépendait Accès Web Windows PowerShell ; vous pouvez désinstaller ces fonctionnalités séparément si besoin.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Désinstallation (rapide) recommandée</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Les procédures de cette section vous permettent de désinstaller l’application web Accès Web Windows PowerShell et la fonctionnalité Accès Web Windows PowerShell à l’aide des applets de commande Windows PowerShell.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 1 : supprimer l’application web</span></a>

------------------------------------------------------------------------

Si vous avez défini un nom de site web personnalisé, ajoutez le paramètre <span class="code">WebsiteName</span> à votre commande et spécifiez le nom du site web. Si vous avez utilisé une application web personnalisée (et non l’application par défaut **pswa**), ajoutez le paramètre <span class="code">WebApplicationName</span> à votre commande et spécifiez le nom de l’application web.

#### Pour supprimer le site Web et les applications Web à l’aide de l’applet de commande Uninstall-PswaWebApplication

1.  Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell.

    -   Sur le Bureau Windows, cliquez avec le bouton droit sur **Windows PowerShell** dans la barre des tâches.

    -   Sur l’écran d’**accueil** de Windows, cliquez sur **Windows PowerShell**..

2.  Tapez **Uninstall-PswaWebApplication**, puis appuyez sur **Entrée**..

3.  Si vous utilisez un certificat de test, ajoutez le paramètre <span class="code">DeleteTestCertificate</span> à l’applet de commande, comme indiqué dans l’exemple suivant.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "Copier dans le Presse-papiers.")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 2 : désinstaller Accès Web Windows PowerShell</span></a>

------------------------------------------------------------------------

#### Pour désinstaller Accès Web Windows PowerShell à l’aide des applets de commande Windows PowerShell

1.  Effectuez une des opérations suivantes pour ouvrir une session Windows PowerShell avec des droits utilisateur élevés. Si une session est déjà ouverte, passez à l’étape suivante.

    -   Sur le Bureau Windows, cliquez avec le bouton droit dans la barre des tâches sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**..

    -   Sur l’écran d’**accueil** de Windows, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**..

2.  Tapez ce qui suit, puis appuyez sur **Entrée**, où *computer_name* représente le nom de l’ordinateur distant sur lequel vous souhaitez installer Accès Web Windows PowerShell, le cas échéant. Le paramètre <span class="code">–Restart</span> redémarre automatiquement les serveurs de destination si la suppression l’exige.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "Copier dans le Presse-papiers.")

        Uninstall-WindowsFeature –Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Pour supprimer des rôles et fonctionnalités d’un disque dur virtuel hors connexion, ajoutez les paramètres <span class="code">-ComputerName</span> et <span class="code">-VHD</span>. Le paramètre <span class="code">ComputerName</span> contient le nom du serveur sur lequel monter le disque dur virtuel, tandis que le paramètre <span class="code">VHD</span> contient le chemin du fichier VHD sur le serveur spécifié.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "Copier dans le Presse-papiers.")

        Uninstall-WindowsFeature –Name WindowsPowerShellWebAccess –VHD <path> -ComputerName <computer_name> -Restart

3.  Une fois l’installation terminée, vérifiez que vous avez bien supprimé Accès Web Windows PowerShell. Pour cela, ouvrez la page **Tous les serveurs** dans le Gestionnaire de serveur, sélectionnez un serveur sur lequel vous avez installé la fonctionnalité, puis examinez la vignette **Rôles et fonctionnalités** dans la page du serveur sélectionné. Vous pouvez également exécuter l’applet de commande <span class="code">Get-WindowsFeature</span> qui cible le serveur sélectionné (Get-WindowsFeature -ComputerName &lt;*nom_ordinateur*&gt;) pour afficher la liste des rôles et fonctionnalités installés sur le serveur.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Désinstallation personnalisée</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Les procédures de cette section vous permettent de désinstaller l’application web Accès Web Windows PowerShell et la fonctionnalité Accès Web Windows PowerShell en utilisant l’Assistant Suppression de rôles et de fonctionnalités dans le Gestionnaire de serveur et la console du Gestionnaire des services Internet.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 1 : supprimer l’application web</span></a>

------------------------------------------------------------------------

#### Pour supprimer le site Web et les applications Web Accès Web Windows PowerShell à l’aide du Gestionnaire de services Internet

1.  Ouvrez la console du Gestionnaire des services Internet en procédant de l’une des manières suivantes. Si elle est déjà ouverte, passez à l’étape suivante.

    -   Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows. Dans le menu **Outils** du Gestionnaire de serveur, cliquez sur **Gestionnaire des services Internet (IIS)**..

    -   Sur l’écran d’**accueil** de Windows, tapez une partie du nom **Gestionnaire des services Internet (IIS)**. Cliquez sur le raccourci quand il s’affiche dans les résultats **Applications**.

2.  Dans le volet de l’arborescence du Gestionnaire des services Internet, sélectionnez le site web qui exécute l’application web Accès Web Windows PowerShell.

3.  Dans le volet **Actions**, sous **Gérer le site web**, cliquez sur **Arrêter**..

4.  Dans le volet de l’arborescence, cliquez avec le bouton droit sur l’application web dans le site web qui exécute l’application web Accès Web Windows PowerShell, puis cliquez sur **Supprimer**..

5.  Dans le volet de l’arborescence, sélectionnez **Pools d’applications**, sélectionnez le dossier du pool d’applications Accès Web Windows PowerShell, cliquez sur **Arrêter** dans le volet **Actions**, puis cliquez sur **Supprimer** dans le volet de contenu.

6.  Fermez le Gestionnaire des services Internet (IIS).

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Remarque </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Le certificat n’est pas supprimé durant la désinstallation. Si vous avez créé un certificat auto-signé ou utilisé un certificat de test et que vous souhaitez le supprimer, supprimez le certificat dans le Gestionnaire des services Internet.</p></td>
    </tr>
    </tbody>
    </table>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Étape 2 : désinstaller Accès Web Windows PowerShell</span></a>

------------------------------------------------------------------------

#### Pour désinstaller Accès Web Windows PowerShell à l’aide de l’Assistant Suppression de rôles et de fonctionnalités

1.  Si le Gestionnaire de serveur est déjà ouvert, passez à l’étape suivante. S’il n’est pas déjà ouvert, ouvrez-le en effectuant l’une des opérations suivantes.

    -   Sur le Bureau Windows, démarrez le Gestionnaire de serveur en cliquant sur **Gestionnaire de serveur** dans la barre des tâches Windows.

    -   Sur l’écran d’**accueil** de Windows, cliquez sur **Gestionnaire de serveur**..

2.  Dans le menu **Gérer**, cliquez sur **Supprimer des rôles et fonctionnalités**..

3.  Dans la page **Sélectionner le serveur de destination**, sélectionnez le serveur ou le disque dur virtuel hors connexion sur lequel vous souhaitez supprimer la fonctionnalité. Pour sélectionner un disque dur virtuel hors connexion, choisissez d’abord le serveur sur lequel monter le disque dur virtuel, puis sélectionnez le fichier VHD. Après avoir sélectionné le serveur de destination, cliquez sur **Suivant**..

4.  Cliquez de nouveau sur **Suivant** pour passer à la page **Supprimer des fonctionnalités**.

5.  Décochez la case **Accès Web Windows PowerShell**, puis cliquez sur **Suivant**..

6.  Dans la page **Confirmer les sélections pour la suppression**, cliquez sur **Supprimer**..

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Voir aussi</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Installer et utiliser Accès Web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[Aide du Gestionnaire des services Internet 7.0](https://technet.microsoft.com/library/cc732664.aspx)

<span>Afficher :</span> Hérité Protégé

<span class="stdr-votetitle">Cette page vous a-t-elle été utile ?</span>
Oui
Non

Vous avez d’autres commentaires ?

<span class="stdr-count"><span class="stdr-charcnt">1500</span> caractères restants</span>
Soumettre
Ignorer

<span class="stdr-thankyou">Merci !</span> <span class="stdr-appreciate">Votre avis nous intéresse.</span>

[Gérer votre profil](https://social.technet.microsoft.com/profile)

|

<a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Commentaires sur le site</a>
Commentaires sur le site

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


