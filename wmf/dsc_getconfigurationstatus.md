# Détails sur l’état de configuration

L’applet de commande `Get-DscConfigurationStatus` obtient des informations sur l’état de la configuration à partir d’un nœud cible. Un objet enrichi est retourné. Il comprend des informations générales indiquant si l’exécution de la configuration a réussi ou échoué. Vous pouvez explorer l’objet pour obtenir des détails sur l’exécution de la configuration, notamment :

* Toutes les ressources qui ont échoué
* Toute ressource ayant demandé un redémarrage
* Les paramètres de métaconfiguration au moment de l’exécution de la configuration
* Etc.

Le jeu de paramètres suivant retourne les informations d’état pour la dernière exécution de configuration :

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```
Le jeu de paramètres suivant retourne les informations d’état pour toutes les exécutions de configuration précédentes :

```powershell
Get-DscConfigurationStatus  -All 
                            [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```

## Exemple

```powershell
PS C:\> $Status = Get-DscConfigurationStatus 

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :   
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :   
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :   
InDesiredState          :   False
InitialState            :   
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```<!--HONumber=Mar16_HO2-->
