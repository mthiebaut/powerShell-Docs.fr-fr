---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Comment écrire et exécuter des scripts dans Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 4b8a9c0c3a710f3b3b9b6077c3c84e174a141db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Comment écrire et exécuter des scripts dans Windows PowerShell ISE

Cette rubrique décrit comment créer, modifier, exécuter et enregistrer des scripts dans le volet Script.

## <a name="how-to-create-and-run-scripts"></a>Comment créer et exécuter des scripts

Vous pouvez ouvrir et modifier des fichiers Windows PowerShell dans le volet Script. Les types de fichiers spécifiques intéressants dans Windows PowerShell sont les fichiers de script (.ps1), les fichiers de données de script (.psd1) et les fichiers de module de script (.psm1). Ces types de fichiers font l’objet d’une coloration de la syntaxe dans l’éditeur du volet Script. D’autres types de fichiers courants que vous pouvez ouvrir dans le volet Script sont les fichiers de configuration (.ps1xml), les fichiers XML et les fichiers texte.

> [!NOTE]
> La stratégie d’exécution de Windows PowerShell détermine si vous pouvez exécuter des scripts et charger des fichiers de configuration et des profils Windows PowerShell. La stratégie d’exécution par défaut, restreinte, empêche l’exécution de tous les scripts et le chargement de profils. Pour savoir comment modifier la stratégie d’exécution afin d’autoriser le chargement et l’utilisation de profils, voir [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) et [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).

### <a name="to-create-a-new-script-file"></a>Pour créer un fichier de script

Dans la barre d’outils, cliquez sur **Nouveau** ou, dans le menu **Fichier**, cliquez sur **Nouveau**. Le fichier créé s’affiche dans un nouvel onglet de fichier sous l’onglet PowerShell actif. N’oubliez pas que les onglets PowerShell sont visibles uniquement quand il y en a plusieurs. Par défaut, un fichier de script type (.ps1) est créé, mais il peut être enregistré avec un nouveau nom et une nouvelle extension. Plusieurs fichiers de script peuvent être créés sous le même onglet PowerShell.

### <a name="to-open-an-existing-script"></a>Pour ouvrir un script existant

Dans la barre d’outils, cliquez sur **Ouvrir** ou, dans le menu **Fichier**, cliquez sur **Ouvrir**. Dans la boîte de dialogue **Ouvrir**, sélectionnez le fichier à ouvrir. Le fichier ouvert s’affiche dans un nouvel onglet.

### <a name="to-close-a-script-tab"></a>Pour fermer un onglet de script

Cliquez sur l’onglet de script du script que vous voulez fermer, puis effectuez l’une des opérations suivantes :

1. Cliquez sur l’icône **Fermer** (X) sous l’onglet de script.

2. Dans le menu **Fichier**, cliquez sur **Fermer**.

Si le fichier a été modifié depuis son dernier enregistrement, vous êtes invité à l’enregistrer ou à l’ignorer.

### <a name="to-display-the-file-path"></a>Pour afficher le chemin d’accès du fichier

Sous l’onglet Fichier, pointez sur le nom de fichier. Le chemin d’accès complet au fichier de script s’affiche dans une info-bulle.

### <a name="to-run-a-script"></a>Pour exécuter un script

Dans la barre d’outils, cliquez sur **Exécuter le Script** ou, dans le menu **Fichier**, cliquez sur **Exécuter**.

### <a name="to-run-a-portion-of-a-script"></a>Pour exécuter une partie d’un script

1. Dans le volet Script, sélectionnez une partie d’un script.

2. Dans le menu **Fichier**, cliquez sur **Exécuter la sélection** ou, dans la barre d’outils, cliquez sur **Exécuter la sélection**.

### <a name="to-stop-a-running-script"></a>Pour arrêter un script en cours d’exécution

Dans la barre d’outils, cliquez sur **Arrêter l’opération**, puis appuyez sur Ctrl+Pause, ou, dans le menu **Fichier**, cliquez sur **Arrêter l’opération**. Appuyer sur **Ctrl+C** fonctionne également, sauf si du texte est sélectionné, auquel cas l’appui sur **Ctrl+C** mappe à la fonction de copie pour le texte sélectionné.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Comment écrire et modifier du texte dans le volet Script

Pour modifier le texte dans le volet Script, procédez comme suit. Vous pouvez copier, couper, coller, rechercher et remplacer du texte. Vous pouvez également annuler et rétablir la dernière action exécutée. Les raccourcis clavier pour exécuter ces actions sont les mêmes que ceux utilisés pour toutes les applications Windows.

### <a name="to-enter-text-in-the-script-pane"></a>Pour entrer du texte dans le volet Script

1. Déplacez le curseur vers le volet Script en cliquant n’importe où dans celui-ci, ou en cliquant sur **Atteindre le volet Script** dans le menu **Affichage**.

2. Créez un script. La coloration de la syntaxe et la saisie semi-automatique par le biais de la touche Tab enrichissent cette expérience dans Windows PowerShell ISE.

3. Pour plus d’informations sur l’utilisation de la fonctionnalité de saisie semi-automatique via la touche Tab pour faciliter la frappe, voir [Comment utiliser la saisie semi-automatique via la touche Tab dans le volet Script et le volet Console](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).

### <a name="to-find-text-in-the-script-pane"></a>Pour rechercher du texte dans le volet Script

1. Pour rechercher du texte n’importe où, appuyez sur **Ctrl+F** ou, dans le menu **Modifier**, cliquez sur **Rechercher dans le script**.

2. Pour rechercher du texte situé après le curseur, appuyez sur **F3** ou, dans le menu **Modifier**, cliquez sur **Rechercher suivant dans le script**.

3. Pour rechercher du texte devant le curseur, appuyez sur **Maj+F3** ou, dans le menu **Modifier**, cliquez sur **Rechercher précédent dans le script**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Pour rechercher et remplacer du texte dans le volet Script

Appuyez sur **CTRL+H** ou, dans le menu **Modifier**, cliquez sur **Remplacer dans le script**. Entrez le texte à rechercher et le texte à y substituer, puis appuyez sur **Entrée**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Pour accéder à une ligne particulière du texte dans le volet Script

1. Dans le volet Script, appuyez sur **Ctrl+G** ou, dans le menu **Modifier**, cliquez sur **Atteindre la ligne**.

2. Entrez un numéro de ligne.

### <a name="to-copy-text-in-the-script-pane"></a>Pour copier du texte dans le volet Script

1. Dans le volet Script, sélectionnez le texte à copier.

2. Appuyez sur **Ctrl+C** ou, dans la barre d’outils, cliquez sur l’icône **Copier**, ou encore, dans le menu **Modifier**, cliquez sur **Copier**.

### <a name="to-cut-text-in-the-script-pane"></a>Pour couper du texte dans le volet Script

1. Dans le volet Script, sélectionnez le texte à couper.

2. Appuyez sur **Ctrl+X** ou, dans la barre d’outils, cliquez sur l’icône **Couper**, ou encore, dans le menu **Modifier**, cliquez sur **Couper**.

### <a name="to-paste-text-into-the-script-pane"></a>Pour coller du texte dans le volet Script

Appuyez sur **Ctrl+V** ou, dans la barre d’outils, cliquez sur l’icône **Coller**, ou encore, dans le menu **Modifier**, cliquez sur **Coller**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Pour annuler une action dans le volet Script

Appuyez sur **Ctrl+Z** ou, dans la barre d’outils, cliquez sur l’icône **Annuler**, ou encore, dans le menu **Modifier**, cliquez sur **Annuler**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Pour rétablir une action dans le volet Script

Appuyez sur **Ctrl+Y** ou, dans la barre d’outils, cliquez sur l’icône **Rétablir**, ou encore, dans le menu **Modifier**, cliquez sur **Rétablir**.

## <a name="how-to-save-a-script"></a>Comment enregistrer un script

Pour enregistrer et nommer un script, procédez comme suit. Un astérisque apparaît en regard du nom de script pour marquer un fichier qui n’a pas été enregistré depuis sa modification. L’astérisque disparaît lors de l’enregistrement du fichier.

### <a name="to-save-a-script"></a>Pour enregistrer un script

Appuyez sur **Ctrl+S** ou, dans la barre d’outils, cliquez sur l’icône **Enregistrer**, ou encore, dans le menu **Fichier**, cliquez sur **Enregistrer**.

### <a name="to-save-and-name-a-script"></a>Pour enregistrer et nommer un script

1. Dans le menu **Fichier**, cliquez sur **Enregistrer sous**. La boîte de dialogue **Enregistrer sous** s’affiche.

2. Dans le champ **Nom de fichier**, entrez un nom pour le fichier.

3. Dans le champ **Type de fichier**, sélectionnez un type de fichier. Par exemple, dans la zone **Type de fichier**, sélectionnez « Scripts PowerShell (\* .ps1) ».

4. Cliquez sur **Enregistrer**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Pour enregistrer un script en encodage ASCII

Par défaut, Windows PowerShell ISE enregistre les nouveaux fichiers de script (.ps1), les fichiers de données de script (.psd1) et les fichiers de module de script (.psm1) au format Unicode (BigEndianUnicode). Pour enregistrer un script dans un autre encodage, comme ASCII (ANSI), utilisez les méthodes **Save** ou **SaveAs** sur l’objet [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile).

La commande suivante enregistre un nouveau script sous MyScript.ps1 avec un encodage ASCII.

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

La commande suivante remplace le fichier de script actuel par un fichier du même nom, mais avec un encodage ASCII.

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

La commande suivante obtient l’encodage du fichier actuel.

```powershell
$psISE.CurrentFile.encoding
```

Windows PowerShell ISE prend en charge les options d’encodage suivantes : ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 et Default. La valeur de l’option Default varie selon le système.

Windows PowerShell ISE ne modifie pas l’encodage des scripts qui ont été créés par d’autres éditeurs, même si vous utilisez les commandes Save ou Save As dans Windows PowerShell ISE.

## <a name="see-also"></a>Voir aussi

- [Exploration de Windows PowerShell ISE](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)