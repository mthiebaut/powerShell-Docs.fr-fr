---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: cedda61241df4965fe5db723f03e3497f046fa44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="77b88-102">Extraire et analyser des objets structurés hors de contenu String</span><span class="sxs-lookup"><span data-stu-id="77b88-102">Extract and Parse Structured Objects out of String</span></span>
<span data-ttu-id="77b88-103">Cet article présente également certaines fonctionnalités supplémentaires pour l’applet de commande ConvertFrom-String :</span><span class="sxs-lookup"><span data-stu-id="77b88-103">This also introduces some additional functionality for the ConvertFrom-String cmdlet:</span></span>

-   <span data-ttu-id="77b88-104">Suppression de la propriété de texte d’étendue par défaut.</span><span class="sxs-lookup"><span data-stu-id="77b88-104">Removes the extent text property by default.</span></span> <span data-ttu-id="77b88-105">Vous pouvez l’inclure avec le paramètre -IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="77b88-105">You can include it with the -IncludeExtent parameter.</span></span>

-   <span data-ttu-id="77b88-106">Nombreux correctifs de bogues d’algorithmes d’apprentissage résolus suite aux commentaires fournis par les MVP et la Communauté.</span><span class="sxs-lookup"><span data-stu-id="77b88-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

-   <span data-ttu-id="77b88-107">Nouveau paramètre -UpdateTemplate pour enregistrer les résultats de l’algorithme d’apprentissage dans un commentaire dans le fichier de modèle.</span><span class="sxs-lookup"><span data-stu-id="77b88-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="77b88-108">Ainsi, le processus d’apprentissage (l’étape la plus lente) a un coût unique.</span><span class="sxs-lookup"><span data-stu-id="77b88-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="77b88-109">L’exécution de Convert-String avec un modèle qui contient l’algorithme d’apprentissage encodé est désormais presque instantanée.</span><span class="sxs-lookup"><span data-stu-id="77b88-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>


<a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="77b88-110">Extraire et analyser des objets structurés hors de contenu String</span><span class="sxs-lookup"><span data-stu-id="77b88-110">Extract and parse structured objects out of string content</span></span>
----------------------------------------------------------

<span data-ttu-id="77b88-111">En collaboration avec [Microsoft Research](http://research.microsoft.com/), une nouvelle applet de commande **ConvertFrom-String** a été ajoutée.</span><span class="sxs-lookup"><span data-stu-id="77b88-111">In collaboration with [Microsoft Research](http://research.microsoft.com/), a new **ConvertFrom-String** cmdlet has been added.</span></span>

<span data-ttu-id="77b88-112">Cette applet de commande prend en charge deux modes : l’analyse délimitée de base et l’analyse pilotée par un exemple généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="77b88-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="77b88-113">Par défaut, l’analyse délimitée fractionne l’entrée au niveau de l’espace blanc et elle affecte des noms de propriétés aux groupes résultants.</span><span class="sxs-lookup"><span data-stu-id="77b88-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="77b88-114">Vous pouvez personnaliser le délimiteur :</span><span class="sxs-lookup"><span data-stu-id="77b88-114">You can customize the delimiter:</span></span>

> <span data-ttu-id="77b88-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span><span class="sxs-lookup"><span data-stu-id="77b88-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span></span>

<span data-ttu-id="77b88-116">P1    P2</span><span class="sxs-lookup"><span data-stu-id="77b88-116">P1    P2</span></span>
--    --

<span data-ttu-id="77b88-117">L’applet de commande prend également en charge l’analyse pilotée par un exemple généré automatiquement basée sur le travail de recherche [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) mené par [Microsoft Research](http://research.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="77b88-117">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) research work in [Microsoft Research](http://research.microsoft.com).</span></span>

<span data-ttu-id="77b88-118">Pour commencer, prenez un carnet d’adresses basé sur du texte :</span><span class="sxs-lookup"><span data-stu-id="77b88-118">To get started, consider a text-based address book:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA

<span data-ttu-id="77b88-119">Copiez quelques exemples dans un fichier, que vous utiliserez comme modèle :</span><span class="sxs-lookup"><span data-stu-id="77b88-119">Copy a few examples into a file, which you will use as your template:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



<span data-ttu-id="77b88-120">Placez des accolades autour des données que vous souhaitez extraire, en leur donnant un nom.</span><span class="sxs-lookup"><span data-stu-id="77b88-120">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="77b88-121">La propriété **Name** (et ses autres propriétés associées) pouvant apparaître plusieurs fois, vous devez utiliser un astérisque (\*) pour indiquer que cela génère plusieurs enregistrements (plutôt que l’extraction d’un ensemble de propriétés dans un enregistrement unique) :</span><span class="sxs-lookup"><span data-stu-id="77b88-121">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

<span data-ttu-id="77b88-122">À partir de cet ensemble d’exemples, **ConvertFrom-String** peut maintenant extraire automatiquement la sortie basée sur des objets à partir des fichiers d’entrée ayant une structure similaire.</span><span class="sxs-lookup"><span data-stu-id="77b88-122">From this set of examples, **ConvertFrom-String** can now automatically extract object-based output from input files with similar structure.</span></span>

> <span data-ttu-id="77b88-123">2 \[C:\\temp\]</span><span class="sxs-lookup"><span data-stu-id="77b88-123">2 \[C:\\temp\]</span></span>
>
> <span data-ttu-id="77b88-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span><span class="sxs-lookup"><span data-stu-id="77b88-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span></span>
>
> <span data-ttu-id="77b88-125">ExtentText                     Name               City     State</span><span class="sxs-lookup"><span data-stu-id="77b88-125">ExtentText                     Name               City     State</span></span>
> ----------                     ----               ----     -----
> <span data-ttu-id="77b88-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span><span class="sxs-lookup"><span data-stu-id="77b88-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span></span>

<span data-ttu-id="77b88-127">Pour effectuer des manipulations de données supplémentaires sur le texte extrait, la propriété **ExtentText** capture le texte brut à partir duquel l’enregistrement a été extrait.</span><span class="sxs-lookup"><span data-stu-id="77b88-127">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="77b88-128">Pour nous faire part de vos commentaires sur cette fonctionnalité ou pour partager du contenu pour lequel vous avez des difficultés à écrire des exemples, envoyez-nous un message à l’adresse <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="77b88-128">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>