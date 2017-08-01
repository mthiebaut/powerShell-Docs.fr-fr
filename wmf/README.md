---
title: Windows Management Framework (WMF)
ms.date: 2016-05-16
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: eacd33d2a0a92977a3990132e23eef9871a7f0dc
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: fr-FR
---
# <a name="windows-management-framework"></a><span data-ttu-id="d99fc-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="d99fc-103">Windows Management Framework</span></span>

<span data-ttu-id="d99fc-104">Windows Management Framework (WMF) est le mécanisme de remise qui fournit une interface de gestion cohérente sur les différentes versions de Windows et Windows Server.</span><span class="sxs-lookup"><span data-stu-id="d99fc-104">Windows Management Framework (WMF) is the delivery mechanism that provides a consistent management interface across the various flavors of Windows and Windows Server.</span></span>
<span data-ttu-id="d99fc-105">Quand WMF est installé, les clients peuvent interagir de manière transparente entre des combinaisons de systèmes d’exploitation dans leur environnement.</span><span class="sxs-lookup"><span data-stu-id="d99fc-105">With the installation of WMF, customers get a seamless way to interoperate between mixes of OSes in their environment.</span></span>
<span data-ttu-id="d99fc-106">WMF rend les mises à jour des fonctionnalités de gestion, dans une version donnée de Windows et Windows Server, disponibles pour installation sur des versions inférieures (en général, deux versions inférieures) de Windows et Windows Server.</span><span class="sxs-lookup"><span data-stu-id="d99fc-106">WMF makes the updates to management functionality, in a given release of Windows and Windows Server, available for installation on lower versions (typically, 2 lower versions) of Windows and Windows Server.</span></span>

<span data-ttu-id="d99fc-107">L’installation de WMF ajoute ou met à jour les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="d99fc-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="d99fc-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d99fc-108">Windows PowerShell</span></span>
- <span data-ttu-id="d99fc-109">Configuration de l’état souhaité de Windows PowerShell (DSC)</span><span class="sxs-lookup"><span data-stu-id="d99fc-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="d99fc-110">Windows PowerShell Integrated Script Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="d99fc-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="d99fc-111">Windows Remote Management (WinRM)</span><span class="sxs-lookup"><span data-stu-id="d99fc-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="d99fc-112">Infrastructure de gestion Windows (WMI, Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="d99fc-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="d99fc-113">Windows PowerShell Web Services (Extension ISS Management OData)</span><span class="sxs-lookup"><span data-stu-id="d99fc-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="d99fc-114">Journalisation de l’inventaire logiciel</span><span class="sxs-lookup"><span data-stu-id="d99fc-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="d99fc-115">Fournisseur CIM de Gestionnaire de serveur</span><span class="sxs-lookup"><span data-stu-id="d99fc-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="d99fc-116">Notes de publication de WMF</span><span class="sxs-lookup"><span data-stu-id="d99fc-116">WMF Release Notes</span></span>
<span data-ttu-id="d99fc-117">Pour en savoir plus sur les diverses améliorations apportées à PowerShell et d’autres composants d’une version donnée de WMF, consultez les liens ci-dessous pour consulter les notes de publication :</span><span class="sxs-lookup"><span data-stu-id="d99fc-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>


- [<span data-ttu-id="d99fc-118">WMF 5.1 (préversion)</span><span class="sxs-lookup"><span data-stu-id="d99fc-118">WMF 5.1 (Preview)</span></span>](5.1/release-notes.md)
- [<span data-ttu-id="d99fc-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="d99fc-119">WMF 5.0</span></span>](5.0/releasenotes.md)


## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="d99fc-120">Disponibilité de WMF sur les systèmes d’exploitation Windows</span><span class="sxs-lookup"><span data-stu-id="d99fc-120">WMF Availability Across Windows Operating Systems</span></span>

><span data-ttu-id="d99fc-121">TODO : Ajouter des liens vers des DLC WMF spécifiques sur l’en-tête de colonne</span><span class="sxs-lookup"><span data-stu-id="d99fc-121">TODO: Add links to specific WMF DLC on the column header</span></span>

| <span data-ttu-id="d99fc-122">Version du système d'exploitation</span><span class="sxs-lookup"><span data-stu-id="d99fc-122">Operating System Version</span></span> | [<span data-ttu-id="d99fc-123">WMF 5.1 Preview*</span><span class="sxs-lookup"><span data-stu-id="d99fc-123">WMF 5.1 Preview*</span></span>]() | [<span data-ttu-id="d99fc-124">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="d99fc-124">WMF 5.0</span></span>]() | [<span data-ttu-id="d99fc-125">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="d99fc-125">WMF 4.0</span></span>]() |  [<span data-ttu-id="d99fc-126">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="d99fc-126">WMF 3.0</span></span>]() | [<span data-ttu-id="d99fc-127">WMF (2.0)</span><span class="sxs-lookup"><span data-stu-id="d99fc-127">WMF (2.0)</span></span>]() |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| <span data-ttu-id="d99fc-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="d99fc-128">Windows Server 2016</span></span> | <span data-ttu-id="d99fc-129">Fourni par défaut*</span><span class="sxs-lookup"><span data-stu-id="d99fc-129">Ships in-box*</span></span> | <span data-ttu-id="d99fc-130">Fourni par défaut*</span><span class="sxs-lookup"><span data-stu-id="d99fc-130">Ships in-box*</span></span> |  |  |  |
| <span data-ttu-id="d99fc-131">Windows 10</span><span class="sxs-lookup"><span data-stu-id="d99fc-131">Windows 10</span></span> | <span data-ttu-id="d99fc-132">Fourni par défaut*</span><span class="sxs-lookup"><span data-stu-id="d99fc-132">Ships in-box*</span></span> | <span data-ttu-id="d99fc-133">Fourni par défaut*</span><span class="sxs-lookup"><span data-stu-id="d99fc-133">Ships in-box*</span></span>  | | | |  
| <span data-ttu-id="d99fc-134">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d99fc-134">Windows Server 2012 R2</span></span>| <span data-ttu-id="d99fc-135">??</span><span class="sxs-lookup"><span data-stu-id="d99fc-135">??</span></span> | <span data-ttu-id="d99fc-136">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-136">Yes</span></span> | <span data-ttu-id="d99fc-137">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="d99fc-137">Ships in-box</span></span> |  |  |
| <span data-ttu-id="d99fc-138">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d99fc-138">Windows 8.1</span></span> | <span data-ttu-id="d99fc-139">??</span><span class="sxs-lookup"><span data-stu-id="d99fc-139">??</span></span> | <span data-ttu-id="d99fc-140">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-140">Yes</span></span> |  <span data-ttu-id="d99fc-141">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="d99fc-141">Ships in-box</span></span> |  |  |
| <span data-ttu-id="d99fc-142">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d99fc-142">Windows Server 2012</span></span> | <span data-ttu-id="d99fc-143">??</span><span class="sxs-lookup"><span data-stu-id="d99fc-143">??</span></span> | <span data-ttu-id="d99fc-144">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-144">Yes</span></span> | <span data-ttu-id="d99fc-145">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-145">Yes</span></span> |  <span data-ttu-id="d99fc-146">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="d99fc-146">Ships in-box</span></span> | |
| <span data-ttu-id="d99fc-147">Windows 8</span><span class="sxs-lookup"><span data-stu-id="d99fc-147">Windows 8</span></span> |  |  |  | <span data-ttu-id="d99fc-148">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="d99fc-148">Ships in-box</span></span> | |
| <span data-ttu-id="d99fc-149">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d99fc-149">Windows Server 2008 R2 SP1</span></span> | <span data-ttu-id="d99fc-150">??</span><span class="sxs-lookup"><span data-stu-id="d99fc-150">??</span></span> | <span data-ttu-id="d99fc-151">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-151">Yes</span></span> | <span data-ttu-id="d99fc-152">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-152">Yes</span></span> |  <span data-ttu-id="d99fc-153">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-153">Yes</span></span>| <span data-ttu-id="d99fc-154">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="d99fc-154">Ships in-box</span></span> |
| <span data-ttu-id="d99fc-155">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d99fc-155">Windows 7 SP1</span></span>  | <span data-ttu-id="d99fc-156">??</span><span class="sxs-lookup"><span data-stu-id="d99fc-156">??</span></span> | <span data-ttu-id="d99fc-157">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-157">Yes</span></span> | <span data-ttu-id="d99fc-158">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-158">Yes</span></span> | <span data-ttu-id="d99fc-159">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-159">Yes</span></span> | <span data-ttu-id="d99fc-160">Fourni par défaut</span><span class="sxs-lookup"><span data-stu-id="d99fc-160">Ships in-box</span></span> |
| <span data-ttu-id="d99fc-161">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="d99fc-161">Windows Server 2008 SP2</span></span> | | | | <span data-ttu-id="d99fc-162">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-162">Yes</span></span> | <span data-ttu-id="d99fc-163">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-163">Yes</span></span> |
| <span data-ttu-id="d99fc-164">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="d99fc-164">Windows Vista</span></span> | | | | | <span data-ttu-id="d99fc-165">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-165">Yes</span></span> |
| <span data-ttu-id="d99fc-166">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="d99fc-166">Windows Server 2003</span></span>| | | |  | <span data-ttu-id="d99fc-167">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-167">Yes</span></span> |
| <span data-ttu-id="d99fc-168">Windows XP</span><span class="sxs-lookup"><span data-stu-id="d99fc-168">Windows XP</span></span> | | | |  | <span data-ttu-id="d99fc-169">Oui</span><span class="sxs-lookup"><span data-stu-id="d99fc-169">Yes</span></span> |

><span data-ttu-id="d99fc-170">TODO : Expliquer * dans le tableau ci-dessus</span><span class="sxs-lookup"><span data-stu-id="d99fc-170">TODO: Explain * in the above table</span></span>
