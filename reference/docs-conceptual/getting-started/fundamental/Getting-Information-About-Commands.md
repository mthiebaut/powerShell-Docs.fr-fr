---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Obtention d'informations sur les commandes
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 98e449110860ea81939d6ec0b7b1a8534a2da2aa
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2017
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="313ca-103">Obtention d'informations sur les commandes</span><span class="sxs-lookup"><span data-stu-id="313ca-103">Getting Information About Commands</span></span>
<span data-ttu-id="313ca-104">L’applet de commande Windows PowerShell **Get-Command** permet d’obtenir toutes les commandes disponibles dans la session active.</span><span class="sxs-lookup"><span data-stu-id="313ca-104">The Windows PowerShell **Get-Command** cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="313ca-105">Quand vous tapez **Get-Command** dans une invite Windows PowerShell, la sortie est similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="313ca-105">When you type **Get-Command** at a Windows PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="313ca-106">Cette sortie ressemble beaucoup à la sortie Help de Cmd.exe, à savoir un résumé des commandes internes sous forme de tableau.</span><span class="sxs-lookup"><span data-stu-id="313ca-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="313ca-107">Dans l’extrait de la sortie de la commande **Get-Command** ci-dessus, chaque commande est de type Cmdlet (« applet de commande »).</span><span class="sxs-lookup"><span data-stu-id="313ca-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="313ca-108">Une applet de commande est un type de commande fondamental de Windows PowerShell, qui correspond à peu près aux commandes **dir** et **cd** de Cmd.exe, et aux commandes intégrées dans les interpréteurs de commandes UNIX tels que BASH.</span><span class="sxs-lookup"><span data-stu-id="313ca-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="313ca-109">Dans la sortie de la commande **Get-Command**, toutes les définitions se terminent par des points de suspension (...). Ceci indique que PowerShell ne peut pas afficher tout le contenu dans l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="313ca-109">In the output of the **Get-Command** command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="313ca-110">Quand Windows PowerShell affiche la sortie, il la met en forme en tant que texte et la réorganise pour faire tenir les données dans la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="313ca-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="313ca-111">Nous aborderons ce sujet plus loin dans la section sur les formateurs.</span><span class="sxs-lookup"><span data-stu-id="313ca-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="313ca-112">L’applet de commande **Get-Command** dispose d’un paramètre **Syntax** qui permet d’obtenir la syntaxe de chaque applet de commande.</span><span class="sxs-lookup"><span data-stu-id="313ca-112">The **Get-Command** cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="313ca-113">Pour obtenir la syntaxe de l'applet de commande Get-Help, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="313ca-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

<span data-ttu-id="313ca-114">**Get-Command Get-Help -Syntax**</span><span class="sxs-lookup"><span data-stu-id="313ca-114">**Get-Command Get-Help -Syntax**</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a><span data-ttu-id="313ca-115">Affichage des types de commandes disponibles</span><span class="sxs-lookup"><span data-stu-id="313ca-115">Displaying Available Command Types</span></span>
<span data-ttu-id="313ca-116">La commande **Get-Command** ne répertorie pas toutes les commandes disponibles dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="313ca-116">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="313ca-117">La commande **Get-Command** répertorie uniquement les applets de commande dans la session active.</span><span class="sxs-lookup"><span data-stu-id="313ca-117">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="313ca-118">Windows PowerShell prend en charge plusieurs autres types de commandes.</span><span class="sxs-lookup"><span data-stu-id="313ca-118">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="313ca-119">Les alias, fonctions et scripts sont aussi des commandes Windows PowerShell, bien qu'ils ne soient pas abordés en détail dans le Guide d'utilisation de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="313ca-119">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="313ca-120">Les fichiers externes exécutables ou possédant un gestionnaire de type de fichier inscrit sont également considérés comme des commandes.</span><span class="sxs-lookup"><span data-stu-id="313ca-120">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="313ca-121">Pour obtenir toutes les commandes dans la session, tapez :</span><span class="sxs-lookup"><span data-stu-id="313ca-121">To get all commands in the session, type:</span></span>

```
Get-Command *
```

<span data-ttu-id="313ca-122">Étant donné que cette liste recense les fichiers externes dans votre chemin de recherche, elle peut contenir des milliers d'éléments.</span><span class="sxs-lookup"><span data-stu-id="313ca-122">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="313ca-123">Il est plus judicieux d'examiner un ensemble réduit de commandes.</span><span class="sxs-lookup"><span data-stu-id="313ca-123">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="313ca-124">Pour obtenir les commandes natives d’autres types, utilisez le paramètre **CommandType** de l’applet de commande **Get-Command**.</span><span class="sxs-lookup"><span data-stu-id="313ca-124">To get native commands of other types, use the **CommandType** parameter of the **Get-Command** cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="313ca-125">L’astérisque (\*) est utilisé comme caractère générique dans les arguments de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="313ca-125">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="313ca-126">Le symbole \* représente un ou plusieurs caractères.</span><span class="sxs-lookup"><span data-stu-id="313ca-126">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="313ca-127">Pour rechercher toutes les commandes dont le nom commence par la lettre « a », vous pouvez taper **Get-Command \&#42;**.</span><span class="sxs-lookup"><span data-stu-id="313ca-127">You can type **Get-Command a\&#42;** to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="313ca-128">Contrairement aux caractères génériques dans Cmd.exe, un caractère générique peut représenter un point dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="313ca-128">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="313ca-129">Pour obtenir les alias des commandes, c'est-à-dire les surnoms affectés aux commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="313ca-129">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```
Get-Command -CommandType Alias
```

<span data-ttu-id="313ca-130">Pour obtenir les fonctions dans la session active, tapez :</span><span class="sxs-lookup"><span data-stu-id="313ca-130">To get the functions in the current session, type:</span></span>

```
Get-Command -CommandType Function
```

<span data-ttu-id="313ca-131">Pour afficher les scripts dans le chemin de recherche de Windows PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="313ca-131">To display scripts in Windows PowerShell's search path, type:</span></span>

```
Get-Command -CommandType Script
```

