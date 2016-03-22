# Utilisation d’un serveur de rapports DSC

> S’applique à : Windows PowerShell 5.0

> **Remarque :** Le serveur de rapports décrit dans cette rubrique n’est pas disponible dans PowerShell 4.0. Pour créer des rapports dans PowerShell 4.0, consultez Utilisation d’un serveur de compatibilité DSC.

Le gestionnaire de configuration local d’un nœud peut être configuré pour envoyer des rapports sur son état de configuration à un serveur collecteur, qui peut alors être interrogé pour récupérer ces données. Chaque fois, le nœud vérifie et applique
une configuration, il envoie un rapport au serveur de rapports. Ces rapports sont stockés dans une base de données sur le serveur et peuvent être récupérés en appelant le service web de création de rapports. Chaque rapport contient
des informations telles que les configurations qui ont été appliquées et si l’opération a réussi, les ressources utilisées, les erreurs qui ont été levées et les heures de début et de fin.

## Configuration d’un nœud pour envoyer des rapports

Vous indiquez à un nœud d’envoyer des rapports à un serveur en utilisant un bloc **ReportServerWeb** dans la configuration du gestionnaire de configuration local du nœud (pour plus d’informations sur la configuration du gestionnaire de configuration local,
 consultez [Configuration du gestionnaire de configuration local](metaConfig.md)). Le serveur auquel le nœud envoie des rapports doit être configuré comme un serveur web collecteur (vous ne pouvez pas envoyer de rapports
 à un partage SMB). Pour plus d’informations sur la configuration d’un serveur collecteur, consultez [Configuration d’un serveur collecteur web DSC](pullServer.md). Le serveur de rapports peut être le même service duquel
 le nœud extrait des configurations et obtient des ressources, mais il peut également être un service différent.
 
 Dans le bloc **ReportServerWeb**, vous spécifiez l’URL du service d’extraction
 et une clé d’inscription connue du serveur.
 
  La configuration suivante configure un nœud de façon à extraire des configurations d’un seul service et à envoyer des rapports
 à un service sur un autre serveur. 
 
```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCReportServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}
PullClientConfigID
```

## Obtention des données du rapport

Les rapports envoyés au serveur collecteur sont entrés dans une base de données sur le serveur. Les rapports sont disponibles par le biais d’appels au service web. Pour récupérer des rapports pour un nœud spécifique, 
envoyez une demande HTTP au service web de rapports sous la forme suivante :
`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentID = MyNodeAgentId)/Reports` 
où `MyNodeAgentId` est l’ID de l’agent du nœud pour lequel vous voulez obtenir des rapports. Vous pouvez obtenir l’ID de l’agent d’un nœud en appelant [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)
sur ce nœud.

Les rapports sont retournés sous forme de tableau d’objets JSON.

Le script suivant retourne les rapports pour le nœud sur lequel il est exécuté :

```powershell
function GetReport
{
    param($AgentId = "$((glcm).AgentId)", $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCReportServer.svc")
    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```
    
## Affichage des données du rapport

Si vous définissez une variable sur le résultat de la fonction **GetReport**, vous pouvez afficher les champs individuels dans un élément du tableau retourné :

```powershell
$reports = GetReport
$reports[1]

JobId                : 71515ae8-7294-40a3-8137-fc85bf4b678f
OperationType        : Consistency
RefreshMode          : 
Status               : 
ReportFormatVersion  : 1.0
ConfigurationVersion : 2.0.0
StartTime            : 02/08/2016 01:28:54
EndTime              : 02/08/2016 01:28:57
RebootRequested      : False
Errors               : {}
StatusData           : {{"NumberOfResources":"2","Locale":"en-US","ResourcesInDesiredState":[{"ResourceId":"[WindowsFeature]MyFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::4::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"},{"ResourceId":"[WindowsFeature]My2ndFeatureInstance","SourceI
                       nfo":"C:\\ReportTest\\ClientConfig.ps1::8::9::WindowsFeature","ModuleName":"PsDesiredStateConfiguration","ModuleVersion":"1.0","
                       ConfigurationName":"ClientConfig","ResourceName":"WindowsFeature"}]}}
```

Notez que le champ **StatusData** est un objet avec trois propriétés : **NumberOfResources**, **Locale** et **ResourcesInDesiredState**. La propriété **ResourcesInDesiredState**
est un tableau d’objets qui ont chacun un nombre de propriétés. Le script suivant prend un seul rapport comme paramètre, effectue une itération dans son tableau **ResourcesInDesiredState**
et l’écrit dans la console :
 
```powershell
function GetStatusData
{
    param ($Report)
    $statusData = $Report.StatusData | ConvertFrom-Json

    $Resources = $statusData.ResourcesInDesiredState

    Foreach ($Resource in $Resources)
    {
        Write-Host 'ResourceId: ' $Resource.ResourceId
        Write-Host 'SourceInfo: ' $Resource.SourceInfo
        Write-Host 'ModuleName: ' $Resource.ModuleName
        Write-Host 'ModuleVersion: ' $Resource.ModuleVersion
        Write-Host 'ConfigurationName: ' $Resource.ConfigurationName
        Write-Host 'ResourceName: ' $Resource.ResourceName
        Write-Host
    }
}
```

Voici un exemple de sortie après avoir appelé la fonction **GetStatusData** :

```powershell
GetStatusData -Report $report[1]

ResourceId:  [WindowsFeature]MyFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::4::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature

ResourceId:  [WindowsFeature]My2ndFeatureInstance
SourceInfo:  C:\ReportTest\ClientConfig.ps1::8::9::WindowsFeature
ModuleName:  PsDesiredStateConfiguration
ModuleVersion:  1.0
ConfigurationName:  ClientConfig
ResourceName:  WindowsFeature
```

Notez que ces exemples ont pour but de vous donner une idée de ce que vous pouvez faire avec les données du rapport. Pour une présentation de l’utilisation de JSON dans PowerShell, consultez
[Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).

## Voir aussi
>[Configuration du gestionnaire de configuration local](metaConfig.md)
>[Configuration d’un serveur collecteur web DSC](pullServer.md)
>[Configuration d’un client collecteur à l’aide du nom de configuration](pullClientConfigNames.md)
<!--HONumber=Feb16_HO4-->
