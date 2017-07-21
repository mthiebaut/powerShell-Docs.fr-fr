---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: "exemple de modèle d’un problème ou limitation connu"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="25aed-103">Remarque : fournir un titre descriptif proposé et une brève description</span><span class="sxs-lookup"><span data-stu-id="25aed-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="25aed-104">Exemples : erreurs ExecutionPolicy erronées</span><span class="sxs-lookup"><span data-stu-id="25aed-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="25aed-105">Sous Windows 7, l’utilisation de modules PowerShell et de ressources DSC peut générer des erreurs liées à ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="25aed-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="25aed-106">Solution</span><span class="sxs-lookup"><span data-stu-id="25aed-106">Resolution</span></span>

<span data-ttu-id="25aed-107">Pour résoudre le problème, affectez la valeur **RemoteSigned** à **ExecutionPolicy** en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :</span><span class="sxs-lookup"><span data-stu-id="25aed-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

