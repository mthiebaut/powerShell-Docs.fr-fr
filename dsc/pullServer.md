---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Configuration d’un serveur collecteur web DSC"
ms.openlocfilehash: 03d4d148c87854b146091aa0e8d815b8c35def72
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2017
---
# <a name="setting-up-a-dsc-web-pull-server"></a><span data-ttu-id="90a83-103">Configuration d’un serveur collecteur web DSC</span><span class="sxs-lookup"><span data-stu-id="90a83-103">Setting up a DSC web pull server</span></span>

> <span data-ttu-id="90a83-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="90a83-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="90a83-105">Un serveur collecteur web DSC est un service web dans IIS qui utilise une interface OData pour que les fichiers de configuration DSC soient disponibles à la demande pour les nœuds cibles.</span><span class="sxs-lookup"><span data-stu-id="90a83-105">A DSC web pull server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="90a83-106">Configuration requise pour utiliser un serveur collecteur :</span><span class="sxs-lookup"><span data-stu-id="90a83-106">Requirements for using a pull server:</span></span>

* <span data-ttu-id="90a83-107">Un serveur en cours d’exécution :</span><span class="sxs-lookup"><span data-stu-id="90a83-107">A server running:</span></span>
  - <span data-ttu-id="90a83-108">WMF/PowerShell 5.0 ou version supérieure</span><span class="sxs-lookup"><span data-stu-id="90a83-108">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="90a83-109">Rôle serveur IIS</span><span class="sxs-lookup"><span data-stu-id="90a83-109">IIS server role</span></span>
  - <span data-ttu-id="90a83-110">Service DSC</span><span class="sxs-lookup"><span data-stu-id="90a83-110">DSC Service</span></span>
* <span data-ttu-id="90a83-111">Idéalement, des moyens de générer un certificat pour sécuriser les informations d’identification transmises au gestionnaire de configuration local sur les nœuds cibles</span><span class="sxs-lookup"><span data-stu-id="90a83-111">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="90a83-112">Vous pouvez ajouter le rôle serveur IIS et le service DSC avec l’Assistant Ajout de rôles et fonctionnalités dans le Gestionnaire de serveur, ou à l’aide de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90a83-112">You can add the IIS server role and DSC Service with the Add Roles and Features wizard in Server Manager, or by using PowerShell.</span></span> <span data-ttu-id="90a83-113">Les exemples de scripts inclus dans cette rubrique gèrent également ces deux étapes pour vous.</span><span class="sxs-lookup"><span data-stu-id="90a83-113">The sample scripts included in this topic will handle both of these steps for you as well.</span></span>

## <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="90a83-114">Utilisation de la ressource xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="90a83-114">Using the xDSCWebService resource</span></span>
<span data-ttu-id="90a83-115">Le moyen le plus simple de configurer un serveur collecteur web consiste à utiliser la ressource xWebService, incluse dans le module xPSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="90a83-115">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span> <span data-ttu-id="90a83-116">Les étapes suivantes expliquent comment utiliser la ressource dans une configuration qui configure le service web.</span><span class="sxs-lookup"><span data-stu-id="90a83-116">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="90a83-117">Appelez l’applet de commande [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) pour installer le module **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="90a83-117">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="90a83-118">**Remarque** : **Install-Module** est inclus dans le module **PowerShellGet** de PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="90a83-118">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="90a83-119">Vous pouvez télécharger le module **PowerShellGet** pour PowerShell 3.0 et 4.0 ici : [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="90a83-119">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="90a83-120">Obtenez un certificat SSL pour le serveur collecteur DSC auprès d’une autorité de certification approuvée, au sein de votre organisation ou auprès d’une autorité publique.</span><span class="sxs-lookup"><span data-stu-id="90a83-120">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="90a83-121">Le certificat reçu de l’autorité est généralement au format PFX.</span><span class="sxs-lookup"><span data-stu-id="90a83-121">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="90a83-122">Installez le certificat sur le nœud qui sera le serveur DSC à l’emplacement par défaut, c’est-à-dire : CERT:\LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="90a83-122">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="90a83-123">Notez l’empreinte de certificat.</span><span class="sxs-lookup"><span data-stu-id="90a83-123">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="90a83-124">Sélectionnez un GUID à utiliser comme clé d’inscription.</span><span class="sxs-lookup"><span data-stu-id="90a83-124">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="90a83-125">Pour en générer un à l’aide de PowerShell, entrez ce qui suit à l’invite PowerShell et appuyez sur Entrée : « ``` [guid]::newGuid()``` » ou « ```New-Guid``` ».</span><span class="sxs-lookup"><span data-stu-id="90a83-125">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="90a83-126">Cette clé est utilisée par les nœuds clients comme une clé partagée pour l’authentification lors de l’inscription.</span><span class="sxs-lookup"><span data-stu-id="90a83-126">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="90a83-127">Pour plus d’informations, consultez la section Clé d’inscription ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="90a83-127">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="90a83-128">Dans PowerShell ISE, démarrez (F5) le script de configuration suivant (inclus dans le dossier Example du module **xPSDesiredStateConfiguration** en tant que Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="90a83-128">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="90a83-129">Ce script configure le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="90a83-129">This script sets up the pull server.</span></span>
  
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

1. <span data-ttu-id="90a83-130">Exécutez la configuration, en passant l’empreinte du certificat SSL comme paramètre **certificateThumbPrint** et une clé d’inscription GUID comme paramètre **RegistrationKey** :</span><span class="sxs-lookup"><span data-stu-id="90a83-130">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

## <a name="registration-key"></a><span data-ttu-id="90a83-131">Clé d’inscription</span><span class="sxs-lookup"><span data-stu-id="90a83-131">Registration Key</span></span>
<span data-ttu-id="90a83-132">Pour que les nœuds clients puissent s’inscrire auprès du serveur afin de pouvoir utiliser les noms de configuration au lieu de l’ID de configuration, une clé d’inscription, créée par la configuration ci-dessus, est enregistrée dans un fichier nommé `RegistrationKeys.txt` dans `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="90a83-132">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="90a83-133">La clé d’inscription fonctionne comme un secret partagé utilisé lors de l’inscription initiale par le client avec le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="90a83-133">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="90a83-134">Le client génère un certificat auto-signé qui est utilisé pour l’authentification unique auprès du serveur collecteur une fois l’inscription terminée.</span><span class="sxs-lookup"><span data-stu-id="90a83-134">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="90a83-135">L’empreinte de ce certificat est stockée localement et associée à l’URL du serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="90a83-135">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="90a83-136">**Remarque** : Les clés d’inscription ne sont pas prises en charge dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="90a83-136">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="90a83-137">Pour configurer un nœud pour l’authentification auprès du serveur collecteur, la clé d’inscription doit se trouver dans la métaconfiguration de tous les nœuds cibles que vous prévoyez d’inscrire auprès de ce serveur.</span><span class="sxs-lookup"><span data-stu-id="90a83-137">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="90a83-138">Notez que la propriété **RegistrationKey** dans la métaconfiguration ci-dessous est supprimée une fois que l’ordinateur cible a été correctement inscrit, et que la valeur « 140a952b-b9d6-406b-b416-e0f759c9c0e4 » doit correspondre à la valeur stockée dans le fichier RegistrationKeys.txt sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="90a83-138">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="90a83-139">Conservez la valeur de la clé d’inscription en lieu sûr, car elle permet d’inscrire n’importe quel ordinateur cible auprès du serveur.</span><span class="sxs-lookup"><span data-stu-id="90a83-139">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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
> <span data-ttu-id="90a83-140">**Remarque** : la section **ReportServerWeb** permet d’envoyer les données de rapport au serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="90a83-140">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span> 

<span data-ttu-id="90a83-141">Si la propriété **ConfigurationID** est absente du fichier de métaconfiguration, cela signifie implicitement que ce serveur collecteur prend en charge la version V2 du protocole du serveur collecteur et donc qu’une inscription initiale est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="90a83-141">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="90a83-142">Inversement, si la propriété **ConfigurationID** est présente, la version V1 du protocole du serveur collecteur est utilisée et il n’y a pas de traitement de l’inscription.</span><span class="sxs-lookup"><span data-stu-id="90a83-142">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="90a83-143">**Remarque** : dans un scénario PUSH, la version actuelle contient un bogue qui demande de définir une propriété ConfigurationID dans le fichier de métaconfiguration pour les nœuds qui n’ont jamais été inscrits auprès d’un serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="90a83-143">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="90a83-144">Cette opération permet de forcer le protocole du serveur collecteur V1 et d’éviter les messages d’échec d’inscription.</span><span class="sxs-lookup"><span data-stu-id="90a83-144">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="90a83-145">Placement des configurations et des ressources</span><span class="sxs-lookup"><span data-stu-id="90a83-145">Placing configurations and resources</span></span>

<span data-ttu-id="90a83-146">Une fois l’installation du serveur collecteur terminée, vous placez les modules et configurations à extraire par les nœuds cibles dans les dossiers définis par les propriétés **ConfigurationPath** et **ModulePath** de la configuration du serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="90a83-146">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="90a83-147">Ces fichiers doivent se trouver dans un format spécifique afin que le serveur collecteur puisse les traiter correctement.</span><span class="sxs-lookup"><span data-stu-id="90a83-147">These files need to be in a specific format in order for the pull server to correctly process them.</span></span> 

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="90a83-148">Format du package de module de ressources DSC</span><span class="sxs-lookup"><span data-stu-id="90a83-148">DSC resource module package format</span></span>

<span data-ttu-id="90a83-149">Chaque module de ressources doit être compressé et nommé selon le modèle `{Module Name}_{Module Version}.zip` suivant.</span><span class="sxs-lookup"><span data-stu-id="90a83-149">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="90a83-150">Par exemple, un module xWebAdminstration avec une version de module 3.1.2.0 est nommé « xWebAdministration_3.2.1.0.zip ».</span><span class="sxs-lookup"><span data-stu-id="90a83-150">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="90a83-151">Chaque version d’un module doit être contenue dans un seul fichier zip.</span><span class="sxs-lookup"><span data-stu-id="90a83-151">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="90a83-152">Étant donné que chaque fichier zip ne contient qu’une seule version d’une ressource, le format du module ajouté dans WMF 5.0 qui contient plusieurs versions de module dans un seul répertoire n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="90a83-152">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="90a83-153">Cela signifie qu’avant de créer le package des modules de ressources DSC à utiliser avec le serveur collecteur, vous devez apporter une petite modification à la structure de répertoires.</span><span class="sxs-lookup"><span data-stu-id="90a83-153">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="90a83-154">Le format par défaut des modules contenant les ressources DSC dans WMF 5.0 est « {Dossier du module}\{{Version du module}\DscResources\{Dossier des ressources DSC}\' ».</span><span class="sxs-lookup"><span data-stu-id="90a83-154">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="90a83-155">Avant de créer les packages pour le serveur collecteur, supprimez simplement le dossier **{Version du module}** pour transformer le chemin en « {Dossier du module}\DscResources\{Dossier des ressources DSC}\' ».</span><span class="sxs-lookup"><span data-stu-id="90a83-155">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="90a83-156">Ensuite, compressez le dossier comme décrit ci-dessus, et placez ces fichiers zip dans le dossier **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="90a83-156">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="90a83-157">Utilisez `new-dscchecksum {module zip file}` pour créer un fichier de somme de contrôle pour le module qui vient d’être ajouté.</span><span class="sxs-lookup"><span data-stu-id="90a83-157">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="90a83-158">Format du fichier MOF de configuration</span><span class="sxs-lookup"><span data-stu-id="90a83-158">Configuration MOF format</span></span> 
<span data-ttu-id="90a83-159">Un fichier MOF de configuration doit être associé à un fichier de somme de contrôle pour que le gestionnaire de configuration local sur un nœud cible puisse valider la configuration.</span><span class="sxs-lookup"><span data-stu-id="90a83-159">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="90a83-160">Pour créer une somme de contrôle, appelez l’applet de commande [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx).</span><span class="sxs-lookup"><span data-stu-id="90a83-160">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="90a83-161">L’applet de commande prend un paramètre **Path** qui spécifie le dossier où se trouve la configuration MOF.</span><span class="sxs-lookup"><span data-stu-id="90a83-161">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="90a83-162">L’applet de commande crée un fichier de somme de contrôle nommé `ConfigurationMOFName.mof.checksum`, où `ConfigurationMOFName` est le nom du fichier MOF de configuration.</span><span class="sxs-lookup"><span data-stu-id="90a83-162">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="90a83-163">S’il existe plusieurs fichiers MOF de configuration dans le dossier spécifié, une somme de contrôle est créée pour chaque configuration du dossier.</span><span class="sxs-lookup"><span data-stu-id="90a83-163">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="90a83-164">Placez les fichiers MOF et leurs fichiers de somme de contrôle associés dans le dossier **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="90a83-164">Place the MOF files and their associated checksum files in the the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="90a83-165">**Remarque** : Si vous modifiez le fichier MOF de configuration de quelque façon que ce soit, vous devez aussi recréer le fichier de somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="90a83-165">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="tooling"></a><span data-ttu-id="90a83-166">Outils</span><span class="sxs-lookup"><span data-stu-id="90a83-166">Tooling</span></span>
<span data-ttu-id="90a83-167">Pour faciliter la configuration, la validation et la gestion du serveur collecteur, les outils suivants sont fournis comme exemples dans la dernière version du module xPSDesiredStateConfiguration :</span><span class="sxs-lookup"><span data-stu-id="90a83-167">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>
1. <span data-ttu-id="90a83-168">Module permettant de créer le package des modules de ressources DSC et les fichiers de configuration à utiliser sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="90a83-168">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="90a83-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="90a83-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="90a83-170">Exemples ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="90a83-170">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="90a83-171">Script qui valide la configuration du serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="90a83-171">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="90a83-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="90a83-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>


## <a name="pull-client-configuration"></a><span data-ttu-id="90a83-173">Configuration du client collecteur</span><span class="sxs-lookup"><span data-stu-id="90a83-173">Pull client configuration</span></span> 
<span data-ttu-id="90a83-174">Les rubriques suivantes décrivent la configuration des clients collecteurs en détail :</span><span class="sxs-lookup"><span data-stu-id="90a83-174">The following topics describe setting up pull clients in detail:</span></span>

* [<span data-ttu-id="90a83-175">Configuration d’un client collecteur DSC à l’aide de l’ID de configuration</span><span class="sxs-lookup"><span data-stu-id="90a83-175">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
* [<span data-ttu-id="90a83-176">Configuration d’un client collecteur DSC à l’aide du nom de configuration</span><span class="sxs-lookup"><span data-stu-id="90a83-176">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="90a83-177">Configurations partielles</span><span class="sxs-lookup"><span data-stu-id="90a83-177">Partial configurations</span></span>](partialConfigs.md)


## <a name="see-also"></a><span data-ttu-id="90a83-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90a83-178">See also</span></span>
* [<span data-ttu-id="90a83-179">Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="90a83-179">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="90a83-180">Application des configurations</span><span class="sxs-lookup"><span data-stu-id="90a83-180">Enacting configurations</span></span>](enactingConfigurations.md)
* [<span data-ttu-id="90a83-181">Utilisation d’un serveur de rapports DSC</span><span class="sxs-lookup"><span data-stu-id="90a83-181">Using a DSC report server</span></span>](reportServer.md)

