---
title: Utilisation de Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf06f1e5-3945-47e4-98be-412f5a1f43fe
---
# Utilisation de Windows PowerShell
[!INCLUDE[wps_1](../Token/wps_1_md.md)] est un interpréteur de ligne de commande basé sur les tâches et un langage de script conçu spécialement pour l’administration du système. Basé sur .NET Framework, [!INCLUDE[wps_2](../Token/wps_2_md.md)] aide les professionnels de l’informatique et les utilisateurs avancés à contrôler et à automatiser l’administration du système d’exploitation Windows et des applications s’exécutant sur Windows.

Les ressources contenues dans cette section vous aident à découvrir [!INCLUDE[wps_2](../Token/wps_2_md.md)], les fonctionnalités fournies avec [!INCLUDE[wps_2](../Token/wps_2_md.md)] l’éditeur graphique de [!INCLUDE[wps_2](../Token/wps_2_md.md)], et l’environnement d’écriture de scripts intégré de [!INCLUDE[wps_2](../Token/wps_2_md.md)].

## Contenu de cette section
Dans cette section, vous allez découvrir [!INCLUDE[wps_2](../Token/wps_2_md.md)], comment utiliser [!INCLUDE[wps_2](../Token/wps_2_md.md)] et les nouveautés des dernières versions de [!INCLUDE[wps_2](../Token/wps_2_md.md)].

-   [Nouveautés dans Windows PowerShell](../Topic/What-s-New-in-Windows-PowerShell.md). Cette rubrique décrit les modifications apportées à [!INCLUDE[wps_2](../Token/wps_2_md.md)] 3.0 et [!INCLUDE[wps_2](../Token/wps_2_md.md)] 4.0.

-   [Prise en main de Windows PowerShell](../Topic/Getting-Started-with-Windows-PowerShell.md). Introduction et didacticiel décrivant notamment la configuration requise et fournissant des instructions d’installation et de démarrage de [!INCLUDE[wps_2](../Token/wps_2_md.md)] sur tous les systèmes d’exploitation pris en charge.

-   [Guide de l’utilisateur de Windows PowerShell](../Topic/Windows-PowerShell-User-s-Guide.md). Introduction détaillée comprenant des scripts et des scénarios concrets pour vous aider à démarrer.

-   [Environnement d’écriture de scripts intégré de Windows PowerShell &#40;ISE&#41;](../Topic/Windows-PowerShell-Integrated-Scripting-Environment--ISE-.md). Documentation relative à [!INCLUDE[wps_2](../Token/wps_2_md.md)], éditeur de script graphique [!INCLUDE[wps_2](../Token/wps_2_md.md)] et console.

-   [Vue d’ensemble de la configuration d’état souhaité (DSC) Windows PowerShell](assetId:///04c9e716-822c-40f0-8fdf-f2dda8abd888). Introduction à la configuration d’état souhaité (DSC) Windows PowerShell, nouvelle fonctionnalité de [!INCLUDE[wps_2](../Token/wps_2_md.md)] 4.0. DSC peut aider les administrateurs à mettre en place des configurations cohérentes dans les environnements Windows et sur des périphériques tels que des commutateurs réseau.

-   [Aide sur la ligne de commande PowerShell.exe](../Topic/PowerShell.exe-Command-Line-Help.md). Comment démarrer [!INCLUDE[wps_2](../Token/wps_2_md.md)] à partir de l’invite de commandes Windows et comment exécuter des commandes [!INCLUDE[wps_2](../Token/wps_2_md.md)] de base.

-   [Glossaire Windows PowerShell](../Topic/Windows-PowerShell-Glossary.md). Découvrez les termes couramment utilisés dans [!INCLUDE[wps_2](../Token/wps_2_md.md)] et sa documentation.

## Technologies connexes
[!INCLUDE[wps_2](../Token/wps_2_md.md)] fait partie d’une famille de technologies de script associées qui vous aident à automatiser la gestion à distance d’ordinateurs Windows. Pour plus d'informations sur ces technologies, cliquez sur les liens ci-dessous.

-   [Flux de travail Windows PowerShell](http://technet.microsoft.com/library/jj134242.aspx). Introduits initialement dans [!INCLUDE[psversion3](../Token/psversion3_md.md)], les flux de travail [!INCLUDE[wps_2](../Token/wps_2_md.md)] permettent aux professionnels de l’informatique et aux développeurs de tirer parti de [Windows Workflow Foundation](http://msdn.microsoft.com/library/ee342461.aspx) avec les fonctionnalités et la simplicité d’automatisation de [!INCLUDE[wps_2](../Token/wps_2_md.md)].

-   [Accès Web Windows PowerShell](http://technet.microsoft.com/library/hh831611.aspx). Initialement introduit dans [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], Accès Web [!INCLUDE[wps_2](../Token/wps_2_md.md)] joue le rôle de passerelle [!INCLUDE[wps_2](../Token/wps_2_md.md)] en fournissant une console web [!INCLUDE[wps_2](../Token/wps_2_md.md)] ciblant un ordinateur distant. Elle permet aux professionnels de l’informatique d’exécuter des commandes et des scripts [!INCLUDE[wps_2](../Token/wps_2_md.md)] à partir d’une console [!INCLUDE[wps_2](../Token/wps_2_md.md)] dans un navigateur web, sans nécessiter [!INCLUDE[wps_2](../Token/wps_2_md.md)], de logiciel de gestion à distance ou d’installation d’un plug-in de navigateur sur l’appareil client.

-   [Windows PowerShell Web Services (Extension ISS Management OData)](http://msdn.microsoft.com/library/windows/desktop/hh880865.aspx) [!INCLUDE[wps_2](../Token/wps_2_md.md)] Web Services est une infrastructure qui permet d’exposer facilement les applets de commande [!INCLUDE[wps_2](../Token/wps_2_md.md)] à travers un service web basé sur OData qui s’exécute sur un serveur web (IIS).

-   [Prendre en main la configuration d’état souhaité Windows PowerShell](assetId:///c134aa32-b085-4656-9a89-955d8ff768d0). La configuration d’état souhaité (DSC) [!INCLUDE[wps_2](../Token/wps_2_md.md)], introduite dans [!INCLUDE[psversion4](../Token/psversion4_md.md)], est une nouvelle plateforme de gestion dans [!INCLUDE[wps_2](../Token/wps_2_md.md)], qui permet de déployer et de gérer les données de configuration de services logiciels et l’environnement dans lequel ces services s’exécutent. DSC offre un ensemble d’extensions de langage, de nouvelles applets de commande et de ressources [!INCLUDE[wps_2](../Token/wps_2_md.md)] que vous pouvez utiliser pour spécifier de façon déclarative comment configurer l’état de votre environnement logiciel.

-   [Windows Management Framework 4.0 Preview](http://go.microsoft.com/fwlink/?LinkID=293881) inclut des mises à jour de [!INCLUDE[wps_2](../Token/wps_2_md.md)], [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE, [!INCLUDE[wps_2](../Token/wps_2_md.md)] Web Services (extension IIS Management OData), WinRM (Gestion à distance de Windows), WMI (Infrastructure de gestion Windows), le fournisseur WMI du Gestionnaire de serveur, ainsi qu’une nouvelle fonctionnalité pour la version 4.0, la configuration d’état souhaité (DSC) [!INCLUDE[wps_2](../Token/wps_2_md.md)]. Windows Management Framework 4.0 Preview permet d’installer et d’utiliser ces technologies sur des ordinateurs exécutant [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)] SP1 et [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)]SP1.

-   [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) inclut des mises à jour de [!INCLUDE[wps_2](../Token/wps_2_md.md)], [!INCLUDE[wps_2](../Token/wps_2_md.md)]ISE, [!INCLUDE[wps_2](../Token/wps_2_md.md)] Web Services (extension IIS Management OData), WinRM (Windows Remote Management), WMI (Infrastructure de gestion Windows) et le fournisseur WMI du Gestionnaire de serveur. Windows Management Framework 3.0 permet d’installer et d’utiliser ces technologies sur des ordinateurs exécutant [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)] SP1, Windows Server 2008 SP2 et [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)]SP1.

## Utilisation de Windows PowerShell
Pour vous lancer dans l’apprentissage de [!INCLUDE[wps_2](../Token/wps_2_md.md)], commencez par consulter les ressources suivantes :

-   [Microsoft Virtual Academy : Outils avancés et scripts avec PowerShell 3.0 Démarrage rapide](http://www.microsoftvirtualacademy.com/training-courses/advanced-tools-scripting-with-powershell-3-0-jump-start). Destiné aux professionnels de l’informatique, administrateurs et membres du support technique, ce démarrage rapide explique comment utiliser [!INCLUDE[wps_2](../Token/wps_2_md.md)] pour améliorer les fonctionnalités de gestion, automatiser les tâches redondantes et gérer l’environnement à l’échelle. Jeffrey Snover, l’inventeur de [!INCLUDE[wps_2](../Token/wps_2_md.md)], et Jason Helmick, technologiste confirmé chez Concentrated Technology, vous expliquent comment [!INCLUDE[wps_2](../Token/wps_2_md.md)] fonctionne et comment adapter [!INCLUDE[wps_2](../Token/wps_2_md.md)] à vos besoins.

-   [Microsoft Virtual Academy : Outils avancés et écriture de scripts avec PowerShell 3.0-Démarrage rapide](http://www.microsoftvirtualacademy.com/training-courses/getting-started-with-powershell-3-0-jump-start). Ce cours avancé sur [!INCLUDE[wps_2](../Token/wps_2_md.md)] s’adresse aux professionnels de l’informatique qui souhaitent transformer leurs scripts d’automatisation et de gestion en temps réel en outils et applets de commande réutilisables. Jeffrey Snover, l’architecte et l’inventeur de [!INCLUDE[wps_2](../Token/wps_2_md.md)], et Jason Helmick, informaticien, vous donnent des conseils et passent en revue les modèles et les meilleures pratiques pour créer et gérer des outils.

-   [Prise en main de Windows PowerShell](../Topic/Getting-Started-with-Windows-PowerShell.md). Introduction et didacticiel décrivant notamment la configuration requise et fournissant des instructions d’installation et de démarrage de [!INCLUDE[wps_2](../Token/wps_2_md.md)] sur tous les systèmes d’exploitation pris en charge.

-   [Guide de l’utilisateur de Windows PowerShell](../Topic/Windows-PowerShell-User-s-Guide.md). Introduction détaillée comprenant des scripts et des scénarios concrets pour vous aider à démarrer.

-   [Informations de référence sur le module Windows PowerShell Core](http://technet.microsoft.com/library/hh847741(v=wps.630).aspx). Liste alphabétique des rubriques d’aide pour les fonctionnalités de langage et les applets de commande incluses dans le moteur [!INCLUDE[wps_2](../Token/wps_2_md.md)].

-   [Automatisation de Windows et de Windows Server avec Windows PowerShell](http://technet.microsoft.com/library/dn249523.aspx). Liste alphabétique des rubriques d’aide sur les modules [!INCLUDE[wps_2](../Token/wps_2_md.md)] faisant partie de fonctionnalités ou de rôles de serveur inclus dans Windows Server et Windows Client.

-   [Automatisation de System Center avec Windows PowerShell](https://technet.microsoft.com/en-us/library/mt156962.aspx). Liste alphabétique des rubriques d’aide sur les modules [!INCLUDE[wps_2](../Token/wps_2_md.md)] inclus avec les composants de Microsoft System Center.

## Téléchargement et mise à jour de l'aide Windows PowerShell
Les rubriques suivantes décrivent comment obtenir l’aide la plus récente pour [!INCLUDE[wps_2](../Token/wps_2_md.md)] et comment l’afficher à l’invite de commandes de [!INCLUDE[wps_2](../Token/wps_2_md.md)].

-   Applet de commande [Update-Help](http://technet.microsoft.com/library/hh849720.aspx). Applet de commande [!INCLUDE[wps_2](../Token/wps_2_md.md)] qui télécharge et installe les dernières versions des rubriques d’aide pour les modules [!INCLUDE[wps_2](../Token/wps_2_md.md)] sur votre ordinateur.

    Pour plus d’informations sur le système d’aide actualisable dans [!INCLUDE[wps_2](../Token/wps_2_md.md)], notamment sur la manière de l’installer sur des ordinateurs isolés réseau, voir [about_Updatable_Help](http://technet.microsoft.com/library/hh847735.aspx), [Save-Help](http://technet.microsoft.com/library/hh849724.aspx) et [Supporting Updatable Help](http://msdn.microsoft.com/library/hh852754.aspx) (en anglais).

-   Applet de commande [Get-Help](http://technet.microsoft.com/library/hh849696(v=wps.630).aspx). Applet de commande [!INCLUDE[wps_2](../Token/wps_2_md.md)] que vous pouvez utiliser pour en savoir plus sur les applets de commande et les fournisseurs installés sur votre système.

-   Vous pouvez obtenir des notifications sur les mises à jour des fichiers d’aide publiés en vous abonnant au flux RSS suivant : [http://sxp.microsoft.com/feeds/msdntn/PowerShellHelpVersions](http://sxp.microsoft.com/feeds/msdntn/PowerShellHelpVersions).



<!--HONumber=Apr16_HO1-->


