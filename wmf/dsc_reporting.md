# Fournir un rapport sur l’état de la configuration à l’emplacement central

Vous pouvez envoyer des informations détaillées sur l’état de la configuration DSC à un serveur exécutant le service DSC. Les informations retournées par l’applet de commande Get-DscConfigurationStatus sont envoyées au service DSC. Quand vous définissez le serveur de rapports dans une métaconfiguration, cet état est envoyé au serveur si une erreur se produit ou quand la configuration se termine correctement. Ces informations sont envoyées quand un nœud est configuré en mode par extraction ou par envoi. Les informations d’état sont stockées dans la base de données du service DSC.

## Exemple de métaconfiguration pour les rapports d’état
```PowerShell
[DscLocalConfigurationManager()]
Configuration ReportingClientMetaConfig
{
    Settings
        {
            RefreshFrequencyMins = 30
            RefreshMode = "PUSH"
            ConfigurationModeFrequencyMins = 15
            AllowModuleOverwrite = $true
        }

        ReportServerWeb ReportManager
        {
            ServerUrL = "http://localhost:8080/PSDSCPullServer/PSDSCPullserver.svc"
            AllowUnsecureConnection  = $true
        }           
}
```
Un point de terminaison OData est créé avec le service DSC qui expose ces informations d’état. En passant un ID de configuration ou un ID d’agent {$guid} au point de terminaison, vous pouvez recueillir et analyser tout l’état d’un nœud.

## Exemple de demande web pour recueillir l’état de configuration 
```PowerShell
$statusReports = Invoke-WebRequest -Uri "[http://localhost:8080/PSDSCPullserver/PSDSCPullserver.svc/Node(ConfigurationId='$guid')/StatusReport](http://localhost:8080/PSDSCPullserver/psdscpullserver.svc/Node(ConfigurationId='$guid')/StatusReport)s" -UseBasicParsing -UseDefaultCredentials -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" -Headers @{Accept = "application/json"; ProtocolVersion = “1.1”}
```<!--HONumber=Mar16_HO2-->
