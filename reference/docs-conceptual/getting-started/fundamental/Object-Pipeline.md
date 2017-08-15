---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,applet de commande
title: "Pipeline d’objet"
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 3fa41cc744cf3ab66fc5ef186ead8eb919429a76
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2017
---
# <a name="object-pipeline"></a>Pipeline d’objet
Les pipelines agissent comme une série de segments de canal connectés. Les éléments se déplaçant dans pipeline passent par chaque segment. Pour créer un pipeline dans Windows PowerShell, vous interconnectez des commandes à l’aide que l’opérateur barre verticale « | » (pipe). La sortie de chaque commande est utilisée en tant qu’entrée pour la commande suivante.

Les pipelines constituent indubitablement le concept plus important utilisé dans les interfaces de ligne de commande. Correctement utilisés, les pipelines non seulement réduisent l’effort que nécessite la saisie de commandes complexes, mais aussi facilitent l’affichage du flux de travail dans les commandes. Une caractéristique utile connexe des pipelines est que, comme ils opèrent sur chaque élément séparément, vous n’avez pas à les modifier selon qu’ils contiennent zéro, un ou plusieurs éléments. En outre, chaque commande dans un pipeline (appelée élément de pipeline) transmet généralement sa sortie à la commande suivante, élément par élément. Généralement, cela réduit la demande de ressources de commandes complexes, et permet de commencer à recevoir la sortie immédiatement.

Dans ce chapitre, nous expliquons en quoi le pipeline Windows PowerShell diffère des pipelines des interpréteurs de commandes les plus populaires, puis présentons des outils de base que vous pouvez utiliser pour contrôler la sortie du pipeline et voir comment celui-ci fonctionne.

