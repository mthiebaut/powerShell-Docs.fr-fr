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
ms.translationtype: HT
ms.contentlocale: fr-FR
---
### <a name="considerations-when-limiting-commands"></a><span data-ttu-id="d132a-103">Éléments à prendre en considération lors de la limitation des commandes</span><span class="sxs-lookup"><span data-stu-id="d132a-103">Considerations When Limiting Commands</span></span>
<span data-ttu-id="d132a-104">Un point important concerne cette étape.</span><span class="sxs-lookup"><span data-stu-id="d132a-104">There is one important point to make about this step.</span></span>
<span data-ttu-id="d132a-105">Il est essentiel que toutes les capacités exposées par le biais de JEA se trouvent dans des zones limitées à l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="d132a-105">It is critical that all capabilities exposed through JEA are located in administrator-restricted areas.</span></span>
<span data-ttu-id="d132a-106">Les utilisateurs non-administrateurs ne doivent pas avoir la possibilité de modifier les scripts utilisés par le biais des points de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="d132a-106">Non-administrator users should not have the capability to modify the scripts used through JEA endpoints.</span></span>

<span data-ttu-id="d132a-107">Par ailleurs, il est essentiel de ne pas donner aux utilisateurs JEA la possibilité de remplacer des configurations JEA et des scripts inscrits sur liste verte pendant leurs sessions JEA.</span><span class="sxs-lookup"><span data-stu-id="d132a-107">On a related note, it is critical that you do not give JEA users the ability to overwrite JEA configurations and whitelisted scripts within their JEA sessions.</span></span>
<span data-ttu-id="d132a-108">Faites très attention quand vous exposez des commandes telles que `Copy-Item` !</span><span class="sxs-lookup"><span data-stu-id="d132a-108">Be extremely careful when exposing commands like `Copy-Item`!</span></span>

