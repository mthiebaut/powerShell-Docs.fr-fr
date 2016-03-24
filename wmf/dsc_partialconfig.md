# Configurer un nœud avec plusieurs fragments de configuration (configurations partielles)

WMF 5.0 vous aide à remettre des documents de configuration à un nœud en plusieurs fragments. Pour qu’un nœud reçoive plusieurs fragments d’un document de configuration, il faut que son gestionnaire de configuration local soit configuré pour spécifier les fragments attendus, comme illustré dans cet exemple.

```powershell
[DSCLocalConfigurationManager()]
configuration SQLServerDSCSettings
{
    Node localhost
    {
        Settings
        {
            ConfigurationModeFrequencyMins = 30
        }

        ConfigurationRepositoryWeb OSConfigServer
        {
            ServerURL = "https://corp.contoso.com/OSConfigServer/PSDSCPullServer.svc"
        }

        ConfigurationRepositoryWeb SQLConfigServer
        {
            ServerURL = "https://corp.contoso.com/SQLConfigServer/PSDSCPullServer.svc"
        }

        PartialConfiguration OSConfig
        {
            Description = 'Configuration for the Base OS'
            ExclusiveResources = 'PSDesiredStateConfiguration\*'
            ConfigurationSource = '[ConfigurationRepositoryWeb]OSConfigServer'
        }

        PartialConfiguration SQLConfig
        {
            Description = 'Configuration for the SQL Server'
            ConfigurationSource = '[ConfigurationRepositoryWeb]SQLConfigServer'
            DependsOn = '[PartialConfiguration]OSConfig'
        }
    }
}
```

Dans une configuration partielle, le nom de la configuration doit correspondre à celui défini dans le gestionnaire de configuration local. Dans l’exemple ci-dessus, les configurations doivent être nommées `OSConfig` et `SQLConfig`.

Le fait de configurer le gestionnaire de configuration local pour des configurations partielles autorise la coordination de la configuration, mais ne fournit PAS de fonctionnalités de sécurité.<!--HONumber=Mar16_HO2-->
