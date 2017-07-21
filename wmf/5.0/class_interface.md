---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: e503f9a4462e94fce42ffcdcc0976d261c051f87
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="2bfa4-102">Déclarer une interface implémentée</span><span class="sxs-lookup"><span data-stu-id="2bfa4-102">Declare Implemented Interface</span></span>

<span data-ttu-id="2bfa4-103">Vous pouvez déclarer des interfaces implémentées après les types de base, ou immédiatement après un signe deux-points (:), si aucun type de base n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="2bfa4-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="2bfa4-104">Séparez tous les noms de types par des virgules.</span><span class="sxs-lookup"><span data-stu-id="2bfa4-104">Separate all type names by using commas.</span></span> <span data-ttu-id="2bfa4-105">Cela ressemble beaucoup à la syntaxe C#.</span><span class="sxs-lookup"><span data-stu-id="2bfa4-105">It’s very similar to C# syntax.</span></span>

```PowerShell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

