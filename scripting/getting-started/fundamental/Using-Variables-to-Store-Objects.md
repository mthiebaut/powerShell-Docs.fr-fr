---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Utilisation de variables pour stocker des objets
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 067948d7c234fb70c7cf9966c9ae3e8df1f99757
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="0f458-103">Utilisation de variables pour stocker des objets</span><span class="sxs-lookup"><span data-stu-id="0f458-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="0f458-104">Windows PowerShell fonctionne avec des objets.</span><span class="sxs-lookup"><span data-stu-id="0f458-104">Windows PowerShell works with objects.</span></span> <span data-ttu-id="0f458-105">Windows PowerShell permet de créer des variables (essentiellement des objets nommés) pour conserver les sorties en vue d’une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="0f458-105">Windows PowerShell lets you create variables - essentially named objects - to preserve output to use later.</span></span> <span data-ttu-id="0f458-106">Si vous êtes habitué à utiliser des variables dans d’autres interpréteurs de commandes, n’oubliez pas que les variables Windows PowerShell sont des objets, et non du texte.</span><span class="sxs-lookup"><span data-stu-id="0f458-106">If you are used to working with variables in other shells, remember that Windows PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="0f458-107">Les variables sont toujours spécifiées avec le caractère initial $, et leur nom peut comprendre des caractères alphanumériques ou des traits de soulignement.</span><span class="sxs-lookup"><span data-stu-id="0f458-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="0f458-108">Création d’une variable</span><span class="sxs-lookup"><span data-stu-id="0f458-108">Creating a Variable</span></span>
<span data-ttu-id="0f458-109">Vous pouvez créer une variable en tapant un nom de variable valide :</span><span class="sxs-lookup"><span data-stu-id="0f458-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="0f458-110">Cette opération ne retourne aucun résultat, car **$loc** n’a pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="0f458-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="0f458-111">Vous pouvez créer une variable et lui attribuer une valeur au cours de la même étape.</span><span class="sxs-lookup"><span data-stu-id="0f458-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="0f458-112">Windows PowerShell ne crée la variable que si elle n’existe pas. Sinon, il attribue la valeur spécifiée à la variable existante.</span><span class="sxs-lookup"><span data-stu-id="0f458-112">Windows PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="0f458-113">Pour stocker votre emplacement actuel dans la variable **$loc**, tapez :</span><span class="sxs-lookup"><span data-stu-id="0f458-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="0f458-114">Aucune sortie ne s’affiche quand vous tapez cette commande, car la sortie est envoyée à $loc.</span><span class="sxs-lookup"><span data-stu-id="0f458-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="0f458-115">Dans Windows PowerShell, une sortie affichée est un effet secondaire du fait que les données non redirigées autrement sont toujours envoyées à l’écran.</span><span class="sxs-lookup"><span data-stu-id="0f458-115">In Windows PowerShell, displayed output is a side effect of the fact that data which is not otherwise directed always gets sent to the screen.</span></span> <span data-ttu-id="0f458-116">La saisie de $loc affiche votre emplacement actuel :</span><span class="sxs-lookup"><span data-stu-id="0f458-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="0f458-117">Vous pouvez utiliser l’applet de commande **Get-Member** pour afficher des informations sur le contenu de variables.</span><span class="sxs-lookup"><span data-stu-id="0f458-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="0f458-118">Le piping de $loc vers l’applet de commande Get-Member montre qu’il s’agit d’un objet **PathInfo**, tout comme la sortie de l’applet de commande Get-Location :</span><span class="sxs-lookup"><span data-stu-id="0f458-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="0f458-119">Manipulation de variables</span><span class="sxs-lookup"><span data-stu-id="0f458-119">Manipulating Variables</span></span>
<span data-ttu-id="0f458-120">Windows PowerShell fournit plusieurs commandes pour manipuler des variables.</span><span class="sxs-lookup"><span data-stu-id="0f458-120">Windows PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="0f458-121">Vous pouvez afficher leur liste complète sous forme lisible en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0f458-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="0f458-122">Outre les variables que vous créez dans votre session Windows PowerShell actuelle, il existe plusieurs variables définies par le système.</span><span class="sxs-lookup"><span data-stu-id="0f458-122">In addition to the variables you create in your current Windows PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="0f458-123">Vous pouvez utiliser l’applet de commande **Remove-Variable** pour effacer toutes les variables non contrôlées par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f458-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by Windows PowerShell.</span></span> <span data-ttu-id="0f458-124">Pour effacer toutes les variables, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="0f458-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="0f458-125">Cela a pour effet d’afficher l’invite de confirmation ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="0f458-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="0f458-126">Si vous exécutez ensuite l’applet de commande **Get-Variable**, vous voyez les autres variables Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f458-126">If you then run the **Get-Variable** cmdlet, you will see the remaining Windows PowerShell variables.</span></span> <span data-ttu-id="0f458-127">Dans la mesure où il existe également un lecteur Windows PowerShell variable, vous pouvez également afficher toutes les variables Windows PowerShell en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0f458-127">Since there is also a variable Windows PowerShell drive, you can also display all Windows PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="0f458-128">Utilisation de variables Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="0f458-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="0f458-129">Bien que Windows PowerShell ne soit pas Cmd.exe, il s’exécute dans un environnement d’interface de commande, et peut utiliser les mêmes variables que celles disponibles tout environnement sous Windows.</span><span class="sxs-lookup"><span data-stu-id="0f458-129">Although Windows PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="0f458-130">Ces variables sont exposées via un lecteur nommé **env**:.</span><span class="sxs-lookup"><span data-stu-id="0f458-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="0f458-131">Vous pouvez consulter ces variables en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0f458-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="0f458-132">Si les applets de commande variables standards ne sont pas conçues pour fonctionner avec des variables **env :**, vous pouvez toujours utiliser celles-ci en spécifiant le préfixe **env:**.</span><span class="sxs-lookup"><span data-stu-id="0f458-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="0f458-133">Par exemple, pour afficher le répertoire racine du système d’exploitation, vous pouvez utiliser la variable **%systemroot%** de l’interface de commande à partir de Windows PowerShell en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="0f458-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within Windows PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="0f458-134">Vous pouvez également créer et modifier des variables d’environnement à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f458-134">You can also create and modify environment variables from within Windows PowerShell.</span></span> <span data-ttu-id="0f458-135">Les variables d’environnement auxquelles vous accédez à partir de Windows PowerShell sont conformes aux règles normales applicables aux variables d’environnement ailleurs dans Windows.</span><span class="sxs-lookup"><span data-stu-id="0f458-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>

