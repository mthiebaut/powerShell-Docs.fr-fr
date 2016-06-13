---
title:  Objet ISEOptions
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  75e2a76f-f3d1-490b-ad5d-e3829946aabb
---

# Objet ISEOptions
  L’objet **ISEOptions** représente différents paramètres pour Windows PowerShell ISE. Il s’agit d’une instance de la classe **Microsoft.PowerShell.Host.ISE.ISEOptions**.

 L’objet **ISEOptions** fournit les méthodes et propriétés suivantes.

 **Méthodes**

-   [RestoreDefaultConsoleTokenColors()](#rdctc)

-   [RestoreDefaults()](#rd)

-   [RestoreDefaultConsoleTokenColors()](#rdtc)

-   [RestoreDefaultConsoleTokenColors()](#rdxtc)

 **Propriétés**

-   [AutoSaveMinuteInterval](#asmi)

-   [CommandPaneBackgroundColor](#cpbc)

-   [CommandPaneUp](#cpu)

-   [ConsolePaneBackgroundColor](#conpbc)

-   [ConsolePaneForegroundColor](#conpfc)

-   [ConsolePaneTextBackgroundColor](#conptbc)

-   [ConsoleTokenColors](#contc)

-   [DebugBackgroundColor](#dbc)

-   [DebugForegroundColor](#dfc)

-   [DefaultOptions](#do)

-   [ErrorBackgroundColor](#ebc)

-   [ErrorForegroundColor](#efc)

-   [FontName](#fn)

-   [FontSize](#fs)

-   [IntellisenseTimeoutInSeconds](#itis)

-   [MruCount](#mc)

-   [OutputPaneBackgroundColor](#opbc)

-   [OutputPaneTextForegroundColor](#optfc)

-   [OutputPaneTextBackgroundColor](#optbc)

-   [ScriptPaneBackgroundColor](#spbc)

-   [ScriptPaneForegroundColor](#spfc)

-   [SelectedScriptPaneState](#ssps)

-   [ShowDefaultSnippets](#sds)

-   [ShowIntellisenseInConsolePane](#siicp)

-   [ShowIntellisenseInScriptPane](#siisp)

-   [ShowLineNumbers](#sln)

-   [ShowOutlining](#so)

-   [ShowToolBar](#stb)

-   [ShowWarningBeforeSavingOnRun](#swbsor)

-   [ShowWarningForDuplicateFiles](#swfdf)

-   [TokenColors](#tc)

-   [UseEnterToSelectInConsolePaneIntellisense](#uetsicpi)

-   [UseEnterToSelectInScriptPaneIntellisense](#uetsispi)

-   [UseLocalHelp](#ulh)

-   [VerboseBackgroundColor](#vbc)

-   [VerboseForegroundColor](#vfc)

-   [WarningBackgroundColor](#wbc)

-   [WarningForegroundColor](#wfc)

-   [XmlTokenColors](#xtc)

-   [Zoom](#z)

## Méthodes

###  <a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Restaure les valeurs par défaut des couleurs de jeton dans le volet de la console.

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

###  <a name="rd"></a> RestoreDefaults\(\)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Restaure les valeurs par défaut de tous les paramètres d’options dans le volet de la console. Elle réinitialise également le comportement des différents messages d’avertissement qui contiennent la case à cocher standard permettant de ne plus afficher les messages.

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

###  <a name="rdtc"></a> RestoreDefaultTokenColors\(\)
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Restaure les valeurs par défaut des couleurs de jeton dans le volet de script.

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

###  <a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Restaure les valeurs par défaut des couleurs de jeton pour les éléments XML affichés dans Windows PowerShell ISE. Consultez également [XmlTokenColors](#xtc).

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## Propriétés

###  <a name="asmi"></a> AutoSaveMinuteInterval
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie le nombre de minutes entre chaque sauvegarde automatique de vos fichiers par Windows PowerShell ISE. La valeur par défaut est deux minutes. La valeur est un entier.

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

###  <a name="cpbc"></a> CommandPaneBackgroundColor
  Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.  Pour les versions ultérieures, consultez [ConsolePaneBackgroundColor](#conpbc).

 Spécifie la couleur d’arrière-plan pour le volet de commandes. Il s’agit d’une instance de la classe **System.Windows.Media.Color**.

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

###  <a name="cpu"></a> CommandPaneUp
  Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.

 Spécifie si le volet de commandes se trouve au-dessus du volet de sortie.

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

###  <a name="conpbc"></a> ConsolePaneBackgroundColor
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie la couleur d’arrière-plan pour le volet de la console. Il s’agit d’une instance de la classe **System.Windows.Media.Color**.

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

###  <a name="conpfc"></a> ConsolePaneForegroundColor
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie la couleur de premier plan pour le texte affiché dans le volet de la console.

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

###  <a name="conptbc"></a> ConsolePaneTextBackgroundColor
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie la couleur d’arrière-plan pour le texte affiché dans le volet de la console.

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

###  <a name="contc"></a> ConsoleTokenColors
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie les couleurs des jetons IntelliSense dans le volet de la console Windows PowerShell ISE. Cette propriété est un objet dictionnaire qui contient les paires nom\/valeur des types et couleurs des jetons dans le volet de la console. Pour modifier les couleurs des jetons IntelliSense dans le volet de script, consultez [TokenColors](#tc). Pour restaurer les valeurs par défaut des couleurs, consultez [RestoreDefaultConsoleTokenColors()](#rdctc). Les couleurs des jetons peuvent être définies pour les éléments suivants : Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

###  <a name="dbc"></a> DebugBackgroundColor
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie la couleur d’arrière-plan pour le texte de débogage affiché dans le volet de la console. Il s’agit d’une instance de la classe **System.Windows.Media.Color**.

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

###  <a name="dfc"></a> DebugForegroundColor
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie la couleur de premier plan pour le texte de débogage affiché dans le volet de la console. Il s’agit d’une instance de la classe **System.Windows.Media.Color**.

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

###  <a name="do"></a> DefaultOptions
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Collection de propriétés qui spécifient les valeurs par défaut à utiliser avec les méthodes Reset.

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

###  <a name="ebc"></a> ErrorBackgroundColor
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie la couleur d’arrière-plan pour le texte d’erreur affiché dans le volet de la console. Il s’agit d’une instance de la classe **System.Windows.Media.Color**.

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

###  <a name="efc"></a> ErrorForegroundColor
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie la couleur de premier plan pour le texte d’erreur affiché dans le volet de la console. Il s’agit d’une instance de la classe **System.Windows.Media.Color**.

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

###  <a name="fn"></a> FontName
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie le nom de la police actuellement utilisée dans le volet de script et le volet de la console.

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

###  <a name="fs"></a> FontSize
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie la taille de la police sous forme de nombre entier. Cette propriété s’applique au volet de script, au volet de commandes et au volet de sortie. La valeur doit être comprise entre 8 et 32.

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

###  <a name="itis"></a> IntellisenseTimeoutInSeconds
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie le nombre de secondes pendant lesquelles IntelliSense tente de résoudre le texte que vous venez de taper. Après ce nombre de secondes, le délai de tentative IntelliSense expire et vous pouvez continuer à taper du texte. La valeur par défaut est trois secondes. La valeur est un entier.

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

###  <a name="mc"></a> MruCount
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie le nombre de fichiers récemment ouverts que Windows PowerShell ISE suit et affiche en bas du menu **Ouvrir**. La valeur par défaut est 10. La valeur est un entier.

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

###  <a name="opbc"></a> OutputPaneBackgroundColor
  Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.  Pour les versions ultérieures, consultez [ConsolePaneBackgroundColor](#conpbc).

 Propriété en lecture\/écriture qui obtient ou définit la couleur d’arrière-plan pour le volet de sortie. Il s’agit d’une instance de la classe **System.Windows.Media.Color**.

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

###  <a name="optfc"></a> OutputPaneTextForegroundColor
  Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.  Pour les versions ultérieures, consultez [ConsolePaneForegroundColor](#conpfc).

 Propriété en lecture\/écriture qui modifie la couleur de premier plan du texte affiché dans le volet de sortie de Windows PowerShell ISE 2.0.

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

###  <a name="optbc"></a> OutputPaneTextBackgroundColor
  Cette fonctionnalité est présente dans Windows PowerShell ISE 2.0, mais a été supprimée ou renommée dans les versions ultérieures de l'environnement ISE.  Pour les versions ultérieures, consultez [ConsolePaneTextBackgroundColor](#conptbc).

 Propriété en lecture\/écriture qui modifie la couleur d’arrière-plan du texte affiché dans le volet de sortie.

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

###  <a name="spbc"></a> ScriptPaneBackgroundColor
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Propriété en lecture\/écriture qui obtient ou définit la couleur d’arrière-plan pour les fichiers. Il s’agit d’une instance de la classe **System.Windows.Media.Color**.

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = ”yellow”

```

###  <a name="spfc"></a> ScriptPaneForegroundColor
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Propriété en lecture\/écriture qui obtient ou définit la couleur de premier plan pour les fichiers autres que de script dans le volet de script.
Pour définir la couleur de premier plan pour les fichiers de script, utilisez la propriété [TokenColors](The-ISEOptions-Object.md#tc).

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

###  <a name="ssps"></a> SelectedScriptPaneState
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Propriété en lecture\/écriture qui obtient ou définit l’emplacement du volet de script à l’écran. Les valeurs possibles sont « Maximized », « Top » ou « Right ».

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

###  <a name="sds"></a> ShowDefaultSnippets
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie si la liste **Ctrl\+J** des extraits de code inclut les éléments de démarrage qui sont fournis dans Windows PowerShell. Si cette propriété a la valeur **$false**, la liste **Ctrl\+J** contient uniquement les extraits de code définis par l’utilisateur. La valeur par défaut est **$true**.

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

###  <a name="siicp"></a> ShowIntellisenseInConsolePane
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie si IntelliSense affiche des suggestions de syntaxe, de paramètre et de valeur dans le volet de la console. La valeur par défaut est **$true**.

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

###  <a name="siisp"></a> ShowIntellisenseInScriptPane
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie si IntelliSense affiche des suggestions de syntaxe, de paramètre et de valeur dans le volet de script. La valeur par défaut est **$true**.

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

###  <a name="sln"></a> ShowLineNumbers
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie si le volet de script affiche les numéros de ligne dans la marge de gauche. La valeur par défaut est **$true**.

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

###  <a name="so"></a> ShowOutlining
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie si le volet de script affiche des crochets pouvant être développés et réduits en regard des sections de code dans la marge de gauche. Quand les crochets sont affichés, vous pouvez cliquer sur l’icône avec le signe moins \(\-\) à côté du bloc de texte à réduire ou sur l’icône avec le signe plus \(\+\) pour le développer. La valeur par défaut est **$true**.

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

###  <a name="stb"></a> ShowToolBar
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie si la barre d’outils ISE est affichée en haut de la fenêtre Windows PowerShell ISE. La valeur par défaut est **$true**.

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

###  <a name="swbsor"></a> ShowWarningBeforeSavingOnRun
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie si un message d’avertissement s’affiche quand un script est automatiquement enregistré avant de s’exécuter. La valeur par défaut est **$true**.

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

###  <a name="swfdf"></a> ShowWarningForDuplicateFiles
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie si un message d’avertissement s’affiche quand le même fichier est ouvert dans plusieurs onglets PowerShell. Si cette propriété a la valeur **$true**, l’ouverture du même fichier dans plusieurs onglets entraîne l’affichage de ce message : « Une copie de ce fichier est ouverte dans un autre onglet PowerShell. Les modifications apportées à ce fichier affecteront toutes les copies ouvertes. » La valeur par défaut est **$true**.

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

###  <a name="tc"></a> TokenColors
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie les couleurs des jetons IntelliSense dans le volet de script Windows PowerShell ISE. Cette propriété est un objet dictionnaire qui contient les paires nom\/valeur des types et couleurs des jetons dans le volet de script. Pour modifier les couleurs des jetons IntelliSense dans le volet de la console, consultez [ConsoleTokenColors](#contc). Pour restaurer les valeurs par défaut des couleurs, consultez [RestoreDefaultTokenColors()](#rdtc). Les couleurs des jetons peuvent être définies pour les éléments suivants : Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

###  <a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie si vous pouvez utiliser la touche Entrée pour sélectionner une option fournie par IntelliSense dans le volet de la console. La valeur par défaut est **$true**.

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

###  <a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie si vous pouvez utiliser la touche Entrée pour sélectionner une option fournie par IntelliSense dans le volet de script. La valeur par défaut est **$true**.

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

###  <a name="ulh"></a> UseLocalHelp
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie si l’aide installée localement ou l’aide en ligne de la bibliothèque TechNet s’affiche quand vous appuyez sur F1 après avoir placé le curseur dans un mot clé. Si cette propriété a la valeur **$true**, une fenêtre contextuelle affiche le contenu de l’aide installée localement. Vous pouvez installer les fichiers d’aide en exécutant la commande `Update-Help`. Si cette propriété a la valeur **$false**, votre navigateur s’ouvre et affiche une page de la bibliothèque TechNet.

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

###  <a name="vbc"></a> VerboseBackgroundColor
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie la couleur d’arrière-plan pour le texte de commentaire affiché dans le volet de la console. Il s’agit d’un objet **System.Windows.Media.Color**.

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

###  <a name="vfc"></a> VerboseForegroundColor
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie la couleur de premier plan pour le texte de commentaire affiché dans le volet de la console. Il s’agit d’un objet **System.Windows.Media.Color**.

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor =”yellow”
```

###  <a name="wbc"></a> WarningBackgroundColor
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie la couleur d’arrière-plan pour le texte d’avertissement affiché dans le volet de la console. Il s’agit d’un objet **System.Windows.Media.Color**.

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

###  <a name="wfc"></a> WarningForegroundColor
  Prise en charge dans Windows PowerShell ISE 2.0 et versions ultérieures.

 Spécifie la couleur de premier plan pour le texte d’avertissement affiché dans le volet de sortie. Il s’agit d’un objet **System.Windows.Media.Color**.

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor =”yellow”
```

###  <a name="xtc"></a> XmlTokenColors
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie un objet dictionnaire qui contient les paires nom\/valeur des types et couleurs des jetons pour le contenu XML qui s’affiche dans Windows PowerShell ISE. Les couleurs des jetons peuvent être définies pour les éléments suivants : Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable. Consultez également [RestoreDefaultXmlTokenColors()](#rdxtc).

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

###  <a name="z"></a> Zoom
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Spécifie la taille relative du texte dans les volets de la console et de script. La valeur par défaut est 100. Utilisez des valeurs plus basses pour réduire la taille du texte affiché dans Windows PowerShell ISE ou des valeurs plus élevées pour augmenter la taille du texte affiché. La valeur est un nombre entier compris entre 20 et 400.

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## Voir aussi
 [Modèle objet de script Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
 [Référence de modèle objet Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md)



<!--HONumber=May16_HO2-->


