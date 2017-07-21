---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 2d629d98b59c455011f4a5d955ef666218ae2f3f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="472bd-102">L’applet de commande Test-DscConfiguration prend en charge les configurations de référence</span><span class="sxs-lookup"><span data-stu-id="472bd-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="472bd-103">L’applet de commande Test-DscConfiguration a été mise à jour pour autoriser le test de l’état de configuration souhaitée d’un ou plusieurs nœuds cibles en spécifiant un document de configuration de référence à comparer.</span><span class="sxs-lookup"><span data-stu-id="472bd-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="472bd-104">Les nouveaux jeux de paramètres suivants utilisent des configurations DSC dans le chemin spécifié uniquement pour tester et jamais pour appliquer chaque configuration sur les nœuds cibles spécifiés.</span><span class="sxs-lookup"><span data-stu-id="472bd-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="472bd-105">Comme avec Start-DscConfiguration et d’autres applets de commande DSC, le nom de chaque document MOF est utilisé pour déterminer le nœud cible sur lequel tester la configuration.</span><span class="sxs-lookup"><span data-stu-id="472bd-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span> 

```PowerShell
Test-DscConfiguration   [-Path] <string> 
                        [[-ComputerName] <string[]>] 
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

<span data-ttu-id="472bd-106">Les nouveaux jeux de paramètres suivants utilisent une configuration DSC unique seulement pour tester et jamais pour appliquer la configuration sur les nœuds cibles spécifiés.</span><span class="sxs-lookup"><span data-stu-id="472bd-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span> 

```PowerShell
Test-DscConfiguration   -ReferenceConfiguration <string> 
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

