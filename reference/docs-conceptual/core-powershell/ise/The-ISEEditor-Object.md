---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Objet ISEEditor
ms.assetid: 0101daf8-4e31-4e4c-ab89-01d95dcb8f46
ms.openlocfilehash: e2ddb0de1089c832f130e1f5c7c8dcb199aca2fa
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2017
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="8d7a3-103">Objet ISEEditor</span><span class="sxs-lookup"><span data-stu-id="8d7a3-103">The ISEEditor Object</span></span>
  <span data-ttu-id="8d7a3-104">Un objet **ISEEditor** est une instance de la classe Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="8d7a3-105">Le volet de la console est un objet **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="8d7a3-106">Chaque objet [ISEFile](The-ISEFile-Object.md) est associé à un objet **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="8d7a3-107">Les sections suivantes répertorient les méthodes et propriétés d’un objet **ISEEditor**.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="8d7a3-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8d7a3-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="8d7a3-109">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="8d7a3-109">Clear\(\)</span></span>
  <span data-ttu-id="8d7a3-110">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-111">Efface le texte affiché dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="8d7a3-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="8d7a3-112">EnsureVisible\(int lineNumber\)</span></span>
  <span data-ttu-id="8d7a3-113">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-114">Fait défiler l’éditeur pour afficher la ligne qui correspond à la valeur du paramètre **lineNumber** spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="8d7a3-115">Elle lève une exception si le numéro de ligne spécifié est en dehors de la plage 1-dernier numéro de ligne, qui définit les numéros de ligne valides.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

 <span data-ttu-id="8d7a3-116">**lineNumber** Numéro de la ligne à afficher.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="8d7a3-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="8d7a3-117">Focus\(\)</span></span>
  <span data-ttu-id="8d7a3-118">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-119">Définit le focus sur l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="8d7a3-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="8d7a3-120">GetLineLength\(int lineNumber \)</span></span>
  <span data-ttu-id="8d7a3-121">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-122">Obtient la longueur, sous forme d’entier, de la ligne spécifiée par le numéro de ligne.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

 <span data-ttu-id="8d7a3-123">**lineNumber** Numéro de la ligne dont la longueur doit être obtenue.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-123">**lineNumber** The number of the line of which to get the length.</span></span>

 <span data-ttu-id="8d7a3-124">**Returns** Longueur de la ligne correspondant au numéro de ligne spécifié.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="8d7a3-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="8d7a3-125">GoToMatch\(\)</span></span>
  <span data-ttu-id="8d7a3-126">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="8d7a3-127">Déplace le point d’insertion vers le caractère correspondant si la propriété **CanGoToMatch** de l’objet editor a la valeur **$true**. Ceci se produit quand le point d’insertion se situe juste avant une parenthèse ouvrante, un crochet ouvrant ou une accolade ouvrante \( \[,{ - ou juste après une parenthèse fermante, un crochet fermant ou une accolade fermante -\),\],}.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="8d7a3-128">Le point d’insertion se trouve avant un caractère ouvrant ou après un caractère fermant.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="8d7a3-129">Si la propriété **CanGoToMatch** a la valeur **$false**, cette méthode n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span> <span data-ttu-id="8d7a3-130">Consultez [CanGoToMatch]().</span><span class="sxs-lookup"><span data-stu-id="8d7a3-130">See [CanGoToMatch]().</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a><span data-ttu-id="8d7a3-131">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="8d7a3-131">InsertText\( text \)</span></span>
  <span data-ttu-id="8d7a3-132">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-132">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-133">Remplace la sélection par du texte ou insère du texte à la position actuelle du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-133">Replaces the selection with text or inserts text at the current caret position.</span></span>

 <span data-ttu-id="8d7a3-134">**text** : chaîne Texte à insérer.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-134">**text** - String The text to insert.</span></span>

 <span data-ttu-id="8d7a3-135">Consultez l’[exemple de script]() plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-135">See the [Scripting Example]() later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="8d7a3-136">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="8d7a3-136">Select\( startLine, startColumn, endLine, endColumn \)</span></span>
  <span data-ttu-id="8d7a3-137">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-137">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-138">Sélectionne le texte spécifié par les paramètres **startLine**, **startColumn**, **endLine** et **endColumn**.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-138">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

 <span data-ttu-id="8d7a3-139">**startLine** : entier Ligne où commence la sélection.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-139">**startLine** - Integer The line where the selection starts.</span></span>

 <span data-ttu-id="8d7a3-140">**startColumn** : entier Colonne dans la ligne de début où commence la sélection.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-140">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

 <span data-ttu-id="8d7a3-141">**endLine** : entier Ligne où se termine la sélection.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-141">**endLine** - Integer The line where the selection ends.</span></span>

 <span data-ttu-id="8d7a3-142">**endColumn** : entier Colonne dans la ligne de fin où se termine la sélection.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-142">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

 <span data-ttu-id="8d7a3-143">Consultez l’[exemple de script]() plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-143">See the  [Scripting Example]() later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="8d7a3-144">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="8d7a3-144">SelectCaretLine\(\)</span></span>
  <span data-ttu-id="8d7a3-145">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-145">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-146">Sélectionne la ligne entière de texte où se trouve actuellement le point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-146">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="8d7a3-147">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="8d7a3-147">SetCaretPosition\( lineNumber, columnNumber \)</span></span>
  <span data-ttu-id="8d7a3-148">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-148">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-149">Définit la position du point d’insertion en fonction du numéro de ligne et du numéro de colonne spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-149">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="8d7a3-150">Elle lève une exception si le numéro de ligne du point d’insertion ou le numéro de colonne du point d’insertion sont en dehors de leurs plages valides respectives.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-150">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

 <span data-ttu-id="8d7a3-151">**lineNumber** : entier Numéro de ligne du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-151">**lineNumber** - Integer The caret line number.</span></span>

 <span data-ttu-id="8d7a3-152">**columnNumber** : entier Numéro de colonne du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-152">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="8d7a3-153">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="8d7a3-153">ToggleOutliningExpansion\(\)</span></span>
  <span data-ttu-id="8d7a3-154">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="8d7a3-155">Développe ou réduit toutes les sections de plan.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-155">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="8d7a3-156">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8d7a3-156">Properties</span></span>

###  <span data-ttu-id="8d7a3-157"><a name="CanGoToMatch"></a> CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="8d7a3-157"><a name="CanGoToMatch"></a> CanGoToMatch</span></span>
  <span data-ttu-id="8d7a3-158">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-158">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="8d7a3-159">Propriété booléenne en lecture seule qui indique si le point d’insertion se trouve à côté d’une parenthèse, d’un crochet ou d’une accolade - \(\), \[\], {}.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-159">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="8d7a3-160">Si le point d’insertion est situé juste avant le caractère ouvrant ou juste après le caractère fermant d’une paire, cette propriété a la valeur **$true**.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-160">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="8d7a3-161">Sinon, elle a la valeur **$false**.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-161">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

###  <span data-ttu-id="8d7a3-162"><a name="CaretColumn"></a> CaretColumn</span><span class="sxs-lookup"><span data-stu-id="8d7a3-162"><a name="CaretColumn"></a> CaretColumn</span></span>
  <span data-ttu-id="8d7a3-163">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-163">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-164">Propriété en lecture seule qui obtient le numéro de colonne correspondant à la position du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-164">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

###  <span data-ttu-id="8d7a3-165"><a name="CaretLine"></a> CaretLine</span><span class="sxs-lookup"><span data-stu-id="8d7a3-165"><a name="CaretLine"></a> CaretLine</span></span>
  <span data-ttu-id="8d7a3-166">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-166">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-167">Propriété en lecture seule qui obtient le numéro de la ligne où se trouve le point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-167">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

###  <span data-ttu-id="8d7a3-168"><a name="CaretLineText"></a> CaretLineText</span><span class="sxs-lookup"><span data-stu-id="8d7a3-168"><a name="CaretLineText"></a> CaretLineText</span></span>
  <span data-ttu-id="8d7a3-169">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-170">Propriété en lecture seule qui obtient la ligne entière de texte où se trouve le point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-170">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

###  <span data-ttu-id="8d7a3-171"><a name="LineCount"></a> LineCount</span><span class="sxs-lookup"><span data-stu-id="8d7a3-171"><a name="LineCount"></a> LineCount</span></span>
  <span data-ttu-id="8d7a3-172">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-172">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-173">Propriété en lecture seule qui obtient le nombre de lignes affichées dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-173">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

###  <span data-ttu-id="8d7a3-174"><a name="SelectedText"></a> SelectedText</span><span class="sxs-lookup"><span data-stu-id="8d7a3-174"><a name="SelectedText"></a> SelectedText</span></span>
  <span data-ttu-id="8d7a3-175">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-175">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-176">Propriété en lecture seule qui obtient le texte sélectionné dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-176">The read-only property that gets the selected text from the editor.</span></span>

 <span data-ttu-id="8d7a3-177">Consultez l’[exemple de script]() plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-177">See the  [Scripting Example]() later in this topic.</span></span>

###  <span data-ttu-id="8d7a3-178"><a name="Text"></a> Text</span><span class="sxs-lookup"><span data-stu-id="8d7a3-178"><a name="Text"></a> Text</span></span>
  <span data-ttu-id="8d7a3-179">Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-179">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8d7a3-180">Propriété en lecture\/écriture qui obtient ou définit le texte dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-180">The read/write property that gets or sets the text in the editor.</span></span>

 <span data-ttu-id="8d7a3-181">Consultez l’[exemple de script]() plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-181">See the [Scripting Example]() later in this topic.</span></span>

##  <span data-ttu-id="8d7a3-182"><a name="example"></a> Exemple de script</span><span class="sxs-lookup"><span data-stu-id="8d7a3-182"><a name="example"></a> Scripting Example</span></span>

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase. 
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line. 
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="8d7a3-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d7a3-183">See Also</span></span>
- [<span data-ttu-id="8d7a3-184">Objet ISEFile</span><span class="sxs-lookup"><span data-stu-id="8d7a3-184">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="8d7a3-185">Objet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="8d7a3-185">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="8d7a3-186">Modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="8d7a3-186">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="8d7a3-187">Informations de référence sur le modèle objet Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="8d7a3-187">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="8d7a3-188">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="8d7a3-188">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
