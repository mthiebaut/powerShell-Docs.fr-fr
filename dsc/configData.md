---
title: "Séparation des données de configuration et d’environnement"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 787ac3c3d6ffaf7b1009fe3cfd64a0aefadc32d1
ms.openlocfilehash: 8d305c67fb22e0d27dc1a36ba93369e9633680d3

---

# <a name="separating-configuration-and-environment-data"></a>Séparation des données de configuration et d’environnement

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

À l’aide du paramètre DSC intégré **ConfigurationData**, vous pouvez définir les données qui peuvent être utilisées dans une configuration. Cela vous permet de créer une configuration unique utilisée pour plusieurs nœuds ou différents environnements. Par exemple, si vous développez une application, vous pouvez utiliser une seule configuration pour les environnements de développement et de production et utiliser les données de configuration pour spécifier les données de chaque environnement.

Examinons un exemple très simple pour voir comment cela fonctionne. Nous allons créer une configuration unique qui garantit la présence d’**IIS** sur certains nœuds et la présence d’**Hyper-V** sur d’autres : 

```powershell
Configuration MyDscConfiguration {
    
    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
        
    }
    Node $AllNodes.Where($_.Role -eq "VMHost").NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData = 
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        }

        @{
            NodeName    = 'VM-2'
            FeatureName = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

La dernière ligne de ce script compile la configuration dans des documents MOF, en passant `$MyData` comme valeur du paramètre **ConfigurationData**. `$MyData` spécifie deux nœuds différents, chacun avec son propre `NodeName` et `Role`. La configuration crée les blocs **Nœud** de façon dynamique en prenant la collection de nœuds qu’elle obtient à partir de `$MyData` (en particulier, `$AllNodes`) et filtre cette collection sur la propriété `Role`.

Voyons maintenant en détail comment cela fonctionne.

## <a name="the-configurationdata-parameter"></a>Le paramètre ConfigurationData

Une configuration DSC prend un paramètre nommé **ConfigurationData**, que vous spécifiez lorsque vous compilez la configuration. Pour plus d’informations sur la compilation de configurations, voir [Configurations DSC](configurations.md).

Le paramètre **ConfigurationData** est une table de hachage qui doit contenir au moins une clé nommée **AllNodes**. Il peut également avoir d’autres clés :

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

La valeur de la clé **AllNodes** est un tableau. Chaque élément de ce tableau est également une table de hachage qui doit contenir au moins une clé nommée **NodeName** :

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
        },

 
        @{
            NodeName = "VM-2"
        },

 
        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""   
}
```

Vous pouvez ajouter d’autres clés à chaque table de hachage :

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

Pour appliquer une propriété à tous les nœuds, vous pouvez créer un membre du tableau **AllNodes** dont un **NodeName** a la valeur `*`. Par exemple, pour attribuer la propriété `LogPath` à tous les nœuds, vous pouvez procéder ainsi :

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },

 
        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },

 
        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },

 
        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Ceci équivaut à ajouter une propriété portant le nom `LogPath` avec la valeur `"C:\Logs"` à chacun des autres blocs (`VM-1`, `VM-2` et `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Définition de la table de hachage ConfigurationData

Vous pouvez définir **ConfigurationData** soit comme variable dans le même fichier de script qu’une configuration (comme dans nos exemples précédents), soit dans un fichier .psd1 distinct. Pour définir **ConfigurationData** dans un fichier .psd1, créez un fichier contenant uniquement la table de hachage qui représente les données de configuration.

Par exemple, vous pouvez créer un fichier nommé `MyData.psd1` avec le contenu suivant :

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        }

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

Pour utiliser les données de configuration qui sont définies dans un fichier .psd1, vous passez le chemin et le nom de ce fichier comme valeur du paramètre **ConfigurationData** lors de la compilation de la configuration :

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Utilisation de variables ConfigurationData dans une configuration

DSC fournit trois variables spéciales qui peuvent être utilisées dans un script de configuration : **$AllNodes**, **$Node** et **$ConfigurationData**.

- **$AllNodes** fait référence à l’ensemble de la collection de nœuds définis dans **ConfigurationData**. Vous pouvez filtrer la collection **AllNodes** à l’aide de **.Where()** et **.ForEach()**.
- **Node** fait référence à une entrée particulière dans la collection **AllNodes** une fois qu’elle a été filtrée à l’aide de **.Where()** ou **.ForEach()**.
- **ConfigurationData** fait référence à la table de hachage entière qui est passée comme paramètre lors de la compilation d’une configuration.

## <a name="devops-example"></a>Exemple DevOps

Examinons un exemple complet qui utilise une configuration unique pour configurer les environnements de développement et de production d’un site web. Dans l’environnement de développement, IIS et SQL Server sont installés sur un même nœud. Dans l’environnement de production, IIS et SQL Server sont installés sur des nœuds séparés. Nous allons utiliser un fichier de données de configuration .psd1 pour spécifier les données des deux environnements.

### <a name="configuration-data-file"></a>Fichier de données de configuration

Nous allons définir les données de l’environnement de développement et de production dans un fichier nommé `DevProdEnvData.psd1` comme suit :

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        }

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"

        }

    )

}

    )

}
```

### <a name="configuration-file"></a>Fichier de configuration

À présent, dans la configuration, nous allons filtrer les nœuds que nous avons définis dans `DevProdEnvData.psd1` selon leur rôle (`MSSQL`, `Dev` ou les deux) et les configurer en conséquence. Dans l’environnement de développement, SQL Server et IIS se trouvent sur le même nœud, tandis que dans l’environnement de production, ils se trouvent sur deux nœuds différents. Le contenu du site est également différent, comme spécifié par les propriétés `SiteContents`.

À la fin du script de configuration, nous appelons la configuration (nous la compilons dans un document MOF), en passant `DevProdEnvData.psd1` comme paramètre `$ConfigurationData`.

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.Nodename
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {            
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where($_.Role -contains "Web")
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite 
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }       


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

## <a name="see-also"></a>Voir aussi
- [Options relatives aux informations d’identification dans les données de configuration](configDataCredentials.md)
- [Configurations DSC](configurations.md)


<!--HONumber=Nov16_HO3-->


