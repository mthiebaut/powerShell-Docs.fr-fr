---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 6caff8c06174a1dcb990ed8e5062ccca5848dbb8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="convert-string"></a><span data-ttu-id="c1c87-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="c1c87-102">Convert-String</span></span>
<span data-ttu-id="c1c87-103">**Convert-String** expose une fonctionnalité de « remplacement par magie ».</span><span class="sxs-lookup"><span data-stu-id="c1c87-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="c1c87-104">Fournissez des exemples indiquant l’aspect souhaité du texte avant et après l’opération, et l’applet de commande **Convert-String** met automatiquement en forme le texte.</span><span class="sxs-lookup"><span data-stu-id="c1c87-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="c1c87-105">Voici un exemple qui prend un prénom et un nom, et les remplace par le nom, une virgule, l’initiale du prénom, puis un point.</span><span class="sxs-lookup"><span data-stu-id="c1c87-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="c1c87-106">Essayez avec une expression régulière et regardez combien de temps cela vous prend.</span><span class="sxs-lookup"><span data-stu-id="c1c87-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

