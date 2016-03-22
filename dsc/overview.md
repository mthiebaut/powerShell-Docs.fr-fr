# Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell 

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Cette rubrique décrit la fonctionnalité Desired State Configuration (ou « DSC ») disponible dans Windows PowerShell. Elle offre une vue d’ensemble de DSC et répertorie les diverses ressources de documentation à consulter pour vous familiariser avec DSC.

## Description de la fonctionnalité
DSC est une nouvelle plateforme de gestion de Windows PowerShell qui permet de déployer et gérer les données de configuration des services logiciels, et de gérer l’environnement dans lequel ces services s’exécutent.

DSC fournit un ensemble d’extensions de langage Windows PowerShell, de nouvelles applets de commande Windows PowerShell, ainsi que diverses ressources à l’aide desquelles vous pouvez déclarer la configuration souhaitée pour votre environnement logiciel. DSC vous permet également de mettre à jour et de gérer des configurations existantes.

## Cas pratiques
Voici quelques exemples de scénarios où vous pouvez utiliser les ressources DSC intégrées pour automatiser la configuration et la gestion d’un ensemble d’ordinateurs (également appelés « nœuds cibles ») :

* Activation ou désactivation des rôles et fonctionnalités serveur
* Gestion des entrées de Registre
* Gestion des fichiers et répertoires
* Démarrage, arrêt et gestion des processus et services
* Gestion des groupes d’utilisateurs et comptes d’utilisateur
* Déploiement de nouveaux logiciels
* Gestion des variables d’environnement
* Exécution des scripts Windows PowerShell
* Correction d’une configuration non conforme à l’état souhaité
* Détection de l’état de la configuration actuelle sur un nœud donné

## Concepts clés
DSC est une plateforme déclarative employée pour la configuration, le déploiement et la gestion des systèmes. Elle réunit trois composants principaux :

* Les [configurations](configurations.md) sont des scripts PowerShell déclaratifs qui définissent et configurent des instances de ressources. Quand une configuration est exécutée, DSC (et toutes les ressources appelées par cette configuration) « fait simplement en sorte » que le système se trouve dans l’état souhaité défini par la configuration. Les configurations DSC sont également idempotent, c’est-à-dire que le Gestionnaire de configuration local (ou « LCM ») s’assure en permanence que les machines restent configurées dans l’état déclaré dans la configuration.
* Les ressources sont les blocs de construction impératifs de DSC qui sont créés pour modéliser les divers composants d’un sous-système et implémenter le flux de contrôle de leurs différents états. Elles sont stockées dans les modules PowerShell et peuvent être créées pour modéliser des éléments généraux, comme un fichier ou un processus Windows, ou des éléments plus spécifiques, tels qu’un serveur IIS ou une machine virtuelle Azure.
* Le LCM est le moteur utilisé par DSC pour faciliter les interactions entre les ressources et les configurations. Le LCM interroge régulièrement le système, via le flux de contrôle implémenté par les ressources, pour s’assurer que le système est dans l’état déclaré dans une configuration. Si le système n’est pas dans l’état souhaité, le LCM utilise une logique supplémentaire à l’intérieur des ressources pour « faire en sorte » qu’il soit conforme à l’état déclaré dans la configuration. 

DSC inclut également plusieurs nouveaux mots clés de langage, applets de commande et outils que vous pouvez utiliser pour créer des configurations, générer plus facilement des ressources DSC, appeler des configurations et gérer le LCM. La plupart de ces applets de commande sont fournies dans le module PsDesiredStateConfig de Windows 8.1 (y compris `Start-DscConfiguration`, `Set-DscLocalConfigurationManager` et `Get-DscResource`). xDscResourceDesigner (disponible dans la [galerie PowerShell](https://www.powershellgallery.com/packages/xDSCResourceDesigner/)) regroupe plusieurs applets de commande qui simplifient le développement des ressources DSC.

## Voir aussi
* [Configurations DSC](configurations.md)
* [Ressources DSC](resources.md)
* [Configuration du Gestionnaire de configuration local](metaconfig.md)

<!--HONumber=Feb16_HO4-->
