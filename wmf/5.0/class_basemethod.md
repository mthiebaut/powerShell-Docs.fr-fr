---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 28da6d12d3f7a59777425e1cc4531a609a793ddb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="call-base-class-method"></a><span data-ttu-id="f77a0-102">Appeler une méthode de classe de base</span><span class="sxs-lookup"><span data-stu-id="f77a0-102">Call Base Class Method</span></span>

<span data-ttu-id="f77a0-103">Vous pouvez substituer des méthodes existantes dans les sous-classes.</span><span class="sxs-lookup"><span data-stu-id="f77a0-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="f77a0-104">Pour cela, déclarez les méthodes à l’aide des mêmes nom et signature :</span><span class="sxs-lookup"><span data-stu-id="f77a0-104">To do this, declare methods by using the same name and signature:</span></span>

```PowerShell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

<span data-ttu-id="f77a0-105">Pour appeler des méthodes de classe de base à partir des implémentations substituées, effectuez un transtypage vers la classe de base ([baseClass]$this) lors de l’appel :</span><span class="sxs-lookup"><span data-stu-id="f77a0-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

```PowerShell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

<span data-ttu-id="f77a0-106">Toutes les méthodes PowerShell sont virtuelles.</span><span class="sxs-lookup"><span data-stu-id="f77a0-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="f77a0-107">Vous pouvez masquer les méthodes .NET non virtuelles dans une sous-classe en utilisant la même syntaxe que pour une substitution : il vous suffit de déclarer des méthodes avec les mêmes nom et signature.</span><span class="sxs-lookup"><span data-stu-id="f77a0-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

```PowerShell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

