---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
title: exemple de modèle d’un problème ou limitation connu
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="6f930-103">Remarque : fournir un titre descriptif proposé et une brève description</span><span class="sxs-lookup"><span data-stu-id="6f930-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="6f930-104">Exemples : erreurs ExecutionPolicy erronées</span><span class="sxs-lookup"><span data-stu-id="6f930-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="6f930-105">Sous Windows 7, l’utilisation de modules PowerShell et de ressources DSC peut générer des erreurs liées à ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="6f930-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="6f930-106">Solution</span><span class="sxs-lookup"><span data-stu-id="6f930-106">Resolution</span></span>

<span data-ttu-id="6f930-107">Pour résoudre le problème, affectez la valeur **RemoteSigned** à **ExecutionPolicy** en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :</span><span class="sxs-lookup"><span data-stu-id="6f930-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```