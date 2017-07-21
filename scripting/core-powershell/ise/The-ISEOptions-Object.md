---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Objet ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 56bdd5999b46b6e29e762c2d9a2060cebe3a1299
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="2b318-103">Objet ISEOptions</span><span class="sxs-lookup"><span data-stu-id="2b318-103">The ISEOptions Object</span></span>
  <span data-ttu-id="2b318-104">L’objet **ISEOptions** représente différents paramètres pour Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b318-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="2b318-105">Il s’agit d’une instance de la classe **Microsoft.PowerShell.Host.ISE.ISEOptions**.</span><span class="sxs-lookup"><span data-stu-id="2b318-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="2b318-106">L’objet **ISEOptions** fournit les méthodes et propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="2b318-106">The **ISEOptions** object provides the following methods and properties.</span></span>

 <span data-ttu-id="2b318-107">**Méthodes**</span><span class="sxs-lookup"><span data-stu-id="2b318-107">**Methods**</span></span>

-   [<span data-ttu-id="2b318-108">RestoreDefaultConsoleTokenColors()</span><span class="sxs-lookup"><span data-stu-id="2b318-108">RestoreDefaultConsoleTokenColors()</span></span>](#rdctc)

-   [<span data-ttu-id="2b318-109">RestoreDefaults()</span><span class="sxs-lookup"><span data-stu-id="2b318-109">RestoreDefaults()</span></span>](#rd)

-   [<span data-ttu-id="2b318-110">RestoreDefaultTokenColors()</span><span class="sxs-lookup"><span data-stu-id="2b318-110">RestoreDefaultTokenColors()</span></span>](#rdtc)

-   [<span data-ttu-id="2b318-111">RestoreDefaultXmlTokenColors()</span><span class="sxs-lookup"><span data-stu-id="2b318-111">RestoreDefaultXmlTokenColors()</span></span>](#rdxtc)

 <span data-ttu-id="2b318-112">**Propriétés**</span><span class="sxs-lookup"><span data-stu-id="2b318-112">**Properties**</span></span>

-   [<span data-ttu-id="2b318-113">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="2b318-113">AutoSaveMinuteInterval</span></span>](#asmi)

-   [<span data-ttu-id="2b318-114">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-114">CommandPaneBackgroundColor</span></span>](#cpbc)

-   [<span data-ttu-id="2b318-115">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="2b318-115">CommandPaneUp</span></span>](#cpu)

-   [<span data-ttu-id="2b318-116">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-116">ConsolePaneBackgroundColor</span></span>](#conpbc)

-   [<span data-ttu-id="2b318-117">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-117">ConsolePaneForegroundColor</span></span>](#conpfc)

-   [<span data-ttu-id="2b318-118">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-118">ConsolePaneTextBackgroundColor</span></span>](#conptbc)

-   [<span data-ttu-id="2b318-119">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="2b318-119">ConsoleTokenColors</span></span>](#contc)

-   [<span data-ttu-id="2b318-120">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-120">DebugBackgroundColor</span></span>](#dbc)

-   [<span data-ttu-id="2b318-121">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-121">DebugForegroundColor</span></span>](#dfc)

-   [<span data-ttu-id="2b318-122">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="2b318-122">DefaultOptions</span></span>](#do)

-   [<span data-ttu-id="2b318-123">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-123">ErrorBackgroundColor</span></span>](#ebc)

-   [<span data-ttu-id="2b318-124">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-124">ErrorForegroundColor</span></span>](#efc)

-   [<span data-ttu-id="2b318-125">FontName</span><span class="sxs-lookup"><span data-stu-id="2b318-125">FontName</span></span>](#fn)

-   [<span data-ttu-id="2b318-126">FontSize</span><span class="sxs-lookup"><span data-stu-id="2b318-126">FontSize</span></span>](#fs)

-   [<span data-ttu-id="2b318-127">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="2b318-127">IntellisenseTimeoutInSeconds</span></span>](#itis)

-   [<span data-ttu-id="2b318-128">MruCount</span><span class="sxs-lookup"><span data-stu-id="2b318-128">MruCount</span></span>](#mc)

-   [<span data-ttu-id="2b318-129">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-129">OutputPaneBackgroundColor</span></span>](#opbc)

-   [<span data-ttu-id="2b318-130">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-130">OutputPaneTextForegroundColor</span></span>](#optfc)

-   [<span data-ttu-id="2b318-131">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-131">OutputPaneTextBackgroundColor</span></span>](#optbc)

-   [<span data-ttu-id="2b318-132">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-132">ScriptPaneBackgroundColor</span></span>](#spbc)

-   [<span data-ttu-id="2b318-133">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-133">ScriptPaneForegroundColor</span></span>](#spfc)

-   [<span data-ttu-id="2b318-134">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="2b318-134">SelectedScriptPaneState</span></span>](#ssps)

-   [<span data-ttu-id="2b318-135">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="2b318-135">ShowDefaultSnippets</span></span>](#sds)

-   [<span data-ttu-id="2b318-136">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="2b318-136">ShowIntellisenseInConsolePane</span></span>](#siicp)

-   [<span data-ttu-id="2b318-137">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="2b318-137">ShowIntellisenseInScriptPane</span></span>](#siisp)

-   [<span data-ttu-id="2b318-138">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="2b318-138">ShowLineNumbers</span></span>](#sln)

-   [<span data-ttu-id="2b318-139">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="2b318-139">ShowOutlining</span></span>](#so)

-   [<span data-ttu-id="2b318-140">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="2b318-140">ShowToolBar</span></span>](#stb)

-   [<span data-ttu-id="2b318-141">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="2b318-141">ShowWarningBeforeSavingOnRun</span></span>](#swbsor)

-   [<span data-ttu-id="2b318-142">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="2b318-142">ShowWarningForDuplicateFiles</span></span>](#swfdf)

-   [<span data-ttu-id="2b318-143">TokenColors</span><span class="sxs-lookup"><span data-stu-id="2b318-143">TokenColors</span></span>](#tc)

-   [<span data-ttu-id="2b318-144">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="2b318-144">UseEnterToSelectInConsolePaneIntellisense</span></span>](#uetsicpi)

-   [<span data-ttu-id="2b318-145">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="2b318-145">UseEnterToSelectInScriptPaneIntellisense</span></span>](#uetsispi)

-   [<span data-ttu-id="2b318-146">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="2b318-146">UseLocalHelp</span></span>](#ulh)

-   [<span data-ttu-id="2b318-147">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-147">VerboseBackgroundColor</span></span>](#vbc)

-   [<span data-ttu-id="2b318-148">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-148">VerboseForegroundColor</span></span>](#vfc)

-   [<span data-ttu-id="2b318-149">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-149">WarningBackgroundColor</span></span>](#wbc)

-   [<span data-ttu-id="2b318-150">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-150">WarningForegroundColor</span></span>](#wfc)

-   [<span data-ttu-id="2b318-151">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="2b318-151">XmlTokenColors</span></span>](#xtc)

-   [<span data-ttu-id="2b318-152">Zoom</span><span class="sxs-lookup"><span data-stu-id="2b318-152">Zoom</span></span>](#z)

## <a name="methods"></a><span data-ttu-id="2b318-153">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2b318-153">Methods</span></span>

###  <span data-ttu-id="2b318-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="2b318-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="2b318-155">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-156">Restaure les valeurs par défaut des couleurs de jeton dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-156">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

###  <span data-ttu-id="2b318-157"><a name="rd"></a> RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="2b318-157"><a name="rd"></a> RestoreDefaults\(\)</span></span>
  <span data-ttu-id="2b318-158">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-159">Restaure les valeurs par défaut de tous les paramètres d’options dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-159">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="2b318-160">Elle réinitialise également le comportement des différents messages d’avertissement qui contiennent la case à cocher standard permettant de ne plus afficher les messages.</span><span class="sxs-lookup"><span data-stu-id="2b318-160">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

###  <span data-ttu-id="2b318-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="2b318-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="2b318-162">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-163">Restaure les valeurs par défaut des couleurs de jeton dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="2b318-163">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

###  <span data-ttu-id="2b318-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="2b318-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="2b318-165">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-165">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-166">Restaure les valeurs par défaut des couleurs de jeton pour les éléments XML affichés dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b318-166">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="2b318-167">Consultez également [XmlTokenColors](#xtc).</span><span class="sxs-lookup"><span data-stu-id="2b318-167">Also see [XmlTokenColors](#xtc).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="2b318-168">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2b318-168">Properties</span></span>

###  <span data-ttu-id="2b318-169"><a name="asmi"></a> AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="2b318-169"><a name="asmi"></a> AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="2b318-170">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-170">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-171">Spécifie le nombre de minutes entre chaque sauvegarde automatique de vos fichiers par Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b318-171">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="2b318-172">La valeur par défaut est deux minutes.</span><span class="sxs-lookup"><span data-stu-id="2b318-172">The default value is 2 minutes.</span></span> <span data-ttu-id="2b318-173">La valeur est un entier.</span><span class="sxs-lookup"><span data-stu-id="2b318-173">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

###  <span data-ttu-id="2b318-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="2b318-175">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="2b318-175">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="2b318-176">Pour les versions ultérieures, consultez [ConsolePaneBackgroundColor](#conpbc).</span><span class="sxs-lookup"><span data-stu-id="2b318-176">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="2b318-177">Spécifie la couleur d’arrière-plan pour le volet de commandes.</span><span class="sxs-lookup"><span data-stu-id="2b318-177">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="2b318-178">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="2b318-178">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

###  <span data-ttu-id="2b318-179"><a name="cpu"></a> CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="2b318-179"><a name="cpu"></a> CommandPaneUp</span></span>
  <span data-ttu-id="2b318-180">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="2b318-180">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="2b318-181">Spécifie si le volet de commandes se trouve au-dessus du volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="2b318-181">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

###  <span data-ttu-id="2b318-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="2b318-183">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-183">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-184">Spécifie la couleur d’arrière-plan pour le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-184">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="2b318-185">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="2b318-185">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

###  <span data-ttu-id="2b318-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="2b318-187">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-188">Spécifie la couleur de premier plan pour le texte affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-188">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

###  <span data-ttu-id="2b318-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="2b318-190">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-190">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-191">Spécifie la couleur d’arrière-plan pour le texte affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-191">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="2b318-192"><a name="contc"></a> ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="2b318-192"><a name="contc"></a> ConsoleTokenColors</span></span>
  <span data-ttu-id="2b318-193">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-193">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-194">Spécifie les couleurs des jetons IntelliSense dans le volet de la console Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b318-194">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="2b318-195">Cette propriété est un objet dictionnaire qui contient les paires nom\/valeur des types et couleurs des jetons dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-195">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="2b318-196">Pour modifier les couleurs des jetons IntelliSense dans le volet de script, consultez [TokenColors](#tc).</span><span class="sxs-lookup"><span data-stu-id="2b318-196">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tc).</span></span> <span data-ttu-id="2b318-197">Pour restaurer les valeurs par défaut des couleurs, consultez [RestoreDefaultConsoleTokenColors()](#rdctc).</span><span class="sxs-lookup"><span data-stu-id="2b318-197">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors()](#rdctc).</span></span> <span data-ttu-id="2b318-198">Les couleurs des jetons peuvent être définies pour les éléments suivants : Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="2b318-198">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="2b318-199"><a name="dbc"></a> DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-199"><a name="dbc"></a> DebugBackgroundColor</span></span>
  <span data-ttu-id="2b318-200">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-200">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-201">Spécifie la couleur d’arrière-plan pour le texte de débogage affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-201">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="2b318-202">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="2b318-202">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="2b318-203"><a name="dfc"></a> DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-203"><a name="dfc"></a> DebugForegroundColor</span></span>
  <span data-ttu-id="2b318-204">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-204">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-205">Spécifie la couleur de premier plan pour le texte de débogage affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-205">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="2b318-206">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="2b318-206">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

###  <span data-ttu-id="2b318-207"><a name="do"></a> DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="2b318-207"><a name="do"></a> DefaultOptions</span></span>
  <span data-ttu-id="2b318-208">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-208">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-209">Collection de propriétés qui spécifient les valeurs par défaut à utiliser avec les méthodes Reset.</span><span class="sxs-lookup"><span data-stu-id="2b318-209">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3

```

###  <span data-ttu-id="2b318-210"><a name="ebc"></a> ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-210"><a name="ebc"></a> ErrorBackgroundColor</span></span>
  <span data-ttu-id="2b318-211">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-211">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-212">Spécifie la couleur d’arrière-plan pour le texte d’erreur affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-212">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="2b318-213">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="2b318-213">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

###  <span data-ttu-id="2b318-214"><a name="efc"></a> ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-214"><a name="efc"></a> ErrorForegroundColor</span></span>
  <span data-ttu-id="2b318-215">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-215">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-216">Spécifie la couleur de premier plan pour le texte d’erreur affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-216">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="2b318-217">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="2b318-217">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

###  <span data-ttu-id="2b318-218"><a name="fn"></a> FontName</span><span class="sxs-lookup"><span data-stu-id="2b318-218"><a name="fn"></a> FontName</span></span>
  <span data-ttu-id="2b318-219">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-219">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-220">Spécifie le nom de la police actuellement utilisée dans le volet de script et le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-220">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

###  <span data-ttu-id="2b318-221"><a name="fs"></a> FontSize</span><span class="sxs-lookup"><span data-stu-id="2b318-221"><a name="fs"></a> FontSize</span></span>
  <span data-ttu-id="2b318-222">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-222">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-223">Spécifie la taille de la police sous forme de nombre entier.</span><span class="sxs-lookup"><span data-stu-id="2b318-223">Specifies the font size as an integer.</span></span> <span data-ttu-id="2b318-224">Cette propriété s’applique au volet de script, au volet de commandes et au volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="2b318-224">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="2b318-225">La valeur doit être comprise entre 8 et 32.</span><span class="sxs-lookup"><span data-stu-id="2b318-225">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

###  <span data-ttu-id="2b318-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="2b318-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="2b318-227">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-227">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-228">Spécifie le nombre de secondes pendant lesquelles IntelliSense tente de résoudre le texte que vous venez de taper.</span><span class="sxs-lookup"><span data-stu-id="2b318-228">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="2b318-229">Après ce nombre de secondes, le délai de tentative IntelliSense expire et vous pouvez continuer à taper du texte.</span><span class="sxs-lookup"><span data-stu-id="2b318-229">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="2b318-230">La valeur par défaut est trois secondes.</span><span class="sxs-lookup"><span data-stu-id="2b318-230">The default value is 3 seconds.</span></span> <span data-ttu-id="2b318-231">La valeur est un entier.</span><span class="sxs-lookup"><span data-stu-id="2b318-231">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

###  <span data-ttu-id="2b318-232"><a name="mc"></a> MruCount</span><span class="sxs-lookup"><span data-stu-id="2b318-232"><a name="mc"></a> MruCount</span></span>
  <span data-ttu-id="2b318-233">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-233">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-234">Spécifie le nombre de fichiers récemment ouverts que Windows PowerShell ISE suit et affiche en bas du menu **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="2b318-234">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="2b318-235">La valeur par défaut est 10.</span><span class="sxs-lookup"><span data-stu-id="2b318-235">The default value is 10.</span></span> <span data-ttu-id="2b318-236">La valeur est un entier.</span><span class="sxs-lookup"><span data-stu-id="2b318-236">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

###  <span data-ttu-id="2b318-237"><a name="opbc"></a> OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-237"><a name="opbc"></a> OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="2b318-238">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="2b318-238">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="2b318-239">Pour les versions ultérieures, consultez [ConsolePaneBackgroundColor](#conpbc).</span><span class="sxs-lookup"><span data-stu-id="2b318-239">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="2b318-240">Propriété en lecture\/écriture qui obtient ou définit la couleur d’arrière-plan pour le volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="2b318-240">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="2b318-241">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="2b318-241">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

###  <span data-ttu-id="2b318-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="2b318-243">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="2b318-243">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="2b318-244">Pour les versions ultérieures, consultez [ConsolePaneForegroundColor](#conpfc).</span><span class="sxs-lookup"><span data-stu-id="2b318-244">For later versions, see [ConsolePaneForegroundColor](#conpfc).</span></span>

 <span data-ttu-id="2b318-245">Propriété en lecture\/écriture qui modifie la couleur de premier plan du texte affiché dans le volet de sortie de Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="2b318-245">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

###  <span data-ttu-id="2b318-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="2b318-247">Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="2b318-247">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="2b318-248">Pour les versions ultérieures, consultez [ConsolePaneTextBackgroundColor](#conptbc).</span><span class="sxs-lookup"><span data-stu-id="2b318-248">For later versions, see [ConsolePaneTextBackgroundColor](#conptbc).</span></span>

 <span data-ttu-id="2b318-249">Propriété en lecture/écriture qui modifie la couleur d’arrière-plan du texte affiché dans le volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="2b318-249">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="2b318-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="2b318-251">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-251">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-252">Propriété en lecture/écriture qui obtient ou définit la couleur d’arrière-plan pour les fichiers.</span><span class="sxs-lookup"><span data-stu-id="2b318-252">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="2b318-253">Il s’agit d’une instance de la classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="2b318-253">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = ”yellow”

```

###  <span data-ttu-id="2b318-254"><a name="spfc"></a> ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-254"><a name="spfc"></a> ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="2b318-255">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-255">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-256">Propriété en lecture/écriture qui obtient ou définit la couleur de premier plan pour les fichiers autres que de script dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="2b318-256">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="2b318-257">Pour définir la couleur de premier plan pour les fichiers de script, utilisez la propriété [TokenColors](The-ISEOptions-Object.md#tc).</span><span class="sxs-lookup"><span data-stu-id="2b318-257">To set the foreground color for script files, use the [TokenColors](The-ISEOptions-Object.md#tc) property.</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

###  <span data-ttu-id="2b318-258"><a name="ssps"></a> SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="2b318-258"><a name="ssps"></a> SelectedScriptPaneState</span></span>
  <span data-ttu-id="2b318-259">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-259">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-260">Propriété en lecture/écriture qui obtient ou définit l’emplacement du volet de script à l’écran.</span><span class="sxs-lookup"><span data-stu-id="2b318-260">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="2b318-261">Les valeurs possibles sont « Maximized », « Top » ou « Right ».</span><span class="sxs-lookup"><span data-stu-id="2b318-261">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

###  <span data-ttu-id="2b318-262"><a name="sds"></a> ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="2b318-262"><a name="sds"></a> ShowDefaultSnippets</span></span>
  <span data-ttu-id="2b318-263">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-264">Spécifie si la liste **Ctrl+J** des extraits de code inclut les éléments de démarrage qui sont fournis dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b318-264">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="2b318-265">Si cette propriété a la valeur **$false**, la liste **Ctrl+J** contient uniquement les extraits de code définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2b318-265">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="2b318-266">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="2b318-266">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

###  <span data-ttu-id="2b318-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="2b318-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="2b318-268">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-268">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-269">Spécifie si IntelliSense affiche des suggestions de syntaxe, de paramètre et de valeur dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-269">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="2b318-270">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="2b318-270">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

###  <span data-ttu-id="2b318-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="2b318-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="2b318-272">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-272">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-273">Spécifie si IntelliSense affiche des suggestions de syntaxe, de paramètre et de valeur dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="2b318-273">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="2b318-274">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="2b318-274">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

###  <span data-ttu-id="2b318-275"><a name="sln"></a> ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="2b318-275"><a name="sln"></a> ShowLineNumbers</span></span>
  <span data-ttu-id="2b318-276">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-276">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-277">Spécifie si le volet de script affiche les numéros de ligne dans la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="2b318-277">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="2b318-278">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="2b318-278">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

###  <span data-ttu-id="2b318-279"><a name="so"></a> ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="2b318-279"><a name="so"></a> ShowOutlining</span></span>
  <span data-ttu-id="2b318-280">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-280">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-281">Spécifie si le volet de script affiche des crochets pouvant être développés et réduits en regard des sections de code dans la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="2b318-281">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="2b318-282">Quand les crochets sont affichés, vous pouvez cliquer sur l’icône avec le signe moins \(-\) à côté du bloc de texte à réduire ou sur l’icône avec le signe plus \(+\) pour le développer.</span><span class="sxs-lookup"><span data-stu-id="2b318-282">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="2b318-283">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="2b318-283">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

###  <span data-ttu-id="2b318-284"><a name="stb"></a> ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="2b318-284"><a name="stb"></a> ShowToolBar</span></span>
  <span data-ttu-id="2b318-285">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-286">Spécifie si la barre d’outils ISE est affichée en haut de la fenêtre Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b318-286">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="2b318-287">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="2b318-287">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

###  <span data-ttu-id="2b318-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="2b318-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="2b318-289">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-289">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-290">Spécifie si un message d’avertissement s’affiche quand un script est automatiquement enregistré avant de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="2b318-290">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="2b318-291">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="2b318-291">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

###  <span data-ttu-id="2b318-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="2b318-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="2b318-293">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-293">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-294">Spécifie si un message d’avertissement s’affiche quand le même fichier est ouvert dans plusieurs onglets PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b318-294">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="2b318-295">Si cette propriété a la valeur **$true**, l’ouverture du même fichier dans plusieurs onglets entraîne l’affichage de ce message : « Une copie de ce fichier est ouverte dans un autre onglet PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b318-295">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab.</span></span> <span data-ttu-id="2b318-296">Les modifications apportées à ce fichier affecteront toutes les copies ouvertes. »</span><span class="sxs-lookup"><span data-stu-id="2b318-296">Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="2b318-297">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="2b318-297">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

###  <span data-ttu-id="2b318-298"><a name="tc"></a> TokenColors</span><span class="sxs-lookup"><span data-stu-id="2b318-298"><a name="tc"></a> TokenColors</span></span>
  <span data-ttu-id="2b318-299">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-299">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-300">Spécifie les couleurs des jetons IntelliSense dans le volet de script Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b318-300">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="2b318-301">Cette propriété est un objet dictionnaire qui contient les paires nom/valeur des types et couleurs des jetons dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="2b318-301">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="2b318-302">Pour modifier les couleurs des jetons IntelliSense dans le volet de la console, consultez [ConsoleTokenColors](#contc).</span><span class="sxs-lookup"><span data-stu-id="2b318-302">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#contc).</span></span> <span data-ttu-id="2b318-303">Pour restaurer les valeurs par défaut des couleurs, consultez [RestoreDefaultTokenColors()](#rdtc).</span><span class="sxs-lookup"><span data-stu-id="2b318-303">To reset the colors to the default values, see [RestoreDefaultTokenColors()](#rdtc).</span></span> <span data-ttu-id="2b318-304">Les couleurs des jetons peuvent être définies pour les éléments suivants : Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="2b318-304">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="2b318-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="2b318-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="2b318-306">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-306">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-307">Spécifie si vous pouvez utiliser la touche Entrée pour sélectionner une option fournie par IntelliSense dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-307">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="2b318-308">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="2b318-308">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

###  <span data-ttu-id="2b318-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="2b318-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="2b318-310">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-310">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-311">Spécifie si vous pouvez utiliser la touche Entrée pour sélectionner une option fournie par IntelliSense dans le volet de script.</span><span class="sxs-lookup"><span data-stu-id="2b318-311">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="2b318-312">La valeur par défaut est **$true**.</span><span class="sxs-lookup"><span data-stu-id="2b318-312">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

###  <span data-ttu-id="2b318-313"><a name="ulh"></a> UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="2b318-313"><a name="ulh"></a> UseLocalHelp</span></span>
  <span data-ttu-id="2b318-314">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-314">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-315">Spécifie si l’aide installée localement ou l’aide en ligne de la bibliothèque TechNet s’affiche quand vous appuyez sur F1 après avoir placé le curseur dans un mot clé.</span><span class="sxs-lookup"><span data-stu-id="2b318-315">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="2b318-316">Si cette propriété a la valeur **$true**, une fenêtre contextuelle affiche le contenu de l’aide installée localement.</span><span class="sxs-lookup"><span data-stu-id="2b318-316">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="2b318-317">Vous pouvez installer les fichiers d’aide en exécutant la commande `Update-Help`.</span><span class="sxs-lookup"><span data-stu-id="2b318-317">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="2b318-318">Si cette propriété a la valeur **$false**, votre navigateur s’ouvre et affiche une page de la bibliothèque TechNet.</span><span class="sxs-lookup"><span data-stu-id="2b318-318">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

###  <span data-ttu-id="2b318-319"><a name="vbc"></a> VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-319"><a name="vbc"></a> VerboseBackgroundColor</span></span>
  <span data-ttu-id="2b318-320">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-320">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-321">Spécifie la couleur d’arrière-plan pour le texte de commentaire affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-321">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="2b318-322">Il s’agit d’un objet **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="2b318-322">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="2b318-323"><a name="vfc"></a> VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-323"><a name="vfc"></a> VerboseForegroundColor</span></span>
  <span data-ttu-id="2b318-324">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-324">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-325">Spécifie la couleur de premier plan pour le texte de commentaire affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-325">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="2b318-326">Il s’agit d’un objet **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="2b318-326">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor =”yellow”
```

###  <span data-ttu-id="2b318-327"><a name="wbc"></a> WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-327"><a name="wbc"></a> WarningBackgroundColor</span></span>
  <span data-ttu-id="2b318-328">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-328">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-329">Spécifie la couleur d’arrière-plan pour le texte d’avertissement affiché dans le volet de la console.</span><span class="sxs-lookup"><span data-stu-id="2b318-329">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="2b318-330">Il s’agit d’un objet **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="2b318-330">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="2b318-331"><a name="wfc"></a> WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="2b318-331"><a name="wfc"></a> WarningForegroundColor</span></span>
  <span data-ttu-id="2b318-332">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-332">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="2b318-333">Spécifie la couleur de premier plan pour le texte d’avertissement affiché dans le volet de sortie.</span><span class="sxs-lookup"><span data-stu-id="2b318-333">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="2b318-334">Il s’agit d’un objet **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="2b318-334">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor =”yellow”
```

###  <span data-ttu-id="2b318-335"><a name="xtc"></a> XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="2b318-335"><a name="xtc"></a> XmlTokenColors</span></span>
  <span data-ttu-id="2b318-336">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-336">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-337">Spécifie un objet dictionnaire qui contient les paires nom/valeur des types et couleurs des jetons pour le contenu XML qui s’affiche dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2b318-337">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="2b318-338">Les couleurs des jetons peuvent être définies pour les éléments suivants : Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="2b318-338">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="2b318-339">Consultez également [RestoreDefaultXmlTokenColors()](#rdxtc).</span><span class="sxs-lookup"><span data-stu-id="2b318-339">Also see [RestoreDefaultXmlTokenColors()](#rdxtc).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

###  <span data-ttu-id="2b318-340"><a name="z"></a> Zoom</span><span class="sxs-lookup"><span data-stu-id="2b318-340"><a name="z"></a> Zoom</span></span>
  <span data-ttu-id="2b318-341">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="2b318-341">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="2b318-342">Spécifie la taille relative du texte dans les volets de la console et de script.</span><span class="sxs-lookup"><span data-stu-id="2b318-342">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="2b318-343">La valeur par défaut est 100.</span><span class="sxs-lookup"><span data-stu-id="2b318-343">The default value is 100.</span></span> <span data-ttu-id="2b318-344">Utilisez des valeurs plus basses pour réduire la taille du texte affiché dans Windows PowerShell ISE ou des valeurs plus élevées pour augmenter la taille du texte affiché.</span><span class="sxs-lookup"><span data-stu-id="2b318-344">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="2b318-345">La valeur est un nombre entier compris entre 20 et 400.</span><span class="sxs-lookup"><span data-stu-id="2b318-345">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="2b318-346">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b318-346">See Also</span></span>
- [<span data-ttu-id="2b318-347">Modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="2b318-347">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="2b318-348">Informations de référence sur le modèle objet Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="2b318-348">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

