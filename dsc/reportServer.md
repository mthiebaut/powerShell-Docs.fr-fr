---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Utilisation d’un serveur de rapports DSC"
ms.openlocfilehash: 31b0df7d9baf30d93154d6a28b21f32fc052bc06
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="2d52c-103">Utilisation d’un serveur de rapports DSC</span><span class="sxs-lookup"><span data-stu-id="2d52c-103">Using a DSC report server</span></span>

> <span data-ttu-id="2d52c-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2d52c-104">Applies To: Windows PowerShell 5.0</span></span>

><span data-ttu-id="2d52c-105">**Remarque** : le serveur de rapports décrit dans cette rubrique n’est pas disponible dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="2d52c-105">**Note:** The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="2d52c-106">Le gestionnaire de configuration local d’un nœud peut être configuré pour envoyer des rapports sur son état de configuration à un serveur collecteur, qui peut alors être interrogé pour récupérer ces données.</span><span class="sxs-lookup"><span data-stu-id="2d52c-106">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server, which can then be queried to retrieve that data.</span></span> <span data-ttu-id="2d52c-107">Chaque fois, le nœud vérifie et applique une configuration, il envoie un rapport au serveur de rapports.</span><span class="sxs-lookup"><span data-stu-id="2d52c-107">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="2d52c-108">Ces rapports sont stockés dans une base de données sur le serveur et peuvent être récupérés en appelant le service web de création de rapports.</span><span class="sxs-lookup"><span data-stu-id="2d52c-108">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span> <span data-ttu-id="2d52c-109">Chaque rapport contient des informations telles que les configurations qui ont été appliquées et si l’opération a réussi, les ressources utilisées, les erreurs qui ont été levées et les heures de début et de fin.</span><span class="sxs-lookup"><span data-stu-id="2d52c-109">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="2d52c-110">Configuration d’un nœud pour envoyer des rapports</span><span class="sxs-lookup"><span data-stu-id="2d52c-110">Configuring a node to send reports</span></span>

<span data-ttu-id="2d52c-111">Vous indiquez à un nœud d’envoyer des rapports à un serveur en utilisant un bloc **ReportServerWeb** dans la configuration du gestionnaire de configuration local du nœud (pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration du gestionnaire de configuration local](metaConfig.md)).</span><span class="sxs-lookup"><span data-stu-id="2d52c-111">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md)).</span></span> <span data-ttu-id="2d52c-112">Le serveur auquel le nœud envoie des rapports doit être configuré comme un serveur web collecteur (vous ne pouvez pas envoyer de rapports à un partage SMB).</span><span class="sxs-lookup"><span data-stu-id="2d52c-112">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="2d52c-113">Pour plus d’informations sur la configuration d’un serveur collecteur, consultez [Configuration d’un serveur collecteur web DSC](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="2d52c-113">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="2d52c-114">Le serveur de rapports peut être le même service duquel le nœud extrait des configurations et obtient des ressources, mais il peut également être un service différent.</span><span class="sxs-lookup"><span data-stu-id="2d52c-114">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>
 
<span data-ttu-id="2d52c-115">Dans le bloc **ReportServerWeb**, vous spécifiez l’URL du service d’extraction et une clé d’inscription connue du serveur.</span><span class="sxs-lookup"><span data-stu-id="2d52c-115">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>
 
<span data-ttu-id="2d52c-116">La configuration suivante configure un nœud de façon à extraire des configurations d’un seul service et à envoyer des rapports à un service sur un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="2d52c-116">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span> 
 
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
ReportClientConfig
```

<span data-ttu-id="2d52c-117">La configuration suivante configure un nœud de façon à utiliser un seul serveur pour les configurations, les ressources et les rapports.</span><span class="sxs-lookup"><span data-stu-id="2d52c-117">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfig
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
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
        
        

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfig
```

><span data-ttu-id="2d52c-118">**Remarque :** vous pouvez donner le nom de votre choix au service web quand vous configurez un serveur collecteur, mais la propriété **ServerURL** doit correspondre au nom du service.</span><span class="sxs-lookup"><span data-stu-id="2d52c-118">**Note:** You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="2d52c-119">Obtention des données du rapport</span><span class="sxs-lookup"><span data-stu-id="2d52c-119">Getting report data</span></span>

<span data-ttu-id="2d52c-120">Les rapports envoyés au serveur collecteur sont entrés dans une base de données sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="2d52c-120">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="2d52c-121">Les rapports sont disponibles par le biais d’appels au service web.</span><span class="sxs-lookup"><span data-stu-id="2d52c-121">The reports are available through calls to the web service.</span></span> <span data-ttu-id="2d52c-122">Pour récupérer des rapports pour un nœud spécifique, envoyez une demande HTTP au service web de rapports sous la forme suivante : `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId= 'MyNodeAgentId')/Reports` où `MyNodeAgentId` est l’ID de l’agent du nœud pour lequel vous voulez obtenir des rapports.</span><span class="sxs-lookup"><span data-stu-id="2d52c-122">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId= 'MyNodeAgentId')/Reports` where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="2d52c-123">Vous pouvez obtenir l’ID de l’agent d’un nœud en appelant [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) sur ce nœud.</span><span class="sxs-lookup"><span data-stu-id="2d52c-123">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) on that node.</span></span>

<span data-ttu-id="2d52c-124">Les rapports sont retournés sous forme de tableau d’objets JSON.</span><span class="sxs-lookup"><span data-stu-id="2d52c-124">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="2d52c-125">Le script suivant retourne les rapports pour le nœud sur lequel il est exécuté :</span><span class="sxs-lookup"><span data-stu-id="2d52c-125">The following script returns the reports for the node on which it is run:</span></span>

```powershell
function GetReport
{
    param($AgentId = "$((glcm).AgentId)", $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCPullServer.svc")
    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```
    
## <a name="viewing-report-data"></a><span data-ttu-id="2d52c-126">Affichage des données du rapport</span><span class="sxs-lookup"><span data-stu-id="2d52c-126">Viewing report data</span></span>

<span data-ttu-id="2d52c-127">Si vous définissez une variable sur le résultat de la fonction **GetReport**, vous pouvez afficher les champs individuels dans un élément du tableau retourné :</span><span class="sxs-lookup"><span data-stu-id="2d52c-127">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

```powershell
$reports = GetReport
$reports[1]


JobId                : 019dfbe5-f99f-11e5-80c6-001dd8b8065c
OperationType        : Consistency
RefreshMode          : Pull
Status               : Success
ReportFormatVersion  : 2.0
ConfigurationVersion : 2.0.0
StartTime            : 04/03/2016 06:21:43
EndTime              : 04/03/2016 06:22:04
RebootRequested      : False
Errors               : {}
StatusData           : {{"StartDate":"2016-04-03T06:21:43.7220000-07:00","IPV6Addresses":["2001:4898:d8:f2f2:852b:b255:b071:283b","fe80::852b:b255:b071
                       :283b%12","::2000:0:0:0","::1","::2000:0:0:0"],"DurationInSeconds":"21","JobID":"{019DFBE5-F99F-11E5-80C6-001DD8B8065C}","Curren
                       tChecksum":"A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F","MetaData":"Author: configAuthor; Name: 
                       Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost: CONTOSO-PullSrv;","RebootRequested":"False
                       ","Status":"Success","IPV4Addresses":["10.240.179.151","127.0.0.1"],"LCMVersion":"2.0","ResourcesNotInDesiredState":[{"SourceInf
                       o":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall","ModuleName":"xNetworking","DurationInSeconds":"8.785",
                       "InstanceName":"Firewall","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"xFirewall","ModuleVersion":"2.7.0.0","
                       RebootRequested":"False","ResourceId":"[xFirewall]Firewall","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"False
                       "}],"NumberOfResources":"2","Type":"Consistency","HostName":"CONTOSO-PULLCLI","ResourcesInDesiredState":[{"SourceInfo":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive","ModuleName":"PSDesiredStateConfiguration","DurationInSeconds":"1.848",
                       "InstanceName":"ArchiveExample","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"Archive","ModuleVersion":"1.1","
                       RebootRequested":"False","ResourceId":"[Archive]ArchiveExample","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"T
                       rue"}],"MACAddresses":["00-1D-D8-B8-06-5C","00-00-00-00-00-00-00-E0"],"MetaConfiguration":{"AgentId":"52DA826D-00DE-4166-8ACB-73F2B46A7E00",
                       "ConfigurationDownloadManagers":[{"SourceInfo":"C:\\ReportTest\\LCMConfig.ps1::14::9::ConfigurationRepositoryWeb","A
                       llowUnsecureConnection":"True","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","RegistrationKey":"","ResourceId":"[Config
                       urationRepositoryWeb]CONTOSO-PullSrv","ConfigurationNames":["ClientConfig"]}],"ActionAfterReboot":"ContinueConfiguration","LCMCo
                       mpatibleVersions":["1.0","2.0"],"LCMState":"Idle","ResourceModuleManagers":[],"ReportManagers":[{"AllowUnsecureConnection":"True
                       ","RegistrationKey":"","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","ResourceId":"[ReportServerWeb]CONTOSO-PullSrv","S
                       ourceInfo":"C:\\ReportTest\\LCMConfig.ps1::24::9::ReportServerWeb"}],"StatusRetentionTimeInDays":"10","LCMVersion":"2.0","Config
                       urationMode":"ApplyAndMonitor","RefreshFrequencyMins":"30","RebootNodeIfNeeded":"True","RefreshMode":"Pull","DebugMode":["NONE"]
                       ,"LCMStateDetail":"","AllowModuleOverwrite":"False","ConfigurationModeFrequencyMins":"15"},"Locale":"en-US","Mode":"Pull"}}
AdditionalData       : {}
```

<span data-ttu-id="2d52c-128">Par défaut, les rapports sont triés par **JobID**.</span><span class="sxs-lookup"><span data-stu-id="2d52c-128">By default, the reports are sorted by **JobID**.</span></span> <span data-ttu-id="2d52c-129">Pour obtenir le rapport le plus récent, vous pouvez trier les rapports dans l’ordre décroissant de la valeur de la propriété **StartTime**, puis obtenir le premier élément du tableau :</span><span class="sxs-lookup"><span data-stu-id="2d52c-129">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="2d52c-130">Notez que la propriété **StatusData** est un objet avec un certain nombre de propriétés.</span><span class="sxs-lookup"><span data-stu-id="2d52c-130">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="2d52c-131">C’est là que figurent une bonne partie des données de création de rapports.</span><span class="sxs-lookup"><span data-stu-id="2d52c-131">This is where much of the reporting data is.</span></span> <span data-ttu-id="2d52c-132">Examinons les différents champs de la propriété**StatusData** pour le rapport le plus récent :</span><span class="sxs-lookup"><span data-stu-id="2d52c-132">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

```powershell
$statusData = $reportMostRecent.StatusData | ConvertFrom-Json
$statusData

StartDate                  : 2016-04-04T11:21:41.2990000-07:00
IPV6Addresses              : {2001:4898:d8:f2f2:852b:b255:b071:283b, fe80::852b:b255:b071:283b%12, ::2000:0:0:0, ::1...}
DurationInSeconds          : 25
JobID                      : {135D230E-FA92-11E5-80C6-001DD8B8065C}
CurrentChecksum            : A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F
MetaData                   : Author: configAuthor; Name: Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost: 
                             CONTOSO-PullSrv;
RebootRequested            : False
Status                     : Success
IPV4Addresses              : {10.240.179.151, 127.0.0.1}
LCMVersion                 : 2.0
ResourcesNotInDesiredState : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall; ModuleName=xNetworking; 
                             DurationInSeconds=10.725; InstanceName=Firewall; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=xFirewall; 
                             ModuleVersion=2.7.0.0; RebootRequested=False; ResourceId=[xFirewall]Firewall; ConfigurationName=Sample_ArchiveFirewall; 
                             InDesiredState=False}}
NumberOfResources          : 2
Type                       : Consistency
HostName                   : CONTOSO-PULLCLI
ResourcesInDesiredState    : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive; ModuleName=PSDesiredStateConfiguration; 
                             DurationInSeconds=2.672; InstanceName=ArchiveExample; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=Archive; 
                             ModuleVersion=1.1; RebootRequested=False; ResourceId=[Archive]ArchiveExample; ConfigurationName=Sample_ArchiveFirewall; 
                             InDesiredState=True}}
MACAddresses               : {00-1D-D8-B8-06-5C, 00-00-00-00-00-00-00-E0}
MetaConfiguration          : @{AgentId=52DA826D-00DE-4166-8ACB-73F2B46A7E00; ConfigurationDownloadManagers=System.Object[]; 
                             ActionAfterReboot=ContinueConfiguration; LCMCompatibleVersions=System.Object[]; LCMState=Idle; 
                             ResourceModuleManagers=System.Object[]; ReportManagers=System.Object[]; StatusRetentionTimeInDays=10; LCMVersion=2.0; 
                             ConfigurationMode=ApplyAndMonitor; RefreshFrequencyMins=30; RebootNodeIfNeeded=True; RefreshMode=Pull; 
                             DebugMode=System.Object[]; LCMStateDetail=; AllowModuleOverwrite=False; ConfigurationModeFrequencyMins=15}
Locale                     : en-US
Mode                       : Pull
```

<span data-ttu-id="2d52c-133">Cela indique, entre autres, que la configuration la plus récente a appelé deux ressources, et que l’une d’elles était dans l’état souhaité, tandis que l’autre pas.</span><span class="sxs-lookup"><span data-stu-id="2d52c-133">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="2d52c-134">Vous pouvez obtenir une sortie plus lisible uniquement de la propriété **ResourcesNotInDesiredState**:</span><span class="sxs-lookup"><span data-stu-id="2d52c-134">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

```powershell
$statusData.ResourcesInDesiredState

SourceInfo        : C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive
ModuleName        : PSDesiredStateConfiguration
DurationInSeconds : 2.672
InstanceName      : ArchiveExample
StartDate         : 2016-04-04T11:21:55.7200000-07:00
ResourceName      : Archive
ModuleVersion     : 1.1
RebootRequested   : False
ResourceId        : [Archive]ArchiveExample
ConfigurationName : Sample_ArchiveFirewall
InDesiredState    : True
```

<span data-ttu-id="2d52c-135">Notez que ces exemples ont pour but de vous donner une idée de ce que vous pouvez faire avec les données du rapport.</span><span class="sxs-lookup"><span data-stu-id="2d52c-135">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="2d52c-136">Pour obtenir une présentation de l’utilisation de JSON dans PowerShell, voir [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="2d52c-136">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="2d52c-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d52c-137">See Also</span></span>
- [<span data-ttu-id="2d52c-138">Configuration du gestionnaire de configuration local</span><span class="sxs-lookup"><span data-stu-id="2d52c-138">Configuring the Local Configuration Manager</span></span>](metaConfig.md)
- [<span data-ttu-id="2d52c-139">Configuration d’un serveur collecteur web DSC</span><span class="sxs-lookup"><span data-stu-id="2d52c-139">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="2d52c-140">Configuration d’un client collecteur à l’aide du nom de configuration</span><span class="sxs-lookup"><span data-stu-id="2d52c-140">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)

