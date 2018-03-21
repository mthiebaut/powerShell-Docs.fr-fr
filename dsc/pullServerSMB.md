---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Configuration d’un serveur collecteur SMB DSC"
ms.openlocfilehash: ff3faeb1952e6116cf97b1aaf8f125d8931dd35e
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="75e48-103">Configuration d’un serveur collecteur SMB DSC</span><span class="sxs-lookup"><span data-stu-id="75e48-103">Setting up a DSC SMB pull server</span></span>

><span data-ttu-id="75e48-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="75e48-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="75e48-105">Un serveur collecteur [SMB](https://technet.microsoft.com/library/hh831795.aspx) DSC est un ordinateur qui héberge des partages de fichiers SMB qui fournissent des fichiers de configuration DSC et des ressources DSC aux nœuds cibles quand ces derniers les demandent.</span><span class="sxs-lookup"><span data-stu-id="75e48-105">A DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="75e48-106">Pour utiliser un serveur collecteur SMB pour DSC, vous devez effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="75e48-106">To use an SMB pull server for DSC, you have to:</span></span>
- <span data-ttu-id="75e48-107">Configurer un partage de fichiers SMB sur un serveur qui exécute PowerShell 4.0 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="75e48-107">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="75e48-108">Configurer un client qui exécute PowerShell 4.0 ou version ultérieure pour l’extraction à partir de ce partage SMB</span><span class="sxs-lookup"><span data-stu-id="75e48-108">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="75e48-109">Utilisation de la ressource xSmbShare pour créer un partage de fichiers SMB</span><span class="sxs-lookup"><span data-stu-id="75e48-109">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="75e48-110">Il existe plusieurs façons de configurer un partage de fichiers SMB, mais nous allons le faire à l’aide de DSC.</span><span class="sxs-lookup"><span data-stu-id="75e48-110">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="75e48-111">Installer la ressource xSmbShare</span><span class="sxs-lookup"><span data-stu-id="75e48-111">Install the xSmbShare resource</span></span>

<span data-ttu-id="75e48-112">Appelez l’applet de commande [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) pour installer le module **xSmbShare**.</span><span class="sxs-lookup"><span data-stu-id="75e48-112">Call the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xSmbShare** module.</span></span>
><span data-ttu-id="75e48-113">**Remarque** : **Install-Module** est inclus dans le module **PowerShellGet** de PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="75e48-113">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="75e48-114">Vous pouvez télécharger le module **PowerShellGet** pour PowerShell 3.0 et 4.0 ici : [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="75e48-114">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> <span data-ttu-id="75e48-115">**xSmbShare** contient la ressource DSC **xSmbShare** qui peut être utilisée pour créer un partage de fichiers SMB.</span><span class="sxs-lookup"><span data-stu-id="75e48-115">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="75e48-116">Créer le répertoire et le partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="75e48-116">Create the directory and file share</span></span>

<span data-ttu-id="75e48-117">La configuration suivante utilise la ressource [File](fileResource.md) pour créer le répertoire du partage et la ressource **xSmbShare** pour configurer le partage SMB :</span><span class="sxs-lookup"><span data-stu-id="75e48-117">The following configuration uses the [File](fileResource.md) resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
 
    Node localhost {
 
        File CreateFolder {
 
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
 
        }
 
        xSMBShare CreateShare {
 
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
 
        }
        
    }
 
}
```

<span data-ttu-id="75e48-118">La configuration crée le répertoire `C:\DscSmbShare` s’il n’existe pas et utilise ensuite ce répertoire comme partage de fichiers SMB.</span><span class="sxs-lookup"><span data-stu-id="75e48-118">The configuration creates the directory `C:\DscSmbShare` if it doesn't already exists, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="75e48-119">L’autorisation **FullAccess** doit être accordée à tous les comptes nécessitant des droits en écriture/suppression dans le partage de fichiers, et l’autorisation **ReadAccess** doit être accordée à tous les nœuds client obtenant des configurations et/ou ressources DSC à partir du partage (étant donné que DSC s’exécute sous le compte système par défaut, l’ordinateur doit donc avoir accès au partage).</span><span class="sxs-lookup"><span data-stu-id="75e48-119">**FullAccess** should be given to any account that needs to write to or delete from the file share, and **ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share ( this is because DSC runs as the system account by default, so the computer itself has to have access to the share).</span></span>


### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="75e48-120">Donner accès au système de fichiers pour le client collecteur</span><span class="sxs-lookup"><span data-stu-id="75e48-120">Give file system access to the pull client</span></span>

<span data-ttu-id="75e48-121">L’autorisation **ReadAccess** accordée à un nœud client permet à ce dernier d’accéder au partage SMB, mais pas aux fichiers et dossiers dans ce partage.</span><span class="sxs-lookup"><span data-stu-id="75e48-121">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="75e48-122">Vous devez accorder explicitement l’accès au dossier et aux sous-dossiers du partage SMB pour les nœuds clients.</span><span class="sxs-lookup"><span data-stu-id="75e48-122">You have to explicitly grant client nodes access to the SMB share folder and sub-folders.</span></span> <span data-ttu-id="75e48-123">Vous pouvez le faire avec DSC à l’aide de la ressource **cNtfsPermissionEntry**, qui est contenue dans le module [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0).</span><span class="sxs-lookup"><span data-stu-id="75e48-123">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="75e48-124">La configuration suivante ajoute un bloc **cNtfsPermissionEntry** qui accorde un accès ReadAndExecute au client collecteur :</span><span class="sxs-lookup"><span data-stu-id="75e48-124">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl
 
    Node localhost {
 
        File CreateFolder {
 
            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
 
        }
 
        xSMBShare CreateShare {
 
            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
 
        }

        cNtfsPermissionEntry PermissionSet1 {
            
        Ensure = 'Present'
        Path = 'C:\DSCSMB'
        Principal = 'myDomain\Contoso-Server$'
        AccessControlInformation = @(
            cNtfsAccessControlInformation
            {
                AccessControlType = 'Allow'
                FileSystemRights = 'ReadAndExecute'
                Inheritance = 'ThisFolderSubfoldersAndFiles'
                NoPropagateInherit = $false
            }
        )
        DependsOn = '[File]CreateFolder'
        
        }
 
        
    }
 
}
```

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="75e48-125">Placement des configurations et des ressources</span><span class="sxs-lookup"><span data-stu-id="75e48-125">Placing configurations and resources</span></span>

<span data-ttu-id="75e48-126">Enregistrez les fichiers MOF de configuration et/ou les ressources DSC que les nœuds clients doivent extraire dans le dossier de partage SMB.</span><span class="sxs-lookup"><span data-stu-id="75e48-126">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="75e48-127">Les fichiers MOF de configuration doivent être nommés _ConfigurationID_.mof, où _ConfigurationID_ est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible.</span><span class="sxs-lookup"><span data-stu-id="75e48-127">Any configuration MOF file must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="75e48-128">Pour plus d’informations sur la configuration des clients collecteurs, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="75e48-128">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="75e48-129">**Remarque :** Vous devez utiliser les ID de configuration si vous utilisez un serveur collecteur SMB.</span><span class="sxs-lookup"><span data-stu-id="75e48-129">**Note:** You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="75e48-130">Les noms de configuration ne sont pas pris en charge pour SMB.</span><span class="sxs-lookup"><span data-stu-id="75e48-130">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="75e48-131">Chaque module de ressources doit être compressé et nommé selon le modèle `{Module Name}_{Module Version}.zip` suivant.</span><span class="sxs-lookup"><span data-stu-id="75e48-131">Each resource module needs to be zipped and named according the the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="75e48-132">Par exemple, un module xWebAdminstration avec une version de module 3.1.2.0 est nommé « xWebAdministration_3.2.1.0.zip ».</span><span class="sxs-lookup"><span data-stu-id="75e48-132">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="75e48-133">Chaque version d’un module doit être contenue dans un seul fichier zip.</span><span class="sxs-lookup"><span data-stu-id="75e48-133">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="75e48-134">Étant donné que chaque fichier zip ne contient qu’une seule version d’une ressource, le format du module ajouté dans WMF 5.0 qui contient plusieurs versions de module dans un seul répertoire n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="75e48-134">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="75e48-135">Cela signifie qu’avant de créer le package des modules de ressources DSC à utiliser avec le serveur collecteur, vous devez apporter une petite modification à la structure de répertoires.</span><span class="sxs-lookup"><span data-stu-id="75e48-135">This means that before packaging up DSC resource modules for use with pull server you need to make a small change to the directory structure.</span></span> <span data-ttu-id="75e48-136">Le format par défaut des modules contenant les ressources DSC dans WMF 5.0 est « {Dossier du module}\{{Version du module}\DscResources\{Dossier des ressources DSC}\' ».</span><span class="sxs-lookup"><span data-stu-id="75e48-136">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="75e48-137">Avant de créer les packages pour le serveur collecteur, supprimez simplement le dossier **{Version du module}** pour transformer le chemin en « {Dossier du module}\DscResources\{Dossier des ressources DSC}\' ».</span><span class="sxs-lookup"><span data-stu-id="75e48-137">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="75e48-138">Ensuite, compressez le dossier comme décrit ci-dessus, et placez ces fichiers zip dans le dossier de partage SMB.</span><span class="sxs-lookup"><span data-stu-id="75e48-138">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span> 

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="75e48-139">Création de la somme de contrôle MOF</span><span class="sxs-lookup"><span data-stu-id="75e48-139">Creating the MOF checksum</span></span>
<span data-ttu-id="75e48-140">Un fichier MOF de configuration doit être associé à un fichier de somme de contrôle pour que le gestionnaire de configuration local sur un nœud cible puisse valider la configuration.</span><span class="sxs-lookup"><span data-stu-id="75e48-140">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="75e48-141">Pour créer une somme de contrôle, appelez l’applet de commande [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx).</span><span class="sxs-lookup"><span data-stu-id="75e48-141">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="75e48-142">L’applet de commande prend un paramètre **Path** qui spécifie le dossier où se trouve la configuration MOF.</span><span class="sxs-lookup"><span data-stu-id="75e48-142">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="75e48-143">L’applet de commande crée un fichier de somme de contrôle nommé `ConfigurationMOFName.mof.checksum`, où `ConfigurationMOFName` est le nom du fichier MOF de configuration.</span><span class="sxs-lookup"><span data-stu-id="75e48-143">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="75e48-144">S’il existe plusieurs fichiers MOF de configuration dans le dossier spécifié, une somme de contrôle est créée pour chaque configuration du dossier.</span><span class="sxs-lookup"><span data-stu-id="75e48-144">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="75e48-145">Le fichier de somme de contrôle doit être présent dans le même répertoire que celui du fichier MOF de configuration (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` par défaut), et avoir le même nom, mais avec l’extension `.checksum`.</span><span class="sxs-lookup"><span data-stu-id="75e48-145">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

><span data-ttu-id="75e48-146">**Remarque** : Si vous modifiez le fichier MOF de configuration de quelque façon que ce soit, vous devez aussi recréer le fichier de somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="75e48-146">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="75e48-147">Configuration d’un client collecteur pour SMB</span><span class="sxs-lookup"><span data-stu-id="75e48-147">Setting up a pull client for SMB</span></span>

<span data-ttu-id="75e48-148">Pour configurer un client qui extrait des configurations et/ou des ressources à partir d’un partage SMB, configurez le Gestionnaire de configuration local (LCM) du client avec des blocs **ConfigurationRepositoryShare** et **ResourceRepositoryShare** qui spécifient le partage à partir duquel les configurations et les ressources DSC sont extraites.</span><span class="sxs-lookup"><span data-stu-id="75e48-148">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="75e48-149">Pour plus d’informations sur la configuration du gestionnaire de configuration local, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="75e48-149">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="75e48-150">**Remarque :** par souci de simplicité, cet exemple utilise **PSDscAllowPlainTextPassword** pour autoriser la transmission d’un mot de passe en texte clair au paramètre **Informations d’identification**.</span><span class="sxs-lookup"><span data-stu-id="75e48-150">**Note:** For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="75e48-151">Pour plus d’informations sur la transmission plus sécurisée d’informations d’identification, consultez [Options d’informations d’identification dans les données de configuration](configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="75e48-151">For information about passing credentials more securely, see [Credentials Options in Configuration Data](configDataCredentials.md).</span></span>

><span data-ttu-id="75e48-152">**Remarque :** vous devez spécifier un **ConfigurationID** dans le bloc **Paramètres** d’une métaconfiguration pour un serveur d’extraction SMB, même si vous ne faites qu’extraire des ressources.</span><span class="sxs-lookup"><span data-stu-id="75e48-152">**Note:** You must specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }
         
         ConfigurationRepositoryShare SmbConfigShare      
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
            
        }      
    }
}

$ConfigurationData = @{

    AllNodes = @(

        @{

            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves

            NodeName="localhost"

            PSDscAllowPlainTextPassword = $true

        })

        

}
```

## <a name="acknowledgements"></a><span data-ttu-id="75e48-153">Accusés de réception</span><span class="sxs-lookup"><span data-stu-id="75e48-153">Acknowledgements</span></span>

<span data-ttu-id="75e48-154">Un remerciement particulier aux personnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="75e48-154">Special thanks to the following:</span></span>

- <span data-ttu-id="75e48-155">Mike F. Robbins, dont les billets sur l’utilisation de SMB pour DSC ont permis de documenter le contenu de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="75e48-155">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="75e48-156">Son blog : [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="75e48-156">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="75e48-157">Serge Nikalaichyk, qui a créé le module **cNtfsAccessControl**.</span><span class="sxs-lookup"><span data-stu-id="75e48-157">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="75e48-158">La source de ce module se trouve ici : https://github.com/SNikalaichyk/cNtfsAccessControl.</span><span class="sxs-lookup"><span data-stu-id="75e48-158">The source for this module is at https://github.com/SNikalaichyk/cNtfsAccessControl.</span></span>

## <a name="see-also"></a><span data-ttu-id="75e48-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75e48-159">See also</span></span>
- [<span data-ttu-id="75e48-160">Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="75e48-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="75e48-161">Application des configurations</span><span class="sxs-lookup"><span data-stu-id="75e48-161">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="75e48-162">Configuration d’un client collecteur à l’aide de l’ID de configuration</span><span class="sxs-lookup"><span data-stu-id="75e48-162">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

 
