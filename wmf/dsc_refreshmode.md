# Valeur supplémentaire pour la propriété RefreshMode

Cette version introduit une nouvelle valeur `RefreshMode`, **Disabled**. Quand ce mode est défini, le gestionnaire de configuration local n’effectue pas la gestion des documents. Vous pouvez utiliser ce mode quand un outil de gestion de la configuration tiers est utilisé au lieu de DSC tout en tirant parti des ressources DSC avec l’applet de commande `Invoke-DscResource`, ou si vous devez simplement arrêter le traitement DSC pour une raison quelconque.

```powershell
Configuration LCMSettings
{
    Node localhost
    {
        LocalConfigurationManager
        {
           RefreshMode = 'Disabled'
        }
    }
}

LCMSettings -OutputPath .\LCMSettings
Set-DscLocalConfigurationManager -Path .\LCMSettings -Verbose -ComputerName localhost
```
<!--HONumber=Mar16_HO2-->
