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
# <a name="deliver-a-configuration-document-without-applying"></a>Remettre un document de configuration sans l’appliquer

L’applet de commande [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) copie un fichier MOF de configuration sur un nœud cible, mais n’applique pas la configuration.
Cette configuration est appliquée durant le contrôle de cohérence suivant, ou quand vous exécutez l’applet de commande [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx).