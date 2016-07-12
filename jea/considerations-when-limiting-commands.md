---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "éléments à prendre en considération lors de la limitation des commandes"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 9f3f79a29e0fb7ec5a5111284bb7985548e17749

---

### Éléments à prendre en considération lors de la limitation des commandes
Un point important concerne cette étape.
Il est essentiel que toutes les capacités exposées par le biais de JEA se trouvent dans des zones limitées à l’administrateur.
Les utilisateurs non-administrateurs ne doivent pas avoir la possibilité de modifier les scripts utilisés par le biais des points de terminaison JEA.

Par ailleurs, il est essentiel de ne pas donner aux utilisateurs JEA la possibilité de remplacer des configurations JEA et des scripts inscrits sur liste verte pendant leurs sessions JEA.
Faites très attention quand vous exposez des commandes telles que `Copy-Item` !




<!--HONumber=Jul16_HO1-->


