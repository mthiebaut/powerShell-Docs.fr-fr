# Configuration d’un serveur collecteur web DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Un serveur collecteur web DSC est un service web dans IIS qui utilise une interface OData pour que les fichiers de configuration DSC soient disponibles à la demande pour les nœuds cibles.

Configuration requise pour utiliser un serveur collecteur :

* Un serveur en cours d’exécution :
  - WMF/PowerShell 4.0 ou version supérieure
  - Rôle serveur IIS
  - Service DSC
* Idéalement, des moyens de générer un certificat pour sécuriser les informations d’identification transmises au gestionnaire de configuration local sur les nœuds cibles

Vous pouvez ajouter le rôle serveur IIS et le service DSC avec l’Assistant Ajout de rôles et fonctionnalités dans le Gestionnaire de serveur, ou à l’aide de PowerShell. Les exemples de scripts inclus dans cette rubrique gèrent également ces deux étapes pour vous.

## Utilisation de la ressource xWebService
Le moyen le plus simple de configurer un serveur collecteur web consiste à utiliser la ressource xWebService, incluse dans le module xPSDesiredStateConfiguration. Les étapes suivantes expliquent comment utiliser la ressource dans une configuration qui configure le service web.

1. Appelez l’applet de commande [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) pour installer le module **xPSDesiredStateConfiguration**. **Remarque** : **Install-Module** est inclus dans le module **PowerShellGet** de PowerShell 5.0. Vous pouvez télécharger le module **PowerShellGet** pour PowerShell 3.0 et 4.0 ici : [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186). 
1. Créez un certificat auto-signé avec le sujet `"CN=PSDSCPullServerCert"` dans le magasin `CERT:\LocalMachine\MY\`. Vous pouvez le faire avec la commande `New-SelfSignedCertificate  -CertStoreLocation 'CERT:\LocalMachine\MY' -DnsName "PSDSCPullServerCert"`.
1. Dans PowerShell ISE, démarrez (F5) le script de configuration suivant (inclus dans le dossier Example du module **xPSDesiredStateConfiguration** en tant que Sample_xDscWebService.ps1). Ce script configure le serveur collecteur et un serveur de compatibilité.
  
```powershell
configuration Sample_xDscWebService 
6 { 
7     param  
8     ( 
9         [string[]]$NodeName = 'localhost', 
10 
 
11         [ValidateNotNullOrEmpty()] 
12         [string] $certificateThumbPrint 
13     ) 
14 
 
15     Import-DSCResource -ModuleName xPSDesiredStateConfiguration 
16 
 
17     Node $NodeName 
18     { 
19         WindowsFeature DSCServiceFeature 
20         { 
21             Ensure = "Present" 
22             Name   = "DSC-Service"             
23         } 
24 
 
25         xDscWebService PSDSCPullServer 
26         { 
27             Ensure                  = "Present" 
28             EndpointName            = "PSDSCPullServer" 
29             Port                    = 8080 
30             PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer" 
31             CertificateThumbPrint   = $certificateThumbPrint          
32             ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
33             ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"             
34             State                   = "Started" 
35             DependsOn               = "[WindowsFeature]DSCServiceFeature"                         
36         } 
```

1. Exécutez la configuration, en passant l’empreinte numérique du certificat auto-signé que vous avez créé comme paramètre **certificateThumbPrint** :

```powershell
PS:\>$myCert = Get-ChildItem CERT: | Where-Object {$_.Subject -eq 'CN=PSDSCPullServerCert'}
PS:\>Sample_xDSCService -certificateThumbprint $myCert.Thumbprint 
```

## Clé d’inscription
Pour que les nœuds clients puissent s’inscrire auprès du serveur afin de pouvoir utiliser les noms de configuration au lieu de l’ID de configuration, une clé d’inscription (qui est un GUID connu par le serveur et le nœud client) doit être placée dans un fichier nommé `RegistrationKeys.txt`. Par défaut, le serveur collecteur créé dans cet exemple suppose que ce fichier se trouve dans `C:\Program Files\WindowsPowerShell\DscService`. Créez un fichier texte avec une seule ligne composée de la clé d’inscription et enregistrez-le dans le dossier.
> **Remarque** : Les clés d’inscription ne sont pas prises en charge dans PowerShell 4.0. 

## Placement des configurations et des ressources
Une fois la configuration du serveur collecteur terminée, un nouveau dossier s’affiche sous `$env:PROGRAMFILES\WindowsPowerShell` nommé « DscService ». Dans ce dossier se trouvent deux autres dossiers nommés « Modules » et « Configuration ». Dans le dossier « Modules », placez toutes les ressources nécessaires aux configurations que les nœuds doivent extraire de ce serveur. Dans le dossier « Configuration », placez les fichiers MOF de configuration de toutes les configurations qui doivent être extraites par les nœuds. Les noms des fichiers MOF dépendent du type de client collecteur. Les rubriques suivantes décrivent la configuration des clients collecteurs en détail :

* [Configuration d’un client collecteur DSC à l’aide de l’ID de configuration](pullClientConfigID.md)
* [Configuration d’un client collecteur DSC à l’aide du nom de configuration](pullClientConfigNames.md)
* [Configurations partielles](partialConfigs.md)

## Création de la somme de contrôle MOF
Un fichier MOF de configuration doit être associé à un fichier de somme de contrôle pour que le gestionnaire de configuration local sur un nœud cible puisse valider la configuration. Pour créer une somme de contrôle, appelez l’applet de commande [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx). L’applet de commande prend un paramètre **Path** qui spécifie le dossier où se trouve la configuration MOF. L’applet de commande crée un fichier de somme de contrôle nommé `ConfigurationMOFName.mof.checksum`, où `ConfigurationMOFName` est le nom du fichier MOF de configuration. S’il existe plusieurs fichiers MOF de configuration dans le dossier spécifié, une somme de contrôle est créée pour chaque configuration du dossier.

Le fichier de somme de contrôle doit être présent dans le même répertoire que celui du fichier MOF de configuration (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` par défaut), et avoir le même nom, mais avec l’extension `.checksum`.

>**Remarque** : Si vous modifiez le fichier MOF de configuration de quelque façon que ce soit, vous devez aussi recréer le fichier de somme de contrôle.

## Voir aussi
* [Présentation de la configuration d’état souhaité Windows PowerShell](overview.md)
* [Application des configurations](enactingConfigurations.md)
* [Comment récupérer des informations sur les nœuds à partir d’un serveur collecteur DSC](retrieveNodeInfo.md)
<!--HONumber=Feb16_HO4-->
