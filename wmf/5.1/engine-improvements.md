---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
title: "Améliorations du moteur PowerShell dans WMF 5.1"
ms.openlocfilehash: 6c8000ccfc59ab46de95dc4f67161e12a5a41199
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
#<a name="powershell-engine-improvements"></a><span data-ttu-id="1aa77-103">Améliorations du moteur PowerShell</span><span class="sxs-lookup"><span data-stu-id="1aa77-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="1aa77-104">Les améliorations suivantes du moteur principal PowerShell ont été implémentées dans WMF 5.1 :</span><span class="sxs-lookup"><span data-stu-id="1aa77-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>


## <a name="performance"></a><span data-ttu-id="1aa77-105">Performances</span><span class="sxs-lookup"><span data-stu-id="1aa77-105">Performance</span></span> ##

<span data-ttu-id="1aa77-106">Les performances ont été améliorées dans certains domaines importants :</span><span class="sxs-lookup"><span data-stu-id="1aa77-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="1aa77-107">Démarrage</span><span class="sxs-lookup"><span data-stu-id="1aa77-107">Startup</span></span>
- <span data-ttu-id="1aa77-108">Le traitement « pipeline » vers les applets de commande ForEach-Object et Where-Object est environ 50 % plus rapide.</span><span class="sxs-lookup"><span data-stu-id="1aa77-108">Pipelining to cmdlets like ForEach-Object and Where-Object is approximately 50% faster</span></span> 

<span data-ttu-id="1aa77-109">Voici quelques exemples d’améliorations (les résultats peuvent varier en fonction de votre matériel) :</span><span class="sxs-lookup"><span data-stu-id="1aa77-109">Some example improvements (your results may vary depending on your hardware):</span></span> 

| <span data-ttu-id="1aa77-110">Scénario</span><span class="sxs-lookup"><span data-stu-id="1aa77-110">Scenario</span></span> | <span data-ttu-id="1aa77-111">Durée 5.0 (ms)</span><span class="sxs-lookup"><span data-stu-id="1aa77-111">5.0 Time (ms)</span></span> | <span data-ttu-id="1aa77-112">Durée 5.1 (ms)</span><span class="sxs-lookup"><span data-stu-id="1aa77-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="1aa77-113">900</span><span class="sxs-lookup"><span data-stu-id="1aa77-113">900</span></span> | <span data-ttu-id="1aa77-114">250</span><span class="sxs-lookup"><span data-stu-id="1aa77-114">250</span></span> |
| <span data-ttu-id="1aa77-115">Première exécution PowerShell : `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="1aa77-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="1aa77-116">30 000</span><span class="sxs-lookup"><span data-stu-id="1aa77-116">30000</span></span> | <span data-ttu-id="1aa77-117">13 000</span><span class="sxs-lookup"><span data-stu-id="1aa77-117">13000</span></span> |
| <span data-ttu-id="1aa77-118">Création du cache d’analyse de commande : `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="1aa77-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="1aa77-119">7000</span><span class="sxs-lookup"><span data-stu-id="1aa77-119">7000</span></span> | <span data-ttu-id="1aa77-120">520</span><span class="sxs-lookup"><span data-stu-id="1aa77-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="1aa77-121">1400</span><span class="sxs-lookup"><span data-stu-id="1aa77-121">1400</span></span> | <span data-ttu-id="1aa77-122">750</span><span class="sxs-lookup"><span data-stu-id="1aa77-122">750</span></span> |
  
> <span data-ttu-id="1aa77-123">Notez qu’une modification liée au démarrage peut affecter certains scénarios non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1aa77-123">Note One change related to startup might impact some unsupported scenarios.</span></span> 
> <span data-ttu-id="1aa77-124">PowerShell ne lit plus les fichiers `$pshome\*.ps1xml`. Ces fichiers ont été convertis en C# pour éviter une surcharge du processeur et des fichiers lors du traitement des fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="1aa77-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span> 
<span data-ttu-id="1aa77-125">Les fichiers existent toujours pour prendre en charge V2 côte à côte. Ainsi, si vous modifiez le contenu des fichiers, cela n’affecte pas V5 mais uniquement V2.</span><span class="sxs-lookup"><span data-stu-id="1aa77-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span> 
<span data-ttu-id="1aa77-126">Notez que la modification du contenu de ces fichiers n’a jamais été un scénario pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1aa77-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="1aa77-127">Une autre modification visible est la façon dont PowerShell met en cache les commandes exportées et d’autres informations pour les modules installés sur un système.</span><span class="sxs-lookup"><span data-stu-id="1aa77-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span> <span data-ttu-id="1aa77-128">Auparavant, ce cache était stocké dans le répertoire `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="1aa77-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span> <span data-ttu-id="1aa77-129">Dans WMF 5.1, le cache est un fichier unique `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="1aa77-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="1aa77-130">Pour plus de détails, voir la page [Cache d’analyse de module](scenarios-features.md#module-analysis-cache).</span><span class="sxs-lookup"><span data-stu-id="1aa77-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>

