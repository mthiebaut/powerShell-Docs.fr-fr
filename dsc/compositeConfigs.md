---
title: Imbrication des configurations
ms.date: 2017-03-27
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: carmonm
ms.prod: powershell
ms.openlocfilehash: 3afc4c87b1bc54e5f251a3a54eab5f448900f124
ms.sourcegitcommit: 65250232157bb1c742d7d385933b8abc24a570fb
translationtype: HT
---
# <a name="nesting-dsc-configurations"></a>Imbrication des configurations DSC

Une configuration imbriquée (également appelée configuration composite) est une configuration appelée dans une autre configuration, comme s’il s’agissait d’une ressource.
Les deux configurations doivent être définies dans le même fichier.

Examinons un exemple simple :

```powershell
Configuration FileConfig 
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }
    
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

Dans cet exemple, `FileConfig` accepte deux paramètres obligatoires, **CopyFrom** et **CopyTo**, tous deux utilisés comme valeurs pour les propriétés **SourcePath** et **DestinationPath** du bloc de ressources `File`. La configuration `NestedConfig` appelle `FileConfig` comme s’il s’agissait d’une ressource.
Les propriétés du bloc de ressources `NestedConfig` (**CopyFrom** et **CopyTo**) sont les paramètres de la configuration `FileConfig`.

## <a name="see-also"></a>Voir aussi

- [Ressources composites : utilisation d’une configuration DSC en tant que ressource](authoringResourceComposite.md)
