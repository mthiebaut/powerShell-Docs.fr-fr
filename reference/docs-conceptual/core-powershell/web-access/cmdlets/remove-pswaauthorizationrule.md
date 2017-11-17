---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,applet de commande
ms.date: 2016-12-12
title: remove pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: a8304b68a446de0be98aa732304c71302fb8389e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="b0b79-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b0b79-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="b0b79-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b0b79-104">SYNOPSIS</span></span>

<span data-ttu-id="b0b79-105">Supprime une règle d’autorisation spécifiée d’Accès Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="b0b79-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0b79-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b0b79-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="b0b79-107">Id</span><span class="sxs-lookup"><span data-stu-id="b0b79-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="b0b79-108">Règle</span><span class="sxs-lookup"><span data-stu-id="b0b79-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="b0b79-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b0b79-109">DESCRIPTION</span></span>

<span data-ttu-id="b0b79-110">Supprime une règle d’autorisation spécifiée d’Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0b79-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="b0b79-111">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="b0b79-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="b0b79-112">-Force</span><span class="sxs-lookup"><span data-stu-id="b0b79-112">-Force</span></span>

<span data-ttu-id="b0b79-113">Exécute l'applet de commande sans demander confirmation.</span><span class="sxs-lookup"><span data-stu-id="b0b79-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="b0b79-114">Par défaut, l’applet de commande demande confirmation avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="b0b79-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="b0b79-115">Alias</span><span class="sxs-lookup"><span data-stu-id="b0b79-115">Aliases</span></span>                              | <span data-ttu-id="b0b79-116">none</span><span class="sxs-lookup"><span data-stu-id="b0b79-116">none</span></span>                                 |
| <span data-ttu-id="b0b79-117">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-117">Required?</span></span>                            | <span data-ttu-id="b0b79-118">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-118">false</span></span>                                |
| <span data-ttu-id="b0b79-119">Position ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-119">Position?</span></span>                            | <span data-ttu-id="b0b79-120">nommé</span><span class="sxs-lookup"><span data-stu-id="b0b79-120">named</span></span>                                |
| <span data-ttu-id="b0b79-121">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="b0b79-121">Default Value</span></span>                        | <span data-ttu-id="b0b79-122">none</span><span class="sxs-lookup"><span data-stu-id="b0b79-122">none</span></span>                                 |
| <span data-ttu-id="b0b79-123">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b0b79-124">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-124">false</span></span>                                |
| <span data-ttu-id="b0b79-125">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b0b79-126">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="b0b79-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="b0b79-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="b0b79-128">Spécifie les identificateurs (ID) d’une ou plusieurs règles à supprimer.</span><span class="sxs-lookup"><span data-stu-id="b0b79-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="b0b79-129">Alias</span><span class="sxs-lookup"><span data-stu-id="b0b79-129">Aliases</span></span>                              | <span data-ttu-id="b0b79-130">none</span><span class="sxs-lookup"><span data-stu-id="b0b79-130">none</span></span>                                 |
| <span data-ttu-id="b0b79-131">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-131">Required?</span></span>                            | <span data-ttu-id="b0b79-132">true</span><span class="sxs-lookup"><span data-stu-id="b0b79-132">true</span></span>                                 |
| <span data-ttu-id="b0b79-133">Position ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-133">Position?</span></span>                            | <span data-ttu-id="b0b79-134">2</span><span class="sxs-lookup"><span data-stu-id="b0b79-134">2</span></span>                                    |
| <span data-ttu-id="b0b79-135">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="b0b79-135">Default Value</span></span>                        | <span data-ttu-id="b0b79-136">none</span><span class="sxs-lookup"><span data-stu-id="b0b79-136">none</span></span>                                 |
| <span data-ttu-id="b0b79-137">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b0b79-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="b0b79-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="b0b79-139">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b0b79-140">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="b0b79-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="b0b79-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="b0b79-142">Spécifie les règles à supprimer.</span><span class="sxs-lookup"><span data-stu-id="b0b79-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="b0b79-143">Alias</span><span class="sxs-lookup"><span data-stu-id="b0b79-143">Aliases</span></span>                              | <span data-ttu-id="b0b79-144">none</span><span class="sxs-lookup"><span data-stu-id="b0b79-144">none</span></span>                                 |
| <span data-ttu-id="b0b79-145">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-145">Required?</span></span>                            | <span data-ttu-id="b0b79-146">true</span><span class="sxs-lookup"><span data-stu-id="b0b79-146">true</span></span>                                 |
| <span data-ttu-id="b0b79-147">Position ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-147">Position?</span></span>                            | <span data-ttu-id="b0b79-148">2</span><span class="sxs-lookup"><span data-stu-id="b0b79-148">2</span></span>                                    |
| <span data-ttu-id="b0b79-149">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="b0b79-149">Default Value</span></span>                        | <span data-ttu-id="b0b79-150">none</span><span class="sxs-lookup"><span data-stu-id="b0b79-150">none</span></span>                                 |
| <span data-ttu-id="b0b79-151">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b0b79-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="b0b79-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="b0b79-153">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b0b79-154">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="b0b79-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b0b79-155">-Confirm</span></span>

<span data-ttu-id="b0b79-156">Votre confirmation sera requise avant l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0b79-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="b0b79-157">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-157">Required?</span></span>                            | <span data-ttu-id="b0b79-158">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-158">false</span></span>                                |
| <span data-ttu-id="b0b79-159">Position ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-159">Position?</span></span>                            | <span data-ttu-id="b0b79-160">nommé</span><span class="sxs-lookup"><span data-stu-id="b0b79-160">named</span></span>                                |
| <span data-ttu-id="b0b79-161">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="b0b79-161">Default Value</span></span>                        | <span data-ttu-id="b0b79-162">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-162">false</span></span>                                |
| <span data-ttu-id="b0b79-163">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b0b79-164">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-164">false</span></span>                                |
| <span data-ttu-id="b0b79-165">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b0b79-166">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="b0b79-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b0b79-167">-WhatIf</span></span>

<span data-ttu-id="b0b79-168">Présente les conséquences éventuelles de l’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0b79-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b0b79-169">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="b0b79-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="b0b79-170">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-170">Required?</span></span>                            | <span data-ttu-id="b0b79-171">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-171">false</span></span>                                |
| <span data-ttu-id="b0b79-172">Position ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-172">Position?</span></span>                            | <span data-ttu-id="b0b79-173">nommé</span><span class="sxs-lookup"><span data-stu-id="b0b79-173">named</span></span>                                |
| <span data-ttu-id="b0b79-174">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="b0b79-174">Default Value</span></span>                        | <span data-ttu-id="b0b79-175">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-175">false</span></span>                                |
| <span data-ttu-id="b0b79-176">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b0b79-177">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-177">false</span></span>                                |
| <span data-ttu-id="b0b79-178">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="b0b79-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b0b79-179">false</span><span class="sxs-lookup"><span data-stu-id="b0b79-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="b0b79-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="b0b79-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="b0b79-181">Cette applet de commande prend en charge les paramètres courants : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="b0b79-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="b0b79-182">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b0b79-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="b0b79-183">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b0b79-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="b0b79-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="b0b79-184">int\[\]</span></span>

<span data-ttu-id="b0b79-185">Cette applet de commande accepte un tableau d’entiers ou un tableau d’objets PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="b0b79-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="b0b79-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="b0b79-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="b0b79-187">Cette applet de commande accepte un tableau d’entiers ou un tableau d’objets PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="b0b79-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="b0b79-188">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b0b79-188">OUTPUTS</span></span>

<span data-ttu-id="b0b79-189">Cette applet de commande ne produit pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="b0b79-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="b0b79-190">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b0b79-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="b0b79-191">EXEMPLE 1</span><span class="sxs-lookup"><span data-stu-id="b0b79-191">EXAMPLE 1</span></span>

<span data-ttu-id="b0b79-192">Cet exemple supprime la règle d’autorisation avec l’ID *2*.</span><span class="sxs-lookup"><span data-stu-id="b0b79-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="b0b79-193">EXEMPLE 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="b0b79-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="b0b79-194">Cet exemple supprime toutes les règles d’autorisation et demande une confirmation à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b0b79-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="b0b79-195">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="b0b79-195">Related topics</span></span>

- [<span data-ttu-id="b0b79-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b0b79-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="b0b79-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b0b79-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="b0b79-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="b0b79-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="b0b79-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b0b79-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
