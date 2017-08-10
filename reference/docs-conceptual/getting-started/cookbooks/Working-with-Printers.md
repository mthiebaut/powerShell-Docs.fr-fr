---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Utilisation d’imprimantes"
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: c8b4d728c9fddd39e1aeb56d6f9b8ffffe4c7292
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2017
---
# <a name="working-with-printers"></a><span data-ttu-id="afb30-103">Utilisation d’imprimantes</span><span class="sxs-lookup"><span data-stu-id="afb30-103">Working with Printers</span></span>
<span data-ttu-id="afb30-104">Vous pouvez utiliser Windows PowerShell pour gérer des imprimantes à l’aide de WMI et de l’objet COM WScript.Network de WSH.</span><span class="sxs-lookup"><span data-stu-id="afb30-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="afb30-105">Nous allons utiliser une combinaison de ces deux outils pour effectuer des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="afb30-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="afb30-106">Affichage de la liste des connexions d’imprimante</span><span class="sxs-lookup"><span data-stu-id="afb30-106">Listing Printer Connections</span></span>
<span data-ttu-id="afb30-107">La manière la plus simple de répertorier les imprimantes installées sur un ordinateur consiste à utiliser la classe WMI **Win32_Printer** :</span><span class="sxs-lookup"><span data-stu-id="afb30-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="afb30-108">Vous pouvez également répertorier les imprimantes à l’aide de l’objet COM **WScript.Network** qui est généralement utilisé dans des scripts WSH :</span><span class="sxs-lookup"><span data-stu-id="afb30-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="afb30-109">Cette commande retournant une simple collection de chaînes correspondant à des noms de port et d’imprimante sans étiquettes distinctives, elle n’est pas facile à interpréter.</span><span class="sxs-lookup"><span data-stu-id="afb30-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="afb30-110">Ajout d’une imprimante réseau</span><span class="sxs-lookup"><span data-stu-id="afb30-110">Adding a Network Printer</span></span>
<span data-ttu-id="afb30-111">Pour ajouter une nouvelle imprimante réseau, utilisez l’objet COM **WScript.Network** :</span><span class="sxs-lookup"><span data-stu-id="afb30-111">To add a new network printer, use **WScript.Network**:</span></span>

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="afb30-112">Définition d’une imprimante par défaut</span><span class="sxs-lookup"><span data-stu-id="afb30-112">Setting a Default Printer</span></span>
<span data-ttu-id="afb30-113">Pour utiliser WMI afin de définir l’imprimante par défaut, recherchez l’imprimante dans la collection **Win32_Printer**, puis appelez la méthode **SetDefaultPrinter** :</span><span class="sxs-lookup"><span data-stu-id="afb30-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="afb30-114">L’objet COM **WScript.Network** est un peu plus simple à utiliser, car il dispose d’une méthode **SetDefaultPrinter** qui accepte uniquement le nom de l’imprimante en tant qu’argument :</span><span class="sxs-lookup"><span data-stu-id="afb30-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="afb30-115">Suppression d’une connexion d’imprimante</span><span class="sxs-lookup"><span data-stu-id="afb30-115">Removing a Printer Connection</span></span>
<span data-ttu-id="afb30-116">Pour supprimer une connexion d’imprimante, utilisez la méthode **WScript.Network RemovePrinterConnection**:</span><span class="sxs-lookup"><span data-stu-id="afb30-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```

