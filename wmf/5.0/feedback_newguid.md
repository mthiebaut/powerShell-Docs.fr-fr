---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 91c115c7f0553cd5edf7fecf04e6a5c71c0a1aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="new-guid"></a><span data-ttu-id="9bd3a-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="9bd3a-102">New-Guid</span></span>
<span data-ttu-id="9bd3a-103">Bien souvent, lors de l’écriture de scripts (ou même d’une ressource DSC), vous devez utiliser un identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="9bd3a-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="9bd3a-104">Les GUID fonctionnent correctement, et il est facile d’appeler la classe Guid du .NET Framework pour en générer un, mais le fait de disposer d’une applet de commande rend cela plus simple à découvrir pour les utilisateurs qui ne se sont pas encore familiarisés avec la classe .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="9bd3a-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="9bd3a-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="9bd3a-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="9bd3a-106">Guid</span><span class="sxs-lookup"><span data-stu-id="9bd3a-106">Guid</span></span>

----

<span data-ttu-id="9bd3a-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="9bd3a-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>