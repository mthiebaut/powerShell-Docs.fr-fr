---
title: Utilisation d’imprimantes
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
---
# Utilisation d’imprimantes
Vous pouvez utiliser Windows PowerShell pour gérer des imprimantes à l’aide de WMI et de l’objet COM WScript.Network de WSH. Nous allons utiliser une combinaison de ces deux outils pour effectuer des tâches spécifiques.

### Affichage de la liste des connexions d’imprimante
La manière la plus simple de répertorier les imprimantes installées sur un ordinateur consiste à utiliser la classe WMI **Win32_Printer** :

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

Vous pouvez également répertorier les imprimantes à l’aide de l’objet COM **WScript.Network** qui est généralement utilisé dans des scripts WSH :

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Cette commande retournant une simple collection de chaînes correspondant à des noms de port et d’imprimante sans étiquettes distinctives, elle n’est pas facile à interpréter.

### Ajout d’une imprimante réseau
Pour ajouter une nouvelle imprimante réseau, utilisez l’objet COM **WScript.Network** :

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### Définition d’une imprimante par défaut
Pour utiliser WMI afin de définir l’imprimante par défaut, recherchez l’imprimante dans la collection **Win32_Printer**, puis appelez la méthode **SetDefaultPrinter** :

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

L’objet COM **WScript.Network** est un peu plus simple à utiliser, car il dispose d’une méthode **SetDefaultPrinter** qui accepte uniquement le nom de l’imprimante en tant qu’argument :

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### Suppression d’une connexion d’imprimante
Pour supprimer une connexion d’imprimante, utilisez la méthode **WScript.Network RemovePrinterConnection**:

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```



<!--HONumber=Apr16_HO1-->


