# Configuration d’un client collecteur à l’aide de l’ID de configuration

> S’applique à : Windows PowerShell 5.0

Chaque nœud cible doit recevoir l’instruction d’utiliser le mode par extraction ainsi que l’URL où contacter le serveur collecteur pour obtenir des configurations. Pour ce faire, vous devez configurer le gestionnaire de configuration local avec les informations nécessaires. Pour configurer le gestionnaire de configuration local, vous créez un type spécial de configuration, avec l’attribut **DSCLocalConfigurationManager**. Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](metaConfig.md).

> **Remarque** : Cette rubrique s’applique à PowerShell 5.0. Pour des informations sur la configuration d’un client collecteur dans PowerShell 4.0, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration dans PowerShell 4.0](pullClientConfigID4.md)

Le script suivant configure le gestionnaire de configuration local pour extraire les configurations d’un serveur nommé « CONTOSO-PullSrv ».

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = 1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }      
    }
}
PullClientConfigID
```

Dans le script, le bloc **ConfigurationRepositoryWeb** définit le serveur collecteur. Paramètre **ServerURL**

Quand le script s’exécute, il crée un dossier de sortie nommé **PullClientConfigID** et y place un fichier MOF de métaconfiguration. Dans ce cas, le fichier MOF de métaconfiguration est nommé `localhost.meta.mof`.

Pour appliquer la configuration, appelez l’applet de commande **Set-DscLocalConfigurationManager** avec le paramètre **Path** défini sur l’emplacement du fichier MOF de métaconfiguration. Par exemple : `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

## ID de configuration

Le script définit la propriété **ConfigurationID** du gestionnaire de configuration local sur un GUID déjà créé à cet effet (vous pouvez créer un GUID à l’aide de l’applet de commande **New-Guid**). Le paramètre **ConfigurationID** est utilisé par le gestionnaire de configuration local pour rechercher la configuration appropriée sur le serveur collecteur. Le fichier MOF de configuration sur le serveur collecteur doit être nommé _ConfigurationID_.mof, où _ConfigurationID_ est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible.

## Serveur collecteur SMB

Pour configurer un client de façon à extraire des configurations d’un serveur SMB, utilisez un bloc **ConfigurationRepositoryShare**. Dans un bloc **ConfigurationRepositoryShare**, vous spécifiez le chemin du serveur en définissant la propriété **SourcePath**. La métaconfiguration suivante configure le nœud cible de façon à extraire des configurations d’un serveur collecteur SMB nommé **SMBPullServer**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## Serveurs de ressources et de rapports

Par défaut, le nœud client obtient les ressources nécessaires du serveur collecteur de configuration et lui signale les états. Toutefois, vous pouvez spécifier différents serveurs collecteurs pour les ressources et les rapports.
Pour spécifier un serveur de ressources, vous utilisez un bloc **ResourceRepositoryWeb** (pour un serveur collecteur web) ou **ResourceRepositoryShare** (pour un serveur collecteur SMB).
Pour spécifier un serveur de rapports, vous utilisez un bloc **ReportRepositoryWeb**. Un serveur de rapports ne peut pas être un serveur SMB.
La métaconfiguration suivante configure un client collecteur de façon à obtenir sa configuration de **CONTOSO-PullSrv** et ses ressources de **CONTOSO-ResourceSrv**, et à envoyer des rapports d’état à **CONTOSO-ReportSrv**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## Voir aussi

* [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md)<!--HONumber=Feb16_HO4-->
