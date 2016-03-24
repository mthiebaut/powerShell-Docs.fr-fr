# Configurer le gestionnaire de configuration local DSC avec le nouvel attribut de métaconfiguration

L’attribut `DscLocalConfigurationManager` désigne un bloc de configuration en tant que métaconfiguration, qui sert à configurer le gestionnaire de configuration local DSC. Avec cet attribut, une configuration peut contenir uniquement des éléments qui configurent le gestionnaire de configuration local DSC. Pendant le traitement, cette configuration génère un fichier `*.meta.mof` qui est ensuite envoyé aux nœuds cibles appropriés à l’aide de l’applet de commande `Set-DscLocalConfigurationManager`.

```powershell
[DscLocalConfigurationManager()]
configuration meta
{
    Node localhost
    {
        Settings
        {
            ConfigurationMode = "ApplyAndAutocorrect"
            ConfigurationID = "5603f952-d6c6-4971-88c4-948636bf5c3f"
            RefreshMode = "Pull"
        }
        ConfigurationRepositoryWeb PullServer
        {
            ServerURL = "https://corp.contoso.com/PSDSCPullServer/PSDSCPullServer.svc"
        }
    }
}
```

L’exemple ci-dessus configure le mode d’actualisation du gestionnaire de configuration local pour utiliser le mode par extraction, affecte ApplyAndAutocorrect comme mode de configuration, et définit le type et l’emplacement du serveur collecteur.

Ce nouvel attribut de configuration remplace et étend la fonctionnalité de la ressource LocalConfigurationManager par rapport à PowerShell 4.0. Cette ressource LocalConfigurationManager est encore prise en charge dans les configurations sans cet attribut, pour des raisons de compatibilité descendante.

Métaressources :

| **Nom de ressource**            | **Description**                                |
|------------------------------|------------------------------------------------|
| LocalConfigurationManager    | Différents paramètres d’exécution du moteur DSC      |
| PartialConfiguration         | Paramètres de configuration partiels                 |
| ConfigurationRepositoryWeb   | Dépôt de configuration basé sur le web             |
| ConfigurationRepositoryShare | Dépôt de configuration basé sur un partage de fichiers      |
| ResourceRepositoryWeb        | Dépôt de ressources basé sur le web                  |
| ResourceRepositoryShare      | Dépôt de ressources basé sur un partage de fichiers                 |
| ReportServerWeb              | Point de terminaison de rapport basé sur le web pour un scénario d’extraction |
<!--HONumber=Mar16_HO2-->
