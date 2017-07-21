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
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="d09fe-102">Extraction à la demande des configurations DSC</span><span class="sxs-lookup"><span data-stu-id="d09fe-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="d09fe-103">La nouvelle applet de commande Update-DscConfiguration déclenche une extraction à partir des serveurs collecteurs définis dans la métaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="d09fe-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="d09fe-104">Ce comportement est souvent appelé « Extraire maintenant ».</span><span class="sxs-lookup"><span data-stu-id="d09fe-104">The behavior is often referred to as 'Pull Now'.</span></span> 


<span data-ttu-id="d09fe-105">Une fois déclenchée, l’extraction se comporte exactement comme si elle avait été déclenchée selon la fréquence normale :</span><span class="sxs-lookup"><span data-stu-id="d09fe-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="d09fe-106">La somme de contrôle de la configuration actuelle est comparée à la somme de contrôle de la configuration sur le serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="d09fe-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span> 
2. <span data-ttu-id="d09fe-107">Si elles sont identiques, l’extraction se termine correctement sans appliquer la configuration.</span><span class="sxs-lookup"><span data-stu-id="d09fe-107">If they are the same, it completes successfully without applying the configuration.</span></span> 
3. <span data-ttu-id="d09fe-108">Si elles sont différentes, la configuration est extraite à partir du serveur collecteur et appliquée.</span><span class="sxs-lookup"><span data-stu-id="d09fe-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="d09fe-109">**Remarque :** Si RefreshMode = ’Push’ pour la métaconfiguration, une erreur est retournée par cette applet de commande. Celle-ci ne fait donc jamais rien quand un nœud cible est en mode Push (par envoi).</span><span class="sxs-lookup"><span data-stu-id="d09fe-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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

