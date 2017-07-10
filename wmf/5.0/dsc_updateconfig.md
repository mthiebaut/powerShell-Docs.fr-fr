---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 410fa4b6c6d3e2708da78414cbb9b80dd3ca1387
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
<a id="on-demand-pull-of-dsc-configurations" class="xliff"></a>
# Extraction à la demande des configurations DSC

La nouvelle applet de commande Update-DscConfiguration déclenche une extraction à partir des serveurs collecteurs définis dans la métaconfiguration. Ce comportement est souvent appelé « Extraire maintenant ». 


Une fois déclenchée, l’extraction se comporte exactement comme si elle avait été déclenchée selon la fréquence normale :

1. La somme de contrôle de la configuration actuelle est comparée à la somme de contrôle de la configuration sur le serveur collecteur. 
2. Si elles sont identiques, l’extraction se termine correctement sans appliquer la configuration. 
3. Si elles sont différentes, la configuration est extraite à partir du serveur collecteur et appliquée.

**Remarque :** Si RefreshMode = ’Push’ pour la métaconfiguration, une erreur est retournée par cette applet de commande. Celle-ci ne fait donc jamais rien quand un nœud cible est en mode Push (par envoi).

```PowerShell
Update-DscConfiguration     [[-ComputerName] <string[]>] 
                            [-Wait]
                            [-Force] 
                            [-JobName <string>] 
                            [-Credential<pscredential>] 
                            [-ThrottleLimit <int>] 
                            [-WhatIf] 
                            [-Confirm] 
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]> 
                            [-Wait] 
                            [-Force] 
                            [-JobName <string>] 
                            [-ThrottleLimit <int>]
                            [-WhatIf] 
                            [-Confirm] 
                            [<CommonParameters>]
```

