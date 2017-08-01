---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,jea
ms.date: 2016-06-22
title: introduction
ms.technology: powershell
ms.openlocfilehash: 71264d1001228249d9f2bb0f72473e9761170bf0
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: fr-FR
---
# <a name="introduction"></a><span data-ttu-id="4f4f8-103">Introduction</span><span class="sxs-lookup"><span data-stu-id="4f4f8-103">Introduction</span></span>

##  <a name="motivation"></a><span data-ttu-id="4f4f8-104">**Motivation**</span><span class="sxs-lookup"><span data-stu-id="4f4f8-104">**Motivation**</span></span>  
<span data-ttu-id="4f4f8-105">Quand vous accordez à une personne un accès privilégié à vos systèmes, vous étendez votre confiance à cette personne.</span><span class="sxs-lookup"><span data-stu-id="4f4f8-105">When you grant someone privileged access to your systems, you extend your trust boundary to that person.</span></span>
<span data-ttu-id="4f4f8-106">Ce n’est pas sans risque, car les administrateurs sont une surface d’attaque.</span><span class="sxs-lookup"><span data-stu-id="4f4f8-106">This is a risk -- administrators are an attack surface.</span></span>
<span data-ttu-id="4f4f8-107">Les attaques internes et les informations d’identification volées sont à la fois réelles et courantes.</span><span class="sxs-lookup"><span data-stu-id="4f4f8-107">Insider attacks and stolen credentials are both real and common.</span></span>

##  <a name="not-a-new-problem"></a><span data-ttu-id="4f4f8-108">**Le problème n’est pas nouveau**</span><span class="sxs-lookup"><span data-stu-id="4f4f8-108">**Not a new problem**</span></span>  
<span data-ttu-id="4f4f8-109">Vous connaissez probablement déjà le principe du privilège minimum et vous utilisez peut-être une forme de contrôle d’accès en fonction du rôle (RBAC) avec les applications qui le proposent.</span><span class="sxs-lookup"><span data-stu-id="4f4f8-109">You are probably very familiar with the principle of least privilege, and you might use some form of role-based access control (RBAC) with applications that provide it.</span></span>
<span data-ttu-id="4f4f8-110">Toutefois, l’efficacité et la facilité de gestion de ces solutions sont souvent limitées par leur large étendue et leur imprécision.</span><span class="sxs-lookup"><span data-stu-id="4f4f8-110">However, the effectiveness and manageability of these solutions are often limited by their broad scope and imprecision.</span></span>
<span data-ttu-id="4f4f8-111">De plus, il existe des lacunes dans la couverture RBAC.</span><span class="sxs-lookup"><span data-stu-id="4f4f8-111">Furthermore, there are gaps in RBAC coverage.</span></span>
<span data-ttu-id="4f4f8-112">Par exemple, dans Windows, un accès privilégié correspond largement à un commutateur binaire, ce qui vous oblige à accorder des autorisations inutiles lors de l’ajout d’utilisateurs au groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="4f4f8-112">For example, in Windows, privileged access is largely a binary switch, forcing you to give unnecessary permissions when adding users to the Administrators group.</span></span>

##  <a name="just-enough-administration-jea"></a><span data-ttu-id="4f4f8-113">**Just Enough Administration (JEA)**</span><span class="sxs-lookup"><span data-stu-id="4f4f8-113">**Just Enough Administration (JEA)**</span></span> 
<span data-ttu-id="4f4f8-114">Fournit une plateforme de contrôle d’accès en fonction du rôle (RBAC) par le biais de la communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f4f8-114">Provides a role-based access control (RBAC) platform through PowerShell Remoting.</span></span>
<span data-ttu-id="4f4f8-115">*Elle permet à des utilisateurs spécifiques d’effectuer des tâches administratives spécifiques sur des serveurs sans leur octroyer de droits d’administrateur.*</span><span class="sxs-lookup"><span data-stu-id="4f4f8-115">*It allows specific users to perform specific administrative tasks on servers without giving them administrator rights.*</span></span>
<span data-ttu-id="4f4f8-116">Cela vous permet de combler les lacunes de vos solutions RBAC existantes et de simplifier la gestion de ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="4f4f8-116">This allows you to fill in the gaps between your existing RBAC solutions, and simplifies management of those settings.</span></span>

