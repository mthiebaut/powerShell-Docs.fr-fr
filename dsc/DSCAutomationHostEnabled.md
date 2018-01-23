---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Clé de Registre DSCAutomationHostEnabled"
ms.openlocfilehash: c58b7a8f2485ff02f09763749a3de8a75f882d19
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
>S’applique à : Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Clé de Registre DSCAutomationHostEnabled

DSC utilise la clé de Registre **DSCAutomationHostEnabled** sous **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** pour activer la configuration de l’ordinateur au moment du démarrage initial.
DSCAutomationHostEnabled prend en charge trois modes :

|  Valeur de DSCAutomationHostEnabled  |  Description   | 
|---|---| 
0 | Désactive la configuration de la machine au démarrage. |
1 | Active la configuration de la machine au démarrage. |
2 | Active la configuration de la machine uniquement si DSC est en attente ou en cours. Il s'agit de la valeur par défaut. |

## <a name="see-also"></a>Voir aussi

Pour obtenir un exemple montrant comment utiliser cette fonctionnalité pour exécuter des configurations au démarrage initial, consultez [Configurer une machine virtuelle au démarrage initial à l’aide de DSC](bootstrapDsc.md).


