---
title: Objet ISEAddOnTool
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
---
# Objet ISEAddOnTool
  Un objet **ISEAddonTool** représente un outil complémentaire installé qui apporte des fonctionnalités supplémentaires à Windows PowerShell ISE. L’outil **Commandes** en est un exemple. Vous pouvez l’afficher en cliquant sur **Affichage**, puis sur **Afficher le composant additionnel de commande**. Vous pouvez ensuite utiliser cet outil par le biais des différents objets **ISEAddOnTool** disponibles.

 Chaque outil complémentaire peut être associé au volet vertical ou horizontal. Le volet vertical est ancré sur le bord droit de Windows PowerShell ISE. Le volet horizontal est ancré sur le bord inférieur.

 Chaque onglet PowerShell dans Windows PowerShell ISE peut avoir son propre ensemble d’outils complémentaires installés. Consultez [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md) et [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md) pour accéder à la collection d’outils disponibles pour l’onglet actuellement sélectionné ou les propriétés communes à tous les objets **PowerShellTab** fournis dans l’objet collection [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md).

## Méthodes
 Il n’existe pas de méthode Windows PowerShell ISE spécifique pour les objets de cette classe.

## Propriétés

###  <a name="Control"></a> Control
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 La propriété **Control** fournit un accès en lecture à de nombreux détails de l’outil complémentaire Commandes.

```
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher

```

###  <a name="IsVisible"></a> IsVisible
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Propriété booléenne qui indique si l’outil complémentaire est actuellement visible dans le volet associé. S’il est visible, vous pouvez définir la propriété **IsVisible** à la valeur **$false** pour masquer l’outil, ou définir la propriété **IsVisible** à la valeur **$true** pour afficher un outil complémentaire dans l’onglet PowerShell correspondant. Notez qu’un outil complémentaire masqué n’est plus accessible via l’objet **CurrentVisibleHorizontalTool** ou **CurrentVisibleVerticalTool**, et qu’il ne peut donc pas être affiché en définissant cette propriété sur cet objet.

```
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible=$true

```

###  <a name="name"></a> Nom
  Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

 Propriété en lecture seule qui obtient le nom de l’outil complémentaire.

```
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.name
Commands

```

## Voir aussi
 [Objet ISEAddOnToolCollection](The-ISEAddOnToolCollection-Object.md)
 [Modèle objet de script Windows PowerShell ISE](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
 [Référence de modèle objet Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md)
 [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)


<!--HONumber=May16_HO2-->


