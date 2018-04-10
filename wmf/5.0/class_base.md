---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 43b26426a76b6503a83e35ae0c02a0af69902ed6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="declare-base-class"></a><span data-ttu-id="3d11e-102">Déclarer une classe de base</span><span class="sxs-lookup"><span data-stu-id="3d11e-102">Declare Base Class</span></span>
<span data-ttu-id="3d11e-103">Vous pouvez déclarer une classe Windows PowerShell comme type de base pour une autre classe Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3d11e-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="3d11e-104">Vous pouvez également utiliser des types .NET Framework existants comme classes de base :</span><span class="sxs-lookup"><span data-stu-id="3d11e-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```