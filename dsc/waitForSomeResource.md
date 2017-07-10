---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WaitForSome
ms.openlocfilehash: 5d67a9111f6358240590b651e627ffb96abc0896
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="dsc-waitforsome-resource" class="xliff"></a>
# Ressource DSC WaitForSome

> S’applique à : Windows PowerShell 5.0 et ultérieur

La ressource de configuration d’état souhaité (DSC) **WaitForAny** peut être utilisée dans un bloc de nœud dans une [configuration DSC](configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.

La ressource réussit si la ressource spécifiée dans la propriété **ResourceName** est dans l’état souhaité sur un nombre minimal de nœuds (spécifié par **NodeCount**) défini par la propriété **NodeName**. 


<a id="syntax" class="xliff"></a>
## Syntaxe

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    NodeCount = [Uint32]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

<a id="properties" class="xliff"></a>
## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Nom_ressource| Le nom de la ressource de la dépendance.| 
| NodeName| Les nœuds cible de la ressource de la dépendance.| 
| NodeCount| Le nombre minimal de nœuds qui doivent être dans l’état souhaité pour que cette ressource réussisse.|
| RetryIntervalSec| Le nombre de secondes avant la nouvelle tentative. Le minimum est 1.| 
| RetryCount| Le nombre maximum de nouvelles tentatives.| 
| ThrottleLimit| Le nombre de machines à connecter simultanément. La valeur par défaut est new-cimsession.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.|


<a id="example" class="xliff"></a>
## Exemple

Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](crossNodeDependencies.md)

