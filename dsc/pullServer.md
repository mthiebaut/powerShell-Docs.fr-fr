---
ms.date: 2018-02-02
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Service collecteur DSC
ms.openlocfilehash: d5e24dcc093c73d8ebbaa618517193dacc4f2aaf
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="14322-103">Service collecteur Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="14322-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="14322-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="14322-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="14322-105">La gestion du Gestionnaire de configuration local peut être centralisée par une solution de service collecteur.</span><span class="sxs-lookup"><span data-stu-id="14322-105">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="14322-106">Lorsque vous utilisez cette approche, le nœud géré est inscrit auprès d’un service et se voit affecter une configuration dans les paramètres LCM.</span><span class="sxs-lookup"><span data-stu-id="14322-106">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="14322-107">La configuration et toutes les ressources DSC nécessaires en tant que dépendances de la configuration sont téléchargées sur l’ordinateur et utilisées par le Gestionnaire de configuration local pour gérer la configuration.</span><span class="sxs-lookup"><span data-stu-id="14322-107">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="14322-108">Des informations sur l’état de l’ordinateur géré sont chargées sur le service pour créer des rapports.</span><span class="sxs-lookup"><span data-stu-id="14322-108">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="14322-109">Ce concept est appelé « service collecteur ».</span><span class="sxs-lookup"><span data-stu-id="14322-109">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="14322-110">Les options actuelles du service collecteur sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="14322-110">The current options for pull service include:</span></span>

- <span data-ttu-id="14322-111">Service Desired State Configuration Azure Automation</span><span class="sxs-lookup"><span data-stu-id="14322-111">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="14322-112">Service collecteur exécuté sur Windows Server</span><span class="sxs-lookup"><span data-stu-id="14322-112">A pull service running on Windows Server</span></span>
- <span data-ttu-id="14322-113">Solutions open source gérées par la communauté</span><span class="sxs-lookup"><span data-stu-id="14322-113">Community maintained open source solutions</span></span>
- <span data-ttu-id="14322-114">Partage SMB</span><span class="sxs-lookup"><span data-stu-id="14322-114">An SMB share</span></span>

<span data-ttu-id="14322-115">**La solution recommandée**, qui est à la fois l’option offrant le plus de fonctionnalités, est [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="14322-115">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="14322-116">Le service Azure peut gérer les nœuds locaux dans des centres de données privés ou dans des clouds publics tels qu’Azure et AWS.</span><span class="sxs-lookup"><span data-stu-id="14322-116">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="14322-117">Pour les environnements où les serveurs ne peut pas se connecter directement à Internet, envisagez de limiter le trafic sortant à la seule plage IP Azure publiée (voir [Plages d’adresses IP Azure Datacenter](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="14322-117">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="14322-118">Fonctionnalités du service en ligne qui ne sont actuellement pas disponibles dans le service collecteur sur Windows Server :</span><span class="sxs-lookup"><span data-stu-id="14322-118">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="14322-119">Toutes les données sont chiffrées, en transit comme au repos</span><span class="sxs-lookup"><span data-stu-id="14322-119">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="14322-120">Les certificats clients sont créés et gérés automatiquement</span><span class="sxs-lookup"><span data-stu-id="14322-120">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="14322-121">Magasin des secrets pour une gestion centralisée des [mots de passe/informations d’identification](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), ou des [variables](https://docs.microsoft.com/en-us/azure/automation/automation-variables) telles que les noms des serveurs ou les chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="14322-121">Secrets store for centrally managing [passwords/credentials](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), or [variables](https://docs.microsoft.com/en-us/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="14322-122">Gestion centralisée du nœud [configuration du LCM](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="14322-122">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="14322-123">Assignation centralisée de configurations aux nœuds clients</span><span class="sxs-lookup"><span data-stu-id="14322-123">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="14322-124">Mise des modifications de la configuration en « groupes de contrôle de validité » pour effectuer des tests avant la production</span><span class="sxs-lookup"><span data-stu-id="14322-124">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="14322-125">Création de rapports graphiques</span><span class="sxs-lookup"><span data-stu-id="14322-125">Graphical reporting</span></span>
  - <span data-ttu-id="14322-126">Détails de l’état au niveau de la granularité de la ressource DSC</span><span class="sxs-lookup"><span data-stu-id="14322-126">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="14322-127">Messages d’erreur en clair des ordinateurs clients pour la résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="14322-127">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="14322-128">[Intégration à Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) pour les alertes, tâches automatisées, application Android/iOS pour les rapports et les alertes</span><span class="sxs-lookup"><span data-stu-id="14322-128">[Integration with Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="14322-129">Service collecteur DSC dans Windows Server</span><span class="sxs-lookup"><span data-stu-id="14322-129">DSC pull service in Windows Server</span></span>

<span data-ttu-id="14322-130">Il est possible de configurer un service collecteur pour l’exécuter sur Windows Server.</span><span class="sxs-lookup"><span data-stu-id="14322-130">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="14322-131">Veuillez noter que la solution de service collecteur incluse dans Windows Server contient uniquement les fonctionnalités de stockage des configurations/modules à télécharger et de capture de données de rapport dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="14322-131">Please be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="14322-132">Elle ne contient pas les nombreuses fonctionnalités offertes par le service dans Azure et n’est donc pas un bon outil pour évaluer la manière dont le service doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="14322-132">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="14322-133">Le service collecteur proposé dans Windows Server est un service web dans IIS qui utilise une interface OData pour mettre les fichiers de configuration DSC à la disposition des nœuds cibles quand ceux-ci en ont besoin.</span><span class="sxs-lookup"><span data-stu-id="14322-133">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="14322-134">Configuration requise pour utiliser un serveur collecteur :</span><span class="sxs-lookup"><span data-stu-id="14322-134">Requirements for using a pull server:</span></span>

- <span data-ttu-id="14322-135">Un serveur en cours d’exécution :</span><span class="sxs-lookup"><span data-stu-id="14322-135">A server running:</span></span>
  - <span data-ttu-id="14322-136">WMF/PowerShell 5.0 ou version supérieure</span><span class="sxs-lookup"><span data-stu-id="14322-136">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="14322-137">Rôle serveur IIS</span><span class="sxs-lookup"><span data-stu-id="14322-137">IIS server role</span></span>
  - <span data-ttu-id="14322-138">Service DSC</span><span class="sxs-lookup"><span data-stu-id="14322-138">DSC Service</span></span>
- <span data-ttu-id="14322-139">Idéalement, des moyens de générer un certificat pour sécuriser les informations d’identification transmises au gestionnaire de configuration local sur les nœuds cibles</span><span class="sxs-lookup"><span data-stu-id="14322-139">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="14322-140">La meilleure façon de configurer Windows Server pour héberger un service collecteur est d’utiliser une configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="14322-140">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="14322-141">Vous trouverez ci-dessous un exemple de script.</span><span class="sxs-lookup"><span data-stu-id="14322-141">An example script is provided below.</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="14322-142">Utilisation de la ressource xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="14322-142">Using the xDSCWebService resource</span></span>

<span data-ttu-id="14322-143">Le moyen le plus simple de configurer un serveur collecteur web consiste à utiliser la ressource xWebService, incluse dans le module xPSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="14322-143">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="14322-144">Les étapes suivantes expliquent comment utiliser la ressource dans une configuration qui configure le service web.</span><span class="sxs-lookup"><span data-stu-id="14322-144">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="14322-145">Appelez l’applet de commande [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) pour installer le module **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="14322-145">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="14322-146">**Remarque** : **Install-Module** est inclus dans le module **PowerShellGet** de PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="14322-146">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="14322-147">Vous pouvez télécharger le module **PowerShellGet** pour PowerShell 3.0 et 4.0 ici : [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="14322-147">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="14322-148">Obtenez un certificat SSL pour le serveur collecteur DSC auprès d’une autorité de certification approuvée, au sein de votre organisation ou auprès d’une autorité publique.</span><span class="sxs-lookup"><span data-stu-id="14322-148">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="14322-149">Le certificat reçu de l’autorité est généralement au format PFX.</span><span class="sxs-lookup"><span data-stu-id="14322-149">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="14322-150">Installez le certificat sur le nœud qui sera le serveur DSC à l’emplacement par défaut, c’est-à-dire : CERT:\LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="14322-150">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="14322-151">Notez l’empreinte de certificat.</span><span class="sxs-lookup"><span data-stu-id="14322-151">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="14322-152">Sélectionnez un GUID à utiliser comme clé d’inscription.</span><span class="sxs-lookup"><span data-stu-id="14322-152">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="14322-153">Pour en générer un à l’aide de PowerShell, entrez ce qui suit à l’invite PowerShell et appuyez sur Entrée : « ``` [guid]::newGuid()``` » ou « ```New-Guid``` ».</span><span class="sxs-lookup"><span data-stu-id="14322-153">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="14322-154">Cette clé est utilisée par les nœuds clients comme une clé partagée pour l’authentification lors de l’inscription.</span><span class="sxs-lookup"><span data-stu-id="14322-154">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="14322-155">Pour plus d’informations, consultez la section Clé d’inscription ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="14322-155">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="14322-156">Dans PowerShell ISE, démarrez (F5) le script de configuration suivant (inclus dans le dossier Example du module **xPSDesiredStateConfiguration** en tant que Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="14322-156">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="14322-157">Ce script configure le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="14322-157">This script sets up the pull server.</span></span>

```powershell
    configuration Sample_xDscPullServer
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
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName
         {
             WindowsFeature DSCServiceFeature
             {
                 Ensure = 'Present'
                 Name   = 'DSC-Service'
             }

             xDscWebService PSDSCPullServer
             {
                 Ensure                   = 'Present'
                 EndpointName             = 'PSDSCPullServer'
                 Port                     = 8080
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer"
                 CertificateThumbPrint    = $certificateThumbPrint
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'
                 UseSecurityBestPractices = $false
             }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }

```

1. <span data-ttu-id="14322-158">Exécutez la configuration, en passant l’empreinte du certificat SSL comme paramètre **certificateThumbPrint** et une clé d’inscription GUID comme paramètre **RegistrationKey** :</span><span class="sxs-lookup"><span data-stu-id="14322-158">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose

```

#### <a name="registration-key"></a><span data-ttu-id="14322-159">Clé d’inscription</span><span class="sxs-lookup"><span data-stu-id="14322-159">Registration Key</span></span>

<span data-ttu-id="14322-160">Pour que les nœuds clients puissent s’inscrire auprès du serveur afin de pouvoir utiliser les noms de configuration au lieu de l’ID de configuration, une clé d’inscription, créée par la configuration ci-dessus, est enregistrée dans un fichier nommé `RegistrationKeys.txt` dans `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="14322-160">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="14322-161">La clé d’inscription fonctionne comme un secret partagé utilisé lors de l’inscription initiale par le client avec le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="14322-161">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="14322-162">Le client génère un certificat auto-signé qui est utilisé pour l’authentification unique auprès du serveur collecteur une fois l’inscription terminée.</span><span class="sxs-lookup"><span data-stu-id="14322-162">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="14322-163">L’empreinte de ce certificat est stockée localement et associée à l’URL du serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="14322-163">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="14322-164">**Remarque** : Les clés d’inscription ne sont pas prises en charge dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="14322-164">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="14322-165">Pour configurer un nœud pour l’authentification auprès du serveur collecteur, la clé d’inscription doit se trouver dans la métaconfiguration de tous les nœuds cibles que vous prévoyez d’inscrire auprès de ce serveur.</span><span class="sxs-lookup"><span data-stu-id="14322-165">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="14322-166">Notez que la propriété **RegistrationKey** dans la métaconfiguration ci-dessous est supprimée une fois que l’ordinateur cible a été correctement inscrit, et que la valeur « 140a952b-b9d6-406b-b416-e0f759c9c0e4 » doit correspondre à la valeur stockée dans le fichier RegistrationKeys.txt sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="14322-166">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="14322-167">Conservez la valeur de la clé d’inscription en lieu sûr, car elle permet d’inscrire n’importe quel ordinateur cible auprès du serveur.</span><span class="sxs-lookup"><span data-stu-id="14322-167">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
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
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes


```

> <span data-ttu-id="14322-168">**Remarque** : la section **ReportServerWeb** permet d’envoyer les données de rapport au serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="14322-168">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="14322-169">Si la propriété **ConfigurationID** est absente du fichier de métaconfiguration, cela signifie implicitement que ce serveur collecteur prend en charge la version V2 du protocole du serveur collecteur et donc qu’une inscription initiale est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="14322-169">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="14322-170">Inversement, si la propriété **ConfigurationID** est présente, la version V1 du protocole du serveur collecteur est utilisée et il n’y a pas de traitement de l’inscription.</span><span class="sxs-lookup"><span data-stu-id="14322-170">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="14322-171">**Remarque** : dans un scénario PUSH, la version actuelle contient un bogue qui demande de définir une propriété ConfigurationID dans le fichier de métaconfiguration pour les nœuds qui n’ont jamais été inscrits auprès d’un serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="14322-171">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="14322-172">Cette opération permet de forcer le protocole du serveur collecteur V1 et d’éviter les messages d’échec d’inscription.</span><span class="sxs-lookup"><span data-stu-id="14322-172">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="14322-173">Placement des configurations et des ressources</span><span class="sxs-lookup"><span data-stu-id="14322-173">Placing configurations and resources</span></span>

<span data-ttu-id="14322-174">Une fois l’installation du serveur collecteur terminée, vous placez les modules et configurations à extraire par les nœuds cibles dans les dossiers définis par les propriétés **ConfigurationPath** et **ModulePath** de la configuration du serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="14322-174">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="14322-175">Ces fichiers doivent se trouver dans un format spécifique afin que le serveur collecteur puisse les traiter correctement.</span><span class="sxs-lookup"><span data-stu-id="14322-175">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="14322-176">Format du package de module de ressources DSC</span><span class="sxs-lookup"><span data-stu-id="14322-176">DSC resource module package format</span></span>

<span data-ttu-id="14322-177">Chaque module de ressources doit être compressé et nommé selon le modèle `{Module Name}_{Module Version}.zip` suivant.</span><span class="sxs-lookup"><span data-stu-id="14322-177">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="14322-178">Par exemple, un module xWebAdminstration avec une version de module 3.1.2.0 est nommé « xWebAdministration_3.2.1.0.zip ».</span><span class="sxs-lookup"><span data-stu-id="14322-178">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="14322-179">Chaque version d’un module doit être contenue dans un seul fichier zip.</span><span class="sxs-lookup"><span data-stu-id="14322-179">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="14322-180">Étant donné que chaque fichier zip ne contient qu’une seule version d’une ressource, le format du module ajouté dans WMF 5.0 qui contient plusieurs versions de module dans un seul répertoire n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="14322-180">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="14322-181">Cela signifie qu’avant de créer le package des modules de ressources DSC à utiliser avec le serveur collecteur, vous devez apporter une petite modification à la structure de répertoires.</span><span class="sxs-lookup"><span data-stu-id="14322-181">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="14322-182">Le format par défaut des modules contenant les ressources DSC dans WMF 5.0 est « {Dossier du module}\{{Version du module}\DscResources\{Dossier des ressources DSC}\' ».</span><span class="sxs-lookup"><span data-stu-id="14322-182">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="14322-183">Avant de créer les packages pour le serveur collecteur, supprimez simplement le dossier **{Version du module}** pour transformer le chemin en « {Dossier du module}\DscResources\{Dossier des ressources DSC}\' ».</span><span class="sxs-lookup"><span data-stu-id="14322-183">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="14322-184">Ensuite, compressez le dossier comme décrit ci-dessus, et placez ces fichiers zip dans le dossier **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="14322-184">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="14322-185">Utilisez `new-dscchecksum {module zip file}` pour créer un fichier de somme de contrôle pour le module qui vient d’être ajouté.</span><span class="sxs-lookup"><span data-stu-id="14322-185">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="14322-186">Format du fichier MOF de configuration</span><span class="sxs-lookup"><span data-stu-id="14322-186">Configuration MOF format</span></span>

<span data-ttu-id="14322-187">Un fichier MOF de configuration doit être associé à un fichier de somme de contrôle pour que le gestionnaire de configuration local sur un nœud cible puisse valider la configuration.</span><span class="sxs-lookup"><span data-stu-id="14322-187">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="14322-188">Pour créer une somme de contrôle, appelez l’applet de commande [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx).</span><span class="sxs-lookup"><span data-stu-id="14322-188">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span>
<span data-ttu-id="14322-189">L’applet de commande prend un paramètre **Path** qui spécifie le dossier où se trouve la configuration MOF.</span><span class="sxs-lookup"><span data-stu-id="14322-189">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="14322-190">L’applet de commande crée un fichier de somme de contrôle nommé `ConfigurationMOFName.mof.checksum`, où `ConfigurationMOFName` est le nom du fichier MOF de configuration.</span><span class="sxs-lookup"><span data-stu-id="14322-190">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="14322-191">S’il existe plusieurs fichiers MOF de configuration dans le dossier spécifié, une somme de contrôle est créée pour chaque configuration du dossier.</span><span class="sxs-lookup"><span data-stu-id="14322-191">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="14322-192">Placez les fichiers MOF et leurs fichiers de somme de contrôle associés dans le dossier **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="14322-192">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="14322-193">**Remarque** : Si vous modifiez le fichier MOF de configuration de quelque façon que ce soit, vous devez aussi recréer le fichier de somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="14322-193">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="14322-194">Outils</span><span class="sxs-lookup"><span data-stu-id="14322-194">Tooling</span></span>

<span data-ttu-id="14322-195">Pour faciliter la configuration, la validation et la gestion du serveur collecteur, les outils suivants sont fournis comme exemples dans la dernière version du module xPSDesiredStateConfiguration :</span><span class="sxs-lookup"><span data-stu-id="14322-195">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="14322-196">Module permettant de créer le package des modules de ressources DSC et les fichiers de configuration à utiliser sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="14322-196">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="14322-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="14322-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="14322-198">Exemples ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="14322-198">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="14322-199">Script qui valide la configuration du serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="14322-199">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="14322-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="14322-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="14322-201">Solutions de service collecteur de la communauté</span><span class="sxs-lookup"><span data-stu-id="14322-201">Community Solutions for Pull Service</span></span>

<span data-ttu-id="14322-202">La communauté DSC a créé plusieurs solutions pour implémenter le protocole de service collecteur.</span><span class="sxs-lookup"><span data-stu-id="14322-202">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="14322-203">Pour les environnements locaux, elle offre des fonctionnalités de service collecteur et la possibilité de contribuer en retour avec des améliorations incrémentielles.</span><span class="sxs-lookup"><span data-stu-id="14322-203">For on-premises environments these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="14322-204">Tug</span><span class="sxs-lookup"><span data-stu-id="14322-204">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="14322-205">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="14322-205">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="14322-206">Configuration du client collecteur</span><span class="sxs-lookup"><span data-stu-id="14322-206">Pull client configuration</span></span>

<span data-ttu-id="14322-207">Les rubriques suivantes décrivent la configuration des clients collecteurs en détail :</span><span class="sxs-lookup"><span data-stu-id="14322-207">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="14322-208">Configuration d’un client collecteur DSC à l’aide de l’ID de configuration</span><span class="sxs-lookup"><span data-stu-id="14322-208">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="14322-209">Configuration d’un client collecteur DSC à l’aide du nom de configuration</span><span class="sxs-lookup"><span data-stu-id="14322-209">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="14322-210">Configurations partielles</span><span class="sxs-lookup"><span data-stu-id="14322-210">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="14322-211">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14322-211">See also</span></span>

- [<span data-ttu-id="14322-212">Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="14322-212">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="14322-213">Application des configurations</span><span class="sxs-lookup"><span data-stu-id="14322-213">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="14322-214">Utilisation d’un serveur de rapports DSC</span><span class="sxs-lookup"><span data-stu-id="14322-214">Using a DSC report server</span></span>](reportServer.md)
