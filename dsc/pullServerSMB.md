# Configuration d’un serveur collecteur SMB DSC

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Un serveur collecteur [SMB](https://technet.microsoft.com/en-us/library/hh831795.aspx) DSC est un partage de fichiers SMB qui fournit des fichiers de configuration DSC et/ou des ressources DSC
aux nœuds cibles quand ces derniers les demandent.

Pour utiliser un serveur collecteur SMB pour DSC, vous devez effectuer les étapes suivantes :
- Configurer un partage de fichiers SMB sur un serveur qui exécute PowerShell 4.0 ou version ultérieure
- Configurer un client qui exécute PowerShell 4.0 ou version ultérieure pour l’extraction à partir de ce partage SMB

## Utilisation de la ressource xSmbShare pour créer un partage de fichiers SMB

Il existe plusieurs façons de configurer un partage de fichiers SMB, mais nous allons le faire à l’aide de DSC.

### Installer la ressource xSmbShare

Appelez l’applet de commande [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) pour installer le module **xSmbShare**.
>**Remarque** : **Install-Module** est inclus dans le module **PowerShellGet** de PowerShell 5.0. Vous pouvez télécharger le module **PowerShellGet** pour PowerShell 3.0 et 4.0
>à la page [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186) (Aperçu des modules PowerShell PackageManagement). **xSmbShare** contient la ressource DSC **xSmbShare** qui peut être utilisée
pour créer un partage de fichiers SMB.

### Créer le répertoire et le partage de fichiers

La configuration suivante utilise la ressource [File](fileResource.md) pour créer le répertoire du partage et la ressource **xSmbShare** pour configurer le partage SMB :

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

La configuration crée le répertoire `C:\DscSmbShare` s’il n’existe pas et utilise ensuite ce répertoire comme partage de fichiers SMB. L’autorisation **FullAccess** doit être accordée à tous les
comptes devant écrire ou supprimer des entrées dans le partage de fichiers, et l’autorisation **ReadAccess** doit être accordée à tous les nœuds clients obtenant des configurations et/ou des ressources DSC du partage (
étant donné que DSC s’exécute sous le compte système par défaut, l’ordinateur doit donc avoir accès au partage).


### Donner accès au système de fichiers pour le client collecteur

L’autorisation **ReadAccess** accordée à un nœud client permet à ce dernier d’accéder au partage SMB, mais pas aux fichiers et dossiers dans ce partage. Vous devez accorder explicitement l’accès au dossier et aux sous-dossiers
du partage SMB pour les nœuds clients. Vous pouvez le faire avec DSC à l’aide de la ressource **cNtfsPermissionEntry**, qui est contenue dans le module [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0)
. La configuration suivante ajoute un bloc **cNtfsPermissionEntry** qui accorde un accès ReadAndExecute au client collecteur :

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

## Placement des configurations et des ressources

Enregistrez les fichiers MOF de configuration et/ou les ressources DSC que les nœuds clients doivent extraire dans le dossier de partage SMB.

Les fichiers MOF de configuration doivent être nommés _ConfigurationID_.mof, où _ConfigurationID_ est la valeur de la propriété **ConfigurationID** du gestionnaire de configuration local du nœud cible. Pour plus d’informations sur
la configuration des clients collecteurs, consultez [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md).

>**Remarque :** Vous devez utiliser les ID de configuration si vous utilisez un serveur collecteur SMB. Les noms de configuration ne sont pas pris en charge pour SMB.

Toutes les ressources nécessaires pour le client doivent être placées dans le dossier de partage SMB sous forme de fichiers `.zip` archivés.  

## Création de la somme de contrôle MOF
Un fichier MOF de configuration doit être associé à un fichier de somme de contrôle pour que le gestionnaire de configuration local sur un nœud cible puisse valider la configuration. 
Pour créer une somme de contrôle, appelez l’applet de commande [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx). L’applet de commande prend un paramètre **Path** qui spécifie le dossier 
où se trouve le fichier MOF de configuration. L’applet de commande crée un fichier de somme de contrôle nommé `ConfigurationMOFName.mof.checksum`, où `ConfigurationMOFName` est le nom du fichier MOF de configuration. 
S’il existe plusieurs fichiers MOF de configuration dans le dossier spécifié, une somme de contrôle est créée pour chaque configuration du dossier.

Le fichier de somme de contrôle doit être présent dans le même répertoire que celui du fichier MOF de configuration (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` par défaut), et avoir le même nom, mais avec l’extension `.checksum`.

>**Remarque** : Si vous modifiez le fichier MOF de configuration de quelque façon que ce soit, vous devez aussi recréer le fichier de somme de contrôle.

## Accusés de réception

Un remerciement particulier aux personnes suivantes :

- Mike F. Robbins, dont les billets sur l’utilisation de SMB pour DSC ont permis de documenter le contenu de cette rubrique. Son blog : [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, qui a créé le module **cNtfsAccessControl**. La source de ce module est à l’adresse https://github.com/SNikalaichyk/cNtfsAccessControl.

## Voir aussi
- [Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell](overview.md)
- [Application des configurations](enactingConfigurations.md)
- [Configuration d’un client collecteur à l’aide de l’ID de configuration](pullClientConfigID.md)

 

<!--HONumber=Mar16_HO2-->


