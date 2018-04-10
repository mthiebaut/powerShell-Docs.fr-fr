---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a>Informations détaillées sur l’état du gestionnaire de configuration local

Nous avons apporté des améliorations à l’exposition des détails concernant l’état du gestionnaire de configuration local. Le LCMState retourné par Get-DscLocalConfigurationManager peut maintenant contenir les valeurs suivantes :

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Nous avons également ajouté une propriété LCMStateDetail qui contient davantage d’informations sur l’état.