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
<a id="convert-string" class="xliff"></a>
# Convert-String
**Convert-String** expose une fonctionnalité de « remplacement par magie ». Fournissez des exemples indiquant l’aspect souhaité du texte avant et après l’opération, et l’applet de commande **Convert-String** met automatiquement en forme le texte. Voici un exemple qui prend un prénom et un nom, et les remplace par le nom, une virgule, l’initiale du prénom, puis un point. Essayez avec une expression régulière et regardez combien de temps cela vous prend.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

