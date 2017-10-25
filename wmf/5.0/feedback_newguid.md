---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="new-guid"></a>New-Guid
Bien souvent, lors de l’écriture de scripts (ou même d’une ressource DSC), vous devez utiliser un identificateur unique. Les GUID fonctionnent correctement, et il est facile d’appeler la classe Guid du .NET Framework pour en générer un, mais le fait de disposer d’une applet de commande rend cela plus simple à découvrir pour les utilisateurs qui ne se sont pas encore familiarisés avec la classe .NET Framework :

PS C:\\&gt; New-Guid

Guid

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d

