---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 136e16ae74e54f3bc9d0623178257df1e9104aac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="8899a-102">Remettre un document de configuration sans l’appliquer</span><span class="sxs-lookup"><span data-stu-id="8899a-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="8899a-103">L’applet de commande [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) copie un fichier MOF de configuration sur un nœud cible, mais n’applique pas la configuration.</span><span class="sxs-lookup"><span data-stu-id="8899a-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="8899a-104">Cette configuration est appliquée durant le contrôle de cohérence suivant, ou quand vous exécutez l’applet de commande [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).</span><span class="sxs-lookup"><span data-stu-id="8899a-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>