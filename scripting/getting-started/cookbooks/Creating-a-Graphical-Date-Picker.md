---
title: "Création d'un sélecteur de dates graphique"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: f359254900dce0ef0a28af3e16b8ef4095e85309

---

# Création d'un sélecteur de dates graphique
Dans Windows PowerShell 3.0 et versions ultérieures, vous pouvez créer un formulaire avec un contrôle graphique de type calendrier qui permet aux utilisateurs de sélectionner un jour du mois.

## Créer un contrôle sélecteur de dates graphique
Copiez le code suivant, puis collez-le dans Windows PowerShell ISE. Ensuite, enregistrez-le en tant que script Windows PowerShell (.ps1).

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form 

$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"

$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar) 

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $True

$result = $form.ShowDialog() 

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

Le script commence par charger deux classes .NET Framework : **System.Drawing** et **System.Windows.Forms**. Démarrez ensuite une nouvelle instance de la classe .NET Framework **Windows.Forms.Form**. Celle-ci fournit une fenêtre ou un formulaire vide où vous pouvez ajouter des contrôles.

```
$form = New-Object Windows.Forms.Form
```

Après avoir créé une instance de la classe Form, affectez des valeurs à trois propriétés de cette classe.

-   **Text.** Il s'agit du titre de la fenêtre.

-   **Size.** Il s'agit de la taille du formulaire en pixels. Le script précédent crée un formulaire de 243 pixels de largeur par 230 pixels de hauteur.

-   **StartingPosition.** Cette propriété facultative a la valeur **CenterScreen** dans le script précédent. Si vous n'ajoutez pas cette propriété, Windows sélectionne un emplacement quand le formulaire est ouvert. Si vous affectez à **StartingPosition** la valeur **CenterScreen**, le formulaire s’affiche automatiquement au milieu de l’écran à chaque chargement.

```
$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"
```

Ensuite, créez et ajoutez un contrôle calendrier dans votre formulaire. Dans cet exemple, le jour actuel n'est ni mis en surbrillance ni encerclé. Les utilisateurs peuvent sélectionner un seul jour à la fois dans le calendrier.

```
$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Ensuite, créez un bouton **OK** dans votre formulaire. Spécifiez la taille et le comportement du bouton **OK**. Dans cet exemple, le bouton se trouve à 165 pixels du bord supérieur du formulaire et à 38 pixels du bord gauche. Le bouton mesure 23 pixels de haut et 75 pixels de long. Le script utilise des types Windows Forms prédéfinis pour déterminer le comportement du bouton.

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

De la même façon, créez un bouton **Annuler**. Le bouton **Annuler** se trouve à 165 pixels du bord supérieur de la fenêtre, mais à 113 pixels du bord gauche.

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Affectez à la propriété **Topmost** la valeur **$True** pour forcer la fenêtre à s’ouvrir au-dessus des autres fenêtres et boîtes de dialogue.

```
$form.Topmost = $True
```

Ajoutez la ligne de code suivante pour afficher le formulaire dans Windows.

```
$result = $form.ShowDialog()
```

Enfin, le code à l’intérieur du bloc **If** indique à Windows comment traiter le formulaire quand un utilisateur sélectionne un jour dans le calendrier, puis clique sur le bouton **OK** ou appuie sur la touche **Entrée**. Windows PowerShell affiche la date sélectionnée aux utilisateurs.

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## Voir aussi
[Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?](http://go.microsoft.com/fwlink/?LinkId=506644)
[GitHub: Dave Wyatt’s WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
[Astuce Windows PowerShell de la semaine : création d’un sélecteur de dates graphique](http://technet.microsoft.com/library/ff730942.aspx)




<!--HONumber=Jun16_HO4-->


