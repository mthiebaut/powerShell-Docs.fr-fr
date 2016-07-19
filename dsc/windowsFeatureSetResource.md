---
title: Ressources WindowsFeatureSet dans DSC
ms.date: 2016-05-24
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 97714d3fa9a1c00fb3d2e79cc873280ca945a840
ms.openlocfilehash: df6869cdf1d1f6c823704e4de2882e90cb672ad2

---

# Ressources WindowsFeatureSet dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **WindowsFeatureSet** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des rôles et des fonctionnalités sont ajoutés ou supprimés sur un nœud cible.
Cette ressource est une [ressource composite](authoringResourceComposite.md) qui appelle la ressource [WindowsFeature](windowsfeatureResource.md) pour chaque fonctionnalité spécifiée dans la propriété `Name`.

Utilisez cette ressource quand vous voulez configurer certaines fonctionnalités de Windows au même état.

## Syntaxe

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

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Name| Nom des rôles ou fonctionnalités dont vous voulez garantir l’ajout ou la suppression. Il s’agit du même nom que celui de la propriété **Name** de l’applet de commande [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx), et non du nom d’affichage des rôles ou des fonctionnalité.| 
| Credential| Informations d’identification à utiliser pour ajouter ou supprimer les rôles ou les fonctionnalités.| 
| Ensure| Indique si les rôles ou fonctionnalités sont ajoutés. Pour vous assurer que les rôles ou fonctionnalités sont ajoutés, affectez la valeur « Present » à cette propriété. Pour vous assurer que les rôles ou fonctionnalités sont supprimés, affectez la valeur « Absent ».| 
| IncludeAllSubFeature| Affectez la valeur **$true** à cette propriété pour inclure toutes les sous-fonctionnalités requises avec la fonctionnalité que vous spécifiez avec la propriété **Name**.| 
| LogPath| Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.| 
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 
| Source| Indique l’emplacement du fichier source à utiliser pour l’installation, si nécessaire.| 

## Exemple

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




<!--HONumber=Jul16_HO1-->


