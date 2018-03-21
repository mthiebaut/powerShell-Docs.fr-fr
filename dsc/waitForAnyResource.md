---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource DSC WaitForAny
ms.openlocfilehash: 43922dbcccb6d06d7d9edfcf16ce4eb107e9d4e6
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforany-resource"></a>Ressource DSC WaitForAny

> S’applique à : Windows PowerShell 5.1 et ultérieur

La ressource de configuration d’état souhaité (DSC) **WaitForSome** peut être utilisée dans un bloc de nœud dans une [configuration DSC](configurations.md) pour spécifier les dépendances sur les configurations sur d’autres nœuds.

La ressource réussit si la ressource spécifiée par la propriété **ResourceName** est dans l’état souhaité sur un des nœuds cible définis dans la propriété **NodeName**.


## <a name="syntax"></a>Syntaxe

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Nom_ressource| Le nom de la ressource de la dépendance. Si cette ressource appartient à une configuration différente, mettez en forme le nom comme ceci : « [__type_ressource__]__nom_ressource__::[__nom_configuration__]::[__nom_configuration__] »| 
| NodeName| Les nœuds cible de la ressource de la dépendance.| 
| RetryIntervalSec| Le nombre de secondes avant la nouvelle tentative. Le minimum est 1.| 
| RetryCount| Le nombre maximum de nouvelles tentatives.| 
| ThrottleLimit| Le nombre de machines à connecter simultanément. La valeur par défaut est new-cimsession.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource __ResourceName__ de type __ResourceType__, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de cette ressource, consultez [Spécification des dépendances entre nœuds](crossNodeDependencies.md)

