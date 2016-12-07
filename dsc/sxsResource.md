---
title: Utilisation de ressources avec plusieurs versions
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: a3f2cf37eb185124d73443bbe42b5fcc82034f15
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="using-resources-with-multiple-versions"></a>Utilisation de ressources avec plusieurs versions

> S’applique à : Windows PowerShell 5.0

Dans PowerShell 5.0, les ressources DSC peuvent avoir plusieurs versions et celles-ci peuvent être installées sur un ordinateur côte à côte. L’implémentation inclut plusieurs versions d’un module de ressource qui sont contenues dans le même dossier de module.

## <a name="installing-multiple-resource-versions-side-by-side"></a>Installation de plusieurs versions de ressources côte à côte

Vous pouvez utiliser les paramètres **MinimumVersion**, **MaximumVersion** et **RequiredVersion** de l’applet de commande [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) pour indiquer la version d’un module à installer. L’appel de l’applet de commande **Install-Module** sans spécifier de version installe la version la plus récente.

Par exemple, il existe plusieurs versions du module **xFailOverCluster**, chacun contenant une ressource **xCluster**. Le résultat de l’appel de l’applet de commande **Install-Module** sans spécifier de numéro de version est le suivant :

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Maintenant, si vous rappelez **Install-Module**, mais indiquez la valeur 1.1.0.0 pour le paramètre **RequiredVersion**, le résultat est le suivant :

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Spécification d’une version de ressource dans une configuration

Si plusieurs ressources sont installées sur un ordinateur, vous devez spécifier la version d’une ressource quand vous l’utilisez dans une configuration. Pour cela, vous devez spécifier le paramètre **ModuleVersion** du mot-clé **Import-DscResource**. Si vous ne parvenez pas à spécifier la version d’un module d’une ressource dont plusieurs versions sont installées, la configuration génère une erreur.

La configuration suivante montre comment spécifier la version de la ressource à appeler :

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

>Remarque : Le paramètre ModuleVersion d’Import-DscResource n’est pas disponible dans PowerShell 4.0. Dans PowerShell 4.0, vous pouvez spécifier une version du module en passant un objet de spécification de module au paramètre ModuleName d’Import-DscResource. Un objet de spécification de module est une table de hachage qui contient les clés ModuleName et RequiredVersion. Par exemple :

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

Cela fonctionne également dans PowerShell 5.0, mais il est recommandé d’utiliser le paramètre **ModuleVersion**.

## <a name="see-also"></a>Voir aussi
* [Configurations DSC](configurations.md)
* [Ressources DSC](resources.md)

