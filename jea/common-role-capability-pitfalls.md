---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,jea
ms.date: 2016-06-22
title: "pièges liés aux capacités de rôle"
ms.technology: powershell
ms.openlocfilehash: 8e928ec07ef98b2ec8186a27d3aefa1450a3a424
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: fr-FR
---
### <a name="common-role-capability-pitfalls"></a><span data-ttu-id="dd6f9-103">Pièges liés aux capacités de rôle</span><span class="sxs-lookup"><span data-stu-id="dd6f9-103">Common Role Capability Pitfalls</span></span>
<span data-ttu-id="dd6f9-104">Vous pouvez tomber dans quelques pièges courants en suivant vous-même ce processus.</span><span class="sxs-lookup"><span data-stu-id="dd6f9-104">You may run into a few common pitfalls if you go through this process yourself.</span></span>
<span data-ttu-id="dd6f9-105">Voici un guide rapide qui explique comment identifier et corriger ces problèmes lors de la modification ou la création d’un point de terminaison :</span><span class="sxs-lookup"><span data-stu-id="dd6f9-105">Here is a quick guide explaining how to identify and remediate these issues when modifying or creating a new endpoint:</span></span>

#### <a name="functions-vs-cmdlets"></a><span data-ttu-id="dd6f9-106">Fonctions et Applets de commande</span><span class="sxs-lookup"><span data-stu-id="dd6f9-106">Functions vs. Cmdlets</span></span>
<span data-ttu-id="dd6f9-107">Les commandes PowerShell écrites dans PowerShell sont des fonctions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd6f9-107">PowerShell commands written in PowerShell are PowerShell functions.</span></span>
<span data-ttu-id="dd6f9-108">Les commandes PowerShell écrites comme des classes .NET spécialisées sont des applets de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd6f9-108">PowerShell commands written as specialized .NET classes are PowerShell cmdlets.</span></span>
<span data-ttu-id="dd6f9-109">Vous pouvez déterminer le type de commande en exécutant `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="dd6f9-109">You can check the command type by running `Get-Command`.</span></span>

#### <a name="visibleproviders"></a><span data-ttu-id="dd6f9-110">VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="dd6f9-110">VisibleProviders</span></span>
<span data-ttu-id="dd6f9-111">Vous devez exposer tous les fournisseurs dont vos commandes ont besoin.</span><span class="sxs-lookup"><span data-stu-id="dd6f9-111">You will need to expose any providers your commands need.</span></span>
<span data-ttu-id="dd6f9-112">Le plus courant est le fournisseur FileSystem, mais vous aurez peut-être besoin d’en exposer d’autres comme le fournisseur Registry.</span><span class="sxs-lookup"><span data-stu-id="dd6f9-112">The most common is the FileSystem provider, but you may also need to expose others, like the Registry provider.</span></span>
<span data-ttu-id="dd6f9-113">Pour une présentation des fournisseurs, consultez le [billet de blog Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span><span class="sxs-lookup"><span data-stu-id="dd6f9-113">For an introduction to providers, check out this [Hey, Scripting Guy blog post](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span></span>
<span data-ttu-id="dd6f9-114">Soyez prudent quand vous exposez des fournisseurs. Souvent, il est préférable de définir votre propre fonction qui utilise les fournisseurs sous-jacents plutôt que d’exposer directement le fournisseur dans une session JEA.</span><span class="sxs-lookup"><span data-stu-id="dd6f9-114">Be careful when exposing providers -- often, it is better to define your own function that works with the underlying providers than to directly expose the provider in a JEA session.</span></span>
<span data-ttu-id="dd6f9-115">Ainsi, vous pouvez quand même autoriser des utilisateurs à travailler avec des fichiers, des clés de Registre, etc., tout en continuant à déterminer **quels** fichiers et clés de Registre ils peuvent utiliser à l’aide d’une logique de validation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="dd6f9-115">This way, you can still allow users to work with files, registry keys, etc. but retain control over **which** files and registry keys they can work with using custom validation logic.</span></span>

