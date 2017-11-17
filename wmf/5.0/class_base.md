---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 5dbaa126cf9ae3917c3a8787ffc5ef5ac77b19c1
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2017
---
# <a name="declare-base-class"></a><span data-ttu-id="f46ca-102">Déclarer une classe de base</span><span class="sxs-lookup"><span data-stu-id="f46ca-102">Declare Base Class</span></span>
<span data-ttu-id="f46ca-103">Vous pouvez déclarer une classe Windows PowerShell comme type de base pour une autre classe Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f46ca-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

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

<span data-ttu-id="f46ca-104">Vous pouvez également utiliser des types .NET Framework existants comme classes de base :</span><span class="sxs-lookup"><span data-stu-id="f46ca-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

