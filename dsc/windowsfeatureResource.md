---
title:   Ressource WindowsFeature dans DSC
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Ressource WindowsFeature dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **WindowsFeature** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des rôles et des fonctionnalités sont ajoutés ou supprimés sur un nœud cible.

## Syntaxe

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Nom| Indique le nom du rôle ou de la fonctionnalité dont vous voulez garantir l’ajout ou la suppression. Il s’agit du même nom que celui de la propriété __Name__ de l’applet de commande [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) et non du nom d’affichage du rôle ou de la fonctionnalité.| 
| Credential| Indique les informations d’identification à utiliser pour ajouter ou supprimer le rôle ou la fonctionnalité.| 
| Ensure| Indique si le rôle ou la fonctionnalité sont ajoutés. Pour vous assurer que le rôle ou la fonctionnalité sont ajoutés, définissez cette propriété sur « Present ». Pour que le rôle ou la fonctionnalité soient supprimés, définissez la propriété sur « Absent ».| 
| IncludeAllSubFeature| Définissez cette propriété sur __$true__ pour garantir que l’état de toutes les sous-fonctionnalités nécessaires est l’état de la fonctionnalité que vous spécifiez avec la propriété __Name__.| 
| LogPath| Indique le chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.| 
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 
| Source| Indique l’emplacement du fichier source à utiliser pour l’installation, si nécessaire.| 

## Exemple
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```



<!--HONumber=May16_HO3-->


