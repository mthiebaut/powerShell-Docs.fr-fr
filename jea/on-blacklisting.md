---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande,jea
ms.date: 2016-06-22
title: "à propos de l’inscription sur liste rouge"
ms.technology: powershell
ms.openlocfilehash: e823cc0b130500fb7ea60e65acf27f90ad3f3802
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: fr-FR
---
### <a name="on-blacklisting"></a><span data-ttu-id="7b2f1-103">À propos de l’inscription sur liste rouge</span><span class="sxs-lookup"><span data-stu-id="7b2f1-103">On Blacklisting</span></span>
<span data-ttu-id="7b2f1-104">Maintenant que vous avez manipulé JEA, vous vous demandez peut-être s’il est possible d’inscrire des commandes sur liste rouge.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-104">After playing around with JEA, you may be wondering if it is possible to blacklist commands.</span></span>
<span data-ttu-id="7b2f1-105">Cette demande est compréhensible, mais elle n’est pas actuellement prévue pour JEA pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="7b2f1-105">This is an understandable request, but it is not currently planned for JEA for the following reasons:</span></span>

1.  <span data-ttu-id="7b2f1-106">Nous avons conçu JEA pour limiter les opérateurs aux actions qu’ils ont besoin d’effectuer.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-106">We designed JEA to limit operators to only the actions they need to do.</span></span>
<span data-ttu-id="7b2f1-107">Une liste rouge fait le contraire.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-107">A blacklist is the opposite.</span></span>

2.  <span data-ttu-id="7b2f1-108">Les auteurs des commandes PowerShell n’ont pas conçu des commandes PowerShell avec JEA à l’esprit.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-108">PowerShell command authors did not design PowerShell commands with the JEA in mind.</span></span>
<span data-ttu-id="7b2f1-109">Dans une nouvelle installation de Windows Server 2016, environ 1 520 commandes sont disponibles tout de suite.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-109">On a fresh install of Windows Server 2016, there are about 1520 commands immediately available.</span></span>
<span data-ttu-id="7b2f1-110">Les modèles de menace définis pour ces commandes ne comprenaient pas la possibilité qu’un utilisateur les exécutent en tant que compte plus privilégié.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-110">The threat models for these commands did not include the possibility that a user would be running commands as a more privileged account.</span></span>
<span data-ttu-id="7b2f1-111">Par exemple, certaines commandes permettent l’injection de code par conception (par exemple, Add-Type et Invoke-Command dans le module PowerShell principal).</span><span class="sxs-lookup"><span data-stu-id="7b2f1-111">For example, certain commands allow for code injection by design (e.g. Add-Type and Invoke-Command in the core PowerShell module).</span></span>
<span data-ttu-id="7b2f1-112">JEA peut vous avertir quand vous exposez les commandes spécifiques que nous connaissons, mais nous n’avons pas réévalué toutes les autres commandes dans Windows au regard du nouveau modèle de menace.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-112">JEA can warn you when you expose the specific commands we know about, but we have not re-assessed every other command in Windows based on the new threat model.</span></span>
<span data-ttu-id="7b2f1-113">Vous devez comprendre les capacités des commandes que vous exposez par le biais de JEA.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-113">You must understand the capabilities of the commands you exposing through JEA.</span></span>  

3.  <span data-ttu-id="7b2f1-114">De plus, même si JEA a bloqué toutes les commandes comportant des vulnérabilités d’injection de code, il n’existe aucune garantie qu’un utilisateur malveillant ne serait pas capable d’exécuter une action inscrite sur liste rouge avec une autre commande connexe.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-114">Furthermore, even if JEA blocked all commands with code-injection vulnerabilities, there is no guarantee that a malicious user would not be able to carry out a blacklisted action with another related command.</span></span>
<span data-ttu-id="7b2f1-115">Sauf si vous comprenez toutes les commandes que vous exposez, il vous est impossible de garantir qu’une certaine action n’est pas possible.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-115">Unless you understand all of the commands that you are exposing, it is impossible for you to guarantee that a certain action is not possible.</span></span>
<span data-ttu-id="7b2f1-116">Il vous incombe de comprendre les commandes que vous exposez, qu’elles utilisent une liste verte ou une liste rouge.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-116">The burden is on you to understand what commands you are exposing, whether they are using a whitelist or a blacklist.</span></span>
<span data-ttu-id="7b2f1-117">Le nombre de commandes qu’exposerait une liste rouge serait difficile à gérer, c’est pourquoi JEA est plutôt implémenté avec des listes vertes.</span><span class="sxs-lookup"><span data-stu-id="7b2f1-117">The number of commands a blacklist would expose is unmanageable, so JEA is implemented using whitelists instead.</span></span>

