---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: 302a347b0f4c9c322f7701e8d6a721f9ffba9b59
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="convert-string"></a><span data-ttu-id="d34ba-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="d34ba-102">Convert-String</span></span>
<span data-ttu-id="d34ba-103">**Convert-String** expose une fonctionnalité de « remplacement par magie ».</span><span class="sxs-lookup"><span data-stu-id="d34ba-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="d34ba-104">Fournissez des exemples indiquant l’aspect souhaité du texte avant et après l’opération, et l’applet de commande **Convert-String** met automatiquement en forme le texte.</span><span class="sxs-lookup"><span data-stu-id="d34ba-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="d34ba-105">Voici un exemple qui prend un prénom et un nom, et les remplace par le nom, une virgule, l’initiale du prénom, puis un point.</span><span class="sxs-lookup"><span data-stu-id="d34ba-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="d34ba-106">Essayez avec une expression régulière et regardez combien de temps cela vous prend.</span><span class="sxs-lookup"><span data-stu-id="d34ba-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```