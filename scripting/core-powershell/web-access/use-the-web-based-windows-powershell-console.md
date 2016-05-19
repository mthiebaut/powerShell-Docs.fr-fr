#  Utiliser la console web Windows PowerShell

Mise à jour : 24 juin 2013

S’applique à : Windows Server 2012 R2, Windows Server 2012

Accès Web Windows PowerShell® permet aux utilisateurs de Windows PowerShell® de se connecter à un site web sécurisé à l’aide du protocole SSL (Secure Sockets Layer) afin d’utiliser des sessions, des applets de commande et des scripts Windows PowerShell pour gérer un ordinateur distant. La console Windows PowerShell s’exécutant dans un navigateur web, elle peut être ouverte à partir de différents périphériques clients tels que des téléphones portables, des tablettes, des bornes Internet publiques, des ordinateurs portables ou des ordinateurs partagés ou empruntés. La console web Windows PowerShell a pour cible un ordinateur distant spécifié par les utilisateurs dans le cadre du processus de connexion. Cette rubrique décrit comment se connecter et commencer à utiliser la console web Accès Web Windows PowerShell.

Elle ne décrit pas comment utiliser Windows PowerShell ou exécuter des applets de commande ou des scripts. Pour plus d’informations sur la façon d’utiliser Windows PowerShell et pour accéder à des ressources de script, consultez la section Voir aussi à la fin de cette rubrique.

Dans cette rubrique :

-   [Navigateurs et périphériques clients pris en charge](#BKMK_browser)

-   [Connexion à l’accès Web Windows PowerShell](#BKMK_sign)

-   [Déconnexion et dépassement de délais](#BKMK_timeout)

-   [Différences dans la console Windows PowerShell Web](#BKMK_web)

<a href="" id="BKMK_browser"></a>
------------------------------------------------------------------------

Accès Web Windows PowerShell prend en charge les navigateurs Internet suivants. Bien que les navigateurs mobiles ne soient pas officiellement pris en charge, nombre d’entre eux sont susceptibles de pouvoir exécuter la console web Windows PowerShell. D’autres navigateurs acceptant les cookies, exécutant JavaScript et exécutant des sites Web HTTPS sont censés fonctionner, mais n’ont pas été testés officiellement.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Navigateurs d’ordinateur de bureau pris en charge</span></a>

------------------------------------------------------------------------

-   Windows® Internet Explorer® pour Microsoft Windows® 8.0, 9.0, 10.0 et 11.0

-   Mozilla Firefox® 10.0.2

-   Google Chrome™ 17.0.963.56m pour Windows

-   Apple Safari® 5.1.2 pour Windows

-   Apple Safari 5.1.2 pour Mac OS®

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Navigateurs ou appareils mobiles testés de façon minimale</span></a>

------------------------------------------------------------------------

-   Windows Phone 7 et 7.5

-   Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)

-   Apple Safari pour système d’exploitation iPhone 5.0.1

-   Apple Safari pour système d’exploitation iPad 2 5.0.1

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configuration requise des navigateurs</span></a>

------------------------------------------------------------------------

Pour utiliser la console web Accès Web Windows PowerShell, les navigateurs doivent :

-   autoriser les cookies à partir du site web de la passerelle Accès Web Windows PowerShell ;

-   être en mesure d’ouvrir et de lire des pages HTTPS ;

-   ouvrir et exécuter des sites Web qui utilisent JavaScript.

<a href="" id="BKMK_sign"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Connexion à l’accès Web Windows PowerShell</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Votre administrateur Accès Web Windows PowerShell doit vous fournir une URL qui est l’adresse du site web de la passerelle Accès Web Windows PowerShell de votre organisation. Par défaut, l’adresse de ce site web est https://&lt;nom_serveur&gt;/pswa. Avant de vous connecter à Accès Web Windows PowerShell, vérifiez que vous disposez du nom ou de l’adresse IP de l’ordinateur distant que vous souhaitez gérer. Vous devez être un utilisateur autorisé sur l’ordinateur distant et celui-ci doit être configuré pour autoriser la gestion à distance. Pour plus d’informations sur la configuration de votre ordinateur pour autoriser la gestion à distance, consultez [Activer et utiliser des commandes distantes dans Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx). Le moyen le plus simple de configurer votre ordinateur pour autoriser la gestion à distance consiste à exécuter l’applet de commande **Enable-PSRemoting -force** sur l’ordinateur, dans une session Windows PowerShell qui a été ouverte avec des droits d’utilisateur élevés (**Exécuter en tant qu’administrateur**).

### Pour se connecter à Windows PowerShell Web Access

1.  Ouvrez le site web Accès Web Windows PowerShell dans une fenêtre ou un onglet de navigateur Internet.

2.  Dans la page de connexion à Accès Web Windows PowerShell, indiquez votre nom d’utilisateur réseau, votre mot de passe et le nom de l’ordinateur que vous souhaitez gérer (et sur lequel vous êtes un utilisateur autorisé). Si l’administrateur Accès Web Windows PowerShell vous a demandé d’utiliser un URI de site personnalisé ou de serveur proxy plutôt qu’un nom d’ordinateur, sélectionnez **URI de connexion** dans le champ **Type de connexion**, puis spécifiez l’URI.

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
    <td><ul>
    <li><p>Si l’ordinateur de destination est membre d’un groupe de travail, utilisez la syntaxe suivante pour fournir votre nom d’utilisateur et vous connecter à l’ordinateur : &lt;<em>nom_groupe_de_travail</em>&gt;\&lt;<em>nom_utilisateur</em>&gt;.</p></li>
    <li><p>Si l’ordinateur de destination est le serveur passerelle, vous pouvez spécifier <strong>localhost</strong> dans le champ <strong>Nom de l’ordinateur</strong>.</p></li>
    <li><p>Si l’ordinateur de destination est le serveur passerelle et qu’il appartient à un groupe de travail, vous pouvez spécifier <strong>localhost</strong> dans le champ <strong>Nom de l’ordinateur</strong>, mais ne spécifiez pas localhost\&lt;<em>user_name</em>&gt; dans le champ <strong>Nom d’utilisateur</strong>. Vous devez utiliser &lt;<em>nom_groupe_de_travail</em>&gt;\&lt;<em>nom_utilisateur</em>&gt;.</p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

3.  La section **Paramètres de connexion facultatifs** porte sur les exigences d’autorisation de l’ordinateur distant que vous souhaitez gérer. Pour plus d’informations sur les paramètres équivalents aux paramètres de connexion facultatifs, consultez l’[Aide de l’applet de commande Enter-PSSession](https://technet.microsoft.com/library/dd315384.aspx)..

    En général, les informations d’identification que vous passez par le biais de la passerelle Accès Web Windows PowerShell sont identiques à celles reconnues par l’ordinateur distant que vous souhaitez gérer. Toutefois, si vous souhaitez utiliser des informations d’identification différentes pour gérer l’ordinateur spécifié à l’étape 2, développez la section **Paramètres de connexion facultatifs** et spécifiez les autres informations d’identification. Sinon, passez à l’étape 6.

4.  Si l’administrateur Accès Web Windows PowerShell a créé une configuration de session personnalisée pour les utilisateurs d’Accès Web Windows PowerShell, tapez le nom de cette configuration se session dans le champ **Nom de la configuration**. Pour plus d’informations sur les configurations de sessions, consultez [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) sur le site web de Microsoft.

5.  Conservez le **Type d’authentification** **Par défaut**, sauf indication contraire de l’administrateur Accès Web Windows PowerShell.

6.  Cliquez sur **Se connecter**..

<a href="" id="BKMK_timeout"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Déconnexion et dépassement de délais</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Vous serez déconnecté de votre session web Windows PowerShell dans les cas suivants.

-   Clic sur le bouton **Se déconnecter** dans le coin inférieur droit de la console (Windows Server 2012 uniquement).

-   Clic sur le bouton **Enregistrer** ou **Quitter** dans le coin inférieur droit de la console (Windows Server 2012 R2 uniquement). Cliquez sur **Enregistrer** pour enregistrer et fermer votre session Accès Web Windows PowerShell ; vous pouvez vous reconnecter à la session ultérieurement. Quand vous vous reconnectez à Accès Web Windows PowerShell, une liste de vos sessions enregistrées s’affiche ; vous pouvez sélectionner et vous reconnecter à une session enregistrée ou démarrer une nouvelle session. Le nombre maximal de sessions ouvertes autorisées à la fois enregistrées et actives par utilisateur, est configuré par l’administrateur de la passerelle.

    Cliquez sur **Quitter** pour quitter la session Accès Web Windows PowerShell sans l’enregistrer.

-   Tentative de connexion pour gérer un autre ordinateur distant dans la même session de navigateur ou sous un nouvel onglet de la même session de navigateur. (Cela ne s’applique pas si le serveur de passerelle exécute Windows Server 2012 R2 ; l’exécution d’Accès Web Windows PowerShell sur Windows Server 2012 R2 autorise plusieurs sessions utilisateur sous de nouveaux onglets dans la même session de navigateur.) Pour plus d’informations sur la façon d’utiliser plusieurs sessions actives sur le même ordinateur, consultez « Connexion simultanée à plusieurs ordinateurs cibles » dans la section [Limitations de la console web](#BKMK_limits) de cette rubrique.

-   20 minutes d’inactivité au cours de la session. L’administrateur de la passerelle peut personnaliser le délai d’inactivité. Pour plus d’informations, consultez [Gestion des sessions](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt)..

    -   Si vous êtes déconnecté d’une session de la console web en raison d’une erreur réseau ou d’autres défaillances ou arrêts non planifiés, et non parce que vous avez vous-même fermé la session, la session Accès Web Windows PowerShell continue de s’exécuter, connectée à l’ordinateur cible, jusqu’à ce que le délai d’expiration côté client soit écoulé. Par défaut, ce délai est de 20 minutes et est configuré par l’administrateur de la passerelle. La session est déconnectée après les 20 minutes définies par défaut, ou au terme du délai spécifié par l’administrateur de la passerelle, le délai le plus court étant appliqué.

        Si le serveur de passerelle exécute Windows Server 2012 R2, Accès Web Windows PowerShell permet aux utilisateurs de se reconnecter ultérieurement aux sessions enregistrées. Toutefois, vous ne pouvez pas accéder à ces sessions ou vous y reconnecter tant que le délai d’expiration spécifié par l’administrateur de la passerelle n’est pas écoulé.

-   Fermeture de la fenêtre ou de l’onglet de navigateur.

-   Mise hors tension ou déconnexion du périphérique client sur lequel le navigateur s’exécute.

-   Exécution de la commande **Exit** dans la console web. Cette commande ne fonctionne pas si la configuration de session à laquelle vous êtes connecté est configurée pour prendre en charge le mode [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) ou si elle est dans une instance d’exécution restreinte.

Si vous souhaitez vous reconnecter, rouvrez la page web Accès Web Windows PowerShell et connectez-vous en effectuant les étapes de la section [Pour se connecter à Accès Web Windows PowerShell](#BKMK_signin) de cette rubrique.

<a href="" id="BKMK_web"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Différences dans la console Windows PowerShell Web</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Une fois que vous vous êtes connecté à Accès Web Windows PowerShell, une console web Windows PowerShell s’ouvre dans la fenêtre ou l’onglet de votre navigateur. La console étant connectée à l’ordinateur distant que vous avez spécifié lors du processus de connexion, seuls les applets de commande ou scripts Windows PowerShell disponibles sur cet ordinateur distant peuvent être utilisés dans la console. Cette section décrit d’autres limitations des consoles Accès Web Windows PowerShell et les différences entre les consoles Accès Web Windows PowerShell et la console **PowerShell.exe** installée.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Différences fonctionnelles avec PowerShell.exe</span></a>

------------------------------------------------------------------------

La plupart des fonctionnalités hôtes de Windows PowerShell sont disponibles dans la console web Accès Web Windows PowerShell, mais certaines fonctionnalités ne sont pas accessibles.

-   <span class="label">Affichage imbriqué de la progression.</span>  Accès Web Windows PowerShell affiche une interface utilisateur graphique de progression pour les applets de commande qui indiquent la progression, mais seules les informations de progression de niveau supérieur sont affichées.

-   <span class="label">Modification de la couleur d’entrée.</span>  La couleur d’entrée (premier plan et arrière-plan) ne peut pas être modifiée. Le style des messages de sortie, d’avertissement, de commentaires et d’erreur peut être modifié en exécutant un script.

-   <span class="label">PSHostRawUserInterface.</span>  Accès Web Windows PowerShell est implémenté sur la gestion à distance Windows PowerShell et utilise une instance d’exécution distante. Accès Web Windows PowerShell n’implémente pas certaines méthodes dans cette interface (par exemple les commandes qui écrivent dans la console Windows). Les commandes telles que **PowerTab** ne fonctionnent pas dans Accès Web Windows PowerShell.

-   <span class="label">Touches de fonction.</span>  Accès Web Windows PowerShell ne prend pas en charge certaines touches de fonction, souvent car ces commandes sont réservées par le navigateur.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Touche de fonction non prise en charge</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ctrl+C</p></td>
<td><p>Dans Accès Web Windows PowerShell, <strong>Ctrl+C</strong> est utilisé par le navigateur pour copier du contenu. La console propose un bouton <strong>Annuler</strong>, et les utilisateurs peuvent également utiliser <strong>Ctrl+Q</strong> pour annuler des commandes.</p></td>
</tr>
<tr class="even">
<td><p>Alt-Espace, e, l</p></td>
<td><p>Parcourir la mémoire tampon d’écran</p></td>
</tr>
<tr class="odd">
<td><p>Alt+Espace, e, f</p></td>
<td><p>Rechercher du texte dans la mémoire tampon d’écran</p></td>
</tr>
<tr class="even">
<td><p>Alt+Espace, e, k</p></td>
<td><p>Sélectionner du texte à copier à partir de la mémoire tampon d’écran</p></td>
</tr>
<tr class="odd">
<td><p>Alt+Espace, e, p</p></td>
<td><p>Coller le contenu du Presse-papiers dans la console Windows PowerShell</p></td>
</tr>
<tr class="even">
<td><p>Alt+Espace, c</p></td>
<td><p>Fermer la console Windows PowerShell</p></td>
</tr>
<tr class="odd">
<td><p>Ctrl+Pause</p></td>
<td><p>Forcer la fermeture de la fenêtre Windows PowerShell</p></td>
</tr>
<tr class="even">
<td><p>Ctrl+Origine</p></td>
<td><p>Supprimer à partir du début de la ligne de commande actuelle</p></td>
</tr>
<tr class="odd">
<td><p>Ctrl+Fin</p></td>
<td><p>Supprimer jusqu’à la fin de la ligne de commande</p></td>
</tr>
<tr class="even">
<td><p>F1</p></td>
<td><p>Déplacer le curseur d’un caractère vers la droite sur la ligne de commande</p></td>
</tr>
<tr class="odd">
<td><p>F2</p></td>
<td><p>Créer une commande en copiant la dernière commande jusqu’au caractère que vous tapez</p></td>
</tr>
<tr class="even">
<td><p>F3</p></td>
<td><p>Terminer la ligne de commande avec le contenu de votre dernière ligne de commande</p></td>
</tr>
<tr class="odd">
<td><p>F4</p></td>
<td><p>Supprimer des caractères à la position du curseur</p></td>
</tr>
<tr class="even">
<td><p>F5</p></td>
<td><p>Parcourir l’historique des commandes (des plus récentes au plus anciennes). Pour accéder aux commandes de l’historique dans Accès Web Windows PowerShell, cliquez sur les boutons de défilement <strong>Historique</strong> dans la console web.</p></td>
</tr>
<tr class="odd">
<td><p>F7</p></td>
<td><p>Sélectionner de manière interactive une commande dans votre historique de commandes</p></td>
</tr>
<tr class="even">
<td><p>F8</p></td>
<td><p>Parcourir l’historique en affichant les commandes qui correspondent au texte actif</p></td>
</tr>
<tr class="odd">
<td><p>F9</p></td>
<td><p>Exécuter une commande numérotée spécifique de l’historique</p></td>
</tr>
<tr class="even">
<td><p>Page précédente</p></td>
<td><p>Exécuter la première commande de l’historique</p></td>
</tr>
<tr class="odd">
<td><p>Page suivante</p></td>
<td><p>Exécuter la dernière commande de l’historique</p></td>
</tr>
<tr class="even">
<td><p>Alt+F7</p></td>
<td><p>Effacer la liste de l’historique de commandes</p></td>
</tr>
</tbody>
</table>

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitations de la console web</span></a>

------------------------------------------------------------------------

-   <span class="label">Double-saut.</span>   Vous pouvez rencontrer la limitation relative au double-saut (connexion à un second ordinateur à partir de la première connexion) si vous tentez de créer ou de travailler sur une nouvelle session à l’aide d’Accès Web Windows PowerShell. Accès Web Windows PowerShell utilise une instance d’exécution à distance et, actuellement, **PowerShell.exe** ne prend pas en charge l’établissement d’une connexion à distance vers un second ordinateur à partir d’une instance d’exécution à distance. Si vous essayez de vous connecter à un second ordinateur distant à partir d’une connexion existante, par exemple à l’aide de l’applet de commande **Enter-PSSession**, vous pouvez recevoir différents messages d’erreur, tels que « Impossible d’obtenir les ressources réseau ».

    Pour éviter les erreurs de double-saut, votre administrateur doit configurer l’authentification CredSSP dans l’environnement réseau de votre organisation. Pour plus d’informations sur la configuration de l’authentification CredSSP, consultez [CredSSP pour l’accès à distance de second saut](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) sur le site web de Microsoft. Vous pouvez également fournir des informations d’identification explicites quand vous voulez gérer un second ordinateur distant ; il est peu probable que des informations d’identification implicites autorisent le second saut.

-   Accès Web Windows PowerShell utilise et présente les mêmes limitations qu’une session Windows PowerShell à distance. Les commandes qui appellent directement des API de console Windows, telles que celles pour éditeurs basés sur console ou pour programmes de menu basé sur du texte, ne fonctionnent pas car les commandes ne lisent ni n’écrivent dans des canaux d’entrée, de sortie et d’erreur. Par conséquent, les commandes qui lancent un fichier exécutable, telles que **notepad.exe**, ou qui affichent une interface utilisateur graphique, telles que <span class="code">OpenGridView</span> ou <span class="code">ogv</span>, ne fonctionnent pas. Votre expérience est affectée par ce comportement ; pour vous, Accès Web Windows PowerShell semble ne pas répondre à votre commande.

-   La saisie semi-automatique par le biais de la touche Tab ne fonctionne pas dans une configuration de session avec une instance d’exécution restreinte ou en mode **NoLanguage**. Bien que les administrateurs puissent configurer une session pour prendre en charge la saisie semi-automatique via la touche TAB, cette pratique est déconseillée pour des raisons de sécurité car elle peut exposer les informations suivantes aux utilisateurs non autorisés :

    -   chemins d’accès de système de fichiers internes ;

    -   dossiers partagés sur les ordinateurs internes ;

    -   variables dans l’instance d’exécution ;

    -   types chargés ou espaces de noms du .NET Framework ;

    -   Variables d’environnement

-   Les utilisateurs connectés à une configuration de session **NoLanguage** ou à une instance d’exécution restreinte dans Accès Web Windows PowerShell ne peuvent pas exécuter la commande **Quitter** pour mettre fin à la session. Pour se déconnecter, les utilisateurs doivent cliquer sur **Se déconnecter** dans la page de console.

-   <span class="label">Connexion simultanée à plusieurs ordinateurs cibles.</span>   Si le serveur de passerelle exécute Windows Server 2012, Accès Web Windows PowerShell n’autorise qu’une seule connexion d’ordinateur distant par session de navigateur. Il n’autorise pas les utilisateurs à se connecter à plusieurs ordinateurs distants à l’aide d’onglets de navigateur distincts. Quand vous ouvrez un nouvel onglet ou une nouvelle fenêtre de navigateur, Accès Web Windows PowerShell vous invite à mettre fin à votre session active et à démarrer une nouvelle session, afin que vous puissiez vous connecter au nouvel (ou au même) ordinateur distant. Si toutefois vous souhaitez ouvrir plusieurs sessions sur différents ordinateurs distants, une fonctionnalité d’Internet Explorer vous permet d’établir une nouvelle session. Pour démarrer une nouvelle session de navigateur dans Internet Explorer, appuyez sur **Alt**, ouvrez le menu **Fichier**, puis sélectionnez **Nouvelle session**. Ensuite, ouvrez le site web Accès Web Windows PowerShell dans la nouvelle session et connectez-vous pour accéder à un autre ordinateur distant.

    Quand la passerelle Accès Web Windows PowerShell s’exécute sur Windows Server 2012 R2, les utilisateurs peuvent ouvrir plusieurs connexions à des ordinateurs distants dans différents onglets de navigateur. Si vous souhaitez ouvrir plusieurs connexions à un ordinateur distant à l’aide de la console web Windows PowerShell, vérifiez auprès de votre administrateur de passerelle Accès Web Windows PowerShell que cette fonctionnalité est prise en charge par le serveur de passerelle.

-   <span class="label">Sessions Windows PowerShell persistantes (reconnexion).</span>   Une fois le délai d’expiration de la passerelle Accès Web Windows PowerShell atteint, la connexion à distance entre la passerelle et l’ordinateur cible est fermée. Ceci arrête toutes les applets de commande et scripts en cours. Il est conseillé d’utiliser l’infrastructure **-Job** Windows PowerShell quand vous effectuez des tâches longues, de manière à pouvoir démarrer des travaux, vous déconnecter de l’ordinateur, vous reconnecter ultérieurement et conserver les travaux. L’un des autres avantages offerts par les applets de commande **-Job** est la possibilité de les démarrer à l’aide d’Accès Web Windows PowerShell, de se déconnecter, puis de se reconnecter ultérieurement en exécutant Accès Web Windows PowerShell ou un autre hôte (tel que l’environnement d’écriture de scripts intégré de Windows PowerShell®).

-   <span class="label">Redimensionnement de la console.</span>   Vous pouvez redimensionner la fenêtre de console **PowerShell.exe** des trois manières suivantes :

    -   en faisant glisser et en ajustant la taille de la fenêtre de console avec la souris ;

    -   en modifiant les propriétés de hauteur et de largeur à l’aide d’une interface utilisateur graphique destinée aux propriétés de la console ;

    -   en modifiant la hauteur et la largeur des fenêtres de console avec une applet de commande.

        La fenêtre de console Accès Web Windows PowerShell peut être configurée comme suit à l’aide des applets de commande. Dans l’exemple suivant, un utilisateur affecte la valeur **20** à la largeur de la console Accès Web Windows PowerShell.

        [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_778d5e55-9195-4bd7-b313-d1fbca7876e4'); "Copier dans le Presse-papiers.")

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        Vous pouvez modifier la hauteur de la console d’une manière similaire.

        D’autres exemples de personnalisation de l’affichage de la console sont disponibles sur le [blog de l’équipe Windows PowerShell](http://blogs.msdn.com/b/powershell/)..

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Voir aussi</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Référence pour les applets de commande Windows PowerShell](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell sur Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[Référentiel du Centre de scripts TechNet](http://gallery.technet.microsoft.com/scriptcenter)
[Centre de scripts - Blog « Hey, Scripting Guy! »](https://technet.microsoft.com/scriptcenter)
[Blog de l’équipe Windows PowerShell](http://blogs.msdn.com/b/powershell/)

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


