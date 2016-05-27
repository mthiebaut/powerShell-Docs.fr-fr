---
title:   Configuration du Gestionnaire de configuration local
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Configuration du Gestionnaire de configuration local

> S’applique à : Windows PowerShell 5.0

Le Gestionnaire de configuration local (ou « LCM ») est le moteur de la fonctionnalité DSC (Desired State Configuration) de Windows PowerShell. Le LCM s’exécute sur chaque nœud cible pour analyser et appliquer les configurations transmises au nœud. Il a également en charge plusieurs autres opérations liées à DSC, notamment les suivantes.

* Déterminer le mode d’actualisation (push ou pull).
* Spécifier la fréquence à laquelle un nœud extrait et applique les configurations.
* Associer le nœud à des serveurs collecteurs.
* Spécifier des configurations partielles.

Un type spécial de configuration vous permet de configurer le LCM pour définir chacun de ces comportements. Les sections qui suivent décrivent comment configurer le LCM.

> **Remarque** : Cette rubrique concerne le gestionnaire de configuration local introduit dans Windows PowerShell 5.0. Pour plus d’informations sur la configuration du LCM dans Windows PowerShell 4.0, consultez [Gestionnaire de configuration local DSC Windows PowerShell 4.0](metaconfig4.md).

## Création et application d’une configuration du LCM

Pour configurer le LCM, vous devez créer et exécuter un type spécial de configuration. Pour spécifier une configuration du LCM, utilisez l’attribut DscLocalConfigurationManager. L’exemple ci-dessous montre une configuration simple qui définit le LCM en mode push.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
} 
```

Appelez et exécutez la configuration pour créer le fichier MOF de configuration, comme pour une configuration standard. Pour plus d’informations sur la création d’un fichier MOF de configuration, consultez [Compilation de la configuration](configurations#compiling-the-configuration). À la différence d’une configuration standard, vous n’appliquez pas de configuration du gestionnaire de configuration local en appelant l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx). Appelez plutôt l’applet de commande [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) en spécifiant le chemin du fichier MOF de configuration comme paramètre. Après avoir appliqué la configuration, vous pouvez afficher les propriétés du gestionnaire de configuration local en appelant l’applet de commande [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).

Une configuration du LCM peut contenir des blocs pour un ensemble limité de ressources uniquement. Dans l’exemple précédent, **Settings** est la seule ressource appelée. Voici les autres ressources disponibles :

* **ConfigurationRepositoryWeb** : spécifie un serveur collecteur HTTP pour les configurations. 
* **ConfigurationRepositoryShare** : spécifie un serveur collecteur SMB pour les configurations.
* **ResourceRepositoryWeb** : spécifie un serveur collecteur HTTP pour les modules.
* **ResourceRepositoryShare** : spécifie un serveur collecteur SMB pour les modules.
* **ReportServerWeb** : spécifie un serveur collecteur HTTP auquel les rapports sont envoyés.
* **PartialConfiguration** : spécifie des configurations partielles.

## Paramètres de base

À part les propriétés relatives aux serveurs collecteurs et aux configurations partielles, toutes les propriétés du gestionnaire de configuration local se définissent dans un bloc **Settings**. Un bloc **Settings** définit les propriétés suivantes.

|  Propriété  |  Type  |  Description   | 
|----------- |------- |--------------- | 
| ConfigurationModeFrequencyMins| UInt32| Fréquence, en minutes, à laquelle la configuration actuelle est vérifiée et appliquée. Cette propriété est ignorée si la propriété ConfigurationMode est définie sur ApplyOnly. La valeur par défaut est 15. __Remarque__ : La valeur de cette propriété doit être un multiple de la valeur de la propriété __RefreshFrequencyMins__, ou la valeur de la propriété __RefreshFrequencyMins__ doit être un multiple de la valeur de cette propriété.| 
| RebootNodeIfNeeded| bool| Définissez cette propriété sur __$true__ pour redémarrer automatiquement le nœud après l’application d’une configuration nécessitant un redémarrage. Sinon, vous devez redémarrer manuellement le nœud. La valeur par défaut est __$false__.| 
| ConfigurationMode| string | Spécifie de quelle façon le LCM applique réellement la configuration aux nœuds cibles. Cette propriété peut avoir différentes valeurs. La valeur __ApplyOnly__ indique à DSC d’appliquer la configuration et de ne faire aucune autre opération, sauf si une nouvelle configuration est transmise au nœud cible ou est extraite d’un serveur. Après l’application initiale d’une nouvelle configuration, DSC ne vérifie pas si le nœud cible est encore dans l’état précédemment configuré. La valeur __ApplyAndMonitor__ (valeur par défaut) indique au LCM d’appliquer chaque nouvelle configuration. Après l’application initiale d’une nouvelle configuration, DSC vérifie si le nœud cible est dans l’état souhaité et, si ce n’est pas le cas, il signale l’écart dans les journaux. La valeur __ApplyAndAutoCorrect__ indique à DSC d’appliquer chaque nouvelle configuration. Après l’application initiale d’une nouvelle configuration, DSC vérifie si le nœud cible est dans l’état souhaité et, si ce n’est pas le cas, il signale l’écart dans les journaux, puis il réapplique la configuration actuelle.| 
| ActionAfterReboot| string| Spécifie le comportement après un redémarrage survenant pendant l’application d’une configuration. Il y a deux valeurs possibles. __ContinueConfiguration__ : l’application de la configuration actuelle se poursuit. __StopConfiguration__ : l’application de la configuration actuelle s’arrête.| 
| RefreshMode| string| Spécifie de quelle façon le LCM obtient les configurations. Les valeurs possibles sont les suivantes : __Disabled__ : désactive les configurations DSC pour ce nœud. __Push__ : les configurations sont exécutées en appelant l’applet de commande Start-DscConfiguration. Chaque configuration est immédiatement appliquée au nœud. Il s’agit de la valeur par défaut. __Pull__ : le nœud est configuré pour vérifier régulièrement les configurations disponibles sur un serveur collecteur. Si cette propriété est définie sur Pull, vous devez spécifier un serveur collecteur dans un bloc __ConfigurationRepositoryWeb__ ou __ConfigurationRepositoryShare__. Pour plus d’informations sur les serveurs collecteurs, consultez [Configuration d’un serveur collecteur DSC](pullServer.md).| 
| CertificateID| string| GUID qui identifie le certificat utilisé pour sécuriser les informations d’identification d’accès à la configuration. Pour plus d’informations, consultez [Want to secure credentials in Windows PowerShell Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)? (Sécuriser les informations d’identification dans DSC Windows PowerShell).| 
| ConfigurationID| string| GUID qui identifie le fichier de configuration à obtenir d’un serveur collecteur en mode pull. Le nœud extrait les configurations en mode pull du serveur collecteur si le nom du fichier de configuration MOF est ConfigurationID.mof. __Remarque__ : Si vous définissez cette propriété, vous ne pouvez pas inscrire le nœud auprès d’un serveur collecteur en utilisant __RegistryKeys__. Pour plus d’informations, consultez [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md).| 
| RefreshFrequencyMins| Uint32| Fréquence en minutes à laquelle le LCM interroge un serveur collecteur pour obtenir les configurations mises à jour. Cette valeur est ignorée si le LCM n’est pas configuré en mode pull. La valeur par défaut est 30. __Remarque__ : La valeur de cette propriété doit être un multiple de la valeur de la propriété __ConfigurationModeFrequencyMins__, ou la valeur de la propriété __ConfigurationModeFrequencyMins__ doit être un multiple de la valeur de cette propriété.| 
| AllowModuleOverwrite| bool| Définissez cette propriété sur __$TRUE__ si vous autorisez le remplacement des configurations existantes sur le nœud cible par les nouvelles configurations téléchargées du serveur de configuration. Autrement, définissez-la sur $FALSE.| 
| DebugMode| string| Les valeurs possibles sont __None (valeur par défaut)__, __ForceModuleImport__ et __All__. <ul><li>Définissez cette propriété sur __None__ pour utiliser les ressources mises en cache. Il s’agit de la valeur par défaut qui doit être utilisée dans les scénarios de production.</li><li>Définissez cette propriété sur __ForceModuleImport__ pour forcer le gestionnaire de configuration local à recharger tous les modules de ressources DSC, même ceux ayant déjà été chargés et mis en cache. Ce comportement diminue les performances de DSC, car chaque module utilisé est systématiquement rechargé. En général, vous utilisez cette valeur lors du débogage d’une ressource.</li><li>Dans cette version, __All__ est équivalent à __ForceModuleImport__</li></ul> |
| ConfigurationDownloadManagers| CimInstance[]| Obsolète. Utilisez des blocs __ConfigurationRepositoryWeb__ et __ConfigurationRepositoryShare__ pour définir les serveurs collecteurs de configurations.| 
| ResourceModuleManagers| CimInstance[]| Obsolète. Utilisez des blocs __ResourceRepositoryWeb__ et __ResourceRepositoryShare__ pour définir les serveurs collecteurs de ressources.| 
| ReportManagers| CimInstance[]| Obsolète. Utilisez des blocs __ReportServerWeb__ pour définir les serveurs collecteurs de rapports.| 
| PartialConfigurations| CimInstance| Non implémentée. Ne pas utiliser.| 
| StatusRetentionTimeInDays | UInt32| Nombre de jours pendant lesquels le LCM conserve l’état de la configuration actuelle.| 

## Serveurs collecteurs

Un serveur collecteur est un service web OData ou un partage SMB qui est utilisé comme emplacement central des fichiers DSC. La configuration du LCM permet de définir les types de serveurs collecteurs suivants :

* **Serveur de configuration** : référentiel pour les configurations DSC. Définissez les serveurs de configuration à l’aide des blocs **ConfigurationRepositoryWeb** (pour les serveurs web) et **ConfigurationRepositoryShare** (pour les serveurs SMB).
* Serveur de ressources : référentiel pour les ressources DSC, packagées comme modules PowerShell. Définissez les serveurs de ressources à l’aide des blocs **ResourceRepositoryWeb** (pour les serveurs web) et **ResourceRepositoryShare** (pour les serveurs SMB).
* Serveur de rapports : service vers lequel DSC envoie les données de rapport. Définissez les serveurs de rapports à l’aide des blocs **ReportServerWeb**. Un serveur de rapports doit être un service web.

Pour plus d’informations sur la configuration et l’utilisation des serveurs collecteurs, consultez [Configuration d’un serveur collecteur DSC](pullServer.md).

## Blocs de serveur de configuration

Pour définir un serveur de configuration web, créez un bloc **ConfigurationRepositoryWeb**. Un bloc **ConfigurationRepositoryWeb** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---| 
|AllowUnsecureConnection|bool|Définissez cette propriété sur **$TRUE** pour autoriser le nœud à se connecter au serveur sans authentification. Définissez-la sur **$FALSE** pour rendre l’authentification obligatoire.|
|CertificateID|string|GUID qui identifie le certificat utilisé pour l’authentification auprès du serveur.|
|ConfigurationNames|String[]|Tableau des noms des configurations à extraire par le nœud cible. Ils sont utilisés uniquement si le nœud a été inscrit auprès du serveur collecteur à l’aide d’une propriété **RegistrationKey**. Pour plus d’informations, consultez [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md).|
|RegistrationKey|string|GUID sous lequel le nœud est inscrit auprès du serveur collecteur. Pour plus d’informations, consultez [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md).|
|ServerURL|string|URL du serveur de configuration.|

Pour définir un serveur de configuration SMB, créez un bloc **ConfigurationRepositoryShare**. Un bloc **ConfigurationRepositoryShare** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---|
|Credential|MSFT_Credential|Informations d’identification utilisées pour l’authentification auprès du partage SMB.|
|SourcePath|string|Chemin du partage SMB.|

## Blocs de serveur de ressources

Pour définir un serveur de ressources web, créez un bloc **ResourceRepositoryWeb**. Un bloc **ResourceRepositoryWeb** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---|
|AllowUnsecureConnection|bool|Définissez cette propriété sur **$TRUE** pour autoriser le nœud à se connecter au serveur sans authentification. Définissez-la sur **$FALSE** pour rendre l’authentification obligatoire.|
|CertificateID|string|GUID qui identifie le certificat utilisé pour l’authentification auprès du serveur.|
|RegistrationKey|string|GUID qui identifie le nœud inscrit auprès du serveur collecteur. Pour plus d’informations, consultez « Comment inscrire un nœud auprès d’un serveur collecteur DSC ».|
|ServerURL|string|URL du serveur de configuration.|
 
Pour définir un serveur de ressources SMB, créez un bloc **ResourceRepositoryShare**. Un bloc **ResourceRepositoryShare** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---|
|Credential|MSFT_Credential|Informations d’identification utilisées pour l’authentification auprès du partage SMB.|
|SourcePath|string|Chemin du partage SMB.|

## Blocs de serveur de rapports

Un serveur de rapports doit être un service web OData. Pour définir un serveur de rapports, créez un bloc **ReportServerWeb**. Un bloc **ReportServerWeb** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---| 
|AllowUnsecureConnection|bool|Définissez cette propriété sur **$TRUE** pour autoriser le nœud à se connecter au serveur sans authentification. Définissez-la sur **$FALSE** pour rendre l’authentification obligatoire.|
|CertificateID|string|GUID qui identifie le certificat utilisé pour l’authentification auprès du serveur.|
|RegistrationKey|string|GUID qui identifie le nœud inscrit auprès du serveur collecteur. Pour plus d’informations, consultez « Comment inscrire un nœud auprès d’un serveur collecteur DSC ».|
|ServerURL|string|URL du serveur de configuration.|

## Configurations partielles

Pour définir une configuration partielle, créez un bloc **PartialConfiguration**. Pour plus d’informations sur les configurations partielles, consultez [Configurations partielles DSC](partialConfigs.md). Un bloc **PartialConfiguration** définit les propriétés suivantes.

|Propriété|Type|Description|
|---|---|---| 
|ConfigurationSource|string[]|Tableau des noms des serveurs de configuration, définis précédemment dans les blocs **ConfiguratoinRepositoryWeb** et **ConfigurationRepositoryShare**, à partir desquels la configuration partielle est extraite.|
|DependsOn|string{}|Liste des noms des autres configurations à exécuter avant l’application de cette configuration partielle.|
|Description|string|Texte qui décrit la configuration partielle.|
|ExclusiveResources|string[]|Tableau des ressources exclusives de cette configuration partielle.|
|RefreshMode|string|Spécifie de quelle façon DCS obtient cette configuration partielle. Les valeurs possibles sont les suivantes : **Disabled** : désactive cette configuration partielle. **Push** : la configuration partielle est transmise au nœud en appelant l’applet de commande [Publish-DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx). Une fois que toutes les configurations partielles pour le nœud ont été obtenues d’un serveur en mode push ou pull, la configuration peut être démarrée en appelant `Start-DscConfiguration –UseExisting`. Il s’agit de la valeur par défaut. **Pull** : le nœud est configuré pour vérifier régulièrement si la configuration partielle est disponible sur un serveur collecteur. Si cette propriété est définie sur « Pull », vous devez spécifier un serveur collecteur à l’aide de la propriété **ConfigurationSource**. Pour plus d’informations sur les serveurs collecteurs, consultez [Configuration d’un serveur collecteur DSC](pullServer.md).|
|ResourceModuleSource|string[]|Tableau des noms des serveurs de ressources à partir desquels télécharger les ressources nécessaires pour cette configuration partielle. Ces noms doivent être ceux des serveurs de ressources définis précédemment dans les blocs **ResourceRepositoryWeb** et **ResourceRepositoryShare**.|

## Voir aussi 

### Concepts
[Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell](overview.md)
 
[Configuration d’un serveur collecteur DSC](pullServer.md) 

[Gestionnaire de configuration local de la configuration d’état souhaité Windows PowerShell 4.0](metaConfig4.md) 

### Autres ressources
[Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) 

[Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md) 



<!--HONumber=May16_HO3-->


