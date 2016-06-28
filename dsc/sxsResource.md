---
title: Utilisation de ressources avec plusieurs versions
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 01720794aa1d200428c2729463fba92970f9cb56
ms.openlocfilehash: 716ecd9b14976dd70b69a740850ab53670387956

---

# Utilisation de ressources avec plusieurs versions

> S’applique à : Windows PowerShell 5.0

Dans PowerShell 5.0, les ressources DSC peuvent avoir plusieurs versions et celles-ci peuvent être installées sur un ordinateur côte à côte. L’implémentation inclut plusieurs versions d’un module de ressource qui sont contenues dans le même dossier de module.

## Installation de plusieurs versions de ressources côte à côte

Vous pouvez utiliser les paramètres **MinimumVersion**, **MaximumVersion** et **RequiredVersion** de l’applet de commande [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) pour indiquer la version d’un module à installer. L’appel de l’applet de commande **Install-Module** sans spécifier de version installe la version la plus récente.

Par exemple, il existe plusieurs versions du module **xFailOverCluster**, chacun contenant une ressource **xCluster**. Le résultat de l’appel de l’applet de commande **Install-Module** sans spécifier de numéro de version est le suivant :

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Maintenant, si vous rappelez **Install-Module**, mais indiquez la valeur 1.1.0.0 pour le paramètre **RequiredVersion**, le résultat est le suivant :

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## Spécification d’une version de ressource dans une configuration

Si plusieurs ressources sont installées sur un ordinateur, vous devez spécifier la version d’une ressource quand vous l’utilisez dans une configuration. Pour cela, vous devez spécifier le paramètre **ModuleVersion** du mot-clé **Import-DscResource**. Si vous ne parvenez pas à spécifier la version d’un module d’une ressource dont plusieurs versions sont installées, la configuration génère une erreur.

La configuration suivante montre comment spécifier la version de la ressource à appeler :

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

>Remarque : Le paramètre ModuleVersion d’Import-DscResource n’est pas disponible dans PowerShell 4.0. Dans PowerShell 4.0, vous pouvez spécifier une version du module en passant un objet de spécification de module au paramètre ModuleName d’Import-DscResource. Un objet de spécification de module est une table de hachage qui contient les clés ModuleName et RequiredVersion. Par exemple :

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}     
```

Cela fonctionne également dans PowerShell 5.0, mais il est recommandé d’utiliser le paramètre **ModuleVersion**.

## Voir aussi
* [Configurations DSC](configurations.md)
* [Ressources DSC](resources.md)




<!--HONumber=Jun16_HO4-->


