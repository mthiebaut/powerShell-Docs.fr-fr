---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,installation
title: Ressources WindowsFeatureSet dans DSC
ms.openlocfilehash: 3cdabc36ef35c2bf912ac54393fe40024a8e8bc0
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsfeatureset-resource"></a>Ressources WindowsFeatureSet dans DSC

> S’applique à : Windows PowerShell 5.0

La ressource **WindowsFeatureSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des rôles et des fonctionnalités sont ajoutés ou supprimés sur un nœud cible.
Cette ressource est une [ressource composite](authoringResourceComposite.md) qui appelle la ressource [WindowsFeature](windowsfeatureResource.md) pour chaque fonctionnalité spécifiée dans la propriété `Name`.

Utilisez cette ressource quand vous voulez configurer certaines fonctionnalités de Windows au même état.

## <a name="syntax"></a>Syntaxe

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]] 
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Nom| Nom des rôles ou fonctionnalités dont vous voulez garantir l’ajout ou la suppression. Il s’agit du même nom que celui de la propriété **Name** de l’applet de commande [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx), et non du nom d’affichage des rôles ou des fonctionnalité.| 
| Credential| Informations d’identification à utiliser pour ajouter ou supprimer les rôles ou les fonctionnalités.| 
| Ensure| Indique si les rôles ou fonctionnalités sont ajoutés. Pour vous assurer que les rôles ou fonctionnalités sont ajoutés, affectez la valeur « Present » à cette propriété. Pour vous assurer que les rôles ou fonctionnalités sont supprimés, affectez la valeur « Absent ».| 
| IncludeAllSubFeature| Affectez la valeur **$true** à cette propriété pour inclure toutes les sous-fonctionnalités requises avec la fonctionnalité que vous spécifiez avec la propriété **Name**.| 
| LogPath| Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.| 
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 
| Source| Indique l’emplacement du fichier source à utiliser pour l’installation, si nécessaire.| 

## <a name="example"></a>Exemple

La configuration suivante garantit que les fonctionnalités **Serveur Web** (IIS) et **Serveur SMTP**, et toutes leurs sous-fonctionnalités, sont installées.

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        } 
    }
}
```

