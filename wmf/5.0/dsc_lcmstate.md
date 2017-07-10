---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="detailed-information-about-lcm-state" class="xliff"></a>
# Informations détaillées sur l’état du gestionnaire de configuration local

Nous avons apporté des améliorations à l’exposition des détails concernant l’état du gestionnaire de configuration local. Le LCMState retourné par Get-DscLocalConfigurationManager peut maintenant contenir les valeurs suivantes :

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Nous avons également ajouté une propriété LCMStateDetail qui contient davantage d’informations sur l’état.

