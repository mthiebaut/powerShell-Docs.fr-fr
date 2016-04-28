# Configuration d’un serveur collecteur web DSC

> S’applique à : Windows PowerShell 5.0

Un serveur collecteur web DSC est un service web dans IIS qui utilise une interface OData pour que les fichiers de configuration DSC soient disponibles à la demande pour les nœuds cibles.

Configuration requise pour utiliser un serveur collecteur :

* Un serveur en cours d’exécution :
  - WMF/PowerShell 5.0 ou version supérieure
  - Rôle serveur IIS
  - Service DSC
* Idéalement, des moyens de générer un certificat pour sécuriser les informations d’identification transmises au gestionnaire de configuration local sur les nœuds cibles

Vous pouvez ajouter le rôle serveur IIS et le service DSC avec l’Assistant Ajout de rôles et fonctionnalités dans le Gestionnaire de serveur, ou à l’aide de PowerShell. Les exemples de scripts inclus dans cette rubrique gèrent également ces deux étapes pour vous.

## Utilisation de la ressource xWebService
Le moyen le plus simple de configurer un serveur collecteur web consiste à utiliser la ressource xWebService, incluse dans le module xPSDesiredStateConfiguration. Les étapes suivantes expliquent comment utiliser la ressource dans une configuration qui configure le service web.

1. Appelez l’applet de commande [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) pour installer le module **xPSDesiredStateConfiguration**. **Remarque** : **Install-Module** est inclus dans le module **PowerShellGet** de PowerShell 5.0. Vous pouvez télécharger le module **PowerShellGet** pour PowerShell 3.0 et 4.0 ici : [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186). 
1. Obtenez un certificat SSL pour le serveur collecteur DSC auprès d’une autorité de certification approuvée, au sein de votre organisation ou auprès d’une autorité publique. Le certificat reçu de l’autorité est généralement au format PFX. Installez le certificat sur le nœud qui sera le serveur DSC à l’emplacement par défaut, c’est-à-dire : CERT:\LocalMachine\My. Notez l’empreinte de certificat.
1. Sélectionnez un GUID à utiliser comme clé d’inscription. Pour en générer un à l’aide de PowerShell, entrez ce qui suit à l’invite PowerShell et appuyez sur Entrée : « ``` [guid]::newGuid()``` ». Cette clé est utilisée par les nœuds clients comme une clé partagée pour l’authentification lors de l’inscription. Pour plus d’informations, voir la section [Clé d’inscription](#RegKey) ci-dessous.
1. Dans PowerShell ISE, démarrez (F5) le script de configuration suivant (inclus dans le dossier Example du module **xPSDesiredStateConfiguration** en tant que Sample_xDscWebService.ps1). Ce script configure le serveur collecteur.
  
```powershell
configuration Sample_xDscWebService 
{ 
    param  
    ( 
            [string[]]$NodeName = 'localhost', 
            
            [ValidateNotNullOrEmpty()] 
            [string] $certificateThumbPrint,
            
            [Parameter(Mandatory)]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey 
     ) 
 
 
     Import-DSCResource -ModuleName xPSDesiredStateConfiguration 

     Node $NodeName 
     { 
         WindowsFeature DSCServiceFeature 
         { 
             Ensure = "Present" 
             Name   = "DSC-Service"             
         } 
 
 
         xDscWebService PSDSCPullServer 
         { 
             Ensure                  = "Present" 
             EndpointName            = "PSDSCPullServer" 
             Port                    = 8080 
             PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer" 
             CertificateThumbPrint   = $certificateThumbPrint          
             ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
             ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"             
             State                   = "Started" 
             DependsOn               = "[WindowsFeature]DSCServiceFeature"                         
         } 

        File RegistrationKeyFile
        {
            Ensure          ='Present'
            Type            = 'File'
            DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
            Contents        = $RegistrationKey
        }
    }
}

```

1. Exécutez la configuration, en passant l’empreinte du certificat SSL comme paramètre **certificateThumbPrint** et une clé d’inscription GUID comme paramètre **RegistrationKey** :

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certifcates in your local store 
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCService -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutpuPath c:\Configs\PullServer
```

## Clé d’inscription
Pour que les nœuds clients puissent s’inscrire auprès du serveur afin de pouvoir utiliser les noms de configuration au lieu de l’ID de configuration, une clé d’inscription, créée par la configuration ci-dessus, est enregistrée dans un fichier nommé `RegistrationKeys.txt` dans `C:\Program Files\WindowsPowerShell\DscService`. La clé d’inscription fonctionne comme un secret partagé utilisé lors de l’inscription initiale par le client avec le serveur collecteur. Le client génère un certificat auto-signé qui est utilisé pour l’authentification unique auprès du serveur collecteur une fois l’inscription terminée. L’empreinte de ce certificat est stockée localement et associée à l’URL du serveur collecteur.
> **Remarque** : Les clés d’inscription ne sont pas prises en charge dans PowerShell 4.0. 

Pour configurer un nœud pour l’authentification auprès du serveur collecteur, la clé d’inscription doit se trouver dans la métaconfiguration de tous les nœuds cibles que vous prévoyez d’inscrire auprès de ce serveur. Notez que la propriété **RegistrationKey** dans la métaconfiguration ci-dessous est supprimée une fois que l’ordinateur cible a été correctement inscrit, et que la valeur « 140a952b-b9d6-406b-b416-e0f759c9c0e4 » doit correspondre à la valeur stockée dans le fichier RegistrationKeys.txt sur le serveur collecteur. Conservez la valeur de la clé d’inscription en lieu sûr, car elle permet d’inscrire n’importe quel ordinateur cible auprès du serveur.

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
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL         = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey   = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes
```
> **Remarque** : la section **ReportServerWeb** permet d’envoyer les données de rapport au serveur collecteur. 

Si la propriété **ConfigurationID** est absente du fichier de métaconfiguration, cela signifie implicitement que ce serveur collecteur prend en charge la version V2 du protocole du serveur collecteur et donc qu’une inscription initiale est nécessaire. Inversement, si la propriété **ConfigurationID** est présente, la version V1 du protocole du serveur collecteur est utilisée et il n’y a pas de traitement de l’inscription.

>**Remarque** : dans un scénario PUSH, la version actuelle contient un bogue qui demande de définir une propriété ConfigurationID dans le fichier de métaconfiguration pour les nœuds qui n’ont jamais été inscrits auprès d’un serveur collecteur. Cette opération permet de forcer le protocole du serveur collecteur V1 et d’éviter les messages d’échec d’inscription.

## Placement des configurations et des ressources
Une fois l’installation du serveur collecteur terminée, vous placez les modules et configurations à extraire par les nœuds cibles dans les dossiers définis par les propriétés **ConfigurationPath** et **ModulePath** de la configuration du serveur collecteur. Ces fichiers doivent se trouver dans un format spécifique afin que le serveur collecteur puisse les traiter correctement. 

### Format du package de module de ressources DSC
Chaque module de ressources doit être compressé et nommé selon le modèle suivant **{Nom du module}_{Version du module}.zip**. Par exemple, un module xWebAdminstration avec une version de module 3.1.2.0 est nommé « xWebAdministration_3.2.1.0.zip ». Chaque version d’un module doit être contenue dans un seul fichier zip. Étant donné que chaque fichier zip ne contient qu’une seule version d’une ressource, le format du module ajouté dans WMF 5.0 qui contient plusieurs versions de module dans un seul répertoire n’est pas pris en charge. Cela signifie qu’avant de créer le package des modules de ressources DSC à utiliser avec le serveur collecteur, vous devez apporter une petite modification à la structure de répertoires. Le format par défaut des modules contenant les ressources DSC dans WMF 5.0 est « {Dossier du module}\{Version du module}\DscResources\{Dossier des ressources DSC}\ ». Avant de créer les packages pour le serveur collecteur, supprimez simplement le dossier **{Version du module}** pour transformer le chemin en « {Dossier du module}\DscResources\{Dossier des ressources DSC}\ ». Ensuite, compressez le dossier comme décrit ci-dessus, et placez ces fichiers zip dans le dossier **ModulePath**.

### Format du fichier MOF de configuration 
Un fichier MOF de configuration doit être associé à un fichier de somme de contrôle pour que le gestionnaire de configuration local sur un nœud cible puisse valider la configuration. Pour créer une somme de contrôle, appelez l’applet de commande [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx). L’applet de commande prend un paramètre **Path** qui spécifie le dossier où se trouve la configuration MOF. L’applet de commande crée un fichier de somme de contrôle nommé `ConfigurationMOFName.mof.checksum`, où `ConfigurationMOFName` est le nom du fichier MOF de configuration. S’il existe plusieurs fichiers MOF de configuration dans le dossier spécifié, une somme de contrôle est créée pour chaque configuration du dossier. Placez les fichiers MOF et leurs fichiers de somme de contrôle associés dans le dossier **ConfigurationPath**.

>**Remarque** : Si vous modifiez le fichier MOF de configuration de quelque façon que ce soit, vous devez aussi recréer le fichier de somme de contrôle.

## Outils
Pour faciliter la configuration, la validation et la gestion du serveur collecteur, les outils suivants sont fournis comme exemples dans la dernière version du module xPSDesiredStateConfiguration :
1. Module permettant de créer le package des modules de ressources DSC et les fichiers de configuration à utiliser sur le serveur collecteur. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Exemples ci-dessous :

```powershell
    # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
     $moduleList = @("xWebAdministration", "xPhp") 
     Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 
     
     # Example 2 - Package modules and mof documents from c:\LocalDepot
     Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
```

1. Script qui valide la configuration du serveur collecteur. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/Examples/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).


## Configuration du client collecteur 
Les rubriques suivantes décrivent la configuration des clients collecteurs en détail :

* [Configuration d’un client collecteur DSC à l’aide de l’ID de configuration](pullClientConfigID.md)
* [Configuration d’un client collecteur DSC à l’aide du nom de configuration](pullClientConfigNames.md)
* [Configurations partielles](partialConfigs.md)


## Voir aussi
* [Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell](overview.md)
* [Application des configurations](enactingConfigurations.md)
* [Utilisation d’un serveur de rapports DSC](reportServer.md)


<!--HONumber=Mar16_HO5-->


