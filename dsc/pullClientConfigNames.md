---
title:   Configuration d’un client collecteur à l’aide du nom de configuration
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Configuration d’un client collecteur à l’aide du nom de configuration

> S’applique à : Windows PowerShell 5.0

Chaque nœud cible doit recevoir l’instruction d’utiliser le mode par extraction ainsi que l’URL où contacter le serveur collecteur pour obtenir des configurations. Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires. Pour le configurer, vous créez un type spécial de configuration, avec l’attribut **DSCLocalConfigurationManager**. Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](metaConfig.md).

> **Remarque** : Cette rubrique s’applique à PowerShell 5.0. Pour des informations sur la configuration d’un client collecteur dans PowerShell 4.0, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0](pullClientConfigID4.md)

Le script suivant configure le gestionnaire de configuration local de façon à extraire des configurations d’un serveur nommé « CONTOSO-PullSrv » :

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
            
        }      
    }
}
PullClientConfigID
```

Dans le script, le bloc **ConfigurationRepositoryWeb** définit le serveur collecteur. La propriété **ServerURL** spécifie le point de terminaison pour le serveur collecteur.

La propriété **RegistrationKey** est une clé partagée entre tous les nœuds clients d’un serveur collecteur et ce serveur collecteur. La même valeur est stockée dans un fichier sur le serveur collecteur. La propriété **ConfigurationNames** spécifie le nom de la configuration destinée au nœud client. Sur le serveur collecteur, le fichier MOF de configuration pour ce nœud client doit être nommé *ConfigurationNames*.mof, où *ConfigurationNames* correspond à la valeur de la propriété **ConfigurationNames** que vous définissez dans cette métaconfiguration.

Quand le script s’exécute, il crée un dossier de sortie nommé **PullClientConfigID** et y place un fichier MOF de métaconfiguration. Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.

Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration. Par exemple : `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

> **Remarque** : Les clés d’enregistrement fonctionnent uniquement avec les serveurs collecteurs web. Vous devez encore utiliser **ConfigurationID** avec un serveur collecteur SMB. Pour plus d’informations sur la configuration d’un serveur collecteur à l’aide de **ConfigurationID**, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md)

## Serveurs de ressources et de rapports

Si vous spécifiez uniquement un bloc **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** dans votre configuration du gestionnaire de configuration local (comme dans l’exemple précédent), le client collecteur extrait des ressources du serveur spécifié, mais il ne lui envoie pas de rapport. Vous pouvez utiliser un serveur collecteur unique pour les configurations, les ressources et les rapports, mais vous devez créer un bloc **ReportRepositoryWeb** pour configurer les rapports. L’exemple suivant montre une métaconfiguration qui configure un client de façon à extraire les configurations et les ressources, et à envoyer des données de rapport à un seul serveur collecteur.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```


Vous pouvez également spécifier différents serveurs collecteurs pour les ressources et les rapports. Pour spécifier un serveur de ressources, vous utilisez un bloc **ResourceRepositoryWeb** (pour un serveur collecteur web) ou **ResourceRepositoryShare** (pour un serveur collecteur SMB).
Pour spécifier un serveur de rapports, vous utilisez un bloc **ReportRepositoryWeb**. Un serveur de rapports ne peut pas être un serveur SMB.
La métaconfiguration suivante configure un client collecteur de façon à obtenir sa configuration de **CONTOSO-PullSrv** et ses ressources de **CONTOSO-ResourceSrv**, et à envoyer des rapports d’état à **CONTOSO-ReportSrv** :

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigID
```

## Voir aussi

* [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md)
* [Configuration d’un serveur collecteur web DSC](pullServer.md)



<!--HONumber=May16_HO3-->


