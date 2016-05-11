# Utilisation de DSC sur Nano Server

> S’applique à : Windows PowerShell 5.0

**DSC sur Nano Server** est un package facultatif dans le dossier `NanoServer\Packages` du support Windows Server 2016. Le package peut être installé quand vous créez un disque dur virtuel pour Nano Server en
spécifiant **Microsoft-NanoServer-DSC-Package** comme valeur du paramètre **Packages** de la fonction **New-NanoServerImage**. Par exemple, si vous créez un disque dur virtuel pour une machine virtuelle,
la commande ressemble à ceci :

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Pour plus d’informations sur l’installation et l’utilisation de Nano Server, ainsi que sur le mode de gestion de Nano Server avec la communication à distance PowerShell, voir 
[Prise en main de Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx).


## Fonctionnalités DSC disponibles sur Nano Server

 Comme Nano Server ne prend en charge qu’un ensemble limité d’API par rapport à une version complète de Windows Server, DSC sur Nano Server n’a pas exactement les mêmes fonctionnalités que DSC exécuté sur 
 les références complètes pour l’instant. En effet, DSC sur Nano Server est en cours de développement et ne dispose pas encore de toutes les fonctionnalités.
 
 Les fonctionnalités DSC suivantes sont actuellement disponibles sur Nano Server : 


* Modes par envoi et par extraction
* Toutes les applets de commande DSC qui existent sur une version complète de Windows Server, y compris les suivantes : 
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)
        
  * [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx)
        
  * [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stop-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [Publish-DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Restore-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)

  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
    
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
        
  * [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)

  * [New-DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)
    
* Compilation de configurations (voir [Configurations DSC](configurations.md))
* Compilation de métaconfigurations (voir [Configuration du Gestionnaire de configuration local](metaConfig.md))
* [Exécution de DSC avec les informations d’identification de l’utilisateur (RunAs)](runAsUser.md)
* Ressources basées sur une classe (voir [Écriture d’une ressource DSC personnalisée avec les classes PowerShell](authoringResourceClass.md))
* [Spécification de dépendances entre nœuds](crossNodeDependencies.md) 
* [Contrôle de version de ressources](sxsResource.md)
* Événements
* Client collecteur (configurations et ressources) (voir [Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md))
* [Configurations partielles (envoi et extraction)](partialConfigs.md)
* [Rapports au serveur collecteur](reportServer.md) 
* Chiffrement de document MOF
* Journalisation des événements
* Création de rapports DSC Azure Automation


* Ressources qui fonctionnent
  * [Archive](archiveResource.md)
  * [Environment](environmentResource.md)
  * [File](fileResource.md)
  * [Group](groupResource.md)
  * GroupSet
  * [Log](logResource.md)
  * ProcessSet
  * [Registry](registryResource.md)
  * [Service](serviceResource.md)
  * ServiceSet
  * [Script](scriptResource.md)
  * [User](userResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)

  * WaitForAll (voir [Spécification de dépendances entre nœuds](crossNodeDependencies.md))
  * WaitForAny (voir [Spécification de dépendances entre nœuds](crossNodeDependencies.md))
  * WaitForSome (voir [Spécification de dépendances entre nœuds](crossNodeDependencies.md))

## Fonctionnalités DSC non disponibles sur Nano Server

Les fonctionnalités DSC suivantes ne sont pas disponibles sur Nano Server :

* Serveur collecteur : vous ne pouvez pas configurer un serveur collecteur sur Nano Server pour le moment
* Tout ce qui n’est pas dans la liste des fonctionnalités marche

## Utilisation de ressources DSC personnalisées sur Nano Server
 
En raison des ensembles limités d’API Windows et de bibliothèques CLR disponibles sur Nano Server, les ressources DSC qui fonctionnent sur la version CLR complète de Windows ne fonctionnent pas nécessairement sur Nano Server. 
Effectuez les tests de bout en bout avant de déployer des ressources personnalisées DSC dans un environnement de production.

## Voir aussi
- [Prise en main de Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx)

<!--HONumber=Apr16_HO4-->


