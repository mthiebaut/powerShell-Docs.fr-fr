---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,jea
ms.date: 2016-06-22
title: "éléments à prendre en considération lors de la limitation des commandes"
ms.technology: powershell
ms.openlocfilehash: 0b4396ee130d99c42f613c1b79193c236ad472e7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
### <a name="considerations-when-limiting-commands"></a>Éléments à prendre en considération lors de la limitation des commandes
Un point important concerne cette étape.
Il est essentiel que toutes les capacités exposées par le biais de JEA se trouvent dans des zones limitées à l’administrateur.
Les utilisateurs non-administrateurs ne doivent pas avoir la possibilité de modifier les scripts utilisés par le biais des points de terminaison JEA.

Par ailleurs, il est essentiel de ne pas donner aux utilisateurs JEA la possibilité de remplacer des configurations JEA et des scripts inscrits sur liste verte pendant leurs sessions JEA.
Faites très attention quand vous exposez des commandes telles que `Copy-Item` !

