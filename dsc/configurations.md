---
title:   Configurations DSC
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Configurations DSC

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Les configurations DSC sont des scripts PowerShell qui définissent un type spécial de fonction. 
Pour définir une configuration, utilisez le mot clé PowerShell __Configuration__.

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
```

Enregistrez le script comme fichier .ps1.

## Syntaxe de configuration

Un script de configuration comprend les éléments suivants :

- Le bloc **Configuration**. Il s’agit du bloc de script le plus externe. Pour le définir, utilisez le mot clé **Configuration**, puis attribuez-lui un nom. Ici, le nom de la configuration est « MyDscConfiguration ».
- Un ou plusieurs blocs **Node**. Ils définissent les nœuds (ordinateurs ou machines virtuelles) que vous configurez. Dans la configuration ci-dessus, un bloc **Node** cible un ordinateur nommé « TEST-PC1 ».
- Un ou plusieurs blocs de ressources. C’est là que la configuration définit les propriétés pour les ressources qu’elle configure. Ici, nous avons deux blocs de ressources qui appellent tous les deux la ressource « WindowsFeature ».

Dans un bloc **Configuration**, vous pouvez faire tout ce qu’il est possible de faire dans une fonction PowerShell. Par exemple, dans l’exemple précédent, si vous ne vouliez pas coder en dur le nom de l’ordinateur cible dans la configuration, vous auriez pu ajouter un paramètre pour le nom du nœud :

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
```

Dans cet exemple, vous spécifiez le nom du nœud en lui passant comme paramètre $ComputerName quand vous [compilez la configuration](# Compiling the configuration). Par défaut, le nom est « localhost ».

## Compilation de la configuration.
Avant de pouvoir promulguer une configuration, vous devez la compiler dans un document MOF. Pour cela, appelez la configuration comme pour une fonction PowerShell.
>__Remarque__ : Pour appeler une configuration, la fonction doit se trouver dans la portée globale (comme pour toutes les fonctions PowerShell). Vous avez le choix entre « dot sourcer » le script, exécuter le script de configuration avec la touche F5 ou cliquer sur le bouton __Exécuter le script__ dans l’environnement ISE. Pour « dot sourcer » le script, exécutez la commande `. .\myConfig.ps1`, où `myConfig.ps1` correspond au nom du fichier de script qui contient votre configuration.

Quand vous appelez la configuration, les éléments suivants sont créés :

- Un dossier dans le répertoire actif portant le même nom que la configuration.
- Un fichier nommé _NodeName_.mof dans le nouveau répertoire, où _NodeName_ correspond au nom du nœud cible de la configuration. S’il existe plusieurs nœuds, un fichier MOF est créé pour chaque nœud.

>__Remarque__ : Le fichier MOF contient toutes les informations de configuration du nœud cible. Il est donc important de le sécuriser. Pour plus d’informations, consultez [Sécurisation du fichier MOF](secureMOF.md).

Après la compilation de la première configuration, vous obtenez la structure de dossiers suivante :

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 TEST-PC1.mof
```  

Si la configuration prend un paramètre, comme dans le deuxième exemple, le paramètre doit être fourni au moment de la compilation. Voici à quoi cela ressemble :

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration -ComputerName 'MyTestNode'
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```      

## Utilisation de DependsOn
__DependsOn__ est un mot clé DSC très utile. En général (même si ce n’est pas toujours le cas), DSC applique les ressources dans l’ordre dans lequel elles figurent dans la configuration. Toutefois, __DependsOn__ spécifie les ressources qui dépendent d’autres ressources, et le gestionnaire de configuration local permet de s’assurer qu’elles sont appliquées dans le bon ordre, quel que soit l’ordre dans lequel les instances de ressources sont définies. Par exemple, une configuration peut spécifier qu’une instance de la ressource __User__ dépend de l’existence d’une instance __Group__ :

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}
```

## Utilisation de nouvelles ressources dans la configuration
Si vous avez exécuté les exemples précédents, vous avez peut-être remarqué un avertissement disant que vous utilisez une ressource sans l’avoir importée explicitement.
Actuellement, DSC est fourni avec 12 ressources contenues dans le module PSDesiredStateConfiguration. Les autres ressources des modules externes doivent être placées dans `$env:PSModulePath` pour être reconnues par le gestionnaire de configuration local. Une nouvelle applet de commande, [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), peut être utilisée pour déterminer quelles ressources sont installées sur le système et lesquelles peuvent être utilisées par le gestionnaire de configuration local. 
Une fois ces modules placés dans `$env:PSModulePath` et correctement reconnus par [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), ils doivent encore être chargés dans votre configuration. __Import-DscResource__ est un mot clé dynamique qui peut être reconnu uniquement au sein d’un bloc __Configuration__ (ce n’est donc pas une applet de commande). __Import-DscResource__ accepte deux paramètres :
* __ModuleName__ est recommandé pour l’utilisation d’__Import-DscResource__. Il accepte le nom du module qui contient les ressources à importer (ainsi qu’un tableau de chaînes comprenant des noms de modules). 
* __Name__ correspond au nom de la ressource à importer. Il ne s’agit pas du nom convivial retourné comme « Name » par [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), mais du nom de classe utilisé lors de la définition du schéma de la ressource (retourné comme __ResourceType__ par [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)). 

## Voir aussi
* [Vue d’ensemble de la fonctionnalité Desired State Configuration de Windows PowerShell](overview.md)
* [Ressources DSC](resources.md)
* [Configuration du Gestionnaire de configuration local](metaConfig.md)



<!--HONumber=May16_HO3-->


