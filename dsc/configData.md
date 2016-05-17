---
title:   Séparation des données de configuration et d’environnement
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Séparation des données de configuration et d’environnement

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Avec la configuration de l’état souhaité (DSC) de Windows PowerShell, il est possible de séparer les données de configuration de la logique de configuration. La configuration structurelle (par exemple, une configuration qui nécessiterait l’installation d’IIS) est séparée de la configuration de l’environnement. Autrement dit, qu’il s’agisse d’un environnement de test ou de production, même si les noms des nœuds sont différents, la même configuration est appliquée. Les avantages sont les suivants :

* Vous pouvez réutiliser vos données de configuration pour plusieurs ressources, nœuds et configurations.
* La logique de configuration est plus facilement réutilisable si elle ne contient pas de données codées en dur. Cette règle se rapproche des recommandations relatives à l’écriture de scripts pour les fonctions.
* Si certaines données doivent être modifiées, vous pouvez effectuer les modifications depuis un seul et même emplacement, ce qui vous permet de gagner du temps et de réduire le risque d’erreurs.

## Exemples et concepts de base

Pour spécifier la partie environnement de la configuration, DSC utilise le paramètre **ConfigurationData**, qui est une table de hachage (elle peut également accepter un fichier .psd1 contenant la table de hachage). Cette table de hachage doit avoir au moins une clé **AllNodes** avec une valeur structurée. Par exemple :

```powershell
$MyData = 
@{
    AllNodes = @();
    NonNodeData = ""   
}
```

Notez la clé AllNodes, dont la valeur est un tableau. Chaque élément de ce tableau est également une table de hachage qui nécessite NodeName comme clé :

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

Dans AllNodes, chaque entrée de table de hachage correspond aux données de configuration d’un nœud de la configuration. Outre la clé NodeName nécessaire, vous pouvez ajouter d’autres clés à la table de hachage, comme par exemple les suivantes :

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3";
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

DSC propose trois variables spéciales que vous pouvez utiliser dans le script de configuration :

* **$AllNodes** : référence tous les nœuds. Vous pouvez utiliser le filtrage avec **.Where()** et **.ForEach()**. Au lieu de coder en dur le nom des nœuds quand vous sélectionnez les nœuds à utiliser, vous pouvez écrire quelque chose comme ceci pour sélectionner VM-1 et VM-3 dans l’exemple ci-dessus :

```powershell
configuration MyConfiguration
{
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
    }
}
```

* **$Node** : une fois que l’ensemble de nœuds est filtré, vous pouvez utiliser $Node pour référencer l’entrée en question. Par exemple :

```powershell
configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }
    }
}
```

Pour appliquer une propriété à l’ensemble des nœuds, vous pouvez définir ceci : NodeName = “*”. Par exemple, pour attribuer la propriété LogPath à tous les nœuds, vous pouvez effectuer ceci :

```
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3";
            Role     = "WebServer";
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );
}
```

* **$ConfigurationData** : vous pouvez utiliser cette variable à l’intérieur d’une configuration pour accéder à la table de hachage des données de configuration passée comme paramètre. Par exemple :

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1";
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2";
            Role     = "SQLServer"
        },
 

        @{
            NodeName = "VM-3";
            Role     = "WebServer";
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );

    NonNodeData = 
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }   
} 

configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```

Vous trouverez un exemple complet dans le [module xWebAdministration](https://powershellgallery.com/packages/xWebAdministration).



<!--HONumber=May16_HO3-->


