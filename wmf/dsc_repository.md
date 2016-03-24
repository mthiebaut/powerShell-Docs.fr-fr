# Séparation des dépôts de configuration, de ressources et de rapports

Dans cette version, vous avez toute la flexibilité nécessaire pour extraire et envoyer des rapports à un ou plusieurs serveurs collecteurs DSC. Vous pouvez définir chaque point de terminaison séparément, et ainsi extraire des configurations à partir d’un emplacement, extraire des ressources à partir d’un deuxième emplacement, et envoyer des rapports vers un troisième emplacement. C’est exactement ce que fait la métaconfiguration suivante.

```PowerShell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
    }

    ConfigurationRepositoryWeb Configurations
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
    }

    ResourceRepositoryWeb Resources
    {
        ServerURL = “https://ResourceServer:8080/psdscpullserver.svc”
        RegistrationKey = "aaaf952b-b9d6-406b-b416-e0f759c6e000"
    }

    ReportServerWeb Reports
    {
        ServerURL = “https://ReportServer:8080/psdscpullserver.svc”
        RegistrationKey = "fefe592b-b9d6-046b-b146-e0f759c0c0c0"
    }
}
```

Vous pouvez également utiliser n’importe quelle combinaison de ces opérations. La métaconfiguration suivante configure un nœud cible en mode par envoi, mais le nœud extraira les ressources dont il ne dispose pas à partir d’un « serveur collecteur DSC » et signalera son état à un autre « serveur collecteur DSC ».


```PowerShell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "Push";
        RebootNodeIfNeeded = $true;
    }

    ResourceRepositoryWeb Resources
    {
        ServerURL = “https://ResourceServer:8080/psdscpullserver.svc”
        RegistrationKey = "aaaf952b-b9d6-406b-b416-e0f759c6e000"
    }

    ReportServerWeb Reports
    {
        ServerURL = “https://ReportServer:8080/psdscpullserver.svc”
        RegistrationKey = "fefe592b-b9d6-046b-b146-e0f759c0c0c0"
    }
}
```<!--HONumber=Mar16_HO2-->
