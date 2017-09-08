---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Hiérarchie du modèle objet ISE"
ms.assetid: bc3300e4-9c17-4f00-a621-c8867126e3b3
ms.openlocfilehash: b6e251eac7db56896490362392e0a1c4c10a8d4a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2017
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="c44df-103">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="c44df-103">The ISE Object Model Hierarchy</span></span>
  <span data-ttu-id="c44df-104">Cette rubrique présente la hiérarchie des objets qui font partie de l’environnement d’écriture de scripts intégré de Windows PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="c44df-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="c44df-105">Windows PowerShell ISE est inclus dans Windows PowerShell 3.0 et Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="c44df-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span> <span data-ttu-id="c44df-106">Cliquez sur un objet pour accéder à la documentation de référence de la classe qui définit l’objet.</span><span class="sxs-lookup"><span data-stu-id="c44df-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

##  <a name="psise-object"></a><span data-ttu-id="c44df-107">**$psISE, objet**</span><span class="sxs-lookup"><span data-stu-id="c44df-107">**$psISE Object**</span></span>
 <span data-ttu-id="c44df-108">L’objet **$psISE** est l’[objet racine](The-ObjectModelRoot-Object.md) de la hiérarchie d’objets Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c44df-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="c44df-109">Cet objet de premier niveau fournit les objets de script suivants :</span><span class="sxs-lookup"><span data-stu-id="c44df-109">Located at the top level, it makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="c44df-110">**[$psISE.CurrentFile]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-110">**[$psISE.CurrentFile]()**</span></span>

-   <span data-ttu-id="c44df-111">**[$psISE.CurrentPowerShellTab]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-111">**[$psISE.CurrentPowerShellTab]()**</span></span>

-   <span data-ttu-id="c44df-112">**[$psISE.CurrentVisibleHorizontalTool]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-112">**[$psISE.CurrentVisibleHorizontalTool]()**</span></span>

-   <span data-ttu-id="c44df-113">**[$psISE.CurrentVisibleVerticalTool]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-113">**[$psISE.CurrentVisibleVerticalTool]()**</span></span>

-   <span data-ttu-id="c44df-114">**[$psISE.Options]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-114">**[$psISE.Options]()**</span></span>

-   <span data-ttu-id="c44df-115">**[$psISE.PowerShellTabs]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-115">**[$psISE.PowerShellTabs]()**</span></span>

##  <a name="psisecurrentfilethe-isefile-objectmd"></a><span data-ttu-id="c44df-116">**[$psISE.CurrentFile](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-116">**[$psISE.CurrentFile](The-ISEFile-Object.md)**</span></span>
 <span data-ttu-id="c44df-117">L’objet **$psISE.CurrentFile** est une instance de la classe [ISEFile](The-ISEFile-Object.md) et fournit les objets de script suivants :</span><span class="sxs-lookup"><span data-stu-id="c44df-117">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="c44df-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**</span></span>

-   <span data-ttu-id="c44df-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**  Cet objet est une instance de la classe [ISEEditor](The-ISEEditor-Object.md) et fournit les objets de script suivants :</span><span class="sxs-lookup"><span data-stu-id="c44df-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="c44df-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="c44df-121">**[CaretColumn](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-121">**[CaretColumn](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="c44df-122">**[CaretLine](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-122">**[CaretLine](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="c44df-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="c44df-124">**[LineCount](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-124">**[LineCount](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="c44df-125">**[SelectedText](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-125">**[SelectedText](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="c44df-126">**[Text](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-126">**[Text](The-ISEEditor-Object.md)**</span></span>

-   <span data-ttu-id="c44df-127">**[EncodingThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-127">**[EncodingThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-128">**[FullPathThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-128">**[FullPathThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-129">**[IsSavedThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-129">**[IsSavedThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-130">**[IsUntitledThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-130">**[IsUntitledThe-ISEFile-Object.md]()**</span></span>

##  <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a><span data-ttu-id="c44df-131">**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-131">**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span></span>
 <span data-ttu-id="c44df-132">L’objet **$psISE.CurrentPowerShellTab** est une instance de la classe [PowerShellTab](The-PowerShellTab-Object.md) et fournit les objets de script suivants :</span><span class="sxs-lookup"><span data-stu-id="c44df-132">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="c44df-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**  Cet objet est une instance de la classe [ISEMenuItem](The-ISEMenuItem-Object.md) et fournit les objets de script suivants :</span><span class="sxs-lookup"><span data-stu-id="c44df-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**  This object is an instance of the [ISEMenuItem](The-ISEMenuItem-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="c44df-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="c44df-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="c44df-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="c44df-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span></span>

-   <span data-ttu-id="c44df-138">**[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-138">**[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**  Cet objet est une instance de la classe [ISEEditor](The-ISEEditor-Object.md) et fournit les objets de script suivants :</span><span class="sxs-lookup"><span data-stu-id="c44df-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="c44df-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="c44df-141">**[CaretColumnThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-141">**[CaretColumnThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="c44df-142">**[CaretLineThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-142">**[CaretLineThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="c44df-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="c44df-144">**[LineCountThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-144">**[LineCountThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="c44df-145">**[SelectedTextThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-145">**[SelectedTextThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="c44df-146">**[TextThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-146">**[TextThe-ISEEditor-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-147">**[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-147">**[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-148">**[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-148">**[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span></span>

-   <span data-ttu-id="c44df-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="c44df-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-152">**[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-152">**[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-153">**[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-153">**[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span></span>

-   <span data-ttu-id="c44df-155">**[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-155">**[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="c44df-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="c44df-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

##  <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="c44df-160">**$psISE.CurrentVisibleHorizontalTool**</span><span class="sxs-lookup"><span data-stu-id="c44df-160">**$psISE.CurrentVisibleHorizontalTool**</span></span>
 <span data-ttu-id="c44df-161">L’objet **$psISE.CurrentVisibleHorizontalTool** est une instance de la classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="c44df-161">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="c44df-162">Il représente l’outil complémentaire installé qui est actuellement ancré sur le bord supérieur de la fenêtre Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c44df-162">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="c44df-163">Cet objet fournit les objets de script suivants :</span><span class="sxs-lookup"><span data-stu-id="c44df-163">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="c44df-164">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-164">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-166">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-166">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span></span>

##  <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="c44df-167">**$psISE.CurrentVisibleVerticalTool**</span><span class="sxs-lookup"><span data-stu-id="c44df-167">**$psISE.CurrentVisibleVerticalTool**</span></span>
 <span data-ttu-id="c44df-168">L’objet **$psISE.CurrentVisibleHorizontalTool** est une instance de la classe [ISEAddOnTool](The-ISEAddOnTool-Object.md).</span><span class="sxs-lookup"><span data-stu-id="c44df-168">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="c44df-169">Il représente l’outil complémentaire installé qui est actuellement ancré sur le bord droit de la fenêtre Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c44df-169">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="c44df-170">Cet objet fournit les objets de script suivants :</span><span class="sxs-lookup"><span data-stu-id="c44df-170">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="c44df-171">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-171">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-173">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-173">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span></span>

##  <a name="psiseoptions"></a><span data-ttu-id="c44df-174">**$psISE.Options**</span><span class="sxs-lookup"><span data-stu-id="c44df-174">**$psISE.Options**</span></span>
 <span data-ttu-id="c44df-175">L’objet **$psISE.Options** fournit les objets de script suivants :</span><span class="sxs-lookup"><span data-stu-id="c44df-175">The **$psISE.Options** object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="c44df-176">**[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-176">**[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-177">**[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-177">**[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-178">**[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-178">**[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-179">**[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-179">**[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-180">**[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-180">**[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-181">**[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-181">**[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-182">**[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-182">**[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span></span>

-   <span data-ttu-id="c44df-184">**[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-184">**[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-185">**[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-185">**[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-186">**[$psISE.Options.FontNameThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-186">**[$psISE.Options.FontNameThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-187">**[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-187">**[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-188">**[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-188">**[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-189">**[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-189">**[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-190">**[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-190">**[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-191">**[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-191">**[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-192">**[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-192">**[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-193">**[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-193">**[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-194">**[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-194">**[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-195">**[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-195">**[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-196">**[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-196">**[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-197">**[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-197">**[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-198">**[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-198">**[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-199">**[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-199">**[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-200">**[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-200">**[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-201">**[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-201">**[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-204">**[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-204">**[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-205">**[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-205">**[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-206">**[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-206">**[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-207">**[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-207">**[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-208">**[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-208">**[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-209">**[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-209">**[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="c44df-210">**[$psISE.Options.ZoomThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="c44df-210">**[$psISE.Options.ZoomThe-ISEOptions-Object.md]()**</span></span>

##  <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a><span data-ttu-id="c44df-211">**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="c44df-211">**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span></span>
 <span data-ttu-id="c44df-212">L’objet **$psISE.PowerShellTabs** est une instance de la classe [PowerShellTabCollection](The-PowerShellTabCollection-Object.md).</span><span class="sxs-lookup"><span data-stu-id="c44df-212">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="c44df-213">Cet objet est une collection de tous les onglets PowerShell ouverts qui représentent les environnements d’exécution Windows PowerShell disponibles sur l’ordinateur local ou sur les ordinateurs distants connectés.</span><span class="sxs-lookup"><span data-stu-id="c44df-213">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="c44df-214">Chaque membre de la collection est une instance de la classe [PowerShellTab](The-PowerShellTab-Object.md).</span><span class="sxs-lookup"><span data-stu-id="c44df-214">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="c44df-215">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c44df-215">See Also</span></span>
- [<span data-ttu-id="c44df-216">Modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c44df-216">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c44df-217">Informations de référence sur le modèle objet Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c44df-217">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

