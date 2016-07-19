---
title: Ressource WindowsOptionalFeature dans DSC
ms.date: 2016-05-24
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 97714d3fa9a1c00fb3d2e79cc873280ca945a840
ms.openlocfilehash: 1254037b655a3160c90e69971c9faf061f205917

---

# Ressource WindowsOptionalFeature dans DSC

> S’applique à : Windows PowerShell 5.0

La ressource **WindowsOptionalFeature** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour garantir que des fonctionnalités facultatives sont activées sur un nœud cible.

## Syntaxe

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Name| Indique le nom de la fonctionnalité que vous souhaitez voir activée ou désactivée.| 
| Ensure| Spécifie si la fonctionnalité est activée. Pour vous assurer que la fonctionnalité est activée, affectez la valeur « Present » à cette propriété. Pour vous assurer que la fonctionnalité est désactivée, affectez la valeur « Absent ».|
| Source| Non implémentée.|
| NoWindowsUpdateCheck| Indique si DISM contacte Windows Update (WU) lors de la recherche des fichiers sources pour activer une fonctionnalité. Si la valeur est $true, DISM ne contacte pas Windows Update.|
| RemoveFilesOnDisable| Affectez la valeur **$true** pour supprimer tous les fichiers associés à la fonctionnalité quand elle est désactivée (autrement dit, quand **Ensure** a la valeur « Absent »).|
| LogLevel| Niveau de sortie maximal affiché dans les journaux. Les valeurs acceptées sont les suivantes : « ErrorsOnly » (seules les erreurs sont enregistrées), « ErrorsAndWarning » (les erreurs et les avertissements sont enregistrés) et « ErrorsAndWarningAndInformation » (les erreurs, les avertissements et les informations de débogage sont enregistrés).|
| LogPath| Chemin d’un fichier journal dans lequel le fournisseur de ressources doit enregistrer l’opération.| 
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 
 






<!--HONumber=Jul16_HO1-->


