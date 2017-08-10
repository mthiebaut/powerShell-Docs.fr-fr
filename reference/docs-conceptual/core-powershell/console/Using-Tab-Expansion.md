---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Utilisation du développement par tabulation"
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: c158e544d79bf6010690160eea71630a1981e8a5
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
# <a name="using-tab-expansion"></a><span data-ttu-id="5ee9c-103">Utilisation du développement par tabulation</span><span class="sxs-lookup"><span data-stu-id="5ee9c-103">Using Tab Expansion</span></span>
<span data-ttu-id="5ee9c-104">Les interpréteurs de ligne de commande offrent souvent une manière de compléter automatiquement les noms de fichiers ou commandes longs, en accélérant la saisie de commandes et en fournissant des indications.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing hints.</span></span> <span data-ttu-id="5ee9c-105">Windows PowerShell permet de renseigner des noms de fichiers et des noms de d’applet de commande en appuyant sur la touche **Tab**.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-105">Windows PowerShell allows you to fill in file names and cmdlet names by pressing the **Tab** key.</span></span>

> [!NOTE]
> <span data-ttu-id="5ee9c-106">Le développement par tabulation est contrôlé par la fonction interne TabExpansion ou TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="5ee9c-107">Étant donné que cette fonction peut être modifiée ou remplacée, cette explication a trait au comportement de la configuration Windows PowerShell par défaut.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default Windows PowerShell configuration.</span></span>

<span data-ttu-id="5ee9c-108">Pour renseigner automatiquement un nom de fichier ou un chemin d’accès à partir des choix disponibles, tapez une partie du nom, puis appuyez sur la touche **Tab**.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-108">To fill in a filename or path from the available choices automatically, type part of the name and press the **Tab** key.</span></span> <span data-ttu-id="5ee9c-109">Windows PowerShell développe automatiquement le nom sur la base de la première correspondance trouvée.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-109">Windows PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="5ee9c-110">Des appuis répétés sur la touche **Tab** permettent de passer en revue tous les choix disponibles.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-110">Pressing the **Tab** key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="5ee9c-111">Le développement par tabulation des noms d’applet de commande est légèrement différent.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="5ee9c-112">Pour développer par tabulation un nom d’applet de commande, tapez la première partie entière du nom (verbe) et le trait d’union qui suit.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="5ee9c-113">Vous pouvez entrer davantage de caractères du nom pour une correspondance partielle.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="5ee9c-114">Par exemple, si vous tapez **get-co**, puis appuyez sur la touche **Tab**, Windows PowerShell développe automatiquement le nom de l’applet de commande **Get-Command** (notez qu’il modifie également la casse des lettres pour leur attribuer leur format standard).</span><span class="sxs-lookup"><span data-stu-id="5ee9c-114">For example, if you type **get-co** and then press the **Tab** key, Windows PowerShell will automatically expand this to the **Get-Command** cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="5ee9c-115">Si vous appuyez de nouveau sur la touche **Tab**, Windows PowerShell remplace ce nom par le seul autre nom d’applet de commande correspondant, **Get-Content**.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-115">If you press **Tab** key again, Windows PowerShell replaces this with the only other matching cmdlet name, **Get-Content**.</span></span>

<span data-ttu-id="5ee9c-116">Vous pouvez utiliser le développement par tabulation à plusieurs reprises sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="5ee9c-117">Par exemple, vous pouvez l’utiliser sur le nom de l’applet de commande **Get-Content** en entrant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="5ee9c-117">For example, you can use tab expansion on the name of the **Get-Content** cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="5ee9c-118">Lorsque vous appuyez sur la touche **Tab**, la commande est développée en :</span><span class="sxs-lookup"><span data-stu-id="5ee9c-118">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="5ee9c-119">Vous pouvez ensuite partiellement spécifier le chemin d’accès au fichier journal Active Setup, puis utiliser à nouveau le développement par tabulation :</span><span class="sxs-lookup"><span data-stu-id="5ee9c-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="5ee9c-120">Lorsque vous appuyez sur la touche **Tab**, la commande est développée en :</span><span class="sxs-lookup"><span data-stu-id="5ee9c-120">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="5ee9c-121">Une limitation du processus de développement par tabulation est que les tabulations sont toujours interprétées comme des tentatives de compléter un mot.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="5ee9c-122">Si vous copiez et collez des exemples de commandes dans une console Windows PowerShell, assurez-vous qu’ils ne contiennent pas de tabulations. Autrement, les résultats seront imprévisibles et presque certainement différents de ce que vous attendez.</span><span class="sxs-lookup"><span data-stu-id="5ee9c-122">If you copy and paste command examples into a Windows PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>

